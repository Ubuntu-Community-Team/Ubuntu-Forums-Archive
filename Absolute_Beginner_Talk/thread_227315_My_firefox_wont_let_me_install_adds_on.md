---
title: "My firefox wont let me install adds on"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by cyclister on 2006-08-01
How do I turn this on?
Looking in my advance but cant change that setting

---

### Post by Ares Drake on 2006-08-01
like you i can't find a way to install the addons. However it is not even necessary. You can install them with synaptic packet manager: i.e. flashplugin-nonfree for flash and mozilla-acroread for pdf...

---

### Post by steve.horsley on 2006-08-01
All I do is to pull down the menu Tools->Extensions and then click Get More Extensions. The only reason I can imagine that this might not work is if you don't have rights to some of the firefox directories in your home. Have you ever run firefox under sudo? Have a look in .mozilla (in your home directory) and see if any files are owned by root. Or just do:
> sudo chown -R username .mozilla
replacing username with your user name of course.

Just a wild guess.

---

### Post by cyclister on 2006-08-01
This is ridicouls cant get in adds on even in sudo mode ](*,) 
I have sudo let firefox  bla bla bla, cookies for just that site.
Tried even to re install firefox that wont help a bit

Its left a note software installations is currently disabled?
How do I enable that?

In my advanced part I have some settings I cant reach, for some reason I cant understand.

And no every adds on you cant get from apt-get/synaptic that was a little disapointing.

---

### Post by deadgobby on 2006-08-01
> **cyclister said:**
> This is ridicouls cant get in adds on even in sudo mode ](*,) 
I have sudo let firefox  bla bla bla, cookies for just that site.
Tried even to re install firefox that wont help a bit

Its left a note software installations is currently disabled?
How do I enable that?

In my advanced part I have some settings I cant reach, for some reason I cant understand.

And no every adds on you cant get from apt-get/synaptic that was a little disapointing.
What add on are you trying to install? Like Mplayer, flash, and Jave? If all three. You may want to install Automatix. 
[http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix](http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix)
 This may help out your headache. Please read before installing Automatix.

---

### Post by cyclister on 2006-08-03
Its this one
[https://addons.mozilla.org/firefox/125/](https://addons.mozilla.org/firefox/125/)

---

### Post by Blur-king on 2006-08-03
Hi Was there a promt from firefox that "software installation is disabled". If there is then you have to enable it. Type **about:config** in the address bar. Then look for **xpinstall.enabled  **if the value is false, double-click it to change it to **true**   You can then restart firefox.

---

### Post by cyclister on 2006-08-03
Thx that did the trick :mrgreen:

---

