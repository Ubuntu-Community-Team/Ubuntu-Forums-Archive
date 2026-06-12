---
title: "when I log in, it logs me back out?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Zoiked on 2007-11-25
Just installed Ubuntu Gutsy fresh(not upgrade). Everytime I log in, it plays the login music and sits there for five seconds show just a light brown background and three seconds later it logs me right back out. 

The only way I can get in is to log in using the failsafe gnome. 

How do I fix this? 

Where do I find the startup scripts to turn off something that might cause the problem?

Thanks.

---

### Post by kelbizzle on 2007-11-26
I'm having the same exact issue on my laptop except I upgraded. Care to add it to my bug report? --> [https://bugs.launchpad.net/ubuntu/+bug/163223](https://bugs.launchpad.net/ubuntu/+bug/163223)

---

### Post by doftf on 2007-11-26
I am having the same issue.  When I log in with my user name and password, the system acts like it's loading -- shows the default tan background and the mouse icon.  However, after about 1 minute (I have a slow computer), I get the login screen again.  Same cycle.  I did the upgrade through Fiesty using a Wireless network adapter.

I did discover, however, that I was able to login through recovery mode.  But, being that I know very little about Ubuntu, I was unable to do anything from there.

I did have some customization to the 7.04 version before upgrading to 7.10 (Gutsy).  I have a custom login screen, and customized settings in terms of appearance.   System is an Intel Celeron 633Mhz with 256MB Ram & 8GB Hard drive.  7.04 ran very well, however a little slow.  Anybody have any ideas?  Is this a setting conflict with Gutsy?:confused:

---

### Post by kelbizzle on 2007-11-27
Did anyone add to my bug report?? Users of the forum don't develop this software. It seems like the only ones that can help us is the developers. UNLESS someone has already worked around this issue.

---

### Post by Grey Box on 2007-11-27
I used to have this problem randomly in Feisty. I had to go and delete the .Xauthority file and it would fix the problem. I have no idea what used to cause it, but sometimes after something crashed the window manager it would behave like this.

You could try to log in in text-mode (CTRL-ALT-F2) and type:

```
rm .Xauthority
```

And then go back to the login manager (CTRL-ALT-F7) and try again.  But please note, gnome crashing like that can have many causes and my simple fix is only one thing to try. Smarter people than me can help you better but they would need some kind of error information.

Also, try creating a different user and loging in there.

---

### Post by TorchlightJay on 2007-11-27
you may have 100% full partition, that can do it as well.

---

