---
title: "&quot;too many session files in /var/tmp&quot;"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by darthvivi on 2006-09-04
I'm not using Ubuntu right now but I know I'll get a reply here 5 times faster than any other Linux forum, so I wanted to ask here. (If that's off-topic and unwanted, I'm really sorry and won't do so in the future)

I just installed Slackware. I'm getting tons of errors and I need to edit /etc/fstab, which I think will fix it. However, when I type "vi /etc/fstab" it says, "too many session files in /var/tmp"

Is there some way to fix that?

Edit: If there is a good general Linux forum, could someone point me to it? I haven't been able to find one.

---

### Post by taurus on 2006-09-04
Make sure you are root when you run that command, vi /etc/fstab!  And if you wish, you can delete everything in /var/tmp since it's a place where temp files are stored.

---

### Post by poeyuan on 2008-04-14
in my case, the /var/tmp directory has much files in it.
it make the inode numbers 100% used

you can use "df -i" to check your parttion 's inodes.

this is my df -i

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/cciss/c0d0p1     768544  768544       0  100% /

find and delete the small files can solute it.

Sorry about my poor english . ^_^

---

