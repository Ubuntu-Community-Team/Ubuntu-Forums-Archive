---
title: "pc doesn't shut down"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by erikw on 2008-01-11
d

---

### Post by chips24 on 2008-01-11
thats great... how can i help you if all you say is d?
maby you can give a little more information.:confused:

---

### Post by nikoPSK on 2008-01-11
try this:
 
```
 
sudo shutdown -h now

```

---

### Post by chips24 on 2008-01-11
sorry about my little hint of sarcasm, but i dont see any point of making a post if youre not gonna give detailed information, have you tried manually pressing the power button? it dosnt mess up the computer like it does with windows. there might be a hardware problem.

---

### Post by nikoPSK on 2008-01-11
> **chips24 said:**
> sorry about my little hint of sarcasm, but i dont see any point of making a post if youre not gonna give detailed information, have you tried manually pressing the power button? it dosnt mess up the computer like it does with windows. there might be a hardware problem.
 
It's fine, just don't go on about it. :KS

---

### Post by jd65pl on 2008-01-11
This is a double post probably why it just says 'd' [here]("http://ubuntuforums.org/showthread.php?t=664622") is the other.

```
sudo shutdown 00
```

I think you probably need to have a look at your logs

---

### Post by erikw on 2008-01-11
Sorry about the 1 message, but this is what I was trying to write;
I installed 7.10 on my Acer Extensa 5620 but when I close Ubuntu I got the following message on a black screen;
-networkmanager: <warn> nm_signal_hadler(): caught signal 15, shutting down normally
-networkmanager: <info> caught termination signal
-networkmanager: <debug> [1200057705.773186] nm_print_open_socks()pen socket list
-networkmanager: <debug> [1200057705.773282] nm_print_open_socks()pen sockets list done
-networkmanager: <info> deactivating device eth0
-networkmanager: <info> deactivating device eth1

After that I get a blinking cursor and I need to shut off power manually.

I allready tried this with the same result, doesn't help!!

Quote:
Originally Posted by atari130xe View Post
I got it! have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody.

---

### Post by erikw on 2008-01-11
I tried in a terminal this,

sudo shutdown -h now

But then I'am asked for my password, and when I type my keyboard doesn't react anymore.

---

### Post by DarkN00b on 2008-01-11
When typing your password you won't see anything happen even though your password is being entered. Just type your password and hit enter. It will work just fine.

---

### Post by nikoPSK on 2008-01-11
> **erikw said:**
> I tried in a terminal this,
 
sudo shutdown -h now
 
But then I'am asked for my password, and when I type my keyboard doesn't react anymore.
 
it's a protection feature.

---

