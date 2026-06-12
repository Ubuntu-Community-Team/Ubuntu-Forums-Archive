---
title: "Problems with ISOs of multiple distros"
date: 2016-05-14
forum: Any Other OS
---

### Post by yman on 2016-05-14
I've downloaded ISOs of multiple distros. Whether I run them in virtualbox or install them to a flash drive and then boot real hardware with them, non of them work properly. LinuxMint-Xfce runs, but the disc check shows errors and the bootsplash on VirtualBox doesn't display properly and shows error messages. Xubuntu 16.04 sometimes boots on VirtualBox, but fails on real hardware. Lubuntu 16.04 fails on both. Ubuntu MATE runs on VirtualBox but IIRC fails on real hardware. Fedora Xfce, Kali Linux Light, and Mythbuntu seem to run okay on VirtualBox (even if the bootsplash is wrong and shows errors).

So why are 2 or 3 Ubuntu derivatives completely failing on real hardware? I'd like to install Lubuntu on an old netbook, but it won't boot. Xubuntu also doesn't seem reliable enough, and although I don't want to use LinuxMint especially since the disc check shows many errors, it may be my only option for something that is actually suitable for my needs and pleasant to use and based on Ubuntu.

---

### Post by QIII on 2016-05-14
Hello!

Given your description, my first inclination would be to suspect that your process of downloading and preparing install media -- or the hardware you are using -- is the issue.

How are you downloading?  Burning?  What media are you using?  If you are burning optical media, are you sure your hardware is not faulty?

---

### Post by yman on 2016-05-14
I downloaded them using the torrents, then verified the download using the Transmission "Verify Local Data" function. In VirtualBox I just mounted the ISO as a disc and booted from it. For testing on physical hardware I used Ubuntu's Startup Disc Creator to install the ISO on a USB flash drive. I made multiple attempts. Some distros consistently failed in the same way even when I re-dowloaded them. Some consistently succeeded in the same way. I'm going to try Elementary next.

EDIT: I forgot to mention that in all cases I'm downloading the 32 bit ISO because the machine I intend to install the distro on is an old nebook with an Atom processor and 1 GB RAM.

---

### Post by QIII on 2016-05-14
> **yman said:**
> ... Atom processor ...

Becomes significant in my mind.  But I wouldn't expect failure in VM.  How have you provisioned the VMs?

When you say "fail in the same way", what do you mean?

---

### Post by yman on 2016-05-14
Default, except for the memory which I set to 1 GB to imitate the memory constraint that exists on the netbook.

Always fails the same way means that for example Xubuntu always fails to to find some kind of COM32 or something like that, while Lubuntu always fails to display or do anything, LM-Xfce always shows garbled text while booting along with status and error messages, etc.

---

### Post by oldfred on 2016-05-14
Some Atoms are Bay Trail.

 Bay Trail issues, boot parameter required
[http://ubuntuforums.org/showthread.php?t=2314964](http://ubuntuforums.org/showthread.php?t=2314964)
[https://en.wikipedia.org/wiki/List_of_Intel_Atom_microprocessors](https://en.wikipedia.org/wiki/List_of_Intel_Atom_microprocessors)

Some have 32 bit UEFI.

 Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

---

### Post by yman on 2016-05-15
It's an Acer Aspire One with Intel Atom processor that originally came with Windows XP. Based on the Wikipedia article it seems this model was released in 2008, while Bay Trail is from 2013, so no.

Also I forgot to mention that I was trying the latest stable release of each of the above distros, and that I also tried Lubuntu 14.04 in addition to Lubuntu 16.04. Lubuntu 16.04 failed to even display anything on the screen except maybe a cursor, but IIRC Lubuntu 14.04 did boot. The problem is that support for 14.04 will run out in 11 months, and I want to "fire and forget" about this OS installation, so I want something with support for at least until after the next LTS.

Also I forgot to mention that I tried Lubuntu and I think Xubuntu on my main laptop which is System76 Galago Ultra Pro from 2014, and they had the same problems. considering that 3 machines all had problems with the same OS images, and considering that from what I can see the problems stay the same even if I delete the ISO and download and use a fresh one, it feels to me like a problem with the ISO. I'm thinking now that maybe there is a problem with the 16.04 release images since the only OS I can't boot at all in a VM is Lubuntu, and the only ones that I tried on real hardware that won't boot are Xubuntu, Lubuntu, and Ubuntu MATE. I tried Elementary and it worked. Also Ubuntu Kylin worked in VM, but I don't see a point to trying it on HW since I don't know Chinese and can't find a way to switch the UI to another language.

To summarize:

Don't work on real HW:
Lubuntu 16.04, Xubuntu 16.04, Ubuntu MATE 16.04

Do work on real HW:
LinuxMint Xfce 17.3, Xubuntu 16.04, ElementaryOS 0.3.2, Lubuntu 14.04.4

Don't work in VB:
Lubuntu 16.04

Do work in VB:
Xubuntu 16.04, Ubuntu MATE 16.04, LinuxMint Xfce 17.3, ElementaryOS 0.3.2, Fedora Xfce 23, Kali Linux Light 2016.1, Ubuntu Kylin 16.06, Mythbuntu 16.04, Lubuntu 14.04.4

When booting Xubuntu on the Acer:
> 
Missing parameter in configuration file. Keyword: path
gfxboo.c32: not a COM32R image
boot:

---

### Post by sudodus on 2016-05-15
The 'gfxboo.c32: not a COM32R image' output indicates a known bug with the Ubuntu Startup Disk Creator. Use another tool. ***mkusb clones*** the iso file to a USB pendrive. That process is much more reliable, (and the Ubuntu Startup Disk Creator 0.3.2 of Ubuntu 16.04 LTS is also using that process).

See this link: [mkusb](https://help.ubuntu.com/community/mkusb)

But there is an additional problem with Lubuntu 16.04 LTS and some old Intel graphics chips. You can use the method described at the following link to work around the problem with the graphics,

[New Lubuntu tarball with 'xserver-xorg-video-intel' for Intel graphics](http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13487384#post13487384)

---

### Post by yman on 2016-05-15
Thanks for the tip, but I have just one question: could they have possibly made mkusb less user-friendly? It will take time for me to figure out how to actually use this thing before I can test Lubuntu and Xubuntu.

---

### Post by PaulW2U on 2016-05-15
> **yman said:**
> Thanks for the tip, but I have just one question: could they have possibly made mkusb less user-friendly? It will take time for me to figure out how to actually use this thing before I can test Lubuntu and Xubuntu.
I find using **mkusb-nox** in a terminal easier to use than the GUI version, **mkusb**. Perhaps give it a try?

---

### Post by sudodus on 2016-05-15
I made mkusb. The intention is to make things very clear to help beginners avoid writing to the wrong drive. But I listen to you, when you say that it is 'less user friendly', and I will look at possibilities to make it easier to use. Please tell me, what you would suggest :-)

-o-

I often use the simple text, 'no X', version mkusb-nox and I agree with *PaulW2U*, that it is faster and easier for people who need less guidance.

---

### Post by yman on 2016-05-16
I'm sure mkusb is a great tool, especially if it is being used as a basis for other tools, but the GUI needs to be remade. Startup Disc Creator is a good example, even if you would have to make it more complicated to include all the options.

I'm sorry for being so critical.

---

### Post by sudodus on 2016-05-16
Am I understanding correctly, that you want fewer windows and less information - the ultimate goal would be to have one single window (plus a checkpoint window), like the Startup Disc Creator?

---

### Post by yman on 2016-05-16
Or it can be a wizard. The problem here is that it's not clear when I'm supposed to do what, so I feel like I keep going backwards and forwards without understanding what I'm doing or where I am in the process.

I don't want less information. I want clear information and a way to know clearly where I am and what I'm doing.

---

### Post by sudodus on 2016-05-16
I see - so some information at each window about what to do next (or to make it very clear without having to refer to the manual).

I hope to get time to make a revamped version with a much simpler interface - so your comments are welcome :-)

---

### Post by yman on 2016-05-16
It's the design that is based on a menu that is so problematic. I think some kind of linear process would be much better.

---

### Post by sudodus on 2016-05-16
It is hard to avoid a menu 'select what you want to do' unless I make separate programs for each task, but it can be clean, not mixed with anything else.

[LIST=1]
[*]Select what you want to do
[*]Select source file (if a source file is needed)
[*]Select target device
[*]Extra choices (where relevant)
[*]Final checkpoint
[/LIST]

---

### Post by uRock on 2016-05-16
I stopped using Ubuntu's Startup Disk Creator a long time ago. I prefer to let dd  do the work. ```
sudo dd if=/home/path/to/iso/whatever.iso of=/dev/sd<drive letter>
```

---

### Post by sudodus on 2016-05-16
Yes. But dd is nicknamed 'disk destroyer' or 'data destroyer', and it deserves it. mkusb is using dd under the hood. mkusb 'only' helps making sure that you write to the correct target drive.

---

### Post by uRock on 2016-05-18
> **sudodus said:**
> Yes. But dd is nicknamed 'disk destroyer' or 'data destroyer', and it deserves it. mkusb is using dd under the hood. mkusb 'only' helps making sure that you write to the correct target drive.

dd definitely requires paying attention. I always format the drive with GParted before running the command and make note of the drive letters during the process.

---

### Post by yman on 2016-05-19
I'm trying to use mkusb-nox, but it seems stuck on this stage:
[ATTACH=CONFIG]269164[/ATTACH]

The command I used was
> sudo -H mkusb '~/Disc Images/Operating Systems/lubuntu-16.04-desktop-i386.iso' p
(~ is the path of my home directory. I changed what I wrote here for privacy)

This is the output:
> lubuntu-16.04-desktop-i386.iso: No such file or directory
'~/Disc Images/Operating Systems/lubuntu-16.04-desktop-i386.iso' does not work as a source ISO file

EDIT: Nevermind. I needed to cd to the same directory.

EDIT: The filesystem doesn't get mounted in Ubuntu, and the Acer won't boot from it. Using Disks to write the image to the USB worked better, in that at least the Acer finally booted into Xubuntu and Xubuntu fully loaded, but not without some problems, such as constantly going to sleep and not connecting to WiFi.

---

### Post by sudodus on 2016-05-19
Yes, it works to cd to the file's directory.

You discovered a bug. There is an error, when there is a space in the path to the source file. The file name itself could contain spaces and other special characters, but not the directory part of the path.

I fixed that bug in mkusb 10.6.4 and uploaded it to **ppa:mkusb/unstable**.

Thanks for finding it and telling me :-)

---

### Post by yman on 2016-05-21
I used mkusb-nox to install Lubuntu 16.04 to a USB. It worked and my System76 laptop booted from it without a hitch. The Acer however failed on loading Xorg like you said it would, but at least it got past the bootloader, which is progress. mkusb-nox was definitely a lot simpler to use. Perhaps I will try to see if I can install Lubuntu 14.04.4 and then install the missing package and then dist-upgrade to 16.04. I'll have to do a dry-run in VirtualBox first. Or maybe I'll use the OEM image. This really seems like the kind of thing that the Lubuntu team should take care of in the default release image, though.

I would recommend for mkusb to use 1 window which displays the following:
[LIST]
[*]A section for choosing the source. This is just a header saying something like "choose the disc image you would like to install to a USB flash drive:", and a widget that displayes the currently selected file along with a button to open a file chooser to select an image file.
[*]A section for choosing the destination device. This is just a header saying something like "choose the USB flash drive you would like to install to:"  and a radio-button list of available devices so that you can choose one.
[*]A section for the persistent file system option. This is just a checkbox saying something like "I would like the device to have a persistent filesystem (for live systems)" and a slider letting you choose the percentage of the free space you want to use for that. If the checkbox is ticked, the slider is enabled. If the checkbox is not ticked, the slider is disabled.
[*]An Advanced section. You have to press a ^ button to show the content of this section which includes the choice of bootloader and partition table or whatever. These are options that mkusb-nox doesn't ask about anyway.
[/LIST]
Click next and you will get a popup asking if you are sure you want to write image-file.format to device such-and-such (warning: this action will completely erase all data on device such-and-such and cannot be reversed). If you click no the popup will close and no action will be taken. You are back in the main window. If you click yes the popup will close, the action will be performed, and the main window will switch to page 2, showing the progress. All you need is a text description of what is happening. Perhaps a list of actions, with actions that have already been completed being marked with a check mark and the current action being displayed in bold letters, like this:

V action 1
V action 2
**action 3**
action 4

and also a progress bar and an estimate of time remaining.

That's about the whole thing right there. Also, the more colors and sizes you use the harder it is on the eyes and the harder it is to actually notice anything. Use little text with the system default theme and colors for both the text and the background. You don't need giant red text to warn people.

---

### Post by sudodus on 2016-05-21
1. Yes, Lubuntu 16.04 LTS is really missing the package xserver-xorg-video-intel. But I think that it will be included in the point releases, starting with Lubuntu 16.04.1 LTS late July or early August. Until then a tarball, compressed image file or installing 14.04.4 and do-release-upgrade are possible work-arounds.

2. Thanks for this detailed description of an improved graphical user interface :-)

---

