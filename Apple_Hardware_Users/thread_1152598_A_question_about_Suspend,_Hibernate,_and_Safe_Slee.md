---
title: "A question about Suspend, Hibernate, and Safe Sleep"
date: 2009-05-08
forum: Apple Hardware Users
---

### Post by Altay_H on 2009-05-08
I was reading over the implementation of Suspend and Hibernate in various operating systems and I noticed that Macintosh saves the RAM to the disk when put in sleep mode and restores from the RAM if power has not been lost, or from the disk if power has been lost.

What I'm wondering is how Macintosh can save the contents of the RAM to the disk within 2-5 seconds. I don't own an Apple computer myself, but based on my experience with my father's Macbook, Macintosh computers don't suspend any slower than other computers despite saving the RAM.

My Vista computer takes at least 60 seconds to hibernate (not including restoring). Even Intrepid Ibex took at least 20 seconds to hibernate (I haven't tried Hibernating in Jaunty Jackalope yet).

My question is, how does Macintosh manage to save the contents of the RAM to the disk so quickly? Is it simply a hardware issue? Is there a "safe sleep" option for Linux?

---

### Post by tiagobt on 2009-05-08
Apple notebooks have a feature called "safe sleep," which saves the contents of the RAM to the disk when the lid is closed. If the notebook is turned on in normal power conditions, the resume process is almost instantaneous. If the notebook is turned on after a power loss, the resume process takes a while because the RAM has to be restored from the disk.

I believe the safe sleep mode integrates the suspend and hibernate features from Linux. However, I have never heard of a similar feature in Linux or Windows.

In my MacBook (second generation), sleeping takes about 10 seconds in Mac OS (you have to wait until the external light starts blinking) and resuming from a power loss takes about 10 seconds as well. In Linux (Ubuntu Jaunty), hibernating takes about 30 seconds and resuming takes about 35 seconds. Like you said, sleeping in Mac OS is much faster, but 2 seconds sounds a bit too fast. How did you measure the sleep time?

I am really not sure how Mac OS manages to copy the contents to the disk so fast. Maybe Mac OS takes up less RAM than Linux, but this would not explain a three-times-faster hibernation. Besides, Linux copies the contents to the swap partition, which should be fast as well. Any other ideas?

---

### Post by Altay_H on 2009-05-08
> **tiagobt said:**
> In my MacBook (second generation), sleeping takes about 10 seconds in Mac OS [...] 2 seconds sounds a bit too fast. How did you measure the sleep time?
I didn't actually measure the sleep time, I was just estimating. Ten seconds is probably more accurate. What I meant was that it wasn't any slower than Sleep on Windows or Linux, yet considerably faster than Hibernate on either.


> **tiagobt said:**
> I am really not sure how Mac OS manages to copy the contents to the disk so fast. Maybe Mac OS takes up less RAM than Linux, but this would not explain a three-times-faster hibernation. Besides, Linux copies the contents to the swap partition, which should be fast as well. Any other ideas?
I suppose the fact that Linux uses a dedicated swap partition might explain why it's significantly faster than Windows. Macintosh remains a mystery though. I'll be interested if anyone actually has any ideas.

---

### Post by Doncr on 2009-05-09
Kubuntu x86 on my desktop machine suspends to ram fairly fast - much quicker than 8.10 - but then I have not re-installed a lot of things yet, such as Samba - which may make a difference.

I cannot get suspend to ram or suspend to disk working on Kubuntu PPC 8.10 on a G4 TiBook 500. Appears to suspend but when 'waking' it seems to continue to suspend and then stop, and needs to be restarted again. I cannot get it to upgrade to 9.04 either. Get an error about "Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file"

---

### Post by Person_1873 on 2010-02-20
the way it works (it's called hybrid-sleep on vista and win7) is that it makes the machine appear as though it's sleeping but before it actually goes down to S3 it starts to copy the contents of the ram to the HDD, it would only appear as though it were sleeping rather than hibernating, but in actual fact it is doing both

---

