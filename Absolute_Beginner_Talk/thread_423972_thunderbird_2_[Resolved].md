---
title: "thunderbird 2 [Resolved]"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by MrGreen on 2007-04-26
Hi,

Wondered if thunderbird 2 can be loaded under ubuntu?

TIA

MrG

---

### Post by igknighted on 2007-04-26
Of course :).  I Just got the file from the mozilla site in tar.gz form, extracted it and moved it into /opt.  Then launch it with the command /opt/thunderbird/thunderbird.  You can change the menu entry in your applications menu by right clicking -> edit menus then changing to the new command in the thunderbird entry.  Or you could create a new one for Tbird2 if you want to have the option to use either.

It's really easy, but if you want a script to automate it more there is one floating around somewhere (try the wiki maybe?)

---

### Post by earobinson on 2007-04-26
[http://ubuntuforums.org/showthread.php?t=413908](http://ubuntuforums.org/showthread.php?t=413908)

---

### Post by aysiu on 2007-04-26
This script will help:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird)

---

### Post by MrGreen on 2007-04-26
Wow thanks that was a breeze ... did search for thunderbird 2 but got nothing found ;-S

---

### Post by nhandler on 2007-04-26
Also, once you install thunderbird2, remember to uninstall the original thunderbird (unless of course you want to keep it). you can remove it with sudo apt-get remove mozilla-thunderbird

---

### Post by MrGreen on 2007-04-26
Thanks again... just wish I could restore my address book and emails from old distro install

---

### Post by Efros on 2007-04-26
Got this image of the little yellow Thunderbird 4 being loaded into the big green Thunderbird 2, 

[IMG]http://www.gasolinealleyantiques.com/diecast/images/matchbox/dinky-thunderbirdtwo.JPG[/IMG]

4

[IMG]http://www.ludd.luth.se/~kavli/Thunderbirds/Thunderbird-4.jpg[/IMG]

Ah FAB Parker...

---

### Post by autocrosser on 2007-04-26
AHHHH--those were the days!!!!:popcorn:

---

### Post by MrGreen on 2007-04-26
Thunderbird three was my fav.. . rofl man those eye brows ;-)

---

### Post by earobinson on 2007-04-27
> **MrGreen said:**
> Thanks again... just wish I could restore my address book and emails from old distro install
you should be able to if you backed them up.

---

### Post by MrGreen on 2007-04-27
I tried to just move them into .mozilla-thunderbird but it did not come up

Have backed up .thunderbird, email is working address book needs sorting but I lost my mails ;-(

That said I am very happy with Ubuntu install got some little things to sort out, but not a problem

---

### Post by earobinson on 2007-04-27
Weird, guess I should take that into account when I upgrade ... thanks.

---

### Post by Efros on 2007-04-28
[IMG]http://www.bbc.co.uk/cult/anderson/thunderbirds/images/p2_parker.jpg[/IMG]


Dennis Healey modelled himself on Parker.

---

### Post by nanotube on 2007-04-29
> **MrGreen said:**
> I tried to just move them into .mozilla-thunderbird but it did not come up

Have backed up .thunderbird, email is working address book needs sorting but I lost my mails ;-(

That said I am very happy with Ubuntu install got some little things to sort out, but not a problem

if you have a 'fresh' install, then your tb2 profile will be stored in .thunderbird, not in .mozilla-thunderbird. maybe that's why your stuff doesn't show up. so move your stuff to .thunderbird, not to .mozilla-thunderbird.

---

### Post by eternalsword on 2007-04-29
> **MrGreen said:**
> I tried to just move them into .mozilla-thunderbird but it did not come up

Have backed up .thunderbird, email is working address book needs sorting but I lost my mails ;-(

That said I am very happy with Ubuntu install got some little things to sort out, but not a problem

what you need to do exactly the following from the terminal:

cp -r ~/.mozilla-thunderbird/`ls ~/.mozilla-thunderbird | grep default`/* ~/.thunderbird/`ls ~/.thunderbird | grep default`/

---

