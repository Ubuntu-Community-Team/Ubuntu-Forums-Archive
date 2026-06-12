---
title: "lost password"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by ggnewman on 2007-06-28
Help!!!! I have a Red Hat Linux 6 but do not have the password and username into it Is there a way we can resolve this

---

### Post by farueulogy on 2007-06-28
Welcome to the **UBUNTU** forms.

I've got a feeling you've got a difficult job on your hands. Maybe someone with experience will come to you soon but I'm not sure how many red hat-ers are around.

---

### Post by pmg on 2007-06-29
I think RedHat6 used the ext2 filesystem, so Ubuntu should be able to mount it.  If so, you might be able to boot the Ubuntu live boot cd and do all the following steps as root (i.e. with sudo):
[LIST]
[*]run "fdisk -l" to get a list of filesystems and type IDs;
[*]for each type "83" filesystem (there may only be one), mount it (e.g. sudo mount /dev/hda1 /mnt);
[*]look to find the one that is the root filesystem (normally mounted at /), and when you find it;
[*]make a copy of the "etc/shadow" file (cp /mnt/etc/shadow /mnt/etc/shadow.old) so you can restore it if necessary;
[*]edit the shadow file where the password is stored (vi /mnt/etc/shadow);
[*]remove the password for root - that is remove everything between the second and third colon;
[*]save the file - might have to force write it (":w!" in vi), or you might have to "chmod 600" it before you edit it;
[*]run the "sync" command to make sure your changes are written to disk;
[*]unmount the filesystem (umount /mnt);
[*]reboot your Redhat system, and attempt to login as root.  The password should be nothing, so if it still prompts just hit enter.  
[/LIST]
Once you are in at as root you can look at /etc/shadow to see what userids have passwords, and use the command "passwd joeuser" to reset the password for that userid.
Good luck.

I'll also throw a plug in here for [Knoppix]("http://www.sknoppix.org").  It's really not a noob tool, so I hesitate to point to it on a beginners forum, but it's a live boot CD with a number of tools that can help with system recovery problems like this.  If the above with the Ubuntu cd doesn't work, you might want to give that a try, but you've got to have a pretty good idea of what your doing.

---

### Post by farueulogy on 2007-06-29
Now that's some expert advice :O

---

