---
title: "Network Hard Drive--can't find it from Hotmail or Yahoo mail"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by tjoel99 on 2007-06-10
I keep my documents on a network hard drive that is mounted in Places.  All is great except when I'm in Hotmail or Yahoo mail and try to access it to send an attachment, it's not visible and I don't know how to find it.  Help please!

---

### Post by H3g3m0n on 2007-06-10
The easiest way is to go Bookmarks>+Add Bookmark in nautilus when browsing the drive to make it show up in the dialog box that is used for sending attachments. Its possible that Firefox doesn't support the network browsing uri's though and while you might beable to locate the files you could get an error (try it and see).

If it doesn't work you could also look at mounting it on the local filesystem with CIFS/Samba (assuming your using smb shares) if you are prepared to do something with a bit more difficulty. Its similar to the Map network drive option in windows but I don't think there is an easy GUI tool for setting it up. There should be plenty of guides around if you search for CIFS and samba.

---

### Post by tjoel99 on 2007-06-10
Thank you.  I bookmarked it in Nautilus and I think I mounted it in Samba.  Here is what I did.  I drove to it in Nautilus in the Network area.  I right clicked on it and selected "Connect to Server."  It now shows up with a little "SMB" on it.  When I right click on it now, it gives me the option to unmount.  So I assume it is mounted.

However it still doesn't show up ... not just in Firefox but now I see that it also doesn't show up in any picture editor.    What should I do next?  Thank you.

---

### Post by H3g3m0n on 2007-06-11
That isn't actually mounting the folder locally, I think its just adding it to nautilus virtual file system in the "Computer" section, so not much different to a bookmark. I have checked bookmarking folders and they don't work in Firefox unfortunately.

You need to add a line like:
```
//server/share /mnt/yourmountpoint cifs credentials=/etc/smbcredentials,file_mode=0777,dir_mode=0777 0 0
```
to /etc/fstab

make the /mnt/yourmountpoint directory

And make /etc/smbcredentials with:
```
username=youusername
password=yourpassword
```

Then type 'mount /mnt/yourmountpoint'

From memory you also need to install a package to get samba working, I think 'apt-get install samba' will have everything needed, although it includes the whole samba server rather than just the needed bit.

Theres heaps of other guides on getting samba working, and I think the permissions in my fstab might be worng so it might be worth looking around.

There its a gnome-firefox-support package thats installed by default thats supposed to allow for smb:// style uris but it only seem to allow browsing them, not having firefox upload files from them.

---

