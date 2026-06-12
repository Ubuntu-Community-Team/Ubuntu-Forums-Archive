---
title: "I broke sources.list can anyone please help?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by i_z0mbie on 2008-02-09
I was trying to install WINE so that I could operate a particular simulation program. In the process I was told to do the following:

"First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Gutsy (7.10):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list"

This did not work; I had the idea that perhaps -O should be -o. . .hence I entered the following command:

"sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -o /etc/apt/sources.list.d/winehq.list"

This appeared to have the result of overwriting any files that were in the folder sources.list.d However my sources.list and sources.list.save files are in /etc/apt not /etc/apt/sources.list.d Therefore I simply removed the winehq files and copied the sources.list files into the sources.list.d folder.
But there is now an error on line one reading:

"Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name."

When I try to edit the code to delete line one and keep:

"deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse"

I get a message saying that I do not have permission to do this. I tried the command:

"gksudo gedit /etc/apt/sources.list"

because I read that this would allow me to have write access. But this returned the message:

"Could not create per-user gnome configuration directory `/root/.gnome2/': No such file or directory"

Please is there anyone who can help me to either fix the problem manually or to restore my computer to a previous day? Please someone help me, and may the Flying Spaghetti Monster bless you. Thanks.

Yours Very Desperately

Jonny

---

### Post by spiderbatdad on 2008-02-09
```
gksu gedit /etc/apt/sources.list
```

---

### Post by i_z0mbie on 2008-02-09
I get the following message when I try gksu:

"(gksu:2364): Gtk-WARNING **: cannot open display:"

Thanks for trying, I fear that I may have to reinstall everything.

---

### Post by spiderbatdad on 2008-02-09
are you by chance using a secondary user account? Or is this the account created at the time of installation? Hope you don't have to reinstall, but sometimes that makes people more comforatble.

---

### Post by i_z0mbie on 2008-02-09
I'm using the one created at install.  I tried to login as root; but when I go to system-> Admin-> Login Window (so that root can login with GDM) the 'puter acts like it's loading the screen and then nothing happens.  I tried logging in through the terminal as root but that also did not work.  I really am stumped.

---

### Post by seventhc on 2008-02-09
[COLOR=Black]Go into synaptic and do a search for[/COLOR] [COLOR=Navy]*gksu *[COLOR=Black]and mark it for reinstallation.[/COLOR][/COLOR]

---

### Post by spiderbatdad on 2008-02-09
it should not be necessary to login as root. You can navigate graphically to your user account System>>Administration>>Users and Groups. There, you can select you name and click Properties. Then select User Privileges tab and ensure Administer the System is selected.

---

### Post by i_z0mbie on 2008-02-09
Ok, well I found that the gksu folder was not under the synaptic folder they are both under /usr/share now the only file I see in gksu is:

gksu-migrate-conf.sh

Also I supposedly do have the correct privileges.  

Ok so how do I reinstall gksu?

---

### Post by spiderbatdad on 2008-02-09
```
sudo apt-get remove --purge gksu
sudo apt-get install gksu
```

---

### Post by i_z0mbie on 2008-02-09
Thank you so much for your help.  Here's what I finally did.  I gave the command 

sudo bash in a terminal and logged in as root. . .which I know is bad then I used gnu nano to edit the files.  It appears to be working as I did a sudo apt-get update and it ran.  However it did say that I have redundant files.  I believe that I created /etc/apt/sources.list.d/. . . when I first started this problem.  But, I'm not going to play with it too much.  Again thanks for your help. 

Yours &c.

Jonny

---

