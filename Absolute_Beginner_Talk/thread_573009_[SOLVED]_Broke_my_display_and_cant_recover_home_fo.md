---
title: "[SOLVED] Broke my display and cant recover home folder - help!!"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-10-11
Whilst trying to get realplay working last night so I could watch BBC clips, I seem to have broken my display.  Its a long story so I wont bore anyone with it unless they are really interested :lolflag:

If I have broke it then no problem, il just have to learn from the experience and remember not to do it again.  Im running a fujitsu siemens Amilo PA 1510 laptop and apart from a lot of work in one of the directories in my home folder, there isnt much that I really need to save.  As such, im thinking of just wiping it and installing 7.10 when it is released.  

However......I cant seem to recover my home folder!!!  Ive booted from the live CD and it would seem that I dont have permission to copy the contents of my home folder - I was thinking of just dumping it all on to a memory stick, wiping the thing and starting from scratch.

Can anyone help?

---

### Post by cameronw on 2007-10-11
So by breaking your display do you mean that you have maybe stuffed up your Xorg.conf and X server won't start? For that Envy will do the job. Could you give a little more on the problem.

---

### Post by MikeSz on 2007-10-11
Sorry - yes, I cant start X.  I was uninstalling and reinstalling things like realplay and helix and it also involved playing with a few of the c++ elements (cant remember exactly what the file was called but it was something like libdsptd++5 or similar).  Anyway, I read in here that realplay would work if you moved to ++6 instead of 5 so I did a lot of uninstalling and reinstalling in synaptic.  Unfortunately when I restarted I got just text (after my normal splash screen) saying there was a problem with X and did I want to see the diagnostic file (which meant nothing to me!).

So, thinking that I had broke it (fair enough) I tried to back my home folder up with the live CD.  the files themselves appear, though they have a little red cross in the corner over their icon - as do the individual folders.  If I remember rightly there is also a padlock symbol over the drive icon itself.  When I tried to copy the files from my home folder to the memstick it told me I didnt have permission to read the files as I am not the owner.

Does that help at all?

---

### Post by cameronw on 2007-10-11
Hmmm, the live CD runs as root so it should have the correct permissions to view them. What filesystem is the home dir on? The diagnostic file coming up when you try to start X probably means that the Xorg.conf is corrupted. There may be a command to fix it, although I thought it gives you an option for it to correct itself?

Added: Oh by the way did you restart just after it gave you the diagnostic file dialog? The self repair dialog is after this.

---

### Post by Lunz on 2007-10-11
try reconfigure your xserver again


sudo dpkg-reconfigure xserver-xorg

---

### Post by cameronw on 2007-10-11
If you cannot repair your X server, I had a look at my lost+found folder and found that a lock means that you have no writing privileges, and a red cross  means you have no access to a file at all. Could you try chown in Terminal, and post the output?

---

### Post by MikeSz on 2007-10-11
Cameronw - the file system is just the standard file system, I havent made any changes to it - the machine only runs Ubuntu so its just a standard setup (I only use the machine for work so I havent really changed much from the standard installation other than adding a few media codecs and obviously the theme).  I have restarted it (first thing I did) and after booting to a text style log-on, it pops up a message asking me if I want to view the diagnostic file for X (the whole lot looks like an old MS-DOS editor) - to be honest, I havent selected "no" yet so I dont know what happens if you go for that one but I get the feeling it isnt going to work #-o

On the subject of reconfiguring Xorg - Il give that a try thanks (wont have access to the machine for another couple of hours).  Can I just ask a stupid question there though, where do I enter the above code - wherever I can find a prompt after a failed boot?  i.e. by selecting "no" to the diags box option?

---

### Post by forestpixie on 2007-10-11
> Can I just ask a stupid question there though, where do I enter the above code - wherever I can find a prompt after a failed boot? i.e. by selecting "no" to the diags box option?

no stupid questions - only stupid answers :)

if you say no - you'll get a prompt as you thought enter it then, answer questions as best you can - if you're not sure about driver go for vesa and at the least you'll get in

the other option is to use the backup - you have got one right :)

when you get to the prompt have a look for backups

```
cd /etc/X11
```
```
dir xorg*
```

you should have xorg.conf and hopefully a backup

to replace xorg.conf with the backup

do

```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` 
that assumes name of backup to be xorg.conf.backup obviously - if it's different change the name to suit

---

### Post by FranMichaels on 2007-10-11
Hello,

Try to boot into recovery mode.

To do, restart the machine, when it says Loading GRUB (or something like that)
press escape, then use the down arrow to choose the option with (recovery mode)

I'm not sure what got removed, anyway you should see a prompt now (and you'll be root.)

try

```
apt-get install ubuntu-desktop
```

if nothing is missing and it's just xorg.conf that got messed up

```
dpkg-reconfigure xserver-xorg
```

after that's done
type
```
reboot
```

Okay, if this made no difference,

Use your live cd, open up a terminal from Accessories.

Type
gksudo nautilus

That will open nautiuls with root privilege, and you can copy whatever you want. Use it to change the owner later, or you can use chown.

Hope everything works out!

---

### Post by MikeSz on 2007-10-11
Cheers - thats great!  Fantastic help as usual.  I will give those a try when I get home

---

### Post by MikeSz on 2007-10-11
Thanks to everyone who has helped here today - I typed "dpkg-reconfigure xserver-xorg", rebooted and its sorted now!!!  I now have my desktop back and everything is as it was!!!  Thanks a million guys!!!  :guitar:

---

