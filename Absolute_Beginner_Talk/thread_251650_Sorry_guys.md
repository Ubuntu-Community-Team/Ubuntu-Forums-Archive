---
title: "Sorry guys"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by kockbeard on 2006-09-05
How can I set up a second profile for the wife so she can use the puter and have her own background and favourites and stuff

---

### Post by goatmale on 2006-09-05
system<administartion<users and groups. 
add a user, give her a password and you should be good.

---

### Post by catlett on 2006-09-05
There is a gui for adding users and groups. Go to the top panel and enter into System<Administration<Users and Group. I know there is an "add user" button but I do not know the process because I never used it.
To add a system user from the terminal enter (I will use wife as thew users name but put in whatever the name is to be)
```
sudo useradd wife
```
If you want her to have sudo powers, add her to the admin group
```
sudo adduser wife admin
```

---

### Post by kockbeard on 2006-09-05
Not sure if she needs sudo powers all she really wants to do is play music and surf the web, will that be possible with the "light" version of entry?? Also does that mean she gets her own logon when the machine boots??

---

### Post by catlett on 2006-09-05
I didn't mean to leave you hanging, these Ubuntu servers are really bad the last few months. I am continually timing out while trying to connect.
Anyways, usinmg User and Groups is probably the easiest way to add a user.
And yes she will enter her name and password at the log in page. You do not need to restart to switch users, you can log out and have her log in from the log in screen.

---

### Post by kockbeard on 2006-09-06
Don't worry about "leaving me hanging" I'm more than grateful that you guys even answer me at all.

I know what yuo mean about the servers timing out though, looking around the rest of the web there seems to be a lot of recent interest in Ubuntu, so I'm guessing that the traffic volumes are off the scale.

Anyway I set it up through System > Admin, she'll try it tonight and we'll see if it works then.

Can't wait to be as quick with Ubuntu as I was with windows, then I can start helping others, this is truly the friendliest technical support forum I've ever encountered

---

### Post by daou on 2006-09-06
> Can't wait to be as quick with Ubuntu as I was with windows, then I can start helping others, this is truly the friendliest technical support forum I've ever encountered

I've been using Ubuntu for two months and I'm already faster with it than with Windows (13 years of experience). Some of that has to do with the OS not hanging every 30 minutes and requiring a CTRL+ALT+DEL explorer.exe ;) .
And yes, this is the friendliest forum period that I have run into. It's contagious. I try to help as much as I can. And I've even begun developing my own app for GNOME because I want to contribute.

---

