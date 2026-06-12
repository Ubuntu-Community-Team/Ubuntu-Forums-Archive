---
title: "Why can't cups find printing device?"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by hellowood on 2006-07-28
hi,everyone!My cups runs well,but it can't find printing device,as showing nothing after enter "lpinfo -v" in command line.Somebody tells me that the user must be lpadmin group,but I can't find it in /etc/group!Surprise:!: And when i try to add cupsys into lp group using "adduser cupsys lp",it shows "adduser: cupsys: login already in use".What's the problem?And what should i do?:confused: 
Thanks for any information!

---

### Post by hellowood on 2006-07-30
can anybody helps me?

---

### Post by hellowood on 2006-07-30
help!:---)

---

### Post by OU812 on 2006-07-31
As far as I know, you already are a member of the lpadmin group. To verify this, I did system>admin>users and groups. Then I did groups>lpadmin>properties and my username was in the list. There are two ways of setting up your printer: using ubuntu's tools or entering [http://localhost:631/admin](http://localhost:631/admin) into your web browser. If nothing works, try a google search with the make and model of your printer, and the keyword linux. This may help.

john

---

### Post by alan yeates on 2006-07-31
> **OU812 said:**
> As far as I know, you already are a member of the lpadmin group. To verify this, I did system>admin>users and groups. Then I did groups>lpadmin>properties and my username was in the list. There are two ways of setting up your printer: using ubuntu's tools or entering [http://localhost:631/admin](http://localhost:631/admin) into your web browser. If nothing works, try a google search with the make and model of your printer, and the keyword linux. This may help.

john
The best answer I have seen was to add 'cupsys' to the group 'shadow', you may well have to try several printer models to find one that works. There are many newer models unsupported however, and it could be a good idea to see if yours is one of those. My Canon IP 3000 is a dead loss unless you use Turboprint though it does sort-of work with the S800 driver!

---

### Post by hellowood on 2006-07-31
thanks in advance!everyone!

---

