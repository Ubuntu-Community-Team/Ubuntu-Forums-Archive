---
title: "GAIM install problems, wine install problems, EVERYTHING install problems!"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-07-29
I can't seem to find my C: drive after I installed wine, although I am pretty sure i installed it correctly! I even went to winecfg and everything! Where is my drive located?! I tried to install Warcraft III on it and ran:

wine Install.exe

in the /media/cdrom directory and entered the keys and everything, but I can't launch the program because i cant find the War3.exe file in my non-existant c-drive. I then tried to install it again, but it says that directory already exists. Arg...

For GAIM, I tried to install Extended Prefrences but the instuctions clearly do not work. I click on the file and choose to run the install script, but seeming nothing happens. I tried to install the WineTools the same way and the same thing happened! I clicked on the install.sh and clicked run but absolutely NOTHING HAPPENED!!!

THEN I TRY TO GET GOOGLETALK ON GAIM AND I FOLLOW THE EASY INSTRUCTIONS CAReFULLY AND EVEN THAT SIMPLE TASK DOESN'T WORK! HOST UNKNOWN ERROR! NEVER GOT THAT ERROR WITH WINDOWS!

Ugh... sorry for being so angry; just hafta vent at everyone for a bit. I'm just really frustrated that everything I try seems to fail. Please help. :(

---

### Post by gnoshi on 2006-07-29
I believe C drive will normall be in ~/.wine/drive_c/

As for Gaim, you should be able to install simply from packages.
sudo apt-get install gaim

---

### Post by Indras on 2006-07-29
> **Charco said:**
> I can't seem to find my C: drive after I installed wine, although I am pretty sure i installed it correctly! I even went to winecfg and everything! Where is my drive located?! I tried to install Warcraft III on it and ran:

wine Install.exe

in the /media/cdrom directory and entered the keys and everything, but I can't launch the program because i cant find the War3.exe file in my non-existant c-drive. I then tried to install it again, but it says that directory already exists. Arg...

Open your home folder in nautilus and hit CTRL+H (to show hidden files).  You should see a directory called ".wine" in there.  Your C: drive will be in that.  I'd just suggest making a shortcut to the desktop to this folder.

I wish I could give you some insight into the other problems you're having, perhaps try running the ".sh" files from a terminal and posting the output?

---

### Post by Charco on 2006-07-29
Ok, I found that path in terminal, but how do I actually launch the War3.exe? As for GAIM, I have GAIM installed, but i can't get the plugin Extended Preferences to install. And any ideas on the google talk not working?

---

### Post by Indras on 2006-07-29
Once you've found the executable, just type:
```
wine War3.exe
```

As long as you've configured wine correctly, everything should work just fine.  If not, try running winecfg to make sure everything is set up right.

Here's a HOWTO I googled up from the Wine Application DB:

[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

As for gaim extended preferences, I've actually never heard of it.  I use Gaim 2 beta 3 that Automatix installed for me, I've never tried any of the plugins.

And I have no idea what Google Talk is.

---

### Post by Charco on 2006-07-29
Ok, thanks for your help. I got some things running now, yay.

---

### Post by jmattos on 2007-03-10
> **Charco said:**
> I can't seem to find my C: drive after I installed wine, although I am pretty sure i installed it correctly! I even went to winecfg and everything! Where is my drive located?! I tried to install Warcraft III on it and ran:

wine Install.exe

in the /media/cdrom directory and entered the keys and everything, but I can't launch the program because i cant find the War3.exe file in my non-existant c-drive. I then tried to install it again, but it says that directory already exists. Arg...

For GAIM, I tried to install Extended Prefrences but the instuctions clearly do not work. I click on the file and choose to run the install script, but seeming nothing happens. I tried to install the WineTools the same way and the same thing happened! I clicked on the install.sh and clicked run but absolutely NOTHING HAPPENED!!!

THEN I TRY TO GET GOOGLETALK ON GAIM AND I FOLLOW THE EASY INSTRUCTIONS CAReFULLY AND EVEN THAT SIMPLE TASK DOESN'T WORK! HOST UNKNOWN ERROR! NEVER GOT THAT ERROR WITH WINDOWS!

Ugh... sorry for being so angry; just hafta vent at everyone for a bit. I'm just really frustrated that everything I try seems to fail. Please help. :(

firstly, I feel your pain.

Secondly, check out this page which talks about installing stuff using aptitude instead of apt-get


[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

sudo aptitude install wine gaim

---

