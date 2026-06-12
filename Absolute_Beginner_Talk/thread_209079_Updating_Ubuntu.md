---
title: "Updating Ubuntu"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by maltaethiron on 2006-07-04
Hey everyone, I'm just your run-of-the-mill Linux n00b that started playing with this whole new operating system a few days ago, and I'm trying to figure some things out right now.  First off, My uncle gave me an Ubuntu disc that installed Version 5.10 on my computer.  I ordered some new discs yesterday, but don't feel like waiting 4 to 6 weeks to get them to update.  Is there any way I can download an update for my computer?

Second: My sound isn't working for some reason.  I have speakers plugged into my computer, but every time I go to click on the volume controls on the panel, I get an error message that reads "No volume control elements and/or devices found."

Any help on these would be greatly appreciated.


-Paul

---

### Post by Jagot on 2006-07-04
Make sure you have updated everything.  Do this in Terminal to ensure:

```
sudo aptitude update && sudo aptitude upgrade
```

Then, either in Terminal or by hitting Alt+F2, do this:

```
gksudo "update-manager -d"
```

---

### Post by LordRaiden on 2006-07-04
Answer to Question 1 - if you want to update to Dapper - then do the following.

open up a terminal window

If you are using Ubuntu
```
sudo gedit /etc/apt/sources.list
```

If Kubuntu,
```
sudo kate /etc/apt/sources.list
```

Comment out the reference to CD with '#' sign. Then where ever it says 'breezy' change it to 'dapper'.

After that  ```
sudo apt-get dist-upgrade
``` 

After everything is downloaded and updated, you wil have the latest and greatest Ubuntu. I do suggest waiting for the CD though.

Answer to Question 2 - try playing music after doing the updates,  if you can hear anything, you are good to go. If not, follow the instructions in my signature below.

---

