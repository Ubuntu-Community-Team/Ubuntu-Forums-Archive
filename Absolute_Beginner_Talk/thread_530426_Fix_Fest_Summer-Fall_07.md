---
title: "Fix Fest Summer-Fall 07"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by siraf on 2007-08-20
Hey all,
I've felt guilty for having run ubuntu since Warty and not really been active in the community. So this week, I'm giving something back.
Here's how I'd like this thread to work:

[LIST=1]
[*]Scan the thread for a problem that you have solved.
[*]Post the solution or a tip to that problem.
[*]Post your problem, if you have one.
[*]Smile, your in the ubuntu community. :)
[/LIST]

example:

(since there are no posted problems, I'll think of one I recently solved)

fooPerson: I can't get my compiz-fusion to work! the windows don't have borders!

me: try running "gtk-window-decorator --replace". If that still doesn't work, try removing any nvidia software if you know that your box doesn't use nvidia. The beryl compositor seems to have issues with it.

me: My sound card works, but I can't get the mike to be detected. It's on the front of my gateway cx2726. 

etc...


I realize that the ENTIRE forum is built for this, but I figure that one thread with some quick suggestions might also help. Pay it forward, and remember, even if you know every piece of software and every piece of software, and even if you're linus tordvalds himself, you're still a newb at heart.

---

### Post by pgar23 on 2007-08-20
payton@the-desktop:/usr/local/src/ndiswrapper-1.47$ cd /usr/local/src/Drivers
    payton@the-desktop:/usr/local/src/Drivers$ ls
    WUSB54GS.cat  WUSB54GS.inf  WUSB54GSv2.cat  WUSB54GSv2.inf
    payton@the-desktop:/usr/local/src/Drivers$ cd
    payton@the-desktop:~$ ndiswrapper -v
    utils version: '1.9', utils version needed by module: '1.9'
    module details:
    filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
    version:        1.47
    vermagic:       2.6.20-15-generic SMP mod_unload 586 
    payton@the-desktop:~$ cd /usr/local/src/Drivers
    payton@the-desktop:/usr/local/src/Drivers$ sudo ndiswrapper -i WUSB54GSv2.inf
    installing wusb54gsv2 ...
    [FONT=Times]couldn't find SourceDisksFiles section - continuing anyway


Here's my problem. I will pay it forward by posting solution in my thread...
[/FONT]

---

### Post by siraf on 2007-08-20
do you have the "linux-restricted-modules" installed? also, I think there is a "modprobe" command that may help you.
Could you also put the link to your thread up?
I'm no expert with wrapping, but I hope that helps somewhat.

---

### Post by pgar23 on 2007-08-20
Link to my thread:  [http://ubuntuforums.org/showthread.php?t=530422](http://ubuntuforums.org/showthread.php?t=530422)

What is "linux-restricted-modules"?

---

### Post by siraf on 2007-08-20
it all depends on your pc architecture. but for x86 i believe : "linux-restricted-modules-2.6.17" is what you want. just apt-get install that.
Also, after that's installed, go to system>administration>linux restricted 
good luck.

---

### Post by pgar23 on 2007-08-20
but what is that??? do you mean restricted drivers manager???<--------I have this one.

---

### Post by siraf on 2007-08-20
> **pgar23 said:**
> but what is that??? do you mean restricted drivers manager???<--------I have this one.

Then just check it in the menu, the driver shouldn't need wrapping, or maybe it does. I don't know. Try installing the ".cat" file first.

---

### Post by pgar23 on 2007-08-20
Thanks for trying. :)

---

