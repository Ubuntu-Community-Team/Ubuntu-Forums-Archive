---
title: "How to download source packages usign Synaptic?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by ociretsih on 2006-11-14
This is my question. I have source packages repositories enabled in Synaptic, but I do not see any option to download source packages, I can download just binary packages.

---

### Post by hotbrainz on 2006-11-14
If you just want to do the installs then u can use those. If you want to see the source and do changes then use the "ubuntu packages" link in my signature

---

### Post by ReaderRat on 2006-11-14
You may need to enable the source repositories in Synaptic Package Manager. Then you should be able to download source files. I believe source files are designated '-src' in Synaptic.

---

### Post by angkor on 2006-11-14
or from the command line:

```
sudo apt-get source {package-name}
```

Also remember to run 'sudo apt-get update' or click the reload button in Synaptic after making changes to your sources.

---

### Post by ociretsih on 2006-11-14
Thanks, ReaderRat, but my problems is that when I see "Repositories" in Synaptic, there appear, for example, Ubuntu 6.06 LTS (Binary) and also Ubuntu 6.06 LTS (Source), and some more "Source" repositories. So I think I've enabled the "Source" repositories, but there does not appear any "-src" package. Why? How do you do enable the source packages in Synaptic?

---

### Post by lamego on 2006-11-14
Application sources can't be installed from Synaptic, you will need to use the "sudo apt-get source " as suggested by angkor .

---

