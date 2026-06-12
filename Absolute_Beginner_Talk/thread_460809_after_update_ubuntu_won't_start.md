---
title: "after update ubuntu won't start"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by obb2007 on 2007-06-01
installed some update, that included kernel update and was prompted to restart. after i did, the ubuntu splash started to load and was stuck. every time. do i need to install everyhting now? if i do, how do i know it won't happen in the nest time i update?

---

### Post by AtrejuT on 2007-06-01
That really should not happen...

Can you press
```

ctrl+alt+f1

```
as soon as the bootup splash appears? That should bring you to a console and hopefully give us some more info on where it is stuck.

Did you try booting in recovery mode?

---

### Post by obb2007 on 2007-06-01
no. nothing. it just stuck right after the splash screen loads.

---

### Post by AtrejuT on 2007-06-01
OK, so maybe try the following: You still get to grub and to select which kernel you want to boot, right?
So if the old kernel is still on the list you could try booting that one.

You can also try pressing 'e' in grub, then go down one line, press 'e' again go to the end of the line and remove the 'quiet splash' there. Press Enter and then press 'b'.
 Let me know what happens.

---

### Post by khardbored on 2007-06-01
Basically we need to know where the system is hanging during the loading process. The usplash screen is just a nice graphic to look at while Linux goes through all the needed inits for startup. By doing what atrejut said, we'll be able to figure out where she is hanging and get you fixed. I really suggest you take his advice, good luck!

---

### Post by HobbitCy on 2007-06-01
this happened to me aswell
but it was the second time i had installed ubuntu on the pc within a 2 day period so i just thought i did something wrong
the grub screen gives me a choice of the new .16 or .15 the .15 works fine .16 stick on boot screen
am i missing anything by being in .15 instead of .16 im a very basic beginner

---

### Post by khardbored on 2007-06-01
You should do what was suggested before as well.

You can also try pressing 'e' in grub, then go down one line, press 'e' again go to the end of the line and remove the 'quiet splash' there. Press Enter and then press 'b'.
Let me know what happens.

That way we know where it's hanging up with the new kernel.

---

### Post by AtrejuT on 2007-06-01
But for the time being you can also just run it on the .15 kernel.
There will be nothing different that you'll notice (I think)

---

### Post by RomeReactor on 2007-06-01
> **AtrejuT said:**
> OK, so maybe try the following: You still get to grub and to select which kernel you want to boot, right?
So if the old kernel is still on the list you could try booting that one.

You can also try pressing 'e' in grub, then go down one line, press 'e' again go to the end of the line and remove the 'quiet splash' there. Press Enter and then press 'b'.
 Let me know what happens.

Hi. Alternatively, you can just press ALT+F2 while the system is loading; that switches it verbose.

---

### Post by fanpan on 2007-06-01
Same problem here. After starting in the recovery mode I get the following:

[   27.75995]  hde: dma-timer-expiry: dma status == 0X24
[  37.739879] hde: DMA interupt recovery
[  37.739879] hde: lost interupt

These lines are repeated continuously.

Interestingly, my other computer starts up without any problem. One of the differences is I have SATA drives in the computer that hangs. I have had some problems wirh SATA drives in Ubuntu in the past.

Any ideas?

---

### Post by Azzuron on 2007-06-01
I discovered this same issue when i boot in recovery also.  Kernel -15 works fine, i didn't notice it trying to access hd* at all during the startup, i think this issue has to do with the sata modules not getting loaded. Ive read in a thread that you can add the module piix to the modules file and rebuild your initramfs and it should fix the issue. ill be trying that this second and ill post results.

   --Dave

---

### Post by fanpan on 2007-06-01
Found the solution in another thread.

gksudo gedit /etc/fstab

change the sd* references to hd*

After this, I was able to boot up without problem

I hope this helps.

---

