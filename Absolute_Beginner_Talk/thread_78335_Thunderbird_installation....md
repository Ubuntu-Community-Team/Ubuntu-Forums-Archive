---
title: "Thunderbird installation..."
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by pommattski on 2005-10-18
Hi, 

I have successfully installed Breezy, dual-booting with WinXP.  I have been using Thunderbird for a while in Windows, and plan to share the mail/profile with Ubuntu.

Should I or should I not remove Evolution before or after installing Thunderbird?  
I will not use it, but I came accross an old thread here that seemed to indicate that removing it may cause problems..
... I suppose I could just remove it from the Application menu...

May not be important, but thought I'd check.

If anyone has any advice/tips on the sharing of profiles between the 2 OSs, that'd be appreciated.  I have moved my Win Thunderbird profile to a FAT32 partition already and got it working in Windows.

Cheers,
Matt.

---

### Post by bluefrog on 2005-10-18
leave evolution. won't hurt

if your thunderbird profile is on FAT32 then you can read/wrtite from linux. Make a symlink for this in your ./thunderbird folder in linux. Like this you will have the same info in both linux and windows

---

### Post by pommattski on 2005-10-18
Thanks bluefrog, 

I'll leave Evolution for now... 

Re. the symlink - I just did that (actually linked to the profile folder itself)... Testing it now... All the mail is visible in both OSs and I can send and receive mail OK.
The only minor 'strangeness' I've noticed is that a couple of my mail folder's names have changed... but that *may* have been because the names contained slashes ("/")... 

Cool.  I now have fewer reasons to boot into Windows.

Cheers,
Matt.

---

