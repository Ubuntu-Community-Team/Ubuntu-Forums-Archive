---
title: "Pidgin can't connect"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by EYALf on 2007-12-09
The software it self is working but it does not connect to msn/google

it says "Connection error from Notification server:
Unable to connect"

what should i do?

---

### Post by Eldar11 on 2007-12-09
Did you make sure you have all of your connection settings right?
Is your computer connected to the internet?
Does you account work in a different location?
What computer are you using and what distro? (Gusty?, Fiesty?)

There is not enough information yet

---

### Post by EYALf on 2007-12-09
hi thanks for your resspond..
 im running Gusty on my computer and yes, my computer is connected to the internet...

have no idea what to do..
 I dont have anywhere else to run linux from, im pretty sure all of my settings are correct.

---

### Post by nikoPSK on 2007-12-09
possibly someone changed your pw? Try making an aim account or something and seeing if it logs on.

---

### Post by asathorny on 2007-12-10
Hi.
If you just want to use MSN messenger on your ubuntu Gutsy Gibbon machine the solution is really easy.
Open your chosen web browser 'Firefox' perhaps and google to web messenger and sign in as a web user to MSN messenger voila, problem solved and no need to install MSN on your computer, which of course you can't do in Linux.

Hope this solves your problem.

Asa
:):)

---

### Post by philinux on 2007-12-10
Try Kopete instead .

---

### Post by spiderbatdad on 2007-12-10
you could always install mercury messenger an msn client for linux supports video, too

---

### Post by lswest on 2007-12-10
well this may seem simple, but it may very well have happened;) make sure your password is right, and that the keyboard settings are correct, so that y=y and not y=z and vice versa.  Might be the problem.  Otherwise make sure you use port 1863 for MSN, or the http protocol (in case the 1863 port is blocked, Pidgin then uses the port 80).  don't know so much about google talk (unless you're using a google address in MSN, then make sure that it is enabled for MSN)

---

### Post by meborc on 2007-12-10
pidgin used to have a few nasty bugs concerning login... you could try the newest version of pidgin (2.3.1) or you could switch to [emesene]("http://www.emesene.org") ... it has been a lifesaver to me :) pidgin is sometimes too unreliable

(be warned, the emesene site is a bit slow due to high traffic)

---

### Post by EYALf on 2007-12-10
it works!
the MSN profile works. I just had to check the "Use http method" box.

though the gmail account still isn't working.

im sure the pw is correct, i use it every day on the same computer.

wait a minute, if i have a gmail mail, does that mean i can log into google talk? that was my assumption ...

any how, these are my settings:
protocol: XMPP
screen name : this is my user name right?
domain: gmail.com
resource: home
pw:
local alias: here i put my user name also...

in the advanced section:
connect port :5222
connect server: talk.google.com

proxy type: use GNOME proxy settings

i thank you all...

---

