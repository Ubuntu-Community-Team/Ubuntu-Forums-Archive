---
title: "A Questiion"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by wallacethegreat on 2007-01-08
Hi All, 

As a newbie to Ubuntu (and any flavour of Linux to be honest, currently running 6.06 LTS which I installed from a Live CD at the weekend onto a 250 GB External USB 2 Hard Drive,  I find that after approximately 20 minutes the mouse freezes and nothing I do will get the mouse to start again. 
If I am using firefox to check email I can tab to continue reading email depending on the mail client I am using.

Is there something I am doing wrong or is there a setting I need to alter. 

The system is an AMD x64 3800+
Nvidia 7300gs grahics card with 128 MB dedicated and 128 MB shared
1GB DDR2 Ram.

This is driving me nuts ](*,)  as I am using this to try to give myself some linux experiance.

Many thanks in advance

Wallacethegreat

---

### Post by Odisej on 2007-01-08
Is your mouse on USB or PS/2 port? try to change and see what happens.

Odisej

---

### Post by xopher on 2007-01-08
Or, you could try switching to another driver, try evdev for instance. There's a lot of info about it on the forums, search and discover ;)

---

### Post by wallacethegreat on 2007-01-08
> **Odisej said:**
> Is your mouse on USB or PS/2 port? try to change and see what happens.

Odisej

It is a USB mouse. 

Does this make a huge difference as I thought that USB didn't require drivers.

---

### Post by Efwis on 2007-01-08
usb doesn't require drivers, but they do require power from your computer. sometimes if one usb item uses more power than another, it will shut down the other usb ports because there is no power to them.

I usually recommend if you are using an external HD to use a self powered usb hub. by doing that you have less power drain on the usb ports your computer has.

---

### Post by wallacethegreat on 2007-01-09
> **Efwis said:**
> usb doesn't require drivers, but they do require power from your computer. sometimes if one usb item uses more power than another, it will shut down the other usb ports because there is no power to them.

I usually recommend if you are using an external HD to use a self powered usb hub. by doing that you have less power drain on the usb ports your computer has.

My external HD is self powered therefore is only using the connection to transfer information. The only other active USB devices are the mouse and keyboard. 

I have no slot to use a ps/2 keyboard or an ordinary mouse..  what else can I do? :-k 

I have heard a suggestion that it may be to do with the fglrx drivers but I do not have these on this system.

All suggestions gratefully recieved.

WallaceTheGreat

---

### Post by smoker on 2007-01-09
have you tried it in other usb sockets, for example, if it is plugged in at the rear, try it on a socket at the front

---

### Post by Odisej on 2007-01-09
In one of the threads I read that updating BIOS  may help in some cases as well. Sorry for not being able to help more as it looks like the problem is hardware specific. 

What kind of mouse are u using? 

Maybe using Edgy will also solve a problem or two. Well, just a suggestion...

odisej

---

### Post by az on 2007-01-09
When that happens, can you restart X? (CTRL-ALT-Backspace)

Can you go into a Virtual Console  (CTRL-ALT-F1)?  If so, log in and try to restart X

sudo /etc/init.d/gdm restart

You can check the X logs in /var/log/Xorg.log to see if any events are listed.

---

