---
title: "Limewire mess"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-04-24
Hi. This should be a quickie. After an aborted attempt to install Lime-Wire-free-4.12.11 I have a locked Desktop icon of the above program which I cannot delete. When I try to use Synaptic PM I get a box popping up which reads:

E: The package LimeWire-free needs to be re-installed, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

All I want to do is get rid of the whole LimeWire shooting match, so's I can get on with box-building. Any clues?
Thank you, Michael.

---

### Post by Seisen on 2007-04-24
have you tried "sudo rm -r nameoffile" in the terminal

---

### Post by MichaelSM on 2007-04-24
Thank you Seisen for your immediate response. In Terminal , I ran 

sudo rm -r

then dragged the offending file into place and hit Enter.
Yes the LimeWire file disappeared from Desktop, but I still get the same errors when I try to use Synaptic. Was I too easy with the dragging? Must be more to it. By the way, I did a re-start as well.

Delighted to hear from someone so quickly.
Cheers,
Michael.

---

### Post by Seisen on 2007-04-24
try deleting these files.

/opt/LimeWire/

/usr/bin/runLime.sh

/usr/share/applications/LimeWire.desktop by using 

sudo rm -r

---

### Post by MichaelSM on 2007-04-24
Hi Seisen. It was several weeks ago, so I can't recall the details. It was very untidy with Java issues and the install was done obviously as sudo and I can't remember why. Permissions for the file were/are 'root'. 
I know that's not much help. 
If I could find where the remnants of it are, I could sudo the file and remove it, I guess.
Thanks again,
Michael.

---

### Post by Seisen on 2007-04-24
Delete these files and see if it works.

```
/opt/LimeWire/

/usr/bin/runLime.sh

/usr/share/applications/LimeWire.desktop
```

---

### Post by MichaelSM on 2007-04-24
You are being helpful and patient.

OK. Tried IT both ways. 

The first, using sudo rm -r and attaching files did nothing. so, I worked with sudo gedit on all three file names, but they were all empty.

I just tried Synaptic in some hope of a difference. Same errors.

Hope I did things right.

Michael.

---

### Post by MichaelSM on 2007-04-24
Hi Seisen. Me again. I just did some homework in File search and found 28 extant entries for LimeWire. Is there a way of deleting them in that area, or should I just wade through them one by one until they're all dead? 
Thank you again,
Michael.

---

### Post by Seisen on 2007-04-24
Try this to see if it works.  

```
dpkg --remove --force-remove-reinstreq limewire
```

---

### Post by MichaelSM on 2007-04-24
Seisen, here's the news:

michael@michael-desktop:~$ sudo dpkg --remove --force-remove-reinstreq LimeWire
dpkg - warning: ignoring request to remove limewire which isn't installed.
michael@michael-desktop:~$ sudo dpkg --remove --force-remove-reinstreq limewire
dpkg - warning: ignoring request to remove limewire which isn't installed.
michael@michael-desktop:~$ 

It never got installed in the first place, looks like it hung up on an issue and can't find a way out or in.

BUGGER! 

I hope I'm not wasting your time.

Thanks again,
Michael.

---

### Post by Seisen on 2007-04-24
Try this to install it and see if it works.

[http://ubuntuforums.org/showthread.php?t=278134]("http://ubuntuforums.org/showthread.php?t=278134")

If that doesn't work PM me and I will help you later when I get back on.

---

### Post by ajmannen on 2007-04-24
Use FrostWire instead, works much better on linix. + you get the same speed as you do in LimeWire pro

---

### Post by MichaelSM on 2007-04-24
Hi. My last hope. Since I've found all the LimeWire files in File Search; I've tried to delete them but don't have permission. All I need to do I suppose is to access the File system as root. I just don't know how to do it!
Any help appreciated.
Best wishes,
Michael.

---

### Post by MichaelSM on 2007-04-24
Hello ajmannen. Frostwire is a pearler, and I'll have it as soon as I can get rid of this LimeWire s@#t. I make up boxes for other people. This box and HD is one I've stuffed up and am trying to fix. The other HDs have Frostwire and work like a dream. I just made a mess of this one late one night. Well, nobody's perfect ...
Thanks for your response.
Cheers,
Michael.

---

