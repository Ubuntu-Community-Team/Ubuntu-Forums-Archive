---
title: "Help finding IP address, please"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-01-05
I'm in, what might very well be, the final stages of my 10 week long quest to get online with Dial-Up.    :-)

To answer the command of, "Enter the IP number for your primay nameserver",

A ) Would that be ME ?

B ) Since my search has failed to turn up an IP number, I would appreciate it if someone would advise me how to do that.

Thanks.

---

### Post by Lord Illidan on 2006-01-05
I think your ISP will help with that. I assume you are talking about your DNS. Ask your ISP for the IP address.

---

### Post by cstudent on 2006-01-05
Hi Lewis

If I remember right, you're bouncing back and forth from Windows to Ubuntu trying to get your dial-up modem to work. In Windows get online and and then click the Start button and then Run. In the run box type cmd and hit enter. You'll get a dos window. At the prompt type ipconfig -all. You'll get a bunch of info concerning your ip address and dns servers. Unless you're running a dns server yourself, which I'm pretty sure you're not, then the first ip listed under DNS Servers is the one you would use.

---

### Post by matthew on 2006-01-05
The IP nameserver is the server that you connect your computer to that takes the named web addresses (like [www.google.com](www.google.com)) and resolves them to numeric addresses that your browser can actually connect to. It is likely one that is operated by your internet service provider. You could call them and ask what the IP address is for their nameserver, or look in the documentation they have provided either in print or online if you are able to find it. If you have successfully connected with a browser using linux on your computer you can look in the /etc/resolv.conf file and see what is listed there. For example, here is mine. ```
search ph.cox.net
nameserver 68.2.16.30
nameserver 68.2.16.25
nameserver 68.6.16.30
```I am in Phoenix, Arizona using Cox as my ISP. They have three nameservers so if one is busy or down my resolv.conf just looks at the next one in the list. Sometimes all that is needed is a line like this```
nameserver xxx.xxx.xxx.xxx
```using the numeric address of a known nameserver, for speeds sake preferably the one used by your ISP or at least near to you.

Sorry this wasn't a specific solution and answer, but hopefully I've given you enough info to know where to look next and how to find what you need.

---

### Post by L Campbell on 2006-01-05
[QUOTE=cstudent]Hi Lewis

If I remember right, you're bouncing back and forth from Windows to Ubuntu trying to get your dial-up modem to work. In Windows get online and and then click the Start button and then Run. In the run box type cmd and hit enter. You'll get a dos window. At the prompt type ipconfig -all. You'll get a bunch of info concerning your ip address and dns servers. Unless you're running a dns server yourself, which I'm pretty sure you're not, then the first ip listed under DNS Servers is the one you would use.[/QUOTE]
>>>>>>>>>>

Hello again and thanks for all your help in the past.     :-)

There must be something wrong with my (98SE) computer.  When I enter 'cmd' it says it cannot find the file.

Out of curiousity, I then typed ' ipconfig -all '.  A DOS screen appeared but only for a NANOsecond so, although I saw it flash by, there was no chance of reading the text.

Kind regards.

---

### Post by L Campbell on 2006-01-05
[QUOTE=matthew]The IP nameserver is the server that you connect your computer to that takes the named web addresses (like [www.google.com](www.google.com)) and resolves them to numeric addresses that your browser can actually connect to. It is likely one that is operated by your internet service provider. You could call them and ask what the IP address is for their nameserver, or look in the documentation they have provided either in print or online if you are able to find it. If you have successfully connected with a browser using linux on your computer you can look in the /etc/resolv.conf file and see what is listed there.   SNIP
<<<<<<<<<<<<<

Thanks for your reply, I appreciate it.

I have NEVER been online with Ubuntu and hope this will change _soon_.   :-)

However, I do have a Mepis computer, so I tried your suggestion 
( /etc/resolv.conf ) but could not get a response other than 'permission denied'.  I then preceeded it with 'sudo' but go NO reaction.

Maybe Mepis uses slightly different commands?

Kind regards.

---

### Post by Lord Illidan on 2006-01-05
[quote=L Campbell]>>>>>>>>>>

Hello again and thanks for all your help in the past.     :-)

There must be something wrong with my (98SE) computer.  When I enter 'cmd' it says it cannot find the file.

Out of curiousity, I then typed ' ipconfig -all '.  A DOS screen appeared but only for a NANOsecond so, although I saw it flash by, there was no chance of reading the text.

Kind regards.[/quote]

Ok, type command instead of cmd. cmd is used on XP. Then enter ipconfig -all

---

### Post by Chipmunk on 2006-01-05
Another option with win98se is to click start, go to 'run' and type winipcfg and click ok.

Then click the dropdown box to select your dialup connection, it will display all the relevent information including your Nameserver addresses.:D

---

### Post by L Campbell on 2006-01-05
[QUOTE=Lord Illidan]Ok, type command instead of cmd. cmd is used on XP. Then enter ipconfig -all[/QUOTE]


Great.  Thank you, this works well.

Kind regards.

---

### Post by L Campbell on 2006-01-05
[QUOTE=Chipmunk]Another option with win98se is to click start, go to 'run' and type winipcfg and click ok.

Then click the dropdown box to select your dialup connection, it will display all the relevent information including your Nameserver addresses.:D[/QUOTE]
..................................


This worked well, too.  

Many thanks.

---

### Post by FLeiXiuS on 2006-01-05
Don't forget about DOS' trusty command prompt!

```

ipconfig /all

```

That'll print just about everything you'll need!

---

