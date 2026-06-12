---
title: "grsync config help..."
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-10-11
OK so last night I finally got smb4k configured and mounted my network drive.
Now I am trying to backup my home folder to the server with grsync. my problem is that it also is syncing some folders that are network like smbdk which houses my music and videos.  since all of my docs and stuff are on the server I only need to backup my ubuntu specific configuration files.  how do I become selective about which files sync and when?  I would like to autorun this once daily on the first boot.

---

### Post by julian67 on 2007-10-11
Grsync is just a nice gui front for rsync and Grsync doesn't have all the rsync options available *but *if you click on the Advanced tab you'll see a box titled Additional options:

In this box you can add rsync command line options. You can specify folders or filetypes to exclude, or even better make a text file containing a list of the exclusions and point rsync to that list. See the rsync man page for details.

---

### Post by mramsey on 2007-10-11
> **julian67 said:**
> Grsync is just a nice gui front for rsync and Grsync doesn't have all the rsync options available *but *if you click on the Advanced tab you'll see a box titled Additional options:

In this box you can add rsync command line options. You can specify folders or filetypes to exclude, or even better make a text file containing a list of the exclusions and point rsync to that list. See the rsync man page for details.

Great...I knew there had to be more to it. thanks j

---

