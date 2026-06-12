---
title: "Restoring 2 profiles in thunderbird - how to?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by pluisr on 2007-10-29
Hi!

I recently installed Ubuntu 71.0 on my computer and got rid of WinXP I like so far....But here  is a problem I need to solve: I backed my 2 thunderbird profiles (that I used in win-thunderbird) up with mozbackup,  and I want to restore them into Ubuntu-thunderbird.

Can anyone please help me?

Any place where i can find a step by step please?

:confused:

Thanks in advance!

---

### Post by thelocust on 2007-10-29
Do you have access to the profile files them selfs or does mozbackup put them in some kind of file format? if you can get access to the files then just copy them to your /home/username/.mozilla thunderbird/profiles/ (don't know the name of the thunderbird file but you'll find it.) and edit the profiles.ini file.

---

### Post by NT4usB on 2007-10-29
I create the user(s) on the new system. Don't bother with filling out the correct information, just enough to get past the profilemanager.
Then I copy the entire contents of: 
.../profiles/xxxxxx.default/
off the old machine into the newly created 
/xxxxx.default/
folder on the new box.
Don't copy the xxxx.default folder, just the contents.
chown and chmod to taste.
Alternatively, you can drop the old xxxx.default folder into profiles and browse to select it from within 'view settings for this account' but I haven't had as much luck with that.
More reading [here.]("http://kb.mozillazine.org/Moving_your_profile_folder")

---

### Post by pluisr on 2007-11-13
Many thanks!

FYI: 

1st. I had to create 2 profiles with the profile manager (the same details as I had in win) and copy the files prefs.js and profiles.ini to desktop
2nd. Restore each profile copying the contents of my old win profiles in its ubuntu/thunderbird correspondent folder.
3rd. Finally copy the previously copied to desktop files pref.js and profiles.ini to its correspondent place, replacing the old ones.

Hope it helps others too :)

More info here: [http://kb.mozillazine.org/Moving_from_Windows_to_Linux](http://kb.mozillazine.org/Moving_from_Windows_to_Linux)

---

