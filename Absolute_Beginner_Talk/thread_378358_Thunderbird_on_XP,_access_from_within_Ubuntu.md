---
title: "Thunderbird on XP, access from within Ubuntu ?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by loanrangie on 2007-03-07
I use Thunderbird in XP as my mail client, can i get access to it from within Ubuntu ? Basically would like to be able to login to either OS and have access to the same email folders etc like already downloaded emails etc - is this realistic and possible ?

---

### Post by bollix47 on 2007-03-07
If your Thunderbird profile in XP is on a FAT32 partition then yes you can by changing the profile.ini file in ~/.mozilla-thunderbird to point to your profile in XP.

At least that works for me:

[General]
StartWithLastProfile=1

[Profile0]
Name=Default User
IsRelative=0
Path=/media/hda1/Documents and Settings/UserName/Application Data/Thunderbird/Profiles/k22lcm0t.default

[Profile1]
Name=bollix
IsRelative=1
Path=7w0s3pwk.bollix
Default=1

Subsitute UserName for the one you're using in XP and change the profile name.

---

### Post by rada on 2007-03-07
Yes, definitely doable.  Need to have or make a FAT32 partition to share data with windows, so ubuntu can write to it. Take a look at these pages and post back if you're still not clear what to do.

[[COLOR="Blue"]The mechanics of the sharing[/COLOR] ]("http://www.ces.clemson.edu/linux/firefox-thunderbird.shtml")

(this guy has mounted his FAT32 partition at /mnt/windowsd)

[[COLOR="Blue"]Where to put your profiles[/COLOR]]("http://www.mozilla.org/support/firefox/profile")

---

### Post by PartisanEntity on 2007-03-07
I have been told it is also possible to make an ext2 partition and store your email files on it, then if you install [the ext2 driver]("http://www.fs-driver.org/") in windows you can access the ext2 partition from both xp and ubuntu.

---

