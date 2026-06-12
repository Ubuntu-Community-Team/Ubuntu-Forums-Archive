---
title: "Evolution email generates folders that can't be deleted."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by bwallum on 2008-01-07
I am being flooded with folders in my Evolution email tree which i can't delete.

For my normal Inbox folder I also get these folders:-
inbox.before_restore_2008-01-07_10.43.28.649732
.
inbox.cmeta.before_restore_2008-01-07_10.43.28.649732
.
inbox.ev-summary.before_restore_2008-01-07_10.43.28.649732
.
inbox.ibex.index.before_restore_2008-01-07_10.43.28.649732

and lots of them too!

I can delete the 'inbox.before_restore_' folders. 
I can't delete the 'cmeta', 'ev-summary', and 'ibex.index' folders.

I have been using Simple Backup and Simple Restore which appear to work normally for all my '/home/' files.

I'm running on AMD64 hardware and Ubuntu AMD64 desktop, set up by clean install and then restoring '/home/' from second hardrive using Simple Restore.

I have tried deleting evolution directories in various orders but no change in effect. I have completely removed and reinstalled evolution to no effect. I have tried restoring the .evolution file on its own to no effect.

Can you help delete the unwanted folders please?

Regards
Bob

---

### Post by Ub1476 on 2008-01-07
Does root acces help?

```
sudo evolution
```

---

### Post by bwallum on 2008-01-07
Hi Ub1476

I muddled around and found the offending folders in:

/home/bob/.evolution/lmail/local/

(anyone following - changing bob to your folder is pretty obvious but for newbies watch out for the period before evolution, its a hidden file, use Ctrl+H to see it)

I then found Edit>Select Pattern after using Places>Home Folder>.evolution...

In the Edit>Select Pattern dialogue I typed in..... [ *before_restore* ] ...ignore square brackets, and sent every nasty one of them to the waste bin!

I don't know if your solution would work because they have all gone now and I can't regenerate them. Thanks for the help anyway.

I just wish i could remember all the little wrinkles I go through!

Kind Regards and Happy New Year 
Bob

---

