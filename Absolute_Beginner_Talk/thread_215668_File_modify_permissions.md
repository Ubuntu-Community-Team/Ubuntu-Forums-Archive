---
title: "File modify permissions"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by meshica7 on 2006-07-14
Hello folks,new to Ubuntu/Linux here...

 I recently installed Ubuntu (Dapper) on a 2nd drive on my Power Mac G4.I now have a dual boot system!A big thank you to [nooBWilling To Learn]("http://ubuntuforums.org/member.php?u=83738") for all of the great support in getting me up and running!
 I have a question about modyfing folders.Here is what I am trying to do...
 I want to add some firmware files to lib/firmware so I can get Ubunto to work with my Airport Extreme and get on the internet.When I go to move the files,I am told that I do not have sufficient permissions to do so and I must be logged in as root.I assumed since I did not create any other user profiles that I was the root user at login.If not,how do I get these permissions?
 Any help is appreciated!:mrgreen: 

thanx!
 Juan

---

### Post by T700 on 2006-07-14
For security reasons, there is no default root account in Ubuntu.  To act as root in Ubuntu/Gnome, preface the command with either "sudo" (for non graphical apps or "gksudo" for graphical ones.  When it asks for a password, use the one you use to log into your computer.  For example:

```
sudo aptitude install xyz
``` 
The commands under KDE are "sudo" and "kdesu".

Paul

---

### Post by meshica7 on 2006-07-15
Thanx for the info.I was able to move the files in question using the **mv** commands this way.
 
 I have a question concerning a message I recieved in the term after I tried to type the sudo command a few times later:

**Timestamp too far in the future: DATE/TIME**

 What does this mean? When I get this message,I can't exucute any commands as with sudo.Is there a work-around?
 Thanx
 juan

---

