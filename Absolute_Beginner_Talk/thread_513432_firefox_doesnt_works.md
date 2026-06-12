---
title: "firefox doesnt works"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by reneesito on 2007-07-30
im using ubuntu 6 something
i downloaded some stuff
and now firefox doesnt open 
i uninstalled and try to installed again by using the terminal and synaptic package manager but it can downloaded and it marks this error

E: /var/cache/apt/archives/firefox_1.5.dfsg
+1.5.0.13~prepatch070716-ubuntu1_i386.deb:trying to overwrite`/
usr/lib/firefox/defaults`, which also in package limewire-basic

---

### Post by aysiu on 2007-07-30
Have you tried this? ```
sudo mv /usr/lib/firefox/defaults /root/.Trash/
sudo apt-get -f install
sudo apt-get install --reinstall firefox
```

---

### Post by shagster_ on 2007-07-30
why would the limewire-basic package depend on the firefox dir??

---

### Post by aysiu on 2007-07-30
> **shagster_ said:**
> why would the limewire-basic package depend on the firefox dir??
I don't know why.

An alternative is to remove Limewire and use Frostwire. Worked for this person:
[http://www.hostingforum.ca/640092-force-firefox-upgrade.html](http://www.hostingforum.ca/640092-force-firefox-upgrade.html)

---

### Post by shagster_ on 2007-07-30
*any*wire is craps anyways, i was just trying to think what could they (limewire programmers) want from those files....bah...

---

