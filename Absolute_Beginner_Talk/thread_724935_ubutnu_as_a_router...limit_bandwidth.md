---
title: "ubutnu as a router...limit bandwidth?"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-03-15
I have Ubuntu set up as a router. I  did this by SpaceTeddy's great how-to at: [http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874) . Everything works fine, I have my internet coming into my desktop on eth0 and then my notebook connected to eth1 on the desktop. My notebook gets a good internet connection and everything. The problem I am having is that if I download something with the note book it pulls all the bandwidth from the desktop and it can barely load a web page. I would like to figure out how to tell the system that the desktop is most important and the notebook can have the left-over bandwidth...can I do this?

thanks for your time! :)

---

### Post by dstew on 2008-03-15
My first guess is that you need to set some of the TCP/IP rules in your /etc/sysctl.conf file. See [this thread]("http://bbs.archlinux.org/viewtopic.php?id=31385"). What rules to set I don't know, but I think this is the right place to start.

EDIT: [Here ]("http://ubuntuforums.org/archive/index.php/t-351795.html")is another.

---

### Post by rockinlinux on 2008-03-15
Yeah, i know next to nothing about all of this stuff. I think you are right about the rules but i guess i too dont know waht ones i need...

I looked at the links, quiet interesting but im not sure they are what i need...maybe though

---

### Post by Cyanic420 on 2008-03-15
None of those settings are going to help you as those just manipulate the Linux tcp/ip stack which AFAIK does not contain any QoS features. You can set up routing/internet sharing and play with TCP window scaling, but QoS on Linux may require a third party app. or even replacing the stack with another.

---

