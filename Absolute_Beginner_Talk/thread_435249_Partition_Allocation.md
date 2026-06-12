---
title: "Partition Allocation"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by LE CHARBON on 2007-05-06
I want to make sure I have it split pretty good. If someone could critique this. I do not need an even split, just an opinion if it looks like the right amount for a 120 GIB HD. This is what I ended up with.:-| 

NTFS 46.9 GIB

/HOME  18.56 GIB
SWAP  2.19 GIB
/ 44.13 GIB

---

### Post by bobplano on 2007-05-06
you probably don't need such a large root partition unless you regularly install 40 gigs worth of programs. my suggestion is switch the /home and / amounts

---

### Post by LE CHARBON on 2007-05-06
If I switch the names will I need to reinstall? Can this be done with live cd using gparted, or what? Can I get an explanation? :confused:  Complete ubuntu beginner.

---

### Post by bobplano on 2007-05-06
have you already installed ubuntu? it's fine if you've already installed ubuntu, there's enough memory for each partition. i'm not sure how you would switch them, but i know it would be difficult

---

### Post by LE CHARBON on 2007-05-06
It's installed.

---

### Post by antoz on 2007-05-06
You may be able to shrink one and enlarge the other depending on where they are located in relation to each other, don't know about swapping them. There is really nothing wrong with your setup exept  it would have been better to have the home partition larger as bobplano sugested.

---

### Post by LE CHARBON on 2007-05-06
What is the best way to resize and how? If you do not mind. I would appreciate that!

---

### Post by louieb on 2007-05-06
Because I lazy I vote for the reinstall.  Much less work, probably less time. Resizing is always iffy . Just swap / and /home assignments and be done with it.

---

### Post by Clay_Banger on 2007-05-06
using gparted would be the best way. you can download a live cd and boot into it. it is then very straight forward to shrink your root partition, move your swap partition then increase the size of your home partition.

---

