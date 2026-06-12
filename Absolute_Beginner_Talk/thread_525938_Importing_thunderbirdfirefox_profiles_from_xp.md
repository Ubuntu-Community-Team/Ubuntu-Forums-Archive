---
title: "Importing thunderbird/firefox profiles from xp"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by fistikuffs on 2007-08-14
hi is it possible to import thunderbird/firefox profiles from xp? how is it done?

---

### Post by colsinc on 2007-08-14
Hi fistikuffs,

Yes, it is possible and actually quite easy.  Your Firefox profile is located in

C:\Documents and Settings\YourUserName\Application Data\Mozilla\Firefox\Profiles\

I think you will need to enable viewing hidden folders to get there.  Your Thunderbird profile should be in Application Data or Mozilla as well (I can't quite remember).  Anyway, look around for a folder with a random name like 6zul3xho.default - there will be one for each profile you have.  Oh, and be sure to make a copy of this folder before doing anything!  With backup safely made, go into the random-name-folder and delete 'chrome' folder, now all you need to do is copy the random-name-folder to your linux installation, where it should go in:

/home/YourUserName/.Mozilla/Firefox/Profiles/
or
/home/YourUserName/.Thunderbird/Profiles/

I'm pretty sure those locations are right, if they aren't there, make sure the programs are installed!

Then just run said programs and you should be away.  Hope this helps!

---

### Post by SeanBlader on 2007-08-14
I copied the whole thunderbird settings folder that included all the account information as well and all those settings ended up in Ubuntu thunderbird as well. It was really great.

---

### Post by swazzler on 2007-12-26
Hey Guys,
I'm looking for some help in transferring my thunderbird profile form xp to ubuntu 7.10
I've copied my profile over to .mozilla-thunderbird and the profiles.ini lists the correct default folder.
However, everytime I open Thunderbird, it asks me to set up a new account. It does't list any of the three accounts I had access to in XP.
Also, it seems to have found my Personal Address Book and Collected Addresses, but not the additional Address Books I had created.
I thought it might be a question of lack of compatibility with some of my add ons so I removed them all - themes, extensions etc. - and had the same result: no email accounts and basic address books

What am I missing?

---

