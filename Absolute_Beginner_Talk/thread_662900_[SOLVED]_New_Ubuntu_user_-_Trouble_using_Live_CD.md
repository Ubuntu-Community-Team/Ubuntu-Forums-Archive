---
title: "[SOLVED] New Ubuntu user - Trouble using Live CD"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by ss_4 on 2008-01-09
I am a brand new user to Ubuntu and I downloaded version 7.10. Because I have an Intel Q6600 processor I downloaded the 64 bit version.
Then I burned the image to a CD.
When I boot it up I press the "Start or Install Ubuntu" button but afterwards all I get is a blank screen saying no signal.

---

### Post by lian1238 on 2008-01-09
I guess it means no signal is coming to your monitor from your video card. Not sure why that is, though.

---

### Post by Midwest-Linux on 2008-01-09
> **ss_4 said:**
> I am a brand new user to Ubuntu and I downloaded version 7.10. Because I have an Intel Q6600 processor I downloaded the 64 bit version.
Then I burned the image to a CD.
When I boot it up I press the "Start or Install Ubuntu" button but afterwards all I get is a blank screen saying no signal.

 


1. You must burn it as a ISO file. Nero is able to do this.
2. Always use the slowest speed when burning.
3. Try the alternate text installer- if you want just a installation.
4. Do a checksum, do the numbers match up?
5. Try changing the setting to VGA or set to lowest level.
6. Check the CD to make sure there are no defects.

 Just out of habit I've always used the alternate text installer for any installation, but if you just want to run it live. Then the alternate text installer likely won't work as a Live CD. Recheck the checksum, redo the  ISO running the slowest speed. Let us know if that was the problem.

---

### Post by philinux on 2008-01-09
It likely your graphics card. Try the safe graphics option or maybe get the text based installer cd.

What graphics card/integrated is in your machine.

---

### Post by ss_4 on 2008-01-10
> **Midwest-Linux said:**
> 1. You must burn it as a ISO file. Nero is able to do this.
2. Always use the slowest speed when burning.
3. Try the alternate text installer- if you want just a installation.
4. Do a checksum, do the numbers match up?
5. Try changing the setting to VGA or set to lowest level.
6. Check the CD to make sure there are no defects.

 Just out of habit I've always used the alternate text installer for any installation, but if you just want to run it live. Then the alternate text installer likely won't work as a Live CD. Recheck the checksum, redo the  ISO running the slowest speed. Let us know if that was the problem.

1. I have burned it as a ISO
2. I burned it using Roxio, how do I change the speed?
3. What is a text installer? I only want to use ubuntu as a Live CD.
4. What is a checksum?
5. How do I change this setting?
6. When I boot the CD get to the Ubuntu start page but not any further.

> **philinux said:**
> It likely your graphics card. Try the safe graphics option or maybe get the text based installer cd.

What graphics card/integrated is in your machine.

I have a Dell PC with a 8600 GT graphics card.

---

### Post by Tadock on 2008-01-10
Ive got the same card use the[ Alternative Ubuntu Install]("http://mirrors.kernel.org/ubuntu-releases/gutsy/ubuntu-7.10-desktop-amd64.iso") instead to install it. Once that is done then use the[ Envy Script]("http://albertomilone.com/nvidia_scripts1.html") to install the Nvidia driver

---

### Post by ss_4 on 2008-01-10
> **Tadock said:**
> Ive got the same card use the[ Alternative Ubuntu Install]("http://mirrors.kernel.org/ubuntu-releases/gutsy/ubuntu-7.10-desktop-amd64.iso") instead to install it. Once that is done then use the[ Envy Script]("http://albertomilone.com/nvidia_scripts1.html") to install the Nvidia driver

What is the Alternative Ubuntu Install? Do I have to install the driver even if i'm using it as a live cd?

---

### Post by Tadock on 2008-01-10
I am sorry I guess I assumed that you wanted to install Ubuntu. the alternative install is a text base install that is used when the machine has a graphical problem like with the 8600GT. The script is for after Ubuntu is installed to have X work properly, play games etc. I do not know of a way to get the live CD to work is you just wanted to test out Ubuntu from the live CD with out installing the OS.

---

### Post by ss_4 on 2008-01-10
The specs of my computer are: 

Windows Vista, Intel Q6600, Nvidia 8600GT, 2GB Ram and it's a dell.

---

### Post by Tadock on 2008-01-10
> **ss_4 said:**
> The specs of my computer are: 

Windows Vista, Intel Q6600, Nvidia 8600GT, 2GB Ram and it's a dell.

Okay, the specs help. But, I am still confused on what you are trying to do. Try Ubuntu? Install Ubuntu?

---

### Post by ss_4 on 2008-01-10
> **Tadock said:**
> Okay, the specs help. But, I am still confused on what you are trying to do. Try Ubuntu? Install Ubuntu?

I want to try Ubuntu using a Live CD, but when I boot from the disk and click "start ubuntu" I get a blank screen. I only want to use Ubuntu as a live CD.

---

### Post by Tadock on 2008-01-10
I do not see a way that it can be done mayb someone with more experience has the answer. Because, I don't good luck.

---

### Post by ss_4 on 2008-01-10
can anyone help me?

---

### Post by webofunni on 2008-01-10
I think this is a problem with ubuntu 6.10 .....................

It happens because the graphical screen loads in high resolution greater than 1024x768 .... 

I hope that your maximum resolution of the monitor is 1024x768 ......

I think this is your problem

---

### Post by Linuxratty on 2008-01-10
if your going to burn an ISO,Deep Burner's free app will suite you better.
 It should work in Vista.

---

### Post by ss_4 on 2008-01-11
> **webofunni said:**
> I think this is a problem with ubuntu 6.10 .....................

It happens because the graphical screen loads in high resolution greater than 1024x768 .... 

I hope that your maximum resolution of the monitor is 1024x768 ......

I think this is your problem

I've download 7.10, so should it be a problem?

---

### Post by ss_4 on 2008-01-12
> **ss_4 said:**
> I am a brand new user to Ubuntu and I downloaded version 7.10. Because I have an Intel Q6600 processor I downloaded the 64 bit version.
Then I burned the image to a CD.
When I boot it up I press the "Start or Install Ubuntu" button but afterwards all I get is a blank screen saying no signal.

> **ss_4 said:**
> The specs of my computer are: 

Windows Vista, Intel Q6600, Nvidia 8600GT, 2GB Ram and it's a dell.

> **ss_4 said:**
> I want to try Ubuntu using a Live CD, but when I boot from the disk and click "start ubuntu" I get a blank screen. I only want to use Ubuntu as a live CD.

I would like to try Ubuntu as a live cd, but cannot because of this problem. Does anyone know how to fix this?

---

### Post by philinux on 2008-01-12
At the initial screen did you try the safe graphics option

---

### Post by limac on 2008-01-12
ss_4: if you are burning the image from windows, try using infrarecorder, or if there is anyway (i don't think so) to get k3b installed there, that's better, and before burning it ives you a couple of options, there change the burn speed to very low (the lowest) so that all the info can ACCURATELY go into the cd.

---

### Post by jank on 2008-01-12
If you don't want to install linux and only run from a live cd i would recommend you chose a distribution that is specialized to run from a live-cd, like puppylinux or knoppix. If you wan't to try ubuntu before you install it you should of course stick to the disk you have.

---

### Post by ss_4 on 2008-01-12
> **limac said:**
> ss_4: if you are burning the image from windows, try using infrarecorder, or if there is anyway (i don't think so) to get k3b installed there, that's better, and before burning it ives you a couple of options, there change the burn speed to very low (the lowest) so that all the info can ACCURATELY go into the cd.

Whats a k3b? I'm totally new to linux.

---

### Post by ss_4 on 2008-01-12
> **philinux said:**
> At the initial screen did you try the safe graphics option

Yes, just tried it. Still got the same problem.

> **jank said:**
> If you don't want to install linux and only run from a live cd i would recommend you chose a distribution that is specialized to run from a live-cd, like puppylinux or knoppix. If you wan't to try ubuntu before you install it you should of course stick to the disk you have.

I heard that ubuntu is very popular, so wanted to try it.

---

### Post by jupiter74 on 2008-01-12
I believe that the ubuntu version 7.10 live CD will not work with your graphics card - Nvidia 8600GT.

The reason you see the blank screen is because the X server (the graphical user interface) cannot start or doesn't have the drivers/configuration built in to run your Nvidia card and/or monitor.

I had similar problems with the Nvidia 8800 GTS card, but in my scenario I was installing ubuntu, so I was able to use the *alternate* ubuntu CD version 7.10, this is the text-based installer that doesn't need to start the X server. Once ubuntu was installed, I could login and download drivers directly from Nvidia and then start the X server. Note: you can search the forums for 8600GT.

The live CD is designed to start X and only has certain versions of drivers on it, unfortunately it cannot get more updated drivers for the live experience.  You might have to wait until the next live CD version comes out or try another live CD distro.

You have to understand that the video card manufactures don't release the source to their drivers so the linux community has to write them from scratch, so don't get discouraged. It only gets better.

---

### Post by ss_4 on 2008-01-13
> **jupiter74 said:**
> I believe that the ubuntu version 7.10 live CD will not work with your graphics card - Nvidia 8600GT.

The reason you see the blank screen is because the X server (the graphical user interface) cannot start or doesn't have the drivers/configuration built in to run your Nvidia card and/or monitor.

I had similar problems with the Nvidia 8800 GTS card, but in my scenario I was installing ubuntu, so I was able to use the *alternate* ubuntu CD version 7.10, this is the text-based installer that doesn't need to start the X server. Once ubuntu was installed, I could login and download drivers directly from Nvidia and then start the X server. Note: you can search the forums for 8600GT.

The live CD is designed to start X and only has certain versions of drivers on it, unfortunately it cannot get more updated drivers for the live experience.  You might have to wait until the next live CD version comes out or try another live CD distro.

You have to understand that the video card manufactures don't release the source to their drivers so the linux community has to write them from scratch, so don't get discouraged. It only gets better.

Thanks a lot for your detailed answer. I now realise that I probably won't be able run the live CD. I would like to ask what is the differance between the normal ubuntu  and the alternate one.

---

### Post by jupiter74 on 2008-01-17
From the downloads section:
[INDENT]Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.[/INDENT]

The alternate CD is not a live CD, it is meant to actually install onto the machine. All live CDs can just boot off the CD-ROM drive, giving you a test drive without anything being written to your hard drive, although some live CD's also have an install option after they boot completely into the operating system (Ubuntu's does).

The other main difference is the alternate CD's *installer* is text based, not graphical (meaning it simply doesn't start X).  This means that you aren't dependent on the X server starting to do an installation just to format the drive and put files on it.

In my scenario, I wanted the installer to install to the hard drive and the text based installer will install the OS on a broader range of hardware simply because it doesn't try to invoke all of your hardware (high resolution video card, sound card).  This doesn't mean that you can't have an X server once the OS is fully loaded, you just choose to install the X server during the text based installation wizard.  This might sound complicated, but it gives you a little more control.  If X still doesn't start, you can fix it from the command prompt *after* the OS is installed (granted if one has the skill set).

You could also try downloading one of the earlier Ubuntu live CD versions like 7.04 and give it a try.  Quick note on how the Ubuntu versions work... 7.04 came out in the 4th month (April) of 2007.  7.10 came out in October of 2007.  The next version 8.04 will come out in April 2008.

---

