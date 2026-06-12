---
title: "apt-get packagevconfiguration; installation question"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by apidya on 2007-12-03
Sorry, this is a very simple beginner's question.

If I install a package such as phpmyadmin on my ubuntu server with apt-get I am given a configuration screen.  If I then uninstall and reinstall the package, I do not get the screen ( I presume it uses the old configuations) Is there a simple reinstall method that will prompt for the configuration screen again?

---

### Post by apjone on 2007-12-03
> **apidya said:**
> Sorry, this is a very simple beginner's question.

If I install a package such as phpmyadmin on my ubuntu server with apt-get I am given a configuration screen.  If I then uninstall and reinstall the package, I do not get the screen ( I presume it uses the old configuations) Is there a simple reinstall method that will prompt for the configuration screen again?

Yes,

```

sudo dpkg-reconfigure *packagename*

```

that should do you

---

### Post by logos34 on 2007-12-03
try 

sudo dpkg -r -P phpmyadmin (-->removes pkg AND purges config files)

Or if you just want to be able to configure it try 

sudo dpkg -reconfigure phpmyadmin

---

### Post by apidya on 2007-12-03
sudo dpkg-reconfigure packagename works great. Thanks for this.  The trouble arose during installation when I pressed Enter instead of space to select and option.

Thanks again

---

