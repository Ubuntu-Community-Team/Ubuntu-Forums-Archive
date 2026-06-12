---
title: "Install Ubuntu : X Server Problem"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by diego898 on 2007-05-13
I am new to installing ubuntu, and when I try to boot from the CD, the very first thing I see after I select start ubuntu is "X Server failed to start" then a long list of something, then "caught error 11" or something similar.

What can I do?

---

### Post by Bachstelze on 2007-05-13
Use the Alternate CD to install. We'l look in that X server problem afterwards.

---

### Post by Happy_Man on 2007-05-13
This means that the CD can't detect your graphics card. What type is it?

EDIT: See now, I was going to suggest that afterrwards....FYI, OP, to get the alternate cd, go to ubuntu.com/download and check the box that says "i want the alternate install cd" or whatever is similar.

---

### Post by diego898 on 2007-05-14
but if Ubuntu cant detect my graphics card right off the bat, don't I have a problem? lol

---

### Post by Happy_Man on 2007-05-14
The text-mode installer needs no GUI...we will get around to walking you through the entire get your screen to be shiny bit later.

---

### Post by diego898 on 2007-05-14
So I tried to use the txt installer, only to get to the partioning, to select guided split the largest one. (The first option) for it to say, partioning halted and reached an error. Before that, the network failed to set up, but I figure its because I am on wireless. Anyway, should i partion the harddrive under windows now and then install ubuntu or can I do that through ubuntu?

---

### Post by eltorodeoro on 2007-05-14
sometimes it's best to perform the install hardwired.  let ubuntu (gparted) handle the partitioning.  the option you chose initially is fine.

---

### Post by diego898 on 2007-05-14
I treid to do it again, and this time it stayed on 0% for 20 minutes. I think I am just going to manually partition using gparted, and then try to install ubuntu. What do you think?

---

### Post by diego898 on 2007-05-14
Now I tried Gparted, and the GUI it loads is all non legible. all of the lines are skewed and you cant really see anything. though when I move the arrow keys, I see a patch of blue move up and down, so I am assuming Ive loaded something correctly. What can I do?

---

### Post by diego898 on 2007-05-14
Update - I correctly partitioned using Ubuntu, and it finished intalling. however, when I try to boot into the system, I get the same X Server error. What can I do to fix this?

---

### Post by Hobo Joe on 2007-05-14
> **diego898 said:**
> Update - I correctly partitioned using Ubuntu, and it finished intalling. however, when I try to boot into the system, I get the same X Server error. What can I do to fix this?

Try booting into recovery mode and typing:

```

sudo dpkg-reconfigure xserver-xorg

```

When it asks for driver, select vesa. Leave everything else as is.

Then type 'startx' and see what happens.

---

### Post by diego898 on 2007-05-15
----------Problem Solved------------

---

