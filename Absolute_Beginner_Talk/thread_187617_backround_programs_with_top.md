---
title: "backround programs with top"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by hikitsu4 on 2006-06-03
Hello i got a question about the backround programs and what they do, this isnt really a newbie question but i kinda wana know what they do anyway, even if im a newbie myself.
The programs im talking about is the ones you get when you type "top" 
(pdflush, migration/0, ksoftirqd/0, watchdog/0, events/0, khelper, ksoftirqd/0, aio/0, reiserfs/0, khubd, init.

---

### Post by Rinzwind on 2006-06-03
pdflush:
In 2.6 pdflush replaces bdflush and kupdated from 2.4 and is responsible for periodically flushing dirty pages in order to ensure that there is enough free memory and to save users from losing data when their computer crashes and things are still in the buffer cache instead of on disk.

ksoftirqd:
used for softirq. Softirq causes tasks from IRQs (like building a TCP/IP packet, say) to be queued up to be run at scheduling time, once per time-slice.

Watchdog:
will watch your computer for those nasty system hang ups and reboot it as needed in your absence.

khubd:
is responsible for configuring devices. Like USB: [http://www.linuxjournal.com/article/8093](http://www.linuxjournal.com/article/8093) (more info)

aio: 
asynchrone input/output. more info: [http://lse.sourceforge.net/io/aio.html](http://lse.sourceforge.net/io/aio.html)

---

