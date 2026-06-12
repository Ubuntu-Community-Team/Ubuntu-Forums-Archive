---
title: "[SOLVED] Ejecting External HDD"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-03
For some reason, when i right-click on my External HDD's icon on the desktop and then click Eject it says 'Cannot eject WD My Book' and then it gives me a message on the bottom right of the screen and opens the file browser pointing to my external HDD.
 
How can I unmount the drive? Until now I have to simply shut down my computer to remove the drive.
 
Also, my HDD has a on/off switch, If I use that while in my Vista, and then try to connect to Ubuntu, it tells me that the drive wasnt shut down properly and so you need log back into Windows and shut down the drive using the 'Safely Remove Hardware'.
 
If i do that and then connect it to Ubuntu...my drive works. Why is this a problem? AFAIK, my drive is even hot swappable..so if i switch it off...it shouldn't matter, Correct ?

---

### Post by LaRoza on 2007-05-03
You have to unmount it first.

Right click it, and choose "unmount".

---

### Post by igknighted on 2007-05-03
> **Inxsible said:**
> For some reason, when i right-click on my External HDD's icon on the desktop and then click Eject it says 'Cannot eject WD My Book' and then it gives me a message on the bottom right of the screen and opens the file browser pointing to my external HDD.
 
How can I unmount the drive? Until now I have to simply shut down my computer to remove the drive.
 
Also, my HDD has a on/off switch, If I use that while in my Vista, and then try to connect to Ubuntu, it tells me that the drive wasnt shut down properly and so you need log back into Windows and shut down the drive using the 'Safely Remove Hardware'.
 
If i do that and then connect it to Ubuntu...my drive works. Why is this a problem? AFAIK, my drive is even hot swappable..so if i switch it off...it shouldn't matter, Correct ?

To unmount the drive you should be able to right click -> unmount.  Or in a terminal, 'sudo umount /dev/sda#' where sda# is the drive to be unmounted.

As for the on/off switch, the short answer is no.  Hot-swappable only means that you can mount it and use it when plugging in while the computer is on.  You still must mount/unmount properly, even in windows.

---

### Post by lepz on 2007-05-03
> **Inxsible said:**
> For some reason, when i right-click on my External HDD's icon on the desktop and then click Eject it says 'Cannot eject WD My Book' and then it gives me a message on the bottom right of the screen and opens the file browser pointing to my external HDD.
 
How can I unmount the drive? Until now I have to simply shut down my computer to remove the drive.
 
Also, my HDD has a on/off switch, If I use that while in my Vista, and then try to connect to Ubuntu, it tells me that the drive wasnt shut down properly and so you need log back into Windows and shut down the drive using the 'Safely Remove Hardware'.
 
If i do that and then connect it to Ubuntu...my drive works. Why is this a problem? AFAIK, my drive is even hot swappable..so if i switch it off...it shouldn't matter, Correct ?

I had the same trouble with my external hd. This worked for me 

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

---

### Post by Inxsible on 2007-05-03
There is no 'Unmount' option on the right click menu. 
 
My hard drive comes up under /media/WD My Book

---

### Post by Inxsible on 2007-05-03
> **lepz said:**
> I had the same trouble with my external hd. This worked for me 
 
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak
 
What does this do exactly ?

---

### Post by silkstone on 2007-05-03
I have the same problem with external HDs in Feisty (though not in Edgy, and not with USB pen-drives), and I've read that there's a bug which can prevent unmounting/ejecting by right-clicking from the GUI.

The solution is to open the terminal and type **eject "WD My Book"**

I think you need the quotes if there are spaces in the name.

Let's know if that works!

---

### Post by Inxsible on 2007-05-03
> **silkstone said:**
> I have the same problem with external HDs in Feisty (though not in Edgy, and not with USB pen-drives), and I've read that there's a bug which can prevent unmounting/ejecting by right-clicking from the GUI.
 
The solution is to open the terminal and type **eject "WD My Book"**
 
I think you need the quotes if there are spaces in the name.
 
Let's know if that works!
 
I shall try that tonight. Hope it works !
 
Still, is there any way to fix the bug so that the graphical way works too ?

---

### Post by silkstone on 2007-05-03
I don't know of a fix, unfortunately.

See [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/36252](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/36252) and scroll down to the recent entries.

---

### Post by Inxsible on 2007-05-03
```

sudo eject /media/"WD My Book"

```
 
removes the mount from the desktop. However the leds on the drive remain "on", making me think that it hasn't really switched off the drive.

---

### Post by silkstone on 2007-05-03
Mmmm.... I'm out of my depth here. :( 

How about **sudo umount /media/"WD My Book"** ?

EDIT/ Right-click on the top panel/bar and select Add to Panel. Look for System Monitor and drag that to the Panel. I have that on the panel all the time. By default it shows the CPU usage, but clicking on it will let you show what drives are mounted and what processes are running. Very useful! If the USB drive is not shown, it is not mounted (whether it is switched on or not). Ubuntu will not necessarily turn off the drive - what matters is whether the data transfer is complete.

---

### Post by Inxsible on 2007-05-03
I already tried that...it does the same thing as eject /media/"WD My Book"

---

### Post by lepz on 2007-05-03
> **Inxsible said:**
> I already tried that...it does the same thing as eject /media/"WD My Book"

Did you try what I told you 6 hours ago?

---

### Post by Inxsible on 2007-05-03
I did try your solution lepz and it didnt work for me. It ejects the drive and immediately mounts it again.
 
I just checked the properties on the drive and in the 'Drive' tab is says
```

Removable: No

```
 
Should it be like that for an external drive?

---

### Post by Leaf on 2007-10-08
I have problems ejecting my external USB HD.

it works in the fact that it unmounts the drive, but IMMEDIATELY remounts it, giving me no time to turn it off after ejecting.  Right now I'm using it read-only, because I cannot stop the hard drive after ejecting!

Is there a command to halt the drive or something?

---

