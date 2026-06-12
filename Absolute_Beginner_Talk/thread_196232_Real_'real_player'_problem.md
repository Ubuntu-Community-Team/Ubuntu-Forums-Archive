---
title: "Real 'real player' problem"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by troica on 2006-06-13
I installed Real Player 10...of course, libstdc++5 package first.
I did this thing in terminal:
wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb)
sudo dpkg -i realplayer_10.0.7-0.0_i386.deb.
Installation completed sucessfully.
But when I open it, nothing's happen!
What did I miss?
There is "Real Player 10" icon under Sound & Video/Applications.

Thank you....troica

---

### Post by caldevil on 2006-06-13
try typing realplay in the terminal and see what happens.

---

### Post by tronica on 2006-06-13
*edit: opps caldevil beat me to it.*

---

### Post by troica on 2006-06-14
I did type 'realplay,' and this is the message;
/usr/bin/realplay: line 75:  5814 Segmentation fault      $REALPLAYBIN "$@"
I'm really new to LINUX.
I don't even know what that means.
Please help.....Troica

---

### Post by troica on 2006-06-14
Oh, when I type 'realplayer,' the message is like this;
*** glibc detected *** free(): invalid next size (fast): 0x0834e950 ***
/usr/bin/realplayer: line 75:  6829 Aborted                 $REALPLAYBIN "$@"

Thank you...Troica

---

### Post by harishg on 2006-06-14
I'm not sure of the problem.But easiest way to install reallayer is to download the bin file from [www.real.com.It](www.real.com.It) worked fine for me.

---

