---
title: "anybody know anything about emu10k1"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-02-24
Hello! i need some help with installing emu 10k1. this is the guide that i have been following.

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+ES.&chip=emu10k2&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+ES.&chip=emu10k2&module=emu10k1)

everything works out fine until i type:cp /downloads/alsa-* . in the terminal.
this is what i get

armcandy@armcandy-desktop:~$ cd /usr/src
armcandy@armcandy-desktop:/usr/src$ mkdir alsa
mkdir: cannot create directory `alsa': File exists
armcandy@armcandy-desktop:/usr/src$ cd alsa
armcandy@armcandy-desktop:/usr/src/alsa$ cp /downloads/alsa-* .
cp: cannot stat `/downloads/alsa-*': No such file or directory
armcandy@armcandy-desktop:/usr/src/alsa$ 

 i am a complet newbie so if you tell me to create something somewhere you have to tell me exactly what to do. if anybody could help that would be great.

---

### Post by igknighted on 2007-02-24
> **hempa said:**
> Hello! i need some help with installing emu 10k1. this is the guide that i have been following.

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+ES.&chip=emu10k2&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+ES.&chip=emu10k2&module=emu10k1)

everything works out fine until i type:cp /downloads/alsa-* . in the terminal.
this is what i get

armcandy@armcandy-desktop:~$ cd /usr/src
armcandy@armcandy-desktop:/usr/src$ mkdir alsa
mkdir: cannot create directory `alsa': File exists
armcandy@armcandy-desktop:/usr/src$ cd alsa
armcandy@armcandy-desktop:/usr/src/alsa$ cp /downloads/alsa-* .
cp: cannot stat `/downloads/alsa-*': No such file or directory
armcandy@armcandy-desktop:/usr/src/alsa$ 

 i am a complet newbie so if you tell me to create something somewhere you have to tell me exactly what to do. if anybody could help that would be great.

That driver should be in the default ubuntu install, why are you trying to download it?

---

### Post by hempa on 2007-02-24
OK! i did not know that. how can i check if i have it and if it is installed

---

### Post by hempa on 2007-02-24
i want to download it because i am having problems with the sound on my computer. i have a 7.1 system but i can only get sound from my two front speakers. i think i have analog sound because the plug from the wire in my creative sound set that goes in to the computer looks like a plug for headphones. i heave heard that if you have digital sound the plug is much fater.

---

### Post by TonKi on 2007-02-24
You had a look at volume-contol? Just an idea ;)

---

### Post by Maestro23 on 2007-02-24
For what it's worth, your "mkdir" command didn't work becuase you where in [COLOR="Red"]/usr [/COLOR]which is owned by root.  You need to use "sudo" in front of your command.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by hempa on 2007-02-24
Ok i wrote this in the terminal "sudo modprobe snd-card-emu10k1" and this is what i got

armcandy@armcandy-desktop:~$ sudo modprobe snd-card-emu10k1
FATAL: Module snd_card_emu10k1 not found.
armcandy@armcandy-desktop:~$

does this mean that i dont have emu 10k1.

i have downloded the latest version of it and it is on my desktop, but i dont know how to install it

---

### Post by igknighted on 2007-02-24
If you go to System -> Preferences -> sound what driver does it say it is using?

That driver is a part fo the kernel.  My SB Live card uses it as the default with no problems.  Also in the course of compiling my kernel I have seen it as an option, so it is there.  The question is how to change it in gnome.  In the KDE control center it would be very easy.  Any gnome peeps know where it is?

EDIT: What is the output of "sudo modprobe -l emu*"?  I get:
/lib/modules/2.6.19-1.2911.fc6/kernel/drivers/input/gameport/emu10k1-gp.ko

---

### Post by hempa on 2007-02-24
> **igknighted said:**
> If you go to System -> Preferences -> sound what driver does it say it is using?

That driver is a part fo the kernel.  My SB Live card uses it as the default with no problems.  Also in the course of compiling my kernel I have seen it as an option, so it is there.  The question is how to change it in gnome.  In the KDE control center it would be very easy.  Any gnome peeps know where it is?

EDIT: What is the output of "sudo modprobe -l emu*"?  I get:
/lib/modules/2.6.19-1.2911.fc6/kernel/drivers/input/gameport/emu10k1-gp.ko

Ok this is what it says in system ->preferences->sound->devices.  
sound events-autodetect
music and movies-autodetect
audio conferencing,sound playback-autodetect. and sound capture-ALSA

in system ->preferences->sound->sounds it says that my default soundcard is audigy 2 [SB0350b]

---

### Post by igknighted on 2007-02-24
> **hempa said:**
> Ok this is what it says in system ->preferences->sound->devices.  
sound events-autodetect
music and movies-autodetect
audio conferencing,sound playback-autodetect. and sound capture-ALSA

in system ->preferences->sound->sounds it says that my default soundcard is audigy 2 [SB0350b]

Are there any other driver choices for that card?  Or do they only give you SB0350b?  Also, what does the modprobe command above say?  If you don't have anything there then your kernel might not have been compiled with that driver, but I highly doubt this.  Unfortunately I do not know gnome well enough to tell you where the proper control panel is to change that driver.  If you have KDE I could walk you through it tho...

---

### Post by hempa on 2007-02-24
no i dont have any other driver options for the soundcard. and at the top of the sounds page it says. enable software sound mixing (ESD) and that box is checked the box below wich says play system sounds is also checked.
how can i go on from here?? how can i install anoyher driver for my soundcard

---

### Post by igknighted on 2007-02-24
> **hempa said:**
> no i dont have any other driver options for the soundcard. and at the top of the sounds page it says. enable software sound mixing (ESD) and that box is checked the box below wich says play system sounds is also checked.
how can i go on from here?? how can i install anoyher driver for my soundcard

You don't need to install a new driver.  You already have the right one (it's part of your kernel), Ubuntu is just not using it.

---

### Post by hempa on 2007-02-24
> **igknighted said:**
> You don't need to install a new driver.  You already have the right one (it's part of your kernel), Ubuntu is just not using it.

how can i get ubuntu to use that driver??
i also did what you asked me earlier and typed this in the terminal

armcandy@armcandy-desktop:~$ sudo modprobe -l emu*
Password:
/lib/modules/2.6.17-11-386/kernel/sound/oss/emu10k1/emu10k1.ko
/lib/modules/2.6.17-11-386/kernel/drivers/input/gameport/emu10k1-gp.ko
armcandy@armcandy-desktop:~$

i hope that will help a little

---

### Post by igknighted on 2007-02-24
if you go to System -> Administration -> Soundcard Detection there should be a bunch of drop down menus, one of which will say what driver it is using, and you should be able to choose the emu10k1.  If you don't have this option, I believe there is a gnome control panel somewhere in synaptic, install that and find the sound configuration in there, as this should be able to do that as well.  I am sure there is a CLI way to do this thats probably easiest, but I do not know it.

---

### Post by hempa on 2007-02-24
I did not find anything called soundcard detection but i went into the device manager and looked on the SB soundcard there and this is what i got

Key-info. linux .driver
Type- strlist
Value- EMU10K1_Audigy

---

### Post by hempa on 2007-02-24
if it is easier for you to guide me through this mess if i use kde i can change to kde.

---

### Post by igknighted on 2007-02-24
Do you have KDE installed?  Don't install it if you don't have it already.  If you are still in gnome, in sys->admin->??? can you get to a screen that looks vaguely like this?  This is from fiesty, I don't know what the edgy/dapper counterparts are like...

---

### Post by hempa on 2007-02-24
i am on that screen now what should i do??

---

### Post by igknighted on 2007-02-24
Sorry this took so long... im packing to go out of town...

I think by changing "autodetect" to some of the other choices on this list will solve your problem.  Clearly autodetect is not working, so it needs a little manual input.  I would do some trial and error here and see if some combination gets your sound going.

---

