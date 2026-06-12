---
title: "kio_http and kio_file : why so many?"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-01-25
Since this seems to be such a noobish question, I think it's better to post this here:

what are kio_http and kio_file? I have so many of them running, especially kio_http when I'm using Konqueror as a browser? Do they pose any RAM resource danger? and are they only found in KDE?

Any enlightenment (no pun here) would be appreciated.

---

### Post by GoldBuggie on 2006-01-25
simple answer...

kio = kde input/output ([http://en.wikipedia.org/wiki/KIO](http://en.wikipedia.org/wiki/KIO))

when you go thrue http:/ in konqueror it uses the kio http and when you access files it most often goes thrue the kio file. It is just how KDE is built, a nice thing actually.

---

### Post by Jucato on 2006-01-25
oooh thanks for that super quick reply!

just one last question though, does it really take up that much space in my resources? Because according to KSysGuard, each kio_http takes up 51,000 VmSize. and I have around 5-6 of them running at the same time.

---

### Post by GoldBuggie on 2006-01-25
my system has about the same size.

the memory management in linux is a bit different then windows. there are numerous www pages on the subject. but basically you can say that linux is designed to take full advantage of your memory. that doesn't mean that all applications should be memory hogs, it just means that your physically memory is often used to the max(much cache). check kinfocenter -> memory for a nice overview of your system

---

### Post by doclivingston on 2006-01-25
The "VmSize" measurement doesn't mean what most people assume it means - it is the size of a process' address space. If you want to know how much memory something is using, look at "resident memory".

---

### Post by Jucato on 2006-01-25
Thanks so much for that reassurance. I was getting paranoid with the VmSize issue because my system hung up last night after xorg used up around 800k+ of VmSize (from composites and shadows), and also got scared of Firefox's big VmSize. So looking for a browser alternative, I turned to our own Konqueror and was quite satisfied, until I saw the kio_http's popping out. Now that I understand a bit about KDE's KIO, I think I'm enjoying Konqueror a bit better. Thanks for your help!!

P.S. doclivingston: where do I find this "resident memory"? Sorry for being such a newbie... :)

---

### Post by doclivingston on 2006-01-25
I imagine it would be somewhere in KSysGuard, however I'm not sure exactly what it would be called (I'm not a KDE user myself). In gnome-system-monitor you need to tell it to display that column, since it isn't visible my default - KSG may be similar.

---

### Post by Jucato on 2006-01-25
Well, KSG isn't that very easy to interpret, with all those lines that look like monitors in hospitals. I'll just check on it again some other time. Thanks for your help!! :) (hope they improve Konqueror's web browsing capabilities soon, or reduce Firefox's resource usage...)

---

