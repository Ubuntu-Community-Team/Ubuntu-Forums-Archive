---
title: "Modprobe &amp; ndiswrapper"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by M0rThden on 2007-03-26
Ive had problems with this before. Earlier my problem was that the ndiswrapper that came with ubuntu is the wrong version. Now i got the right version and now its working a bit better. Its now finding my wireless card correctly 

```
shatcher@shatcher-laptop:~$ ndiswrapper -l
tmimo3p : driver installed
        device (17CB:0002) present
```

So as i learned, the next step was to enter depmod -a. I dont get any errors with it. It turns out to look like this

```
shatcher@shatcher-laptop:~$ sudo depmod -a
shatcher@shatcher-laptop:~$ 

```

When i type in modprobe ndiswrapper. Everything freezes and i have to force a restart by pushing down the pwr button. The card if it helps is a Linksys WRT54GX4. 

Any information would help...im missing my wireless.

---

### Post by undertherift on 2007-03-27
I've never had that problem, but i'd start by seeing whats happening.

Can you try modprobe -n ndiswrapper ?

-n --dry-run
    This option does everything but actually insert or delete the modules (or run the install or remove commands). Combined with -v, it is useful for debugging problems.
source: [http://www.die.net/doc/linux/man/man8/modprobe.8.html](http://www.die.net/doc/linux/man/man8/modprobe.8.html)

Did you run ndiswrapper -m? 

I've never seen that driver before - with my linksys cards, its always been a Broadcom 43xx.  Are you sure you're using the correct driver?

Sorry for basic questions, just covering groundwork.

---

### Post by M0rThden on 2007-03-27
When i run 'ndiswrapper -m' this is what i get...

```
shatcher@shatcher-laptop:~$ sudo ndiswrapper -m
Password:
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
shatcher@shatcher-laptop:~$ 
```

The 'modprobe -n ndiswrapper' command comes up with nothing.

Here is the whole modprobe command line...

```
shatcher@shatcher-laptop:~$ sudo modprobe -n --dry-run -v ndiswrapper
insmod /lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko 

```

Im going to try 'sudo modprobe ndiswrapper' and see what happens.

---

### Post by M0rThden on 2007-03-27
Ok then...

When i do the 'sudo modprobe ndiswrapper' this is what i get...

```
shatcher@shatcher-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

I might try to uninstall and reinstall to get rid of all the files and try it again with the 'ndiswrapper -m' command before the 'modprobe ndiswrapper'

---

### Post by undertherift on 2007-03-27
Wait! 

Before you do all that, check this thread out.
[http://www.linuxquestions.org/questions/showthread.php?t=498542](http://www.linuxquestions.org/questions/showthread.php?t=498542)

Sounds like they've got it solved.

---

### Post by kerry_s on 2007-03-27
Use "ndisgtk" it's a gui for ndiswrapper. After you install it you'll find a menu entry for install windows drivers.

---

### Post by M0rThden on 2007-03-28
> **undertherift said:**
> Wait! 

Before you do all that, check this thread out.
[http://www.linuxquestions.org/questions/showthread.php?t=498542](http://www.linuxquestions.org/questions/showthread.php?t=498542)

Sounds like they've got it solved.

yup that looks like that would help!

Thanks alot!

---

### Post by undertherift on 2007-03-28
My pleasure, enjoy your wireless system.

---

