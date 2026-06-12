---
title: "Problem Updating to 7.10"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Robotchicken1886 on 2007-10-18
So i am having a problem updating to 7.10   when i go to do the auto upgrade (you know in the update manager)  everything goes great until this pops up

CAN NOT DOWNLOAD ALL REPOSITORY INDEXES 
[http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl'



keep in mind i am new at linux

---

### Post by 2beers on 2007-10-18
I guess you just have to wait a little longer...
In german forum's there is talk about "afternoon"... but i guess servers will be a little crowded then...

---

### Post by bodhi.zazen on 2007-10-18
Please remind people to use a torrent to download if at all possible to reduce the load on the servers.

---

### Post by misfitpierce on 2007-10-18
sudo apt-get remove wine or remove the wine repos from sources under system admin. Youll need wine repos for gutsy anyways not for feisty. I would just wait and download disc upon release or when made avail for update which should be when final comes out. Hopefully within the next few hours.

---

### Post by Robotchicken1886 on 2007-10-20
Hey still having problems.   same as above.    i don't think this is a connection issue but a software issue.    note i no longer have wine installed yet it still says it is having problems with it (see above)

---

### Post by Strfie89 on 2007-10-20
> note i no longer have wine installed yet it still says it is having problems with it.

Same goes for me.

---

### Post by Maestro23 on 2007-10-20
> **Robotchicken1886 said:**
> Hey still having problems.   same as above.    i don't think this is a connection issue but a software issue.    note i no longer have wine installed yet it still says it is having problems with it (see above)

Any references in your **sources.list** file?

> cat /etc/apt/sources.lst

Check for any wine repos in there and get rid of them. Use an editor such as** gedit** to edit the file.

> gksudo gedit /etc/apt/sources.list

---

### Post by Strfie89 on 2007-10-20
> **Maestro23 said:**
> Any references in your **sources.list** file?



Check for any wine repos in there and get rid of them. Use an editor such as** gedit** to edit the file.

Complete noob. Please explain: how I would check/ do any of this? :???:

---

### Post by Maestro23 on 2007-10-20
> **Strfie89 said:**
> Complete noob. Please explain: how I would check/ do any of this? :???:

I gave you the terminal commands in my previous post.  "gedit" is the text editor you will use to open the file and make any chages.

---

### Post by Strfie89 on 2007-10-20
Ah. Didn't realize right away that those were terminal commands. Removed one line:

> deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

and am currently retrying the upgrade. 

Fingers are crossed. :)

**EDIT**: So far, so good. Halfway through Step 3 (Fetching the Upgrades).

---

### Post by Strfie89 on 2007-10-21
That solved it! Upgrade has been a success! Thanks for the help! :)

---

