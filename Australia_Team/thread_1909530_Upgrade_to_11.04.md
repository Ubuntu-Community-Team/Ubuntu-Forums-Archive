---
title: "Upgrade to 11.04"
date: 2012-01-15
forum: Australia Team
---

### Post by kizzyaggots on 2012-01-15
Hi, I'm having trouble upgrading from Ubuntu 11.04 to Ubuntu 11.10, i try to upgrade unsuccesfully with this error message..........

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/chris/main'./source/Sources](http://archive.ubuntu.com/ubuntu/dists/chris/main'./source/Sources)  404  Not Found [IP: 91.189.92.171 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Can somebody help me in simple terms as i am new to Ubuntu.


              Cheers Kizzy.

---

### Post by BC59 on 2012-01-15
Open a terminal with CTRL+ALT+T and paste-run the commands:

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
```

---

### Post by kizzyaggots on 2012-01-15
Hi mate i tried that and it's still the same, gives me the same error message etc and refuses to upgrade.

---

### Post by kizzyaggots on 2012-01-15
On the terminal it says 8 installed 1 not upgraded

---

### Post by BC59 on 2012-01-15
Maybe your software sources are messed. Open the Software Sources and from the tab Other Software, try to uncheck any repository not being of the Oneiric version.

eg the repositories should be like this:
[http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu) **oneiric** main

---

### Post by kizzyaggots on 2012-01-15
Thanks mate, that seemed to have worked, so far so good.

:P

---

### Post by kizzyaggots on 2012-01-15
Thanks very much for your help BC59, you were spot on and my system is up and running again perfectly.... thanks again.

         Kind Regards Chris.

---

