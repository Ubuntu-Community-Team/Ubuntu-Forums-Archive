---
title: "Thunderbird Question"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by jsimmons on 2005-06-27
I installed Thunderbird, but I want to import the old settings and folders and stuff from a mounted Windows partition.  Is this possible?

---

### Post by apollo2011 on 2005-06-27
Yes, believe it or not this is possible and there is a HOWTO on it.  The only catch is that the Windows partition has to be FAT because NTFS can't be written to.

Here is the link to the HOWTO:
[http://www.texturizer.net/thunderbird/share_mail.html](http://www.texturizer.net/thunderbird/share_mail.html)

---

### Post by aysiu on 2005-06-27
[QUOTE=jsimmons]I installed Thunderbird, but I want to import the old settings and folders and stuff from a mounted Windows partition.  Is this possible?[/QUOTE]

Yes, quite possible and not that difficult. So, in Windows, your Thunderbird settings are stored in a folder. Likewise, in Linux, your Thunderbird settings are also stored in a folder. The basic gist is that you copy the settings from one folder to the other folder.

In Windows, the folder is probably at C:\Documents and Settings\*your username*\Application Data\Thunderbird

Please note: the folder "Application Data" is a hidden folder. You'll have to go to folder options and check the "show hidden files and folders" checkbox in order to see it.

In Linux, the folder is probably /home/*your username*/.mozilla-thunderbird
.mozilla-thunderbird is a hidden folder as well. You can view it by selecting "view" and "show hidden files."

If you install Thunderbird straight from Mozilla and not through apt-get/Synaptic, the folder may be called .thunderbird instead of .mozilla-thunderbird.

Good luck.

---

