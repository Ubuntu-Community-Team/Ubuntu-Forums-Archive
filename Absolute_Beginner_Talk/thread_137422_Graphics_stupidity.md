---
title: "Graphics stupidity"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by seedman on 2006-02-27
I'm a real newbie who just understood sudo long enough to mess up my system.
I used the command  *$sudo dpkg-reconfigure xserver-xorg  * to try to fix a graphical issue I'm having.
Then I changed somthing for some reason (lack of foresight) and now I get 

Failed to start xserver

It also offers to auto-somthing, but I never get the option because it drops me into command line login.

I'd RTFM but I don't know where one would be or what I did.  
OR... My drive is partitioned with ubuntu on twice (minor foresight).  could I save files from my mistake?
-thanx.
-M

---

### Post by newuser111 on 2006-02-27
just run sudo dpkg-reconfigure xserver-xorg again and select whatever graphics card you have

---

### Post by codejunkie on 2006-02-27
[QUOTE=seedman]I'm a real newbie who just understood sudo long enough to mess up my system.
I used the command  *$sudo dpkg-reconfigure xserver-xorg  * to try to fix a graphical issue I'm having.
Then I changed somthing for some reason (lack of foresight) and now I get 

Failed to start xserver

It also offers to auto-somthing, but I never get the option because it drops me into command line login.

I'd RTFM but I don't know where one would be or what I did.  
OR... My drive is partitioned with ubuntu on twice (minor foresight).  could I save files from my mistake?
-thanx.
-M[/QUOTE]
try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
```this should auto configure the xserver.

---

### Post by seedman on 2006-02-28
[QUOTE=codejunkie]try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
```this should auto configure the xserver.[/QUOTE]



This advice worked.  I bow in thanks and awe.  Ubuntu's forums (and you sweet codejunkie) were both fast and accurate!
I aspire to reach such heights.
\\:D/ 
the only person happier then me is my girlfriend.
-Thanx!

---

