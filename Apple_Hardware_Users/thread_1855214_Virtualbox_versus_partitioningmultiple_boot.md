---
title: "Virtualbox versus partitioning/multiple boot"
date: 2011-10-05
forum: Apple Hardware Users
---

### Post by tim042849 on 2011-10-05
I have a 2011 mac mini with 8 Gbs of RAM. My preference for
ubuntu would be an LTS - thus I am currently using lucid on
my PC. I would welcome comments on what sort of performance
I might expect if I install ubuntu through **virtualbox**.
Certainly it would be handy to have the two OS's coexisting at
the same time, but might I expect slower performance as opposed
to partitioning and dual-booting? Or might there be any other
issues?

Links to discussions and other resources are also invited.
thanks
tim

---

### Post by dpny on 2011-10-05
I run both VirtualBox and Parallels on a Mac Pro with Linux and Windows guests. While Parallels is faster, and has more extensive settings for VRAM, the performance of VirtualBox is just fine. The only issue you might run into is RAM. Depending on 1) your typical RAM usage with the host Os  and 2) what you want to do with your guest OS, 8 GB may not be enough to give both your host Linux install and your guest Linux install enough breathing room.

The only issues I have found are when the hosted OS needed direct access to hardware, like games or CAD/3D programs. FOr more information you can check out the VirtualBox forums.

---

### Post by tim042849 on 2011-10-05
Thanks for the reply. I work in a fairly low-resource environment,
as an example, my main editor is gvim, I use mc as my file manager,
do web development testing using apache, browsers and mysql.
I will give it a try. Got any ideas for a simple series of
tests that I could run before taking the time to configure?
regards
tim

---

### Post by dpny on 2011-10-06
> **tim042849 said:**
> Thanks for the reply. I work in a fairly low-resource environment,
as an example, my main editor is gvim, I use mc as my file manager,
do web development testing using apache, browsers and mysql.
I will give it a try. Got any ideas for a simple series of
tests that I could run before taking the time to configure?
regards
tim

I don't know about tests, but installing VirtualBox is fairly simple, and their documentation is good. Best thing is to give it a shot and see how it goes.

---

### Post by tim042849 on 2011-10-06
> **dpny said:**
> I don't know about tests, but installing VirtualBox is fairly simple, and their documentation is good. Best thing is to give it a shot and see how it goes.
I imagine I could think of a number of parallel routines to
run in ubuntu/bash as opposed to mac/terminal as opposed to
my PC with ubuntu and somehow factor the comparable processor
speeds, but I'll give it a try.
thanks a lot

---

