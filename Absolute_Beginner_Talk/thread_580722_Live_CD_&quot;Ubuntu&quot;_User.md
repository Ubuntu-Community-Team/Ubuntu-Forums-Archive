---
title: "Live CD &quot;Ubuntu&quot; User"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by abosio on 2007-10-19
I have 7.10 running on a USB drive. ([pendrivelinux install]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") works great.) I have set up a new user account with a password. Since the default user, search-defeatingly named "ubuntu", [appears to be a special user]("http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/#comment-1795") that does not retain a password, I am wondering:
[LIST]
[*]If this "ubuntu" user can be safely deleted?
[*]If so, how? (Since is does not appear in the Users and Groups list)
[/LIST]

Disabling the auto-login is not enough, as I would not like anyone sitting at my computer or who obtains my USB drive to be able to use that username to login without a password.

I did a lot of Googling and searching the forum, and I am new to Linux and Ubuntu, so I hope this post is not out of line.

---

### Post by kshane on 2007-10-19
> **abosio said:**
> I have 7.10 running on a USB drive. ([pendrivelinux install]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") works great.) I have set up a new user account with a password. Since the default user, search-defeatingly named "ubuntu", [appears to be a special user]("http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/#comment-1795") that does not retain a password, I am wondering:
[LIST]
[*]If this "ubuntu" user can be safely deleted?
[*]If so, how? (Since is does not appear in the Users and Groups list)
[/LIST]

Disabling the auto-login is not enough, as I would not like anyone sitting at my computer or who obtains my USB drive to be able to use that username to login without a password.

I did a lot of Googling and searching the forum, and I am new to Linux and Ubuntu, so I hope this post is not out of line.

Sorry, I'm not up on using USBs to boot up an OS, but why don't you just make a small partition and install it?

Kevin

---

### Post by abosio on 2007-10-19
> **kshane said:**
> Sorry, I'm not up on using USBs to boot up an OS, but why don't you just make a small partition and install it?

I own a Mac, but it is not Intel. (Even if it was, I would have to buy yet another HD just to do the file shuffling in order to partition.) I have access to a PC laptop, but I am not the owner and am not permitted to make those kinds of changes.

I can already tell I am probably going to want to move to an USB HD with more space, but I like the portability of the flash drive.

I think this is more of a question regarding Ubuntu and it's users from the Live CD than it is about the drive. (Other than I'm guessing that user wouldn't exist if I did a regular install. Now that I think about it, why can't I do a "regular" install onto USB flash? If I can't, does that mean I can't do it on an external HD?)

---

### Post by abosio on 2007-10-22
**Followup**: So I was told by someone to just **sudo passwd ubuntu** to change the password for that account. I did that and then could no longer log in at all. Not even with the other administrative user account I was logged into when I changed the password for the "ubuntu" user.

After giving up on finding a way to get back in I redid the whole USB install from scratch but now it says the drive is not bootable. Tonight I will try to repair the MBR per pendrivelinux's instruction in the hopes it will make it boot again. I had to do that the first time too, but then it was not telling me that it wasn't a bootable drive, it just would not boot.

---

