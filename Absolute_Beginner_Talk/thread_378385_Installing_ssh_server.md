---
title: "Installing ssh server"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by confused44 on 2007-03-07
Hi, 

I've very new and still confused.  I need to install a ssh server.  No idea HOW to do this.  Can someone please help???  Thanks,

Martha

---

### Post by confused44 on 2007-03-07
BTW, I'm using version 6.06 if that helps.  THanks.

---

### Post by Bachstelze on 2007-03-07
```
sudo apt-get install openssh-server
```

---

### Post by confused44 on 2007-03-07
Had tried that.  Did it again to be sure I entered everything correctly.  

This is what I got back:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openssh-server: Depends: openssh-client (= 1:4.2p1-7ubuntu3) but 1:4.2p1-7ubuntu3.1 is to be installed
E: Broken packages

---

### Post by dannyboy79 on 2007-03-07
do a sudo aptitude update first. then
do a sudo aptitude remove openssh-client && sudo aptitude purge openssh-client

then after that is done, if it gives you a broken message again, then use a -f after the word, "aptitude" with the same thing again. this will force it to remove the broken package. (ie: ........ aptitude -f ........)

after that is done, then try again with installing the openssh server

 sudo aptitude install openssh-server

Also, use aptitude always, apt-get doesn't resolve dependencies as good as aptitude! good luck

---

### Post by confused44 on 2007-03-07
Thanks to all!  :)   It worked!  Danny Boy thanks for the clues.  You got it fixed.  I really appreciate it.  Have a great day!

Martha

---

### Post by dannyboy79 on 2007-03-07
i am glad to have helped another user. i just wish I could get help from some1 knowledgable regarding compiling a custom kernel. 98% of my 1500 posts have been helping others, yet out of the 2% that I have posted requesting help, I hardly ever get any. I dislike that about the open-source community. You never get back the same amount you put in. Oh well. I'll just keep waiting and hope some1 will help me.

---

