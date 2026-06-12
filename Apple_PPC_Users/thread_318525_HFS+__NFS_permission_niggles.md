---
title: "HFS+ / NFS permission niggles"
date: 2006-12-14
forum: Apple PPC Users
---

### Post by calum on 2006-12-14
I have an HFS+ partition on an external disk connected to an x86 box running Edgy.  That partition (a backup of my Powerbook's hard disk) is mounted on the Edgy box, and shared on my LAN via NFS.  I'm hitting some permissions problems, though.

If I mount the NFS share on my Powerbook from my own account ('calum', uid 501, no admin privileges), and do ls -l in its root directory, I see (as expected):

drwxrwxr-x   1 root  admin       41 Dec  4 10:50 Applications
drwxr-xr-x   1 root  admin       16 Dec  1 22:29 Applications (Mac OS 9)
drwxr-xr-x   1 root  admin        2 Dec  2 14:53 Desktop Folder
drwxr-xr-x   1 root  admin        4 Dec  2 14:53 Developer
drwxrwxr-t   1 root  admin       55 Dec  3 21:44 Library

etc., and I can happily list the files in any of those folders.

Then when I cd into Users/calum, I see (also as expected):

drwx------   1 calum  calum       4 Mar 18  2006 Applications
drwx------   1 calum  calum      15 Dec  4 17:18 Desktop
drwx------   1 calum  calum      19 Nov  8 23:55 Documents
drwx------   1 calum  calum      12 Dec  4 13:07 Downloads

etc.  However, although I'm shown as the owner of the directories, an 'ls' of those directories returns nothing.  Same in the Finder.  I can see the files just fine on the Linux box, when logged into that as a user with uid 501.

I've confirmed that the owner id on the folders on the external drive really is 501, rather than (say) 99.  The only slight complication, perhaps, is that the uid of the 'calum' account on the Linux box is 115949 (deliberately) rather than 501.  Would that make a difference?  If not, what am I missing?

FWIW, the /etc/exports file on the Linux box is simply:

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/media/LinuxBackup
/media/MacBackup

i.e. no additional parameters set, just the defaults.

---

