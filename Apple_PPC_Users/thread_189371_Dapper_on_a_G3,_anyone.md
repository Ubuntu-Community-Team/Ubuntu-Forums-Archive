---
title: "Dapper on a G3, anyone?"
date: 2006-06-05
forum: Apple PPC Users
---

### Post by heffo_j on 2006-06-05
Hi all,

Thought I would be clever and upgrade Breezy to Dapper on a Blue G3 imac. HA!

I have no mouse or keyboard and the "black screeen of death".

Any advice on how to boot my old Breezy would be appreciated. Can I do so before it cycles into the Dapper stuff (that tech talk see?).

Regards
John

---

### Post by Sav on 2006-06-07
Try to press the tab button on yaboot page.
You would see a kernel named old_linux, or something like that.

Maybe your xorg.conf file is corrupted

---

### Post by ebeyer on 2006-06-07
[QUOTE=heffo_j]Hi all,

Thought I would be clever and upgrade Breezy to Dapper on a Blue G3 imac. HA!

I have no mouse or keyboard and the "black screeen of death".

Any advice on how to boot my old Breezy would be appreciated. Can I do so before it cycles into the Dapper stuff (that tech talk see?).

Regards
John[/QUOTE]

I ran into this exact same issue on the Breezy live CD.  The fix is detailed here: [http://www.ubuntuforums.org/showthread.php?p=1102761&posted=1#post1102761](http://www.ubuntuforums.org/showthread.php?p=1102761&posted=1#post1102761)

It was a bad setting under Monitors in the xorf.conf file.

It's interesting you were able to get as far as you did with Dapper.  I can't get anything on Dapper to load up - I get chucked into the Apple Firmware screen. The bug I'm having is detailed here: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)

---

