---
title: "upgrade thunderbird"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Rita G. on 2007-06-01
anybody know how to upgrade thunderbird email client from 1.5 to 2.0?

---

### Post by jonward0690 on 2007-06-01
Well I know in automatix you can get Thunderbird 2 in there.

---

### Post by taurus on 2007-06-01
See if this gets you the latest version.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird)

---

### Post by Rita G. on 2007-06-01
what is automatix?

---

### Post by Rita G. on 2007-06-01
i also went to this link:

[http://pykeylogger.sourceforge.net/w..._Thun](http://pykeylogger.sourceforge.net/w..._Thun) derbird

followed instructions..............doesn't work.

does anyone actually USE thunderbird? why am i having such a hard time trying to get this to work?

---

### Post by Seisen on 2007-06-01
Which directions did you use?

---

### Post by Moop on 2007-06-02
> **Rita G. said:**
> i also went to this link:

[http://pykeylogger.sourceforge.net/w..._Thun](http://pykeylogger.sourceforge.net/w..._Thun) derbird

followed instructions..............doesn't work.

does anyone actually USE thunderbird? why am i having such a hard time trying to get this to work?


I use Thunderbird and I've used that script to upgrade. Just make sure when you download the script you change the file name "*save it as installnewthunderbird.sh*"

---

### Post by jonward0690 on 2007-06-02
> **Rita G. said:**
> what is automatix?

Automatix is a way to easily install comon aplications here is ther official site.                          [www.getautomatix.com](www.getautomatix.com)

---

### Post by randyrando on 2007-06-02
I just did this today.  Here are the steps I had to do.

1. downloaded thunderbird from the mozilla site using firefox ;)
2. Downloaded it to the desktop.
3. clicked on it and got some app to extract it for me.  I extracted it to:
/usr/local/thunderbird.
4. I then created a launch link to it (/usr/local/thunderbird/thunderbird) and poof, I was running 2.0.  

The hardest part was getting my prefs.js from windows to work.  But it looks like it did (feeling like a hacker tonight).

---

### Post by Rita G. on 2007-06-02
> **Moop said:**
> I use Thunderbird and I've used that script to upgrade. Just make sure when you download the script you change the file name "*save it as installnewthunderbird.sh*"

change it to what?

---

### Post by Rita G. on 2007-06-02
ok....so i got that part done (finally)........and i'm running 2.0.0.0

NOW......when i launch t-bird, an alert box pops out & says:

“Could not connect to server localhost; the connection was refused.”

---

### Post by Rita G. on 2007-06-02
i had to open the webmail extension and reset the pop and smtp settings and they are now both running; but now i get a new alert box when i launch t-bird 2.0:

“Sending of username did not succeed. Mail server localhost responded: hotmail.com is a unsupported domain” 

anybody know how to deal with it?

---

### Post by nanotube on 2007-06-26
make sure to upgrade your webmail and hotmail extensions to the latest versions...

---

### Post by alienexplorers on 2007-06-26
I like keeping my programs updated.  Usually such as in the case of Firefox & Thunderbird I just down load the tar file and load them in my home folder.  This way if I have a problem with one of the new programs I have the old ones to fall back on.

---

### Post by nanotube on 2007-06-26
> **alienexplorers said:**
> I like keeping my programs updated.  Usually such as in the case of Firefox & Thunderbird I just down load the tar file and load them in my home folder.  This way if I have a problem with one of the new programs I have the old ones to fall back on.

well, fyi, ubuntuzilla keeps the repositories versions right there, they are not uninstalled or anything. it installs the mozilla builds in parallel with the repos versions.

also, the most recent version of ubuntuzilla comes with an automatic update checker, so that you will be instantly apprised when a new release of mozilla software is made. 

so... check it out if you care to .:)

---

### Post by DerridaIsDead on 2007-07-13
Hello there,

concerning your error message.

> **Rita G. said:**
> i had to open the webmail extension and reset the pop and smtp settings and they are now both running; but now i get a new alert box when i launch t-bird 2.0:

“Sending of username did not succeed. Mail server localhost responded: hotmail.com is a unsupported domain” 

anybody know how to deal with it?

Receiving  the exact same message here.
Don't happen to have found a solution...
(I've changed the port numbers >1024)

---

### Post by DerridaIsDead on 2007-07-13
Ignore my previous post. Found out why i receive the message that the hotmail.com domain is unsupported. It's actually a user privilige thing. Seem to have installed thunderbird (or the webmail extension)  as root, and tried to run it as a regular user. 
Now I just have to find out what priviliges I should alter.

bye.

---

