---
title: "Startup Apps"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-11-20
Greetings!

Just a simple questions.
I know this has been asked be for but i can't seem to find it by using the search.

Just wanted to know how to change what Apps\Programs startup when you start the computer?

I think it is System>Prefrences>Sessions  But it shows the current running apps and nothing in the 'Startup Programs'.
Is this the correct place where I change the start up apps or is there like some text list that I have to edit?

I would like to just stop the 'Update-notifier' since the thing never shows any updates anyway, but I would like to also add some apps to the list as well.

Thanks

---

### Post by parktownprawn on 2005-11-20
to start a program when gnome starts up go to
System>Preferences>Session

click on the Startup Programs tab

click on Add 

and type in the command for the program you want to start up.

---

### Post by davmac on 2005-11-20
[QUOTE=parktownprawn]to start a program when gnome starts up go to
System>Preferences>Session

click on the Startup Programs tab

click on Add 

and type in the command for the program you want to start up.[/QUOTE]

This will work for an individual user. If you want something that runs as root, or runs as part of the boot up (rather than login) you can open a terminal and type "sudo gedit /etc/init.d/bootmisc.sh" and add the command somewhere near the bottom.

Hope this helps,

Dave Mac

---

