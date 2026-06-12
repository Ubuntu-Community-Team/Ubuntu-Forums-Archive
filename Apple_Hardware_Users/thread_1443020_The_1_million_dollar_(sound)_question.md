---
title: "The 1 million dollar (sound) question"
date: 2010-03-30
forum: Apple Hardware Users
---

### Post by Dark_Ronius on 2010-03-30
Hi all

I have torn my hair out and, for tonight, given up on getting sound working with Ubuntu 10.04 using my Mac. I'd really like to get using the apps from Ubuntu Studio so I can try out the video editing capabilities with the Mac's hardware.

However, I have tried thousands of guides and cannot get the sound to work.

It appears to require Realtek drivers (at least Windows 7 did), although doing lspci -v shows it seems to be an Nvidia card as well.

One of the steps handily uploaded a load of info here for me... [http://www.alsa-project.org/db/?f=3395985838328df6881b87d71fa3bfab29812b7e](http://www.alsa-project.org/db/?f=3395985838328df6881b87d71fa3bfab29812b7e)

Any help would be really, really appreciated... I can't be the only person with a Mac (at least this soundcard) having problems, can I?!

---

### Post by zacbarton on 2010-03-30
I've got a imac 24 (2009 model) and I got sound working by adding "options snd-hda-intel model=lenovo-sky" to /etc/modprobe.d/imac.conf.

---

### Post by jamesey on 2010-03-30
> **Dark_Ronius said:**
> Hi all



However, I have tried thousands of guides and cannot get the sound to work.
!

what version of mac do you have?

---

### Post by Neds Moar Salt on 2010-03-31
> **Dark_Ronius said:**
> Hi all

I have torn my hair out and, for tonight, given up on getting sound working with Ubuntu 10.04 using my Mac. I'd really like to get using the apps from Ubuntu Studio so I can try out the video editing capabilities with the Mac's hardware.

However, I have tried thousands of guides and cannot get the sound to work.

It appears to require Realtek drivers (at least Windows 7 did), although doing lspci -v shows it seems to be an Nvidia card as well.

One of the steps handily uploaded a load of info here for me... [http://www.alsa-project.org/db/?f=3395985838328df6881b87d71fa3bfab29812b7e](http://www.alsa-project.org/db/?f=3395985838328df6881b87d71fa3bfab29812b7e)

Any help would be really, really appreciated... I can't be the only person with a Mac (at least this soundcard) having problems, can I?!

Zap your PRAM/NVRAM then use rEFIt to sync your mbr table if you can't find linux on the boot screen anymore.  It works for me, but the problem is always that using grub to load OSX makes OSX have no sound.

---

### Post by linuxopjemac on 2010-03-31
tell me the exyact model of your computer
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by Dark_Ronius on 2010-04-01
Apologies all for forgetting to put in my Mac version; it's the iMac 24" 2009.

And thanks for your responses... I'll try them out when I've finished my work and can boot into Ubuntu later tonight

---

### Post by Dark_Ronius on 2010-04-01
> I've got a imac 24 (2009 model) and I got sound working by adding "options snd-hda-intel model=lenovo-sky" to /etc/modprobe.d/imac.conf.

Thanks zacbarton, sound is very blatantly now working after accidentally keeping the sound level too high and being shocked by the ethnic vibes of the log in sound!

Anytime you want a free drink or a few, just give us a call ;)

---

### Post by ErsinG on 2010-04-02
Glad your problem solved! :) I wish my sound problem was solved as fast as yours :) 

You can now change your prefix to [solved]
Cheers and enjoy your cup of ubuntu :)

---

### Post by GRScott on 2010-06-05
I have a Imac 24" 2009 and am new to Ubuntu (10.04). Have partitioned with Mac OS Snow Leopard. My sound is not working in Ubuntu. New to the Terminal app.
You said:
"I've got a imac 24 (2009 model) and I got sound working by adding  "options snd-hda-intel model=lenovo-sky" to /etc/modprobe.d/imac.conf."

How do I enter this in the Terminal?
I've tried entering "sudo nano /etc/modprode.d/imac.conf" and then entering "options snd-hda-intel model=lenovo-sky" and then control-o, enter, control-x. And then reboot. 

Am I doing this wrong?

Appreciate any help

---

### Post by itbcn8 on 2010-06-06
Wish I could help but I'm new to terminal too.... Where does everyone learn it? Any books I should read?

---

### Post by linuxopjemac on 2010-06-06
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

Inspiration:
[http://mac.linux.be/content/sound-problems](http://mac.linux.be/content/sound-problems)

---

### Post by sha.goyjo on 2010-06-06
> **itbcn8 said:**
> Wish I could help but I'm new to terminal too.... Where does everyone learn it? Any books I should read?

1st piece of advice
use the following commands
```

$man {command in question}
${command in question} -h
${command in question} --help

```

That will be a good start. Also, work on some older systems, and get yourself a copy of the good ole yggdrasil linux bible. It's really just vocab, mostly.

---

### Post by GRScott on 2010-06-06
Linuxopjemac,

I entered 'sudo nano /etc/moprobe.d/alsa-base.conf <Enter> into Terminal and this showed in my file:
------------------------------------------------------------------------------------------------
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-io$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklis$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blac$
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklis$
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklis$
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2

---------------------------------------------------------------------------------------------------
Now, where would I enter 'options snd-hda-intel model=lenovo-sky' into this and do I also cont-o, Enter, and cont-x?

Thank you for the help. (I do have a Imac9,1)

---

### Post by sha.goyjo on 2010-06-06
I don't know when he'll get back, but I've done this numerous times before, so I'll answer. put it at the bottom, and yes, save, then exit.

---

### Post by Neds Moar Salt on 2010-06-07
> **GRScott said:**
> Linuxopjemac,

I entered 'sudo nano /etc/moprobe.d/alsa-base.conf <Enter> into Terminal and this showed in my file:
------------------------------------------------------------------------------------------------
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-io$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklis$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blac$
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklis$
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklis$
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2

---------------------------------------------------------------------------------------------------
Now, where would I enter 'options snd-hda-intel model=lenovo-sky' into this and do I also cont-o, Enter, and cont-x?

Thank you for the help. (I do have a Imac9,1)

All the commands are there for you at the bottom of the window.  Just scroll down with the arrow keys and type what you want to type in.  Ctrl-x will exit but ask you to save if you modified the file.

---

### Post by Neds Moar Salt on 2010-06-07
> **itbcn8 said:**
> Wish I could help but I'm new to terminal too.... Where does everyone learn it? Any books I should read?

All you need to know is the way you type stuff in.  You really don't need to memorize commands except for nano (pico or nano on mac), cd, mkdir, rm, cp, cat, echo, export, ls, find, grep, sudo/gksudo, login, chmod, chown.
Commands are like this

(command/executable) (parameters)

And you can pipe the output to a file like this:

(command/executable) (parameter) > (file)

What it does is puts the output of the program into a file for you.

---

### Post by linuxopjemac on 2010-06-07
At the bottom of that file is fine indeed.

---

### Post by GRScott on 2010-06-07
Thanks everyone for the help, I entered the script into the file and rebooted and still no sound. I've checked my sound preferences and all are turned on with no mutes. I don't know what to do now.

Lost in the Ubuntu 10.04 o-zone.

---

### Post by linuxopjemac on 2010-06-07
You did something different somewhere as the original poster of this thread with the same machine does have sound. Can the original poster tell us what kernel he is using and if he installed alsa-backport module.

---

### Post by GRScott on 2010-06-09
Thanks everyone - I decided I had done way too many fixes for the sound and went ahead and reinstalled Ubuntu 10.04. After installation, I entered the script into the file in Terminal and wa-la, I've got sound.

:popcorn:

---

### Post by Parthos on 2010-09-15
> **itbcn8 said:**
> Wish I could help but I'm new to terminal too.... Where does everyone learn it? Any books I should read?

I think the programmers that created Ubuntu know the most about how to use terminal, and they just share it online. Maybe they´ve published a book somewhere...

---

