---
title: "Where's Everything?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-10-29
Hey guys. I just installed Gusty on my machine, and to be honest, I am pretty disappointed. The reason being that I cannot find Apache and other packages. Why is this? How can I install them? Thanks.

---

### Post by Flying caveman on 2007-10-29
What do you mean? its in the Synaptic Package Manger isn't it?

---

### Post by Crafty Kisses on 2007-10-29
> **Flying caveman said:**
> What do you mean? its in the Synaptic Package Manger isn't it?

Yeah, they should be.

---

### Post by w4ett on 2007-10-29
Apache is located in the Synaptic Package Manager.

---

### Post by Crafty Kisses on 2007-10-29
> **w4ett said:**
> Apache is located in the Synaptic Package Manager.

There ya go, I was waiting for that. Thanks. :)

---

### Post by drndrw on 2007-10-29
Not in mine. IN fact, there are only like 10 packages that aren't installed among those, there is no Apache or anything else I need :(. Also, where can  get msttcorefonts? I've attached a shot of my package manager. Also, I've tried apt-get install and the package is not found. My package manager screen shot attached (sorry for the white thing in the middle. I think that was the screen shot box).

---

### Post by FuturePilot on 2007-10-29
System>Administration>Software Sources. Make sure you have all repos enabled.

---

### Post by Maestro23 on 2007-10-29
Few links for the OP to read:

Installing Software: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Synaptic: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by sneezymelon on 2007-10-29
> **drndrw said:**
> Not in mine. IN fact, there are only like 10 packages that aren't installed among those, there is no Apache or anything else I need :(. Also, where can  get msttcorefonts? I've attached a shot of my package manager. Also, I've tried apt-get install and the package is not found. My package manager screen shot attached (sorry for the white thing in the middle. I think that was the screen shot box).

have you tried reloading your package list?

---

### Post by drndrw on 2007-10-29
Okay, well I changed my resporites and not it works. But still, there are three packages I want but are not listed. I want msttcorefonts, phpmyadmin, and ddclient. I cannot get any of these. Why is this?

---

### Post by Maestro23 on 2007-10-29
> **drndrw said:**
> Okay, well I changed my resporites and not it works. But still, there are three packages I want but are not listed. I want msttcorefonts, phpmyadmin, and ddclient. I cannot get any of these. Why is this?

Should be there.

I just searched in Synaptic and found everyone of those.  Make sure your Universe and Multivese repos are enabled.  If you have trouble, the link about Synaptic I posted earlier will help.

---

### Post by stoodleysnow on 2007-10-29
> **drndrw said:**
> Okay, well I changed my resporites 
o_0

resporites?!

repositories

---

### Post by drndrw on 2007-10-29
Oops. Sorry for my poor spelling :P. But where do I go to change it to universe?

---

### Post by Maestro23 on 2007-10-29
> **drndrw said:**
> Oops. Sorry for my poor spelling :P. But where do I go to change it to universe?

Did you not even look at the Synatpic link I provided?

Goto: System>>Admin>>Software Sources

See Screenshot below.

---

### Post by Madpilot on 2007-10-29
ddclient - in Universe. 

phpmyadmin - ditto.

msttcorefonts - in Multiverse.

First, close Synaptic. Then go System->Admin->Software Sources, make sure the first four lines are checked off. Then hit Close, and you'll get new sources downloaded. Reopen Synaptic, and (just for good measure) hit the Reload button on the top-left toolbar.

Search again for those three packages, and you should find them.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/) is useful for finding stuff, if you're not sure you've got all sources enabled. Don't download from packages.ubuntu.com, though - use Synaptic after you sort out your sources.

---

### Post by drndrw on 2007-10-29
> **Maestro23 said:**
> Did you not even look at the Synatpic link I provided?

Goto: System>>Admin>>Software Sources

See Screenshot below.

Sorry, I did look. Just not very carefully That fixed my problem. Thanks :)!.

---

### Post by steve.horsley on 2007-10-29
1) Go System->Administration->synaptic Package Manager
2) go Settings->Preferences and make sure the first 4 (main, universe, restricted, multiverse) are enabled.
3) While you're there, un-check the CD (do it doesn't keep asking for it)
4) Close the preferences and click Reload.
After re-reading all the repo inventory database, you should have thousahds of packages to choose from.

Edit:
Dang. Too slow typing again.

---

