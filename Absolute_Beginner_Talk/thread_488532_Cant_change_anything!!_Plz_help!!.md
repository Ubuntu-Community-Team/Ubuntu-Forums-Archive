---
title: "Cant change anything!! Plz help!!"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by imuro on 2007-06-30
I got ubuntu to install on raid 0 finally after god knows how many tries. When I log in as myself (the only user except root) I can't edit the main menu so I don't have access to a whole lot of stuff that I need. Is this because I don't have root privilages? I'm sure that I have "ALL=(ALL) ALL" in /etc/sudoers 

Any help would be appreciated!

Chris

---

### Post by overdrank on 2007-06-30
> **imuro said:**
> I got ubuntu to install on raid 0 finally after god knows how many tries. When I log in as myself (the only user except root) I can't edit the main menu so I don't have access to a whole lot of stuff that I need. Is this because I don't have root privilages? I'm sure that I have "ALL=(ALL) ALL" in /etc/sudoers 

Any help would be appreciated!

Chris

Hi could you tell us what you are trying to edit in the main menu? :-k

---

### Post by Kevin the Olden on 2007-06-30
try...

sudo passwd

this will allocate a password for root. the you can log on as root (or su) and do what you need.


cheers and beers...

---

