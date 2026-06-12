---
title: "How do I change what users can see mounted drives?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by NineseveN on 2007-11-23
Is there a way to change what drives show up (or mount) for each user in Ubuntu? I created another user for my better half, but when I log in under the new account, all of my drives are shown in the icons on her desktop. Not even talking about the need for privacy, I have work documents and other important things that I want no one else to have access to if they log into their account on this machine. I have that all set-up in Windows XP already.

These are all NTFS (Windows XP) drives or partitions. I'm new to Ubuntu and *nix in general, but I'm hoping that there's a way to do this.

The new user has all of the privileges checked except "Administer the System".

Under advances, the Main Group is showing her username.


Thanks in advance. I did do a search, but I didn't find anything really answering this specific query (everything I found was how to mount drives that aren't showing for the main user).

---

### Post by jken146 on 2007-11-23
If you want to remove the icons from the desktop, do the following:

Press Alt+F2, then type
gconf-editor
Navigate to apps>nautilus>desktop and un-tick the box next to volumes_visible.

I'm not sure if this will do it for all users or just the one you're in when you do it.  Instinctively I'd think the latter.


If you want to restrict permissions on those volumes, press Alt+F2, type
gksu nautilus
Navigate to /media
and you can change the permissions of the files (right-click > Properties > Permissions).

---

### Post by NineseveN on 2007-11-23
> **jken146 said:**
> If you want to remove the icons from the desktop, do the following:

Press Alt+F2, then type
gconf-editor
Navigate to apps>nautilus>desktop and un-tick the box next to volumes_visible.

I'm not sure if this will do it for all users or just the one you're in when you do it.  Instinctively I'd think the latter.

Thanks! That worked well. It only applies to the logged in user, but I took them off of both accounts (I didn't really care for them being on there myself regardless of security/privacy).


> If you want to restrict permissions on those volumes, press Alt+F2, type
gksu nautilus
Navigate to /media
and you can change the permissions of the files (right-click > Properties > Permissions).

I did that, the first time I tried to run Nautilus, nothing happened (maybe I did it wrong). The second time I ran it, I found where the permissions are, but when I try to change the GROUP to her username (which is the same as her group in the user panel) to set the permission for her account only, it just keeps flashing back to "plugdev" and seemingly won't let me change it for any others.

Based on the options listed, I think you pointed me to the right place, I just need to figure out what I'm doing wrong with it...so time to do a little work on Google. Thanks for the help, I appreciate it.

---

### Post by NineseveN on 2007-11-30
Okay, so I still haven't figured out how to do this. I don't want to go in and screw things up, so I'm hoping a bump will get some help here.

To clarify, I have partitions other than the one Ubuntu is installed on that automatically show up in "Places" and Places>Computer for any new user I create.

I don't want all of these to show up for other user accounts, I only want them to have access to the CD ROM, DVD and the related Ubuntu partitions (their home folder etc...).

Once that is complete, if I could also then designate one particular partition (or a folder on a partition if need be) for them to have access to, that would complete what I want to do.

Can anyone think of what I might do. I'm really new to Ubuntu and Linux, so I'm kinda at a loss. I know how to do it in Windows, but I want to get rid of Windows entirely so that we can both just use Ubuntu on this machine.

Thanks in advance for any help.

---

### Post by lespaul_rentals on 2007-11-30
Okay, I *think* this might work.  **Don't try this until someone else confirms for me.**

What if he made the mount point folder accessible only to the root?  Then he would need the root password to access them.

---

### Post by mgmiller on 2007-11-30
I'm not sure about having the partition invisible, but if you set the permissions of the partition to your ownership only and deny all others all other access, then all they will see is a "locked" folder icon and won't be able to browse it at all.

---

### Post by NineseveN on 2007-11-30
> **mgmiller said:**
> I'm not sure about having the partition invisible, but if you set the permissions of the partition to your ownership only and deny all others all other access, then all they will see is a "locked" folder icon and won't be able to browse it at all.

That would be fine. It's not like I'm trying to hide the existence of the partitions, I just can't have someone esle have easy automatic access to these files if I create a user account for them. I thought maybe I could just have those partitions not mount automatically under other users by editing a config file (fstab?), I'm not trying to prevent intrusion, only accidental discovery and manipulation/deletion/reading without making it too difficult for me to access the folders regularly.

When I try to change the permissions using the method stated in this thread earlier, it shows the owner of those partitions as root and says I cannot change the permissions since I am not the owner. Do I have to actually log in as root or did I screw somehting up on install?

I'm trying not to sound like a total idiot here, I just don't want to hose my data or my system. I hate being new to things, I feel completely lost. It's like, I understand how permissions work on a general level, but actually manipulating them in Ubuntu is a bit of a loss to me.

---

### Post by psusi on 2007-11-30
Either convert to a unix filesystem where you can set permissions, or edit your /etc/fstab and add an entry for the ntfs volume, with the options "uid=youraccountname,umask=700" and all of the files on the partition will be owned by you, and only accessible to you.

---

### Post by NineseveN on 2007-11-30
> **psusi said:**
> Either convert to a unix filesystem where you can set permissions, or edit your /etc/fstab and add an entry for the ntfs volume, with the options "uid=youraccountname,umask=700" and all of the files on the partition will be owned by you, and only accessible to you.

Thanks! Now, one question (I know, I'm being a pain in the ***), but at some point in the next 6 months, I probably will be getting rid of XP totally and thus converting to a unix file system on all partitions, so at that point, I am assuming that I'll have to go back and edit fstab again to change it back, correct? 

I'm going to try this suggestion when I get home. Thanks.

---

### Post by NineseveN on 2007-11-30
> **psusi said:**
> Either convert to a unix filesystem where you can set permissions, or edit your /etc/fstab and add an entry for the ntfs volume, with the options "uid=youraccountname,umask=700" and all of the files on the partition will be owned by you, and only accessible to you.

Okay, I did that in my account and it did the exact opposite, I lost those drives under my user account even though I supplied my username in the line "uid=youraccountname,umask=700".

I'm going to try and edit fstab under her account and put the same line in there. This might just work.

---

### Post by NineseveN on 2007-11-30
> **NineseveN said:**
> Okay, I did that in my account and it did the exact opposite, I lost those drives under my user account even though I supplied my username in the line "uid=youraccountname,umask=700".

I'm going to try and edit fstab under her account and put the same line in there. This might just work.

After I opened fstab, I thought about it and it just seemed really stupid that I would have to log into her account to edit permissions that exclude her...but I did it just to try it. It still made the drives disappear for me. So I changed the uid= to her account name, and that did it. 

So the correct command for me was to enter

**uid=theaccountnameyouwanttoexcludeaccess,umask=700**

after "[COLOR="Red"]defaults[/COLOR]" in fstab for each volume I did not want her to have access to. 

Looks like it worked perfectly. Thanks.

---

