---
title: "EasyUbuntu install question"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by bobmorris on 2006-09-04
Installing EasyUbuntu
[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

It says to run these four lines in terminal

wget [http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2](http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2)
tar -jxvf current.tar.bz2
cd EasyUbuntu_2006-XX-XX
sudo python easyubuntu.in

When I run the last line I get

"You cannot run EasyUbuntu as root. Please run it as a user."

There's only one user, me. Do I need to make another one?

---

### Post by baldy1324 on 2006-09-04
then just run ```
python easyubuntu.in
``` without sudo. sudo temporarily makes you the root (administrator equivelent in windows) so you have root and you as users and many others for specific tasks like ftp and ssh...8) 
it will probably then ask you for your password later.

---

### Post by szf on 2006-09-04
I have to say that I've been on both sides of the coin with EasyUbuntu (which rocks, btw)... Our home system required me to be admin, whereas another system required a local user.

That said,

Change directory (cd) to the EasyUbuntu directory in your Ubuntu username and do:
[FONT="Fixedsys"]
$ python easyubuntu.in
[/FONT]

It should *just work*.

---

### Post by bobmorris on 2006-09-04
That worked.

However when I do it now, clicked a few of the codec options, it says it'll install 40 packages, and then -

To Be Removed

Ubuntu desktop (say what?)

Why is that there, sounds dangerous?

So I'm not doing anything now... What should I do?

---

### Post by bobmorris on 2006-09-04
Ok, guess that wasn't a big deal. Did it with just one option, and it deinstalled Ubuntu desktop, yet all is fine. 

Saying "Removing Ubuntu desktop" seems guaranteed to spook newbs like me.

---

### Post by szf on 2006-09-04
I notice the same when I de-selected Evolution from another Ubuntu install. I got spooked too, and figured that leaving the xMB of Evolution binaries on the hard disk the was better than <some possibly painful> alternative.

It appears that that that's a package common to all default 'Applications' menu items. Good to know that there's no scary breakage.

---

