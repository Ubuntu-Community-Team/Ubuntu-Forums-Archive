---
title: "Need help with dialup in Xubuntu"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by AggieTwist on 2007-11-25
Hello everyone, I'm brand new to both the forums and Linux and am excited about my experience with both.   I downloaded the Xubuntu LiveCD the other day originally intending to try running it on an old desktop I had lying around but due to too many hardware failures I went ahead and tried it out on my laptop.  In short, system specs are : Intel Core 2 Duo, 1.5 GB RAM, 120 GB HD, 250 GB external HD...and from everything i've read that means I have way more than I need for Xubuntu but figured it'd be good to learn on.

My question is, when running from the LiveCD environment, how do I configure my dialup connection?  I generally run broadband but where I'm currently at I only have dialup access and can't figure out how to find my modem location and configure it properly.  If this has already been addressed in another post I apologized and would appreciate a redirect, if not then any advice is appreciated.  Thanks!

---

### Post by AggieTwist on 2007-11-25
Sorry for the double post but I'm going to boot back into Xubuntu and try a few more things and if it doesn't work I'll check back in a bit to see if any of yall know how to help me...thanks again...

---

### Post by ray bot on 2007-11-25
To configure dial-up, open a terminal and type sudo pppconfig.  If you're using a laptop, I'll assume you probably have a winmodem, rather than a full hardware modem.  Not all winmodems work properly with linux.  You can take a look at [http://linmodems.org/](http://linmodems.org/) to see if yours is supported.

---

### Post by AggieTwist on 2007-11-25
I'll try pppconfig command...I completely forgot to leave info about my modem...It is listed as Toshiba Software Modem but its a winmodem by Agere on COM 3.  I'm really new to Linux so as detailed as you can be in instructions would really help.  I'm a quick learner and pretty good in both Mac OS and Windows but the command line orientation of Linux is pretty new to me as i use very little command line stuff in Windows...

---

### Post by ray bot on 2007-11-25
There is also a gui for configuring this.  Go to System->Administration->Network, and, if your modem was properly detected, there should be an icon called "Modem connection".  You can configure it by selecting it and clicking on "Properties".
I think most Agere modems use the Lucent chipset, which should work fine.  You'll probably need to get the drivers from [http://www.heby.de/ltmodem](http://www.heby.de/ltmodem).
If your modem is on COM 3, then you should set your modem port to /dev/ttyS2 in the Modem tab.

---

### Post by AggieTwist on 2007-11-25
I'll try the GUI again and some of the tips from the DialupModemHowTo/SetupDialer tutorial frome the Ubuntu help forums.  I found an old external modem I had lying around too but my laptop doesn't have a serial port to hook it up without buying an adapter and since I won't be using dialup too much longer I'd prefer to do it without spending money.  I also wasn't sure if it was possible for me to connect from the LiveCD or if it had to be from HDD.  I was curious as to whether you can partition an external HD and run Ubuntu from there cuz i would consider doing that since it'd be no risk to my main drive and info.  Thanks for all your speedy replies and help!

---

### Post by ray bot on 2007-11-25
Booting from an external hard drive should be doable as long as your bios supports it.  You should check these threads for more info:
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
[http://ubuntuforums.org/showthread.php?t=226638](http://ubuntuforums.org/showthread.php?t=226638)

---

### Post by AggieTwist on 2007-11-25
well i tried using wvdialconf and wvdial and also pppconfig and pon & poff all to no avail.  Have yet to get anything to work with the GUI networking either.  I really would like to start using Xubuntu more and gradually switch over but I rely on the internet quite a bit and its just a pain to have to switch between OS everytime.  Really hoping that someone else has a solution for this but if not I may have to wait until January when I get my broadband back...

---

### Post by AggieTwist on 2007-11-25
Or are Ubuntu or Kubuntu any better at detecting or setting up internet connections? Also, how do i play mp3 files on there? They show up but don't actually start playing...Thanks!

---

### Post by ray bot on 2007-11-26
If you're still having trouble with your modem, this thread might help you: [http://ubuntuforums.org/showthread.php?t=198730&highlight=ltmodem](http://ubuntuforums.org/showthread.php?t=198730&highlight=ltmodem).  I think that's the same chipset you're using, although I'm not sure about that Toshiba bit...  It's probably worth a try anyway.

If you want to play mp3s, you first have to make sure you have all the repositories are enabled.  To do this, open a terminal and type sudo nano /etc/apt/sources.list.  If there are any lines in that file that start with "#deb" or "# deb", delete the #.  Then, press ctrl+x to exit, say yes to saving the file, and type sudo apt-get update.
Once you've done that, you can add mp3, flash, java, rar and dvd support by typing sudo apt-get install xubuntu-restricted-extras

---

### Post by AggieTwist on 2007-11-26
First off, thanks for all the effort you have put forth and all the answers although nothing has worked yet.  I'm beginning to fear that if I don't come across a solution soon that it may deter me from continuing my experiment with Ubuntu or Linux altogether.  I rely heavily on having internet access and its just not worth learning a new OS if it can't do something as simple as connecting to the internet without this much hassle.  Someone please help me come up with a solution.  Is connecting to broadband any easier or is it just as much a hassle?  Someone plz show me the light at the end of the tunnel....

---

### Post by AggieTwist on 2007-11-26
I'm just about at my wits end... Would Ubuntu be any easier to do this with than Xubuntu? Should I get 7.10 instead of Dapper?

---

### Post by AggieTwist on 2007-11-26
yes i'm triple posting in an effort to get someone's attention that can answer some of my questions...I can be patient as long as there is an end in sight but not feeling that way.

---

### Post by ray bot on 2007-11-26
I don't think using Ubuntu instead of Xubuntu would change anything, but if you're using Dapper, then getting the latest version might help.  Dapper is fairly old, and a lot of improvements have been made since then.
I think I have a lucent winmodem lying around somewhere; I'll try to find it and see if I can get it working.  If so, I'll let you know what I did.
As for broadband, it's nowhere near as difficult to get connected.  I'm not aware of any network card that doesn't work out of the box in Linux.

---

### Post by AggieTwist on 2007-11-27
Thanks again raybot, you seem to be the only person even remotely interested in helping figure this out.  I think i'm gonna go ahead and get the latest version of Ubuntu and try connecting on broadband tomorrow and if that goes well then I'll hang in there even if I can't get dialup to work since its only a month until I get my broadband back.  I'm still nowhere near figuring out compatibility between my windows documents, files and peripherals but I'm willing to experiment in that area as long as I can get it to connect to the internet.  Thanks again for everything...

---

### Post by ray bot on 2007-11-27
Ok, I found my dusty old winmodem and tried it out.  The bad news is it doesn't work out-of-the-box, even on Feisty.  The good news is I got it working quite easily, and I'm using it right now.  Here's how:

First, get the driver from here: [http://www.barrelsoutofbond.org/downloads/martian/current-full.tar.gz](http://www.barrelsoutofbond.org/downloads/martian/current-full.tar.gz)
Next, you'll need to get a few additional packages to compile the driver.  If you can somehow get Ubuntu on the internet by some other means, then typing ```
sudo apt-get install build-essential linux-headers-`uname -r`
``` should do it.  Otherwise, you'll have to manually download and install the packages.  I'm not entirely sure which dependencies need to be installed and which ones are part of the base system; I'll try to post a complete list later.

Once that's all set up, open a terminal and type the following:
```
tar -xzf martian-full-20061203.tar.gz
cd martian
make all
sudo make install
```

If that works, then the driver is installed.  You can initialize it by typing ```
sudo modprobe martian_dev
sudo martian_modem --daemon
```

After that, if all goes well, your modem will be located at /dev/ttySM0.  You can then use it with wvdial, pppconfig, NetworkManager, etc.

---

### Post by AggieTwist on 2007-11-27
this is what i got from the terminal  
ubuntu@ubuntu:~$ tar -xzf martian-full-20061203.tar.gz
tar: martian-full-20061203.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ubuntu@ubuntu:~$ cd martian
bash: cd: martian: No such file or directory
ubuntu@ubuntu:~$ make all
bash: make: command not found
ubuntu@ubuntu:~$ sudo make install
sudo: make: command not found
ubuntu@ubuntu:~$

I have access to broadband in the evenings but not where I live...I am on Xubuntu right now and it was a breeze on broadband.  Still dno how to fix the modem issue but I'm glad to find its so easy with broadband.

---

### Post by AggieTwist on 2007-11-27
still unable to get dialup to work and would still like to if I can, but just to let you know, I've upgraded to Ubuntu version 7.10 and decided to stick with it. Thanks

---

### Post by ray bot on 2007-11-28
I probably should have mentioned, before running the above commands, you have to go to the directory where you saved the file martian-full-20061203.tar.gz.  When you open a terminal, it starts off in your home directory, but that may not be where the file is.  If the file is on your desktop, then type ```
cd Desktop
``` If you can see the file's icon but are not sure in which directory it is, then right-click it, go to properties, and look beside "Location:"

---

### Post by AggieTwist on 2007-11-28
okay, that may help...the file was saved to a thumb drive since i didn't know if it could be downloaded to the desktop while runnin from LiveCD...also what is the deal with it not recognizing the "make" command? or will this be resolved by changing the location? Also, when the code you list starts on a new line does that mean that you hit "enter" or is there a return keystroke somewhere? Thanks again, you're a real lifesaver even if i never get it to work.

---

### Post by ray bot on 2007-11-28
> okay, that may help...the file was saved to a thumb drive since i didn't know if it could be downloaded to the desktop while runnin from LiveCD...
You can download files to the desktop while running from the live cd, but I wouldn't recommend it, since they will be lost when you reboot.
Thumb drives are usually mounted to /media/disk or something similar.  Try ```
cd /media/disk
``` If that doesn't work, do ```
ls /media
``` and look for something with "disk" or "usb" in it.
> also what is the deal with it not recognizing the "make" command? or will this be resolved by changing the location?
Make is not installed by default.  Running ```
sudo apt-get install build-essential
``` should fix that.
> Also, when the code you list starts on a new line does that mean that you hit "enter" or is there a return keystroke somewhere?
Yes, a new line means you should press enter.

---

### Post by AggieTwist on 2007-11-28
cool, thanks! i'll try it after my hard drive finishes defragging

---

### Post by AggieTwist on 2007-11-28
i haven't tried that again yet but was jw, i found an old hardware external modem and would just need a serial port adapter to hook it up to my laptop...would this be a much simpler solution? what type of adapters do they make?

---

### Post by ray bot on 2007-11-28
A usb to serial port adapter would probably work.  I've never used one myself, but I do believe they should work out of the box.  They probably sell them at your local computer shop; just make sure the adapter has the same amount of pins as your modem.

---

### Post by AggieTwist on 2007-11-28
just bought a new usb external modem that says it works with Linux...about to install it, only one question, it has three folders on the CD that came with it rpm, debian, and tar...which one do I use?  I think tar but you tell me.  It also says to enter my super user password but am not sure what that is either.  what is my Linux source build directory also? Lots of questions I guess but should work with this...

---

### Post by ray bot on 2007-11-28
> just bought a new usb external modem that says it works with Linux...about to install it, only one question, it has three folders on the CD that came with it rpm, debian, and tar...which one do I use?
Debian should work.  Ubuntu uses the same package manager as Debian.
> It also says to enter my super user password but am not sure what that is either.
In Ubuntu, there is no super user password.  Depending on which command it was that asked for your super user password, you can either enter the password you use to log in, or add sudo in front of the command.  One or the other should work.
> what is my Linux source build directory also?
It should be /usr/src/linux-headers-[your kernel version number].  You can get your kernel version number by entering ```
uname -r
```in a terminal.

Note that this directory will not exist if you haven't installed the linux-headers package.  So, try typing ```
ls /usr/src/linux-headers-`uname -r` -d
``` If that gives you a path, then that path is your linux source directory.  If it gives you an error message with "No such file or directory", then type ```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by AggieTwist on 2007-11-29
hey, got that new modem loaded and it works fine...unfortunately my isp's server is down today but i was connected last night. Thanks for all the help...problem SOLVED!

---

### Post by ray bot on 2007-11-29
Sweet.  I'm glad to know you got it working.  :D
Just out of curiosity, I'd be interested to know what brand/model your new modem is.  It could come in handy if I ever have to recommend a usb modem to another Linux user.

---

### Post by AggieTwist on 2007-11-29
its a Zoom usb modem...tiny little thing that measures like 2 inches long by 1 inch wide...says on the box that it works with Windows, Mac, and Linux.  Got mine for like $40 at Best Buy.

---

### Post by AggieTwist on 2007-11-29
bad news...for some reason its working in Windows still but not working in Ubuntu again...it starts dialing the number but then shuts itself off...i don't understand why it would work and then not anymore.  i tried reinstalling the drivers but that didn't work.

---

### Post by ray bot on 2007-11-30
That's odd.. I don't know why it would work one day and not the next.  What program are you using to dial (wvdial, pon, network-admin)?  I'd be curious to see what kind of error message it's giving.

---

### Post by AggieTwist on 2007-12-01
usin network-admin, not all that concerned with it anymore, tired of foolin with it, just use Ubuntu with broadband i guess... be nice to figure out but i don't feel like foolin with it anymore for awhile...might uninstall it and reinstall all over again and see what happens

---

### Post by Bartender on 2007-12-01
Aggie -
The modem set-up under "Networking" hasn't worked since Dapper.

[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

A friend tried one of those Zoom 3095's when they first came out and was unable to get it recognized.  Zoom was supposedly working on their drivers.  I'd sure like to know if you can get yours going because it's a neat little gizmo.

pppconfig is the most basic, trouble-free software for dialing.  Try that first.

---

### Post by AggieTwist on 2007-12-01
it worked when i first installed it, then when it stopped i tried pppconfig and didn't work. i'll fool with it more sometime

---

