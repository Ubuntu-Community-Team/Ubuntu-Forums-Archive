---
title: "[SOLVED] Cant start GDM"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by skyman747 on 2008-02-03
hello, I just installed ubuntu 7.10, and when I went to start it up, there was no desktop.  So I did all the installaion, but when I type

sudo /etc/init.d/gdm start

nothing happens, so I did whereis gdm, and this is what showed up

gdm: /usr/sbin/gdm /etc/gdm /usr/lib/gdm /usr/share/gdm /usr/share/man/man1/gdm.1.gz /usr/share/man/man8/gdm.8.gz

Can anyone tell me what to do now?

If it matters, I am running it on VirtualBox.  thank you for your help

And I no nothing about alot of this stuff, so please try and be as simple as possible with your responses.

---

### Post by skyman747 on 2008-02-03
comon, someone must know the answer

---

### Post by The Cog on 2008-02-03
Try the command **startx** and see what error messages that spits out. Probably need to post them here to see what people have to say about them.

As a thought, it may just be a shortage of memory.

---

### Post by skyman747 on 2008-02-03
Ok, I ran Startx, and this is what I got

xauth:  Creating new authroity file /home/skyler/.serverauth.3736
xauth:  creating new authority file /home/skyler/.Xauthority
xauth:  creating new authority file /home/skyler/.Xauthority

giving up.
xinit:  Connection refused (errno 111): unable to connect to X server
xinit:  No such process (errno 3): Server error.

I dont think that it would be a memory error, because I have virtualbox setup so that the space expands with the virtual computer.

---

### Post by Rocket2DMn on 2008-02-03
Try reconfiguring X, the following will ask you a bunch of questions about your computer hardware, do your best to answer, defaults work for most questions.  When asked about video driver, choose "ati" if your card is an ati, or choose "nv" if your card is an nvidia.  At the resolutions page use TAB to move around and SPACEBAR to select your monitor's max resolution and everything else.
```
sudo dpkg-reconfigure xserver-xorg
```
Then restart gdm
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by skyman747 on 2008-02-03
when I try running X, I get this error

xserver-xorg is broken or not fully installed.

Any solutions?

---

### Post by Rocket2DMn on 2008-02-03
If there is an active internet connection, try running
```
sudo apt-get install ubuntu-desktop
```
This will (re)install the GUI stuff.  If that fails, you may just want to try to reinstall.

---

### Post by skyman747 on 2008-02-03
Thanks, Took a while, but got it figured out.  Thanks.

---

