---
title: "HELP!! How to install add-on apps"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by coolblue on 2005-07-12
OK now I have this Ubuntu add-on CD which supposedly has LOTS of packages (as  I've seen the list). But I can't figure out how to install things like MySQLCC and many other stuff which are not talked about in the guide.

How can I make sure that ALL or ONLY the packages which I select get installed?

Plz help the newbie.

Thanks

---

### Post by jiyuu0 on 2005-07-12
You must first burn the .ISO (do not extract and burn it if you want sysresccd to work)

After burning it, you need to install/extract the Add-On CD
sudo sh /media/cdrom0/install.sh
*This will only copy all the packages mentioned in UbuntuGuide into your hardisk. A copy of UbuntuGuide will be located on Desktop

Then, to custom install Add-On Apps (after install/extract the Add-On CD)
sudo sh $HOME/Downloads/ug-install.sh
*This will prompt you [Y/n/q] to install all the Add-On Apps

The ug-install.sh script will only install the Add-On section. You can then install the other sections by reading the UbuntuGuide located on your desktop

Btw, have you got the latest add-on-cd (2005-07-09)
[http://ubuntuforums.org/showthread.php?p=150088](http://ubuntuforums.org/showthread.php?p=150088)

---

