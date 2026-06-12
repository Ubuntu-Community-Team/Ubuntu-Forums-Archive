---
title: "Updating"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-04-18
Hey everyone,

When I installed Ubuntu, the first time it booted I saw an icon on the top that told me I had software that needed to be updated.  I clicked on it and it gave me a list of software that needed updates and automaticallyl did it.  

Is this automatic updating automatically on after the first boot?

Do I have to run "sudo apt-get update" or "sudo apt-get upgrade" ever?

When ubuntu upgrades come out, will I have to do anything, or will the automatic updater do this for me?

Thanks

---

### Post by earobinson on 2006-04-18
As I understand if you are running gnome it will auto tell you when you need to update (but there is nothing wrong with doing a "sudo apt-get upgrade or update"

When the new dapper comes out you can upgrade by:
1. downloading, and buringing the iso to update (not 100% sure this works)
2. editing /etc/apt/sources.list changing all the "breezy"s to "dapper"s then doing a ```
sudo apt-get update
sudo apt-get dist-upgrade
```

you can always type "man apt-get" for more info

---

