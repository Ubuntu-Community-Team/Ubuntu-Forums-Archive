---
title: "Wonky system time on a PPC Mac mini"
date: 2006-08-02
forum: Apple PPC Users
---

### Post by leaded on 2006-08-02
I've posted about this before but as I learn more about the problem my questions have changed. I'm running Dapper, updated every night, on a 1.42GHz PPC Mac mini with 1GB RAM. It's only function is to use Rsnapshot every night for about 12 development servers and store the data on a 1TB Firewire drive. Ever since I installed Dapper, the system time has always been off. Through the help of this support forum, I found that I can run ntpdate as a cronjob and fix the time.

I was originally running it once a day. But it would be off my almost 4 minutes. I ran it once every four hours but didn't feel comfortable either. Now I run it once an hour, and each time it corrects it by 10 seconds.

Why does this happen? What causes the clock to "tick" slower than normal? Is it the system battery? A co-worker used OS X on it recently and never mentioned any weird time problems. 

I suspect that Ubuntu is not running the CPU at the right speed and must be a few MHz off, which is causing the system time to run slow. 

I found some guides online that mentioned syncing the system time to the hardware clock, but I get errors about the device not being there when I try that.

Not that it's a huge problem, since I'm just using it to copy files with rsync, but it does make me uneasy. Is there anyway I can fix it without having to go back to OS X? (I prefer Ubuntu for automatic updates for 5 years! OS X updates must be done at the console, yuck)

Thanks!

---

### Post by chasisaac on 2006-08-04
> **leaded said:**
> I
I was originally running it once a day. But it would be off my almost 4 minutes. I ran it once every four hours but didn't feel comfortable either. Now I run it once an hour, and each time it corrects it by 10 seconds.


Just wondering as this may seem obvious. . . have you set date and time preferances to set with internet clock?

---

### Post by leaded on 2006-08-04
Yeah. I installed ubuntu-desktop solely for that purpose. It was the only way I could reset the time until someone told me about "ntpdate"

---

