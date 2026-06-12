---
title: "Thunderbird problem - lightning update overwritten data"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by quercusrobur on 2008-01-23
Hi can anybody advise? I've been using Thuderbird as my email client with the Lightening plug in installed as my calender application - I've just downloaded the latest upgrade to lightening, restrted my laptop as requested only to discover that  all my calender data (dates plus 'to do' lists) has apparently been deleted - luckily i didn't have a huge amount on there as i've only just started to try and keep a computerised calender and hadn't gotten round to entering much as yet, but its still annoying... 

Any suggestions how I can recover this data or avoid this happening again next time I want to upgrade???

Thanks, Graham

---

### Post by philinux on 2008-01-23
Did you use 

Tools>addons>find Updates

---

### Post by furball_1185 on 2008-01-23
Thunderbird stored that data (in Ubuntu) in the .mozilla directory off your home space. I think it's actually .mozila/thunderbird or something like that, but it doesn't really matter. To back up your Thunderbird settings, copy the folder to some other location before doing an update

cp -Rf ~/.mozilla mozilla-backup

That command will backup your mozilla prefernces file directory and all files inside to another directory called mozilla-backup. As far as recovering the data, browse around inside the .mozilla directory and see if you can find any of your old files. My experience with Thunderbird has been that these files tend to be unreadable by other programs (I guess for security). If Thunderbird doesn't know about these files, I think that thay may be gone for good, unfortunately. I think Thunderbird has some in-application backup methods you may also want to research.

---

### Post by quercusrobur on 2008-01-23
Thanks for the advice - however all my data has now re-appeared again just as mysteriously as it dis-appeared!!!

---

