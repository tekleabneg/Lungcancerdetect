# Lungcancerdetect
research project
I downloaded the SimpleItk package and trying to load a .mhd image


import SimpleITK as sitk
import numpy as np
import csv
import os
from PIL import Image
import matplotlib.pyplot as plt
%matplotlib inline

def load_itk_image(filename):
    itkimage = sitk.ReadImage(filename)
    numpyImage = sitk.GetArrayFromImage(itkimage)
     
    numpyOrigin = np.array(list(reversed(itkimage.GetOrigin())))
    numpySpacing = np.array(list(reversed(itkimage.GetSpacing())))
     
    return numpyImage, numpyOrigin, numpySpacing
    def readCSV(annotations):
    lines = []
    with open('annotations', "rb") as f:
        csvreader = csv.reader(f)
        for line in csvreader:
            lines.append(line)
    return lines
    
    RuntimeError                              Traceback (most recent call last)
<ipython-input-23-1f6d5a105513> in <module>
      1 # load image
----> 2 numpyImage, numpyOrigin, numpySpacing = load_itk_image(img_path)
      3 print(numpyImage.shape)
      4 print(numpyOrigin)
      5 print(numpySpacing)

<ipython-input-13-7ef72af0dae8> in load_itk_image(file)
      1 def load_itk_image(file):
----> 2     itkimage = sitk.ReadImage('1.3.6.1.4.1.14519.5.2.1.6279.6001.100225287222365663678666836860.mhd')
      3     numpyImage = sitk.GetArrayFromImage(itkimage)
      4 
      5     numpyOrigin = np.array(list(reversed(itkimage.GetOrigin())))

~\Anaconda3\lib\site-packages\SimpleITK\SimpleITK.py in ReadImage(*args)
   8874 
   8875     """
-> 8876     return _SimpleITK.ReadImage(*args)
   8877 class ImageViewer(_object):
   8878     """

RuntimeError: Exception thrown in SimpleITK ReadImage: D:\a\1\sitk\Code\IO\src\sitkImageReaderBase.cxx:104:
sitk::ERROR: Unable to open "1.3.6.1.4.1.14519.5.2.1.6279.6001.100225287222365663678666836860.mhd" for reading.
