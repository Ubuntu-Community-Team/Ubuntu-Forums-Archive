---
title: "medical data DICOM view - howto"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by zorro59 on 2008-02-06
Hi,
i try to browse pictures from Nuclear Magnetic Resonanz Tomografie (NMR, MRT, Kernspin) and x ray computer tomografie (CT) with ubuntu 7.10. These pictures are stored in DICOM Format. It's possible to view each single picture with 
 Aeskulap
 DICOM file navigator
 gimp 
and so on. But none off them is able to load all some 100 pictures at once and to browse them like siemens syngo_fl.exe or philips mlv.exe in win32.

It seems that they don't understand the DICOMDIR file. 

Dicom File Navigator: 
openDicom.DicomException:
   Pixel data samples per pixel are invalid.
Context:
   ParamName:      PixelData.SamplesPerPixel
   ParamValue:     0
StackTrace:
  at openDicom.Image.PixelData.get_SamplesPerPixel () [0x00000] 
  at MainWindow.PrepareImages () [0x00000] 
  at MainWindow.PostDicomFileLoad (System.String fileName) [0x00000] 
  at MainWindow.LoadDicomFile (System.String fileName) [0x00000] 

Aeskulap alows to mark and load all Files from a directory manually, if I select show ALL files in the directorybox. By default it doesn't recognize them to be DICOM files. It is impossible to open the DICOMDIR file.

what can I do?
Are there known problems with case sensity off Filenames?
The filenames are all in uppercase in the DICOMDIR, but the files are stored in lowercase on FAT Partition or FAT USB device. Ubuntu seems to ignore case on FAT devices.

Thanks in advance

---

