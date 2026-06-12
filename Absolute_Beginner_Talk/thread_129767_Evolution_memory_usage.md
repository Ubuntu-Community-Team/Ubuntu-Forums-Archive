---
title: "Evolution memory usage"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Barleyman on 2006-02-14
Hello, I have Breezy Badger installed on a brand new P4 with 1 gig of RAM.  I am using T-bird as my email client.  I still see evolution-alarm-notify, ..-data-server, ...exchane-storage processes using 56, 48, and 25 MiB of virtual memory is this normal?

I am not using evolution at all.  thank in advance for your help.  I liked Ubuntu so much I bought a brand new Dell with XP and didn't even boot into it before installing Ubuntu.

---

### Post by aysiu on 2006-02-14
Well, if you want, you can uninstall Evolution.

Go to System > Administration > Synaptic Package Manager and search by Name for the word *evolution* and mark almost all of them for uninstall.

The only thing you can't uninstall (without screwing up all of Gnome) is the package called *evolution-data*.

P.S. Does it just *appear* to be using a lot of memory, or does your computer's responsiveness noticeably slow down?

---

### Post by Barleyman on 2006-02-14
Thanks for your response.  No, it does not noticeably slow down my system, I was just concerned that over that the system monitor in my Gnome panel says 100% of my memory is in use, of which 28% is cache.  I have attached a screenshot of my system resources (see screenshots).  I read somewhere that Linux optimizes available RAM not in use, perhaps this is happening here, I am not sure.  I am just trying to make sure nothing is running that I don't use or need.  

[IMG]http://www.eberly.org/Screenshot-System%20Monitor.png[/IMG]
[IMG]http://www.eberly.org/Screenshot-System%20Monitor-1.png[/IMG]

---

### Post by aysiu on 2006-02-14
You're fine, especially with half a Gig of memory still unused.

---

