---
title: "Urgent help!!!"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by D_D_T on 2007-08-04
Please help! I'm rather new to Ubuntu and am rather worried.
I recieved an update from Ubuntu and was told to restart my computer (Toshiba Satellite Pro A60). On restart all was going well until there was an "Unexpected Inconsistancey; Run fsck Manually" it said that the fsck died with exit status 4
I have no idea how to run a file systems check manually in maintainence mode. I think that it was supposed to start automatically, but the maintenece shell failed to start. It said:
bash: no job control in this shell
bash: groups: command not found
bash: The: command not found
The program "apt-get" is currently not installed (but it is????). You can install it by typing apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
bash: The: command not found
The program "apt-get" is currently not installed...."
bash: apt-get: command not found
root@myname:~#

What do I do?? Help me please!

---

### Post by laidback on 2007-08-04
I'd run the Live CD again and try the recovery option, if that fails try reinstalling. Perhaps your hdd has failed? You could try a reformat from the Live CD by running Gnome Partition Editor, that'll tell you whether the drive is still seen.

---

### Post by D_D_T on 2007-08-04
why would the hdd just fail like that though?
I'll give the live CD a go and let you know. Thank you!

---

### Post by D_D_T on 2007-08-04
erm... there is no recovery mode on my live cd. only a safe graphics mode, a memory test, install with driver update CD, and some other stuff that prob won't help. Should I go for the memory test or safe mode?

---

### Post by Tux Aubrey on 2007-08-04
I have always wanted to say this (sorry):  **Have you tried turning your computer off and then on again?**

Seriously - today's update did the same to me (although I saw no error messages as I was getting a coffee) - dead as a Dodo.  I hard booted and fsck ran on one partition then back to Gnome.

EDIT: Safe Mode is Recovery - but its just a terminal - you will need run fsck from there.

---

### Post by D_D_T on 2007-08-04
yeah I tried that!! First thing I did. Usually fixes everything but not this time. :(

---

### Post by D_D_T on 2007-08-04
erm, the safe mode comes up saying that the X server failed to start and is now disabled. i've got a commandline up with ubuntu@ubunt:~$ what should I do?

---

### Post by atomkarinca on 2007-08-04
you can try
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by D_D_T on 2007-08-04
how do I run fsck from a terminal?
Thanks for all your help people.

---

### Post by RudolfMDLT on 2007-08-04
"fsck" or "sudo fsck"

If your drives are still mounted, please insert the live disk - boot up and in the terminal, "sudo fsck".

Goodluck,

Rudolf

---

### Post by D_D_T on 2007-08-04
so the command "sudo fsck" results in :
fsck 1.40-WIP (14-Nov-2006)

and then returns to:
ubuntu@ubuntu:~$

I am completely lost. does that mean that I can reboot now from the hard-drive? What should I do?
Thank you so much and apologies for absolute noobiness!

---

### Post by atomkarinca on 2007-08-04
> **D_D_T said:**
> apologies for absolute noobiness!

that's never a bother. i think you're good to go. you can always post back here if it doesn't work again.

---

### Post by philinux on 2007-08-04
I had this happen to me last week after an update it would start to load then drop out to command line telling me to run fsck. Can't remember the syntax but it fixed some corruted blocks and am up and running again. I think you can type in fsck --help or something. someone with more experience can tell you what to type.

---

### Post by D_D_T on 2007-08-04
phew! it's booted up again. thankyou for your help! So much appreciated!
Thank you!!
:)

---

