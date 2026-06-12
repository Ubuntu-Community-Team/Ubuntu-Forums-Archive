---
title: "User right problem while mounting MacOS partition"
date: 2007-01-12
forum: Apple PPC Users
---

### Post by el-sio on 2007-01-12
I am trying to access my personal folder on my  MacOS partition, but whatever option I put in my fstab, the directory is mounted with those rights :

```

el-sio@rivendell:/media/macOS/Users/el_sio$ ls -la | grep drw
drwxr-xr-x 1  501 501    36 2007-01-12 11:55 .
drwxrwxr-t 1 root  80     6 2006-03-17 09:56 ..
drwxr-xr-x 1  501 501     3 2006-02-02 02:54 Applications
drwx------ 1  501 501    18 2007-01-08 11:59 Desktop
drwx------ 1  501 501    44 2006-08-05 20:29 Documents
drwxr-xr-x 1  501 501     3 2005-06-18 01:28 .emacs.d
drwxr-xr-x 1  501 501     3 2005-01-10 13:09 Gmail HD icon
drwx------ 1  501 501    48 2006-05-24 10:12 Library
drwx------ 1  501 501     7 2006-06-08 10:00 Movies
drwxr-xr-x 1  501 501     3 2006-06-08 10:09 .mplayer
drwx------ 1  501 501     5 2006-04-16 07:39 Music
drwxrwxrwx 1  501 501    18 2006-10-09 01:03 Pictures
drwxr-xr-x 1  501 501     6 2006-10-20 13:30 Public
drwxr-xr-x 1  501 501     6 2005-07-06 01:31 Sites

```

Strangely I can access some of them (like the pictures folders) but the rest is not even browsable...

I tried to mount it with uid=0,gid=0,umask=0 option but it did'nt changed a thing.
I tried to add the user 501 to my group and to add myself in group 501 but of course neither this group nor user exist on my system...

I have re-enabled journalizing on my MAcOS partition, so maybe the problem comes from here, but since I don't need writing in it but just want to read files (and of course without being root :D) I am looking for a solution that doesn't require Journal disabling...

Any Idea ?

(and please tell me if it is just not possible without disabling the journal...)

---

### Post by didg on 2007-01-12
hfsplus volumes have both unix like permissions (owner, group and mode) and pre OSX inherited directories permission.  With linux hfsplus driver the mount option uid is only for mapping pre OSX perm.

A partial workaround:
- mount with uid=your id, help if you have pre OSX perms on the volume.
- create a group 501 macusers and put yourself in it, but It won't enable you to browse stuff like
drwx------ 1  501 501     7 2006-06-08 10:00 Movies

For these folders you have to change in OSX  their permissions to 
drwxr-x--- 501 501

---

