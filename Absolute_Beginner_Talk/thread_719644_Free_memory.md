---
title: "Free memory"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-09
When I ran free, this is what I came up with: office@office-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        384768     379692       5076          0      54672     127616
-/+ buffers/cache:     197404     187364
Swap:      1116476      82140    1034336


Does that look right in the fact im only using 5,076?  Any more ideas on things I can try to get the peak out of my machine?  Its not all that powerful, but better then my old Windows 2000 machine

---

### Post by halitech on 2008-03-09
daryl@ubuntu:~$ free
................total       used       free     shared    buffers     cached
Mem:........905588     541368     364220          0       9700     125172
-/+ buffers/cache:     406496     499092
Swap:      2650684      34856    2615828

actually looking at yours, you have 5076 free out of 384768. might be easy to look at if you get the numbers lined up so they are in place :)

edit: well darn, mine did the same thing :(

---

### Post by szymon_g on 2008-03-09
szymon@linugrat:~$ free -m
                  total       used       free     shared    buffers     cached
Mem:          2025       1966         58          0        25       1518
-/+ buffers/cache:        422       1603
Swap:          854         33        821

anyway: unused RAM is a wasted RAM

---

### Post by jfinkels on 2008-03-09
> **sox fan Matt said:**
> When I ran free, this is what I came up with: office@office-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        384768     379692       5076          0      54672     127616
-/+ buffers/cache:     197404     187364
Swap:      1116476      82140    1034336


Does that look right in the fact im only using 5,076?

Actually, it looks like you only have 5,076 bytes free...Note the large swap usage, that means your processes are using a lot of memory, in fact, they are using more memory than you have RAM, so they are writing to disk (i.e. your swap partition).

Type```
free -m
```to see memory usage in terms of MB, which may be easier to read.

---

### Post by sports fan Matt on 2008-03-09
What Can I do to lower the swap number so I can free memory without having to go back to Windows?  It does seem sluggish but im not sure what I can do to fix it..When I initially set it up, I used the entire disk..Is that a bad thing?  I dont want Wiondows back, I just want to decompress a little bit the Linux partition but unsure if its possible...(Am i making any sense)

---

### Post by jfinkels on 2008-03-09
> **sox fan Matt said:**
> What Can I do to lower the swap number so I can free memory without having to go back to Windows?  It does seem sluggish but im not sure what I can do to fix it..When I initially set it up, I used the entire disk..Is that a bad thing?  I dont want Wiondows back, I just want to decompress a little bit the Linux partition but unsure if its possible...(Am i making any sense)

I don't really understand what you are trying to ask here....

The amount of memory that you are using at any given time depends on the number and kind of processes you are running...for example, if you have twenty firefox windows open, each with a dozen tabs, you will be using a lot of memory.

How much memory (RAM) does your computer have? How big is your swap partition? What is the layout of your other partitions?

Your swap partition should be about double the size of your RAM.

If you want to resize your partitions, boot from a Live CD, run GParted, the graphical partition manager, by typing at the terminal ```
gksudo gparted
``` and resize to your heart's content. Be sure to backup your data before resizing your partitions.

---

### Post by sports fan Matt on 2008-03-09
My question is: Do these Figures look about right as far as memory usage and should I be concerned about things as far as thr swap/memory/way it is used?  Just wondering if those figures from "free" look acceptable or is there something i need to change to get the least amount of ram being used when I run applications (Sorry I cant explain it more clearly, justt trying to find the right words to describe my question) 

Free yields:              total       used       free     shared    buffers     cached
Mem:       384768            318080            66688          0           6468           153008
-/+ buffers/cache:     158604     226164
Swap:      1116476     107140    1009336

---

### Post by prshah on 2008-03-09
Yes the figures are fine. You have 384 mb RAM, and about 50% is in use as cache memory. This memory will be freed up as and when programs request more memory. Having very low figures for free memory is common, eg:

```

Mon Mar 10 00:56:01 ~:$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        988         13          0        258        341
-/+ buffers/cache:        389        612
Swap:         1435         34       1401
Mon Mar 10 00:56:08 ~:$ 

```

However, if you feel the system is sluggish, maybe you would be better off with Xubuntu.

Also try reducing your display colors to 16 bit ("sudo gedit /etc/X11/xorg.conf", find DefaultDepth and change it to 16 from 24/32. Save, Close, and then restart the X server with Ctrl+Alt+BkSpace.

This will make a big difference if you are using onboard graphics.

Turning off compiz will also give a huge performance boost.

Cheers,
PRShah

---

### Post by sports fan Matt on 2008-03-09
Started fine EXCEPT i on boot got this really wierd blue lined screen for about 2 seconds after I changed the display,,What caused it, and is it a bother, can i get rid of ir or must i live with it?

---

### Post by sports fan Matt on 2008-03-09
Im installing Xubuntu now through symnpatic..Hopefully it will be just as easy to use and Configure just like Ubuntu :)

---

### Post by sports fan Matt on 2008-03-09
I think i'll stick with xubuntu for now..is the command to remove ubuntu desktop sudo apt-get remove ubuntu desktop?

---

### Post by forestpixie on 2008-03-09
I'm not sure as I've never installed ubuntu that way - always started from there and added kubuntu or xubuntu in which case the command was 

sudo aptitude remove kubuntu-desktop 

I guess if you did a pt-get remove ubuntu-desktop - that's what would go (just the meta package)

unless you've got storage space issues you could just leave the ubuntu one where it is 

this page might help to get rid of the old ubuntu stuff but I'm not too confident

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by prshah on 2008-03-10
I wouldn't recommed you try something like that: installing gnome, then xfce (Xubuntu) then removing gnome is not something that I'd try.

If you need the diskspace, go ahead but be prepared for a reinstall by downloading the Xubuntu live CD.

Cheers,
PRShah

---

