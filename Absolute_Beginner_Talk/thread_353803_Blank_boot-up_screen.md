---
title: "Blank boot-up screen"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by John E on 2007-02-05
I posted this question a couple of weeks ago, without success.

When I boot up from a live CD (Edgy) I see a bouncing progress bar before the desktop eventually comes up. However, now that I've actually installed Edgy, my boot-up screen is mostly blank. I see the Grub menu, then nothing (i.e. 80 seconds or so of a completely blank screen) before my login window eventually appears. Is this normal?

---

### Post by jd65pl on 2007-02-05
No you should see a progress bar, have you search and read other post regarding this problem. Do you have the drivers for your graphics card installed?

---

### Post by John E on 2007-02-05
> **jd65pl said:**
> No you should see a progress bar, have you search and read other post regarding this problem.
I've searched for 'blank' and 'screen' but the problems are mostly about booting up from a live CD and/or the screen going blank instead of displaying the login page. Those aren't the same problems that I'm having. I've even tried connecting a hi-res monitor instead of my usual LCD flat panel (in case it was due to invalid resolution or refresh rate) but that doesn't seem to be the problem. The resolution & refresh rate seem to be acceptable to my monitor but there's simply no picture.

> **jd65pl said:**
> Do you have the drivers for your graphics card installed?
Yes - that's the one thing I can definitely be sure about. I use a twin-monitor setup with a Matrox Millennium G400 graphics card. It's one of the most troublesome setups to configure but the driver is correct and both monitors work (apart from this problem).

---

### Post by dannyboy79 on 2007-02-05
the progress bar graphics and such may not be in your /boot/grub/menu.lst line that boots up your kernel. for example, I turned mine off by using the word quiet, which instead of seeing the progress bar I see a black screen which shows me all the inner workings of whats occuring while the kernel is loaded etc etc. here is my line from my menu.lst file ( i use dapper but I am sure edgy's menu.lst line wouldn't use different boot options as I am sure grub is very similar)

kernel          /vmlinuz-2.6.15-27-686 root=/dev/hdc2 ro quiet noapic

---

### Post by John E on 2007-02-06
Okay, I did a few experiments this morning. Here's my Ubuntu boot up entry (from menu.lst) as it was originally:-

```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot
```

If I take out the words 'quiet' and 'splash' I see a text-mode boot up process that's pretty much identical to booting up in recovery mode (except that I get a graphical login screen at the end).

If I only take out the word 'splash' I see the grub text output (about 8 lines) then nothing for about 20 seconds, then I see this error message:-

```
libgcc_s.so.1 must be installed for pthread_cancel to work
```

then I see nothing more for about 30 seconds, then about 1 x screenful of text flashes by, then I get my login screen.

Finally, if I only take out the word 'quiet' (leaving the word 'splash') I see the Grub output text, then about 2 x pages of text flash by (too fast to read) then nothing for about 60 seconds, then my login screen.

I assume that 'splash' is supposed to give me the Ubuntu logo but it isn't working.

---

### Post by dannyboy79 on 2007-02-06
ok, well it appears that what I thought was wrong isn't wrong and you entry in your menu.lst is correct. I am guessing that wherever the images that are stored which are retreived when starting up are missing so therefor it just shows a black screen. so try to gogle, fix splash screen, or something along those lines. otherwise I am not sure how to help sorry. have you looked at your dmesg after logging in to see if there is something in there which could inform you why this is happening?

---

### Post by vikingdocerrado on 2007-03-07
Hi there John E,

Did you find any way to see the boot-up-splash-bar (bootskin or whatever it is called)?
Did you manage to find out what is the culprit?

I am experiencing pretty much the same thing, I see the bar before installation of Edgy, but after that I only get a blank screen (with a blinking cursor at the upper left corner). The main difference is that this happens with my laptop screen...

---

