---
title: "Firefox &amp; Thunderbird migration, XP =&gt; Ubuntu"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-05-25
Hi,

I use Firefox and Thunderbird on XP. The portable version of both. What is the best way to migrate over to Ubuntu?

Copy and paste would be nice :D 

Though I may have to put in more effort. Can my settings be transferred? Can my data be transferred?

Thank you.

---

### Post by aysiu on 2006-05-25
Yes, yes, and yes.

I'm not sure where the portable versions of Firefox and Thunderbird store their settings, but normally in Windows the settings are stored in C:\Documents and Settings\*username*\Application Data\Mozilla and C:\Documents and Settings\*username*\Application Data\Thunderbird.

In Ubuntu, they're stored in /home/*username*/.mozilla and /home/*username*/.mozilla-thunderbird (Ubuntu's Thunderbird) or /home/*username*/.thunderbird (Mozilla's Thunderbird).

Just copy the folders into their proper places, and you should be good to go.

---

### Post by joshrobinson on 2006-05-25
[QUOTE=u.b.u.n.t.u]Hi,

I use Firefox and Thunderbird on XP. The portable version of both. What is the best way to migrate over to Ubuntu?

Copy and paste would be nice :D 

Though I may have to put in more effort. Can my settings be transferred? Can my data be transferred?

Thank you.[/QUOTE]

your address book and your bookmarks can be exported in your windows xp versions, then burnt to disc or accessed on the hard-drive in ubuntu and imported.. your account for thunderbird should come over too.. ive never tried backing up emails because i really dont save them.. but there could be a way for that too

---

### Post by dmizer on 2006-05-25
copy and paste works fine.  i did it on my firefox/thunderbird.  amazingly it even imported my theme and plugins.

you'll need the folder labled "Mozilla" from "Application Data" in windows (it can be found in documents and settings > username > application data).
copy the Mozilla folder to your home directory in ubuntu.
rename the .mozilla directory in your ubuntu home directory to .mozilla-old.
rename Mozilla to .mozilla, and that will import all your firefox settings.

for thunderbird, the process is similar. except the folder to copy from windows is named "Thunderbird", and if you have thunderbird 1.5 installed in ubuntu, the Thunderbird folder needs to replace the folder in ubuntu named .thunderbird.  if you are using the ubuntu version of thunderbird, the folder to replace would be named .mozilla-thunderbird

that's it.

---

