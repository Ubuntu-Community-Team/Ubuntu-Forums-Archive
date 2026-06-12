---
title: "&quot;Status&quot; role in upgrade to Edgy"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Calculator on 2006-10-28
Please let me know the role of:
1) the "Status" text that requires editing when upgrading to Edgy; and
2) nano?

I have edited out all references to "Courier" due to upgrade problems to Edgy, but I am a little concerned that I may have edited out some important information.  

To overcome upgrade problems I followed this guide from [http://www.ubuntuforums.org/showthread.php?t=285466&highlight=courier:](http://www.ubuntuforums.org/showthread.php?t=285466&highlight=courier:)

1. backup /var/lib/dpkg/status to a safe location
2. remove all courier entries from /var/lib/dpkg/status (nano it, search=ctrl-w)
3. sudo apt-get upgrade
4. sudo apt-get install courier-imap

Thanks

---

