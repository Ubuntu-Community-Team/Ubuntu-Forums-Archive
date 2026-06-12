---
title: "Synaptic and apt-get errors"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by JNasci7906 on 2006-05-23
hey all, 
as of late ive been getting this error message whenenever i start synaptic or try and run apt-get from the console

> W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

and im not sure exactly what that means?? any help would be helpful. Ive tried apt-get update and it said something about 404 file not found....

thanks nash

---

### Post by cnc333 on 2006-05-23
do you have general networking and internet access? i know its a stupid question, but it has to be asked.

---

### Post by aysiu on 2006-05-23
In Synaptic, go to Settings > Repositories, and uncheck the boxes next to those two repositories.

---

### Post by Phlosten on 2006-05-23
That basically means apt cannot find those two entries that are in your sources.list file.
Repositories that were there, but either don't exist anymore or something has changed at the repository and you need to update your sources.list to reflect this. 

They are not official Ubuntu repositories so they would have been put there to install some extra software from somewhere and something has changed since then.

---

### Post by Koech on 2006-05-23
You can edit your sources.list and put new entries in place of those, or use the default ones from the install CD.

---

### Post by catlett on 2006-05-23
Those are 2 servers that Automatix puts in your source list. It doesn't really matter if your connecting them since Automatix already got what it wanted from there and your not getting system updates from there.
Those sites always give errors because they are from Finland (I know koti is finnish now that I think of it, I'm not sure about theli) and a Finnish guy once posted in disbelief that Autiomatix used them because even people in Finland got bad service from them.
You can live with the error text that doesn't harm your system or you can have Synaptic ignore them. Or even more remove the link to them. Open up your source list```
 sudo gedit /etc/apt/sources.list
```
You can now do 1 of 2 things. Either erase the koti and theli entries or put a "#" in front of the line with the koti and theli url. A # in front of something will cause that line to be ignored. So just pu a # in front of the urls and they won't throw up any more errors. If you find you need it for some reason you can remove the # and have the server available again.
Either way will get rid of the error. Delete or # in front.

---

### Post by arnieboy on 2006-05-23
theli.free.fr is for listen media manager which isnt supported for breezy anymore. update to the latest version of automatix or just delete the repos from sources.list

---

### Post by JNasci7906 on 2006-05-23
ok thanks yall im gonna give a few of those a shot......and to cnc333 yes i have the access, however, my d-link wireless usb is more of a 'expletive' than i could have ever imagined.lol

thanks again

nash

---

### Post by JNasci7906 on 2006-05-23
hey thanks guys, all is fine now......hopefully someday after i get good with this linux stuff ill be able to help as you have helped!

---

### Post by catlett on 2006-05-23
This is a bit off topic but since your in the thread, is there a Daper Automatix yet? I am assuming there will be. 
I want to quickly say thanks . Automatix is what kept me in linux. Gave me the ability to have a system I could use even though I didn't know how to install anything.
Thanks and I hope an Automatix happens soon. I always give your link to people but lately I get "Thanks but I'm running Dapper"

---

