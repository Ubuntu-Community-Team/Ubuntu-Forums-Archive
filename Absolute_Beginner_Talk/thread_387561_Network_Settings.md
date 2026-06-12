---
title: "Network Settings"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by X86 on 2007-03-18
in networking if you click on System>Admin>Networking >Network Settings> Hosts    their all gone ? I dont know how this happend.. I did let my 8 yr old nefu play some games on here but Iam not blameing an 8  yr old lol

How do I add them back or is this a real problem?

---

### Post by kambei on 2007-03-18
> **X86 said:**
> in networking if you click on System>Admin>Networking >Network Settings> Hosts    their all gone ? I dont know how this happend.. I did let my 8 yr old nefu play some games on here but Iam not blameing an 8  yr old lol

How do I add them back or is this a real problem?

In the Hosts panel, click the 'Add' button and enter - at the very least - your localhost setting:

127.0.0.1      localhost

---

### Post by oilchangeguy on 2007-03-18
try this screen shot

---

### Post by X86 on 2007-03-18
127.0.0.1 localhost I added that but is this a security risk I seen that screen shot but every network is different so I just want to get it back like it was but I dont want to seem like a dum azz  I been on Ubuntu for a few months .

---

### Post by kambei on 2007-03-18
> **X86 said:**
> 127.0.0.1 localhost I added that but is this a security risk I seen that screen shot but every network is different so I just want to get it back like it was but I dont want to seem like a dum azz  I been on Ubuntu for a few months .

No worries... localhost is not a security risk... and - as a free bonus - it keeps 'The World's Worst Computer Hacker' occupied! :-)

"An urban legend involving 127.0.0.1 is often circulated among the more technical computer related forums on the web. The story often involves an antagonist often referred to as “The World’s Worst Computer Hacker”. The story generally involves the Hacker hacking himself when tricked into using 127.0.0.1 as the IP address to hack into."

[http://en.wikipedia.org/wiki/Localhost](http://en.wikipedia.org/wiki/Localhost)

---

### Post by X86 on 2007-03-18
kambei 
thank you I have 2 more question's because I just installed Xfce4 and Iam getting this error message when I login... 
***********************************************************
Could not look up internet address for x86.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
x86 to the file /etc/hosts on your system.
***********************************************************
2)
Also I dont have KDE installed but I love Konquor browser 
and I realy like it because of the spell check in it is way better then firefox... The spell check in Konquorer isent working when I type to post........ and its config to auto spell check is thier some other plugin

---

### Post by kambei on 2007-03-18
> **X86 said:**
> kambei 
thank you I have 2 more question's because I just installed Xfce4 and Iam getting this error message when I login... 
***********************************************************
Could not look up internet address for x86.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
x86 to the file /etc/hosts on your system.
***********************************************************
2)
Also I dont have KDE installed but I love Konquor browser 
and I realy like it because of the spell check in it is way better then firefox... The spell check in Konquorer isent working when I type to post........ and its config to auto spell check is thier some other plugin

For /etc/hosts... try adding a entry for your computer's hostname and see if that resolves your problem... on my system I have these entries:

127.0.0.1       localhost
127.0.1.1       <add your hostname>

... I have a few other entires for machines on my LAN, but they are just a convenience and are not required.

As for Konqueror, I don't have it installed...

---

### Post by X86 on 2007-03-18
kambei 

error fixed in Xfce4 thank you

---

