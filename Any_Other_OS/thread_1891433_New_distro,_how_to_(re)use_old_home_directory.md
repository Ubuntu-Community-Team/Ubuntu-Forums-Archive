---
title: "New distro, how to (re)use old home directory"
date: 2011-12-05
forum: Any Other OS
---

### Post by InkyDinky on 2011-12-05
I'm playing with the Arch distro and want to be able to access files I have saved in my old users home directory.
What is the best way to do this.
Could I create a new user with the name of my old username? Will this recreate the user directory, wiping out what I all ready had there?
Should I use usermod -d to change the new users home directory? Or will I have a whole bunch of permissions problems still?
Should I just move the contents to my new user's home directory and run a recursive chown?
Is there another way?
I imagine that more than one method works, but what is the easiest (if there is such a thing)?
I'm not a noob, just antsy about possibly wiping out my old home directory, as it has plenty I want to keep.
Thanks,
Nick

---

### Post by Elfy on 2011-12-05
Thread moved to Other OS/Distro Talk.

---

### Post by jjex22 on 2011-12-05
Hi there! 

there are a couple of ways to do this as I'm sure you know; 

1) as if you were upgrading your distro-
-mount the /home partition at /mnt
-copy the data from arch's home to the home partition
-unmount
-rename arch's home to home_old
-create /home
-mount home partition at /home
-edit fstab to auto mount home partition.

2) add user - same as above, but you use a different user name to have 2 sets of documents - this is good if you're likely to have distro specific config files in your /home partition. you can always symlink between the directories you want shared - documents etc.

3) Symlinking - most basic; edit fstab to auto mount the /home partion and set up symlinks between directories so that arch's home contains symlinks called Downloads that link to the home partition's Downloads directory - though you need to rename arch home's directories to /Downloads_old etc.

I've not used 3) so I can't attest to how useful it is - it was recommended to me when I started out. Personally I just don't use a home partition - I boot multiple OS's, so I have a data partition formatted as FAT32, containing folders such as Music, Downloads, Documents, etc. I just configure each OS to auto mount that partition and then set the programs that those OS's use to use the folders on the data partition, and in some instances symlink to them. This is useful to me, but it does limit the scope for /home directory recovery - for me this isn't an issue as I create a complete HDD image once a week for back up, but If you don't you'll have to remember to take into account backing up both the data and / partitions if you used this method.

---

### Post by InkyDinky on 2011-12-05
I appreciate your help jjex22.
I suppose I wasn't completely clear.
I didn't have my old home directory on a different drive.
I think for the time being I'll copy individual files or directories from my old user profile as I need them.
I guess if by copying I don't obtain the correct permissions that I'll just sudo to set permissions correctly.
However to answer my 1st question 'man useradd' (I don't know why I didn't think to look here first) sheds light that the directory will not be destroyed, and that with the -i option I can even obtain ownership of that old home directory. I realize that I'll use old config files but this may not be such a bad thing.

Hmm Symlinking. I don't know much about that and should read up on it.

---

