---
title: "how do I uninstall a python app"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2007-09-22
the application was installed with the typical install script that is out there

```
python setup.py install
```

can i use the same script to uninstall it? like.. passing another parameter or so?

Otherwise i thought i should run

```
whereis myapp
```

and delete all the folders it returns... is there any issu i should be aware in case i have to use this last option?

---

### Post by Zootropo on 2007-09-22
distutils, which is probably what the author used to create the installation script doesn't create an uninstall target by default. So probably you won't have that option.

---

### Post by moephan on 2007-09-22
If you use setup.py you do have to uninstall manually.  If you are very concerned about a complete removal, you may want to check the setup.py file and make sure that it did not install images, symlinks, etc... that won't be picked up by your "whereis" command.

Cheers, Rick

---

