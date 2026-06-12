---
title: "GRUb doesn't show Windows XP"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Fonon on 2007-09-02
Hi.  I recently reinstalled XP so I could play games.  I had to fix teh GRUB so I could log into Ubuntu...but now I can't go into Windows XP because it does not show up in the GRUB.  COuld any one help me?  Thanks in Advance.

---

### Post by Fonon on 2007-09-02
bump

---

### Post by molly_001 on 2007-09-02
As I understand your post, you re-installed Windows XP after having Ubuntu already installed on the machine.

This is OK, but GRUB won't include the Windows XP partition until you follows the instructions [here]("http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot").

NOTE:  You need the Live CD of Ubuntu or Kubuntu or Xubuntu, to accomplish this rewrite of Grub using the sudo grub command.  And, you need to know the partition on which Ubuntu is installed.  If you do not know the partition on which Ubuntu is installed, follows his instructions to use the GParted Live CD.

The fact that his instructions talk about Vista is unimportant.  It will work for XP.

---

