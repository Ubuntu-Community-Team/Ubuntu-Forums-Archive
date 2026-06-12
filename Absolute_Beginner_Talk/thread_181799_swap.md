---
title: "swap"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-05-24
I posted once before about this.  I got some great answers from people.

My /var partition is full.  My question is this.

what do you think about swap partition vs a swap file?

I need more space on /var and /var is right next to my swap space.  I could delete my swap space in favor of a file and maybe add the swap space to my /var partition.

note.  I couldn't even begin to have this conversation on windows.  Lousy junk OS.  My swap partition is BEFORE my /var.  Would that be a problem?  Could I mount /var to one partition and /var/www to a different partition?

Just asking?  thanks.  My partition table is a mess.

Does anyone know of a way to use 'tar' to backup a partition vs backing up the whole drive?  How do I use 'tar' and NOT get any errors.  I don't want to have my backup file not work when I reload the partition.

---

### Post by Sef on 2006-05-24
If you have at least 1 GB, you generally do not need swap, unless you are doing movie editing or heavy gaming.  Maybe update your memory and free up the space.

---

### Post by tonyr on 2006-05-24
Following what **Sef** said, look at **/var/cache/apt/archives**, and **/var/log**.
Do you really want to keep all that stuff forever?

---

### Post by Jucato on 2006-05-24
Keeping a swap partition is generally useful. You never know when you're going to need it. Unless of course you have a whooping amount of RAM. 

AFAIK, swap/virtual memory is best placed on a separation partition rather on the same partition as the OS. I think it has something to do with how the hard drive heads move/read data. I'm not 100% sure if such is the current case with today's hard drive or with Linux.

/var, on the other hand, can easily be reduced in size by removing some unnecessary files like what tonyr said. specially the /apt/cache. You'd be surprised at the amount of space you could clean up by removing the downloaded packages.

---

### Post by morequarky on 2006-05-24
I deleted those files.  Got me some room back. Thanks. I still need to add space.

I have two swap partitions because I thought my original partition was too small.  I see now that I can use a small swap partition and then make a swap file if I need to for short term issues.  That would free up nearly 900MB for me.  In my sig you will see that I have 512MB ram and to be honest I rarely use more then 230 of it. On those very rare situations where I need more then 500MB of swap space I can just add a swap file.

Would this work in backing up ONLY /var or /home or any other partition I have?
"tar cvpwjf /home/varbackup.tar.bz2 /var"

Thanks.

---

