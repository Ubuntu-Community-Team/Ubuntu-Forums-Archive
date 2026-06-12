---
title: "Ubuntu Server Newbie"
date: 2011-09-26
forum: Apple Hardware Users
---

### Post by drewash on 2011-09-26
Greetings, I'm starting my adventures in Linux and am open to any suggestions on projects, ideas, insights, and general knowledge as I start this adventure!

Thanks!

---

### Post by haqking on 2011-09-26
> **drewash said:**
> Greetings, I'm starting my adventures in Linux and am open to any suggestions on projects, ideas, insights, and general knowledge as I start this adventure!

Thanks!

Is this related to Apple as it is in the Apple sub-forum ?

or a general linux and linux server question ?

i will hold my post incase it is meant from an apple persepctive ;-)

---

### Post by drewash on 2011-09-26
> **haqking said:**
> Is this related to Apple as it is in the Apple sub-forum ?

or a general linux and linux server question ?

i will hold my post incase it is meant from an apple persepctive ;-)
Well... I'm installing it on some older Mac PPC hardware.... so therefore posted here.... guess I should have put it in the general section.

Open to anything at this point haqking!   lol

---

### Post by lisati on 2011-09-26
If it's server related as the thread title suggest, then the server section might be better. Is this what you want? If so, one of the mods can move this thread for you.

---

### Post by LinuxFan999 on 2011-09-26
Here is a link with a lot of information 
about Ubuntu server: 
[https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)
You can download Ubuntu server from here:
[http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download)

---

### Post by haqking on 2011-09-26
> **drewash said:**
> Well... I'm installing it on some older Mac PPC hardware.... so therefore posted here.... guess I should have put it in the general section.

Open to anything at this point haqking!   lol

OK well then i will keep it non hardware specific, i just wanted to make sure it didnt directly relate to a Apple issue.  So i have a pretty much standard answer to newbies.


Linux can be daunting due to unfamiliar terrritory but to become a confident user only comes only with experience and read, read, read and try, try try then there are at least some basics needed.

First of all i suggest getting to get grips with the security model early on (bit boring early on and often complicated but helps prevent future hiccups), as there is alot of misunderstanding about Viruses in Linux and malware in general etc so i refer you first to the importance of using sudo here at:

**Security**

rootsudo (**very important you read this one if you read nothing else**)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

here for security in general

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and these stickies (in my signature)

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

here for virus information

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

and this will give you a good grounding in the security of your system and such like.


**Command Line (terminal)**


[https://help.ubuntu.com/community/Be.../BashScripting](https://help.ubuntu.com/community/Be.../BashScripting)

[http://linuxcommand.org/](http://linuxcommand.org/)


**Server and Services**

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

That should get you going.

Have fun

Regards

haqking

---

### Post by drewash on 2011-09-26
> **lisati said:**
> If it's server related as the thread title suggest, then the server section might be better. Is this what you want? If so, one of the mods can move this thread for you.
Yes... moving it to the 10.04 LTS forum might provide more of the info I'm after at this point.   Thanks lisati

---

### Post by haqking on 2011-09-26
> **drewash said:**
> Yes... moving it to the 10.04 LTS forum might provide more of the info I'm after at this point.   Thanks lisati

Well you need to provide specific questions ?

I have posted a lot above about starting out which is where i thought you were at.

if it basically how to with 10.04 server then the links above on server should do it.

here it is again [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

hope this helps, or are you having a specific issue ?

cheers

---

### Post by searchfgold6789 on 2011-09-26
> **drewash said:**
> Greetings, I'm starting my adventures in Linux and am open to any suggestions on projects, ideas, insights, and general knowledge as I start this adventure!

Thanks!
In answer to your question, I'm a little confused as to the actual categorization of this thread, but here's a few things:

[LIST=1]
[*]Begin to learn [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") commands.
[*]Learn about eye candy, my favorite part of linux! Try this... open up a bunch of windows, then hold down the Alt key, then press Tab a few times. (should work on most newer computers). If eyecandy is activated already you should see a really cool animated windows switcher.
[*]Open up the software center and install awesome apps. Stellarium, billard-gl, xcowsay, and bubblemon are just a few of the fun and zany programs Ubuntu has to offer.
[/LIST]
Have a lot of fun,
 - search

---

### Post by haqking on 2011-09-26
> **searchfgold6789 said:**
> In answer to your question, I'm a little confused as to the actual categorization of this thread, but here's a few things:

[LIST=1]
[*]Begin to learn [terminal]("http://https://help.ubuntu.com/community/UsingTheTerminal") commands.
[*]Learn about eye candy, my favorite part of linux! Try this... open up a bunch of windows, then hold down the Alt key, then press Tab a few times. (should work on most newer computers). If eyecandy is activated already you should see a really cool animated windows switcher.
[*]Open up the software center and install awesome apps. Stellarium, billard-gl, xcowsay, and bubblemon are just a few of the fun and zany programs Ubuntu has to offer.
[/LIST]
Have a lot of fun,
 - search

Though as it relates to server 10.04 apart from learning terminal then you can forget the rest as there is no DE by default and best to stay that way ;-)

---

### Post by drewash on 2011-09-26
> **haqking said:**
> Well you need to provide specific questions ?

I have posted a lot above about starting out which is where i thought you were at.

if it basically how to with 10.04 server then the links above on server should do it.

here it is again [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

hope this helps, or are you having a specific issue ?

cheers
Thanks haqking.... your info is greatly appreciated!

---

### Post by haqking on 2011-09-26
> **drewash said:**
> Thanks haqking.... your info is greatly appreciated!

no worries, you are welcome.

remember that server has no DE by default though you can add it.  So best learn the CLI with the command line links above.

Happy reading

Enjoy

---

