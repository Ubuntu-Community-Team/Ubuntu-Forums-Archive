---
title: "File Browser cannot navigate above home folder"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by bipul on 2008-04-04
I run a ububtu 7.04 fiesty fawn system. It was working fine.
Today i was trying out some upgrades on artwork usplashes etc.
once done i wanted to browse to the directories like /bin or /bin or /usr ,etc 
but whenever i click the "<" beside the tab showing my user name , Desk top shows for a few seonds & return to the home folder.
I also get a nautilus-debug-log.txt on my home folder whic goes as thus....


===== BEGIN MILESTONES =====
0x8182d30 2008/04/04 21:10:15.8338 (GLog): file nautilus-navigation-window.c: line 834 (activate_nth_short_list_item): assertion failed: (index < g_list_length (window->details->short_list_viewers))
0x8182d30 2008/04/04 21:10:15.8339 (USER): debug log dumped due to signal 6
===== END MILESTONES =====
===== BEGIN RING BUFFER =====
0x8182d30 2008/04/04 21:10:10.9988 (USER): window 0x81f8048 open location: old="(none)", new="x-nautilus-desktop:"
0x8182d30 2008/04/04 21:10:11.0881 (USER): create new navigation window=0x81de928
0x8182d30 2008/04/04 21:10:11.0881 (USER): window 0x81de928 open location: old="(none)", new="file:///home/bipul"
0x8182d30 2008/04/04 21:10:11.7062 (USER): change view of window 0x81de928: "file:///home/bipul" to "OAFIID:Nautilus_File_Manager_Icon_View"
0x8182d30 2008/04/04 21:10:11.9244 (USER): finished loading window 0x81f8048: x-nautilus-desktop:
0x8182d30 2008/04/04 21:10:11.9699 (USER): finished loading window 0x81de928: file:///home/bipul
0x8182d30 2008/04/04 21:10:15.5423 (USER): selection changed in window 0x81de928
	file:///home/bipul/OFFICE
0x8182d30 2008/04/04 21:10:15.7747 (USER): fm_directory_view_activate_files window=0x81de928
	file:///home/bipul/OFFICE
0x8182d30 2008/04/04 21:10:15.7752 (USER): directory view open_location window=0x81de928: file:///home/bipul/OFFICE
0x8182d30 2008/04/04 21:10:15.7752 (USER): window 0x81de928 open location: old="file:///home/bipul", new="file:///home/bipul/OFFICE"
0x8182d30 2008/04/04 21:10:15.7752 (USER): finished loading window 0x81de928: file:///home/bipul
0x8182d30 2008/04/04 21:10:15.8338 (GLog): file nautilus-navigation-window.c: line 834 (activate_nth_short_list_item): assertion failed: (index < g_list_length (window->details->short_list_viewers))
0x8182d30 2008/04/04 21:10:15.8339 (USER): debug log dumped due to signal 6
===== END RING BUFFER =====


This configuration for the debug log can be re-created
by putting the following in ~/nautilus-debug-log.conf
(use ';' to separate domain names):


[debug log]
max lines=1000

Yester day i also enabled root account login in my system by editing a gdm.conf file
'Allowroot=true'

Please can anyone throw any light??:confused:

---

### Post by bipul on 2008-04-04
Guys for some more info:
i can view other folders using $ nautilus <foldername>
but when i try to open even my directories inside my user folder the problem repeats.

---

### Post by nick_h on 2008-04-04
This problem may be related to [bug #127978](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/127978).

---

### Post by bipul on 2008-04-05
Hey Nich _h Thank You very much!!
U directed me to a link ... from where i got the right thing...
It was Bug no #198716
:guitar:

---

### Post by bipul on 2008-04-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/198716](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/198716)  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/198716](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/198716)

---

### Post by nick_h on 2008-04-05
I've just seen a similar thread [here](http://ubuntuforums.org/showthread.php?t=745868).

---

### Post by bipul on 2008-04-06
Hey Nick ... Nautilus is not throwing any message when i open any folder through my terminal... i was doing it the whole of last day:mad:

---

