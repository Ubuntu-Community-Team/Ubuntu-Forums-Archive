---
title: "How do I do a clean install kernal upgrade?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by nu2this on 2006-09-28
I'm waiting for Edgy & would like to upgrade. I've read in here that a clean install is best. So how do I?
1)place my present home on a separate partion?
2)do the clean install,then put in my old home?
3)after the clean install & replacing home what if any programs will need re-installing(realplayer,totem, wine,etc)?
Almost forgot I'm dual booted.

---

### Post by Jussi Kukkonen on 2006-09-28
I'm guessing you currently do not have a /home-partition? In that case you should copy your home directory (and other important data) onto another partition.

What you should probably do (for possible future re-installs) is to create a /home-partition during the install -- that way you don't have to do all this copying during the next Ubuntu install. This of course assumes you have enough space: multiple partitions waste a little more space as you need to have some free space on root-partition too.

Whether you created a /home-partition or not, after the install you just copy your files to your new home directory. There may be ownership issues, so check who owns the files at this point...

You will of course need to re-install all software if you do a clean install.

---

