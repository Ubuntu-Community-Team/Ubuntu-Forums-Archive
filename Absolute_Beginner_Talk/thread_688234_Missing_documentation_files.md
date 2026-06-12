---
title: "Missing documentation files?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ptoye on 2008-02-05
I'm completely new to Ubuntu (and Linux in general, though have a lot of experience in Solaris Unix).

Having a bit of a problem in the bootup sequence, so decided to look at the GRUB documentation. man grub works fine, and directs you to info grub. But info grub just prints the man page and no more. I've noted that INFOPATH is null - what should I set it to to get the grub page, or is the grub info page missing?

Also, I notice that there may be more information in documentaation/i386/boot.txt but I cannot find this file anywhere on the system. Again, any ideas where to find it?

When I've sorted this lot out there may be many other questions!

Peter

---

### Post by drs305 on 2008-02-05
I can't answer your question directly but here is a good source for finding information about GRUB:

[http://users.bigpond.net.au/hermanzone/p15.htm#Second_method_configfile_boot](http://users.bigpond.net.au/hermanzone/p15.htm#Second_method_configfile_boot)

---

### Post by ptoye on 2008-02-05
Thanks - I'd already found the site, but not that page (yet). And it's got a link back to a post here about booting up which may well solve my booting problem.

But I'm still a bit concerned that I haven't got all the advertised documentation. With luck someone else will be along to answer that one later, once all the Super Tuesday excitement's died down (as a Briton, I can't say it worries me greatly....).

---

### Post by hyper_ch on 2008-02-05
the default grub menu.lst is quite good documented itself.

---

### Post by ptoye on 2008-02-07
The problem I'm having is in viewing the splash screen after Grub has done its job. And whatever I set vga= to doesn't help. 

But I can live with "unsupported video mode" instead of a splash screen.

But my main question was not "how does Grub work?" but "where's the info page which, according to the man page, should be in all full Grub installations?".

I've also found from the main help system that a few of the links don't exist. As the machine's not connected to the Internet at the moment, would this be causing the problem?

I'm totally new to Linux, and am not sure just what I should have on the machine, what I am expected to download as an extra from the various sites, and what I have to search for. And the books I'm looking at don't help at all. And some of the error messages I get are almost as obscure as the Microsoft equivalent :(

---

### Post by drs305 on 2008-02-07
> **ptoye said:**
> I'm totally new to Linux, and am not sure just what I should have on the machine, what I am expected to download as an extra from the various sites, and what I have to search for. And the books I'm looking at don't help at all. And some of the error messages I get are almost as obscure as the Microsoft equivalent :(

We were all new at some point. As long as you have an Internet connection you can probably find the answers either by searching this site or with Google. (On google it would probably help to include 'linux' or 'ubuntu' if the search could also apply to windows/macs. 

As to what you should have, when you need or want something it will become apparent. It works fine out of the box and you can add apps as you become more familiar. If you are looking for an alternative to a windows program, this site might help:
[http://www.linuxalt.com/](http://www.linuxalt.com/)
You can then search this site for opinions on apps you are thinking of installing.

If you get an error message, copy it into the search engine of this site. Someone else has probably had the same error message and chances are good that you can find out more about what's causing the message and, hopefully, how to fix it.

Again, welcome to the world of ubuntu.

---

