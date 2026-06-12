---
title: "cedega install problem"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-09-14
I'm trying to install the cedega time demo.  The mirror cite at softmedia installed it automatically on my desk top.  Whe I double click on it is gives this message:

Could not open the file /home/jim/Desktop/cedega_timedemo_installer using the Western (ISO-8859-15) character coding.

Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again.

character coding current local utf 8.  I tried the western also and it gave the same message.

---

### Post by BionicBigfoot on 2006-12-12
You don't double click. You need to open it with

 sh /[COLOR="Red"]PATH_TO_INSTALLER[/COLOR]/cedega_timedemo_installer

you may need to download a GTK Library thru synaptics

---

### Post by BionicBigfoot on 2006-12-12
PS: You do the above in the Terminal Window

---

### Post by wog on 2006-12-12
Does cedega fight with wine?

---

### Post by neemz on 2006-12-12
cedega and wine co-exist nicely

---

### Post by wog on 2006-12-12
What do I do when trying to install into cedega? When I just double-click on the installer, it automagically uses wine.

---

### Post by neemz on 2006-12-12
To install a game into cedega do it from inside the cedega program.

From a console type this
cedega

In the nice window that pops up I beleive there are options for specifying the location of an installer.

---

### Post by Tellisk on 2006-12-19
> **BionicBigfoot said:**
> You don't double click. You need to open it with

 sh /[COLOR="Red"]PATH_TO_INSTALLER[/COLOR]/cedega_timedemo_installer

you may need to download a GTK Library thru synaptics

What package(s) would one need to get in order for the cedega time demo to install?
I get a message in terminal that says 

sh: Can't open /cedega_timedemo_installer

I am in the correct directory (Desktop).

---

### Post by EvilTchnlgy on 2006-12-23
try typing "chmod +x /cedega_timedemo_installer" first... hope that helps :)

---

