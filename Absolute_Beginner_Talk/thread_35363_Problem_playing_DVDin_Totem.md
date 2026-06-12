---
title: "Problem playing DVDin Totem"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by zaxer on 2005-05-18
Hi guys.

Im having problems when playing a DVD with Totem. Image quality isnt the best one but works. Sound isnt working.

Anyone has the same problem?


Thanks for your support guys.

---

### Post by bruizer on 2005-05-18
I had the same issues... I switched over to XINE and everything works fine. I would like ot konw what was causing this though...

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=bruizer]I had the same issues... I switched over to XINE and everything works fine. I would like ot konw what was causing this though...[/QUOTE]

DMA needs to be turned on:

[http://www.ubuntuforums.org/showthread.php?t=30949&highlight=dma](http://www.ubuntuforums.org/showthread.php?t=30949&highlight=dma)

---

### Post by zaxer on 2005-05-19
[QUOTE=poofyhairguy]DMA needs to be turned on:

[http://www.ubuntuforums.org/showthread.php?t=30949&highlight=dma](http://www.ubuntuforums.org/showthread.php?t=30949&highlight=dma)[/QUOTE]
 It seems like Its already turned ON but still not working :(

```

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

```

---

### Post by estel on 2005-05-19
[QUOTE=zaxer]It seems like Its already turned ON but still not working :(

```

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

```[/QUOTE]

Those lines are commented out - and will therefore not have any affect on your system.

I've got a problem that MPlayer just gives me white noise and an error (Couldn't find matching fliter/ao format), XINE keeps telling me that the ALSA device 'default' is already being used, and XINE gives me a really jumpy DVD watching experience.

Any help?

---

### Post by zaxer on 2005-05-19
[QUOTE=estel]Those lines are commented out - and will therefore not have any affect on your system.

I've got a problem that MPlayer just gives me white noise and an error (Couldn't find matching fliter/ao format), XINE keeps telling me that the ALSA device 'default' is already being used, and XINE gives me a really jumpy DVD watching experience.

Any help?[/QUOTE]
 :)

Thanks. I fixed that.

---

### Post by bruizer on 2005-05-20
DMA fixed it but it is still very choppy. I use the same videos in XINE and all is good. Any thoughts?

---

### Post by poofyhairguy on 2005-05-20
[QUOTE=bruizer]
. I use the same videos in XINE and all is good. Any thoughts?[/QUOTE]


Yep, Xine is better in every way...

---

### Post by bruizer on 2005-05-20
[QUOTE=poofyhairguy]Yep, Xine is better in every way...[/QUOTE]

Hehehe... I am finding out. I have been using mplayer and RealPlayer, but both seem a bit heavy. Pretty happy with XINE so far!

Thanks!

---

