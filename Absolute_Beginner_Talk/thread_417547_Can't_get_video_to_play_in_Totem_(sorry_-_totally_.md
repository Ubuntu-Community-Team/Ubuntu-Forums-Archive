---
title: "Can't get video to play in Totem (sorry - totally new to this!)"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Neil_The_Newbie on 2007-04-21
I am running Ubuntu 6.10 and can't play restricted format video files.

I followed the info listed here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and did the stuff they said:

      Ensure the relevant repositories are enabled. Click System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes. When you close the window, click Reload.
    *

      Install the packages. While you could install packages individually using Synaptic, here is one case where any Ubuntu user can save a lot of time by using the command line. Quit out of Synaptic, then click Application &#8594; Accessories &#8594; Terminal and paste the following command:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

but after that got the message:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ogle-gu

Any ideas?!

Thanks for any help.

---

### Post by nudnik on 2007-04-21
> **Neil_The_Newbie said:**
> I am running Ubuntu 6.10 and can't play restricted format video files.

I followed the info listed here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and did the stuff they said:

      Ensure the relevant repositories are enabled. Click System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes. When you close the window, click Reload.
    *

      Install the packages. While you could install packages individually using Synaptic, here is one case where any Ubuntu user can save a lot of time by using the command line. Quit out of Synaptic, then click Application &#8594; Accessories &#8594; Terminal and paste the following command:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

but after that got the message:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ogle-gu

Any ideas?!

Thanks for any help.

Looks like you left the "i" off the end when you copied and pasted:)  I think its likely that simple.

---

### Post by bagguley on 2007-04-21
If you're completely new to ubuntu and linux easyubuntu or automitix may be what you're looking for. They install stuff like restricted codecs from a windows like interface. I found it useful to use it before i got use to the command line interface.

---

### Post by Neil_The_Newbie on 2007-04-21
ahem!

thanks for that

i got further but then i got:

Media change: please insert the disc labeled                                   
 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)'
in the drive '/cdrom/' and press enter

The problem is that i installed ubuntu from an external dvd writer - which is now NOT working. :-(

how do i point it to my other (internal) dvd drive?

Thanks for the assistance. I'm a total newbie!

---

### Post by nudnik on 2007-04-21
> **Neil_The_Newbie said:**
> ahem!

thanks for that

i got further but then i got:

Media change: please insert the disc labeled                                   
 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)'
in the drive '/cdrom/' and press enter

The problem is that i installed ubuntu from an external dvd writer - which is now NOT working. :-(

how do i point it to my other (internal) dvd drive?

Thanks for the assistance. I'm a total newbie!

Have you tried just placing the disc in the internal drive? That should work....in theory....but remember the mascot...see below.

---

### Post by Neil_The_Newbie on 2007-04-21
yes - i've tried that - but it doesnt seem to look for it there though. frustrating!

:-(

---

### Post by nudnik on 2007-04-21
> **Neil_The_Newbie said:**
> yes - i've tried that - but it doesnt seem to look for it there though. frustrating!

:-(

Power down, unplug the external DVD drive. Reboot with only the internal connected and try again. It might actually read from the internal drive automatically given no other choice.

---

### Post by Neil_The_Newbie on 2007-04-21
I have tried that. But unfortunately it didnt work. its still looking for the disk in that other drive.

aggh!

---

### Post by nudnik on 2007-04-21
> **Neil_The_Newbie said:**
> I have tried that. But unfortunately it didnt work. its still looking for the disk in that other drive.

aggh!

/dev/scd0  The preceding is the link to an internal cd/dvd drive on a typical system...I think.  You will need to reprogram your installation using the command line, but, unfortunately, I've never rewritten the links to a disk manually, so you will need a more skilled Ubuntite than I. Sorry I cant be of more help.

---

### Post by Neil_The_Newbie on 2007-04-21
hey no problem. thank you anyway.

maybe i should try that automitix - whatever that is?!

thanks again for your help

---

### Post by Michaelt74 on 2007-04-21
This may help, check out the part on Multimedia codecs and streaming

[http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

---

