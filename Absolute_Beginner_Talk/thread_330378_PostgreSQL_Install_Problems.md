---
title: "PostgreSQL Install Problems"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by bananabob on 2007-01-03
I have struggled for days, and days, to try and get PostgreSQL to work, so I want to share this post with anyone having the same trouble finding help in the Ubuntu Forums.

I had been installing it using Synaptic, and I had a whole host of problems. I could not find where initdb was to initialise the database. Nor would would Postmaster start up.

To cut a long story short. I turned to Google  and came up with this [How To Install PostgreSQL For Ubuntu]("http://hocuspok.us/journal/postgresql-on-ubuntu-linux-how-to-updated"). I removed the PostgreSQL install using Synaptic's "Mark for complete removal" option. Then I made sure that various odd files had been deleted. Once sure that everything was clean. I installed PostgreSQL using the sudo apt-get install postgresql-8.1 postgresql-client-8.1.

I didn't bother with the pgadmin stuff as I had already installed that with Synaptic, and found that it had installed, and there was a menu entry for it in Applications>System Tools. So I skipped down to the sections on editing the configuration files postgresql.conf and pg_hba.conf.

Then I tried to start Postmaster, and voila! It worked. It also worked over a reboot, which made me a very happy man.

---

### Post by jan on 2007-02-18
Hey,

I run 6.10 and cant locate pg_hba.conf anywhere on the system. Using 8.1.

---

### Post by bananabob on 2007-02-18
go to a terminal and type locate pg_hba.conf you should see the location. If it doesn't giove you one, you havn't got a file of that name.

---

