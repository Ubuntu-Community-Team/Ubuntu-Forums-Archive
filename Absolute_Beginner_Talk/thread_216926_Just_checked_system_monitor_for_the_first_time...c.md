---
title: "Just checked system monitor for the first time...cpu almost at 100%!"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Kevf on 2006-07-16
I have just checked the system monitor for the first time, cause the vans on my barebone were getting a bit noisy. I've just bought a new system (intel 2,6 Ghz, 250 gig hd, and 512 ram) and I found it a litle strange that my barebone was making the sounds of an airplane. 

The only thing I've got running are nine dl's using bit tornado. And the monitor is around 99%! Is this normal?:confused:

---

### Post by christhemonkey on 2006-07-16
What kernel do you have installed?
Find it with this command:
```
uname -r 
```

If you do not already, try using the 686 kernel.
```
sudo apt-get install linux-686 
```
That package always depends on the latest 686 kernel.

---

### Post by Kevf on 2006-07-16
kevf@CC8474-B:~$ uname -r
2.6.15-26-386
kevf@CC8474-B:~$

What exactly does your suggestion changes?

---

### Post by squee on 2006-07-16
Hi, I found with 686 that the shutdown doesnt work properly. I've started a thread on [http://www.ubuntuforums.org/showthread.php?p=1260722#post1260722](http://www.ubuntuforums.org/showthread.php?p=1260722#post1260722) if anyone has similar problems or just wants to help. 

As of 3.47pm GMT  16 july the problem still isnt fixed and any help will be greatly appreciated. The problem is that my hard drives (2) shutdown but the fans and moniter still work. See the link above for more details.

Thanks

---

### Post by christhemonkey on 2006-07-16
It installs a new kernel, one that is compiled more specifically for your architecture.
So it can take advantage of improved instruction sets and stuff.
Read here for an introduction to x86 architectures:
[http://en.wikipedia.org/wiki/X86](http://en.wikipedia.org/wiki/X86)

---

### Post by Drakkor on 2006-07-16
I also installed the 686 kernel and had some sort of problem after that, I
can't remember what it was so I went back to the 386 kernel.

---

### Post by MaximB on 2006-07-16
> **squee said:**
> Hi, I found with 686 that the shutdown doesnt work properly. I've started a thread on [http://www.ubuntuforums.org/showthread.php?p=1260722#post1260722](http://www.ubuntuforums.org/showthread.php?p=1260722#post1260722) if anyone has similar problems or just wants to help. 

As of 3.47pm GMT  16 july the problem still isnt fixed and any help will be greatly appreciated. The problem is that my hard drives (2) shutdown but the fans and moniter still work. See the link above for more details.

Thanks

I suggest you to pose a new thread or countnue YOUR old one
that way people will see your thread question first and deside if they can help you or not.

---

### Post by Kevf on 2006-07-16
Ok got the other kernel installed, last lines from the terminal:

Found kernel: /boot/vmlinuz-2.6.15-26-686
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/vmlinuz-2.6.15-25-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up linux-image-686 (2.6.15.24) ...
Setting up linux-restricted-modules-2.6.15-26-686 (2.6.15.11-3) ...

Setting up linux-restricted-modules-686 (2.6.15.24) ...
Setting up linux-686 (2.6.15.24) ...


So I guess this should do the trick? Or do I need a reboot? :-k

edit: and tnx for the advice so far!

edit 2: oops missed the reboot-icon on top of the screen, sorry!

---

### Post by christhemonkey on 2006-07-16
You do need to reboot yes.
And when you do, press `esc` while grub is loading.
This will bring up the grub menu where you can select the kernel you want.
(you will probably want the one you just installed!)

Then load your torrents and system monitor and see what CPU usage is like.

---

### Post by Kevf on 2006-07-17
tnx for the advice! Also without the esc linux is using 686. System monitor does look a bit better 8)

---

### Post by christhemonkey on 2006-07-18
Im glad.
If you want to see what is taking up more CPU time and system usage, 
you can go to a terminal and type:
```
top
```

---

