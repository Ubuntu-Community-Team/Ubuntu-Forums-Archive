---
title: "newbie in need of help"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by hemdup on 2008-02-20
I have installed the desk top and I cannot hear music from embedded websites. What can be the problem? I hear music from CD's and DVD's but no websites.

---

### Post by DrMega on 2008-02-20
Have you installed the packe called "ubuntu-restricted-extras" which is in the repositories (in Applications->System-<Synaptic)?

---

### Post by jan quark on 2008-02-20
can you please post the link to the website you cannot here the sound ?

---

### Post by njparton on 2008-02-20
Was your sound card detected and configured correctly?

---

### Post by paultag on 2008-02-20
Make sure gstreamer is installed -- this is the package that contains a bunch of audio codecs,

> 
Description: Core GStreamer libraries and elements
 GStreamer is a streaming media framework, based on graphs of filters which
 operate on media data.  Applications using this library can do anything from
 real-time sound processing to playing videos, and just about anything else
 media-related.  Its plugin-based architecture means that new data types or
 processing capabilities can be added simply by installing new plug-ins. 

You may install this by running

```

sudo aptitude install libgstreamer0.10-0

```

Cheers,
Tag

---

### Post by ubuntu-freak on 2008-02-20
My cut & paste [how-to](http://ubuntuforums.org/showthread.php?t=661833) should be of some help, part 2 is dedicated to streaming. Might be worth doing part 1 as well incase you are missing anything.
 
Nathan

---

### Post by hemdup on 2008-02-20
I have tried hearing musice from [http://www.veoh.com]("http://www.veoh.com") and I have been trying to watch tv shows and still I get nothing.

---

