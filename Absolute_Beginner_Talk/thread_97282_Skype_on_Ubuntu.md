---
title: "Skype on Ubuntu"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by soffdarb on 2005-11-30
Hi all, 

Showing my Newbieness here, but I have downloaded Skype from the web site but I dont know how to install it onto my desktop and have it operational.  I can see the package in my home/desktop file but how do I get it out of there and usable.

Thanks, 

Soffdarb

---

### Post by sapo on 2005-11-30
if you downloaded the debian package, open up a terminal and type the following:

```
cd Desktop
sudo dpkg -i skype_1.2.0.18-1_i386.deb
```

this should solve your problem and skype should appear on the internet menu (i think)

---

### Post by somody on 2005-12-01
I don't think so...I think more is needed unfortunately...

---

### Post by The Mekon on 2005-12-01
Have you searched for Skype using the Synaptic Pagkage Manager - Version 1.2.0.11 should be available.

---

### Post by Vlammetje on 2005-12-01
The Synaptic version did not work for me, however the download works, as long as the dependencies are fixed. there is a compiled recent version out there, I just cannot remember where I got it from. I got it yesterday though and it works, it should still be available somewhere.

---

### Post by Mustard on 2005-12-01
[http://www.ubuntulinux.org/wiki/SkypeHowto/](http://www.ubuntulinux.org/wiki/SkypeHowto/)

---

### Post by arnieboy on 2005-12-01
use [automatix]("http://ubuntuforums.org/showthread.php?t=66563") to install skype.

---

### Post by patrick295767 on 2005-12-02
I am usually installing the skype with QT stuffs implemented ...

---

### Post by littlepr on 2005-12-03
All,

I installed it using automix but I can't get it to dial out to land line phone. I have not been able to try it from peer2peer because i don't know anyone who uses it. In windows it works everysingle time. If anyone know the answer let me know the fix or what i might be doing wrong.

---

### Post by arnieboy on 2005-12-03
[QUOTE=littlepr]All,

I installed it using automix but I can't get it to dial out to land line phone. I have not been able to try it from peer2peer because i don't know anyone who uses it. In windows it works everysingle time. If anyone know the answer let me know the fix or what i might be doing wrong.[/QUOTE]
lets try talking to each other real quick. add me on skype. my nick is greyrod.

---

### Post by littlepr on 2005-12-03
Arnieboy,

Sorry about the late response but I just went into preferences and saw that skype is not setup/detecting my headphones under preferences->options->/hand/headset audio devices.

Would you know why? I can listen to music through the headphone speakers and talk on the mic and hear myself. The headset is a Logitech Internet Chat Headset. My sound controller is an on-board nforce2 AC97 Audio Controller (MCP).

Here's the error I get when running it from a command line:

alex@LaCasa:~$ skype
volume_open: error opening /dev/mixer: No such file or directory
volume_open: error opening /dev/mixer: No such file or directory
volume_open: error opening /dev/mixer: No such file or directory
/dev/dsp-1: No such file or directory

---

### Post by arnieboy on 2005-12-03
[QUOTE=littlepr]Arnieboy,

Sorry about the late response but I just went into preferences and saw that skype is not setup/detecting my headphones under preferences->options->/hand/headset audio devices.

Would you know why? I can listen to music through the headphone speakers and talk on the mic and hear myself. The headset is a Logitech Internet Chat Headset. My sound controller is an on-board nforce2 AC97 Audio Controller (MCP).

Here's the error I get when running it from a command line:

alex@LaCasa:~$ skype
volume_open: error opening /dev/mixer: No such file or directory
volume_open: error opening /dev/mixer: No such file or directory
volume_open: error opening /dev/mixer: No such file or directory
/dev/dsp-1: No such file or directory[/QUOTE]
this i think is an arts issue... are u sure u have arts installed?
```
sudo apt-get install arts
```

---

### Post by littlepr on 2005-12-03
Arnieboy,

Just got this message. I thought i had it installed. I will run the install again and them give you a call.

---

### Post by littlepr on 2005-12-03
Arnieboy,

What else would I have to do? Do I need to restart/reboot the PC for arts ARTs to take effect?

---

### Post by arnieboy on 2005-12-03
[QUOTE=littlepr]Arnieboy,

What else would I have to do? Do I need to restart/reboot the PC for arts ARTs to take effect?[/QUOTE]
trt logging out and logging back in and doing the following from terminal:
```
killall -9 esd
```
and then run skype

---

### Post by littlepr on 2005-12-03
Arnieboy,

Still nothing under hand/headset settings. And this is after uninstalling Skype, clearing the skype_xxx_ whatever version.deb from cache and re-installing it through automix. Should I disable sound server startup through System->Preferences->Sound and reboot once again?
What should be set as the default output and default input under Multimedia System Selector under the audio tab?

---

### Post by arnieboy on 2005-12-03
[QUOTE=littlepr]Arnieboy,

Still nothing under hand/headset settings. And this is after uninstalling Skype, clearing the skype_xxx_ whatever version.deb from cache and re-installing it through automix.[/QUOTE]
reinstalling skype wont solve the problem.. its got something to do with your sound server setup and how skype is detecting it. are u using KDE?
EDIT: I just came across this site which might be the cure you are looking for:
[http://195.38.3.142:6502/skype/](http://195.38.3.142:6502/skype/)
give it a try.

---

### Post by littlepr on 2005-12-03
Kde as in Kubuntu? No. This is a fresh install of ubuntu 5.04 upgraded to ubuntu 5.10, updated it and then I used your automix to install some of the other goodies. I will try the link you suggested.

---

### Post by littlepr on 2005-12-03
Kde as in Kubuntu? No. Thisn is a fresh install of ubuntu 5.04 upgraded to ubuntu 5.10, updated it and then I used your automix to install some of the other goodies. I will try the link you suggested.

---

### Post by littlepr on 2005-12-03
Arnieboy,

No luck with the skype_dsp_hijacker. Here are the logs when I try to use it:


ChangeLog  Makefile  README  skype_dsp_hijacker  skype_dsp_hijacker.c
root@LaCasa:/opt/skype_dsp_hijacker-0.6 # ./skype_dsp_hijacker --2nd
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
volume_open: error opening /dev/mixer: No such file or directory
volume_open: error opening /dev/mixer: No such file or directory
volume_open: error opening /dev/mixer: No such file or directory
/dev/dsp-1: No such file or directory

root@LaCasa:/opt/skype_dsp_hijacker-0.6 # ./skype_dsp_hijacker
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.
volume_open: error opening /dev/mixer: No such file or directory
volume_open: error opening /dev/mixer: No such file or directory
volume_open: error opening /dev/mixer: No such file or directory
/dev/dsp-1: No such file or directory

I have to take a break from this now. I catch up with any other suggestions later on.

---

