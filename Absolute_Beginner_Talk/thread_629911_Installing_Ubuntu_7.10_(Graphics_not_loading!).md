---
title: "Installing Ubuntu 7.10 (Graphics not loading?!)"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-12-02
I'm not quite sure what is happening, I'm hoping there is someone here that can help me out.  I've got a custom built system (AMD Athlon x2 64 bit 4600, Geforce 8800 GTS).  

I've got Vista on my Primary Disk - I've left 150GB unpartitioned though.  I insert the 7.10 disk, my computer boots from the ubuntu install disk.

[I]The Ubuntu Menu loads and I have the following options:
Start or Install Ubuntu
Start Ubuntu in safe graphics mode
Install with driver update cd
OEM install (for manufacturers)
Check CD for defects
Memory test
Boot from first hard disk[/I]

I've tried selecting every option from this menu.  For all (excluding the memory test & boot from hd option) the following occurs:  A menu pops up "loadling linux kernel" that zooms across, a few lines of text appear at the bottom that say linux kernel has been loaded ... my cd-drive read-light comes on, flashes for about a minute or so, then goes off ... this whole time the screen is blank.  And it stays that way.  Nothing ever appears on the screen.

I'm not sure why.  I have to hard-boot it.  Any suggestions?  Please? :)

---

### Post by atraeyu on 2007-12-02
Could it have something to do with my graphics card?

---

### Post by overdrank on 2007-12-02
> **atraeyu said:**
> Could it have something to do with my graphics card?

You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash  and then hit enter and then  b to boot. this will allow you to see any errors.  Hope this helps. Good luck!

---

### Post by GSF1200S on 2007-12-02
Ewww.. well let me ask this. Are you determined to get Ubuntu on there, or are you just trying to get a feel for it using the livecd?

If its the latter, I might suggest trying out PCLinuxOS, Fedora, or MEPIS (fedora is gnome main like ubuntu, the others are KDE).

If you know you want ubuntu, im sure the alternate cd would install a full system, but im not sure if the gui will load after you are done. This is rare.. you might also want to check the integrity of the install disc. You may have a corrupted download or the like...

I would try another live cd real quick and see if it works.. You could then try pulling a new torrent and re-downloading ubuntu and try it again.. that seems like a weird problem. We could help you t/s an actual install, but the livecd I dont really know.

I had the same problem with KateOS- it just wont work on my system, no matter what I try...

---

### Post by siciliancasanova on 2007-12-02
"Boot from first hard disk" doesn't boot into Windows?

---

### Post by st33med on 2007-12-02
Also, try the alternative CD. This does not require a display.

It could also be that your disk was not burnt properly.

---

### Post by atraeyu on 2007-12-02
> **siciliancasanova said:**
> "Boot from first hard disk" doesn't boot into Windows?
Yup, it does.

---

### Post by atraeyu on 2007-12-02
> **st33med said:**
> Also, try the alternative CD. This does not require a display.

It could also be that your disk was not burnt properly.
I will try downloading and reburning.  I personally do not think this will make a difference though.

---

### Post by GSF1200S on 2007-12-02
> **atraeyu said:**
> I will try downloading and reburning.  I personally do not think this will make a difference though.

It may not, but then you can try the alternate cd as said above. The only thing is, we may have to help you fix whatevers causing the gui not to load. If after reburning it doesnt work, then once again try another distros livecd just to see...

---

### Post by atraeyu on 2007-12-02
I will try the alternate CD next if this doesn't work.  Fortunately my connection is fast (I'm dling a new copy @ 1100KB/sec).  If the alternate CD doesn't work, what other distro would you suggest trying?

I've run Ubuntu in the past (7.04) but never any other.

---

### Post by GSF1200S on 2007-12-02
> **atraeyu said:**
> I will try the alternate CD next if this doesn't work.  Fortunately my connection is fast (I'm dling a new copy @ 1100KB/sec).  If the alternate CD doesn't work, what other distro would you suggest trying?

I've run Ubuntu in the past (7.04) but never any other.

Youve run it in the past?? On this computer?!!? That is weird. Well, itd be awesome if you could get this 7.10 issue resolved. Lets see where the alternate takes us. I guess you could try Linux Mint or Ubuntu Studio, allthough you may run into the same problems...

If you want another gnome distro, I say you cant go wrong with plain jane debian (lenny, or sid if youre gonna go for broke)... Fedora seems good to, although I know as an Ubuntu user, I always miss apt on other distros (Archs pacman is pretty good imho)

---

### Post by atraeyu on 2007-12-02
I ran 7.04 on my old box (and it is actually still running on my old box, but that's just a server now).  I'm trying to move from Vista to Ubuntu on my desktop/workstation, if possible.

---

### Post by atraeyu on 2007-12-02
I finished the second download, reburned.  Same exact problem with the second disk.  I'm downloading the alternate CD now.

---

### Post by atraeyu on 2007-12-02
Argh!  I downloaded & installed Ubuntu from the Alternate CD.  When I boot Ubuntu 7.10 Kernel (generic) the screen goes blank and ... nothing happens.  At all.  Just like when I tried to run the installer off the regular CD.

---

### Post by atraeyu on 2007-12-03
My personal guess is that this is somehow related to the video card I'm using (EVGA Geforce 8800 GTS).  Is that possible?  I've been googling it all morning, have not yet found anything to confirm or fix this.

---

### Post by Mze on 2007-12-03
Check out this thread: [Geforce 8800 - Gutsy]("http://ubuntuforums.org/showthread.php?t=623180")

---

### Post by atraeyu on 2007-12-03
Woot, just figured it out: [https://bugs.launchpad.net/ubuntu/+bug/140904](https://bugs.launchpad.net/ubuntu/+bug/140904)
Had to boot in recovery mode and run "init 5" from the command prompt.  This loaded the x system.

Once in, I opened up a new terminal, ran su for admin access, then typed: gedit /boot/grub/menu.lst and removed splash from the kernal options (like instructions say).

I boot up without a problem now.

---

### Post by GSF1200S on 2007-12-03
> **atraeyu said:**
> Woot, just figured it out: [https://bugs.launchpad.net/ubuntu/+bug/140904](https://bugs.launchpad.net/ubuntu/+bug/140904)
Had to boot in recovery mode and run "init 5" from the command prompt.  This loaded the x system.

Once in, I opened up a new terminal, ran su for admin access, then typed: gedit /boot/grub/menu.lst and removed splash from the kernal options (like instructions say).

I boot up without a problem now.

Cool.. at least it was an easy fix. And you didnt have to try another distro!

---

### Post by njparton on 2007-12-10
You can also do this at install by hitting F6 and removing splash from the command line options :wink:

---

### Post by culae on 2007-12-11
hi! i'm VERY new too. and i get a similar problem. after i hit install it pop-up the ubuntu logo with the sliding bar and the the black screes with:
"BusyBox v1.1.3...
/bin/sh: can't acces tty; job control turned off
(initramfs)_"
waiting for a command. what command should i do?
thank you
i use a laptop
asus l300
256mb of ram
p4 1.6ghz

culae
ps. i'm using ubuntu 7.04 the original cd

---

### Post by gonesolo on 2007-12-12
> **atraeyu said:**
> Woot, just figured it out: [https://bugs.launchpad.net/ubuntu/+bug/140904](https://bugs.launchpad.net/ubuntu/+bug/140904)
Had to boot in recovery mode and run "init 5" from the command prompt.  This loaded the x system.

Once in, I opened up a new terminal, ran su for admin access, then typed: gedit /boot/grub/menu.lst and removed splash from the kernal options (like instructions say).

I boot up without a problem now.


I'd like to say thank you for this information. I have a 8800GTX card and was having the same problems as you (luckily I have my vista dual boot so could browse here. 

This thread sorted me out thank you very much

---

### Post by atraeyu on 2007-12-19
Dec 19th Update: I ran the update utility today.  I then rebooted.  I booted to a completely black screen.  I choked back a heart attack and booted in recovery mode.  Pressed CTRL-D to continue.  My GUI prompt loaded.  I got into gnome.  I checked the menu.lst file again, sure enough - one of todays updates had reset the menu.lst file and splash was again enabled.

I disabled splash (just remove the word splash), rebooted and got some weird error message that the GUI loader couldn't communicate with gnome.  Everything was jacked up.  I rebooted again, it booted perfectly.  Hope this helps in case anyone else encounters this problem today.

---

### Post by pupEOkami on 2007-12-19
at the option screen for boot/live , hit the F6 option and try these simple commands .
noapic noirqpoll noirqdebug  
that should help ya out

---

### Post by Spydr4590 on 2008-01-09
Thanks for this post! I was having the same issue. All I did was hit F6, and deleted the word splash and hit enter. Everything worked afterwards. I'm using a evga 8800GTS 640 meg

---

