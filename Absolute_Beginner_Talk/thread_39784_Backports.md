---
title: "Backports"
date: 2005-06-06
forum: Absolute Beginner Talk
---

### Post by Sionide on 2005-06-06
I'm confused about the backports... Now that they're denying access to the normal URL - what lines should I have in my sources.list now? I'm not sure how to use the mirrors they tell you to use!

---

### Post by SGC on 2005-06-06
add this to your sources.list:
```

deb http://ubuntu-backports.mirrormax.net hoary-backports main universe multiverse restricted  
deb http://ubuntu-backports.mirrormax.net hoary-extras main universe multiverse restricted 

```

---

### Post by Sionide on 2005-06-06
I'm still having troubles with Synaptic, because of a broken package. How can I fix it, without just deleting it??

---

### Post by xristos on 2005-06-06
In the command line type ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Sionide on 2005-06-06
and if that doesn't work because I connect through a proxy server?

Does apt-get have proxy settings I can edit somewhere?? :(

---

