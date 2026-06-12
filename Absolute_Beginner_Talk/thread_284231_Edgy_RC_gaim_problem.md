---
title: "Edgy RC gaim problem"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by andnobodyslept on 2006-10-25
I just upgraded from Dapper to Edgy and I have to say that things look great. The only problem is that Gaim has stopped working. I attempt to start gaim and it won't start up, I get this error message from the terminal 
"gaim: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory"
After searching for libdbus-1-2 I find out that it is an old package and that it can't be found in the repos, which is strange since I have universe and multivers enabled. Either way I can't get libdbus-1-2 and I can't update or change gaim...any ideas?

---

### Post by skierkegaard on 2006-10-25
My gaim that came with Edgy RC depends on libdbus-1-3.  Maybe try grabbing that.

---

### Post by Aberrix on 2006-10-25
try
```
sudo apt-get install gaim
```
maybe that will 'reinstall' the missing/broken packages.

---

### Post by andnobodyslept on 2006-10-25
I have the installed (also tried reinstalling that), still no luck...thanks for the idea though.

---

### Post by skierkegaard on 2006-10-25
sudo aptitude reinstall gaim

Would be better.

---

### Post by andnobodyslept on 2006-10-25
Strange error when trying to reinstall with aptitude
"Writing extended state information... Error!
E: I wasn't able to locate file for the gaim package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?"

First time I ever got this an I use aptitude a lot.
Any ideas?

---

### Post by andnobodyslept on 2006-10-25
Got it! Before upgrading I had installed the newest beta version from the gaim website. I had to go into synaptic and use force version to downgrade. Everything is working now.
Thanks for the help,
Ian

---

### Post by KuriKai on 2006-10-28
> **andnobodyslept said:**
> Got it! Before upgrading I had installed the newest beta version from the gaim website. I had to go into synaptic and use force version to downgrade. Everything is working now.
Thanks for the help,
Ian

That fixed the same problem on my computer thanks.

---

