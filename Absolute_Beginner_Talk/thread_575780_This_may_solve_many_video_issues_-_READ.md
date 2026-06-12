---
title: "This may solve many video issues - READ"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by njhomeowner on 2007-10-14
Hello,

I see a lot of posts here about people having difficulties getting their video to perform well.  I was also having these problems.  I have a "no-name" video card with an SIS chipset and 32MB of ram that was awfully slow.

I came across the following post on Google's Linux Group:

[http://groups.google.com/group/linuxusersgroup/browse_thread/thread/7446fdb594822f3/026986876027d057?lnk=gst&q=video+drivers#026986876027d057](http://groups.google.com/group/linuxusersgroup/browse_thread/thread/7446fdb594822f3/026986876027d057?lnk=gst&q=video+drivers#026986876027d057)

After running the command "sudo dpkg-reconfigure xserver-xorg " and answering the questions the video performance was significantly increased.

Try it out and post back here with results.

Thanks!!!

---

### Post by crav on 2007-10-14
Can anyone else confirm this?

---

### Post by njhomeowner on 2007-10-14
Did you try this?  I am running Fiesty Fawn on 2 machines and ran it on both with the same excellent results.

Maybe it's me?

---

### Post by jordanmthomas on 2007-10-14
> **crav said:**
> Can anyone else confirm this?

How could choosing the proper driver be a bad thing?

---

### Post by aktiwers on 2007-10-14
I normally only use that command if I messed up xorg and forgot to make a backup.

---

### Post by RedSquirrel on 2007-10-14
> **njhomeowner said:**
> After running the command "sudo dpkg-reconfigure xserver-xorg " and answering the questions the video performance was significantly increased.

Try it out and post back here with results.

Yes, that's a standard command to create the file /etc/X11/xorg.conf (and it will create a backup of your current xorg.conf file).

Here's a link to more video configuration ideas:

**HOWTO: change resolution/refresh rate in Xorg**
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

