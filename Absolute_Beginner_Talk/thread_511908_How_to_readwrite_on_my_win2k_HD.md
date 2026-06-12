---
title: "How to read/write on my win2k HD?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by imnotryan on 2007-07-28
I have a linux HD and a win2k NTFS HD.  Windows HD is read-only.

I have something I need to save to the windows HD - because that is my filesystem for over 10 years, and I'm not seeing a reason to store photos of friends (etc.) across both hard drives, nor a good reason to have the entire folder on both HD's.

Let's say I want to save a .jpg to my windows HD.... Is this dangerous?  How do I accomplish this, Going root in console still does not allow me to change the windows HD "permissions" to read/write.

BTW, i have ubuntu feisty 7.04.

---

### Post by ddrichardson on 2007-07-28
Look into a package called ntfs-3g in the repository. There's more information [here]("http://www.google.co.uk/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.ntfs-3g.org%2F&ei=MYCrRr2XEZXMwAGDvMD6Aw&usg=AFQjCNHT7HIQm6UGNWFjlEv1HkPFTwMrOg&sig2=3dnMkzNJKUUGIul2nwJyQQ").

---

### Post by cbudden on 2007-07-28
If you just install ntfs-config, it will grab ntfs-3g as well, and you'll have a nice gui program to tick to enable ntfs.

---

