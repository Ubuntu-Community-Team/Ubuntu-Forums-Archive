---
title: "[SOLVED] Open Office"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by nina_aoki on 2008-04-03
Hello --

New to the forum, new to Ubuntu as well.  

I'm curious if the new version of Open Office will be included in the new Ubuntu distribution due out in 20 days or so -- or, if the native version of Open Office currently included with Ubuntu will remain the same and any OO updates I'd like to do would require a bit more work and expertise?

From what I'm reading on the OO site, there seems to be some issue with Linux distributions which include the OO suite, such as .deb --  and I'm curious if I chose to update OO if I have to completely remove the existing version packaged with Ubuntu.  

Perhaps I'm asking this question in a circular way, but I guess my question comes down to:  are any of the included apps with Ubuntu (like Open Office)  going to be updated to new versions when the new OS is available?  I couldn't find anything on this in any of the Tracs, but this seemed like the logical place to start asking.

Thanks much,

nina aoki

---

### Post by Xiong Chiamiov on 2008-04-03
[It looks like]("http://packages.ubuntu.com/search?keywords=openoffice&searchon=names&suite=hardy&section=all") the i386 packages have been updated to 2.4 in the hardy repos.  If you feel like it, you can download the .debs there and update, though I'd recommend staying with the version in Adept/Synaptic.

---

### Post by chewearn on 2008-04-03
Short answer, yes.  The update of ubuntu will mostly means update of all apps to the latest stable version.

---

### Post by dmizer on 2008-04-03
all base install software (including OO) as well as any software you install via ubuntu's repositories (synaptic or aptitude/apt) will be included in the automated updates for your system.

this does NOT mean that you will have the most current versions of all software available.  but this does mean that you will have fully patched (ie safe) and functional versions which have been completely tested in ubuntu before release.

---

### Post by nina_aoki on 2008-04-03
Great!  Thanks guys!  I appreciate the help and will thank appropriately!  

My issue here is that I know enough to get myself into trouble, but not enough to get myself out of it where using Linux is concerned.  I'm very much a beginner on this OS.

- nina

---

### Post by nina_aoki on 2008-04-03
dmizer:

Got it, thank you!

- nina

---

### Post by Xiong Chiamiov on 2008-04-03
The only way to learn is to dive headfirst in.  I was forced to learn some basic terminal commands when I entered my first programming course, and over winter break I converted to using Kubuntu primarily (so that I'd have time to figure things out).  I also learn all the time from spending time here.

---

### Post by nina_aoki on 2008-04-03
Xiong Chiamiov - 

Oh I completely agree.  I rebuilt a two year old XP loaded desktop, wiped it, and went with Ubuntu... and just love the OS.  Very challenging, but incredibly rewarding as well.

Thanks!  ;)

- nina

---

### Post by vanadium on 2008-04-03
The update policy of Ubuntu with OpenOffice is rather restrictive. The Gutsy version of OOo is 2.3.0 and even minor upgrades of OOo, e.g. from 2.3.0 to 2.3.1 do not make it in one distribution. This is not a too big issue because the distro updates are frequent nevertheless at one every half year. New distro updates always include the latest stable version, which is 2.4 for Hardy. This means that we can expect to see the forthcoming OOo 3 in the spring edition next year.

---

### Post by nina_aoki on 2008-04-03
vanadium --

Thanks for the great answer!

That's kind of what I gathered from reading the OOo site when I was looking into upgrading from 2.3 to 2.4, -- and when I read the section on Linux distributions (like Ubuntu) which include OO and the complicated arrangements involved, I thought it best to ask before I went messing with it -- hence my question about whether or not the newest (or most stable/tested/agreed upon) version of OO would be included with the upcoming Ubuntu release.

Thanks for filling in the blanks on the tracs of OO with respect to Ubuntu.  Your answer was very helpful. :)

While we're on the topic, do you know if Ubuntu includes the full release of OO?  Their site suggests in a non-descript way that some of the Java dependencies are removed in some Linux distributions without really naming which ones are affected; which seems to make it somewhat complicated to figure out what it is you're exactly running with your install I think.

Is there perhaps a FAQ or something similar which discusses included software with Ubuntu in some kind of detail?  I can look myself, but the thought just popped into my head while I was writing this.  Thank you again for the help!

- nina

---

### Post by vanadium on 2008-04-04
Ubuntu includes the full release, and one reason for that is that there is no "limited" release. You are referring to the "java dependencies", though. Ooo for several functions (especially the Base component) relies on a java virtual machine. The gnu java virtual machine is included by default with Ubuntu. Licence restrictions have precluded Linux distributions to include the Sun platform, but as Sun is open sourcing its Java, this concern might soon belong to the past.

---

### Post by nina_aoki on 2008-04-04
vanadium --

Got it!  Good to know that!  Thank you! ;)

- nina

---

