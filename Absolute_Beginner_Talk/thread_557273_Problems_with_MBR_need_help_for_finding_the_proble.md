---
title: "Problems with MBR: need help for finding the problem and fixing it"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by NorthernPaladin on 2007-09-22
There is something wrong in my MBR. Here is the story: first time I tried ubuntu was in the beginning of this year, tried it fo about 1 month, did not had succes it and switched back to windows. Then I found out that my problems were not because of ubuntu, but because my graphics card was a bit broken(allready have a new one). Then, about a month or two ago I decided to give ubuntu a new try, and it works(mostly). Now I need to switch back to windows because I have not had success in getting some programs and games running. I tried to install windows, and the install went first fine. But when came the step where it had to boot from the harddrive first time, it froze. Installed windows again, same thing. Then I installed ubuntu again, and I saw something interesting: I had formatted the windows partition, but grub gave me the choice to start windows.Interesting. I then tried to install a dual boot to test if that would help. Nope, windows froze again in the same point. Then I tried the recovery console and the fixmbr command. It said something that "your mbr is either invalid or modified version. fixing mbr might destroy all data on the harddrive. Continue?" I pressed yes and it said that new mbr was successfully wrote. Tried to boot to windows, froze again in the same point. Tried the fixmbr again, and again it said the same warning, and again I pressed yes, and again it said that it was successful. Nope, didn't work, froze again in the same point. Then I tried to boot into ubuntu, it worked. So I'm guessing that the fixmbr did nothing. So I need an alternative. And one thing that bugs me is that grub says that I have windows installed, which I don`t have. Does anybody be of any help?
Thank you all in advance, sorry if this post seems long but I wanted to give all info I had.

---

### Post by logos34 on 2007-09-22
What partition did you install windows on?  First, second...?

It does seem odd that grub would show windows after it had been formatted.  (unless the bootsector still contains windows data)

---

