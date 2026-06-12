---
title: "Package Manager Unable to Authenticate Package"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by mcbenz55 on 2007-10-02
Hi,
When using Add/Remove Programs and Synaptic Package Manager a lot of the things I'm trying to get (Bastille, Plugins for Totem) are not able to be authenticated. Should I be worried? Or am I generally okay? Is there somewhere else I can look for authenticated versions? I've downloaded some stuff and checked against the hashes, but its not very convenient.
Thanks

---

### Post by hyper_ch on 2007-10-02
I assume you added own repositoires and you did not add their GPG keys.

---

### Post by mcbenz55 on 2007-10-03
I haven't added any repositories all I've done is search for the apps I was looking for. Does anyone have a link to somewhere explaining the process?

---

### Post by rsambuca on 2007-10-03
Post the output of ```
cat /etc/apt/sources.list
```

---

