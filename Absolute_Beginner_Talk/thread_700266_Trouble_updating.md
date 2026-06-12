---
title: "Trouble updating"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2008-02-18
When I try to update or install anything through "apt-get" or synaptic, I get this error message:

```
E: /var/cache/apt/archives/linux-generic_2.6.22.14.21_i386.deb: files list file for package `linux-generic' is missing final newline
```

Any help would be appreciated.

---

### Post by fraser_m on 2008-02-18
oops.

---

### Post by Anicka on 2008-02-18
By disabling backports you are not allowing some updates (officially unsupported).

Instead you could try to open the file that complained in sudo mode with your favourite texteditor and put a blank line at the end of the file. That should help too. [COLOR="Red"]Doesn't seem to work[/COLOR]

Or you can try to re-download the file form the repos "sudo aptitude -d install package_name", maybe it is a bad download or a temporary problem with this particular file.

Edit: After trying to open the files in apt/archive it doesn't seem to work as easily as I thought, less gives a readable output, but not cat or gedit. Sorry for the misinformation.

---

### Post by fraser_m on 2008-02-18
Fix!

Back up old linux-generic.list
```
sudo mv /var/lib/dpkg/info/linux-generic.list linux-generic.list.bck
```

Remove linux-generic completely
```
sudo apt-get remove --purge linux-generic
```
This gives a moan about how it has no files installed blah blah blah.

```
sudo apt-get install linux-generic
```

Mwahaha. Go me.

---

