---
title: "mozilla-firefox - New Version 1.0.7-0ubuntu0.1 update"
date: 2005-09-25
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-09-25
Greetings,

Been underway for a few weeks,  came home to see that Ubuntu had about seven updates (thats what happens when some jerk cuts your cable modem line outside the house by accident), anyway, upon doing the update, there is in the Available Updates the following:

mozilla-firefox - lightweight web browser based on Mozilla
New Version 1.0.7-0ubuntu0.1

using Software Upate from tool bar, I get the normal window that says "isntallating updates", but then I get an error that says:

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox

I've renamed the mozilla-firefox_1.0.7-0unbunto0.1_i386.deb file to old and changed the 00classic filename around but either way on both my pc and laptop, I get that error.

Any thoughts?  I'm thinking about removing Firefox and then installing again, maybe that would clear it up... :)

Any thoughts?

---

### Post by Gustav on 2005-09-25
[QUOTE=garnertr]Greetings,

Been underway for a few weeks,  came home to see that Ubuntu had about seven updates (thats what happens when some jerk cuts your cable modem line outside the house by accident), anyway, upon doing the update, there is in the Available Updates the following:

mozilla-firefox - lightweight web browser based on Mozilla
New Version 1.0.7-0ubuntu0.1

using Software Upate from tool bar, I get the normal window that says "isntallating updates", but then I get an error that says:

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox

I've renamed the mozilla-firefox_1.0.7-0unbunto0.1_i386.deb file to old and changed the 00classic filename around but either way on both my pc and laptop, I get that error.

Any thoughts?  I'm thinking about removing Firefox and then installing again, maybe that would clear it up... :)

Any thoughts?[/QUOTE]
 You're one the right track.

I had the same problem and removing and installing again fixed it.

---

### Post by timczer on 2005-09-25
This method posted in another  thread by seaeric worked for me:

sudo apt-get update
sudo dpkg -r --force-all firefox
sudo dpkg -r --force-all firefox-gnome-support
sudo apt-get upgrade
and, if asked
sudo apt-get -f install

---

### Post by tray02 on 2005-09-25
yeah.....I have to same problem.....the only way I could post now (since my firefox is out of commission) is through installing mozilla...so what way is the best way to fix the problem so that future problems don't occur?

---

### Post by traherom on 2005-09-25
I had the same problem... I eventually discovered (by running firefox from the command line with a flag which forces it to consider all errors fatal) that my profile was somehow in use (and it wasn't giving me the normal dialog). A reboot fixed it.

A logout/restarting the right processes may work, but I was lazy. :)

---

