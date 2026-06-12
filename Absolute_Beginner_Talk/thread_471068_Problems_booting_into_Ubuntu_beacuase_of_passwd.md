---
title: "Problems booting into Ubuntu beacuase of passwd"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by relneo on 2007-06-11
Hello,
I installed VNC but connect connect to my box remotely. So I ran:
vncpaswd
I was then able to connect to my Ubuntu box from my Windows XP machine. However, I noticed that on my Ubuntu machine, "sudo" was returning an error, which I forgot to write down but it was basically saying that userid 0, ie root, was not in the passwd file.
I then decided to reboot my machine and now I am not booting into GDM. Grub loads and then complains that user 'klog' cannot be found. I am prompted at some point to enter my username and password. I tried my username, I tried 'root'...none of them work.

PLEASE HELP!!!

---

### Post by HackingYodel on 2007-06-11
Which version of Ubuntu are you running and how/which VNC did you install?

What does you system boot into now, if GDM isn't working?  Is it console only or the GDM failsafe console?

Not to insult you, but have you tried the password you set with vncpaswd?

---

### Post by relneo on 2007-06-12
I am running Ubuntu 7.04 Server/Feisty.

As for where it boots to now, it boots into the console. All the daemon aren't loaded properly though, since early in the boot sequence I get the error described above. Upon pressing 'Enter' I am prompted for a username. I tried the password I set with vncpasswd and it doesn't work.

---

### Post by HackingYodel on 2007-06-12
Which VNC program did you install?

It sounds like it really did a number on your Linux installation.  klog has to do with the kernel log and klogd is a system daemon which intercepts and logs Linux kernel messages.

It may be best to reinstall Ubuntu at this point, but it's important we understand what the VNC program did to you system.  How did you install VNC for your Feisty server?

---

### Post by relneo on 2007-06-12
I'm not sure which VNC I installed.. :-(
I think it must have been TightVNC.
Reinstalling means having to reconfigure my applications, right (make, etc..)?

---

### Post by phr0ze on 2007-06-12
When it asks for your username did you try your ubuntu user name and password that you picked when you installed the system? Not the VNC password.

---

### Post by HackingYodel on 2007-06-12
relneo, my friend...

I think you nuked your Ubuntu installation.  I'm going to say that reinstalling is the only option I know that will work.

> Reinstalling means having to reconfigure my applications, right (make, etc..)?
I don't understand what you mean here.  I've been using Ubuntu since 5.10, FreeBSD and Debian for 2-3 years now and have never *needed* to use make...  **apt-get install** and **apt-cache search** are you friends.  I think Ubuntu has nearly 20,000 programs it can install and configure for you using **apt-get install**.

It may have been an error in the config file you used to make your VNC software that caused it to flip-out. After you reinstall, do **apt-cache search vnc** in a terminal and google some of the more interesting programs you see, excellent chance you'll find what you want without a make at all.

Hope that helps!

---

