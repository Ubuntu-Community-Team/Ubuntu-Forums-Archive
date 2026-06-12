---
title: "Questions I've had since I first switched."
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-08-02
I'm happy to say that I am sticking with Ubuntu from here on out. My next laptop is going to be either from Dell or Sony (not a Ubuntu installed laptop from Dell, I want a more powerful laptop as a desktop replacement). I have a few minor problems which I would like to get sorted out.

1. I do NOT like mouse acceleration. I had already developed a muscle memory in XP, and once I got the install of Ubuntu settled, I found out the command to turn mouse acceleration off.

```
xset m 1 1
```

Sudo isn't needed, so I thought I could somehow add that command to a "start-up commands" list, because when I restart it is back to acceleration. What are the default ' xset m ' values just in case?

2. How do I get Num Lock to be on when Ubuntu starts? I know my BIOS has Num Lock defaulted to on and XP didn't change it. I'll check again, but I think it starts off on, then Ubuntu turns it off when it loads.

3. I have gotten some sort of " hda1 has been mounted 20 times, disk check forced " thing twice so far. It seems to check my hard disk. Is this normal? I got a bit scared my hard drive broke when it came up.

I might suggest the user gets a notification of that pending disk check next startup, if it is normal.

---

### Post by wolfen69 on 2007-08-02
yes, it is normal to do a file system check every x amount of boots. i think mine was 30.

---

### Post by wpshooter on 2007-08-02
> **kavon89 said:**
> I'm happy to say that I am sticking with Ubuntu from here on out. My next laptop is going to be either from Dell or Sony (not a Ubuntu installed laptop from Dell, I want a more powerful laptop as a desktop replacement). I have a few minor problems which I would like to get sorted out.

1. I do NOT like mouse acceleration. I had already developed a muscle memory in XP, and once I got the install of Ubuntu settled, I found out the command to turn mouse acceleration off.

```
xset m 1 1
```

Sudo isn't needed, so I thought I could somehow add that command to a "start-up commands" list, because when I restart it is back to acceleration. What are the default ' xset m ' values just in case?

2. How do I get Num Lock to be on when Ubuntu starts? I know my BIOS has Num Lock defaulted to on and XP didn't change it. I'll check again, but I think it starts off on, then Ubuntu turns it off when it loads.

3. I have gotten some sort of " hda1 has been mounted 20 times, disk check forced " thing twice so far. It seems to check my hard disk. Is this normal? I got a bit scared my hard drive broke when it came up.

I might suggest the user gets a notification of that pending disk check next startup, if it is normal.

Yes, I agree with you, that is a very good suggestion.  You might want to look into how you could pass this suggestion on to the developers.  Not really a bug, just a request for enhancement.

---

### Post by Raineer on 2007-08-02
I don't know what the dfaults are but to add to the startup you can add a line to /etc/rc.local and it will run at startup.

Like woflen said, it's normal to occasionally check, its part of linux

As for Numlock?  No clue at all, if you figure it out PLEASE post it, bugs the hell out of me.

---

### Post by Nervouswreck on 2007-08-02
A shell script might work. I'll post it if I can work one out.

---

### Post by Paul820 on 2007-08-02
For numlock, in the terminal type > gconf-editor then double click desktop->gnome->peripherals->keyboard->host-yourName->0 and click the box for numlock on

---

### Post by asmoore82 on 2007-08-02
install numlockx

```
~ $ sudo apt-get install numlockx
```

then Open "System -> Preferences -> Sessions"
click "New" -> name it and command: numlockx on
[AND]
click "New" -> name it and command: xset m 1 1

you can set mouse params back to defaults with the command

```
~ $ xset m default
```

---

### Post by kavon89 on 2007-08-02
> **Paul820 said:**
> For numlock, in the terminal type  then double click desktop->gnome->peripherals->keyboard->host-yourName->0 and click the box for numlock on

That doesn't seem to be a permanent change. Pressing Num lock  on the keyboard unchecks that box. Maybe there could be a little script to change it to true on boot?

I posted the suggestion about the disk check in the idea pool for gusty. [Check it out here.]("http://ubuntuforums.org/showthread.php?p=3122605#post3122605")

---

### Post by kavon89 on 2007-08-02
> **asmoore82 said:**
> install numlockx

```
~ $ sudo apt-get install numlockx
```

then Open "System -> Preferences -> Sessions"
click "New" -> name it and command: numlockx on
[AND]
click "New" -> name it and command: xset m 1 1

you can set mouse params back to defaults with the command

```
~ $ xset m default
```

I think you won this thread. Lemme restart and verify. :D

---

### Post by lambros on 2007-08-02
For Question 1: this is a GNOME user-specific setting.  Anything you put into /etc/rc.local will get overridden by GNOME as soon as you log on as a regular user.  Press Alt+F2, and type in
```
gconf-editor
```
to run the Configuration Editor.

Then navigate to: /desktop/gnome/peripherals/mouse
and have a look at the settings: "motion_acceleration" and "motion_threshold"

You can set those to your liking, then close the editor.  Changes will be permanent, and will be specific to your user account (so different users could have different settings).  I think those settings correspond to the same numbers that you use in the 'xset' command.

For Question 2: I believe you can install the 'numlockx' package:

```
sudo aptitude install numlockx
```

There's no configuration or anything like that.  Install it: you get NumLock switched on by default.  Uninstall it: you don't.  What could be easier? :-)

Sorry I don't know the answer to Question 3 off the top of my head.  I seem to remember seeing a software package you could install, which would give you warning before it does the next filesystem check.  For what it's worth, I think you can adjust the settings using the 'tune2fs' command.

Lambros

---

### Post by asmoore82 on 2007-08-02
EDIT: Never mind ... ::refresh:: Far Out!

---

### Post by philinux on 2007-08-02
Found this how to

[http://ubuntuforums.org/showthread.php?t=16891](http://ubuntuforums.org/showthread.php?t=16891)
:)

---

