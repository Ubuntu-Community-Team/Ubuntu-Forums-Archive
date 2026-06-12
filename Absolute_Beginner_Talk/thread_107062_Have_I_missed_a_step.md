---
title: "Have I missed a step?"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2005-12-22
Hi all! I am totally new to linux and expect this to be a long learning curve.
Here is my first question and my second step. I have downloaded Ubuntu 5.10-install-1386.iso (seems to have downloaded without a fault), and burned it to cd.I have changed boot sequence with the CD as 1st boot device. I intend to dual boot with XP. Unfortunately when the cd is put in the drive and rebooted the PC boots into XP. So, have I missed a step in the download or burning? BTW, love the meaning of UBUNTU.
Thanks for any advice.
sbarton

---

### Post by hashimoto on 2005-12-22
You need to burn the downloaded .iso file to a CD as an image. You have probably burned it as a (data)file, hence no booting. Try looking into your burner software for something like " burn as image".

---

### Post by Brynster on 2005-12-22
When you burnt the CD did you just copy the files to the disc. Or did you set nero (i assume) to burn as a CD image?

If you just dumped the file you will have a file on the CD called soemething around unbuntu510.iso

If you burnt it correctly as a disc image you shoudl see several files listed on the CD.

If you have burnt it correct as a CD image and it still doesn't work then i would suggest the CD burn was bad. Retry buring the disc but set your burning software to burn at the lowest speed available to you (usually aroun 4x or 6x lower if possible)

Darrn beaten to the post Grrrrr :razz:

---

### Post by Sbarton on 2005-12-22
Thanks for replies. I did save the file on HDD. I then burned it (via NERO) and  have a disc with file Ubuntu 5.10-install-iso (1 file visible). If I right click this file ISOBuster opens up the file and I see numerous files such as CD  Session1, Ubuntu bootable cd etc.However, as it is it will not boot. I have obviously missed out doing something or done it wrong! Any help appreciated.
sbarton

---

### Post by bscbrit on 2005-12-22
As the other posts have suggested - burn it again as an image not as a data file.

---

### Post by Sbarton on 2005-12-23
Thanks for all replies! Having now engaged brain before acting, I reburnt as image file. Installation began up to Base install when a number of corrupt files stopped any further installation. Now whether these necessary files were corrupt when downloaded or burnt I have no idea, though I am leaning to the former. I will just wait now until I receive the CD's I have ordered. Thanks for info and patience. I'll be back!:) 
sbarton

---

### Post by hashimoto on 2005-12-23
You could also try the following:

1. Check the md5sum of the downloaded iso file. There is a command line tool for windows which you can easily find with google. You can find the correct md5sum for the download page.

2. Burn the image with a slower speed (say 4x). High speed burns tend to have more errors.

---

