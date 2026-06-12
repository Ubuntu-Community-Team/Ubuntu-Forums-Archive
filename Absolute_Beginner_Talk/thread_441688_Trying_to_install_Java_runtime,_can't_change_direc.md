---
title: "Trying to install Java runtime, can't change directory"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by cypah on 2007-05-12
I have DLed the file .. jre-6u1-linux-i586-rpm.bin .. I can see it sitting on the desktop, under properties it says Location .. /home/herb/Desktop. The direstions say to change to there.
I have tried lots of typos :
herb@Belf:~$ cd /home/herb/desktop
bash: cd: /home/herb/desktop: No such file or directory
herb@Belf:~$ cd /home/herb/desktop/
bash: cd: /home/herb/desktop/: No such file or directory
herb@Belf:~$ cd $home/herb/desktop
bash: cd: /herb/desktop: No such file or directory
herb@Belf:~$ cd /home/desktop
bash: cd: /home/desktop: No such file or directory
herb@Belf:~$ cd /home/desktop/
bash: cd: /home/desktop/: No such file or directory

Whats wrong? Thanks

---

### Post by taurus on 2007-05-12
Linux is case sensitive so /home/herb/Desktop is NOT the same as /home/herb/desktop.

```
cd ~/Desktop
ls -la
```
On the other hand, java is available from the repos so use synaptic to install it.  Which release are you running anyway?

---

### Post by trak87 on 2007-05-12
"Desktop" should be capitalized. Unlike Windows, Unix/Linux is case sensitive.

---

### Post by cypah on 2007-05-12
Ohhhhh ok missed the D ok I am running Badger 5.10, intend to upgrade but just trying to learn Linux first since i already had this CD, any kind of advice and help is greatly appreciated.
Thanks herb

---

### Post by cypah on 2007-05-12
Hmmmm I can see maybe i am going where I maybe do not need to go. I did open Synaptic and asked it to update Java and it did but still Firefox asked for the runtime plugin. That was why I DLed the new Version file. 
I have upgraded everthing that came up after installation and reboot was like 230 packages .. Whew.

---

### Post by taurus on 2007-05-12
Even though Badger is not on the list, try to follow the directions for Dapper.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by cypah on 2007-05-13
Thanks Taurus
I followed that guide sucessfully but I have a broken package that is interferring with completing the upgrade. I have tried every whitch way to remove it but it fails, The package is 'lilypond'. I'm going to hang this up for now since I suspect upgrading to 6.10 will solve it anyway.

So thanks for the pointer, I learned a lot.
:)

---

### Post by zvacet on 2007-05-13
First of all you downloaded rpm package and that is why you are not able to install it.Ubuntu use deb file.if you followed taurus advice and still have broken package go to the **synaptic>edit>fix broken packages**
I hope it will help.

---

### Post by cypah on 2007-05-14
Ohhhh thanks Zvacet, 
(First of all you downloaded rpm package and that is why you are not able to install it.Ubuntu use deb file.
...I have not tried to install only cause I was making the D error. In the further reading I could see that even newer Ubuntu releases called for older than Java 6.0 so I knew I was over my head. 

(if you followed taurus advice and still have broken package go to the synaptic>edit>fix broken packages
...Ok the only one that breaks is lilypond,  the install ends up broken .. gets fixed breaks again and it refuses to be removed. I selected it just to play at so not important but trying to install any package results in error and aborts the install pointing to lilypond. It says to look in the terminal buffer for what went wrong ... haven't found that critter yet.  Gonna look some more later.

That is where I am tonight, feeling my way having not booted the Win rig in a week now. I guess you could say I am being weened. I did DOS before Win 3.1 so some stull is sorter coming back. I am using U-linux for the same desktop functions as I used W-ME(I resisted XP) so I like this OS and I am enjoying learning, I am 76orbits so lucky I can still do that.

At current I am running Firefox and thunderbird and Gaim for Internet and Open Office plus Getit. I have DLed a number of Packages that lure my interest but have not installed and used them yet. I ordered CDs for both Ubuntu 7.04 desktop/server CDs and Ubuntu 6.06.1 desktop/server CDs.

I am bored with retirement and am working on a line of paintings and sculpture and I will be using a 4 box network to connect three workstations up to share the server. I hope I can get your comments and advice, I live rural in SE Texas so the internet is my only hope for help and advice. I tried Fedora Core 6 but had a difficult time with it and the fellows on the SATLUG thought I may be better off with Ubuntu. Afrin had sent me this older distro so I followed the susgestion and I really like it much better, 

Do you agree that going to 6.06.1 is the best choice for me since it is LTS release?. I thought to do that and once all is secure upgrade my main workstation that I will be using mostly for Graphics work would be a way to stay updated, I think I am too new to even make that decision anyway, lol.

Big thanks for the help.
:)

---

