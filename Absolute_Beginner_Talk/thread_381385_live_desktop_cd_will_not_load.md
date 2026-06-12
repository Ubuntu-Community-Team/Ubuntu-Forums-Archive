---
title: "live desktop cd will not load"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by dakuda on 2007-03-10
I am trying to run v6.06 on the live destop cd, to give it a whirl.

I have tried burning the *.iso to a CD several times so far today.  I have burned one at 40x, one at 10x, and one at the slowest (I selected 1x, it burned at 4x) I could get my burner to go.  I used InfraRecorder to make all the CDs.  I checked each for errors, so the CDs are currently error free.

However, every time I attempt to run the CD, I get an error stating the X server is configured incorrectly.  I can choose yes or no to look at the configuration files, then I get sent back to the DOS-like screen and nothing more occurs.  

ANy advice?  My computer is a Dell PowerEdge SC 420 with 512MB RAM, DVD-ROM, and 2 120GB HDs.

---

### Post by overdrank on 2007-03-10
> **dakuda said:**
> I am trying to run v6.06 on the live destop cd, to give it a whirl.

I have tried burning the *.iso to a CD several times so far today.  I have burned one at 40x, one at 10x, and one at the slowest (I selected 1x, it burned at 4x) I could get my burner to go.  I used InfraRecorder to make all the CDs.  I checked each for errors, so the CDs are currently error free.

However, every time I attempt to run the CD, I get an error stating the X server is configured incorrectly.  I can choose yes or no to look at the configuration files, then I get sent back to the DOS-like screen and nothing more occurs.  

ANy advice?  My computer is a Dell PowerEdge SC 420 with 512MB RAM, DVD-ROM, and 2 120GB HDs.

Hi when you get to the dos like screen try this command *sudo dpkg-reconfigure xserver-xorg * and follow the instructions and I hope this helps. Good luck!

---

### Post by dakuda on 2007-03-10
> **paul capps said:**
> Hi when you get to the dos like screen try this command *sudo dpkg-reconfigure xserver-xorg * and follow the instructions and I hope this helps. Good luck!

I will clarify.  I go back to a text-based screen (hence my term, DOS-like), but there is no command line or cursor.  It seems to go back to the text that scrolls while loading, and just freezes.  SO, I cannot enter any commands.

---

### Post by lukem on 2007-03-10
dakuda

It sounds like the live cd is having a problem properly detecting your video setup.  If you never get back to the command line you can't fix it at that point.   I'm sorry not to be of more help, but if there are any options at boot time you might try that.

don't give up

---

### Post by 3rdalbum on 2007-03-11
Try pressing Control-Alt-F2 to bring yourself to a real command line.

---

