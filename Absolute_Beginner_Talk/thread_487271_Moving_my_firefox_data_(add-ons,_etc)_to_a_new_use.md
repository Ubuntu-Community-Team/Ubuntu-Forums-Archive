---
title: "Moving my firefox data (add-ons, etc) to a new user account"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-06-28
Hello,
I've created a new user account (system/administration/users and groups). How do i move my firefox data into that new user account, so that the way I've tweaked firefox in my original user account will be in my new user account?


Thank!

---

### Post by greg_g on 2007-06-28
You could simply copy (from your old user home folder) the .mozilla folder.

That should be it.  It will even bring along your cache :)

if you want a command (assuming you are logged into your new account):
 cp -R /home/{old_username}/.mozilla/ ~


greg

---

### Post by hanzj on 2007-06-28
fx can read all those files with the wierd names?
cool. will try it.

---

### Post by Detonate on 2007-06-28
Works on Thunderbird too.  Just copy all the files from the old profile to the new profile.  Word of caution, it's best if both have the same version number.

---

### Post by hanzj on 2007-06-29
So all I have to do is copy
 /home/olduseraccount/.mozilla/firefox 
to
/home/newuseraccount/.mozilla/firefox
? 
Correct?

---

### Post by alienexplorers on 2007-06-29
From mozilla.com:
> [http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

---

