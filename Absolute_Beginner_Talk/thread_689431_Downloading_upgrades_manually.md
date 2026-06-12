---
title: "Downloading upgrades manually"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by mormor on 2008-02-06
I have a problem with updating my ubuntu. I cant get the internet working, not via wlan or hdspa modem.
Is there a way to upgrade manually? 

Like downloading the packages in windows and then installing them in ubuntu afterwards?

(I am very new so please reply in a very pedagogic languge.)

---

### Post by jan quark on 2008-02-06
well you can browse through the packages 
here

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and through the debian packages 
here

[http://debian.mirror.inra.fr/debian/](http://debian.mirror.inra.fr/debian/)

but I dont know if this will help you to install the needed packages easily I hope so

---

### Post by Keith Hedger on 2008-02-06
In synaptic go to File->Generate packeage download script then save the script and run it from a terminal

---

### Post by emarkd on 2008-02-06
1.  Open Synaptic Package Manager (System > Administration)

2.  Search for what you need, right-click and mark for installation.  Don't click apply!

3.  Click File > Generate Package Download Script and save the file somewhere.

4.  Open the script in your favorite Text Editor and you'll find a nice list of packages, complete with URL's

---

### Post by mikewhatever on 2008-02-06
> **mormor said:**
> I have a problem with updating my ubuntu. I cant get the internet working, not via wlan or hdspa modem.
Is there a way to upgrade manually? 

Like downloading the packages in windows and then installing them in ubuntu afterwards?

(I am very new so please reply in a very pedagogic languge.)

Not quite sure what you want to do here. When you speak of updates, do you mean security ones? If so, then you are not in any danger, since you can't connect to internet. When you say you want to upgrade manually, do you mean upgrading to a newer version? What do you want to upgrade? You operating system? You Open Office? Each one can be done, but the ways are different.

You can install more software, codecs and such, using [nonetdebs site]("http://nonetdebs.homeip.net/?").

---

### Post by mormor on 2008-02-06
I want to upgrade the OS as I think some fixes (like the sound) will be possible then.



[I]pile ALSA, it places a module in one place while Ubuntu has that same module, but a different version, in a different place causing a bunch of conflicts and in the end, no sound.

So in order to fix this all you need to do is open the Software Properties, go to the Updates tab, and enable the Gutsy Backports.

backports.png
(click for a larger view)

Then just run this command

sudo apt-get install linux-backports-modules-generic[/I]

I dont know if it helps clarify...

---

