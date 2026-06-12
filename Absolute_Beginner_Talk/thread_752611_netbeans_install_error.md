---
title: "netbeans install error"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by King Buttons I on 2008-04-11
I tried to install netbeans5.5 from the repository and it failed giving me this message:
    This Package is an installer package, it does not actually contain the NetBeans IDE. You will need to go download the IDE from:

And then it gives me the website and tells me I need to press the return key to try again or type no and the return key to abort. I abort and download it from the netbeans website and get it installed ok. Now whenever I go to install any program using apt-get or synaptic I get  this same error and have to type no and enter to get it to abort. Is there any way to stop this from happening.
Buttons

---

### Post by Biggy on 2008-04-11
install from Synaptic Package Manager

---

### Post by King Buttons I on 2008-04-11
I already have netbeans installed and working, but whenever I go to install or uninstall programs using synaptic or apt-get I still get the same error.
Buttons

---

### Post by Biggy on 2008-04-11
in terminal type :

1 )  sudo aptitude update
2 )  sudo aptitude safe-upgrade

---

### Post by StOoZ on 2008-04-11
it would be better to install it from source, in this case, just go to the website and download the latest version.

---

### Post by Crafty Kisses on 2008-04-11
> **StOoZ said:**
> it would be better to install it from source, in this case, just go to the website and download the latest version.

Yeah, I recommend downloading it from source, compiling it, then using it that way.

---

### Post by King Buttons I on 2008-04-11
Biggy
I ran sudo aptitude update and it ran fine. I ran sudo aptitude safe-upgrade and it went fine until the very end when I got this message:
```
Setting up netbeans5.5 (5.5-0.59) ...

This package is an installer package, it does not actually contain the
NetBeans IDE.  You will need to go download the IDE from:

From the NetBeans IDE 5.5 Download page:
http://www.netbeans.info/downloads/all.php?b_id=2323 

Select the English(en) tgz Download Archive Distribution 82.8 MB
http://www.netbeans.info/downloads/start.php?f_id=13710&lang_id=1

and place the file in /tmp (with root.root ownership) now.


[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of NetBeans IDE
dpkg: error processing netbeans5.5 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netbeans5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up netbeans5.5 (5.5-0.59) ...

This package is an installer package, it does not actually contain the
NetBeans IDE.  You will need to go download the IDE from:

From the NetBeans IDE 5.5 Download page:
http://www.netbeans.info/downloads/all.php?b_id=2323 

Select the English(en) tgz Download Archive Distribution 82.8 MB
http://www.netbeans.info/downloads/start.php?f_id=13710&lang_id=1

and place the file in /tmp (with root.root ownership) now.


[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of NetBeans IDE
dpkg: error processing netbeans5.5 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netbeans5.5

```

---

