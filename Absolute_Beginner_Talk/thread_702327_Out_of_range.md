---
title: "Out of range"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by honest_geezer on 2008-02-20
Trying to install Ubuntu 7.1 on an AMD 64 bit based system, asrock nf6 live-vista motherboard.

I've tried both 64 bit and 32 bit versions and both bomb out with out of range errors. Tried changing resolutions from VGA to 800x600 and up and always get an out of range error.

Any ideas?

Thanks

---

### Post by justleen on 2008-02-20
is the monitor hooked up via a DVI dongle on a VGA port by any change?

---

### Post by erginemr on 2008-02-20
Normally I would suggest you to use the Alternate install CD, but I am trying to find a more direct workaround, since with the Alternate CD, new users cannot experience Ubuntu without installing it to their hard drive. I think I have found one.

So if you can help me in this and apply the following steps in your system, I will be very grateful. 

You may want to write the commands down on a scrap of paper or print it out before the attempt, as it will be hard to remember on a black screen:

1. First, boot your system with the Ubuntu Live CD.

2. At the Ubuntu boot up screen, make sure that the first item (Start or Install Ubuntu) is active and press F6.

3. Replace the words "quite splash --" with "single" and press Enter to continue.

4. Some text messages will flow. When the boot process is complete, you will find yourself logged as root in text mode.

5. Write "nano -w /etc/X11/xorg.conf" or if you are familiar with Vi Editor, "vim /etc/X11/xorg.conf" to edit the "xorg.conf" file.

6. In Vim, you an enter into the editing mode by pressing [i], and into the command mode by pressing [Esc].

7. Find the section [Section "Screen"]. Add the following lines between [DefaultDepth   24] and [EndSection].
```
SubSection  "Display"
       Depth	 24
       Modes	800x600
EndSubSection
```
Neither the indentation, nor the number of spaces is significant here.

8. Save the file with [Ctrl+O] and exit [Ctrl+X] if you are using nano, or use [Esc] and [ZZ] or [:wq] if you are using Vim.

9. Exit the root session either with "exit" or with [Ctrl+D].

10. The system will automatically load to the graphical Live CD environment. If not, you can force it manually by entering "startx".

If this works as expected, I am planning to write a howto on it so that other people may also benefit.

---

### Post by honest_geezer on 2008-02-20
> **justleen said:**
> is the monitor hooked up via a DVI dongle on a VGA port by any change?
No m8 it's not just a standard port.

---

### Post by honest_geezer on 2008-02-20
> **erginemr said:**
> Normally I would suggest you to use the Alternate install CD, but I am trying to find a more direct workaround, since with the Alternate CD, new users cannot experience Ubuntu without installing it to their hard drive. I think I have found one.

So if you can help me in this and apply the following steps in your system, I will be very grateful. 

If this works as expected, I am planning to write a howto on it so that other people may also benefit.

Thanks so much for this and wioll try this in the morning and let you know :) Just came in from work so a bit tired just now :wink:

---

### Post by honest_geezer on 2008-02-20
> **honest_geezer said:**
> Thanks so much for this and wioll try this in the morning and let you know :) Just came in from work so a bit tired just now :wink:

Just tried it now m8, although dead tired was excited to get it going and it it fell  over at live boot script (or something like that lol) - any ideas?

Thanks for the help btw :)

---

### Post by erginemr on 2008-02-20
> **honest_geezer said:**
> Just tried it now m8, although dead tired was excited to get it going and it it fell  over at live boot script (or something like that lol) - any ideas?

Thanks for the help btw :)

So, didn't work I believe :confused:

---

### Post by honest_geezer on 2008-02-21
> **erginemr said:**
> So, didn't work I believe :confused:

Well poss it did, seemed to get further, or at least I could see further in the process but fell over at this stage. I don't know if this is further as it just went out of range before???

Thanks for your help and any further suggestions welcome :)

---

### Post by erginemr on 2008-02-21
OK. One more try and I will leave your tail. :) This one is much simpler:

1. Try booting into the Live CD again. 

2. On the boot up screen, when the first item is selected; press F6 again and replace "quiet splash --" with "single" without the quotes.

3. When (or if) you reach the text prompt at the end of the boot up process, issue this command:
```
dpkg-reconfigure -phigh xserver-xorg
```
Select "vesa" as the driver and "1024x768" as the resolution.

4. Issue "exit" or "Ctrl+D" to boot into the Live CD graphical environment.

If this does not work either, then the only option you have is to download Ubuntu Alternate CD from:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

There should be checkbox down the page that will let you download the text-mode installer CD.

---

### Post by honest_geezer on 2008-02-22
> **erginemr said:**
> OK. One more try and I will leave your tail. :) This one is much simpler:

1. Try booting into the Live CD again. 

2. On the boot up screen, when the first item is selected; press F6 again and replace "quiet splash --" with "single" without the quotes.

3. When (or if) you reach the text prompt at the end of the boot up process, issue this command:
```
dpkg-reconfigure -phigh xserver-xorg
```
Select "vesa" as the driver and "1024x768" as the resolution.

4. Issue "exit" or "Ctrl+D" to boot into the Live CD graphical environment.

If this does not work either, then the only option you have is to download Ubuntu Alternate CD from:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

There should be checkbox down the page that will let you download the text-mode installer CD.

Thanks again for all the help m8. Still getting the out of range error with this. Will try the alternate version and if that doesn't work will just stick with W!indows which it galls me to say, but is maybe gonnae work out easier for me :(

Thanks again!:)

---

### Post by erginemr on 2008-02-22
> **honest_geezer said:**
> Thanks again for all the help m8. Still getting the out of range error with this. Will try the alternate version and if that doesn't work will just stick with W!indows which it galls me to say, but is maybe gonnae work out easier for me :(

Thanks again!:)

aye aye sir ;) u gotta try the Alt-CD anyway, an' come back here if u still got res probs with ur monitor buddy, 'coz we don't wanna lose a fella to dat nasty windoze :) 
):P

---

### Post by honest_geezer on 2008-02-22
> **erginemr said:**
> aye aye sir ;) u gotta try the Alt-CD anyway, an' come back here if u still got res probs with ur monitor buddy, 'coz we don't wanna lose a fella to dat nasty windoze :) 
):P

Well, tried the alt version and it keeled over when trying to format my drive. Just kept going around in circles. Not really sure if it's worth removing my main install (XP) to continue with this, unfortunately, as it didn't recognise my gfx card, network adapter and several other main devices. Don't have any res probs in windaes with the monitor so must be Ubuntu driver related somehow :(

Thanks anyway for the help erginemr, you've been really good :D

---

### Post by erginemr on 2008-02-22
> Thanks anyway for the help erginemr, you've been really good

:( What good is it if it doesn't solve your problem?

I am really sorry that Ubuntu did'nt work for you as you were clearly willing to try it. Even if you could, you should have definitely kept your XP in check and have both Windows and Linux in your computer (i.e. dual-boot). 

I have a final recommendation to you: If you don't dislike KDE environment (as opposed to Gnome, which Ubuntu is), you should give a try to PCLinux OS. It is really user-friendly, is reputable with its good hardware recognition, and has successfully managed to run a laptop that I got my hands on, where the Ubuntu Live CD failed to boot.

It is top two with Ubuntu in the most popular distro's list of [www.distrowatch.com](www.distrowatch.com). It is basically a customized KDE distro, but has a community-developed Gnome version, too. If you are interested, you can download PCLinux OS Live / Installer CD from: [www.pclinuxos.com](www.pclinuxos.com). I hope you will persist with Linux and find the correct distro for you.

Take care yourself friend. ):P

---

### Post by honest_geezer on 2008-02-22
> **erginemr said:**
> :( What good is it if it doesn't solve your problem?

I am really sorry that Ubuntu did'nt work for you as you were clearly willing to try it. Even if you could, you should have definitely kept your XP in check and have both Windows and Linux in your computer (i.e. dual-boot). 

I have a final recommendation to you: If you don't dislike KDE environment (as opposed to Gnome, which Ubuntu is), you should give a try to PCLinux OS. It is really user-friendly, is reputable with its good hardware recognition, and has successfully managed to run a laptop that I got my hands on, where the Ubuntu Live CD failed to boot.

It is top two with Ubuntu in the most popular distro's list of [www.distrowatch.com](www.distrowatch.com). It is basically a customized KDE distro, but has a community-developed Gnome version, too. If you are interested, you can download PCLinux OS Live / Installer CD from: [www.pclinuxos.com](www.pclinuxos.com). I hope you will persist with Linux and find the correct distro for you.

Take care yourself friend. ):P

Yeah was really up for it, really wanted to try something else but ms o/s. It was a dual boot I was trying to set-up but no joy unfortunately. I will keep persisting with Linux, basically thanks to yourself who is so keen and a fan of it erginemr. I will attempt the pclinux install. 

Thanks again for all your help my friend and hope we meet again and I can return the favour! If not, have a really nice life! Take care! :KS

---

