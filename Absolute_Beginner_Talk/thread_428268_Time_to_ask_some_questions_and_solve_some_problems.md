---
title: "Time to ask some questions and solve some problems"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Atmosphere on 2007-04-30
i've been on here for about a week and attempting to solve my own problems but here are some which i couldn't or have just recently developed.

1) GRUB loader takes about 1 minute to load (wasn't like that when first installed and no major changes to system) ???

2) Any of the open office suite software does not load, splash screen appears for about 3 seconds then disappears, nothing in system process'. ??

3) I can connect to the network no problem and can see all the computers however whenever i try and connect to any of the computers it asks for authentication even if that computer doesn't have any security, when connecting to file server (which does have authentication) and i input the login it just keeps on asking for it and i can't access it.

4) I try and add a network printer (canon LBP-1120) which is shared from another computer however it cannot be seen when search.

5) i can't remember the exact thin i was trying to do but was network related and it kept on asking me for authentication just to access a workgroup ... weird.

6) trying to watch a DVD with movieplayer but it says i do not have the right components to do so, restart after i install the components and start again.... how do i install the right components?

all other computers on the network are using windows XP pro SP2 or vista or Server 2003
the Ubuntu computer that is having the problem is one i JUST installed ubuntu and only did a update and enabled desktop effects. I have installed ubuntu on this computer previously and did not have a problem at all. all the problems occured in about 1 hour after install and a few restarts

all help appreciated

edit another problem

installed WINE just to try out i wasn't really thinking but installed Warcraft3 to try with WINE but now i can't uninstall it.

---

### Post by omkarwagh on 2007-04-30
try using vlc for the dvds. if vlc cant run it, i dont think anything can.

---

### Post by Atmosphere on 2007-04-30
vlc is for windows and i'm trying not to run WINE for progs atm

---

### Post by FuriousLettuce on 2007-04-30
VLC is also for Linux - check Synaptic.

---

### Post by az on 2007-04-30
> **Atmosphere said:**
> i've been on here for about a week and attempting to solve my own problems but here are some which i couldn't or have just recently developed.


1.  What part takes long?  The BIOS check?  The Grub Menu, the spash screen?  Be specific.
2.  Have you mixed repositories?  Have you added debian repos or a differen release of Ubuntu to your repos?

3.
[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29](https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29)
[https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)

4. and 5., see above,

6.  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)



> **Atmosphere said:**
> vlc is for windows and i'm trying not to run WINE for progs atm

Vlc is f ree-libre open source.  It is in the Ubuntu repositories.

---

### Post by konst88 on 2007-04-30
2. Try to run them from the terminal, and check the output.

---

### Post by Atmosphere on 2007-04-30
quite literally after the BIOS check and before GRUB loads, all you see is a blinking cursor on the screen for 1 minute with no activity

---

### Post by Atmosphere on 2007-04-30
oh and i haven't added any other repo's to the standard ones

and what is the command to run any of the open office suite in terminal ?

---

### Post by az on 2007-04-30
> **Atmosphere said:**
> quite literally after the BIOS check and before GRUB loads, all you see is a blinking cursor on the screen for 1 minute with no activity

I had a dvd-wrter drive that caused that to happen.  It would pause the whole bootup process as if it were not sure whether it had bootable media in it.  It would happen intermittently.  I pinpointed it to be the cause by watching my machine boot one day with an audio cd in the drive.  It showed the exact same behaviour.  I removed the drive and put it into another computer and it never happened again.

Both the machine and the dvd drive are still working properly.  Go figure!

> **Atmosphere said:**
> oh and i haven't added any other repo's to the standard ones

and what is the command to run any of the open office suite in terminal ?

usr/bin/oowriter

Do you have any broken packages?  What happens if you run

sudo apt-get update
sudo apt-get -f install

and 

sudo apt-get install ubuntu-desktop

---

