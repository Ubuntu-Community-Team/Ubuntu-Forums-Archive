---
title: "Unable to start Ubuntu"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by r_bjarte on 2007-09-10
I used the alternate cd (amd 64) to  install Ubuntu 7.04, along side vista.
As far as I know the installation went without any problems.
But I'm not able to start Ubuntu. 
I just get this error message: Failed to allocate mem recourse: 6 # and (some numbers)
I also unable to start Ubuntu in recovery mode.

---

### Post by univremonster on 2007-09-10
Possibly this was just a bad install?  You could always try it again.  Do you get the option to boot Ubuntu when you first power up?

---

### Post by r_bjarte on 2007-09-10
Yes I did get option to boot Ubuntu.
However I first tried to run the live cd, but I was only able to run i in safe mode. So I got the alternate cd and ran it instead
Now I tried to run the install again, but now I don't get to choose if I want to boot in Vista or Ubuntu. The computer goes directly to Ubuntu and Ubuntu doesn't work. 
:confused:

---

### Post by CaptainInsaneO on 2007-09-10
I'm not totally sure about this, but I think if you press the esc key when your grub menu is SUPPOSED to show up, it will display it.

---

### Post by r_bjarte on 2007-09-10
I'm afraid that I don't understand anything of the command line interface because I'm  totally new to everything that's not windows. I decided to try Ubuntu out of curiosity.
What that comes up is something about a kernel or something. But it doesn't make any sense to me.

---

### Post by CaptainInsaneO on 2007-09-10
That's probably GRUB. When you see the kernel that you want to boot, press the right arrow key (looks like this: -->) and it should boot your Linux. If you don't see anything about Windows there's a possibilty that you overwrote Vista when you tried to install Ubuntu again.

There's a bug report for this error here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294)

Do me a favor and post the output of lpsci and maybe we can help you from there.

---

### Post by CaptainInsaneO on 2007-09-10
> **r_bjarte said:**
> 
I just get this error message: Failed to allocate mem recourse: 6 # and (some numbers)


Please post those "numbers" too, those are important and go hand in hand with the output of lpsci.

Sorry for double post.

---

### Post by r_bjarte on 2007-09-10
I moved my reply down at the end where it belong

---

### Post by CaptainInsaneO on 2007-09-10
If you're able to get a terminal (Ctrl+Alt+F1) you should be able to find the log in /var/log/syslog.

---

### Post by r_bjarte on 2007-09-10
I not quite sure but it looks a lot like this one
[ 0.206515] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
In the bug report there were one guy that posted the same error on a hp dv 6000.
My computer is a dv 6560 or something like that.
By the way; thanks for your help so far:)

---

### Post by CaptainInsaneO on 2007-09-10
I'm seeing a huge number of hp's have this problem. I'm beginning to think it might be cause by the combination of certain hardware they use. This is obviously a hardware problem, there might not be a fix for it. I'll keep looking around, and for the meantime keep an eye on that bug report I gave you. Patience is key, the guy working on that bug has 211 other bugs to work on as well.

Always glad to help, I love these forums and this OS. :guitar:

---

### Post by r_bjarte on 2007-09-10
I'll try to reinstall ubuntu, and see if I'll be able to boot Vista again. 
If it't dosen work I'll reinstall Vista and try Ubuntu again some other time. 
I'll need my computer up and running for my marketing analysis project :)

---

### Post by CaptainInsaneO on 2007-09-10
I like that you haven't dropped the idea of using Linux at the first sign of trouble.

MaximumPC had a good article a little while back on Ubuntu and installing it, you can try going to maximumpc.com and clicking the PDFs link and searching for it there if you need some help in getting started. Good luck!

---

### Post by r_bjarte on 2007-09-10
Everything that you can get for free is appealing to anyone who's ever taken a class i economy :lolflag:

Any way, It looks like reinstalling Ubuntu gives me the opportunity to boot Vista. 
So Ubuntu is still on my computer, but still not working :)

---

