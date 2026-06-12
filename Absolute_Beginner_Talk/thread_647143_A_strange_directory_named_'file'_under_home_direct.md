---
title: "A strange directory named 'file:' under home directory that keeps being created!"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by zefew on 2007-12-22
I started using Gutsy under Gnome (AMD64 bit version), but I keep getting a
strange directory under my home directory /home/user/ named "file:".  This
happens even when I delete the directory.

Content in the 'file:' directory is empty except that you get several subdirectories:
  /home/user/file:/home/
  /home/user/file:/home/user
  /home/user/file:/home/user/Desktop

Since I see Desktop subdirectory inside, I would imagine the cause is probably
from some gnome application, but I can't figure out exactly where it's coming from.

Does anyone know why this thing keeps being created and from where?
It's becoming a bit of an annoyance to me and I'd be glad to know 
what's happening. Thanks!

---

### Post by Nano Geek on 2007-12-22
Does rebooting help?
I had one of those once and after I rebooted and deleted it, it never came back.

---

### Post by zefew on 2007-12-22
Thanks for your reply. It used to be that "delete & reboot" didn't help as well.
But I just rebooted the machine and so far the 'file:' dir hasn't shown up.

If I launch some gnome application, it might reappear though..

On a second thought, the cause might be due to some leftovers from my
installation of 'kde-desktop' which I uninstalled soon after.
But i'll wait & see if the thing pops up again.

---

### Post by discoade on 2007-12-22
There is a mention of this in the warning section on this page but no mention of a cure....

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by wiresquire on 2007-12-29
I just noticed I have a file: directory in my home (eg /home/wiresquire) directory.

The contents of it are the *same* as the  /home/ directory, and I can browse to the other subdirectories and files. It is *not* a link or anything as best I can tell. 

So, I am paranoid about deleting it, in case it kills my whole install !

Has anyone got any advice on what to do?

TIA
ws

---

### Post by daou on 2007-12-29
It's possibly a bug in a script or a program that tries to do something with the /home directory... a typo, perhaps, where "file:/home" should be "file://home" or something similar

You can try doing a search for all text files on the system if one contains "file:/home"... but if it's in a binary file, it would be a bit more difficult

---

### Post by wiresquire on 2007-12-29
Thanks for your response.

 I tried a reboot and forced a fsck.
Now it seems to only have /home/wiresquire/Desktop (which is empty anyways).
So I will try removing it and rebooting, and see what happens.

Mmmm. The only thing I was messing with tonight was some bluetooth to my phone.

Fingers crossed!
ws

---

