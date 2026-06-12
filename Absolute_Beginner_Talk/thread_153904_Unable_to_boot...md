---
title: "Unable to boot.."
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by Slasher9641 on 2006-04-02
I finished the Ubuntu set up but it will not boot and I'm getting this message:

*Id "1" respawning too fast: disabled for 5 minutes

Can anyone help me out this is my first time using Ubuntu.

---

### Post by trent dillman on 2006-04-02
Can you post some specs on your system?

---

### Post by Slasher9641 on 2006-04-02
If that can help I'm using one of my 30 boxs this one is pretty low spec but I would expect it to do the job.

Pentium 3 450mhz with 64mb of RAM
1 x 1.6GB Western digital hard drive master
1 x 2.1GB seagate hard drive in slave

Thats all I can tell you at the moment as it's still hooked up.

I fixed that probelm with a hard drive format and fresh install.

Now I get this admin@ubuntu:-$

The admin is the account I created for the PC and ubuntu I created as the host. What do I do?

---

### Post by JoshHendo on 2006-04-02
You do have less than the min reccomended ammount of ram. Though I don't think this would be the problem.

1. What HDD is it installed on and,
2. Do you get this error before, during or after GRUB?

Thanks :)

---

### Post by Slasher9641 on 2006-04-02
I get the later after I have installed grub. It ques me for user login and password I type those in and I get admin@ubuntu: -$

NB: there is no visual interface yet. It's just a basic command prompt.

---

### Post by steve.horsley on 2006-04-02
The X-windows is not starting. Try entering the command **startx** and let us know the result.

---

### Post by Slasher9641 on 2006-04-02
[QUOTE=steve.horsley]The X-windows is not starting. Try entering the command **startx** and let us know the result.[/QUOTE]

That didn't work it couldn't find the file.

---

### Post by Mustard on 2006-04-02
The problem is related to the Breezy Badger installer not being able to install on systems with low ram.  This is a documented bug, and is fixed in the Dapper Drake installer.  Dapper Drake is a development release and is due for stable release in July I think.

If you have some experience with linux, you may be able to work around it.  If you don't then its probably an insurmountable hurdle at this stage.  The only other solution is to get more RAM, or wait for the Dapper Drake release.

I can't recall the actual bug number at the moment, but if you look on Launchpad.net, you should be able to find it somewhere.

---

### Post by Slasher9641 on 2006-04-02
I've just put 256mb of RAM into the machine I hope that works.

---

### Post by Mustard on 2006-04-02
[QUOTE=Slasher9641]I've just put 256mb of RAM into the machine I hope that works.[/QUOTE]

I'm hopeful myself, or I'll have to eat my words...hehehe. :)

---

### Post by Mustard on 2006-04-02
Looking around launchpad I found this actually...

[https://launchpad.net/distros/ubuntu/+bug/19382](https://launchpad.net/distros/ubuntu/+bug/19382)

and this..

[https://launchpad.net/distros/ubuntu/+bug/18431](https://launchpad.net/distros/ubuntu/+bug/18431)

I'm still looking for the first bug I suspected was the cause.  Normally the first bug says 'killed killed killed' repeatedly.  So I may be off the mark in that case.

There is a long list of unresolved threads on this problem..

[http://ubuntuforums.org/showthread.php?t=103171](http://ubuntuforums.org/showthread.php?t=103171)
[http://ubuntuforums.org/showthread.php?t=100758](http://ubuntuforums.org/showthread.php?t=100758)
[http://ubuntuforums.org/showthread.php?t=18785](http://ubuntuforums.org/showthread.php?t=18785)
[http://ubuntuforums.org/showthread.php?t=110712](http://ubuntuforums.org/showthread.php?t=110712)
[http://ubuntuforums.org/showthread.php?t=143065](http://ubuntuforums.org/showthread.php?t=143065)

The only thing close to an answer I saw in any of them was to power down and start from a cold boot. 0_0  Not much to work with.

Investigating further, a couple of these people continued to post on the forum, after installing ubuntu.  I have no idea how they overcame the problem, I can only assume they kept on trying.

This thread was particularly interesting in that someone accidently created the problem then persisted with the issue and attempted to investigate...

[http://ubuntuforums.org/showthread.php?t=90101](http://ubuntuforums.org/showthread.php?t=90101)

Then end result was that the hard drive died, which could be an indication of where the issue springs from.

This next guy here seems to have had Ubuntu installed and then tried a clean install and encountered the error, he seems to have noticed some type of hard drive error too...

[http://ubuntuforums.org/showthread.php?t=110712](http://ubuntuforums.org/showthread.php?t=110712)

Just a few more links I have found, this one explains how the process starts, but I wouldn't have a clue how to fix it from his description..

[http://www.oreillynet.com/pub/faqs/linux_faq_AEN3482](http://www.oreillynet.com/pub/faqs/linux_faq_AEN3482)

More technical jargon on the problem...

[http://linuxgazette.net/issue46/tag/5.html](http://linuxgazette.net/issue46/tag/5.html)   (seems to point to this being a gnome problem)
[http://linux.derkeiler.com/Mailing-Lists/RedHat/2003-11/2035.html](http://linux.derkeiler.com/Mailing-Lists/RedHat/2003-11/2035.html)
[http://www.linuxhq.com/lnxlists/linux-ppp/lp_9906_01/msg00009.html](http://www.linuxhq.com/lnxlists/linux-ppp/lp_9906_01/msg00009.html)

Ok, thats all the detective work I can do for now.  I'm hopeful that your installation went well and you got past the problem.

---

