---
title: "Absolute Beginner"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by retrogeek on 2007-01-04
I've decided to make the jump to Linux, and I'm going to use Ubuntu because of its wide distribution. I wanted to jump into the forums before my CD arrives so that I could discuss some of the ins and outs.

The PC I will be using is an 866 MhZ PIII with 192 MB RAM. The hard drive's fried on this machine, so I will be purchasing a new drive. I will be formatting and setting this drive up exclusively to run Linux. My "Main machine" is a P4 XP/2000 dual boot, and I am modding a TRS-80 CoCo case with modern components to use as my main computer, haven't firmly decided on an O/S yet. Part of the reason I will be making the Linux jump is to analyze whether or not it is appropriate to use for the new computer.

I am an A+ certified tech, working on my Network + and Security +. I am hardly a newbie, but since my experience has been with (ahem!) those guys from Redmond, there's a lot of relearning I am going to have to do. I am hoping this forum can provide some of the answers.

---

### Post by xyz on 2007-01-04
Hi retrogeek...hi and Welcome!
Here's one of the many places where to start from:
[Ubuntu Edgy Starter Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")
Fell free to ask questions.
Good luck!

---

### Post by CroEragon on 2007-01-04
I think that Ubuntu won't work on first pc (PIII one). For first one you should consider Xbuntu or Flaxbuntu. You should have 256mb RAM to run Ubuntu as far as i know.
About second one i think most of things will work out of box but still if you get into problems you shouldnt give Ubuntu up. Before giving up read as many Linux/ubuntu documentation as possible, search this forum or post question if you cant find answer.
Also you are not newbie with computers and you are willing to learn so there shouldn't be problems bith Linux/Ubuntu.

---

### Post by pross on 2007-01-04
it'll run...it will just be a bit slow

---

### Post by kEinstein on 2007-01-04
> **kEinstein said:**
> Cylinder, Header, Sector Problem with older BIOS versions
[...]
If I am not mistaken, this also applies to Ubuntu. Use the method below to ensure a proper installation:

1) Insert your CD and turn on the computer
2) go to a command line and type 'fdisk -l'. You will be given a table with info on your hard drive
3) look for the values C 'cylinders' H 'headers and S 'sectors', write them down (or remember)
4) go back to the install-screen, use 'expert mode' and add the following arguments
```
 hda=C,H,S 
```
Replace the C,H,S values with your specifications.
e.g. 'fdisk -l' returns C...7752, H...252, S...63 you are required to use the following argument:
```
 hda=7752,252,63 
```
5) hit enter and watch Ubuntu install on your PC.

In case you are interested, this argument aims at the Cylinder, Header, Sector problem on 'old' PCs as your BIOS might not be able to read the values correctly from the partitition table. By giving these arguments at the install line, you override the information with the appropriate values from 'fdisk'

---

### Post by retrogeek on 2007-01-04
Thanks for the heads up on the memory. I'll put memory upgrade on my list for this computer. It's running with a stick of 128 mb and a stick of 64 mb, so it shouldn't be any problem to upgrade to 256, as long as I can find the right memory.

I'm guessing from what I've read that Linux doesn't have the same problem that the "boys from Redmond" have; eg, running the OS with the minimum system requirements resulting in extremely poor performance. At any rate, I'll take a serious look and see if the PC will take two sticks of 256 just to enhance performance.

---

### Post by CroEragon on 2007-01-04
> **retrogeek said:**
> Thanks for the heads up on the memory. I'll put memory upgrade on my list for this computer. It's running with a stick of 128 mb and a stick of 64 mb, so it shouldn't be any problem to upgrade to 256, as long as I can find the right memory.

I'm guessing from what I've read that Linux doesn't have the same problem that the "boys from Redmond" have; eg, running the OS with the minimum system requirements resulting in extremely poor performance. At any rate, I'll take a serious look and see if the PC will take two sticks of 256 just to enhance performance.

No. There is bunch of Linux distributions designed for older PC's that are based on new and advanced distributions. As mentioned before, i know for two Ubuntu based Distributions but you might wanna check [this.]("http://en.wikipedia.org/wiki/Minilinux")

---

### Post by retrogeek on 2007-01-04
Well, part of the reason I want Ubuntu specifically is to evaluate it for my build. My build will be a higher end computer, and I want an option other than Windows. Truthfully, Windows pays my bills, but as tech support, I've seen far too many issues with it (most notably with automatic updates and IE7). I could go down the list of issues I've had with Windows, but I'm certain it's a litany each and every one of you have heard. And with the increasing user friendliness of Linux, I think it's past time I jumped off the Windows bandwagon.

From what I've seen, I don't think I'll have a lot of problems with this computer except the memory, and that's the easiest problem to fix, fortunately.

---

