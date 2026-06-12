---
title: "Something similar to a tuneup utility for ubuntu?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2008-02-07
Hey,

I'm after a program for Linux that would work similar to Tuneup Utilities 2008. I ideally like to optimise my system once a week but have gone since my fresh install of 7.10 in October last year, without a optimisation.

If there isn't could someone please give me a list of optimisation commands or tips/tricks?

Thanks,
Kristian.

---

### Post by buebo on 2008-02-07
Generally stuff like this is not needed under any decent operating system.

Luckily for you, your ubuntu box will keep itself optimized, leaving you with more time to spend and less black magic to handle...

---

### Post by kpkeerthi on 2008-02-07
You do not need any 'optimization tools' as there is no 'registry' in linux. But you may choose to [cleanup some left overs]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html") that tend to accumulate over time.

In addition to that,
1. Cleanup apt cache
```
sudo aptitude clean
```

2. Remove nautilus thumbnails that were not used in the last 14 days (or whichever you prefer)
```
find ~/.thumbnails -name *.png -mtime +14 -exec rm '{}' ';' 
```

3. Periodically check ~/.config and see if there is anything left behind by packages you no longer use.

And perhaps put all the above into one shell script and schedule it with a cron.

---

### Post by Dev'olution on 2008-02-07
Are there any anti-virus or firewalls?

---

### Post by JBAlaska on 2008-02-07
Ubuntu ships with iptables (firewall), you may choose to use a graphical frontend to administer the firewall such as firestarter.

Most agree there is no need for a anti-virus in Linux, although you can get Clam or Avast for Linux for free if you feel the need.

And you also do not need a defrag program when using ext3 filesystem.

This is the beauty of Ubuntu!

---

