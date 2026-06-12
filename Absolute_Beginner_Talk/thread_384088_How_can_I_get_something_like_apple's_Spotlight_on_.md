---
title: "How can I get something like apple's Spotlight on ubuntu?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by diargasm on 2007-03-14
I put the "search for files" panel at the task bar, but I want something more like spotlight.  I found something called "gnome deskbar applet" which seems to be what I am looking for, but the instructions are too difficult.  can someone assist me with that?  It says "Execute the following steps to install deskbar-applet" and then gives a bunch of code.  How do I execute it?  Where do I go.  HELP ME!

---

### Post by orkim on 2007-03-14
Typically you will type it in the Terminal.  If it is full of "apt-get blah" or "sudo blah" stuff this is exactly where you should execute these commands.

You can find that in your menu.  Open it up and copy the commands in there.  Typically its a good idea to understand what the commands do, but if it's from a trustworthy source you should be OK.

Best of luck!

-orkim

---

### Post by silhouette on 2007-03-14
The applet is called Deskbar, and you install it by running

sudo apt-get install deskbar-applet

inside of a terminal window. Then, you can right click on the top panel, select Add to Panel, then choose Deskbar.

---

### Post by diargasm on 2007-03-14
So I did that and it says ```

andre@andre-laptop:~$ 
andre@andre-laptop:~$ sudo apt-get install deskbar-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
deskbar-applet is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andre@andre-laptop:~$ 
andre@andre-laptop:~$ 

```

Does that mean it was installed?

--- Edit -- 

Hey thank you very much!!!!

---

### Post by angkor on 2007-03-14
> **diargasm said:**
> So I did that and it says ```

andre@andre-laptop:~$ 
andre@andre-laptop:~$ sudo apt-get install deskbar-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
deskbar-applet is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andre@andre-laptop:~$ 
andre@andre-laptop:~$ 

```

Does that mean it was installed?

--- Edit -- 

Hey thank you very much!!!!

Then you've already got the applet installed.

Just right-click a panel and add the deskbar-applet.

---

### Post by el_rata on 2007-04-01
check here for the spotlight-like application

[http://www.ubuntuforums.org/showthread.php?t=347364&highlight=spotlight+for+gnome](http://www.ubuntuforums.org/showthread.php?t=347364&highlight=spotlight+for+gnome)

---

