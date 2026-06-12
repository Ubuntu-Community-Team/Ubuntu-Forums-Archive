---
title: "no boot ibook g4 8.04"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by zeus123 on 2008-04-29
Ive just installed xubuntu 8.04 on my ibook g4. 

When I boot I get a blank screen after yaboot. I had this on xubuntu 7.10 but after following these steps the problem was resolved......
"Fire up the terminal and edit /media/disk/etc/yaboot.conf, adding the nosplash and video=ofonly arguments to each of the boot image entries. After saving and exiting, run sudo ybin --config /media/disk/etc/yaboot.conf -v to apply the changes you just made. Next add ide-core to /media/disk/etc/initramfs-tools/modules and run sudo update-initramfs -u /media/disk/etc/initramfs-tools/modules. " 

So I booted up from a live cd to do the same as I did with 7.10. But I cant take the same steps because my hdd doesnt show up when im running from a live cd. 

Is there any way around reinstalling 7.10 and updating to 8.04? 

Many thanks
Rik

---

### Post by toyota_f1 on 2008-04-29
have you tried just doing the

live video=ofonly

at yaboot prompt?

When I boot the 8.04 xubuntu daily on my g3 after this point it takes a while, at least 5 minutes of blank screen and then eventually hits the desktop.

---

### Post by avtolle on 2008-04-29
I don't know if this will be of any help, but this is what I did to edit the /etc/X11/xorg.conf file for my g4 Cube to get around the blank screen on boot (kept getting the error message that no screen is open, as I recall). HTH.

[http://ubuntuforums.org/showthread.php?t=772808](http://ubuntuforums.org/showthread.php?t=772808)

---

### Post by stream303 on 2008-04-29
And with Hardy 8.04, I'm pretty sure you won't need to manually add ide-core - I think that issue has been resolved.

(Update - Yup, I blew it - I just reread your message and see that you are having problems with the hard disk in the first place.  Ok, keep the following as a back-burner note. :) )

So like toyota_f1 said, at the second-stage of the yaboot boot: prompt, just hit -tab- to stop the countdown, and issue
```
live video=ofonly
```

If that brings up the system, you can then make that setting permanent in /media/disk/etc/yaboot.conf by adding video=ofonly in your append= lines

sudo nano -w /media/disk/etc/yaboot.conf

edit your append line to look something like this:

```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        **append="video=ofonly"**

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        **append="video=ofonly"**
```

And then perform ybin on it to let the system know of the change:

```
sudo ybin -v -C /media/disk/etc/yaboot.conf
```

Now that I've opened my big mouth, I wonder if using **nosplash** instead of video=ofonly might be a better option.. :)

---

### Post by avtolle on 2008-04-29
> **stream303 said:**
> And with Hardy 8.04, I'm pretty sure you won't need to manually add ide-core - I think that issue has been resolved.

(Update - Yup, I blew it - I just reread your message and see that you are having problems with the hard disk in the first place.  Ok, keep the following as a back-burner note. :) )

So like toyota_f1 said, at the second-stage of the yaboot boot: prompt, just hit -tab- to stop the countdown, and issue
```
live video=ofonly
```

If that brings up the system, you can then make that setting permanent in /media/disk/etc/yaboot.conf by adding video=ofonly in your append= lines

sudo nano -w /media/disk/etc/yaboot.conf

edit your append line to look something like this:

```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        **append="video=ofonly"**

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        **append="video=ofonly"**
```

And then perform ybin on it to let the system know of the change:

```
sudo ybin -v -C /media/disk/etc/yaboot.conf
```

Now that I've opened my big mouth, I wonder if using **nosplash** instead of video=ofonly might be a better option.. :)
It looks like the parameter "video=ofonly" is included in the yaboot.conf file already on the live cd (from my failed attempt to use the live cd in 8.04), so I think using **nosplash** is the better option. I note that use of the alternate install cd for 8.04 finds the hdd without resort to the modprobe ide-core command, FWIW.

---

### Post by stream303 on 2008-04-29
Oh yeah - definitely a big fan of the "alternate" installers here!

Funny how things work - I was perusing some old-world links and came across something that might be nice to try at the second-stage boot: prompt for that HD that is giving him fits:

```
live ide=nodma
```

Maybe?

---

