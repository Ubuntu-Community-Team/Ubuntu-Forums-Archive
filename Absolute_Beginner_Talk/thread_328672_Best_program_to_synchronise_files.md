---
title: "Best program to synchronise files"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by ngch on 2006-12-31
Hi. I am a student who had recently installed Ubuntu Drapper on my laptop. I frequently type essays with my laptop, and back them up to my removable flash drive. In Windows, I use the Synctoy to synchronise the files I am working on between the laptop and the flash drive. Since I sometimes have to work on my essays on other computers, I need a program that can syncrhonise the files both ways, eg. update files on both computer and flashdrive simultaneously.

I've tried Grsync and Unison as a replacement for Windows Synctoy. Grysync is simple and effective, but it lacks the ability to synchronise files simultaneously. Unison can't even work with my flash drive, saying something about 'error setting permission'.

Is there a linux program that can replace Microsoft Synctoy?

---

### Post by psycho78 on 2006-12-31
Hmm if you don't have a problem with the commandline I can recommend rsync (it's in the repos), read the manpage with man rsync in the console...
I can nearly do everything you want :)

---

### Post by psycho78 on 2006-12-31
I found anther one in the repos searching for rsync, it is called drsync, here is the program description:
wrapper for file synchronisation via rsync
drsync is a Perl wrapper for rsync which keeps track of the filelist between
synchronizations. It is ideal for notebook users who want to keep data in two
(or more) different places. It is also good for the Linux PDAs (Agenda, iPAQ,
Yopi, etc.), to keep data synchronized with the desktop.

Sounds like made for you?? :) I never tried it, but why not give it a chance?

---

### Post by ngch on 2007-01-11
thx for the help!

---

### Post by fadder on 2007-01-11
I think unison should work. I use it between portable and stationary PCs, through a USB-disc. Maybe you should try the unison support forum - they seem pretty active.

The advantage of unison over rsync is that is two-way. Spots changes made on either system and sets rsync going to propogate in whicheve direction is needed. One of the best apps I know.

---

### Post by tweedledee on 2007-01-13
> **ngch said:**
> Is there a linux program that can replace Microsoft Synctoy?

I tried all the suggestions above and none worked quite right for me.  Additional ones to try out, that are all java based and can be downloaded from sourceforge (just google the names):
jfilesync (the one I currently use, seems to no longer be in development)
fullsync
capivara (very nice, but doesn't seem to have an option for time difference tolerance (e.g., < 2 seconds consider the same), which I need)

---

### Post by AirOnSkin on 2007-07-03
i read a lot now about file sync tools because i was also searching for piece of software to replace my AllSync which i used under windows.

i shortly tried out unison gtk now and i'm quite pleased with it. it has the two features i definitly need:
1: multiple profiles
2: sync preview

grsync hast these functions too. i think i'm going to use this one because i read a lot about unison having problems with writing on FAT disks... grsync has the abilitie to ignore the filesystem...

i only miss something on both tools (maybe i didn't look right if there is this option). i would like to set some root-directories to sync but exclude (!) some folders in them... does anyone know if there is an option to do that?

so long :)

air

---

