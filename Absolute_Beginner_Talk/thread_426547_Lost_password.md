---
title: "Lost password"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Wazzer on 2007-04-28
Hi Everyone.

I have just been given a box with xubuntu installed . Unfortunately the person who gave it to me as forgotton what the initial password is. Is there any way round this or will I have to reinstall from scratch?

Many thanks in advance

---

### Post by viciouslime on 2007-04-28
When you first boot the computer, press esc when grub is loading. It will say something like press esc to enter menu and count down from 3.

Then you can select... errrm I can't remember exactly what it is called, recovery mode I think.... but possibly single user mode, or superuser mode. Basically not the default option in the list, but the other one.

You will then be given a command line as root. Type in "passwd <your username>" Set your password. Type in reboot. Et voilà.

EDIT: I am fairly certain it is called recovery mode. Reply to this thread if you need any more help, I will try my best, I realise my description isn't the best, but I haven't got another machine I can go through the steps on myself at the mo, so I am having to do it from memory... sorry.

---

### Post by Wazzer on 2007-04-28
Thanks vicouslime I will try it in the morning and let you know if it works

---

### Post by Wazzer on 2007-04-29
That worked a treat

Many thanks

Wazzer

---

### Post by dabbner on 2007-05-03
I just used this on a box and it worked... wow... so much for Linux security...

---

### Post by mcduck on 2007-05-03
> **dabbner said:**
> I just used this on a box and it worked... wow... so much for Linux security...
if you get physical access to a computer, it's never secure. No matter what OS you use or what tools you use to secure it. Simply booting any live-CD will give you full access to almost any machine, and if there's no CD drive you can always just remove the hard disk and access it's contents on some other machine. BIOS passwords can be usually cleared in couple of seconds, and even in worst case removing CMOS battery & unplugging the power cord for 20 minutes will remove the password. Even encrypting your hard drive is not 100% safe, it just takes more time to open it.

So the recovery mode is really no deal. But if you feel better, you can always add a Grub password to restrict access to recovery mode.

In the end keeping your machine somewhere where no one else can get access to it is the only way to secure it.

---

