---
title: "code????"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by cjpkot on 2005-10-28
I have been reading forms on THE CODE and how people want to upgrade.  I am very new to linux that I know nothing.  Like some one want to upgrade to 5.10 and the answer was given on using the code commands.  Where are they and how do you enter code to upgrade.  I've been going through the software and I see no code applications.
Thanks for everything.

---

### Post by adwait on 2005-10-28
What code are you talking about?
```
this??
```

Thats just a way to separate the commands from the rest of the text, for the sake of clarity. They are supposed to be entered at the terminal. Maybe you have turned off this feature, and hence you are able to see the words [ code ] and [ /code ].

---

### Post by Emerzen on 2005-10-28
You must enter code at a terminal.  Right click on a blank area of the desktop and select 'open terminal'.  If you don't have this option install the following package from Synaptic -> **gnome-terminal**

---

### Post by cjpkot on 2005-10-28
Thank you
Their is some information in the terminal mode do I delete it and enter the commands.

---

### Post by Emerzen on 2005-10-28
No, don't delete anything.  You should have a cursor blinking at you.  Copy the commands you need from the forums, then paste them into your terminal and hit enter.

---

### Post by cjpkot on 2005-10-28
like this as I got from the form.




sudo apt-get update 
sudo apt-get dist-ugprade

---

### Post by Emerzen on 2005-10-28
yes, but put each command-line in one at a time.  Like this:

**sudo apt-get update**

then wait until it's done, then

**sudo apt-get dist-upgrade**

However, have you edited your sources.list first?

---

### Post by cjpkot on 2005-10-28
no I'm sorry I don't even know what a source list is.
That is how new I am.
Thanks

---

### Post by Emerzen on 2005-10-28
Okay, a couple of things you should know before doing a dist-upgrade.  One, you should back-up your system before doing this as it may not work perfectly.  

Here's a thread for the simplest way to do this:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

If you have nothing to lose on your Ubuntu partition, then this may not be necessary.  I would also download and burn the Breezy Install CD and burn it.  That way, if you have to do a clean install it will be a snap.  

If you want to throw caution to the wind, well, here you go:
[B]
sudo gedit /etc/apt/sources.list[/B]

Wherever you have 'hoary' or 'warty' in that file, change it to 'breezy'.  Save the file and close it.  Then put in the above commands to upgrade directly.

---

### Post by Emerzen on 2005-10-28
One more thing: it's always good to have a copy of the Live CD around too.  That way, if you ever break your system so bad you can't get into it, you can pop the LiveCD and get back on the net...and get some help.  So, I would download the Breezy Install and Live CD's before proceeding.  I know this may delay your upgrade, but if you run into trouble, you'll be glad you did it.  If you have a separate partition w/ Windows on it, say, then this isn't so important.

---

### Post by cjpkot on 2005-10-28
I have all ready copied kubuntu 5.10 to disk is that the right breeze you were talking about.
thxs

---

