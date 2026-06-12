---
title: "Syncing itunes folder onto ubuntu"
date: 2009-04-22
forum: Apple Hardware Users
---

### Post by ironlung on 2009-04-22
I apologize if this thread does not belong here.

I have a macbook pro with all my music. I'd like to be able to sync my macbook pro itunes folder onto my ubuntu machine. What I want to happen is that any changes made on my macbook pro will also be replicated on my ubuntu machine. I was wondering if rsync could do this, and together with cron I could set up a time for this to happen. Would you recommend such a setup or do you have any better suggestions? Thanks.

---

### Post by cyberdork33 on 2009-04-22
> **ironlung said:**
> I apologize if this thread does not belong here.

I have a macbook pro with all my music. I'd like to be able to sync my macbook pro itunes folder onto my ubuntu machine. What I want to happen is that any changes made on my macbook pro will also be replicated on my ubuntu machine. I was wondering if rsync could do this, and together with cron I could set up a time for this to happen. Would you recommend such a setup or do you have any better suggestions? Thanks.
sounds like you are on the right track. setup a network share on your mac, and have your Ubuntu machine sync the files in that share via cron.

---

