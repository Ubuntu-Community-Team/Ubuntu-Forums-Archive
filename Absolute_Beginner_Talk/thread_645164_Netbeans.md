---
title: "Netbeans"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by browning_man9 on 2007-12-19
Hey! I am trying to install netbeans 6.0 and I'm getting a box with no text or anything in it. It's simply a gray window with nothing. After a search on the forum some other people had the same problem, but I don't know if they ever found a solution. Any ideas or suggestions? Thanks!

root@dave-ubuntu:/home/dave/NetBeans# ./netbeans-6.0-javaee-linux.sh
Configuring the installer...
Searching for JVM on the system...
Extracting installation data...
Running the installer wizard...
/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:242: Priority specification is unsupported, ignoring



I tried changing to some different themes, and that only gave a different error:

root@dave-ubuntu:/home/dave/NetBeans# ./netbeans-6.0-javaee-linux.sh
Configuring the installer...
Searching for JVM on the system...
Extracting installation data...
Running the installer wizard...
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: lexical error or unexpected token, expected valid token

---

### Post by LookUpSeeBlu on 2008-01-22
I also am running into this issue.  I ended up having to use 5.5 and which installed but gave me that blank screen on opening.  This:

[http://ubuntuforums.org/showthread.php?t=299335]("http://ubuntuforums.org/showthread.php?t=299335")

fixed the SECOND issue.  Still nothing on the first... 

:(

---

### Post by bump_ on 2008-01-22
Hi,

Netbeans does not play well with compiz fusion. If you turn compiz off, you should be able to install and run Netbeans

---

### Post by MockY on 2008-02-15
It is very annoying to disable/enable compiz every time I use Netbeans. I really hope they find a solid solution soon.

---

### Post by Biggy on 2008-04-04
how to enable/disable compiz ?

---

### Post by rajaram_s on 2008-04-04
I am having both compiz and netbeans both of them working absolutely great... What version of net beans were you tring to install?

---

### Post by rajaram_s on 2008-04-04
Anyway, to diable compiz goto preference -> appearance,

select the visual effects tab and select none.

---

### Post by Biggy on 2008-04-04
NetBeans IDE 6.0.1 " All "

---

### Post by Biggy on 2008-04-04
yeah i disable compiz in Preferences > Appearance > Visual Effects > None

but problem still given..

---

### Post by Biggy on 2008-04-04
help plzz !

---

### Post by Biggy on 2008-04-04
/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:242: Priority specification is unsupported, ignoring

---

### Post by Aeph on 2008-04-08
I got the same thing. In the end, I just used Netbeans 5.5 from the synaptic manager.

---

### Post by BabaQ on 2008-04-16
> **Biggy said:**
> yeah i disable compiz in Preferences > Appearance > Visual Effects > None

but problem still given..
maybe you could try disabling it this way:
open a terminal and type:
```
metacity --replace
```

---

### Post by YoG%*@ on 2008-04-17
> **bump_ said:**
> Hi,

Netbeans does not play well with compiz fusion. If you turn compiz off, you should be able to install and run Netbeans

thank you, that saved me a lot of time and frustration today!
mux

---

