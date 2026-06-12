---
title: "Username and password"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Ogrish on 2007-08-27
I installed Ubuntu using Wubi.  It installed perfectly and dual-boot works perfect.  I was able to log on once.  Today I tried to log on and the message says username and password are incorrect.  I'm 99% sure I 'm using the correct name and password.  Please tell me there is a way to retrieve this info.  I've read about bootnig in recovery mode.  If that's what I need to do, how do I do that?  Thank you for any assistance.

---

### Post by Inxsible on 2007-08-27
> **Ogrish said:**
> I installed Ubuntu using Wubi.  It installed perfectly and dual-boot works perfect.  I was able to log on once.  Today I tried to log on and the message says username and password are incorrect.  I'm 99% sure I 'm using the correct name and password.  Please tell me there is a way to retrieve this info.  I've read about bootnig in recovery mode.  If that's what I need to do, how do I do that?  Thank you for any assistance.

There is unfortunately no way to recover the password, but you can reset it.
Go into the recovery mode(usually the second option) and type in
```
passwd <username>
``` username is the username that you want to change the password for. Then enter the new password that you would like. Then simply ```
reboot
``` and select the normal method and use your new password.

---

### Post by Ogrish on 2007-08-27
Thank you.  How do I get into recovery mode?  When I boot up, I have no options. It goes to the login screen.

---

### Post by Inxsible on 2007-08-27
> **Ogrish said:**
> Thank you.  How do I get into recovery mode?  When I boot up, I have no options. It goes to the login screen.
So you don't have a dual boot ?

When you start up your machine, you can hit some key and get into the grub menu. But I can't seem to remember what key it is. Can someone please tell us what it is ??

I am not on my Ubuntu machine and am stuck on XP while I am at my friend's place :(

---

### Post by Ogrish on 2007-08-27
I used Wubi-7.04.04 to auto install Ubuntu.  When I start the computer I get the choice of Windows XP or Ubuntu.  I select Ubuntu and hit enter.  Ubuntu then boots the the login screen.  Is there a key I should hit somewhere during the boot process?  Again thank you for your assistance.

---

### Post by Inxsible on 2007-08-27
> **Ogrish said:**
> I used Wubi-7.04.04 to auto install Ubuntu.  When I start the computer I get the choice of Windows XP or Ubuntu.  I select Ubuntu and hit enter.  Ubuntu then boots the the login screen.  Is there a key I should hit somewhere during the boot process?  Again thank you for your assistance.Apart from Windows and Ubuntu, do you have a third choice for Ubuntu in recovery mode? Thats the one you wanna go into

---

### Post by meierfra on 2007-08-27
select ubuntu and hit enter as usual.

Then hit Esc (hit it a few times to make sure you don't miss the correct time)

Then the grub menu appears and you can choose recovery mode.

---

### Post by Ogrish on 2007-08-27
There are no other options.  While Ubuntu is booting there is scrip going up the screen, but no options.

---

### Post by meierfra on 2007-08-27
> There are no other options. While Ubuntu is booting there is scrip going up the screen, but no options.

That is normal. Since this is the "windows boot menu" used by wubi, and not the "grub menu"

---

### Post by Ogrish on 2007-08-27
I'm up and runnig perfect.  Thanks again for all your help.  :)

---

