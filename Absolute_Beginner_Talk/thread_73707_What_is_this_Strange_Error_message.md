---
title: "What is this Strange Error message?"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by sbleecker on 2005-10-09
What is this Strange Error message?

After reinstalling Yellow Dog on a Mac PowerPC, I got this flashing error message;

According to /var/run/gmd.pid gmd was already running, (number) but seems to have been murdered mysteriously.

It keeps flashing off and on, and will not let me do anything except Control/Alt/Del to restart, then after reloading it starts all over again.

What is going on, and how do I stop it?

---

### Post by Kyral on 2005-10-09
Not to sound rude....but wouldn't this be a better question for the Yellow Dog forums?

---

### Post by sbleecker on 2005-10-09
I don't know if this is a generic LINUX thing or something unique to Yellow Dog.  I have been trying to install LINUX on my Mac's for awhile, and sometimes it works and sometimes I get strange things happening that I don't understand.  
    I have several books on LINUX and Red Hat, but most are not much help as there are about PC's and not Mac's.  I need someplace that I can get answers, and help in general.  Maybe I need a different version of LINUX, or maybe I need to just get the one I have working.  I don't know.

---

### Post by cwaldbieser on 2005-10-10
[QUOTE=sbleecker]What is this Strange Error message?

After reinstalling Yellow Dog on a Mac PowerPC, I got this flashing error message;

According to /var/run/gmd.pid gmd was already running, (number) but seems to have been murdered mysteriously.

It keeps flashing off and on, and will not let me do anything except Control/Alt/Del to restart, then after reloading it starts all over again.

What is going on, and how do I stop it?[/QUOTE]
Here is my educated guess:
The program you are trying to run is only supposed to have one instance running at a time.  Therefore, when it starts up, it creates a file called /var/run/gmd.pid that has its process ID as it's contents.  When the program shuts down, it removes this file.

However, the program got killed without being able to remove the file.  It detects that the process is not running, so it gives you the kooky error message.

I would try logging in via a console (virtual terminal-- normally press CTRL-ALT-F1).  Then I would try to erase the /var/run/gmd.pid file.  Then I would try rebooting with:
```

# shutdown -r now

```
You could also ask around over at linuxquestions.org.  There is usually lots of multi-distro knowledge floating around there.

---

