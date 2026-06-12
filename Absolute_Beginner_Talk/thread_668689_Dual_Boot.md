---
title: "Dual Boot"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Jphenow on 2008-01-15
So i got my new computer and installed kubuntu first because I figured it would be better due to the fact that i can partition it easily, after a few days of off and on setup and configuration I decided to install XP pro for purposes that I require, I now have it installed and ready to go but I found I cannot get into kubuntu now because the boot loader, it appears, must be installed after windows rather than before.. Are there anyways of changing this? I'd rather like to avoid a complete new install of kubuntu, I'm getting used to it and quicker at it but that doesn't mean I love the repetition.

I just want GRUB workin!! =)

thanks in advance!!

---

### Post by Joeb454 on 2008-01-15
I think you can boot into a LiveCD environment and install GRUB from there, though I'm not sure how.

Also have you tried searching Google for Super GRUB Disc?

---

### Post by tstack77 on 2008-01-15
Funny, just had this problem yesterday. Check here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Sef on 2008-01-15
Check out [Super GRUB Boot Disk]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by c0met on 2008-01-15
The below link is a step-by-step guide to setting up GRUB following the installing of Windows XP after Ubuntu has been installed. I have found the site very useful.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

---

### Post by CCNA_student on 2008-01-15
These are the instructions I used(I currently have triple boot), [URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirec
t=RestoreGrub"]https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub[/URL]
I hope that this works for you.

         Sin Cere,

         CCNA

---

### Post by Jphenow on 2008-01-15
Thanks a lot all!! I'll give these a shot!

---

### Post by Jphenow on 2008-01-15
okay i saw all of those, and i can and am willing to do them, but also i was rumaging around windows settings, i went into cntrl panel; system; startup and it shows a file containg this..

> [boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


---

### Post by Tiamats_Chosen on 2008-01-16
i have a work computer i am installing xubuntu 7.10 on right now.  it has 2 physical HD in it. main harddrive is set up to work specifications wiht windows xp on it now.  the 2nd HD is where i am intstalling linux. will grub setup be any different or would it give me access to the separate HD automatically.

---

### Post by Jphenow on 2008-01-16
Hey so I clicked the ubuntu wiki on fixing windows to work, i get to select my drive then it still boots linux!! anyone got any clues or ideas??

---

