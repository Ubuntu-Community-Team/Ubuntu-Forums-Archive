---
title: "firefox"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by leedsdevil on 2007-12-05
ACK ok i did my updates all good now i cant get monzila firefox up and working rite. how do u install the updates ? there is some sites out there that require this update or upgrade. i have the 7.10 ubuntu plz help

---

### Post by mikewhatever on 2007-12-05
What errors do you get when launching firefox? Try typing firefox in the terminal and then post the output.

---

### Post by zlegge08638 on 2007-12-05
Do you mean updating Mozilla Firefox?  If so, Firefox will tell you that and if it doesn't, you have to check for updates on your Ubuntu System.

---

### Post by leedsdevil on 2007-12-05
Intouch has detected that your Mozilla browser must be upgraded.
Browser Name: Mozilla
Major Version: 1
Minor Version: 0.8
Platform: UNIX

---

### Post by zlegge08638 on 2007-12-05
Upgrade Firefox in Terminal...  It should've gave you the steps when you typed in Firefox.

---

### Post by leedsdevil on 2007-12-05
could you or some one give me the steps

---

### Post by SOULRiDER on 2007-12-05
Type this
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Youre using Ubuntu right? Not Kubutnu or Xubuntu.

---

### Post by zlegge08638 on 2007-12-05
Sure go to "System" > "Administration" > and open "Update Manager".  Press "Check" in the update manager and an upgrade for Mozilla Firefox should be displayed.  Then install, everything then should be working.  If not, then something is wrong with Firefox and that is not "Beginners Talk" lol.

---

### Post by leedsdevil on 2007-12-05
ok i check both way guys and still no luck ACK you guys tried was there other commands that i should have used in the termal?

---

### Post by mikewhatever on 2007-12-05
> **leedsdevil said:**
> Intouch has detected that your Mozilla browser must be upgraded.
Browser Name: Mozilla
Major Version: 1
Minor Version: 0.8
Platform: UNIX

It seems that something called intouch tells you to upgrade your firefox to the version between 0.8 - 1.0. The problem is that these versions are long long gone. Firefox has been 1.5+ for about two years. Where do you get that message from?

---

### Post by leedsdevil on 2007-12-05
ok that is from a marykay site that my wife goes to she was able to get on there before i redid her pc im using ubuntu 7.10 and all updated and still cant understand why its doing this?

---

### Post by jryprt on 2007-12-05
Can he go to Synaptic Package Manager & uninstall & than reinstall Firefox ?

---

### Post by alienexplorers on 2007-12-05
Check your version of Firefox by going to Help>About Firefox.  It should be version 2.0.0.11 if it is current.  Mine just upgraded today to this version.

---

### Post by leedsdevil on 2007-12-05
yup thats the one i have...every thing is up to date

---

### Post by leedsdevil on 2007-12-05
ok small update i went on my windows pc(gaming rig only!) in firefox and i got it..? so why cant i get on it from here? its a login site if that mite help

---

### Post by mikewhatever on 2007-12-05
> **leedsdevil said:**
> ok small update i went on my windows pc(gaming rig only!) in firefox and i got it..? so why cant i get on it from here? its a login site if that mite help

Don't know. Can you provide a link for us to try?

---

### Post by leedsdevil on 2007-12-05
marykayintouch thats where she is tryin to go btw all Thanks for the help i know this can be apain...i use the google bar to get there

---

### Post by alienexplorers on 2007-12-05
The site you listed works fine on my system.  At least the login page.  Not being able to login makes total diagnosis impossible.

---

### Post by mikewhatever on 2007-12-05
Look at the part of the url in bold, it pretty much spells is out. [https://applications.marykayintouch.com/Login/main/](https://applications.marykayintouch.com/Login/main/)**RequireIE**.aspx

---

### Post by leedsdevil on 2007-12-05
now you see what i mean like i said i can do it from my pc with firefox and it did before i upgraded hard ware and to 7.10 ubuntu ... so can i strip the firefox and replace it? is there something in plug ins?
:guitar:

---

### Post by alienexplorers on 2007-12-05
There is a firefox extension that allows it to emulate windows.  Maybe you should check to see if someone has a name for this.

---

### Post by mikewhatever on 2007-12-06
> **leedsdevil said:**
> now you see what i mean like i said i can do it from my pc with firefox and it did before i upgraded hard ware and to 7.10 ubuntu ... so can i strip the firefox and replace it? is there something in plug ins?
:guitar:

In my case, it complained about Firefox 2.0.0.11 and Opera 9.24. You could try installing a different browser, no need to remove Firefox because of one stupid site though.

---

### Post by discoade on 2007-12-06
Not a good idea to remove firefox as there some other apps that use some of its files! at least thats what i was told via the site when i installed seamonkey!

---

### Post by perlluver on 2007-12-06
You can also try installing IEs4Linux.  Just type that in google and it will tell you how to install it.  No need to remove firefox though.  Let us know if this helps.

---

### Post by sgarrand on 2007-12-06
You can go to [Get Extensions]("http://en-us.add-ons.mozilla.com/en-US/firefox/2.0.0.11/extensions/") (which appears to be down at this time) and install "User Agent Switcher" to make that site think you're using IE/Windows.

Scott

---

