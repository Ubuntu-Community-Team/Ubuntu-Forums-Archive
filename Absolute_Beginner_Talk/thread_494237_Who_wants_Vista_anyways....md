---
title: "Who wants Vista anyways..."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by csinner on 2007-07-06
Ok, so I really wanted to make my system just Xubuntu, and work from there.

So I did that, but I had the problem where my computer would freeze after a half hour to an hour of work. Total freeze.. Mouse animation is stuck, keyboard and mouse are unresponsive, and program don't respond to any input... Including the passing of time.

So in the interest of getting some work done while sorting out my Xubuntu issues, I installed the windows vista that came with my computer (home premium).
now I have the following setup:
Windows Vista on the first partition of the only harddrive (/dev/sda1)
Linux on the second partition of the only harddrive (/dev/sda3)
and swap space on the third partition of the only harddrive (/dev/sda2)

That is I installed windows on the first partition and then installed linux on the second. Grub didn't set up a widnows boot entry on it's own so I created one:

title		Windows Vista -- Home Premium
root		(hd0,1)
makeactive
savedefault
chainloader +1

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=62c66736-1cc4-4a87-a2be-ce62bccc99f6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

The Ubuntu one is unchanged from what grub had already placed there.

Selecting Windows Vista however has the effect of giving me the classes error 13: invalid or unsupported executable format.

Any and all help is appreciated. Thanks,
~CSinner

---

### Post by Raineer on 2007-07-06
What if you try (hd0,0) ?

---

### Post by kpkeerthi on 2007-07-06
Your Vista is on sda1. So (hd0,0) should work.
```

title Windows Vista -- Home Premium
**[COLOR="Red"]root (hd0,0)[/COLOR]**
makeactive
savedefault
chainloader +1

```

As for the crashing, see if your ubuntu is using swap memory. Open terminal and type **top**. If not, you can force it to use swap memory with the command
```

sudo swapon /dev/sda2

```

---

### Post by csinner on 2007-07-06
I forgot to mention that it was already '(hd0,0)' but i had changed it just to try something different. I changed it back now but it still gives the same error.

I do not know how to continue. Is it possible that the Xubuntu install somehow corrupted my windows installation?

I don't know what else the problem may be.

Is there any way to troubleshoot this?

Thanks,
~CSinner

btw, I just tried that top thing but I dont know how I would see if swap is on or not..

---

### Post by kpkeerthi on 2007-07-06
Can you post the screenshot of the terminal running top command?

---

### Post by csinner on 2007-07-06
I am a newb... I tried the printscr and ctrl+V in gimp but that didnt work... how do I take a screenshot in linux.

Thanks,
~CSinner

---

### Post by Paul820 on 2007-07-06
There is a program in menu->accessories->take screenshot if your printscreen button doesn't work.

---

### Post by csinner on 2007-07-06
ok attached is my top screenshot...

---

### Post by kpkeerthi on 2007-07-06
OK. Ubuntu has recognized your swap partition and I see no problem with it. Not sure why it is crashing.

---

### Post by vexorian on 2007-07-06
I am guessing you got some wireless network driver out there . That's the only think so far that I have seen constantly generating posts about freezes.

---

### Post by csinner on 2007-07-07
Yes I think its the wireless driver as well...

Is there any way to diagnose this?

ANY HELP AT ALL is VERY much appreciated,
~C

Thanks guys..

---

### Post by csinner on 2007-07-08
Take that as a... no?

---

