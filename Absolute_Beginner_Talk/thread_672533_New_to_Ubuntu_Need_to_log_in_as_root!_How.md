---
title: "New to Ubuntu: Need to log in as root! How?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by toomuch on 2008-01-19
I just installed Ubuntu and now need to login as root.  How is this done?  I don't see it in my school book.

Thanks
Dawn

---

### Post by PgR on 2008-01-19
The short answer is "you don't"
In Ubuntu by default the root account has no password. 

Use ```
sudo <command>
``` instead. If you want a session as root, use ```
sudo -i
```

---

### Post by SunnyRabbiera on 2008-01-19
by nature ubuntu doesnt use root, instead the default user is given semi root privileges by using a system called sudo.

---

### Post by Joeb454 on 2008-01-19
If you post telling us exactly why you need to log in as root, I'm sure we can help you and get it sorted :)

---

### Post by toomuch on 2008-01-19
OK, thanks for the replies.  My lab asked me to:
1.  Boot into Linux and log in as root.
2.  Open a terminal window. How you do that will depend on the version of Linux you are running. The terminal looks like a DOS command window. Note: Some versions will give you access by right clicking on the desktop, others will use the Applications/Accessories menu. One of those methods should get a "Terminal" window for you. 

When i turn on the PC i get the log on screen and then password.  Were does root come in?

Dawn

---

### Post by Ub1476 on 2008-01-19
Log in as a user (with administrative privileges/default user). If you gonna play around in the Terminal, always doing root/sudo commands, open the terminal and type this:

```
sudo su
```

Now write the password you were given and you're 100% root.

---

### Post by databoy2k on 2008-01-19
You might need to try a different distribution of Linux. Ubuntu by default hides the root account. Like the guys said above, an administrator account in Ubuntu is able to add root privileges by typing "sudo" before any commands in the command line.
If you're going to use Ubuntu (i.e. not use another OS), add the word "sudo" before any commands that your lab tells you to execute in Terminal. You'll be asked for your password, and you'll be fine.
--Databoy2k

---

### Post by toomuch on 2008-01-19
Great!! that works... sudo.  Wonder why it wasn't in my book.  All well.

Thanks...:)

---

### Post by SunnyRabbiera on 2008-01-19
> **toomuch said:**
> Great!! that works... sudo.  Wonder why it wasn't in my book.  All well.

Thanks...:)

you might have an older book...
how old is this said book?

---

### Post by Steveway on 2008-01-19
> **toomuch said:**
> Great!! that works... sudo.  Wonder why it wasn't in my book.  All well.

Thanks...:)

Well even though sudo has been around for a very long time. (Afaik the first version for Unix-systems is dated back to about 1985)
It has not been commonly used untill some years ago.
Now the most preminant Operating-systems with sudo are Ubuntu and MacOSX.

---

### Post by Dr Small on 2008-01-19
Since nobody posted the link to the wiki article, I will :)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It explains it all ;)
Dr Small

---

