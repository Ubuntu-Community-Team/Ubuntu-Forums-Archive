---
title: "frustrated ubuntu noobie"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by phenix on 2006-03-24
I have ubuntu running on my G3 power book 500mhz, and have been unable to do pretty much anything with it. My main concerns are getting applications, and getting my hardware to work in sync with Ubuntu, and right now am not being able to do either...When starting synaptic im getting the following message every single time:

"W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-powerpc_Packages) - stat (2 No such file or directory)" 
Every single time I try to udated the repositories this message appear, meaning I cannot add any new applications,  and I dont know what to do.

On the hardware side of things, I have a Plextor 504UF USB CD/DVD writer and even though it shows when I go to 'my computer' I havent been able to figure out how to mount it...Heck, I dont even know where to 
start when it comes to looking for mount point and all of that good stuff.

ANyway, I would really like to give Ubuntu a try, but right now everything seems so hard...
thank you for reading my lil book here, the help would be appreciated!!!!!

---

### Post by petri on 2006-03-24
Take a look at [http://www.linuxnewbieguide.org](http://www.linuxnewbieguide.org) It might not give you a direct answers but it will get you going.

---

### Post by christhemonkey on 2006-03-24
Doesnt ubuntu auto mount devices? For isntance when i put a CD in or a usb stick, they all mount fine.  Have you tried inserting a CD and seeing if you can browse it from the my computer dialog? 
Sorry to point out the obvious!

---

### Post by Ubuntuud on 2006-03-24
[QUOTE=phenix]
"W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-powerpc_Packages) - stat (2 No such file or directory)" 
Every single time I try to udated the repositories this message appear, meaning I cannot add any new applications,  and I dont know what to do.[/QUOTE]

I had the same problem a while ago.
You should update your repo's. To do this start up synaptic, preferences (translated, in Dutch it is "instellingen") > packagesources. This will start up a window containing a list of names, delete them all. Then click on "add" and slect all the options. Do this for all three possibilities two times ("breezy badger", security updates, updates). Then select one and click the bottom one of the three option ("add", "delete", [COLOR="Red"]""bewerken""[/COLOR]). 
This will bring up another window, change binary to source. Do this with all three ("breezy badger", security updates, updates). Then close the windows and the error should stop appearing.

Hope this helps.

---

### Post by phenix on 2006-03-24
thanks for the help..
yes, the device appears on my computer, and Im able to browse the cds I put in my external drive, but it wont show on any of my cd burning tools as an option to burn with or read from.... 
thats why I was wandering if there is anything I can do to my fstab file to allow other cd/dvd writing tools to show the device as an option..

---

### Post by phenix on 2006-03-24
thanks Ubuntuud, that helped, although I need to find  a way of getting more options on packages to install....

---

