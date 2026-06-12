---
title: "Firefox problem with 7.10 update"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by r3bol on 2007-10-24
I've just updated to 7.10 and get this when trying to launch FF (which fails to launch after clicking OK to messege)
[IMG]http://i157.photobucket.com/albums/t54/r3bol/Screenshot-1.png[/IMG]
There seems to be plenty of room on my disk...so maybe its the profile directory. I can't seem to find it though! I'm at /usr/lib/firefox or /usr/lib/mozilla-firefox 
What should I be looking for?
Or maybe a reinstall of FF would be better?

Thanks.

---

### Post by Pumalite on 2007-10-24
Better yet; install the latest: [http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)
Download to your Desktop, then:
cd ~/Desktop
tar xvzf firefox-2.0.0.8.tar.gz
cd firefox
./firefox

---

### Post by alienexplorers on 2007-10-24
You can migrate your old extensions to your new profile as shown here:
> [http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

---

### Post by r3bol on 2007-10-24
The reinstall didn't work.

I'll look into > migrate your old extensions to your new profile now.

Thanks.

---

### Post by r3bol on 2007-10-24
I managed to get FF going in -safe-mode and saved my bookmarks.html file. I didn't really need anything else.

Then I tried to create a new profile (hopefully fixing the problem in the process) source= [http://kb.mozillazine.org/Profile_Manager#Accessing_the_Profile_Manager](http://kb.mozillazine.org/Profile_Manager#Accessing_the_Profile_Manager)

cd ./firefox -profilemanager
*bash: cd: ./firefox: Not a directory*

so 
cd /usr/lib/firefox -profilemanager
*/usr/lib/firefox$*

so i tried the commend since i was in the right directory...
profilemanager
*bash: profilemanager: command not found*
-profilemanager
*bash: -profilemanager: command not found*

can anyone spot something i'm doing wrong?

---

### Post by alienexplorers on 2007-10-25
You have to run out of the terminal just:
> firefox -Profilemanager

---

### Post by r3bol on 2007-10-25
thanks, FF seems to be working now after adding the new profile.

---

### Post by FredB on 2007-10-25
> **r3bol said:**
> I've just updated to 7.10 and get this when trying to launch FF (which fails to launch after clicking OK to messege)
[IMG]http://i157.photobucket.com/albums/t54/r3bol/Screenshot-1.png[/IMG]
There seems to be plenty of room on my disk...so maybe its the profile directory. I can't seem to find it though! I'm at /usr/lib/firefox or /usr/lib/mozilla-firefox 
What should I be looking for?
Or maybe a reinstall of FF would be better?

Thanks.

Looks like your ~/.mozilla/firefox/name-of-profile directory is read only.

Close your firefox and in a console, go to your ~/.mozilla/firefox/ directory by entering :

```
cd .mozilla/firefox/ 
```

You'll find a directory with a strange name.

You'll have to set up write permission on it :

```
chmod -R +w name of directory
```

I think it will work.

---

### Post by r3bol on 2007-10-25
:~/.mozilla/firefox$ ls
Hmmm... I wonder what strange directory it could be? :)
[I]ebegmd8m.DH-Test  
pluginreg.dat  
yfxpds4b.2007.10.25
ln3h7bz7.default  
profiles.ini[/I]

---

