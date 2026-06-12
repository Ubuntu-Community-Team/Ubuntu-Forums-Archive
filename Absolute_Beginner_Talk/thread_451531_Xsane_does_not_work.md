---
title: "Xsane does not work"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by neotasic1 on 2007-05-22
Hi all.  I have a problem scanning in Feisty via a ACER/Benq/Vuego 3300 scanner (USB) Running Xsane from Gnome produces an error "failed to open device 'snapscan:libusb:003:005': invalid argument"  This is kinda non intuitive as error messages go, so I have tried running Xsane from the terminal to see if the error message is a bit more informative.  I get this:-

neotasic1@Chiana:~$ xsane
[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
neotasic1@Chiana:~$ 


Couple of problems with this.  The snapscan directory does not exist as per the path given, and the firmware file binary also is conspicuous by its absence.  Given this after a quick peruse of the snapscan.conf file, I didn't see the point of attempting an edit of the firmware file entry.  Am I missing something, or are there drivers missing from my installation (I believe this scanner is supposed to be supported out of the box.)  If so, where do I get them from (I have already installed sane-utils to no effect.)

I have been reading the forum posts with regard to the deliberately broken usb issue in Feisty, but the above problem seems to be different.  Certainly the scanbuttond workaround in my case doesn't. (workaround that is):D  Neither does using scanimage in default mode from the terminal produce any activity.  scanimage -L does recognise that the scanner is there, but it is listed second (presumably not the default device) after my unsupported DVICO fusion HDTV card.  Attempting to run scanimage from the terminal specifying the scanner as the device to use, produces the same error xsane does (as above).  

Installing the previous Edgy Eft kernel is an option I won't entertain at this stage, as I am extremely happy with the rest of the Feisty install and don't want to create a raft of potential problems whilst perhaps fixing one.  Also, as I still have a dual boot option, I can always scan from windows if really get desperate, but this seems a hairbrained approach - so I am looking for an alternative workaround.  Any ideas?

---

### Post by Kobalt on 2007-05-22
Have you checked [that]("https://help.ubuntu.com/community/ScanningHowTo") out already ?

---

### Post by neotasic1 on 2007-05-23
> **Kobalt said:**
> Have you checked [that]("https://help.ubuntu.com/community/ScanningHowTo") out already ?

Thank you, but yes I have followed all the instructions relating to this scanner in this howto.  (The reference to the specific ArtecEplus48U howto was interesting in that the error message is nearly the same, but unhelpful in that the steps outlined are not applicable to my scanner and the firmware file referred to is not correct for the model I own.)  Nor is it very enlightening as to where one may source the firmware file required.  I believe from the reading I have been doing, that this scanner requires the snapscan firmware, which according to snapscan.conf should be automatically detected and configured.  The fact that xsane and scanimage both detect the presence of the ACER flatbed scanner on my system indicates detection has occurred, but progress from there appears non existent due to an inability to locate the driver firmware required.  

I don't have enough system knowledge to peruse the appropriate directories in an effort to locate it myself, nor has a google search been helpful in locating a driver for Linux, although this is a very common budget scanner.

I will continue to do more research on the Sane website and perhaps something will crop up.  Thanks for the reply, and if you think of anything else that might help, let me know.

---

### Post by dazzled on 2007-05-29
Do you have the windows install cd for the scanner? See a similar problem solved with the windows cd at [http://ubuntuforums.org/showthread.php?t=264850&highlight=benq+scanner](http://ubuntuforums.org/showthread.php?t=264850&highlight=benq+scanner)

---

