---
title: "Hello all, I'm a newbie to Linux! I have ?'s!"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by akplynn on 2005-11-22
My name is actually Priscilla & I live in Alaska, USA. :) 

I'm an old gal, compared to most of the folks here, but started teaching myself how to use a computer in the very early 90's or before.... not sure of just when, but it was on a used Mac Plus. Learned on that & newer Mac's for awhile, before picking up a 386DX2 Windows 3.1 machine. With it, I learned a lot about that system & even began to learn how to replace parts - then to build systems. 

OK, .... I am soooo fed up with WINDOWS !!!! I usually have several machines for myself, 1 for hubby & then I also rework older machines to give to people who want to learn about computers, but don't have the money to do so. 

I can't spend my money on new software for everyone I help, so decided to check out Linux. I've downloaded both the Live CD & the installation iso's to this XP machine & after quite a search, found a link to a program that helped my CDRW open & write it to CD's. (It took awhile to find the program needed in the forums & should be a "sticky".) 

I put the Ubuntu LiveCD in the machine & rebooted. IT WORKED !!! IT RECOGNIZED EVERYTHING & EVEN GOT ME ONLINE! YEAHHH! :D  

My ?'s are: 
Does the installation CD contain all the same info & drivers as the LiveCD? 
What 56K modems are preferred for Ubuntu 5.1 ? (This machine will be for my 85 yr old father because he won't do updates on windows & gets trojans & viruses toooooooo often! He only plays games & does email online.) 
Should I expect any surprises or problems? Are there any downloads that I should do ahead of time? 

Any & all help/advice will be greatly appreciated! :) 

akplynn

---

### Post by erikpiper on 2005-11-22
1. Yes, I find it to work better even :) . (And text based install is actually VERY easy)
2. I use DSL so I dunno.....
3. Proprietary codecs.. See the wiki [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)

And with synaptic, downloading, installing, configuring, and updating are done with a few clicks. The wiki sometimes uses the command line because it is faster. (You will understand eventually...)


And WELCOME!

---

### Post by aysiu on 2005-11-22
[QUOTE=akplynn]
Does the installation CD contain all the same info & drivers as the LiveCD?[/QUOTE] Yes.

---

### Post by Dragineez on 2005-11-22
You've already done one very good thing. Joined this forum and asked for help. Another good one is [http://www.linuxquestions.org](http://www.linuxquestions.org)

If you're building a machine for an 85 year old user, stick with one of the major distros (like ubuntu) that have some of the accessibility options. Some cool little tricks, like the one that allows one handed operation of keyboard shortcuts (try doing ctrl-y with arthritis). My mother likes the magnifying glass thingy. Just get it up-to-date before you send it on its way. I don't suspect he'll be installing new hardware and having to re-compile the kernel too often.;)

---

### Post by akplynn on 2005-11-22
Thank you erikpiper, aysiu & Dragineez for your quick replies & links! 

It looks like I have a lot of reading & learning to do! :) 

I guess I'll be sort of returning to the really old days of DOS ... from the looks of it. Gee, I've forgotten most of that .... lol  

My dad only plays games on yahoo, so hopefully, they won't need too much tweaking to get 'em to work. I already found out Ubuntu can open email there & on hotmail, so that's a +. 

He does do some surfing on the web, so will probably need media & sound players ... which the wiki link will help with. :) 

I'll also have to decide which printer to put on here, as he does print out stuff at times.  Is HP, Canon or Epson the preferred choice? 

Many thanks, 
akplynn

---

### Post by matthew on 2005-11-22
[quote=akplynn]I'll also have to decide which printer to put on here, as he does print out stuff at times. Is HP, Canon or Epson the preferred choice?[/quote]
My experience has been that HP has excellent support, i.e. with drivers and ease of setup. I haven't used any of the others you mentions so I'll let someone else comment.

---

### Post by Dragineez on 2005-11-23
[QUOTE=akplynn]I guess I'll be sort of returning to the really old days of DOS ... from the looks of it. Gee, I've forgotten most of that .... lol [/QUOTE]Ah, DOS wasn't that bad. But wait until you start to get a hang of what's possible in the Linux CLI (Command Line Interface).... much more power.
[QUOTE=akplynn]My dad only plays games on yahoo, so hopefully, they won't need too much tweaking to get 'em to work. I already found out Ubuntu can open email there & on hotmail, so that's a +. [/QUOTE]Danger Will Robinson! Aren't the Yahoo games ActiveX? If so, they ***WON'T*** run.
[QUOTE=akplynn]I'll also have to decide which printer to put on here, as he does print out stuff at times.  Is HP, Canon or Epson the preferred choice? [/QUOTE]I cast my vote for Epson.

---

### Post by akplynn on 2005-11-23
[QUOTE=Dragineez]Ah, DOS wasn't that bad. But wait until you start to get a hang of what's possible in the Linux CLI (Command Line Interface).... much more power.

DOS is still usefull, even with XP, so all I need to do is learn the new terms with Ubuntu.  :)

Danger Will Robinson! Aren't the Yahoo games ActiveX? If so, they ***WON'T*** run.
I cast my vote for Epson.[/QUOTE]

Hummmm .... I entered the games listing without problem with the LiveCD, so I sure hope the games work! He likes to play chess & cribbage with his grandson there. ....

If the games need ActiveX & Ubuntu doesn't support it, then I can't install Linux on his system. :(    

Can anyone here verify that the Yahoo games are not available with Ubuntu?

---

### Post by ubuntu27 on 2005-11-23
Hi akplynn. Yes, you can play Yahoo! Games with Linux. I've just played. 

Some games you will need to use Java, and M. Flash Player.

How to install Java: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java)

How to install Flash: [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)

---

### Post by matthewstory on 2005-11-23
The ActiveX for Yahoo Games is used to track the individual's high score and other information about a user loging onto games from the same web browser, so unfortunately if he wants to track his high score he won't be able to do that, he also won't be able to download the games to linux as the non-web-based versions are all only written for windows (they don't work on OSX either).  But neither of these are very big issues.  As far as the modem is concerned, if you have a modem installed in the computer and the live disc configures it properly than you'll have no problem with it in the fully installed version.

cheers,
matt

---

### Post by akplynn on 2005-11-24
[QUOTE=ubuntu27]Hi akplynn. Yes, you can play Yahoo! Games with Linux. I've just played. 

Some games you will need to use Java, and M. Flash Player.

How to install Java: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java)

How to install Flash: [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)[/QUOTE]


Thank You Ubuntu27 !  I'll try setting it up for him, then. Hopefully, it will all work out. ....  if I can keep focused & do it right. At the moment, I'm spending a lot of time with Mom at the Hospital, as she is 80 yrs old & just had a knee operation. She's in a lot of pain .... more so than any other of the operations she's ever had. Morphine is not doing very much for her. 

Again, thank you very much!!! 
akplynn

---

### Post by akplynn on 2005-11-24
[QUOTE=matthewstory]The ActiveX for Yahoo Games is used to track the individual's high score and other information about a user loging onto games from the same web browser, so unfortunately if he wants to track his high score he won't be able to do that, he also won't be able to download the games to linux as the non-web-based versions are all only written for windows (they don't work on OSX either).  But neither of these are very big issues.  As far as the modem is concerned, if you have a modem installed in the computer and the live disc configures it properly than you'll have no problem with it in the fully installed version.

cheers,
matt[/QUOTE]


Matthewstory: I've been using Firefox for some time now & there is a setting in it to allow one to keep cookies, so wouldn't that stay the same? Isn't it the cookies that keep track of the scoring? 

akplynn

---

### Post by Bartender on 2005-11-24
Hiya, akplyn - 
I asked about modems last week - here's the thread...

[http://www.ubuntuforums.org/showthread.php?t=89861](http://www.ubuntuforums.org/showthread.php?t=89861)

Sounds like modems can be a real bear if they're the stripped-down versions that are in most machines these days.  I'll probably go shopping for one of those USR Performance Pro's on eBay when I get around to it...

---

### Post by steve.horsley on 2005-11-24
My understanding is that Epson printers are generally the best supported. I have never had problems with an Epson.

---

