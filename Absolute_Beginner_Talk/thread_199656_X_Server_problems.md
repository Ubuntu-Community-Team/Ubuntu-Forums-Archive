---
title: "X Server problems"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by melkhior on 2006-06-19
Hi, i just installed Ubuntu 6.06 and i got an x server error that i can't solve:

> 
Fatal Server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on x server ":0.0"
After 0 requests (0 known processed) with 0 events remaining.

I have a Pentium D 820, 1 GB RAM, X800XL and Audigy.

If anyone can help me it would be great.

Thank you in advance and forgive me for my bad english.

---

### Post by munckfish on 2006-06-19
Hi

I'm not an expert on X issues but I'm starting to get the hang of trouble shooting X problems, so here's the things I'd try if I were you:

First thing I'd do is have a look at the X server log file (/var/log/Xorg.0.log) and see if there are any obvious hints as to why this has happened.

Next try googling for "X no screens found" I think there's quite a lot of info on this problem out there.

In order to help you further here I think we'd need you to upload:

[LIST=1]
[*]Your X config file /etc/X11/xorg.conf 
[*]Your X server log file (/var/log/Xorg.0.log)
[/LIST]

With that information hopefully someone may be able to spot the problem.

If you need help fetching those files please ask.

---

### Post by melkhior on 2006-06-19
munckfish, thank you for the fast reply :).

First, I took a look into the log but it was empty.
Then, i thought that i could create a X server file with the info but i don't know how to do it and then how to "upload". If you know the way to do or a FAQ with this information it would be great :D.

I will look in google for this error.

Thank you for all :D

---

### Post by munckfish on 2006-06-19
[QUOTE=melkhior]First, I took a look into the log but it was empty.[/QUOTE]

Ok this may be because X didn't manage to start.

[QUOTE=melkhior]Then, i thought that i could create a X server file with the info but i don't know how to do it and then how to "upload".[/QUOTE]

Hmm, do you mean that /etc/X11/xorg.conf doesn't exist?

[QUOTE=melkhior]If you know the way to do or a FAQ with this information it would be great :D.[/QUOTE]

To fetch and upload copies of these files you'll need to transfer copies of them over to the system you are accessing the forum from. The easiest thing to do would be to use a floppy drive or a USB key to transfer the files between systems.

[LIST=1]
[*]Start your computer and login at the prompt.
[*]Insert your floppy or USB key. The system should automatically mount these and make them available under the /media/ directory. For example I'll use my USB key which mounts as /media/DISGO (this may be different on your system).
[*]You can check the disk/key has been mounted correctly by typing ```
mount
``` and examining the output to see if it's there. If it's not come back to me and I'll give further instructions.
[*]Then run the following commands ([COLOR="Red"]!! Remember to replace /media/DISGO with the correct path to your disk/key !![/COLOR]): 
```
cp /etc/X11/xorg.conf /media/DISGO
cp /var/log/Xorg.0.log /media/DISGO
lspci > /media/DISGO/lspci.txt
ls /media/DISGO
```
[*]The output of the last command will allow you to visually confirm that the files have been successfully copied onto your disk.
[*]Now move to your other system and upload the files here.
[/LIST]

---

### Post by -::Bas::- on 2006-06-23
It's your x800xl that's giving you the headache. Try this: [http://www.ubuntuforums.org/showthread.php?t=200559](http://www.ubuntuforums.org/showthread.php?t=200559)

---

