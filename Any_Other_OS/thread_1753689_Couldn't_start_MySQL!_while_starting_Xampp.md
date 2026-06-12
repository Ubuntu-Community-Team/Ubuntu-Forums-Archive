---
title: "Couldn't start MySQL! while starting Xampp"
date: 2011-05-09
forum: Any Other OS
---

### Post by prativasic on 2011-05-09
Hi,
I am totally new in Linux. I tried to install Xampp on my Mint Julia x64 (built on Maverick). Since, there's no x64 version of Xampp, I installed [32bit version using ia-32libs]("http://ubuntuforums.org/showthread.php?t=719110"). Now, when I start xampp it says MySQL couldn't start. 
Here is my terminal ouput:
[INDENT]$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.4...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Couldn't start MySQL!
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
[/INDENT]And then as I go to "localhost", I got stuck on the xampp splash-screen- nothing happens if I choose language. Here is my [phpinfo()]("http://www.mediafire.com/?q4c9yug1375ubxm"). 
Can somebody help?

---

### Post by Perfect Storm on 2011-05-09
Moved to Other OS/Distro Talk.

---

### Post by prativasic on 2011-05-10
@AI, sorry for posting in wrong forum. But I checked it with my laptop which have Lucid x64 installed and I found the same error. I thought it was related to x64 ubuntu, but it was not. It was with root permission. And I just solved the problem. 

The reason I was getting this error for is, I extracted xampp using GUI. Instead, I was needed to extract it as su or root. I just redo the whole thing with su, and I succeed.

Sorry for being impatient. I'll be happy if this post save someone in future from the same error.

---

