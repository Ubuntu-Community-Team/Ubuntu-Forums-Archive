---
title: "SyNAPTIC VS ADD/REMOVE"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-04-28
Which one should one use, Synaptic OR Add/Remove ?

Clean installation and removal of applications are essential for running any OS.

Can any one  give some sort of detailed information.

---

### Post by Nythain on 2007-04-28
for installing i would use synaptic... for removing, if you can find what you want to remove in add/remove i would probably recomend it... or finding the exact name in synaptic and using ,sudo apt-get remove --purge *package*, in a terminal

---

### Post by bapoumba on 2007-04-28
> **dptxp said:**
> Which one should one use, Synaptic OR Add/Remove ?

Clean installation and removal of applications are essential for running any OS.

Can any one  give some sort of detailed information.

They are basically front ends to apt-get. From Add/remove help menu:
> Only simple additions and removals can be performed with Install and Remove Applications. For more advanced needs, the Synaptic Package Manager is used.

Add/remove runs gnome-app-install.

---

### Post by Nythain on 2007-04-28
i love people who answer things better than i do :)

---

### Post by bapoumba on 2007-04-28
> **Nythain said:**
> i love people who answer things better than i do :)
Hey :)
I hope it's okay with you that I added some details to your answer ;)

---

### Post by tommcd on 2007-04-28
Synaptic offers you the option "mark for removal"  which just removes the app, or "mark for complete removal" which will remove the dependencies installed with the app as well. This is useful in some circumstances. The CLI comparisons are "apt-get remove" and "apt-get --purge remove". I always use synaptic.

---

### Post by dptxp on 2007-04-28
I thought that aptitude is preferred to apt-get.
Thanks to all but I think that a bit more elaborate advance explanation shall help the users.

---

### Post by Nythain on 2007-04-28
mmm... the major differencies between apt-get and aptitude were dependancy handling... and with the newer versions of ubuntu, its actually recomended apt-get remove now instead of aptitude, but you should always use the one to remove that you used to install... so if you aptitude installed, then aptitude remove... since synaptic uses i believe apt-get then you should probably stick with it for all your cli needs.

thanks for the clarification on the --purge, can never remember if it goes before or after the remove command.

also thanks for the info on synaptics different options of marking for removal... i usually stick with cli and aptitude so i know that when i remove something any un-needed and or automatically installed dependancies will be removed too

---

### Post by Vixis on 2007-04-28
> **tommcd said:**
> Synaptic offers you the option "mark for removal"  which just removes the app, or "mark for complete removal" which will remove the dependencies installed with the app as well. This is useful in some circumstances. The CLI comparisons are "apt-get remove" and "apt-get --purge remove". I always use synaptic.

"mark for complete removal" will also remove config files in your home folder. It completly removes all traces of this package.

---

### Post by dptxp on 2007-04-28
> **tommcd said:**
> Synaptic offers you the option "mark for removal"  which just removes the app, or "mark for complete removal" which will remove the dependencies installed with the app as well. This is useful in some circumstances. The CLI comparisons are "apt-get remove" and "apt-get --purge remove". I always use synaptic.

Thanks.

Does the later remove (purge) the shared files or check if the files are used by other programs ?

Does any of the add methods duplicate any common files ?

Do the add methods replace older files with latest ones if available ?

Can I add with one and remove with other ?

I thought that latest trend is to use aptitude in place of apt-get in terminal. Then why do these utilities use apt-get and not aptitude ?

---

### Post by Najand on 2007-04-28
Using Synaptic is handy because you can look all packages, still add/remove blahblah is easier to use becuase you can see only neccessory applications.... 
Anyway, APT is much better than APTITUDE.... sometimes APTITUDE install/remove some other unrelated packages....

---

### Post by bapoumba on 2007-04-28
[http://psychocats.net/ubuntu/aptitude]("http://psychocats.net/ubuntu/aptitude")

---

### Post by hyperair on 2007-04-28
Don't forget that now apt-get has the autoremove command which removes all the automatically installed dependencies that are not needed anymore ^^

---

### Post by Najand on 2007-04-28
bapoumda:
A.Y. Siu's article belongs to the old days of dapper... Now we have autoremove with apt-get which is quite exact when deleting the orphanage packages.

---

### Post by bapoumba on 2007-04-28
> **Najand said:**
> bapoumda:
A.Y. Siu's article belongs to the old days of dapper... Now we have autoremove with apt-get which is quite exact when deleting the orphanage packages.

[QUOTE=psychocats aptitude page]aptitude versus apt-get

Important Update
Apparently the new version of apt-get in Edgy Eft (Ubuntu 6.10) has a function that allows you to remove unused dependencies when removing an application:
sudo apt-get autoremove applicationname

So the points outlined on this page about using aptitude over apt-get are largely irrelevant if you're using Edgy Eft (6.10), Feisty Fawn (7.04), or any future version of Ubuntu. [/QUOTE]

;)

edit: I linked to the page, as aysiu had already stated that, and for the ones who wanted some history :)

---

### Post by Najand on 2007-04-28
Ok, Thanks....

---

### Post by bapoumba on 2007-04-28
> **Najand said:**
> Ok, Thanks....
Welcome.
Cheers

---

