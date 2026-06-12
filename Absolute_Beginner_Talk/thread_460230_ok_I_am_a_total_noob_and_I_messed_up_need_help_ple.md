---
title: "ok I am a total noob and I messed up need help please"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2007-05-31
ok I installed ubuntu fiesty ( on my second drive) got it up and running no problem am having problems with installing ET but thats beside the point being a total noob with anything but windows and some dos I followed this guide ( copied and paste) for my x800 ati cardhttp://ubuntuforums.org/showthread.php?t=414194 but after reboot I cannot I recieve and error on my monitor saying that 33mhz is out of rang or something like that I had to reboot onto my other drive that is windows in order to post this problem like I said earlier in this post I am very very new at this but am willing to learn just need help .

---

### Post by kernel tom on 2007-05-31
can you get onto your ubuntu account without using the graphical login?

you should be able to just use the shell, which would look like dos prompts to you, to log in
then do this

sudo dpkg-recongigure xserver-xorg

then follow the prompts and answer the questions about ur devices, one section will ask you for ur  monitor's refresh rate, and i can attempt "auto detection" for you

---

### Post by GabrielDunn on 2007-05-31
Damn Tom you're fast.  

I was about to suggest the same thing.  I have to go command line to configure my xorg as well.  Consider it a learning experience.

---

### Post by Outrunner on 2007-05-31
At bootup, a Grub menu should appear(if not, you'll get a prompt to press ESC for a few seconds to see the menu). Now there should be an option that says (Recovery Mode) or similar. Select it and boot it up. It should drop you off at a command prompt. Login and then type

```
sudo dpkg-reconfigure xserver-xorg
```

and answer the questions. If you're not sure, you can leave the default answers.

EDIT: Wow, am I that slow all of a sudden?

---

### Post by kernel tom on 2007-05-31
> **Outrunner said:**
> At bootup, a Grub menu should appear(if not, you'll get a prompt to press ESC for a few seconds to see the menu). Now there should be an option that says (Recovery Mode) or similar. Select it and boot it up. It should drop you off at a command prompt. Login and then type

```
sudo dpkg reconfigure xserver-xorg
```

and answer the questions. If you're not sure, you can leave the default answers.

EDIT: Wow, am I that slow all of a sudden?

haha, i answered it quickly but spelt reconfigure incorrectly

also on a sidenote

if you miss tehe whole grub menu thing, you may still be able to use this when ur montior is flashing an error...

Ctrl+Alt+F1

then log into that and run that command previously mentioned

---

### Post by Shadowmeph on 2007-05-31
lol in my opinion you all are very fast I rebooted my comp again to try and then had to hard shutdown and reboot into windows came back here "not" expecting any reply s yet but have 3 reply s thank all of you for your quick replys I am going to try this now be right back ( I hope ) lol

---

### Post by Outrunner on 2007-05-31
> **kernel tom said:**
> haha, i answered it quickly but spelt reconfigure incorrectly

also on a sidenote

if you miss tehe whole grub menu thing, you may still be able to use this when ur montior is flashing an error...

Ctrl+Alt+F1

then log into that and run that command previously mentioned

I just noticed, I spellt the command incorrectly too! There's supposed to be a - between dpkg and reconfigure. I guess I'm tired :)

---

### Post by kernel tom on 2007-05-31
haha, yea being at work doesnt help the focus either

so to clear it up

sudo dpkg-reconfigure xserver-xorg

thats the command

---

### Post by kadafi69 on 2007-05-31
edit

---

### Post by Shadowmeph on 2007-05-31
> **kernel tom said:**
> haha, yea being at work doesnt help the focus either

so to clear it up

sudo dpkg-reconfigure xserver-xorg

thats the command
lol yes I realised this after about ten attempts lol I fluked out and did it right the problem was something to do with my digital monitors refresh rate. I thank all of you for your quick reply and help :) now I am going to look for that how to install enemy territory post lol

---

