---
title: "Is this a MythTV or MySQL issue"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Express Train on 2007-06-04
Since I don't have much experience as a system admin, I need guidance narrowing down my issue.  I followed the directions installing MythTV on Feisty at 

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O")

But when I got to the part where I configure the backend, it doesn't seem to save the settings.  I looked at the MythTV forums, and got the impression that I was too low level for their discussion, but I believe that the settings should be saved in the MySQL database.  So I was wondering how I should go about verifying that I have MySQL installed properly.  Or perhaps there is a way to verify that the MythTV backend is setup properly.

I'm just trying to figure out which direction the problem is so I can focus my searching for answers.  Any general guidance is appreciated.

---

### Post by superm1 on 2007-06-04
Hi,

You might try launching mythtv-setup in a terminal.  See if there are any errors there about saving the SQL settings or connecting to databases or anything like that.

---

### Post by Marious on 2007-06-04
I have very little experience with MythTV but I have run into the issue myself and it seems that you have to ensure you set up your MySQL database for it to work, if you run across a good link throw a post on here, because I would sure love to red on it myself. I assume you have a TV Card which one did you get and does it work on Windows?

Marious

---

