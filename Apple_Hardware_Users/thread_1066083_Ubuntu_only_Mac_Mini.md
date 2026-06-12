---
title: "Ubuntu only Mac Mini"
date: 2009-02-10
forum: Apple Hardware Users
---

### Post by tanguy on 2009-02-10
Hi everybody,

I have a weird problem that driving me crazy !

When 8.04 shows up i installed ubuntu on my mac mini (1.83GHz Intel Mac Mini).
I screwed up and didn't installed refit before installing ubuntu.
So i've worked with ubuntu until now but i want to reinstall mac os X back to this mac mini and for the moment it is impossible.

I've the black screen of death at startup : "no bootable device".

Now, neither mac mini original install dvd nor external usb drive with mac os x formatted can boot.

The only bootable devices are: hard disk with ubuntu, ubuntu live cd or any i386 bootable cd like windows XP.

I tried a lot of workaround including all possible keyboard combinaisons but none are working anymore.
I also tried the different  solutions i found in those threads:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=770897](http://ubuntuforums.org/showthread.php?t=770897)
[*][http://ubuntuforums.org/showthread.php?t=622328](http://ubuntuforums.org/showthread.php?t=622328)
[*][http://ubuntuforums.org/showthread.php?t=766074](http://ubuntuforums.org/showthread.php?t=766074)
[/LIST]

So the last thing i tried is : 
take the same model (with mac os installed and working) , make a clone of the hard disk and put this hard disk inside the mac mini (open it ...).
But still have the black screen of death.
I wonder where are the boot informations stored because i have completly removed the ubuntu hard disk and it doesn't work ...

Is anyone who can help me ? 

The only thing i will try is to change the aluminium keyboard ... but even with unpluging it it doesn't boot so i'm very suspicious.

Thanks
tanguy

---

### Post by cyberdork33 on 2009-02-11
how are you seeing the bootable devices?

if you still want to use refit, you can download the iso and burn it to a cd.

---

### Post by tanguy on 2009-02-12
I'm not seeing any bootable devices.
When the hard disk with ubuntu installed is inside, the mac boot on it directly.
When there is a (mbr?) bootable CD/DVD (ubuntu live cd or windows XP) the mac boot on it before booting on the hard disk.

But it doesn't boot od mac dvd -> "no bootable device" message
and it doesn't show a boot select screen event if with alt pressed. (actually no combinaison is working even pram reset)

And i've test with refit by burning the iso, but it don't want to boot on it too.

I borrowed a pc usb keyboard this morning and try to change it and see if i can doing something (like alt or c) on the boot sequence.

---

### Post by tanguy on 2009-02-12
It's unbelievable, the keyboard fix all....
I just plug an dell usb keyboard instead of the mac aluminium one and i can now boot either on mac or ubuntu...

I don't understand how this can happen.
The keyboard is loaded together with boot of the mac mini ? 
If someone can explain me how this can happen i would be very happy and i could sleep tonight.

Thanks cyberdock anyway!

tanguy

---

### Post by cyberdork33 on 2009-02-12
i believe you have run into one of the apple keyboard firmware bugs. Make sure you update the firmware of your Mac mini and it may fix the problem.

---

