---
title: "MX900 goes to sleep and stays asleep!!"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by edifuzzy on 2006-05-05
I have an MX900 bluetooth mouse...it was a total pain to get working but it does work now....The problem that I have is that during watching movies etc the mouse goes into some sort of power saving mode.

Under windows it re-awakens when moved but under linux I have to open the terminal and type " sudo hidd --server --search".. I then have to push the connect button on the bottom of the mouse for it to connect and all is fine after that..

I wish I could avoid having to do this....Does anybody know of any programs/methods that I can use (short of sitting moving it around during a movie)

Thanks in advance for any help

EDI.

P.s incase you haven't noticed...I am a bit of an Ubuntu Noob but I am persevering against all odds!

---

### Post by edifuzzy on 2006-05-09
No replies in 3 days......this must be a hard one....

I haven't even had anyone telling me to look harder or use the search engine!!

Nobody have any ideas?

---

### Post by tdshiv on 2006-05-28
I have the same problem. If i leave linux up and then come back, i have to put in teh command line in order for the mouse to work again.

---

### Post by Stormbringer on 2006-06-07
Hmm ... isn't that hard to solve ... it rather seems no one uses this one ...

Here's how I got my trustworthy MX900 BlueTooth working in Ubuntu 6.06 ...

- While in Gnome press ALT+F2 to trigger the "Run Application" dialog.
- Type: gksudo gedit /etc/default/bluez-utils

Change the following lines:

HIDD_ENABLED="1"
HIDD_OPTIONS="--server"

- Save the file.
- Close gedit.

- Open a terminal and type: sudo /etc/init.d/bluez-utils restart

That should do the magic.

Whenever the mouse goes into suspend mode (i.e. you don't move the mouse within 10 minutes or put it into the craddle) it will reconnect automatically. This may take a few seconds - just be patient.

Upon boot (on GDM's login screen) you also need to have patience for a few seconds --- just move the mouse and wait for the connection to be made.

I hope this will help you.

Regards,
Storm.

[EDIT] --- Fixed typo as reported by smallphox below.

---

### Post by smallphox on 2006-06-08
Thanks for the help, stormbringer, this problem has been pissing me off for days, and I finally decided to do something about it.

Your solution works perfectly, except for the fact that you misspelled this line:

gksudo gedit /etc/defaults/bluez-utils (wrong)

it should be: 

gksudo gedit /etc/default/bluez-utils (right)

, there's no S in "default" =)

Thanks again! =D

Cheers,
smallphox

---

### Post by Stormbringer on 2006-06-08
I'm really sorry about the typo - but I'm glad I could help about.

Cheers,
Storm.

---

