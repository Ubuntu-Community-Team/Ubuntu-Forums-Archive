---
title: "[SOLVED] Absolute Beginner Admin Tutorial?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2007-10-17
Hey all,

Is there a tutorial or howto talking about the very basics of Ubuntu/Debian system admin? I have been using RedHat/Fedora for a long time but know only enough to keep my mythTV system running. I could really use some  basics such as:

Startup process; Where do I put scripts I want to run at startup?
    example, nvidia-settings, AWN etc.

How do I start and stop services from the command line? It's different than Fedora...
    (/sbin/service xxx start/stop/status/restart no worky in Ubuntu)

How do use the command line to set services to autostart?  It's also different...
    I ask these last two because I have a Ubuntu server install and I need to activate FTP to put my web pages on it. I don't know why it's not activated by default but hey...

What are the customary places for things? IE what goes in /bin vs. /usr/bin or /sbin etc. what about this xxx/local stuff? and /var's /shares? /sources?  I know there are customs but I have never known any of them nor ever seen them explained. I assume there is some standardization but I also know if differs by distribution. A real basic overview of the "standard" directory structure of the entire system would be very helpful. Especially since a very common response to a newbie question like how do I get blank running would be "you have to go to your blank installation folder and edit your conf file" Dunno where that is :)

What else should I know? I unfortunately don't know enough to ask any more intelligent questions but these are nagging questions having the answers to will help speed up and make more enjoyable the whole learning process.


Thanks!
Eric

---

### Post by funrider on 2007-10-17
is [https://help.ubuntu.com/](https://help.ubuntu.com/) what you are looking for?

---

### Post by overdrank on 2007-10-17
> **nowhere@cox.net said:**
> Hey all,

Is there a tutorial or howto talking about the very basics of Ubuntu/Debian system admin? I have been using RedHat/Fedora for a long time but know only enough to keep my mythTV system running. I could really use some  basics such as:

Startup process; Where do I put scripts I want to run at startup?
    example, nvidia-settings, AWN etc.

How do I start and stop services from the command line? It's different than Fedora...
    (/sbin/service xxx start/stop/status/restart no worky in Ubuntu)

How do use the command line to set services to autostart?  It's also different...
    I ask these last two because I have a Ubuntu server install and I need to activate FTP to put my web pages on it. I don't know why it's not activated by default but hey...

What are the customary places for things? IE what goes in /bin vs. /usr/bin or /sbin etc. what about this xxx/local stuff? and /var's /shares? /sources?  I know there are customs but I have never known any of them nor ever seen them explained. I assume there is some standardization but I also know if differs by distribution. A real basic overview of the "standard" directory structure of the entire system would be very helpful. Especially since a very common response to a newbie question like how do I get blank running would be "you have to go to your blank installation folder and edit your conf file" Dunno where that is :)

What else should I know? I unfortunately don't know enough to ask any more intelligent questions but these are nagging questions having the answers to will help speed up and make more enjoyable the whole learning process.


Thanks!
Eric

Hi you can find alot of good info from the sticky's
[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)
:)

---

### Post by nowhere@cox.net on 2007-10-17
Hi and thanks for replying.

You are both correct. There is a lot of good information in both the links you gave, but neither of them answered even one of my sample questions.  The closest was in the help page where they did step you through the steps of setting up an FTP daemon.  This section did mention how to start the daemon:
```
 Once you configure vsftpd you can start the daemon. You can run following command to run the vsftpd daemon:

 sudo /etc/init.d/vsftpd start 
```

but this doesn't really explain what is going on. Is this specific to starting the ftp? Can I start, stop reset get status of other daemons?

The most important and ellusive question of the ones I asked was about the directory structure of Linux and Ubuntu.  What are the customs for locating files? A given software package like say firefox, or maybe gcc has files associated with it scattered throughout the entire directory structure on my hard drive. There are files in /bin /var/local /usr/share etc. What goes where and why?  I'm quite sure there are tons of new users like me that have gotten frustrated trying to troubleshoot and we have no idea where files go.

My example is Azureus 3.0 is out and I like it. Repositories only have 2.5. I downloaded the .gz, untarred it in my home folder and it runs fine from there. But it doesn't GO there. Other users dont have access  and now my apps are mixed in with my data etc.  Where does it go?

I am very verbose here because I assume my question wasn't understood. The responses had a bit of a RTFM tone to em but I prefer to think I wasn't clear in my question which is often the case when one doesn't know enough to ask a coherent question. :)

Anyway, thank you both. If I was more clear and you can still help I would appreciate it!

Eric

---

### Post by overdrank on 2007-10-17
> **nowhere@cox.net said:**
> 

I am very verbose here because I assume my question wasn't understood. The responses had a bit of a RTFM tone to em but I prefer to think I wasn't clear in my question which is often the case when one doesn't know enough to ask a coherent question. :)

Anyway, thank you both. If I was more clear and you can still help I would appreciate it!

Eric

HI and I did not mean to give the impression of RTFM. I could not answer all of you question and the sticky's including this one
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
Contain a wealth of material links and is a good reference. Good luck! :)

---

### Post by Duck2006 on 2007-10-17
> **overdrank said:**
> HI and I did not mean to give the impression of RTFM. I could not answer all of you question and the sticky's including this one
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
Contain a wealth of material links and is a good reference. Good luck! :)

Nice link thanks

---

### Post by nowhere@cox.net on 2007-10-17
Np and thanks. That page does have a lot of information but I would bet donuts that the directory structure is not covered. 

:)

Eric

---

### Post by overdrank on 2007-10-17
> **nowhere@cox.net said:**
> Np and thanks. That page does have a lot of information but I would bet donuts that the directory structure is not covered. 

:)

Eric
HI and hope these links will help
[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

---

### Post by nowhere@cox.net on 2007-10-17
WOW Yes, these are Awesome! Thanks a ton!!!

Eric

---

