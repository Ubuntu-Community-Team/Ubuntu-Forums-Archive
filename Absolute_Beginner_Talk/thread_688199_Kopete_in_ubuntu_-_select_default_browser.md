---
title: "Kopete in ubuntu - select default browser"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by mesh_ok on 2008-02-05
Dear All,

I use Kopete instead of Pidgin in my Ubuntu 7.10, and when clicking URLs in Kopete they open in Konqueror. How can this be changed to firefox or another browser?

---

### Post by p_quarles on 2008-02-05
If there's another way, I don't know it, but this will work:
1) Install the package "kcontrol" from the package manager.
2) Run this program (if it doesn't show up in the menu, use alt-F2 and type "kcontrol").
3) Select "KDE Components", then "Component Chooser", and finally "web browser." You can then change the default KDE browser, and Kopete will respect this.

---

### Post by Trail on 2008-02-05
As far as I understand you use Gnome.

The only way I know is to actually edit KDE's preferences... Since I assume you lack the needed packages, execute the following command in a console:

sudo apt-get install kde-systemsettings

Then, execute

systemsettings

And the KDE's control center should pop up. Navigate to Default Applications, Web Browser, and select Firefox.

I cannot test this at the moment, but I believe it should work. Give it a go :)

---

### Post by mesh_ok on 2008-02-05
Thanks guys! Will try it afterwork

---

### Post by p_quarles on 2008-02-05
No problem. Just so you know, too, either of the above methods will work equally well. KDE happens to have two different control panels -- they each have their advantages and disadvantages, but they are equally suited to this task.

---

### Post by nonexl on 2008-02-10
Go to** Synaptic**
Install **kcontrol**
open terminal
type in **kcontrol** (*no sudo required*)
kde components
file associations
search for **html** (and/or php)
In the **Application Preferences Order** *Move Up* or *Add*    **firefox** (or any other browser you want)
Test if it works
Then go back to **Synaptic** and remove **kcontrol** (along with **kdebase-data** & **kicker**)
*_! More important show you're finger to all those KDE users who give us a hard time figuring this out !_*

Happy Kopete messaging on GNOME

---

### Post by Alp82 on 2008-02-22
Or just do this, it's the most simple solution in my opinion:
[http://ubuntuforums.org/showpost.php?p=2624875&postcount=2](http://ubuntuforums.org/showpost.php?p=2624875&postcount=2)

If the line doesnt exist, create it.

---

### Post by 5oak on 2008-02-22
> **Alp82 said:**
> Or just do this, it's the most simple solution in my opinion:
[http://ubuntuforums.org/showpost.php?p=2624875&postcount=2](http://ubuntuforums.org/showpost.php?p=2624875&postcount=2)

If the line doesnt exist, create it.


Awesome! Seems like KDE is banning all other browser (or non-KDE apps for that matter), or is it just me?:confused:

---

### Post by p_quarles on 2008-02-22
> **5oak said:**
> Awesome! Seems like KDE is banning all other browser (or non-KDE apps for that matter), or is it just me?:confused:
That seems like a strange conclusion to draw from a discussion which has so far given you three ways of setting any web browser as the default in KDE.

---

