---
title: "Poor performance from Ubuntu?"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by Animus on 2005-11-03
I had another thread like this, but have decided to make another one in its stead, so I can see if anyone else has any problems like this...

I've started using Ubuntu quite regularly, as until I get my other HD, it's all I have on my desktop.  I'm settling in nicely with how things work, and the apt-get and synaptics package manager work well for me.  However, Ubuntu has been running sluggishly lately, and was wondering if anyone might know why that would be.

Are there programs with memory leaks in Ubuntu?  I'm going to restart and see how that works.  I use Firefox, Amarok, and Gdesklets (starter bar) fairly often, would they affect performance that much?

My specs are as follows:

MSI neo2 platinum nforce 3 250gb Ultra mobo
AMD 3500+ Athlon 64
1 Gig of Corsair 3200 Ram
an 80 gig Generic HD
And then  a CD burner, and a DVD drive

Ubuntu really should not be running this sluggishly, it's like the system is not recognizing all of my memory.  Is there anyway to check and see what Ubuntu and recognizxing your hardware as? (like system in windows)

Ubuntu also crashed yesterday, which was odd.  Also, does anyone know how to fix the refresh rate?  I'm stuck at 60hz, and it's giving me headaches, and no one seems to know how to fix it.  I'm using a Generic Dell monitor thats about 4-5 years old, 17inches in diameter.  I don't know specifics, and unless there is a way to get them in Ubuntu, I will continue not to know them.  

So, if you have any info, performance tweaks, etc, feel free to tell everyone about them here.  

(I am also using the 686 kernal, if that makes a difference)

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=Animus]I had another thread like this, but have decided to make another one in its stead, so I can see if anyone else has any problems like this...

I've started using Ubuntu quite regularly, as until I get my other HD, it's all I have on my desktop.  I'm settling in nicely with how things work, and the apt-get and synaptics package manager work well for me.  However, Ubuntu has been running sluggishly lately, and was wondering if anyone might know why that would be.

Are there programs with memory leaks in Ubuntu?  I'm going to restart and see how that works.  I use Firefox, Amarok, and Gdesklets (starter bar) fairly often, would they affect performance that much?

My specs are as follows:

MSI neo2 platinum nforce 3 250gb Ultra mobo
AMD 3500+ Athlon 64
1 Gig of Corsair 3200 Ram
an 80 gig Generic HD
And then  a CD burner, and a DVD drive

Ubuntu really should not be running this sluggishly, it's like the system is not recognizing all of my memory.  Is there anyway to check and see what Ubuntu and recognizxing your hardware as? (like system in windows)

Ubuntu also crashed yesterday, which was odd.  Also, does anyone know how to fix the refresh rate?  I'm stuck at 60hz, and it's giving me headaches, and no one seems to know how to fix it.  I'm using a Generic Dell monitor thats about 4-5 years old, 17inches in diameter.  I don't know specifics, and unless there is a way to get them in Ubuntu, I will continue not to know them.  

So, if you have any info, performance tweaks, etc, feel free to tell everyone about them here.  

(I am also using the 686 kernal, if that makes a difference)[/QUOTE]


To change refresh rate use this command:

> sudo dpkg-reconfigure xserver-xorg

It has a simple mode where you select the monitor size and it guesses the refresh rate. Or if you know what it is you can use the middle option and set it. The overall specs do not matter, just that one. If you don't know....well....

As far as performance your problem is probably Firefox. On Linux (maybe just Ubuntu) its a ram-eating, CPU wasting, computer crashing pig. The Windows version is the most developed one and it shows. We have talked about this on the forum so I'll sum it up for you: most of the problems in the Linux version are fixed with the next release. Either use the beta version of that (guide is in how to forum), use the very nice epiphany-browser (installable in synaptic) or buy more RAM to make Firefox happy. 

I hope I helped. If not, feel free to PM me.

---

### Post by mlomker on 2005-11-03
The two things that I'd do are to make sure your IDE settings are correct using **hdparm** and run **top** in a terminal to see if something is using up your resources.

```

mlomker@mlomkernote:/$ sudo hdparm -v /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 117210240, start = 0

```

---

### Post by Animus on 2005-11-03
I've run the xserver config program before to no effect.  However, I will look into acquiring or updating my web browser, thanks for your inuput.

---

### Post by mlomker on 2005-11-03
[QUOTE=Animus]I've run the xserver config program before to no effect.  However, I will look into acquiring or updating my web browser, thanks for your inuput.[/QUOTE]

You should really do some searches online for your monitor's model number or somehow find the manual.  It would help a lot of you knew the frequency capabilities of the monitor.  [Here's a post]("http://ubuntuforums.org/showthread.php?p=417734&posted=1#post417734") regarding modelines, and that may be what you need to try next.

---

### Post by aminalshmu on 2005-11-03
to check for memory leaks, run "ps aux" or "top" in a terminal. i've been having issues on a lot of machines with gamin/gam_server hogging memory and cpu. stupid buggy software that comes with gnome...

---

### Post by gravediggers on 2005-11-03
[QUOTE=Animus].....  Is there anyway to check and see what Ubuntu and recognizxing your hardware as? (like system in windows)[/QUOTE]

Someone pointed this out to me the other day. Go to the terminal and use the lshw tool (you might have to do it as root or via sudo, depending how you are set up). I think the version I used was OK, but not as comprehensive as I am used to in Windows.

---

### Post by Teroedni on 2005-11-03
Ubuntu also crashed yesterday, which was odd. Also, does anyone know how to fix the refresh rate? I'm stuck at 60hz, and it's giving me headaches, and no one seems to know how to fix it

In your former post here you have been asked twice to post your xorg
[http://www.ubuntuforums.org/showthread.php?t=84351](http://www.ubuntuforums.org/showthread.php?t=84351)

please do it and we will fix your 60hz problem;)


As for your unstable system. Please dont use i686

Use either k7(32bit)
or the AMD64 Bits verison.
Ive running k7 kernel on a ML30(Turion 64 bits) and it is stable and fast;)
The only thing who is unstable is firefox. Firefox work great until you choose to play video inside it.Then it die:( You be better off by Xine Ephiany and/or Opera:)


Also if you are overcloking it may be a cause.

---

### Post by Animus on 2005-11-03
I didn't see that request to post the file, I can't now because I'm in my laptop in windows.  I would be willing to switch to opera...would anyone know where a guide showing me how to would be located?

I'm not overclocking, so that shouldn't be as issue.

Don't use the 686 kernal?  But in a previous post about performance, I was specifically instructed to use that kernal...however, you seem to know what you're talking about...how woud I go about installing the K7 kernal?  I don't really want to switch to the 64 bit kernal, as many programs have yet to be optimized, and I've heard there are still issues with 64 bit releases, and I'm looking for the most stable system possible.

Alright, tonight I'll post the xorg file, and if it's alright, from there we can try and resolve this monitor issue.  Maybe we can get Opera installed, It'll be compatible with my system once I switch the kernal (again) right?  How does it compare to mozilla, in so far as speed and customobility is concerned?  Anyways, thanks for being of such great help, I'll post again once I get back to my desktop.

---

### Post by mlomker on 2005-11-03
> how woud I go about installing the K7 kernal? 

If you are running an AMD chip then that's what you should use.  Do a search on **linux-image** in Synaptic.

---

### Post by janne5011 on 2005-11-03
Operas "tab browsing is excellent:) 
As a linux newbie i use the "static" version since it works right on, the other version is problematic: error with plugins....:rolleyes: 
I think I improve with Opera...

---

### Post by gt24 on 2005-11-03
[QUOTE=mlomker]If you are running an AMD chip then that's what you should use.  Do a search on **linux-image** in Synaptic.[/QUOTE]

Yep, you search for it, mark it, let it install, reboot.  On your GRUB menu, you have a new option for your K7 kernel.  Select it and boot.  If you get back to an interface and all is fine in Linux land, then you can optionally go back to Synaptic, search once again for linux-image, and remove the i686 kernel.  However, if you don't want to, you don't have to and thus you can have other kernels on your system as a backup.  I'm not too sure how to make one GRUB entry the default entry over another (but I'm sure you can ask around here and get an answer pretty quickly).

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=mlomker]If you are running an AMD chip then that's what you should use.  Do a search on **linux-image** in Synaptic.[/QUOTE]

No. One want to go one step farther. You should install the:

> linux-k7

package. Command:

> sudo apt-get install linux-k7


Just installing the image pacakge can really mess things up. For 686 too. YOu must install the:

> linux-686 

package

---

### Post by mlomker on 2005-11-03
> Just installing the image pacakge can really mess things up. For 686 too. YOu must install the:


Ah, that includes the linux-restricted package for the video and madwifi drivers.  You're correct that most people would want that.

Installing that would actually hose my box because I use the 8.18.8 ATI drivers.  I wish there were more absolutes in this whole process, but a lot of setups are unique.

---

### Post by bluebyt on 2005-11-03
[QUOTE=mlomker]The two things that I'd do are to make sure your IDE settings are correct using **hdparm** and run **top** in a terminal to see if something is using up your resources.

```

mlomker@mlomkernote:/$ sudo hdparm -v /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 117210240, start = 0

```[/QUOTE]

Mine is in 16-bit, is it suppose to affect the performance?
 IO_support   =  0 (default 16-bit)

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=mlomker]
Installing that would actually hose my box because I use the 8.18.8 ATI drivers.  I wish there were more absolutes in this whole process, but a lot of setups are unique.[/QUOTE]

So you can't install those with custom installed ATI drivers eh?

---

### Post by mlomker on 2005-11-03
[QUOTE=poofyhairguy]So you can't install those with custom installed ATI drivers eh?[/QUOTE]

No.  The linux-restricted-modules package is new to Breezy and Septor (the ATI packager for Ubuntu) and I struggled for over a week figuring out a couple issues (64-bit Xorg updates also broke fglrx altogether).  The linux-restricted package includes the older 8.16.20 driver and it'll overwrite your custom-installed driver on every reboot if it is installed.

The problem is that the Breezy-included driver has a bug that causes it to not work on a variety of widescreen LCD displays.

---

### Post by Animus on 2005-11-03
"sudo apt-get install linux-k7" 

I get "E: Couldn't find package linux-k7."

I do have repositories enabled.  This is similar to what I did to get my i686 kernal.  Any idea why synaptics wouldn't be able to pick it up?

Also, posted my xorg file in the other thread.  Thanks for the heads up that the thread was still going, I'd given up on it!

EDIT: Got it working, left a period on the end of k7 lol.  Its installing right now.  I don't need to uninstall the previous kernal do I?

---

### Post by mlomker on 2005-11-04
> I don't need to uninstall the previous kernal do I?

It isn't required.  It'll just take up a little space and add a few extra entries to your grub menu.

---

### Post by Animus on 2005-11-04
Would anyone here know how to create an icon for firefox?  I uninstalled it after I put opera in, and now I'm trying to install The Release Candidate, which I have.  However, I have to execute it through the terminal, and there are no icons present for it.  Anyone have any ideas?

---

### Post by Animus on 2005-11-04
bump

---

### Post by Teroedni on 2005-11-04
Application Menu editor;)

---

### Post by Animus on 2005-11-04
How do i add it with that?  It's installed to the opt folder in the file system, and I can't find a way to make an entry with it.

---

