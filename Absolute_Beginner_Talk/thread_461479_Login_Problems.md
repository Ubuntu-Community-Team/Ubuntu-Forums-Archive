---
title: "Login Problems"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by sabresong on 2007-06-01
Hello.

I've got a problem that seems to have started randomly.

Last night I was studying SQL (I'm fairly new to Linux, but not to computers) and entering SQL commands through the command line interface.  When I finished, I noticed that my taskbar at the bottom of the screen was missing.  Nothing I could think of brought it back, so I rebooted the machine.  The only thing I had done last night was apply updates from the update notification icon on the taskbar before it disappeared.

When the machine rebooted, I could not log in to my account on my computer through the GUI.
I can log in to my wife's account, and thought maybe I could fix the problem by reinstalling the KDE desktop, but my wife's account doesn't have sudo permissions.  I tried logging into the root account, but that's not permitted from the login screen.  Then I tried logging into the console under my account.  That worked, but my network card doesn't start automatically, and I can't seem to start it manually.  The command I'm using to do that is sudo /etc/init.d/networking.  It returns an unknown command error.  When I navigate to /etc/init.d, I see networking listed there.  The network connection works fine under my wife's login.

So I'm wondering what I can do to fix this login problem, and also what I'm doing wrong to start the network interface from the command line.

---

### Post by obrient on 2007-06-01
Have you tried to bring up the interfaces? 

```
sudo ifup -a 
```

This should bring up your network connection.

---

### Post by jonward0690 on 2007-06-01
sudo is'nt acting up is it

---

### Post by pmg on 2007-06-01
Why not login with the other account and start the network, and then switch to a console tty and login as yourself.  To get to a console tty hold the ctrl and alt keys and press F1. (You can also use F2-F6.  F7 takes you back to the Xserver.)  Then you can fix the problem from the command line, or give the other userid sudo access by running **sudo visudo** and copy the line for your userid.

---

### Post by sabresong on 2007-06-02
Thanks for the quick replies.

jonward, sudo seems to be behaving normally.

I tried the ifup -a command, but it reported devices not found.  It didn't list eth0 at all, which is my network card, and reported all the others as missing, which they are, so that's ok.  Is the eth0 thing maybe one of those "no news is good news" things that linux occasionally has?

The suggestion of logging into my wife's account, starting the network, then swithcing to console works very nicely. 

However, reinstalling the kubuntu desktop (apt-get remove kubuntu-desktop, apt-get install kubuntu-desktop) didn't fix the problem.  In fact, I'm not at all sure that it's being removed in the first place, since when I later uninstalled it I restarted the system before reinstalling, and it booted straight to the kde login screen.  I tried the same procedure with aptitude, with the same results.  I'm going to try one more time, since I'm not sure that I remembered to actuall log out of the wife's account, but in case that doesn't work, can you perhaps suggest some other way of getting into my account through kde?

In case it helps, I'm running Feisty 7.04.

---

