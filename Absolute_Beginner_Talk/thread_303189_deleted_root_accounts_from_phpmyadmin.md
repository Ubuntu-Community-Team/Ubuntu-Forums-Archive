---
title: "deleted root accounts from phpmyadmin"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by BrutalEntropy on 2006-11-19
OK I'm an idiot. I'm running 6.10 server, and I will admit I'm a bit of a noob.

I deleted the root accounts from phpmyadmin, and I'd very much like to get them back.

I tried using apt-get remove to uninstall phpmyadmin... no go.

Thanks in advance...

---

### Post by project46@cia.com on 2006-12-13
Hi I did the same thing myself last week. I had never wrote a linux how to before as im new to linux myself but, Try this. (Note this will delete your mysql database)

Delete all files in /var/lib/mysql
including any folders, I used the rm and rmdir commands

Now run dpkg-reconfigure mysql-server-5.0

This will do its magic and detect that the database needs to be remade etc etc. making the 2 root users accounts for you.

Now it will ask you for root passwords etc, just pressed enter with no password, once this is completed its work, you should beable to login with phpmyadmin again :) 127.0.0.1/phpmyadmin

Good Luck

---

### Post by nrune on 2007-04-08
Thank you!  You have saved me endless nights of frustration

---

