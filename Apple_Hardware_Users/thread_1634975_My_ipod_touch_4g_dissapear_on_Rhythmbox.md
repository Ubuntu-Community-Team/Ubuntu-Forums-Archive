---
title: "My ipod touch 4g dissapear on Rhythmbox"
date: 2010-12-01
forum: Apple Hardware Users
---

### Post by chanfle on 2010-12-01
Hello all,
I have a issue with my ipod touch 4g, when I connect on Ubuntu 10.10 the OS it detect perfectly (only see the photo folder)
but on Rhythmbox appear but disaapear quicly and I can't transfer my music on my ipod..
Any help for fix this issue?

Regards

---

### Post by Zookalicious on 2010-12-01
After opening Rhythmbox, unplug and reinsert your iPod.

---

### Post by chanfle on 2010-12-02
> **Zookalicious said:**
> After opening Rhythmbox, unplug and reinsert your iPod.

not working after unplug and reinsert, my ipod have iOS 4.2

any ideas?

---

### Post by arabis on 2010-12-04
You can install this PPA:

[https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/~pmcenery/+archive/ppa")

And update your system.

Also you need usbmuxd-1.0.6. But this PPA don't have this version yet. So you can use this one from Debian:

[http://packages.debian.org/experimental/usbmuxd]("http://packages.debian.org/experimental/usbmuxd")

It works for my ipod 4g

---

### Post by forestcomber on 2010-12-05
This works great !  Thank-you !

---

### Post by chanfle on 2010-12-08
Ok let me try and later I put my feedback

Regards

---

### Post by chanfle on 2010-12-08
Great it's working!!!!
Thanks a lot!!!
Regards

---

### Post by chanfle on 2010-12-09
> **chanfle said:**
> Great it's working!!!!
Thanks a lot!!!
Regards

Eyyy buddys
I have another issue, after implement the steps top mention i can sync my ipod (apparently) but i can't see on my device.
Any tips?

Regards

---

### Post by Zookalicious on 2010-12-09
I've never had much luck with getting rhythmbox to get songs on my iPhone. Clementine has been working magically for me. I've heard banshee is good too. I would try one of those out, rhythmbox would always transfer over the songs but my iPhone would only pick up about half of them. Clementine and Banshee should both work with the stuff you installed earlier in this thread. That's my two cents, somebody else might know how to make rhythmbox play nice.

---

### Post by chanfle on 2010-12-09
> **Zookalicious said:**
> I've never had much luck with getting rhythmbox to get songs on my iPhone. Clementine has been working magically for me. I've heard banshee is good too. I would try one of those out, rhythmbox would always transfer over the songs but my iPhone would only pick up about half of them. Clementine and Banshee should both work with the stuff you installed earlier in this thread. That's my two cents, somebody else might know how to make rhythmbox play nice.

In this moment I try to do with Banshee, but I can't see my songs

---

### Post by Zookalicious on 2010-12-09
In the preferences of banshee there should be an option to designate the location of your library. Just point it towards the folder with your music in it.

Also for what it's worth I've barely used banshee. Always been a bigger fan of Clementine but hopefully it handles transferring songs to your iPod better.

---

### Post by godplayer on 2011-01-01
Hello .. Thanks for the clementine tip off .. I have it installed and it shows the ipod touch in the side panel .. asks to "double click to open " ... But when I double click, it says "File Not Found: '(null)'  " .... Please give a solution if you can. 


 I have added that new ppa and upgraded my ifuse and libmobiledevice ... I am using a 3G ipod touch with iOS 4 ... Please anyone help ...

---

### Post by sevesteen on 2011-01-09
I've got the same situation--Rhythmbox used to work fine on my 2nd gen Touch, but not with my new 4th gen.  Installed the PPA, and now it appears that Rhythmbox can add and remove files, but the ipod database or something isn't updated--deleted songs still show on the iPod itself (but will no longer play) and newly added songs don't show on the iPod's display, but can be seen and played via Rhythmbox.   

Suggestions?

---

### Post by donmatas on 2011-01-18
> **sevesteen said:**
> I've got the same situation--Rhythmbox used to work fine on my 2nd gen Touch, but not with my new 4th gen.  Installed the PPA, and now it appears that Rhythmbox can add and remove files, but the ipod database or something isn't updated--deleted songs still show on the iPod itself (but will no longer play) and newly added songs don't show on the iPod's display, but can be seen and played via Rhythmbox.   

Suggestions?

same situation

thanks
DM

---

### Post by meerkatendriu on 2011-02-20
You can install this PPA:

[https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/%7Epmcenery/+archive/ppa")

And update your system.

Also you need usbmuxd-1.0.6. But this PPA don't have this version yet. So you can use this one from Debian:

[http://packages.debian.org/experimental/usbmuxd](http://packages.debian.org/experimental/usbmuxd)

I have succesfully installed the PPA and updated the system, but when I click on the second link (usbmuxd) the page I get to has the following error message : Package not available in this suite.
I downloaded usbmuxd-1.0.6 from [http://linux.softpedia.com/dyn-postdownload.php?p=56065&t=0&i=1](http://linux.softpedia.com/dyn-postdownload.php?p=56065&t=0&i=1), but the instructions contained in the readme file are incomprehensible. 

I'm also a proud (?) owner of an itouch 4, NOT jailbroken.

---

### Post by Zookalicious on 2011-02-20
> **meerkatendriu said:**
> You can install this PPA:

[https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/%7Epmcenery/+archive/ppa")

And update your system.

Also you need usbmuxd-1.0.6. But this PPA don't have this version yet. So you can use this one from Debian:

[http://packages.debian.org/experimental/usbmuxd](http://packages.debian.org/experimental/usbmuxd)

I have succesfully installed the PPA and updated the system, but when I click on the second link (usbmuxd) the page I get to has the following error message : Package not available in this suite.
I downloaded usbmuxd-1.0.6 from [http://linux.softpedia.com/dyn-postdownload.php?p=56065&t=0&i=1](http://linux.softpedia.com/dyn-postdownload.php?p=56065&t=0&i=1), but the instructions contained in the readme file are incomprehensible. 

I'm also a proud (?) owner of an itouch 4, NOT jailbroken.

That package is compiled for debian. It will not work on ubuntu in that format. 

Also as an aside why would you ever not jailbreak an apple device? It's completely legal and let's you free yourself from apple's insane policies and restrictions.

---

