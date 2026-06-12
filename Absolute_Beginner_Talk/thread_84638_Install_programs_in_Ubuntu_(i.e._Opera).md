---
title: "Install programs in Ubuntu (i.e. Opera)"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by svas on 2005-10-31
I have tried to install Opera 8.50 in Ubuntu, but with no luck. Have gotten some advice at X-Chat, and I have read in these forums. I have tried to dobble click the file, but then it only says:

> 
Could not open «opera_8.50-20050916.6-shared-qt_en_etch_i386.deb»

Type archive not supported.


I have tried with severan different versions of Opera too.

From advice at X-Chat I got to write "sudo dpkg -i opera_8.50.deb" (the new name I gave the file as the original filename was too long to write all the time) but still with no luck. Finally I wrote "sudo gedit /etc/apt/sources.list" in a normal terminal, and also in root (to try to add something from another tread here at Ubuntuforums.org about Opera 8.50), to that file. Still no luck.

Is there no easy way to get new programs installed on a Ubuntu (linux) system?

(Still a newbie.)

---

### Post by Kyral on 2005-10-31
This will be very helpful I feel. Feel free to ask any questions about it though :D

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications)

---

### Post by svas on 2005-10-31
I start Synaptic from System->Administration->Synaptic Package Manager and it asks for the password. I type the only password that I have (same for root and user ;) ) and then nothing happends. Is says in the link above that a Synaptic screen should pop up, but it doesn't. What do I do wrong?

---

### Post by Kyral on 2005-10-31
Uh......hmmm.....did you try the "Add Remove Programs" thing? (Its somewhere in the GNOME System Menu I believe)

I don't think you did anything wrong (unless you made a typo on the password)

---

### Post by svas on 2005-10-31
[QUOTE=Kyral]Uh......hmmm.....did you try the "Add Remove Programs" thing? (Its somewhere in the GNOME System Menu I believe)

I don't think you did anything wrong (unless you made a typo on the password)[/QUOTE]

No typo in the password. No windows pop up. Try to choose Update manager, nothing happens, try Programs->Add aplications nothing happens, try System->Admin->Add aplications nothing happens. No windows pops up. Internet, games and OpenOffice works fine.

I don't know.:confused: :confused: :confused:

---

### Post by Kyral on 2005-10-31
In that case, 1) Synaptic is buggered 2) It means you get to learn how to apt-get the old fashioned way :D

[https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo](https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo)

---

