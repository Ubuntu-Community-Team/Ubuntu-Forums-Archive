---
title: "I can't get flash to work right"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by watkinsted on 2007-11-20
i have added macromedia flash plugin from the synaptic package manager and the libflash-plugin too any ideas?

---

### Post by stchman on 2007-11-20
> **watkinsted said:**
> i have added macromedia flash plugin from the synaptic package manager and the libflash-plugin too any ideas?

If you are talking about making sites like YouTube do this:

```

rm -f ~/.mozilla/plugins/*flash*
sudo apt-get -y install flashplugin-nonfree
```

Flash enabled websites should now work.

---

### Post by ephro on 2007-11-20
Make sure you don't have a flash player installed in ~/.mozilla/plugins

If you installed flash through Firefox itself, it will install there, and cause some conflicts. To fix it, just delete anything in ~/.mozilla/plugins with flash in the name and restart firefox to see if that fixes your problem.

If that doesn't do it can you post more detail about what is wrong along with the Flash details available from the URL about:plugins in Firefox.


Ephro

---

