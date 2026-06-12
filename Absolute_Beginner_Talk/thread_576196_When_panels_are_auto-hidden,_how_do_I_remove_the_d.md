---
title: "When panels are auto-hidden, how do I remove the delay from them popping up?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-10-14
Thanks for the help!

---

### Post by juantovarm on 2007-10-15
i use ktorrent, it's the best i've ever used, all you have to do is reload the program and it starts downloading again, you can find it in add/remove

give it a try, you won't be dissapointed

---

### Post by iamthemicrowave on 2007-10-15
Haha thanks, but I've decide to go back to Azureus.

---

### Post by Beggar on 2007-10-15
In the future, please leave your question, so that other forum member might be able to learn from it. If you problem has been resolved, instead mark the thread as solved.

[Mark as solved.]("http://ubuntuforums.org/showthread.php?t=524404&highlight=mark+as+solved")

---

### Post by iamthemicrowave on 2007-10-15
My problem hasn't been solved.  It is the title of the thread.  I had a question about the Bittorrent client, but I resolved it myself and deleted it.

---

### Post by iamthemicrowave on 2007-10-16
Please tell me the answer someone! It can't bet that hard come on.

---

### Post by juantovarm on 2007-10-16
are you using gnome desktop or kde?

---

### Post by ThrobbingBrain66 on 2007-10-16
In gconf-editor:

Apps > Panel > Global

There are two values you may want to change:  panel_hide_delay and panel_show_delay

---

### Post by iamthemicrowave on 2007-10-16
I am using GNOME desktop 2.20.

When I tried changing those values to 0, nothing happened.  I looked around and found this error message(edited for readability):

No database available to save your configuration: Unable to store a value at key '/apps/panel/global/panel_hide_delay', as the configuration server has no writable databases. There are some common causes of this problem: 

1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 

2) somehow we mistakenly created two gconfd processes 

3) your operating system is misconfigured so NFS file locking doesn't work in your home directory 

or 

4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf.

The only error I understand was the first one, I checked and that file does exist.  Please help.

---

