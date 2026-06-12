---
title: "wpa and airport (not extreme)  feisty ppc"
date: 2007-06-12
forum: Apple PPC Users
---

### Post by todayalemon on 2007-06-12
Hello, 

at the moment i'm trying to make my girlfriend's good old ibook g3 dual usb usable again by using ubntu. It turns out to work fine so far - except wpa-encrypted wireless connections. And there are already a lot of threads, questions and so on on the web about the same topic: 
[http://ubuntuforums.org/showthread.php?t=452838](http://ubuntuforums.org/showthread.php?t=452838)
[http://ubuntuforums.org/showthread.php?t=403585](http://ubuntuforums.org/showthread.php?t=403585)
[http://ubuntuforums.org/showthread.php?t=17009](http://ubuntuforums.org/showthread.php?t=17009)
(just some examples)
And they all seem to be dead now, so i'm asking again. Is there any progress or succesful compiling?
I don't want to reinstall OSX 10.3.9 but i will have to if it is not possible to get this working including wpa (with this "roaming mode enabled" for the wireless-tools-icon in the applet...) as she is going to travel a lot in the next months and will need to access several hotspots (to be able to talk to me via skype)...


thanks for your help!!

---

### Post by stmiller on 2007-06-12
No WPA with the original airport card. :( Sorry. I'm in the same boat.

---

### Post by todayalemon on 2007-06-12
and this is confirmed? isn't there any chance to get this working (i would even begin to learn the whole compiling thing...):(

---

### Post by stmiller on 2007-06-12
Install the program hwinfo [sudo apt-get install hwinfo]

And then type hwinfo in a terminal. Info about the card and driver can been seen there. 

You could try to perhaps find the orinoco sources and see if there are options to build with wpa.

If she is looking to talk via skype, you should perhaps stick to OS X. There is no skype for PowerPC Linux. :(

---

### Post by djhvt on 2007-07-11
ya i gave up trying to get wpa on my g3 ibook firewire, but i refused to back to mac os...sooo i went with the Yellow Dog distro on my ibook and ubuntu on my home pc. everything is happy now

---

