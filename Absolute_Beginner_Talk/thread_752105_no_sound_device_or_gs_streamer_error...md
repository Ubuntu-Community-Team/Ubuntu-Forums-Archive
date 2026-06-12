---
title: "no sound device or gs streamer error.."
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by cello_911 on 2008-04-11
installed linux mint (ubuntu base ) unbale to get any sound at all, error appears stating no device found or no gs streamers installed please advice what i need to do, i use a dell inspiron 1520

thanks

---

### Post by herbster on 2008-04-11
```
lspci
```

Paste the output using [code] tags.

---

### Post by ibutho on 2008-04-11
You can refine the output to just the sound card by doing
```
lspci | grep -i audio
```

---

