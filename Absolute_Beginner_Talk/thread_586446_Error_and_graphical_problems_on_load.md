---
title: "Error and graphical problems on load"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by echo404 on 2007-10-22
After loading the Ubuntu main menu and checking the disk for errors i selected the first option to try to install it and after the bar was fully loaded it displayed four lines of text and the word ok after each, at this point my display started going in and out every few seconds making the text itself very hard to read, and then after a little bit I was given the following error:

bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed

My display continued to go in and out while this error came up a few times until i got a second error telling me my display was having issues and then aborted the install process.

The installation i was trying to do was on a second hard drive set up as a slave on my second IDE, this hard drive is only an 8 gig drive salvaged from my original xbox so there may be computability issues as i don't know the specs on the hard drive, but since i selected nothing to do with this drive i doubt that was the problem.

I later tried to run Ubuntu directly from the live cd but I received the same problem again, with the same display issues.

As for my display issues it may be related to my video card, the ATI all-in-wonder 1800, since i'm not even sure if the card is computable with Ubuntu.

As for the rest of my system specs as they may be needed,
My Motherboard is a LanParty nf4, by DFI
My Processor is an AMD Athlon 64 Processor
I have a Gigg of ram

Any help that can be given to rectify the problem would be much appreciated, Thank you for your time : )

---

### Post by Vansinnesvisan on 2007-10-22
Does your computer use wireless networking card? Based on a  Broadcom chip? I think that error is common for a wireless network card. Ubuntu, I believe, installs the open source driver for your video card by defaul. I'm not certain your card is supported under the xfree ATI driver. It is supported with the proprietary "fglrx" driver.  

You could install Ubuntu under a sort of compatibility mode with mesa driver then install the fglrx driver through the Restricted Drivers program or Synaptic.

One possible way to do this is to boot from the livecd, select install from the menu, then press Alt+Ctrl+F1 to get to a command line. Then type "sudo dpkg-reconfigure xserver-xorg". Select mesa from the list of video card drivers. Then continue through answering the questions. When finished press Alt-Ctrl-F7 to leave the command line. Then, Alt+Ctrl+Backspace to reboot X. 

Then you should have a working graphical interface. Install the fglrx driver via Synaptic or the Restricted Drivers program and reboot X again with Alt-Ctrl-Backspace.

The hard drive might be formatted NTFS or perhaps FAT32, if it came from an Xbox. I think Ubuntu comes with a NTFS-3g driver, so it should be able to read it. But it will likely need to be formatted during the installation process.

---

### Post by pndragon on 2007-10-22
> bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed
I'm having the same problem on an HP Pavillion dv9628nr laptop with, obviously, a Broadcom wireless card. I am trying to install Feisty in a dual boot from the AMD 64 liveCD.  

This is my first time dealing with wireless of any kind and any assistance would be most appreciated.

--- Jim

---

### Post by ugly_b on 2007-10-22
> **pndragon said:**
> I'm having the same problem on an HP Pavillion dv9628nr laptop with, obviously, a Broadcom wireless card. I am trying to install Feisty in a dual boot from the AMD 64 liveCD.  

This is my first time dealing with wireless of any kind and any assistance would be most appreciated.

--- Jim

For a little help with the dv9628nr laptop, see my posts here [http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

Cheers,
[www.WheresMyStar.com](www.WheresMyStar.com)

---

### Post by echo404 on 2007-10-22
I do have a wireless card in my machine right now from a while ago, but i make no use of it as my system is now wired directly into my router, i'll remove it as it no longer serves a purpose and hopefully that will help fix that problem.

as for my hard drive the data on it is no use to me anymore since my xbox power supply decided to catch fire... so reformatting it is no issue

now for my video card drivers, most of what you said went over my head. From what i understood of it, you want me to install a temporary driver that way i can finish my install correctly without any graphical problems like i'm experiencing, and then go back afterward to install a more permanent driver?

If thats the case (or even if it isn't i guess) could you be more specific as to exactly what i have to do, or direct me to a place with detailed instructions.


I also failed to mention in my original post that the 8 gig drive is on my second IDE because my first hard drive contains Windows XP with all my documents and stuff, which i'd like to keep intact, and after a successful Ubuntu install be able to choose which OS to use. Not sure if that will affect anything but it might so i'm throwing it out there.

---

### Post by echo404 on 2007-10-22
Ok first off this was going to be an edit but it would have been a big one and i didn't want the information to be confused with previous stuff.

I went in and removed my wireless network card, and instead of the xbox hard drive (because after doing further research on it i found that it is locked and cannot be used in an average computer) i'm now using a 20 gig hard drive that i just got back from a friend, so now there is no possible compatibility issues with it

Ok I retried clicking on the first option on the Ubuntu screen the "start or install" and got to the same part as before (the orange part goes back and fourth, then the bar fills up and i progress to a screen with four lines of text with "ok" after each of them). Removing the wireless network card solved the error i had been getting, bu my display keeps going in and out until i get an error warning me my display is acting up and recommends aborting whatever i was doing.

So i believe the culprit is my video card (ATI all-in-wonder 1800). I've been told that the card probably isn't supported by the ATI drivers provided in the disk. So where do I go from here?

I was wondering what is supposed to happen after that bar fills up and the four lines of text are displayed. If i'm supposed to get some fancy highly graphic intensive page after that then it would make sense my video card is acting up, however if i'm supposed to be getting a bunch of lines of text without any advanced graphics then perhaps the problem lies elsewhere...

Sadly i don't have any working graphics cards lying around to test to see if the problem is only based on my current card, so that option of testing is kinda shot.

Also I figured the problem may be with a bad disk, so i re downloaded (from a different source, this time a torrent) and rewrote the disk and tried using that with the same error.

I'm also trying to install 7.10 as it is the newest release but being so new there may be a few kinks to work out, would it just be easier to try an earlier release instead?

Again thanks for any help anyone can render.

---

### Post by echo404 on 2007-10-24
ok i was advised to try the alternate cd to see if it would at least allow me to get through the install and it did. However apparently after a correct install and an attempted boot up, Ubuntu brings me to a very similar if not the same screen as the live cd did. upon boot up, i got a similar loading screen, only now it was smaller, and then after it loaded i was brought to a screen for lines of text and ok after each of them, and my display started going crazy.

Unless i can figure out a way to get my display and Ubuntu to play nice together i'm afraid making the switch will be impossible. The only alternative i can see is to try an older version of Ubuntu, but it pains me to have to use outdated software.

Please if anyone can help, i would greatly appreciate it, i've been looking forward to having a linux box for a long time now but it's quickly becoming a bigger headache than i had imagined it would be...

---

### Post by pndragon on 2007-11-15
> **ugly_b said:**
> For a little help with the dv9628nr laptop, see my posts here [http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

Cheers,
[www.WheresMyStar.com](www.WheresMyStar.com)

I finally followed that link (it had to wait while the family and I went on vacation).

First of all, following Dark_Stang's instruction's, I installed Gutsy Gibbon from the Ubuntu LiveCD without a problem. I would recommend installing the bcm43xx drivers first just so that you don't have to see any annoying messages about missing firmware while trying to get your graphics card installed. (This is what I did through all of many re-installations... my fault, **_not_** Dark_Stang).

I originally wanted Kubuntu, but was unable to get the Kubuntu LiveCD to load no matter what parameters I used.

So far everything is working, some things had to be tweaked by hand. For instance, I couldn't play dvds but this fixed it:
```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install totem-xine
sudo apt-get install vlc
sudo apt-get install libdvdread3 libxine1-ffmpeg
sudo apt-get install debhelper build-essential fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh
```This provides you with a VLC Player that does the job quite nicely.

I ended up having to skip KDE because it's network manager won't let you sign in using a WEP 64/128 hexadecimal passkey and, unfortunately, that was not something that I could change. If anyone has an answer to this I would like to hear it.

--- Jim

---

