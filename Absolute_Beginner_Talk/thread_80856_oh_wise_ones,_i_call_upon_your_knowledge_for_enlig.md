---
title: "oh wise ones, i call upon your knowledge for enlightnment! :) (kernel panic)"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by wishyjr on 2005-10-23
hello lovely ubuntu ppl,

i seem to have binned my ubuntu. I was using the ubuntu updater thingy and selected all updates and told it to do its stuff. Everything goes fine and i switch off my pc to go to the pub. When i get back and boot my pc back up again ubuntu throws a kernel panic!

the error i get is:
kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

so.. ive been trying to research into this on the forums but im having little luck. From what i gather, ive updated the kernel but it wont find it to load it (?). Fixes mention something about using a live cd to boot into ubuntu then running a series of commands -something like.. mount the hard drive, goto the boot section of the filesystem, uninstall the kernel, reinstall the kernel etc etc.

 im really stuck here guys. i can get into ubuntu via a live cd but im kinda stuck there. Please aid me oh wise ones!! :)

cheers!

---

### Post by Ampersand on 2005-10-23
Try going into the grub menu during boot (you'll probably need to press Esc when prompted) and see whether there are any older kernels available to boot.

---

### Post by wishyjr on 2005-10-23
hiya, 

yeah, i read that but i cant seem to find any point where im supposed to press esc.

GRUB itself runs fine and to a menu which i always get to (im dual booting with XP) this seems to list kernels as such just the 'generic default', 'recovery' an all that - is that what im looking for? if so, i've tried all of those but its the same error.

oh btw, im running the 2.6.10-5-amd64-generic kernel on hoary if that makes any difference

---

### Post by wishyjr on 2005-10-23
<bump!> anyone got any links to post up even?

---

### Post by Kyral on 2005-10-23
Looks like you don't need to hit escape. You are already where it takes you. Look for a Kernel older (lower version) than what you are using

---

### Post by jose1986 on 2005-10-24
I have the same problem, kanotix, mepis, and fedora are doing the same thin to me, i tryed ubuntu awhile ago but found more compatible programs but is gentoo that advanced?  I hear it takes alot of work, I need some sort of linux on this laptop.

---

### Post by wishyjr on 2005-10-24
hi guys, thanks for replying.

all of the kernels on the list are the same version, theres just generic-default, recovery, generic and generic recovery... and windowXP. They are all my options. Ican boot to XP ok but all of the ubuntu ones lead me to the kernel panic!! :(

---

### Post by wishyjr on 2005-10-24
ok, having done a bit more reading i think i need to mount my hd from a live cd. tried it and it tells me i need to specify the filesystem, not sure where though, ive been running

mount /dev/sda1 /mnt/linux

any idea where i add the filesystem? also, im not sure if 'sda1' is correct. Its a SATA drive and the only one in my pc at the mo, would it be sda0? is there a way of displaying my filesystem? suppose not without mounting it first :)

this.. is.. annoying. :)

---

### Post by Kyral on 2005-10-24
stick "-t <filesystem>" after mount

If you want to know your device name, do sudo fdisk -l

---

### Post by komedycody on 2005-10-24
WTL mate :)

---

### Post by Kyral on 2005-10-24
[QUOTE=komedycody]WTL mate :)[/QUOTE]
"WTL"?

---

### Post by wishyjr on 2005-10-24
yeah... WTL?? :)

well i got my kernel updated but it doesnt seem completely solved my problem, x still doesnt start. but i can access my system without using the live cd now.


think i might give up and install breezy instead. anyone know how i can copy my home directory to a blank cd through the terminal?

cheers

---

### Post by Kyral on 2005-10-24
I meant I dont know what "WTL" means ;P

Anyway try a "sudo dpkg-configure xserver-xorg"

---

### Post by wishyjr on 2005-10-25
LOL - i dont know what WTL means either!! thats why i said 'yeah(?)... WTL?' as if to ask what komedycody meant. :)

anyways.. i'll give that a try, thanks. Could you elaborate on what it is that command does? at a guess i'd say it runs the configuration package for X -true or am i full of it? :)

thanks again!!

---

### Post by BatsotO on 2005-10-25
Something wrong with the superblock. hard drive problem maybe, i dont know for sure.
Try boot from live cd or slack cd and do e2fsck -y /dev/hda1 maybe?

---

### Post by wishyjr on 2005-10-25
hello...

try waht you suggested Kyral but the command wasnt found! is your code correct?

and mr. BetsotO, what is a superblock!? and.. what is/does your command do?

thanks guys :)

---

### Post by Mustard on 2005-10-25
wishyjr, might I suggest (as an alternative option) that you try the IRC help channel for ubuntu at irc.freenode.net in channel #ubuntu.  You might find you are able to find your answers a little faster than via the forum.

[IRC information in the wiki]("https://wiki.ubuntu.com/InternetRelayChat?action=show&redirect=IrcChannels")

---

### Post by az on 2005-10-25
[QUOTE=wishyjr]hello...

try waht you suggested Kyral but the command wasnt found! is your code correct?

and mr. BetsotO, what is a superblock!? and.. what is/does your command do?

thanks guys :)[/QUOTE]

Try

sudo apt-get install ubuntu-desktop.

If that spits out an error, try
sudo apt-get -f install
first.

---

### Post by MichaelM on 2005-10-25
[QUOTE=wishyjr]hello...

try waht you suggested Kyral but the command wasnt found! is your code correct?
[/QUOTE]
That should be "sudo dpkg-**re**configure xserver-xorg". :)

---

### Post by wishyjr on 2005-10-26
cheers guys, i worked out the command was 'reconfigure' from another thread and it ran but threw back an error.

Yeah, when i get time to wok on this properly (im a bit busy these days) i'll take a look at the IRC channel cheers!

azz - i'll give it a shot when i get home from work, thanks :)

---

### Post by wishyjr on 2005-10-26
well... 

azz, cheers for the advise mate but im just getting unmet dependancy errors. This just seems too steep to climb, can anyone suggest the best way to copy over my /home?

thanks

---

### Post by Kyral on 2005-10-26
Sorry for disappearing, got VERY busy.

Now whats going on. I'm confused...

---

### Post by wishyjr on 2005-10-26
well, from what i gather X wont start, and ive just realised that it hasnt been able to load the NVIDIA module. this im assuming is why. so what should i run now to get my nvidia drivers/module setup?... again.

is there anything else i'll probably need to fix after changing the kernel? This really is heart breaking, when my system starts the kernel just looks a mess with half of everything failing.

---

### Post by Kyral on 2005-10-26
sudo apt-get install nvidia-glx

Don't lose hope. Think of it as a crash course in how to fix Linux. After you are done everything will seem like CAKE in comparison :D

---

### Post by Qrk on 2005-10-26
The problem also could be the restricted modules for your new kernel. The xserver loads nvidia, but it isn't supported by your kernel. You may have the nvidia-glx package from your old one, but your new kernel won't support it. 

sudo apt-get install linux-restricted-modules-386

Note the 386. If you installed a kernel for a different arcitecture, you have to install those restriced modules. (K7 or 686, for example)

edit: use the one for amd 64

---

### Post by wishyjr on 2005-10-26
ok, thanks for the support guys.

i ran those commands and they went through fine. rebooted but the kernel still ran like a sack of dog vomit so i thought i'd reconfigure  the xorg file. I came to the desired default colour depth screen and i chose 24bit (as it defaulted to that and thats what i used before) then suddenly the process stops throwing back an error reading something about:


overwriting possibly-customised configuration file /etc/X11/xorg.conf


any ideas on this one?

---

### Post by Kyral on 2005-10-26
Well, did it work before?

Wait is this when you reconfigure after installing NVidia GLX?

---

### Post by wishyjr on 2005-10-26
yes and yes :)

---

### Post by Kyral on 2005-10-26
Then allow sudo dpkg-reconfigure or whatever it is to overwrite the file ;P

---

### Post by sisko on 2005-10-26
[QUOTE=wishyjr]
well i got my kernel updated but it doesnt seem completely solved my problem, x still doesnt start. but i can access my system without using the live cd now.

think i might give up and install breezy instead. anyone know how i can copy my home directory to a blank cd through the terminal?

cheers[/QUOTE]
**wishyjr**, m'man.  Question.  You skipped a step or 12 here.  Somewhere between booting up with the Live CD and here you got your kernel updated.  Where/how did you do that?  I'm following the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=56835&highlight=kernel+compilation"), but to no avail.  Oh, I'm able to compile a kernel or two while in the Live CD, but the first one I successfully compiled fails miserably at startup, and the second one... well, let's just say that all of a sudden it doesn't like the "sudo dpkg -i kernel-image-2.6.10-custom_10.00.Custom_i386.deb" command.  Help!!!!

---

### Post by wishyjr on 2005-10-27
sorry, should have documented what i was doing! :) Sisko, i was using this thread to help me:

[http://www.ubuntuforums.org/showthread.php?t=36573&highlight=kernel+panic+update](http://www.ubuntuforums.org/showthread.php?t=36573&highlight=kernel+panic+update)

basically, i updated my sources.list file with breezy repos (im running hoary at the mo) and used it to grab a newer 'breezy kernel'. 

and Kyral, how do i go about allowing dpkg-reconfigure to overwrite the file (as if you didnt know i was going to ask that ;) LOL! ) ..time for my next lesson in the crash course of linux fixing! :)

btw Kyral - i noticed you use an anime avy, must say im a big fan of anime too! although i dont recognise the character you use.

---

### Post by sisko on 2005-11-09
Oh yeah, we're still not up and running.  HEEEEELLLLLLLLPPPPPPPPP!!!!!!!!!
](*,) ](*,) ](*,) 
The Linux Gods frown upon me.  I feel so unworthy...
:cry:

---

### Post by Kyral on 2005-11-09
[quote=wishyjr]sorry, should have documented what i was doing! :) Sisko, i was using this thread to help me:

[http://www.ubuntuforums.org/showthread.php?t=36573&highlight=kernel+panic+update]("http://www.ubuntuforums.org/showthread.php?t=36573&highlight=kernel+panic+update")

basically, i updated my sources.list file with breezy repos (im running hoary at the mo) and used it to grab a newer 'breezy kernel'. 

and Kyral, how do i go about allowing dpkg-reconfigure to overwrite the file (as if you didnt know i was going to ask that ;) LOL! ) ..time for my next lesson in the crash course of linux fixing! :)

btw Kyral - i noticed you use an anime avy, must say im a big fan of anime too! although i dont recognise the character you use.[/quote] 1) Its Keitaro Urashima from Love Hina

2) I'm an idiot, that line is telling you that it IS overwriting it


Sisko, why exactly do you want to upgrade your kernel?

---

### Post by sisko on 2005-11-09
[QUOTE=Kyral]Sisko, why exactly do you want to upgrade your kernel?[/QUOTE]
I don't want to upgrade my kernel, I want to fix it.  Tried an update using the Synaptic manager, obviously it failed, and I got the infamous "kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)" error.  I've tried to recompile my kernel, to no avail, so now I say "HELP!".:confused:

---

### Post by Kyral on 2005-11-09
It should have left you with the OLD kernel...in GRUB

---

### Post by sisko on 2005-11-09
[QUOTE=Kyral]It should have left you with the OLD kernel...in GRUB[/QUOTE]
If it did, the restore/recover version isn't working.

---

### Post by wishyjr on 2005-11-10
yeah, i found that when mine went wrong -it just didnt leave the old kernel there. 

well, alas i gave up in the end. I'd leant enough for one catastrophy so i grabbed Explorerfs (or something) for windows and backed up my ubuntu stuff then used the situation to upgrade to Breezy.

Gutted to see that you're still having problems Sisko - wish i could help. Are you running Hoary? im guessing so from the kernel your using -maybe time to upgrade too?

---

