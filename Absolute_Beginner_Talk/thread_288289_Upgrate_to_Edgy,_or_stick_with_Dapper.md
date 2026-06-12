---
title: "Upgrate to Edgy, or stick with Dapper?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Tobywuk on 2006-10-29
Hey,

Im new to linux, and ubuntu. I currently have Dapper installed, and have had it for about a month.

 Iv heard mixed things about the new version not being supported for long, and that its buggy, and that lots of people are just sticking with dapper as its a more supported version, and edgy was just created to show what the new linx versions can do, just for demonstration purposes?

Is edgy the new dapper?

Im a bit confused to weather i should stick with dapper or upgrade to edgy?

Thanks :)

---

### Post by tronica on 2006-10-29
i feel edgy is pretty stable, but also that its more for the people who want the bleeding edge distro, but if you want stable, and pretty up to date then i would stick with dapper. you could all ways download edgy and install it on another machine or duel boot it.

---

### Post by bulldog on 2006-10-29
Edgy is not the new Dapper!

Edgy is a test release for new software and is some what buggy.

If you need your computer and you're not very familiar with Linux,I should stick with Dapper.

If you're in for an adventure and don't mind to struggle a bit to seek solutions,and don't mind to reinstall,your just the person for Edgy Eft.

---

### Post by srunni on 2006-10-29
Contrary to what some other people have said, a clean install of Edgy is very stable and has very few problems. I would suggest that you upgrade to Edgy, but not right away - wait for some of the bugs to be worked out. I would also reccomend that you do a clean install on your computer, as the dist-upgrade procedure has many problems. Edgy is not just to show what new linux distros can do, and as far as Dapper's long time support goes - that's not meant for the home desktop user. If you didn't partition your hard drive when you originally installed Ubuntu, make sure you do it this time so that you won't have to back up/restore your data each time you upgrade Ubuntu (every 6 months). Do it like this:

Partition 1 - system
Filesystem: ext3
Size: 10 GB
Mount to: / (root folder)

Partition 2 - home
Filesystem: ext3
Size: Space left over minus swap partition
Mount to: /home (home folder)

Partition 3 - swap
Filesystem: linux-swap or swap (I don't remember what it exactly says in the installer)
Size: 2 times your RAM
Mount to: swap

More info can be found at aysiu's great site: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by jd65pl on 2006-10-29
There is a sticky thread in this forum addressing the issue. [See here]("http://ubuntuforums.org/showthread.php?t=286209")

---

