---
title: "Gyachi"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by arvindenrique on 2008-01-03
i have downloaded gyachi 1.1.0(tar.gz)  for ubuntu 7.10. but i dont know how to install it. my synaptic manager doesnt have it.

---

### Post by hyper_ch on 2008-01-03
On the Gyachi page ([http://gyachi.sourceforge.net/download.shtml](http://gyachi.sourceforge.net/download.shtml)) select the "All other packages and plugins" version. Then you'll be presented by a list of alternate downloads and among them you have this "gyachi_1.1.0-1_i386_gutsy.deb".

Download that to your desktop, double-click it and let gdebi install it.

If you want to compile from source, you first need the compiler (and other stuff)
```

sudo apt-get install build-essential

```
After that you would unpack the tar.gz file and in the terminal go to that directory.
There you'd first look if there's an install (text) guide, if not you'd normally run:
```

./configure
make
sudo make install

```

That may not work as other packages could be missing that you'd need to install first. So you have to install them, very likely also their developer version (normally the have the same name just with an additional ending of "-dev")

Compiling can be more complicated, so if you want to get it up and running, you the .deb file.

---

### Post by kestrel1 on 2008-01-03
Download the Deb Package:
[http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575](http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575)
I think it was the second one down on the page for Gutsy Gibbon (7.10)
Far easier to install.

---

