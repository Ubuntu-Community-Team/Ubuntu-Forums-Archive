---
title: "Two questions"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by klemen912 on 2007-10-14
1. What is "sudo"? In Terminal, I tried to enter password but i can't type anything.
2. Is it there a way to open .exe file in Ubuntu (like uTorrent), because I want to play Darwinia, that is supported by Linux.

---

### Post by bodhi.zazen on 2007-10-14
> **klemen912 said:**
> 1. What is "sudo"? In Terminal, I tried to enter password but i can't type anything.

The password is the same as your log-in. You will not see text in the terminal as you type.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


> 2. Is it there a way to open .exe file in Ubuntu (like uTorrent), because I want to play Darwinia, that is supported by Linux.

You may be able to run with wine.

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by ddrichardson on 2007-10-14
> **klemen912 said:**
> 2. Is it there a way to open .exe file in Ubuntu (like uTorrent), because I want to play Darwinia, that is supported by Linux.

There's a native Linux version on their homepage: [here]("http://www.introversion.co.uk/cgi-bin/countdowndarwinia.cgi?darwinia-demo2-1.3.0.sh").

---

### Post by GutsyGibbon on 2007-10-14
> **klemen912 said:**
> 1. What is "sudo"? In Terminal, I tried to enter password but i can't type anything.

SUDO - **_S_**uper **_U_**ser **_Do_**.

When you're trying to enter your password it may appear as if you're typing nothing, but it's actually just a "hidden-password" security feature. Just type your password, even tho you can't see it, and press your "Return" / "Enter" key.


Good luck,
***GutsyGibbon (Dean)***

---

### Post by aysiu on 2007-10-14
It's not really a great security feature, and, if you think it is, you'd better turn off the black dots that appear for GUI apps!

Read more here:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by Palmyra on 2007-10-14
Whenever you're trying to do something that requires administrative privileges, you are required to enter the administrative password.  This is known, in the Linux world, as your sudo password.  Once you have entered the password, you are now in sudo mode, or administrative mode.  

Sudo is required for anything system wide.  If you are trying to alter anything outside of your home folder (the home folder is the Linux equivalent of the My Documents folder in Windows), you must be in sudo mode.  

When using the terminal, and when you are entering your sudo password, the password will be blank.  Of course, this is done for obvious reasons.  

I don't know what uTorrent is, but you may be looking for something like Deluge.  Do a forum search on Deluge.

---

