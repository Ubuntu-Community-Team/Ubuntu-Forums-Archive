---
title: "Good Backup and Recovery Suggestions"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by user007usa on 2006-12-22
The other day I had an instance where I couldn't to Ubuntu.  What happened was every time I logged in, it dumped me back to the login screen.  So I had to boot from a virtual terminal to fix this (it was because my system partition was full).  I had to basically go into windows in order to research the problem in order to fix it.

Now, I do not use my windows anymore really.  I just keep it around in case something like this happens -- so I can use it and at least get work done.  But I'd love to just delete it entirely and format the partition for linux if I can.  My problem is I am not sure how to backup everything I need, nor do I have knowledge enough to be confident that I could recover from a ubuntu crash (I have 15 years of experience with Windows, three months with Linux).  So if someone(s) would be kind enough to help me plan and know what I need to know, I'd be grateful.

(I just realized I could have used the LiveCD to get on the internet, whoops)

1. In windows there is a "Repair installation" where Windows will simply overwrite the windows files in order to try to get the system bootable again.  This will leave all or most of your files intact.  What is the equivelent in Ubuntu?

2. Say my MBR gets corrupted, but nothing else.  What command(s) can I run in a pinch to rewrite the MBR?

3.  I use GRub.  Which files should I back up here to be able to restore?  And for that matter which Gnome, X, and KDE files should I make sure to have backed up on an external CD as well?

4. Windows has a recovery console where you can do basic fixes and this is what you work with.  vWhat does Ubuntu have like this, and what should I know?

5. Say I have to boot from a LiveCD and mount my existing partition or another partition manually because of corrupted system files.  What commands would I use or at least which commands should I research? 

6. Anything else that you think may be helpful?

---

### Post by aysiu on 2006-12-22
The things you should investigate are recovery mode, ddrescue, and PartImage.

---

### Post by Sef on 2006-12-22
> 6. Anything else that you think may be helpful?
Reply With Quote

Have a Knoppix Live CD handy.   Among other things, you can use it to pull off any files that you need to if you computer can't boot up.

---

