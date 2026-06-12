---
title: "XP to Ubuntu from downloaded CD"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by AkiraBergman on 2007-03-19
Hello all,

I want to install Ubuntu on my second hard disk from the downloaded CD. I have WindowsXP on the first one. The second one currently has Debian/Linux installed. The PC boots to Debian by default but I can switch to XP during the boot.

I have finally achieved burning a bootable CD, but it stops and gives a drive A: prompt. I can not fugure out what it wants. Shouldn't it just carry on and ask me questions about which HD to chose and so on?

Should I do anything about the already installed Debian, like clearing it out? Or, would Ubuntu CD just overwrite it? What would happen to the boot switch for Debian/XP choice?

Thanks so much,
AB.

---

### Post by raja on 2007-03-19
The root partition will be formatted during the install, removing Debian. The bootloader will also installed again, so XP and Ubuntu should be the new choices. 
Are you trying to install with the live cd ? Which version ?

---

### Post by AkiraBergman on 2007-03-19
I burnt the CD from the downloaded (today) ISO image from Ubuntu site. How do you tell which version it is?

---

### Post by AkiraBergman on 2007-03-19
Ooops, this is the name of the file I downloaded;

ubuntu-6.10-desktop-i386.iso

---

### Post by raja on 2007-03-19
You should check the md5sum to be sure that the downloaded image is OK and then burn to disk at a low speed. If there is still a problem trying to boot into the live cd, you can use the alternate cd for installation. It is generally more robust and error-free.

---

### Post by AkiraBergman on 2007-03-19
Do you mean by alternate CD as the ordered CD from Ubuntu site?

---

### Post by raja on 2007-03-19
No. In the downloads you should be able to find an alternate install cd. This will be a text based install without a live environment, but generally works when the live cd fails.

---

### Post by dhughes on 2007-03-19
Just an FYI about making a bootable CD for you or maybe others reading this who don't know.

 In windows the easiest way to make a bootable CD from the downloaded .iso is to use Alex Feinman's ISO Recorder.

 Download and Install ISO Recorder [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)
 and then put a blank CD in the CD drive, right click the image file (Ubuntu in this case) and choose "Copy image to CD". Easy.

 Ubuntu needs such a thing. If I could program I wold do it! But alas I'm a dummy when it comes to that, tried it and failed.

---

### Post by AkiraBergman on 2007-03-19
Thanks everyone. I got him installed now. The problem was that I was using a wrong CD burn program. I followed the Ubuntu recommendations and it worked.

---

### Post by raja on 2007-03-20
> **dhughes said:**
> 
 Ubuntu needs such a thing. If I could program I wold do it! But alas I'm a dummy when it comes to that, tried it and failed.

Burning an ISO to disk is pretty straightforward with any of the cd writing programs in Linux. You can use gnomebaker for example and choose to burn an image to the disk.

---

