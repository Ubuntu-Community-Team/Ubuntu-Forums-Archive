---
title: "How to add multiverse repository?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-07-17
[https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

When I am in synaptic, and hit settings > Repository... I have every single last one selected....

yet I cannot find mplayer.... 

gstreamer0.10-pitfdll IS MIA....

gstreamer0.10-plugins-bad is there, but not gstreamer0.10-plugins-bad-multiverse.....

With the gstreamer0.10-plugins-ugly its there but I get > gstreamer0.10-plugins-ugly-multiverse:
 Depends: liblame0 (>=3.96.1-1) but it is not installable

libxine-extracodecs & w32codecs are also MIA....

---

### Post by Jagot on 2006-07-17
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by fatsheep on 2006-07-17
> **Jagot said:**
> [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


I've found that guide to be incorrect.  Here's what worked for me:

Go to System>Administration>Software Properties. You'll have to enter your password here. After that then select "Ubuntu 6.06 LTS (source)" from the list (should be the first one), click "Add...", select   "non-free (multiverse)" by clicking the check box. Click add again.  Multiverse repositories are now enabled.

---

### Post by IDontKnow9998 on 2006-07-17
> **fatsheep said:**
> I've found that guide to be incorrect.  Here's what worked for me:

Go to System>Administration>Software Properties. You'll have to enter your password here. After that then select "Ubuntu 6.06 LTS (source)" from the list (should be the first one), click "Add...", select   "non-free (multiverse)" by clicking the check box. Click add again.  Multiverse repositories are now enabled.

Yeah that what I just found... the link jagot gave were pretty useless (because I had already been there :P)

---

### Post by Jagot on 2006-07-17
Well, if the first one doesn't work for you then the second one does.

---

### Post by IDontKnow9998 on 2006-07-17
> **Jagot said:**
> Well, tif the first one doesn't work for you then the second one does.

o, didnt even look at second url :P <-Like I said, had it fixed before I saw your reply.

---

### Post by crispy_420 on 2006-07-17
> libxine-extracodecs & w32codecs are also MIA....

You'll have to get some non-official repos. These aren't there due to license issues. You'll also not find lame, libdvdcss, etc. Just search for the PLF repos, they add all that stuff. Or you can do what many others do, use Automatix or Easy Ubuntu.

---

### Post by catlett on 2006-07-17
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)  Scroll down for the commands to wget win32codecs.

---

### Post by DirtDawg on 2006-08-15
> **fatsheep said:**
> I've found that guide to be incorrect.  Here's what worked for me:

Go to System>Administration>Software Properties. You'll have to enter your password here. After that then select "Ubuntu 6.06 LTS (source)" from the list (should be the first one), click "Add...", select   "non-free (multiverse)" by clicking the check box. Click add again.  Multiverse repositories are now enabled.

Thanks Fatsheep. That was driving me nutz.

---

