---
title: "Help needed please, GNOME .ICEauthority error"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Anaraith on 2007-11-20
Hey guys, first off thanks for looking into this thread and helping me. I'm really stuck right now.

Last night I was trying to change it so I could see all my hidden files. I believe I accidentally have changed one of the settings from Read and Write to Access, something along those lines. Now when I try to log in I get the error message:

> 
"The GNOME session manager was unable to lock the file '/home/ross/.ICEauthority/'. Please report this as a Gnome bug. Sometimes this error may occur if the file's directory is unwritable, you could try logging in via the failsafe session and ensuring that it is.


I did some searching on these forums and realized that changing the settings to Access was what caused the problem. I looked through the posts other users have made but have got no where and was wonder if I could get any help. 

I am running Ubuntu Linux 7.04 if this helps.

Any help I would greatly appreciate.

Cheers
Anaraith

---

### Post by markharding557 on 2007-11-20
you could access the partition using a live cd and change permissions that way

---

### Post by Anaraith on 2007-11-20
Thanks for your fast reply but I am completely new to Linux and all so how would I go about doing this?

Cheers

---

### Post by taurus on 2007-11-20
When you first turn on your machine, you will see a GRUB menu (and if you don't see it, you have three seconds to press Esc to display it), move down to the recovery mode (usually the one after the normal kernel) and boot from it.  At the prompt, run

```
chmod 600 /home/ross/.ICEauthority
```
Then, reboot and see if you can log in with your username ross now.

```
shutdown -r now
```

---

### Post by Anaraith on 2007-11-20
I still get the same message as before.

Just to comfirm the GRUB menu should be looking like:

> 
Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Ubuntu 7.04 (7.04) (on /dev/hda1)
SUSE Linux 10.1 (on /dev/hdc2)
Failsafe -- SUSE Linux 10.1 (on /dev/hdc2)


Normally it is the first one that I choose so was I correct to choose the 2nd one on the list to do what you said above?

Thanks for the help!

---

### Post by taurus on 2007-11-20
Yes, pick the second one to boot into recovery mode.

```
**[COLOR="Blue"]Ubuntu, kernel 2.6.20-16-generic (recovery mode)[/COLOR]**
```

Again, boot into recovery mode and run

```
chown -R ross:ross /home/ross
chmod -R 755 /home/ross
chmod 600 /home/ross/.dmrc  /home/ross/.ICEauthority
shutdown -r now
```

Now, can you log in as ross?

---

### Post by Anaraith on 2007-11-20
Yes! I have got in and everything is looking good. I got no error message and everything is just as I left it. Taurus you are a good person. Many thanks to both of you people that have helped in this problem.

Cheers
Anaraith

---

### Post by alexband on 2008-07-17
I registed today just want to say thanks.
Cause I came across the same problem. I searched on the net.
But only this thread clearly and completely solve my problem.

Just thanks!

---

