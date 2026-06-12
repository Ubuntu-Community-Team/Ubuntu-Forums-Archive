---
title: "Problems with streaming video."
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by cambrose on 2007-07-08
Okay, I have come back to ubuntuland, and have been pleasantly surprised so far (omg my wifi works fine), but I am unable to stream the television shows off of [http://www.tv-links.co.uk](http://www.tv-links.co.uk), but whenever I try to, it just gives me a big red X on the screen...any suggestions as to how to fix it?

---

### Post by deadgobby on 2007-07-08
Did you install flash player 9? What vid are you trying to peep at?

---

### Post by tchoklat on 2007-07-08
you may need to install drivers that do not come with Ubuntu due to licensing issues. An easy way is to install automatix from [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) and use it to install the rstricted drivers. That should work I guess!

---

### Post by cambrose on 2007-07-08
Forgot all about automatix, as soon as I get it all installed I'll update you. I am trying to watch all of "dead like me" btw.

---

### Post by cambrose on 2007-07-08
Okay, I tried all that, and still no luck

---

### Post by jimbob on 2007-07-08
I found this via Google and it works great for me on tv-links.co.uk

Find the file ~/.mozilla/firefox/pluginreg.dat and edit it.

Look in the file for a line like this:
/usr/lib/mozilla/plugins/mplayerplug-in.so:$
to determine if the mplayerplug-in is installed. If not exit the file and install it.

Find the sections that have this line in it (could have more than one):
8:video/mp4:MPEG 4 Video:mp4:$

Add this line to the end of those sections
XX:video/divx:DIVX Video:divx:$

XX = next number is sequence.

Very Important: go to the beginning of the section and three is a number of entries in the section add 1 to that value. The value should be XX + 1;

Save the file. Restart Firefox.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by jimbob on 2007-07-08
The line with the happy face in the middle of it (thanks Ubuntu) should read *[COLOR="Blue"]divx(colon)DIVX[/COLOR]*

Replace the (colon) with an actual colon  (sorry)
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by deadgobby on 2007-07-08
> **cambrose said:**
> Forgot all about automatix, as soon as I get it all installed I'll update you. I am trying to watch all of "dead like me" btw.
 Dead Like Me rocks. Too bad they x out the show.

---

