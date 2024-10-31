# An adapter IO for image File Reader and Writer

## Introduction

An implement based on C++ and [OpenImageIO](https://sites.google.com/site/openimageio/home) read and write different image format,  because the code is an adapter for the library, there are several advantages :

- support nearly all the formats
- data type is origin type, i.e **unsigned char**,  **unsigned short**, **float** etc

[OpenCV](https://opencv.org/) or [CImg](https://cimg.eu/) can also read and write image file, but OpenCV is too large, and the image is stored in class **cv::Mat** or **Cimg**, so it will be not complicate to modify the value in the pixel. On the other hand, for the memory issue, all the image is read when open the file.

## Ubuntu

We can follow the the [instruction](https://github.com/AcademySoftwareFoundation/OpenImageIO/blob/master/INSTALL.md) to install the library.

**News** After Ubuntu 20.04, we can install  [OpenImageIO](https://sites.google.com/site/openimageio/home) easily :

```
sudo apt install libopenimageio-dev
```

## Windows

Actually, this code is more useful in Windows, because after building the dependency libraries,  the include, library, and execution file is more simple(just a few files), we only need to set the include and library directory in VS project.

More information can be found in [subfolder](./Windows).

## Example

The code is very easy to use, here is an example to read : 

```
	// define the path
	char szImgPath[512] = ""
	COpenImageIO Image;
	Image.Open(szImgPath);
	
	int nRows = Image.GetRows();
	int nCols = Image.GetCols();
	int nColors = Image.GetPixelBytes();

	unsigned char * pImage = new unsigned char[nRows * nCols * nColors];
	memset(pImage, 0, sizeof(unsigned char) * nRows * nCols * nColors);
	
	Image.Read(pImage);
	
	Image.Close();
```

## Question

### Install bug

If you have a bug in compiling **/lib/x86_64-linux-gnu/libtiff.so.5 : référence indéfinie vers « libdeflate_free_compressor »**, you can compile the [libdeflate](https://github.com/ebiggers/libdeflate) using CMake.

## MAINTENANCE

If you think you have any problem, contact [Teng Wu]<whuwuteng@gmail.com>

