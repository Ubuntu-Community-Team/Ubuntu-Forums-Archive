---
title: "adding thunderbird to new user account"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by mikl2 on 2006-10-06
I've added my wife as a new user with a seperate login account.  I want to remove Evolution from her account and install Thunderbird for her email client.  I am unable to do this when I login to her account, since I don't have admin. powers.  That makes sense.  So....how do I go about this?  I have Thunderbird installed on my admin. account.

3 weeks new: Dapper
Thanks

---

### Post by timetunnel on 2006-10-07
You don't have to "install" Thunderbird for each account seperately. Software in ubuntu / Linux is usually installed with super user privileges ("root") and is available afterwards for every user on the system (except for programs that a normal user shall never use).
So, if you've installed Thunderbird already, for example with Synaptic Package Manager, then everything to run it is already there for your wife's account. You just have to start it.

Do you have the Thunderbird menu item in "Applications->Internet"?

BTW: you can only remove the Evolution package if you uninstall the ubuntu-desktop meta package. I'd rather leave Evolution on your system and ignore it.

---

### Post by cjm5229 on 2006-10-07
If you go to System>Users And Groups from your user, then click on your wifes user and click on Properties, then go to User Privileges,  you can give her user the same privileges you have. then you can use Ala Carte Menu Editor to create a shortcut in her user to Thunderbird. 

Good Luck

---

