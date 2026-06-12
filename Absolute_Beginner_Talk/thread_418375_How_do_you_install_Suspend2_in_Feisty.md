---
title: "How do you install Suspend2 in Feisty?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by pketch on 2007-04-22
Can anyone please tell me how to go about installing Suspend2 in Feisty?

I've looked at suspend2's website but their howto was a little confusing.  I understand I will have to compile a new kernel, but have never done this.  Can someone please list the steps required to install Suspend2 or at least point me to some good docs out on the web?  I am using Feisty Fawn.

Thanks very much for any info!!

---

### Post by rennen01 on 2007-04-22
Here is how to compile a new Kernel:
[http://www.linuxplanet.com/linuxplanet/tutorials/202/1/](http://www.linuxplanet.com/linuxplanet/tutorials/202/1/)

Better read that twice before you attempt it.  Try it on a test machine if you have one.

---

### Post by reacocard on 2007-04-22
Here's a more thorough and ubuntu-oriented guide: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Just follow that guide, but when it gets to the part about patching, use the suspend2 patch instead.

---

### Post by ramjet_1953 on 2007-04-23
Might I suggest that you learn to crawl, before you walk?

Unless you are familiar with using the command line and how pedantic it is, you are really biting off more than you can chew.

I heartily endorse what renn01 said in that you do this on a test machine, or a seperate hard drive. 

Even though kernel compiling is fairly straight forward and if you do it right, doesn't harm your current install, for the unwary, any sort of command line stuff, working with sudo can hose your system easily.

I always do kernel compling on a seperate hard drive and install from my working system.

That way if you break it, you don't lose valuable data.

ps O'Reilly's book "Linux Kernel in a Nutshell" is worth a read. It can be downloaded as a pdf file for free.

Regards,
Roger 8-)

---

