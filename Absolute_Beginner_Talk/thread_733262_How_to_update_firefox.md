---
title: "How to update firefox"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by taco_truck on 2008-03-23
I just installed Ubuntu.  Firefox version 2.0.0.6  How do I update it to the latest 2.0.0.12 version?

---

### Post by Oldsoldier2003 on 2008-03-23
> **taco_truck said:**
> I just installed Ubuntu.  Firefox version 2.0.0.6  How do I update it to the latest 2.0.0.12 version?

```
apt-get update
apt-get upgrade
```

alternatively you can have firefox update itself.

---

### Post by herbster on 2008-03-23
You sure it's 2.0.0.6? Open a terminal and do

```
apt-cache show firefox
```

And see which version it says. If it's 2.0.0.6, you most likely need to do an update as above.

---

### Post by taco_truck on 2008-03-23
Yes, it is 2.0.0.6.  How do I update it?

---

### Post by herbster on 2008-03-23
Oldsoldier2003 has clearly instructed how, run the commands in a terminal that he has posted.

---

### Post by taco_truck on 2008-03-23
Did it, and still did not update.  Can I just get it from the mozilla firefox website??

---

### Post by ghost_ryder35 on 2008-03-23
> **taco_truck said:**
> Did it, and still did not update.  Can I just get it from the mozilla firefox website??

yea, but the above commands should notifiy you if the software that is installed is out dated...

---

### Post by taco_truck on 2008-03-23
Could someone please inform me step by step of how to upgrade it via the firefox website.

Thanks

---

### Post by ghost_ryder35 on 2008-03-23
1. **Download** [http://download.mozilla.org/?product=firefox-2.0.0.12&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-2.0.0.12&os=linux&lang=en-US)

2. Then follow this guide, [http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html) , and just change the filenames he refers to, to your file names eg. firefox-2.0.0.12

---

