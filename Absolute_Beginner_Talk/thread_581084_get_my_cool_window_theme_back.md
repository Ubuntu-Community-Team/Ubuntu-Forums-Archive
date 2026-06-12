---
title: "get my cool window theme back"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-19
before  i had this nice window theme that was in bveryl manager
i used it for compiz, and gave good effect etc.

but now i need to find it, once i do.

how do i make it work? since theres no beryl manager

---

### Post by 001100 on 2007-10-19
you could download berly again and use it, thats what i did. but wait before downloading anything the servers are very buzy.

---

### Post by Anzan on 2007-10-19
Or you could download the Compiz Settings Manager (apt-get or through Synaptic) and set it up again since Beryl is deprecated.

---

### Post by skymera on 2007-10-19
yeah ive got CCSM
but how do i select my theme from there?

---

### Post by Hospadar on 2007-10-19
Hey I had this very same issue, I had to do a couple things

First, install "emerald" from synaptic.
Then, grab the old emerald-themes package from feisty and install it. ([http://packages.ubuntu.com/feisty/x11/emerald-themes](http://packages.ubuntu.com/feisty/x11/emerald-themes))
(at this point if you go to System->Preferences->emerald you can see the emerald themes)
now replace the compiz decorator with ```
 compiz --replace -c emerald
```

Let me know if that works, I might have gotten the command wrong

---

