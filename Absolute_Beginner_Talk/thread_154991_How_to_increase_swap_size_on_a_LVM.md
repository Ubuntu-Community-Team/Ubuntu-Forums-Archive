---
title: "How to increase swap size on a LVM?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-04-04
My current swap file is a logical volume of a volume group. How should I go about increasing the swap size after adding another physical disk?

Thanks !

PS. Is it recommended to put the swap file on a LVM?

---

### Post by waster on 2006-04-04
from dodgy memory, try:

add new physical volume to a volume group (same one?)
create logical volume group if necessary
create logical volume
mkswap on that volume

best to put everything on LVM: makes juggling new drives and partitions much easier in future.

---

### Post by Akhran on 2006-04-04
I have an existing swap file on a logical volume. Do I need to create another logical volume group / volume as shown in your steps and mkswap afterwhich? How do I extend / increase the existing swap?

Thanks!

[QUOTE=waster]from dodgy memory, try:

add new physical volume to a volume group (same one?)
create logical volume group if necessary
create logical volume
mkswap on that volume

best to put everything on LVM: makes juggling new drives and partitions much easier in future.[/QUOTE]

---

### Post by waster on 2006-04-05
you can just mkswap in that case.

If the logical vols are on different physical vols, it is better to have the swap partitions separate, not one big partition. Linux can stripe them. I'm not sure how clever it would be if swap was spread over different physical volumes via LVM. I'd like to think it would be clever enough to exploit this, but the whole point of LVM is abstraction, so I imagine not.

---

