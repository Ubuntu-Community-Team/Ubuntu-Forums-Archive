---
title: "&quot;xset s&quot; not working"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-03-28
Hi, 

Woudl you have any idea : 
why ```
xset s on
xset s blank
xset s 5
```
is working on my laptop  linux  breezy and not on a Tower Linux breezy ?


(I have no xscreensaver running in the process)
( and xset installed ; apt-get -y install xset)

Greetings, 

Thank you

---

### Post by Pragmatist on 2006-03-29
According to the xset man page:

>  The 'blank' flag sets the preference to blank the video (**if the hardware  can  do  so**) rather than display a background pattern 
So maybe your tower system's hardware doesn't support blanking the video. One way to check is to try 'noblank' and see if that works.

xset s on
xset s noblank
xset s 5

---

### Post by patrick295767 on 2006-03-29
[QUOTE=Pragmatist]According to the xset man page:

 
So maybe your tower system's hardware doesn't support blanking the video. One way to check is to try 'noblank' and see if that works.

xset s on
xset s noblank
xset s 5[/QUOTE]
  
I checked again and it worked !!! 
I even didnt think to  check it ,  I trusted too much my fvwm config. 

Thanks man, I certainly have a duplicate line command in my fvwm, that s crazy 'cos I checked it several times.
  
I am wondering damn where is the error, I certainly override the xset by sthg. 
  
Thanks !!
  
(by the way , maybe ...  )
Next step and by the way, would you eventually know under Ubuntu how to make weither xset or xscreensaver for the gdm ?? I found sthg for redhat but not ubuntu ... 
  
and : 

[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man1/xscreensaver.1.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man1/xscreensaver.1.gz)
> USING GDM(1)
The instructions for using xscreensaver with gdm(1) are almost the same as for using xdm(1), above. There are only two differences, really: instead of editing /usr/lib/X11/xdm/Xsetup, edit the file /etc/X11/gdm/Init/Default; and instead of editing /usr/lib/X11/xdm/Xsession, edit one or all of the files in the /etc/X11/gdm/Sessions/ directory. (Note that the default session (/etc/X11/gdm/Sessions/Default) usually simply executes /usr/lib/X11/xdm/Xsession, so be careful you aren't initializing xscreensaver twice.)
  
Greetings !!!

---

### Post by Pragmatist on 2006-03-29
The xscreensaver man page on at the URL you give is very old (2001).  Just type this in a terminal:
```
man xscreensaver
```

The information should be as of 2005(!) and it also has a very different explanation for what you want to do.  It talks about** configuration tools**, how to setup in different D.E.s than GNOME (KDE, CDE, VUE, etc..etc...)

---

