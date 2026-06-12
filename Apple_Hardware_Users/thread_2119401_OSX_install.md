---
title: "OSX install"
date: 2013-02-23
forum: Apple Hardware Users
---

### Post by raystilson on 2013-02-23
I followed  the instructions from help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation to make a partition of my harddrive to install Ubuntu on Mac running latest everything. I do the partition sync from refit, start from the Ubuntu boot disk, open the install drive. Select country. Then I have to choose the partition, I do, then Ubuntu tells me that it has the wrong "root" something. There is no disk utility to format it. What format should I use if I format that partition myself?

---

### Post by iMac71 on 2013-02-24
you might try to follow these steps:

[LIST]
[*]boot from Ubuntu CD;
[*]choose "Try Ubuntu" instead of "Install Ubuntu";
[*]when the Ubuntu Desktop appears, press the [SUPER] key: it's the [WINDOWS] key on Windows keyboards and the [COMMAND] key on Apple ones;
[*]when the Dash appears (the Dash is very similar to OS X spotlight) type "gparted" (without quotes) in the search field;
[*]double click on the icon of gparted to launch the application;
[*]when the gparted window appears, right click on the partition you created with rEFIt and choose "delete" from the contextual menu;
[*]in the "Edit" menu choose "Apply operations";
[*]wait until the partition has been deleted;
[/LIST]
now you've got unallocated space where to install Ubuntu:
[LIST]
[*]exit from gparted;
[*]click on the "Install Ubuntu" icon to start the installation.
[/LIST]

---

