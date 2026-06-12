---
title: "Upgrading from Hoary to Breezy?"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by thekore on 2005-05-28
I will firstly apologise if this has been asked, i had a search around the wiki and the forums but cant see anything that answers my question.

I am currently using Hoary release as my primary and only operating system and have done since Warty. Before moving to ubuntu all other systems were easily upgradable between releases for example suse 8 to suse 9, mandrake 8 to 9 to 10.

However unless i missed something during the upgrade from Warty to Hoary there was no upgrade option? Will this be available when breezy is finalised? 

If there is an option for upgrading already that i have missed can someone explain to me the process of it and its reliability? I really dont want to have to burn all my data onto numerous dvd-r's during an upgrade. 

Thanks in advance for any support.  :-)

---

### Post by Mez on 2005-05-28
There was a process for upgrading from warty to hoary, and is a process of upgrading to breezy (but I HIGHLY recommend you DO NOT UPGRADE TO BREEZY at the moment)

this was, simple, changing all references in your /etc/apt/sources.list from "warty" to"hoary"

There were a couple of other steps involved, but, seeing as you're not upgrading at the moment, I dont need to list htem, but, thats the main part of it.The rest of it wasjust "pinning" packages so you can downgrade again, and just reinstalling a couple of things to make sure yo had a full set of dependencies.

---

### Post by Xian on 2005-05-28
[QUOTE=thekore]However unless i missed something during the upgrade from Warty to Hoary there was no upgrade option? Will this be available when breezy is finalised?[/QUOTE]
The upgrade option is primarily via apt: [Warty to Hoary](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes/view?searchterm=upgrade%20hoary).
The same process is/will be available for Breezy.

---

### Post by thekore on 2005-05-28
thanks Mez and Xian. I was unaware that there would be / was no "cd upgrade" in that case, how successful is the apt upgrade?

---

### Post by Xian on 2005-05-28
[QUOTE=thekore] I was unaware that there would be / was no "cd upgrade" in that case, how successful is the apt upgrade?[/QUOTE]
Works like a charm for most. :)

---

### Post by poofyhairguy on 2005-05-28
[QUOTE=thekore]thanks Mez and Xian. I was unaware that there would be / was no "cd upgrade" in that case, how successful is the apt upgrade?[/QUOTE]

Better than any other OS upgrade method I have ever seen.

---

### Post by thekore on 2005-05-28
thats good to know then, the only similar system i have used is the FreeBSD cvs update. So if its as reputable as that  \\:D/

---

### Post by KiwiNZ on 2005-05-28
imho that the upgrade path in Linux is horrible ( not that much better in Windows either)
Clean install is the only way to go.

Also if you don't intend to doserious testing and bug reports etc I would keep away from Breezy on any production units. Its still just a babe in Diapers.

---

