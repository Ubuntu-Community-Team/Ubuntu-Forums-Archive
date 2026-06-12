---
title: "all probs with dualboot"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by IngSoc on 2006-09-24
Ok so im about to dualboot my compter today with xp ans so far ive heard a few problims, well any ways I was wondering if any one could give me a run down on the best way to install both os`s onto my machine. What would I use to partition? well any ways any thoughts or what has been concerns would be greatly appriated. Thanks.

---

### Post by bulldog on 2006-09-24
Think about how you want to split up you hdd in partitions for XP an Ubuntu.
When you figured that out make a note so you can look back.

Install windows and use the windows cd to partition the space you provide to Windows.
Let the unused space unallocated for Ubuntu.

Then pop in the live cd and boot it.
Hit the install button and follow the onscreen steps.
When coming to partitioning let Ubuntu install in the unallocated space or choose to do it manually.

If you do it manually make a  / 10GB
                                 a swap  1-2GB
               Rest of your space  /home

Hit apply and Ubuntu will install on your hdd.

At the end it installs GRUB so you can choose which OS you want to boot.

This is a short version what happens.
If you need more details,just ask,and we tell you what we know.

---

