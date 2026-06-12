---
title: "Screwed up xorg.conf really bad, how to recover??"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-12-14
I installed an ati driver and it wasnt reporting when I used "fglrxinfo" so i decided to mess around in xorg. All I can say now is that I cannot load the xwindow system at all. Is there a command I can use to manually (or automatically, which i prefer ;)  ) fix my xorg file? 

Thanks

Oh and Ive been trying different things to the file and unfortunately for my noobish self I may have screwed it up even more :S

---

### Post by taurus on 2006-12-14
Boot into recovery mode from GRUB menu and type

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

p.s.  And before you start messing around with /etc/X11/xorg.conf next time, make a backup copy!!!

---

### Post by WalmartSniperLX on 2006-12-14
> **taurus said:**
> Boot into recovery mode from GRUB menu and type

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

p.s.  And before you start messing around with /etc/X11/xorg.conf next time, make a backup copy!!!

Ok ill  make sure I do that next time 

Thanks a lot :D

---

### Post by bodhi.zazen on 2006-12-14
> **taurus said:**
> p.s.  And before you start messing around with /etc/X11/xorg.conf next time, make a backup copy!!!

WalmartSniperLX: Good to see you again. Up to no good I see :D

Always back up ANY system file before you edit it.

Also you never "need" to delete anything from a system file, add a # at the start of the line.

It is always a good habit to comment your changes in system files:
> # The following lines are to break Ubuntu
# And were added by myself :(

blah blah blah

---

### Post by TooRight on 2006-12-14
My xserver was going nuts too giving me problems, and reconfiguring it alone didn't work... gotta love ati eh? :P

What I did was go through the reconfigure part like what taurus said, and still couldn't get into ubuntu because of the graphics thing, but it gave me the option of viewing both records, one was the xorg.conf file. I was getting them ending by saying EE no screens or something like that. 

I hit Cntrl-Alt-F1 to get to a command prompt, then I typed:

```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv                              
sudo shutdown -r now

```

And it worked!!

***** NOTE: > sudo aticonfig --overlay-type=Xv     was the line needed for Edgy.
> sudo aticonfig --overlay-type-Xv     was the line that i had used previously for my Dapper install. The Dapper one uses a "-" sign and the Edgy one uses an "=" sign

Good luck!!

---

