---
title: "Config Errors"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by dazziec on 2006-12-20
I have just tried to install 'Automatix', when i tried just installing with package installer, it kept syaing that i can only have one package working at once? please close down the other packages...but i only had one running. So then i tried to install it with terminal and i keep getting the message ' **E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.'**

What does this mean and how can i solve it?:-?

---

### Post by useResa on 2006-12-20
The error indicates that in a terminal you will have to give the following command```
sudo dpkg --configure -a
```.

The sudo is required because it requires superuser priveleges.

---

### Post by dazziec on 2006-12-20
Thanks...i have put that in......should it do anything?:confused:

---

### Post by dazziec on 2006-12-20
Thanks very much for that......urm...could i ask another question?

PLease can some one tell me what this means:-

E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I have uninstalled and reinstalled but i still can't get rid of this error, until it is sorted it wont let me download any updates...

please help!!!!
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
dazziec
View Public Profile
Send a private message to dazziec
Send email to dazziec
Find all posts by dazziec
Add dazziec to Your Buddy List
Reply

---

### Post by jive_turkey on 2006-12-20
There is a free version of flash, I believe that you can get it direct from Adobe/Macromedia but I could be wrong. Do you get the message after you uninstall the the package?

---

### Post by useResa on 2006-12-20
A solution on how to remove it can be found in [this post](http://www.ubuntuforums.org/showpost.php?p=1684690&postcount=4)
It is done by```
 sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
```

After removal you can find installation instructions [here](http://www.ubuntuforums.org/showpost.php?p=1901759&postcount=5).

Hope this will help you.

**BTW:**I have found these answers by searching the forums for: *flashplugin-nonfree archive*.
A search is - at least this is my opinion - usually a good way to find solutions.
Most of the time errors have been encountered and answered before.

---

