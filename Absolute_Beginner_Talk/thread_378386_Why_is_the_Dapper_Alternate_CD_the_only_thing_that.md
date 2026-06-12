---
title: "Why is the Dapper Alternate CD the only thing that works?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Starks on 2007-03-07
I have an Inspiron 640m/E1405 that is being very stubborn. It won't let me install Edgy or Fawn and only allows me to install Dapper Alternate in text mode.

When I'm not using the Dapper Alternate CD and I try Edgy Alt or Fawn Alt, the installation won't complete due to the partitioner not functioning properly or the X Server not detecting my 1440x900 display.

Is there a reason why I can't install anything other than Dapper or upgrade to a newer version?

---

### Post by dannyboy79 on 2007-03-07
well isn't there also alt install cd's for edgy and fiesty? I had to use the alt install of dapper on my laptop as well. it's a graphic issue.

---

### Post by melancholeric on 2007-03-07
He said he tried edgy and feisty alt cd's too.

Since you can install dapper, can you upgrade from there to to edgy with apt ?

---

### Post by Starks on 2007-03-07
> **melancholeric said:**
> He said he tried edgy and feisty alt cd's too.

Since you can install dapper, can you upgrade from there to to edgy with apt ?

How do I do that? I was under the impression that a Dapper to Edgy upgrade was achievable through CD.

---

### Post by dannyboy79 on 2007-03-07
if you're using the alt cd, than you shouldn't be having any issues with your x-server as it's all text based? so I am not sure what you mean. what type of failures are you getting using the alt cd's with edgy or fiesty??? can you be more specific?

---

### Post by melancholeric on 2007-03-07
> **Starks said:**
> How do I do that? I was under the impression that a Dapper to Edgy upgrade was achievable through CD.

sudo nano /etc/apt/sources.list

change all 'dapper' entries to 'edgy' && save and close, then

sudo apt-get update
sudo apt-get dist-upgrade

I'm sure there's another way too but can't remember the details right now.

But you may want to see if anyone can diagnose and fix the actual problem before doing this.  Fresh install might be easier than upgrading.

---

### Post by buuntuu! on 2007-03-07
upgrading is quite simple, really.
follow the [howto]("https://help.ubuntu.com/community/EdgyUpgrades")
backup your data though!

---

