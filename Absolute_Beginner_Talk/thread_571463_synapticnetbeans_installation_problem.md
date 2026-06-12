---
title: "synaptic/netbeans installation problem"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by moon_goose on 2007-10-09
Hello

I have tried installing NetBeans 5.5 and something went wrong - installer just got stuck. Now when I am trying to use dpkg, it says:
[HTML]
$ sudo dpkg --configure -a
Password:
Setting up netbeans5.5 (5.5-0.59) ...

This package is an installer package, it does not actually contain the
NetBeans IDE.  You will need to go download the IDE from:/

From the NetBeans IDE 5.5 Download page:
http://www.netbeans.info/downloads/all.php?b_id=2323 

Select the English(en) tgz Download Archive Distribution 82.8 MB
http://www.netbeans.info/downloads/start.php?f_id=13710&lang_id=1

and place the file in /tmp (with root.root ownership) now.


[Press RETURN to try again, 'no' + RETURN to abort] [/HTML]

So I downloaded IDE manually and put it into /tmp, which didn't help
/var/lib/dpkg/updates is empty

TIA

---

### Post by luisromangz on 2007-10-09
Have you changed the file ownership?

By the way, you can just extract the tar.gz you downloaded, and use the installer inside.

I don't see the point in having a netbeans .deb if it doesn't download the tar.gz by itself at least.

---

