---
title: "LInux Mint installation problem"
date: 2011-04-23
forum: Any Other OS
---

### Post by abnordude on 2011-04-23
Hi,
I'm currently running ubuntu 11.04.
I downloaded linux mint cd iso from their website.
I burned it to a CD.
And then i put the CD in the drive and restart.
The screen is only showing black.
When I remove the installation CD i can get into ubuntu.
But the screen shows blank when I insert the linux mint installation disk.
I dunno what is wrong.
Please help me.

---

### Post by Rubi1200 on 2011-04-23
Is BIOS set to boot from the CD/DVD drive?

What graphics card do you have installed?

Which version of LM; the latest version 10?

---

### Post by Zero Prime on 2011-04-23
Also, have you checked to make sure it was a good burn?  If you have ever had Ubuntu 10.10 installed on your PC, then it shouldn't be a graphics card problem.  Also, if you are getting a black screen, at least the PC is trying to read from the media which means that it should already be set to read from CD/DVD.  Ir really sounds like a a bad burn or corrupted download to me.

---

### Post by abnordude on 2011-04-24
I'm using the latest  version of linux mint.
I think maybe 10.
I downloaded the iso from their website [CD Version]. and burned at the lowest speed. 
And yet I'm geting the same result.
Completely black screen.
This time I waited for about 15 minutes too.
And still it was black.
No improvement.

---

### Post by Rubi1200 on 2011-04-24
Depending on your graphics card, take a look at some of the options here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by abnordude on 2011-04-24
> **Rubi1200 said:**
> Depending on your graphics card, take a look at some of the options here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)


Yeah. I tried the link that you gave me.
I'm a linux noob. And hence I didnt understand many things that were written in there.
I need something that is simple to understand [sorry], because it's only been some time that i'm using linux.

---

### Post by Rubi1200 on 2011-04-24
We need to know what graphics card you have so we can tell you the right options to use.

---

### Post by abnordude on 2011-04-24
> **Rubi1200 said:**
> We need to know what graphics card you have so we can tell you the right options to use.

I dunno what graphics card i use.
Is there anyway to find out? (oh! I'm currently in opensuse).

---

### Post by Rubi1200 on 2011-04-24
From the terminal:

```
lspci | grep VGA
```

---

### Post by abnordude on 2011-04-24
> **Rubi1200 said:**
> From the terminal:

```
lspci | grep VGA
```

I tried this code but there was no response.
Then i tried this code
 
man nv

I got this result

[FONT=monospace]
NAME
       nv - NVIDIA video driver

SYNOPSIS
       Section "Device"
         Identifier "devname"
         Driver "nv"
         ...
       EndSection

DESCRIPTION
       nv  is  an  Xorg driver for NVIDIA video cards.  The driver supports 2D
       acceleration and provides support for the following framebuffer depths:
       8,  15, 16 (except Riva128) and 24.  All visual types are supported for
       depth 8, TrueColor and DirectColor visuals are supported for the  other
       depths  with the exception of the Riva128 which only supports TrueColor
       in the higher depths.


SUPPORTED HARDWARE
       The nv driver supports PCI, PCI-Express and AGP video  cards  based  on
       the following NVIDIA chips:

       RIVA 128              NV3

       RIVA TNT              NV4

       RIVA TNT2             NV5

       GeForce 256, Quadro   NV10

       GeForce2, Quadro2     NV11 & NV15

       GeForce3, Quadro DCC  NV20

 Manual page nv(4) line 1/198 13%

_____________________________________________________________________
and some more pages.
Well is this enough?


[/FONT]

---

### Post by Rubi1200 on 2011-04-24
I don't understand why that command wouldn't work. All it does is probe the PCI devices on the computer.

Anyway, if you have an NVIDIA card, then follow the instructions in the link:
Use the instructions where it says > How to enable kernel options on the livecd (before install)
You need to use the nomodeset option.

Let me know if this works.

---

### Post by abnordude on 2011-04-25
> **Rubi1200 said:**
> I don't understand why that command wouldn't work. All it does is probe the PCI devices on the computer.

Anyway, if you have an NVIDIA card, then follow the instructions in the link:
Use the instructions where it says 
You need to use the nomodeset option.

Let me know if this works.

I'm not even getting the green screen.
Tis' completely black from the start.

---

### Post by Rubi1200 on 2011-04-25
I honestly don't know what to tell you other than try an earlier version like 9 or even 8. If the problem persists then you know it is probably a hardware issue. If not, we need to figure out what changed between the versions that doesn't allow you to boot the CD.

Also, did you burn at the slowest possible speed and have you tried another CD in case the one you are using is somehow scratched or otherwise defective?

---

### Post by ventrical on 2011-04-25
> **Rubi1200 said:**
> I honestly don't know what to tell you other than try an earlier version like 9 or even 8. If the problem persists then you know it is probably a hardware issue. If not, we need to figure out what changed between the versions that doesn't allow you to boot the CD.

Also, did you burn at the slowest possible speed and have you tried another CD in case the one you are using is somehow scratched or otherwise defective?

Burning ISOs is touchy. I have had a few bad one's - ie; PC LinuxOS Zen,Karmic .. etc.. also .. it is good to make sure that one has the correct web-site and is not the victim of a redirect. There are a lot of 'official' looking sites but who really knows what distros are tampered with or not .

I have Linux Mint 10 working great .. and .. btw .. I do not get a green screen but more of a light greyscale with green undertones at the splash and desktop theme.

I use Brasero or just the standard default. Since I started using Lucid some time ago I haven't had a bad burn that I can recall and the bad burns that I did have came from using Imageburn on a Win XP system.

:)

---

### Post by abnordude on 2011-04-26
> **Rubi1200 said:**
> I honestly don't know what to tell you other than try an earlier version like 9 or even 8. If the problem persists then you know it is probably a hardware issue. If not, we need to figure out what changed between the versions that doesn't allow you to boot the CD.

Also, did you burn at the slowest possible speed and have you tried another CD in case the one you are using is somehow scratched or otherwise defective?

I did burn at the lowest speed, twice and yet I'm getting the black screen.

I'm gonna try to download the DVD version of linux mint. I'll give you the details on what happenes then.

---

