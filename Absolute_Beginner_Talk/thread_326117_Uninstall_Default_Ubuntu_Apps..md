---
title: "Uninstall Default Ubuntu Apps."
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by knoc on 2006-12-27
Is there a way to uninstall the applications pre-installed in Ubuntu by default such as Movie player and Rythmbox? 

I've installed other media applications and internet programs and was just wondering if there is any way to uninstall the default ones due to the fact that I probably won't be using them.

---

### Post by maxamillion on 2006-12-27
I will assume you used synaptic to install the new applications, if so just select the package for deletion instead of installation.

If not you will simply need to do

```
sudo apt-get remove package_name_here
```

or

```
sudo aptitude remove package_name_here
```

depending on your package manager of choice.

---

### Post by knoc on 2006-12-27
thank you for your help:)

---

### Post by aosmith on 2006-12-27
you can use synaptic (system -> admin -> synaptic) aswell which makes doing multiple apps easier imho

---

### Post by 3rdalbum on 2006-12-27
Don't worry if it tells you that it will remove "ubuntu-desktop" - this is normal and will not break your system.

---

