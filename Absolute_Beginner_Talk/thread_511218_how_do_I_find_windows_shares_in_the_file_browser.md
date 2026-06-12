---
title: "how do I find windows shares in the file browser"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by HugoRune on 2007-07-27
Two questions:

1)
I am trying ot access file shares on windows pcs in a home network. 

I can ping the other pc, but places/network/windows network remains totally empty. Accessing the shares from another windows pc works without problems.

How can I display all available pcs and their shares in the file browser?

2)
What am I doing wrong? 

I spend the last hours searching for some documentation about this seemiingly simple problem. Google did not find anything even remotely useful, neither did the ubuntu "system/help and support".
I spend an hour on #ubuntu, but noone seemed to know any solution. someone finally gave me the hint to search "for SAMBA network in the ubuntu wiki", which got me a at least little bit further, and from there I gatheredthat I am supposed to install a package called samba first.
The last I tried was executiong the instructions from this tutorial [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) but I seem to be missing some of the settings that I am supposed to set there (the ones under "Windows Networking")

I would not be so annoyed by this if this would not happen the same way for every second thing that I try to do. Anything involves long fruitless searches for a solution, is this really supposed to work this way?
Am I missing something esential? What am I doing wrong?

---

### Post by BlueNoteExpress on 2007-07-27
[This thread]("http://ubuntuforums.org/showthread.php?t=202605") helped me get file sharing working between Ubuntu and Windows XP.  I still have a couple of strange issues I asked about in another thread here (unfortunately, I didn't get any real answers), but that thread did get it working.  So, follow the guide I linked to and see if that helps you at all.

---

### Post by HugoRune on 2007-07-27
UPDATE!
it suddenly works.
I do not know what caused this, maybe the installation of the samba package, in conjunction with some of the things I tried afterwards.

Well, I am happy that it works now, but I still do not get it. how am I supposed to figure out this stuff?

---

### Post by HugoRune on 2007-07-27
Thanks BlueNoteExpress, the guide is a good start.

It seems like the magic word to unlock this problem was "samba"

---

### Post by BlueNoteExpress on 2007-07-27
You're welcome.  I'm glad it's working for you now.

---

