---
title: "Web Developers: IE &amp; Opera"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by GaFFy on 2006-05-09
I develop web sites and recently switched my server and development computers to Ubuntu.  Everything is working great and this freedom is getting to my head. :mrgreen: 
Problem is I need WinXp (:evil: ) to test how my sites look/work in IE and Opera.

I cant see any other reason for me not to be 100% Ubuntu/Linux.

Anyone know if there is a way to run IE (wine?) and Opera (stoopid errors) in Ubuntu?
I know Opera should but I cant get it to install. ](*,) 

"The following packages have unmet dependencies:
  opera: Depends: xlib6g (>= 3.3.6) but it is not installable or
                  xlibs but it is not installable
         Depends: libqt3c102-mt but it is not installable"

Thanks

---

### Post by mostwanted on 2006-05-09
Opera should be pretty easy to install? Just download the deb from the opera site and install it.

If you want IE (version 6, 5.5, 5 for Windows 98) you can install it with this genious script (WINE is required obviously):

[http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)

---

### Post by towsonu2003 on 2006-05-09
[QUOTE=GaFFy]
I know Opera should but I cant get it to install. ](*,) 

"The following packages have unmet dependencies:
  opera: Depends: xlib6g (>= 3.3.6) but it is not installable or
                  xlibs but it is not installable
         Depends: libqt3c102-mt but it is not installable"
[/QUOTE]
According to these two, it is Opera's fault: 
[https://launchpad.net/distros/ubuntu/+source/qt-x11-free/+bug/22138](https://launchpad.net/distros/ubuntu/+source/qt-x11-free/+bug/22138)
[https://launchpad.net/distros/ubuntu/+source/qt-x11-free/+bug/2724](https://launchpad.net/distros/ubuntu/+source/qt-x11-free/+bug/2724)

Both bug reports are rejected. Try downloading it in tar.gz format, untarring (the firefox style), and executing opera inside the untarred directory...

---

### Post by GaFFy on 2006-05-09
sweet, installing IE now!
I will try that Opera I guess.  I have been trying to stick with software from Ubuntu sources...I just think its safer? :-k

---

### Post by aggiechemist on 2006-05-09
I use Opera, and I think and went and installed all the packages it was complaining about. I just did

sudo apt-get xlibs6g

or whatever it was, and did that for each one. My Opera runs pretty well.

On the downside, I can't get plugins to go. No flash or quicktime (well, MPlayer) or such for me in Opera. I have to get out Firefox for that.

---

### Post by GaFFy on 2006-05-09
I got IE6 installed and the shortcut is on the Desktop but it doesnt do anything when I run it.:confused:

---

### Post by GaFFy on 2006-05-09
nevermind I searched around and found this thread
[http://ubuntuforums.org/showthread.php?t=132508](http://ubuntuforums.org/showthread.php?t=132508)

Installed the new 2 beta from the link and it is working wonderfully :mrgreen:

---

### Post by arsenic23 on 2006-05-09
I use Opera as my primary browser in both windows and Ubuntu and have 0 problems with it on every machine I'm running it on.  The best way I've found to get it to work is by adding 

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

to your sources.list and then messing around with the instructions found here:

[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

