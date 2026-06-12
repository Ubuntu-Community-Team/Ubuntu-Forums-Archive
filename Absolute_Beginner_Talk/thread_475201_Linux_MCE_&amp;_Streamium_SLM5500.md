---
title: "Linux MCE &amp; Streamium SLM5500"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by jrgibb on 2007-06-15
Hi,

Does anyone know if MCE will support my SLM5500 Media device or will I need something like TVersity or Twonky Vision? 

If MCE does not support this type of streaming media device is there a Linux alternative to TVersity / Twonky as I'm not that keen on either of these.

Thanks,

J

---

### Post by JanCeuleers on 2008-02-07
It's not sufficient to point Mythtv at a directory that contains your media (MP3s etc), you also need to get it to scan the contents of that directory for the media to be served (whether via UPNP or otherwise).

For example, mythmusic (invoked from the frontend) has an option for rescanning the media directory. This will cause mythmusic to look at the files, extract metadata from any ID3 tags and add that to the mysql database.

Any time you change your media library a rescan such as the above is needed. (Unfortunately I have not yet found a way to invoke the rescan from the command line).

Hope this helps.

Jan

---

