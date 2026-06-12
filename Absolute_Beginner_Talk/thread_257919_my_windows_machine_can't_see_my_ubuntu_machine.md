---
title: "my windows machine can't see my ubuntu machine"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by benner on 2006-09-15
i have them going through a router.  the kubuntu machine can see the windows machine through 'samba shares' but i don't know what i have to do to the windows machine so that i can access the kubuntu machine.  i have a printer connected to the kubuntu machine so it would be really handy...

---

### Post by kidders on 2006-09-15
Hi there,

This may be a dumb question, but have you installed samba on your Ubuntu box?

A smarter question: Can you access your Ubuntu box "directly" (ie what happens if you try to run "\\192.168.blah.blah\sharename" in windows?)

To answer your question, ordinarily you shouldn't need to do anything to the Windows box to make things cooperate for you ... assuming Ubuntu is well configured.

---

### Post by benner on 2006-09-15
samba is installed.  a friend was here the other day and pinged the kubuntu machine from the windows machine and there was no problem.  when i look at the network in the windows machine, the only machine that appears is itself (a notebook).  is the problem with my settings in the kubuntu machine or do i need to do something to the windows machine?  i know nothing about networking.  this is the first time i have tried to link 2 machines through a router.  i have 3 kubuntu machines going through a switch with a windows machine in my classroom (i'm a teacher) that i will try to sort out if i can do this at home first.  suggestions?  'for dummies' web page?

---

### Post by benner on 2006-09-15
ps. i have the windows machine as 192.168.1.4 and the other as 192.168.1.6

---

### Post by kidders on 2006-09-15
Hi again,

The first thing to note is that Windows can take a few minutes (up to 15, in fact) to wake up to changes on a network. Here's a list of things for you to try, in order:

[LIST=1]
[*]Pick a Ubuntu box and figure out its IP, hostname & the name of one share. **ifconfig** will tell you your IP address(es) and **cat /etc/samba/smb.conf |grep "^\["** will give you a list of share names. (Do not try to use entries called global, homes, printers or print$.)
[*]Ping it from a Windows box by IP and then by hostname.
[*]Try to access the samba share using the IP address and then by hostname. From Windows, this involves hitting START+R and typing, say, \\192.168.1.1\myshare (see what happens) and then trying, say, \\ubuntu\myshare (see what happens).
[/LIST]

Knowing where you fail will help sort out your next step.

**Edit:**

So, ping 192.168.1.6 from your windows box first. Then try it using your Ubuntu box's hostname instead. Then move on to "running" \\192.168.1.6\sharename, and so on.

It's entirely possible, you see, that your Ubuntu box is there, but just not being "advertised" correctly. Also, could you post the contents of /etc/samba/smb.conf?

---

