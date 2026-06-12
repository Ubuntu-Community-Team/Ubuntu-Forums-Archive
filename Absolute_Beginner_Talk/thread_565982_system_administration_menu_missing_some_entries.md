---
title: "system administration menu missing some entries"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by herbg1 on 2007-10-02
Hi,
I am using Ubuntu 7.4.

I am missing "user and groups" and "date and time" from the system administration menu.
The only entries I see are:
Keyring manager
Language support
Login Window
Network tools
printing 
restricted drivers manager
software sources
synaptic package manager
system log
system monitor
update manager.

I went to system, preferences, main menu to try to add entries, but they only had the above choices, all checked.

I even changed the login window so I could log in as root, which I did.  Same choices.

How do I get "users and groups" and "time and date" and possibly what else is missing to show up?

I would not mind reinstalling Ubuntu if I could figure out how to reinstall it without erasing my files.  It always wants me to partition or format my disk if I try to install it again.

Thank you,
Herb Greenman

---

### Post by shad0w_walker on 2007-10-02
I have no idea what happened to your menu entries, but i can give you the commands so you can create the entries again.

Users and groups

Icon path - /usr/share/icons/Human/24x24/apps/config-users.png
Command -  gksu users-admin
Comment - Add or remove users and groups

Time and date

Icon path - /usr/share/icons/Tangerine/32x32/apps/config-date.png
Command - gksu time-admin
Comment - Change system time, date, and timezone

Hopefully that should sort you out nicely.

---

### Post by herbg1 on 2007-10-03
Hi,

You have given me hope.

As a beginner, I do not understand what you asked me to do.  I saw that you had me go to an icon but I do not know what to do with it.  I tried "sudo gksu users-admin" in the command line but nothing came up so I do not know how to give it the command.  

I guess my question is what do I type in to ask me for the command and where do I type in the command.

Thank you,
Herb Greenman

---

### Post by Paul820 on 2007-10-03
He means make a new menu entry from the main menu preferences, fill in the boxes with the information he gave.

---

### Post by herbg1 on 2007-10-03
I went to the system preferences main menu and went to add the items.  The icon did not exist so I left it blank.  I put in the command and comment.  This now shows up in the preference menu unchecked.  I check it, close it, then go back to the preference menu and it remains unchecked.  I uncheck and check others just to see if those take, and they do but the add users that I added in the preference remains unchecked and then of course does not show up in the system administration menu.

I have Ubuntu on another computer and of course all the entries show.  Should I reinstall?

I will not be able to read any replies until I get home again 12 hours from now.  



Thank you.

Herb Greenman

---

### Post by ha7777 on 2007-10-24
I installed MS fonts using Automatix on Gutsy and I am missing System->Preferences->Fonts. How do I get it back?

---

