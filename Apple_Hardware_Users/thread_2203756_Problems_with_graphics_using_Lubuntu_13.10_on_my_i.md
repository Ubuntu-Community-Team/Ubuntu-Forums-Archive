---
title: "Problems with graphics using Lubuntu 13.10 on my iMac G4 700MHz"
date: 2014-02-04
forum: Apple Hardware Users
---

### Post by richardocarroll7 on 2014-02-04
I am looking to install Lubuntu 13.10 on my old PPC iMac g4 700MHz, but it won't even attempt to boot due to the graphics driver. I was able to successfully fix the graphics driver issues using the instructions on this link:
[http://ubuntuforums.org/showthread.php?t=2131644](http://ubuntuforums.org/showthread.php?t=2131644)

but they do not work on anything other than 12.04. Is there any way to install Lubuntu 13.10 and be able to swap the nouveau driver for the older nv driver or am I stuck at 12.04. I would use 1204, but 12.04 in Lubuntu isn't an LTS version so it lost support and Regular Ubuntu 12.04 is almost unusable due to it is so slow that it's funny it even runs on it because you move a window and you can just about watch each pixel move. The only way to get it to boot is to type in at the second stage of yaboot is "Linux nouveau.modeset=0". I did try typing in "Linux nouveau.noaccel=1", but that doesn't work. With the current nouveau driver, if I try to boot normally, it will start to boot, but once the graphics driver boots, part of the screen is white and the other part (which is random each time) will do some sort of gradient green stripes and fade away. If you guys want, I can take a photo of it if you don't know what I am talking about. I just don't know what to do, I see plenty of instructions on how to do it in 12.04, but none in anything newer. If you guys need any more information, please let me know as for I really need to get this fixed. Thank you for reading this and I hope you know how to fix it!

---

### Post by rsavage on 2014-02-07
To compile:

Go to [http://packages.debian.org/sid/xserver-xorg-video-nv](http://packages.debian.org/sid/xserver-xorg-video-nv)

Download the three source files and place them in a new folder (*the name of which should have no spaces*).

Open a terminal in that folder and run 

```

sudo apt-get update
sudo apt-get install build-essential fakeroot dpkg-dev
dpkg-source -x *.dsc

```

That will create a new folder called xserver-xorg-video-nv-2.1.20

In that folder open the file debian/control

Change the line

Architecture: kfreebsd-any hurd-any

to 

Architecture: any

Save the file.

Open a terminal in the xserver-xorg-video-nv-2.1.20 folder

Run the commands

```

sudo apt-get install debhelper pkg-config xserver-xorg-dev x11proto-video-dev x11proto-core-dev x11proto-fonts-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev dpkg-dev automake libtool xutils-dev libdrm-dev x11proto-xf86dri-dev quilt

dpkg-buildpackage -rfakeroot -b -uc

```

To install:

```

cd ..
sudo dpkg -i *.deb

```

p.s. have you seen [http://ubuntuforums.org/showthread.php?t=2079873&p=12336938#post12336938](http://ubuntuforums.org/showthread.php?t=2079873&p=12336938#post12336938) ?

Also, I'm not entirely sure how useful nv will be in very recent versions of *ubuntu.  You may find 12.04 is the better (faster) option and just compile any updates (e.g. pcmanfm) yourself.

---

### Post by richardocarroll7 on 2014-02-07
> **rsavage said:**
> To compile:

Go to [http://packages.debian.org/sid/xserver-xorg-video-nv](http://packages.debian.org/sid/xserver-xorg-video-nv)

Download the three source files and place them in a new folder (*the name of which should have no spaces*).

Open a terminal in that folder and run 

dpkg-source -x *.dsc

That will create a new folder called xserver-xorg-video-nv-2.1.20

In that folder open the file debian/control

Change the line

Architecture: kfreebsd-any hurd-any

to 

Architecture: any

Save the file.

Open a terminal in the xserver-xorg-video-nv-2.1.20 folder

Run the commands

sudo apt-get update

sudo apt-get install build-essential fakeroot dpkg-dev debhelper pkg-config xserver-xorg-dev x11proto-video-dev x11proto-core-dev x11proto-fonts-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev dpkg-dev automake libtool xutils-dev libdrm-dev x11proto-xf86dri-dev quilt

dpkg-buildpackage -rfakeroot -b -uc

To install:

cd ..
sudo dpkg -i *.deb

p.s. have you seen [http://ubuntuforums.org/showthread.php?t=2079873&p=12336938#post12336938](http://ubuntuforums.org/showthread.php?t=2079873&p=12336938#post12336938) ?

Also, I'm not entirely sure how useful nv will be in very recent versions of *ubuntu.  You may find 12.04 is the better option and just compile any updates (e.g. pcmanfm) yourself.

I have encountered a problem with your instructions. When I download the three files and stick them in a folder, when I went into the terminal and changed directories to the folder with those files using the cd command, the dpkg-source -x *.dsc command pulled up an error. The error said "dpkg-source: error: syntax error in xserver-xorg-video-nv_2.1.20-2.dsc at line 1: line with unknown format (not field-colon-value)", I am not sure what that means as for I don't have that much experience in Linux as is. If it counts for anything, I wasn't able to download the .dsc file due to when I clicked on it, it gave me some sort of code I assumed to be the contents of the file, so I copied and pasted it into TextEdit on my Mac and saved it as a .dsc file and brought it to the iMac via a USB thumb drive. I am not sure if the file is incorrect or if I am incorrect.

I did try the instructions from the link [http://ubuntuforums.org/showthread.php?t=2079873&p=12336938#post12336938](http://ubuntuforums.org/showthread.php?t=2079873&p=12336938#post12336938), they didn't work for some reason so I just gave up and installed from the alternate ISO of Lubuntu 13.10.

---

### Post by rsavage on 2014-02-08
> **richardocarroll7 said:**
> If it counts for anything, I wasn't able to download the .dsc file due to when I clicked on it, it gave me some sort of code I assumed to be the contents of the file, so I copied and pasted it into TextEdit on my Mac and saved it as a .dsc file and brought it to the iMac via a USB thumb drive. 

When this happens you can, in Firefox, right click on the link and select "Save link as.." from the menu.  If you do this I think it will work.  The way you did it would probably work in Linux, but I've had problems doing it that way between Windows and Linux and it is probably that same between a Mac and Linux.

I've slightly adjusted the instructions just to make absolutely sure you have that correct packages in place.

AFAIK, you are the first to use nv in 13.10, so there is no guarantee this will work.  As I hinted at before, the driver is pretty old and may not be as fast in new versions of linux (things like abiword may be slow - that is me speculating btw).

You will also have to create an xorg.conf file like you did in 12.04.

Lastly, although Lubuntu is not officially an LTS release, all the underlying stuff is.  So I wouldn't be too concerned about its status.  I compile the Mate desktop myself (the same as Linux Mint) and there are very few updates to the actual desktop (a good thing too!).  I know Lubuntu in 12.04 is not the greatest (it used to be a bit crash-tastic), but I'm sure it can be tweaked to be better behaved.

---

### Post by richardocarroll7 on 2014-02-08
> **rsavage said:**
> When this happens you can, in Firefox, right click on the link and select "Save link as.." from the menu.  If you do this I think it will work.  The way you did it would probably work in Linux, but I've had problems doing it that way between Windows and Linux and it is probably that same between a Mac and Linux.

I've slightly adjusted the instructions just to make absolutely sure you have that correct packages in place.

AFAIK, you are the first to use nv in 13.10, so there is no guarantee this will work.  As I hinted at before, the driver is pretty old and may not be as fast in new versions of linux (things like abiword may be slow - that is me speculating btw).

You will also have to create an xorg.conf file like you did in 12.04.

Lastly, although Lubuntu is not officially an LTS release, all the underlying stuff is.  So I wouldn't be too concerned about its status.  I compile the Mate desktop myself (the same as Linux Mint) and there are very few updates to the actual desktop (a good thing too!).  I know Lubuntu in 12.04 is not the greatest (it used to be a bit crash-tastic), but I'm sure it can be tweaked to be better behaved.

Now I have another problem with the instructions. They all worked perfectly and I made the xorg.conf file and I o  went to reboot, it still won't boot without the nouveau.modeset=0 command and when I do that command at the second boot stage, it freezes at the splash screen with what I believe to be an error on the side that says ".saned disabled: edit /etc/default/saned                    [ OK ]", not sure what that means. I am almost ready to take your advice and revert it to 12.04 and compile the updates myself, even though I don't know how to do that. Would you mind giving instructions on how to do that if you can't figure out why this error is showing up. Is it possible that it's because I put the file on the Desktop and complied it from the desktop?

---

### Post by rsavage on 2014-02-09
I'm sorry I don't know what the problem is.  I don't think that message is anything to do with the problem, just probably the last thing to be written to the screen.  

I think you should always use nouveau.modeset=0 (or nomodeset) with the nv driver.

If you press CTRL-ALT-F1 do you get to a text login?  Is there anyway to post up you Xorg.0.log, dmesg, syslog or lightdm logs?  See [http://askubuntu.com/questions/126065/after-upgrading-to-12-04-i-cant-get-to-the-login-screen](http://askubuntu.com/questions/126065/after-upgrading-to-12-04-i-cant-get-to-the-login-screen)

It would be interesting to know if the debian sid package works in 12.04.  If it doesn't, then I guess there is a problem with one of the recent commits.  You would have to figure it out from here [http://cgit.freedesktop.org/xorg/driver/xf86-video-nv/log/](http://cgit.freedesktop.org/xorg/driver/xf86-video-nv/log/) .  Taking a quick look, the way KMS is detected has been changed so that is something I would maybe look at first.  It is pretty involved stuff for a beginner.

We know the natty version of nv works in 12.04 when re-compiled [https://launchpad.net/ubuntu/+source/xserver-xorg-video-nv/1:2.1.17-3ubuntu7](https://launchpad.net/ubuntu/+source/xserver-xorg-video-nv/1:2.1.17-3ubuntu7), but this won't work in 12.10 and beyond.

A guide to compiling is here [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_compile_a_package.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_compile_a_package.3F) .  It's basically what you've already done.  I'm afraid I don't have time to give you anymore advice on that. I would recommend downgrading abiword to the 11.10 version.  The latest pcmanfm has a built-in search facility I believe, and if you compiled that you could get rid of the rubbish catfish search program (that doesn't work for me in 12.04).  Those changes should give you something better in 12.04.

---

### Post by este.el.paz on 2014-02-09
> **rsavage said:**
> I'm sorry I don't know what the problem is.  I don't think that message is anything to do with the problem, just probably the last thing to be written to the screen.  

I think you should always use nouveau.modeset=0 (or nomodeset) with the nv driver.


We know the natty version of nv works in 12.04 when re-compiled [https://launchpad.net/ubuntu/+source/xserver-xorg-video-nv/1:2.1.17-3ubuntu7](https://launchpad.net/ubuntu/+source/xserver-xorg-video-nv/1:2.1.17-3ubuntu7), but this won't work in 12.10 and beyond. 

@r:

Thanks for posting over here to help out . . . appreciate the link from moore.bryan's thread . . . just posting here to support your thought that 12.04 w/ the nv driver is probably the best choice right now for the G4 iMac; although it seems that Bryan is claiming that he got the nv driver working with 13.10 . . . .  But he seems to be unhappy with the speed of XFCE in comparison to OpenBox.  I did test out the Openbox desktop once I realized that the grey-black desktop was actually a desktop, it does seem to launch apps a bit faster, but the trade off is a lack of eye flash.  Openbox gets installed along with the Lubuntu DE.

I'm also not sure if it's necessary to use or type in "nomodeset" each time in 12.04 . . . it's been awhile since I did the install on my iMac, but I think I've got the very simple xorg.conf file that "str8bs" helped me with to get around the various video/graphics half screen/ black screen issues . . . with nv driver retro-compiled and set in the xorg.conf file for "nv" there have been no video problems . . . in 12.04 Xu/Lu . . . .  I don't have time either to mess around playing with 13.10, I will wait for the next LTS that might be compatible with PPC . . . be it Lubun or Xu or Openbox.  It might be nice to have a little more speed, but it's not worth the hassle that is involved getting the iMac to run Linux . . . much harder than getting the rsavage 12.04 version set up on my iBook with the radeon driver . . . more or less ran straight outta the box . . . very easy, no xorg.conf set up, no nv driver set up--straight, no chaser.

e.e.p.

---

### Post by richardocarroll7 on 2014-02-09
Well, I mostly gave up on trying to get 13.10 onto the G4, I think I will just stick with 12.04. Does anyone know how to get the latest LXDE updates since I think that's the only thing that doesn't get LTS updates. If there is any other pieces of a lubuntu that doesn't get LTS, let me know, but I think that's it, but is there a way to get updates for that or is it impossible to get current LXDE updates on Lubuntu 12.04?

---

### Post by este.el.paz on 2014-02-10
> **richardocarroll7 said:**
> Well, I mostly gave up on trying to get 13.10 onto the G4, I think I will just stick with 12.04. Does anyone know how to get the latest LXDE updates since I think that's the only thing that doesn't get LTS updates. If there is any other pieces of a lubuntu that doesn't get LTS, let me know, but I think that's it, but is there a way to get updates for that or is it impossible to get current LXDE updates on Lubuntu 12.04?

@rc7:

Probably the best decision for a first time install of Linux on an iMac is the 12.04 option . . . although as I mentioned it looks like moore.bryan got 13.10 working, but it seems like he's a long time linux user and likely knows where to find what he needs . . . .  I found that Xubuntu 12.04 has the cairo dock already installed, and then I added the LXDE DE using "synaptic package manager/handler" . . . synaptic will show you the packages that will work with your machine or OS.  However, the guys that know what they are doing like rsavage can seem to get the latest packages to work with the older base system, etc . . . otherwise, for GUI guys like me, either just going with synaptic or running the "sudo apt-get update" command followed by "sudo apt-get upgrade" or if it looks like a kernel upgrade is "being held back" then run "sudo apt-get dist-upgrade" . . . and then click "y" for the answer to "Do you want to install these packages?" . . . and just let the Terminal run the install . . . and "Be Happy" with it.

Otherwise, if you go to the LXDE web site you might be able to find the packages for the 13.10 OS, and possibly download them and then "extract" them and possibly get them to work with 12.04 . . . but that might not work; you'd have to get someone else to give some details on that . . . .  Keeping in mind that the iMac hardware is not at all up to the present web standards where 4 GB of RAM might be needed, and the processor is not anywhere close to the 2 GHz, etc . . . meaning that . . . the 12.04 OS is LTS until 2017???? so that means kernel updates will be maintained . . . and it's OK for the general messing around . . . it's just not overly flashy.  We'll see if the 2014 version of 'buntu that should be LTS will be backported to PPC and whether it will be possible to get it to work with the iMac; or just let 12.04 run until the machines die a natural death of old age, etc.  Best of luck with it . . . .

e.e.p.

---

### Post by rsavage on 2014-02-12
> **richardocarroll7 said:**
> Well, I mostly gave up on trying to get 13.10 onto the G4, I think I will just stick with 12.04. Does anyone know how to get the latest LXDE updates since I think that's the only thing that doesn't get LTS updates. If there is any other pieces of a lubuntu that doesn't get LTS, let me know, but I think that's it, but is there a way to get updates for that or is it impossible to get current LXDE updates on Lubuntu 12.04?

If you want bleeding edge stuff then you can find it here [https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily/](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily/) .  This should compile okay without problems.

However, I would recommend you compile the versions from 13.10.  You may have to do a bit of fiddling to get them to compile - for example, if you are not upgrading everything then with libfm/pcmanfm you need to change a build dependency: libmenu-cache-dev to libmenu-cache1-dev.  You do this in the 'rules' file in the debian directory.

The only reasons to compile something are: there is a security flaw with the version you have and it is not going to get fixed by the packagers, the version you have doesn't work, or you just desperately want the latest thing.  If it works then just leave it as it is. 

Back to nv - if you want it then contact the packagers/maintainers of the driver and pick their brains.

---

### Post by rsavage on 2014-02-12
> **este.el.paz said:**
> I'm also not sure if it's necessary to use or type in "nomodeset" each time in 12.04 . . . it's been awhile since I did the install on my iMac, but I think I've got the very simple xorg.conf file that "str8bs" helped me with to get around the various video/graphics half screen/ black screen issues . . . with nv driver retro-compiled and set in the xorg.conf file for "nv" there have been no video problems . . . in 12.04 Xu/Lu . . . .  

I would recommend you use nomodeset (turning off kms).  Although the feedback on this forum seems to have been that it doesn't matter, reading the code for nv it says there could be problems with kms.  Indeed the nv driver may not actually load with kms on.  It makes me wonder if people are using (unknowingly) an fbdev/nouveaufb combination when they don't use 'nomodeset' (which would be slow).  So better to turn off kms and use one of the legacy framebuffers so that you have suspend (instructions are in the FAQ).

---

### Post by rsavage on 2014-02-12
Attached is an updated pcmanfm powerpc deb for 12.04 (you need to install the libfm ones too)

---

