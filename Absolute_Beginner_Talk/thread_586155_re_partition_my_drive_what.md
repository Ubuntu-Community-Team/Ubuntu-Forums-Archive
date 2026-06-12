---
title: "re partition my drive? what?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Hoaxe on 2007-10-22
ok, I don't think I'm a TOTAL noob, but I'm posting a TOTAL NOOB question because I made a total Noob mistake.

I installed gutsy on my lappy, the install went perfect (can't say as much for my desktop pc though...) but! when i was asked to partition, I thought I had allocated 20gigs to ubuntu and 5 gigs to windows os.

wrong, oh how wrong i am

i realize now, 3 hours into customizing and downloading my apps, that i have the 5 gigs share of the pie. 

frustration ensues.

now i'm wondering, is there a way to take back 15 gigs of my windows drive and give it to linux where it belongs? i can settle for a middle man hard drive, a third partition in other words, but would prefer to simply grow the current linux partition at the expense of the windows one.

thanks.

---

### Post by cfaulkner on 2007-10-22
I would backup data and reformat just to save even more frustration.

---

### Post by LeeAdkins on 2007-10-22
GPartEd, the partition editor on the live disc, *should* let you resize them without too much hassle. It hasn't ever caused me problems, at least.

---

### Post by Sef on 2007-10-24
> GPartEd, the partition editor on the live disc, should let you resize them without too much hassle. It hasn't ever caused me problems, at least.

Another option would be to download [GParted]("http://grparted.sourceforge.net") itself.

---

### Post by Les Oeufs on 2007-10-24
I know what you mean. I was just about to resize my windows partition in the same manner when I suddenly stopped myself to re-read what the installer was saying.
The language they use is sort of ambiguous. The drive was formatted to NTFS with Windows on it. Then it said it was going to reformat the partition and wanted to know the "new partition size". It was a bit confusing because I wasnt sure if they were referring to the new size of the old partition, or the size of the new partition. Turns out its the first one.

---

