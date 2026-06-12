---
title: "Two computers, one email account"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by katiad on 2005-09-11
I have two computers: the first being an XP Pro install, the second being Ubuntu. Both computers are sharing monitor, keyboard, mouse. I'm interested in setting up a FAT32 partition on the windows computer and somehow making it so my POP email accessed through Thunderbird can be read from both Windows and Linux. Possible? I'm not entirely sure what networking/mount setup I'd need, and if this is even advisable. I haven't downloaded or configured samba - but the XP partitions on the XP computer can be read by Linux from the standard Ubuntu install. I'm not sure if a true install of samba is needed for this, or not, nor am I sure what else I'll need to do to make this work.

Thanks for any advice you can give me!

---

### Post by aysiu on 2005-09-11
If you're absolutely sure you want to do this, I think [this thread](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=349664) will help.

Your best and safest bet is to use IMAP instead of POP, though, in which case [this thread](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=356006) will help.

---

### Post by sneax on 2005-09-11
Think different - don't use a FAT partition to store your email, store it on your mail server! Use thunderbird and in settings you can enable: 'only delete emails from server when i do' or something like that. The situation you want to create is this: thunderbird checks the mail on the server, and displays what's on the server. It DOESNT take it away unless you did delete on the client.

This way wehter you check your email from xppro, ubuntu or whatever computer, your whole mail 'setup' will always be on the server. You'll have to config both installations but it's not too hard to do.

---

