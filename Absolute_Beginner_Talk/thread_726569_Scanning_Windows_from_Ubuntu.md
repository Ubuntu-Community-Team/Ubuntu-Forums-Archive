---
title: "Scanning Windows from Ubuntu"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-03-16
How do I go about doing this? I have read somewhere that Linux can spot viruses on Windows systems better than say AVG/Spybot, which are what I'm using. 

How do I go about scanning and deleting viruses on my XP partition with Ubuntu?

---

### Post by |{urse on 2008-03-16
at a shop i used to work at we had an ubuntu drive scanner, which was basically an old pc chassis with an old mobo and ubuntu dapper on a 20gb hdd with extra ide ports and a laptop ide port. it had clam av as well as avg. From what i remember avg would find all the virii but not remove them (lol) but clam would do the job nicely. this works out awesome if you run a tech shop and dont want to practice unsafe sex with your network ^^ :)

---

### Post by PeterJS on 2008-03-16
The not removing them I bet was likely because you were using dapper which pre-dates NTFS write support (added with ntfs-3g, in Fiesty I think?).

To scan a windows drive from ubuntu all you need to do is mount the drive, and point your scanner at it. ClamAV is in the repositories, and you can get AVG debs from here:
[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl)

---

### Post by |{urse on 2008-03-16
Yeah thats's exactly what the problem was, it worked fine with clamAV though, i still scratch my head over that.

---

