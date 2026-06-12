---
title: "problem with mount freenas smb/cifs/usf share on client"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by CallMeDerek on 2007-08-08
I am trying to mount a smb share hosted on freenas in kubuntu.

The kbrower sees it and i can do all the read writes needed, however i am finding backup software like "keep" will not allow me to select the share and write to it.  My thought was to mount the share on the client to see if it resolved the issue but no derivation of the mount command seems to be working.

The share is hosted by freenas, cifs, formated as usf
i have created the directory in my mnt directory locally

using:

sudo mount //server/share/folder  /mnt/folder/

Returns:
mount: wrong fs type, bad option, bad superblock on //server/share/folder,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 

I have tried several variations and switches all lead with the error wrong fs type bad superblock

any advice on what i am doing wrong?

---

