---
title: "[SOLVED] beep on start from sleep"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by magicman5421 on 2008-02-05
when I start my computer up from sleep, as in opening the lid, my computer puts out a loud beeping sound. It isn't coming from the speakers as it happens at the same volume whether the volume in ubuntu is muted or at full. I think it happens whether I put it to sleep by closing the lid or through the power button, but i'm not sure. I'm running ubuntu gutsy on an hp dv9500. This doesn't happen with windows btw (i'm double booting).

---

### Post by doddo on 2008-02-05
could it be coming from the pc speaker??

if thats so, try
```
sudo rmmod pcspkr
```

Note the pcspkr will sound no more, but that is for the best I think ...

If it works;
to make it permanent

```
 sudo -s
echo "blacklist pcspkr" >> /etc/modprobe.d/blacklist

```

---

### Post by emarkd on 2008-02-05
Or you could run System > Preferences > Sound, click on the System Beep tab and uncheck the Enable System Beep box.

---

### Post by doddo on 2008-02-05
> **emarkd said:**
> Or you could run System > Preferences > Sound, click on the System Beep tab and uncheck the Enable System Beep box.

That sound a whole lot simpler

By the way, as it turns out, my trick did not work in the first place:
[http://ramblingfoo.blogspot.com/2007/01/how-to-disable-pcspkr-in-etch.html]("http://ramblingfoo.blogspot.com/2007/01/how-to-disable-pcspkr-in-etch.html")

---

### Post by magicman5421 on 2008-02-06
The Preferences>Sound>System Beep thing did not work and as the other thing didn't work for the guy i'm not going to try it. Any other suggestions?

---

### Post by doddo on 2008-02-07
does```

 sudo rmmod pcspkr 
```
Work?

---

### Post by magicman5421 on 2008-02-09
```
me@my-laptop:~$ sudo rmmod pcspkr
[sudo] password for me:
ERROR: Module pcspkr does not exist in /proc/modules
me@my-laptop:~$ 

```
?
Also, after the latest kernel update my sound stopped working. Beep is still here though. Any smart people have a solution for me?

---

### Post by doddo on 2008-02-09
> **magicman5421 said:**
> ```
me@my-laptop:~$ sudo rmmod pcspkr
[sudo] password for me:
ERROR: Module pcspkr does not exist in /proc/modules
me@my-laptop:~$ 

```

This I take it, would mean that the pc speaker kernel module is built into the kernel!!

If this is the case, then I think your only option is to compile a kernel of your own without the pcspkr module. That would fix your issue for sure, but as this is a bit tricky if you've never done it before.
It is also fun.
I really hope there is another option to fix this

could you post here the output of "lsmod"?

What sound card do u have ??

---

### Post by magicman5421 on 2008-02-09
I have no clue how to compile my own kernel. I'll look up a guide. If you want to help with the sound, here is the link to my post.
[http://ubuntuforums.org/showthread.php?t=692359](http://ubuntuforums.org/showthread.php?t=692359)

---

### Post by doddo on 2008-02-09
sure I'll look into it

Here is a little guide i wrote about compiling kernels. The trick with compiling a good kernel is to have a good .config file. These files tend to get better the more times you compile a kernel. When u get a new kernel, your old .config file can generally be used to compile the new one aswell
if yoi ```
 make oldconfig
``` when entering the menu

 [http://blog.abmas.biz/2007/04/30/howto-compile-your-first-26-linux-kernel-a-crash-course/](http://blog.abmas.biz/2007/04/30/howto-compile-your-first-26-linux-kernel-a-crash-course/)

---

