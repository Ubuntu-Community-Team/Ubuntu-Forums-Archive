---
title: "I'm locked out of Ubuntu, what do I do?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-06-17
I tried to use Ubuntu a little while ago, and I got a "login failed" message when I typed in the password.  I typed the password in exactly as I wrote it on an index card when I installed Ubuntu, but it doesn't work after multiple tries.  The last time I used Ubuntu, I did not change my password or any other setting.  What do I need to to to use Ubuntu again?

It's kind of funny that I've been using Ubuntu on and off since about December of last year, and I'm still at the "absolute beginner" stage.

---

### Post by brooksbp on 2007-06-17
caps lock? try different caps variations of your password

---

### Post by diatribe on 2007-06-17
you've been using ubuntu on and off for a year but you still write your password on an index card? and yes, if there are and capitalizations you need to make sure that you use them, the password is case-sensitive

---

### Post by Feba on 2007-06-17
Starting from "D'oh!" and working our way up: Have you tried checking capslock?

---

### Post by lamalex on 2007-06-17
don't you love worthless replies that don't help you at all?

do this, go in as root in single user mode, at the grub loading screen chose recovery mode (you may need to hit esc at grub stage 1.5). once it's loaded, just type
```
passwd <your username>
```
and reset your password.

---

### Post by HotShotDJ on 2007-06-17
Keep in mind, password is case sensitive.  Make sure your CapsLock key isn't on and that you are typing it EXACTLY like you did when you set the account up.

If you still have trouble, boot into recovery mode (reboot, when grub message comes up, press Esc key and a menu will come up.  You'll see a menu entry for recovery mode.  Choose it and press enter).  After your systems boots, you will be at a command line.  Type "passwd user" (without quotes and replace "user" with the actual name of the account).  You will be prompted for a new password.  Now reboot (type reboot in the console) normally and you should be good to go.

---

### Post by diatribe on 2007-06-18
> **Iamalex said:**
> don't you love worthless replies that don't help you at all?

do this, go in as root in single user mode, at the grub loading screen chose recovery mode (you may need to hit esc at grub stage 1.5). once it's loaded, just type
```
passwd <your username>
```
and reset your password.

I believe you still have to enter a password to get to the root prompt

---

### Post by HotShotDJ on 2007-06-18
> **diatribe said:**
> I believe you still have to enter a password to get to the root promptNope.  No password needed in recovery mode.

---

### Post by lamalex on 2007-06-18
unless he set a root password, which he probably didn't. it's a big security hole, the fix, fill your usb/ps2 ports with glue.

---

### Post by diatribe on 2007-06-18
> **Iamalex said:**
> unless he set a root password, which he probably didn't. it's a big security hole, the fix, fill your usb/ps2 ports with glue.

oh that must be why mine does, thought I was crazy for a moment

---

### Post by Feba on 2007-06-18
>  don't you love worthless replies that don't help you at all?You're right, I know *I'd *hate to get an answer I could at least try out instead of having to wait who knows how long for any sort of response at all.

How DARE people try to help me solve my problem!

---

