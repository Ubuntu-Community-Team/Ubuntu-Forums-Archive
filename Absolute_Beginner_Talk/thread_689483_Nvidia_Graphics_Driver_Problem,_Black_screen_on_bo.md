---
title: "Nvidia Graphics Driver Problem, Black screen on bootup"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by turbo_dsm on 2008-02-06
I just installed Ubuntu on a partition with xp first.  It worked for a few minutes until in the upper right corner there was my name. I clicked on it and it took me to a diff user (but same name) and when it booted under this user a little green chip appeared in the upper right corner as well as a few other options than the first user i booted up with had. I clicked on the green chip and a window popped up for my graphics card to install the drivers. I have an 8800 gts using an samsung syncmaster 915n. I clicked to install the drivers and now when I boot it just remains at a black screen. I realize i have to install a new driver but how do i do this with a black screen? somebody help plz ): im a complete noob at ubuntu and have no idea what im doing.

---

### Post by turbo_dsm on 2008-02-06
i got this working but now have a new problem. i cannot edit my users. i realize one of the users has more features (probably admin) than the other. but when i try to change anything or access anything it prompts for a pw. after i enter the pw it says i do not have access to it. WTF! also internet stopped working on it and i cannot even mess with the network connections.

---

### Post by taurus on 2008-02-06
Remember, the first user that you created during the installing process has root privilege.  Anybody else that you've created after don't unless you add them to group admin in /etc/group.    So, maybe that is your problem, trying to run sudo without root privilege.

---

