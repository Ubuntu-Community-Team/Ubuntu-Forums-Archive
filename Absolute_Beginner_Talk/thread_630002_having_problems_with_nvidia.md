---
title: "having problems with nvidia"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by colomob on 2007-12-02
:(i just installed ubuntu 7.04 and i cant enable the desktop effects.. i have an nvidia graphic card..i need someones help !!

---

### Post by dhar2112 on 2007-12-02
Try this:

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by colomob on 2007-12-02
when i go to restricted drivers nothing appears...

---

### Post by amireldor on 2007-12-02
hmm, let's see if ubuntu finds your card at all

in a terminal, run this command which lists all your connected cards (and filters out those with 'nvidia' in them):
```

$ lspci | grep -i nvidia

01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)

```

[COLOR="dimgray"](shown here with my output)[/COLOR]

---

