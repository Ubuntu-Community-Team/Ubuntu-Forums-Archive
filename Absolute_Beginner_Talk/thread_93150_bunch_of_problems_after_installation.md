---
title: "bunch of problems after installation"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by Wolf1994 on 2005-11-21
1. When Ubuntu rebooted during installation, appeared box with text replaced by squares. Possible because I choose Russian language. As I didn't knew what I was prompted of (there's was word "ubuntu") , I add letters to this word to "ubuntuforever". And now system at beginning of load offers me to create something like: "/etc/hosts/ubuntuforever" - in opposite case its talks that Gnome my cause problems.

2. Perhaps its follows from first point - I can't esttablish Internet connection. Hardware - fits because I had exit in Internet from LiveCD. Also Network card is detected. But when I try to Administer over Networks - system "thinking" for a few seconds and then happens nothing.
I tried use "sudo pppoeconf" but it doesn't working.

3. In first section, in Internet bookmark, last menu item has "Abracadabra" spelling (in LiveCD its was same).

PS. Addition to point 1. Just remembered: I reject Internet connection during installation as one was not detected automatically by DCHP (unlike in LiveCD case) and I left this problem for fully-installed system. So I have to ask: is it possible solution for omissions made during installation?

---

### Post by Wolf1994 on 2005-11-22
Will be very glad if experts answer at least some questions... Or if theme is incorrect and I asking too much - point on it and close the topic, then I ask these questions separately in different topics with related names...

---

### Post by Brunellus on 2005-11-22
cut and paste this command into a terminal, and post the output, so we can see what's going on:

```
ifconfig
```

---

### Post by Wolf1994 on 2005-11-22
This command ignored by "Terminal" - returned command line: wolf@ubuntuforever... Seems my situation is awesome. Problem is that I haven't access to Internet from Ubuntu (I type this under XP) and I have no access to Windows-disk and to diskette-drive. So I even may not be able to post output if I cannot write one by pen and paper.

May be I need to log in as root to gain access to administration?

---

### Post by Brunellus on 2005-11-22
I'm still not quite sure I understand what exactly the problem is.  Have you tried asking the people at [http://forum.ubuntu-ru.org/](http://forum.ubuntu-ru.org/) ?

---

### Post by Wolf1994 on 2005-11-22
Ok. Last suggestion/question.

When I typed in terminal: "sudo pppoeconf" in LiveCD, I was prompted to enter login/password of my provider.

When I typing this command now (under Ubuntu installed on hard-drive) I getting this: "unable to lookup ubuntuforever via gethostbyname()".

May be main problem is that I change word "ubuntu" on "ubuntuforever" during installation?

Sorry for my ignorance, I think you right and I have to ask on Russian forum. Thanks for link.

---

### Post by Wolf1994 on 2005-11-22
I asked my question at Russian forum. But that forum much rare visited and I think I have here better chances to resolve my problem faster. So I make one more attempt to ask.

The first problem is that **I can't go to Internet from my Ubuntu**. As this question will be resolved, further questions I will be able to resolve immediatly from Ubuntu (through FireFox) in easier way than now, from WindowsXP.

I tried command "ifconfig" in terminal window but got nothing, so I can't post my Ubuntu's configuration.

Please give me sequence of steps to do from "A" to "Z" and I'll give you description of system's reaction on each step.

---

### Post by Wolf1994 on 2005-11-24
At last question resolved. May be somebody will found this useful, so I type it.

First problem was in absence of my Ununtu name in /etc/hosts.
 Solution:
 - load Ubuntu from LiveCD
 - mount hard drives with Ubuntu (Administration/System/Disks)
 - Run as different user (root) - nautilus
 - locate and add in etc/hosts "ubuntuforever"

Second problem was - that I installed Ubuntu in expert mode and gave root password, so sudo command was unavailable for simple user.
 Solution:
 - load Ubuntu from LiveCD
 - mount hard drives with Ubuntu (Administration/System/Disks)
 - Run as different user (root) - nautilus
 - locate and  add in etc/sudoers "%wheel ALL=(ALL) ALL"
 - locate and  add in etc/group "wheel::10:root,user"

Ran "sudo pppoeconf" and configured my access to Internet. Now I posting this message under Ubuntu/FireFox!

---

