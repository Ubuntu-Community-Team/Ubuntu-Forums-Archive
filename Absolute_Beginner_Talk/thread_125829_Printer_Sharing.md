---
title: "Printer Sharing"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by tblehr on 2006-02-04
I have looked through countless numbers of threads on this subject and am now just completely overwhelmed.  Samba, CUPS, I just don't get it I guess.  I looked through the "unofficial startup guide" for Samba and that told me nothing....

Anyway, I have a HP PSC 1315 on my Ubuntu machine and works great from there.  My brother has WinXP and wants to use the printer too.  I've got the internet shared between the two of the machines and now I just want to share the printer also.  I just need to know how to do this. :)

Any help would be greatly appreciated! :D

---

### Post by moephan on 2006-02-05
It's not as hard as it sounds. Basically, you hook the computer up to your Ubuntu desktop (which you already did), then you install samba and create a smb.conf file that tells your ubuntu computer to share printers, then you go to the windows machines and tell them to use the printer. I did this for the first time a few weeks ago and it was easier then I thought it would be. Here's a thread that has the smb.conf file that I used:

[http://ubuntuforums.org/showthread.php?t=119486](http://ubuntuforums.org/showthread.php?t=119486)

It's slgihtly more complicated because we also wanted to share home folders, but you can just skip that part.

Cheers, Rick

---

### Post by tblehr on 2006-02-05
Thanks for the reply Rick, i'll give it a shot! :)
~Terrence~

---

### Post by tblehr on 2006-02-05
Ok, I finally gave up!  So I hooked the printer to the WinXP machine, since I don't print much anyway.  Would it be easier to share the printer from the XP machine to the Ubuntu machine?  If so, how could I do that?

Thanks again for everyone's advise! :)

~Terrence~

---

