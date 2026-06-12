---
title: "Network printer woes..."
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-01-22
Hi...  there's a reason I'm posting this in 'absolute beginners' so please don't be too hard on me!

I have an Ubuntu machine connected to a windows XP machine via ethernet card/cable.  The Windows machine has the internet connection and the printer.

On the Linux machine, the internet connection is fine.  And when I try to set up the printer, everything SEEMS fine - until I try to print!

Ubuntu detects the printer. I selected the Samba option, like it says in the Official Ubuntu book.  But It just won't print.  I've done Google searches, but they make it all seem fiendishly difficult and complicated - I'm nervous about editing configuration files, as the book seems to suggest it should just 'work'.

If it helps, when I check the properties of the printer, I get the message that the network printer is 'busy' and that it will try again in 30 seconds.

If anyone could point me to something on 'get your network printer working for complete dummies', I'd be really grateful.

Also, just in case this is connected to the problem: Samba does have problems accessing the shared folders on the windows machine.  It can SEE them, but when I click on them, it won't let me open them.  On the other hand, the windows machine sees the shared ububtu folders with no problem and gives me full access to them.

I'd be really grateful for any advice. My ambition is to get free of windows altogether, but it looks like I have a long way to go!

Thanks!

---

### Post by scrooge_74 on 2007-01-22
Been able to inter connect is a little tricky.  What XP version are you using?  When you try to connect to the XP box does it ask you for user and password? 

Connecting printers in a LAN is tricky also, it wont print because it has to do with the same problem you have with the folders.

Check this [thread]("http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138") it could be the solution to your problem

---

### Post by neoflight on 2007-01-22
did you try connecting the the printer directly to the ubuntu-box?

ihave no problem printing from a windows network...

just add new printer and select the appropriate driver...give the ip pf the printer if possible..that will make it fast rather than the system trying to figure out what  the printer in the network is

---

### Post by whitefort on 2007-01-23
Thanks for the replies, guys.

I'm afraid I still haven't got it working.  I don't think the Firestarter thread really applies, as I'm not running Firestarter (or any other firewall yet) on the Linux machine.

The situation is still that Linux can 'see' the printer and all the shared folders on the windows machine - it's just that in the case of the printer, it still refuses to print, and in the case of the folders when I click on them I get the message that the contents can't be displayed.

There isn't any password involved, because there's no password set up on the windows machine.

The printer is OK with Ubuntu - just not over the network.  I've googled and googled this, and haven't found anything that works (yet - and I'm kinda losing hope).  If Ubuntu is going to be viable for me, I'll need to be able to access the network properly.

This Ubuntu stuff is really, really hard!  :( 

Thanks again.

---

### Post by scrooge_74 on 2007-01-23
You probably are going to need to read further into SAMBA to get it working

---

