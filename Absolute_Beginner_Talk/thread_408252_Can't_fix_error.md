---
title: "Can't fix error"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-04-13
I just did 'sudo apt-get install csh' which did something then died. The message I get is 'dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem' which is Double Dutch to me. Any help greatly appreciated. I'm building a new drive and there's lot to do yet! Cheers to all, Mike.

---

### Post by Fascination on 2007-04-13
Did you try running "dpkg --configure -a"? Also, I would try using "tcsh" as opposed to "csh" (sudo apt-get install tsch) - better support, and more user-friendly. :)

---

### Post by indytim on 2007-04-13
Get to your terminal.  When there, insert the following ONE LINE AT A TIME:

```
sudo apt-get -f install
sudo dpkg --configure -a
```

Good Luck,

IndyTim

---

### Post by MichaelSM on 2007-04-13
Wow that was quick. I don't have the terminal up any more, but when that error popped up I C&P'd it for the next line but it didn't fix anything when I entered it. I don't know what the command means anyway. Should I have put 'csh' in where 'a' is or something like that? 
The main issue is that I can't process any more new installs until the notification disappears from my screen in Synaptic.
If that makes any sense please reply. Thanks again, Mike.

---

### Post by MichaelSM on 2007-04-13
Hello IndyTim. That was an interesting exercise. It actually had nothing to do with csh, it relates to an install of abiword from synaptic which hung up for 15 minutes trying to configure abiword help. Here's the read-out: 

michael@michael-desktop:~$ sudo apt-get -f install
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
michael@michael-desktop:~$ sudo dpkg --configure -a
Setting up abiword-help (2.4.5-0ubuntu2) ...

It's still trying to do it in terminal  with the black block flashing. How do I fix it? Regards, Mike.

---

### Post by MichaelSM on 2007-04-13
Hi folks. It's fixed. I had to run the dpkg etc at the end of the abiword session. At least I can use synaptic now. I hope. Thanks for your replies. Regards, Mike.

---

### Post by indytim on 2007-04-13
The second line of code should fix adept so you can use it to install and/or remove applications.

IndyTim

---

### Post by MichaelSM on 2007-04-13
Thanks Tim. It did. Mike.

---

