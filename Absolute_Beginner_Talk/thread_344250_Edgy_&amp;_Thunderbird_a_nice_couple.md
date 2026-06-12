---
title: "Edgy &amp; Thunderbird a nice couple?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Ashrael on 2007-01-22
I upgraded to edgy last nite.. now i want to read my mail..so i try to start thunderbird....NOPE...it says: mozilla thunderbird is already running, but it's not responding. To open up a new windows...yak yak yak.... Funny thing is IT'S NOT

any ideas? anybody..

---

### Post by Bachstelze on 2007-01-22
```
rm ~/.mozilla/thunderbird/*/default/lock
```

I don't know if this is the exact path but you basically need to delete the "lock" file that is in your thunderbird profile folder, this is a quite common problem.

---

### Post by Ashrael on 2007-01-22
@HymnToLife:   I've looked for the file, but can't find it... My thunderbird profile is on another drive NOT on my /home partition...but on a fat32 part...so i can use it also when i'm in windoze, since 90% of my customers still use that, u know ;)  But i've dona clean install of edgy, so there should not be a profile at all...And there isn't, I just want to use my old profile on the fat32 disk...Where all the mail is stored...  But it still thinks it's running....AND IT ISN'T!!!](*,) 

any clues anyone?

---

### Post by Bachstelze on 2007-01-22
You also need to delete .parentlock in your profile folder. Where the folder is located doesn't matter.

---

### Post by Ashrael on 2007-01-27
@HymnToLife: i deleted the .parentlock files, still didn't work, then i looked at my profiles.ini file and it turns out that since i repatitioned the drives, the link to my mailfolder (on the fat32 disk) had been changed, hda6 became  hda5, changed it...and now it works....!!!!

thanx for your help....

---

