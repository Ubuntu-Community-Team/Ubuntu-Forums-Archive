---
title: "Problem Booting from Live CD"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by parkskier on 2008-01-25
I am having problems loading Ubuntu from the LiveCD I created.  When I reboot my computer, it will load the Ubuntu launch menu.  I select the Start or Install Ubuntu option and a progress bar pops up that says, "Loading Linux Kernel."  The bar gets to 100% and then nothing happens.  I can hear the cd spinning in the drive too.  Any help?  I've also tried booting in safe graphics mode to the say effect.

---

### Post by taurus on 2008-01-25
When you first boot from the CD, you would get a menu and one of them is to check your CD for defects.  Try running that to see if there is anything wrong with your CD first before you boot into it.  Also, if you burnt it at max speed, you might want to consider burning it again except at a slower speed like 4x.

---

### Post by Ryadt on 2008-01-25
You need to download the alternate version of ubuntu on the homepage..then boot from it...but this will be a command line installation..

---

### Post by parkskier on 2008-01-25
Ok, I'm confussed.  I understand the part about the alternate version, but what do you mean by command line installation?  Do I need to download the alternate version and then burn it to cd and then do something?  Or what?  Sorry, I know I am new to this and thanks for the help.

BTW, burning a new disc at a slower speed didn't work.

And by alternate you are referring to the "64bit AMD and Intel computers" version, right?

---

### Post by Ryadt on 2008-01-25
ok..on the ubuntu homepage choose the version of ubuntu which you want to download nad make sure you check the box just under the Start Download button...
then you need to burn it and then install it..
sorry I didn't mean to say command line installation. I should have said text-mode installation..

---

### Post by parkskier on 2008-01-25
Ok, so the Alternate was definitely better, however I think something is messed up, I just don't know where.  If someone could pinpoint where this error would come from that would be great.  So I started up my computer with the cd, and the menu came up.  I decided it would be a good idea to check the cd integrity.  When I did this I get an error saying the following file is corrupt:

./pool/restricted/n/nvidia-kernel-common/nvidia-kernel-common_20051028+1ubuntu7_all.deb

Is this corrupt from the download, or from the cd burning?  I compared my downloaded file using winMd5sum with the appropriate Ubuntu hashes, and it said they were the same.  Also, I tried burning two different discs, one at 16x and one at 10x (the slowest I can).

---

### Post by Ryadt on 2008-01-25
the download was corrupt...I personally used the direct link to download gutsy -laziness :) ..You can try downloading gutsy by torrents..less chance of corrupt files

---

### Post by taurus on 2008-01-25
Please run the option on the first screen to check your CD for defects.

---

### Post by parkskier on 2008-01-25
That's what I did, and that's when I got that that file was corrupt.

---

### Post by parkskier on 2008-01-25
I tried downloading from a different host and burning at 1x using a different image burner and still get the same error.  Could it be a problem with my computer?

---

### Post by Sidewinder1 on 2008-01-25
Welcome Park! I had a similar problem and this is gonna sound funny but get one of those cans of air and blow out your DVD Burner Drive. Mine was full of dust and then it worked fine. Since the md5sum check confirmed the integrity of the file, this solution may work for you also. And it's easy and painless.

---

### Post by parkskier on 2008-01-26
Ok, before I waste another cd, will this fix the problem, or are there other measures I can take in addition to this.

---

