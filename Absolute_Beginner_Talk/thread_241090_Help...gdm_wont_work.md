---
title: "Help...gdm wont work"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Campitor on 2006-08-21
Hello:

  I've been trying to set up xubuntu on an old laptop (Dell Inspiron 266Mhz).  I installed server Dapper with alternate.  Then did:
sudo apt-get install ubuntu-lite-desktop

I didnt like ubuntu-lite, because it wouldnt run many aplications I need.  so I did:

sudo apt-get remove ubuntu-lite-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get remove wdm

after many hours, all apparently went well.  When I rebooted, gdm wouldnt work...after booting all the components, it goes into a blue screen, the turning circle (i.e. wait cursor) works for a second, and then it goes back to the text screen, then it goes into a blue screen, turning circle, text screen...this goes on forever.

I logged in using the rescue mode from grub, and did:
sudo apt-get install gdm --reinstall
sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure gdm

and rebooted...Same problem

The funny thing is...that if I log in in secure mode, and just type: gdm
I go into the loging window and can boot perfectly well into xubuntu or icewm, or even fluxbox.  And everything works fine.  I dont know what else to do.  This is very frustrating...and I-ve already wasted three days on this.  Is there a way I can login using just text (do not go automatically into gdm), and then try to start the window manager of my choice with a comand-line command (i.e. startx or startxfce)?
Please help...I need to work!

Camp

---

### Post by meng on 2006-08-21
Sure: here's what I did (from CLI)

cd /etc/rc2.d
ls (check for the existence of S13gdm)
sudo mv S13gdm _S13gdm (then you can easily reverse the change later)

and reboot

Basically you're removing gdm from the automatic startup at runlevel 2 (which is default for ubuntu)

Actually what I did was subtly different, I removed gdm from runlevel 3, then created a grub option for booting Ubuntu into runlevel 3.

---

### Post by Campitor on 2006-08-21
Hi meng:

  Well it worked...and it didn't. After doing what you suggested, I booted into CLI.  And if I do:  sudo gdm...it goes into the neverending loop.

If I type: startx or startxfce4, I start booting into the wm, I see the mouse turning in the wheel...and then it stops.  I switch  back to tty1 and read:  Error opening /dev/wacom  no such file..

If I type startfluxbox or icewm, nothing happens, it says it can find the X server.

I think I'm gonna do a fresh install, although that takes about two days to complete.  Do you recomend a special server boot command for such an old laptop?  Thanks

---

### Post by meng on 2006-08-21
Sorry to hear you haven't solved things to your satisfaction. I'm not familiar with the range of boot options available, but I hope someone else can help you.

---

### Post by Campitor on 2006-08-22
Well...I got it to work.  Apparently, my boot options included nolapi noapic and something no387.  After removing those from grub with the 'e'dit option, everything works fantastic.  I just need to know how to remove them frum the grub command permanently.

My only question is:  I-ve read some forums where they suggest using the acpi=no option on booting.  Can anyone give me a pointer to where I can read about this?
 thanks

Camp

---

### Post by meng on 2006-08-22
sudo gedit /boot/grub/menu.lst
(or else use the editor of your choice)
this file contains all the boot options
[http://ubuntuforums.org/showthread.php?t=237264](http://ubuntuforums.org/showthread.php?t=237264)
may help you with the no ACPI. I tried it on my 2004 Dell, but without luck. Maybe it will suit you.

---

