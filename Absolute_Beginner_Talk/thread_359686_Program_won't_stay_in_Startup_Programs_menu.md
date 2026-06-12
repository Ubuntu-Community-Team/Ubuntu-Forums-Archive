---
title: "Program won't stay in Startup Programs menu"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by twtmc on 2007-02-12
I am not sure if this is allowed here because it is indirectly related to beryl (that's what isn't staying in the startup programs menu), but here it goes. I have tried putting it in so many different ways into the Startup Programs tab in System>Preferences>Sessions>Startup Programs, but whenever I restart or logout it disappears. What do I do?

---

### Post by quark_77 on 2007-02-13
Hi twtmc,

This sounds like a permissions issue on your startup directory, which is located here: /home/[your user name]/.config/autostart. To find out what the permissions for this directory are, try using nautilus and making sure you can create and delete files.

In case you can't, you need to change the permissions to allow you to access this folder. To do this, use the following:
```
sudo chown [your user name] /home/[your user name]/.config/autostart
sudo chmod 755 /home/[your user name]/.config/autostart
```
This does two things: a) sets you as the owner of the folder (should already be set up, but worth checking) and b) modifies the folders permissions giving: you all access, your group read & exec, everyone else read & exec.

Having checked the permissions, try to add something to the startup list. Click close, go back and look, if it is still there problem solved, if not, honestly not sure!

Good luck & Hope this helps!

PS If you would like more explanation on chown/chmod I have found a brilliant tutorial here: [http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners](http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners) scroll down to section 5: permissions. It explains the numbers you see above.

---

### Post by mwob on 2007-03-10
Found this today and its exactly what I was looking for - thanks for the tip :-)

---

### Post by punkboy on 2007-04-08
Thanks, I thought that was the issue but was unsure of the location of the file.

Regards,
brett

---

### Post by Citizen-D on 2007-05-21
Thanks from me too Quark_77.  I had the exact same problem as twtmc and sure enough, autostart was owned by root.  I chowned it and now have control back of my sessions.

Cheers,

D

---

### Post by dimbulb1024 on 2007-10-23
I am having this problem with gDesklets. As per quark_77 I checked for the autostart file in .config but there isn't one.
Should I create one?

---

