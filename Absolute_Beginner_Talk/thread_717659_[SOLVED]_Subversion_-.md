---
title: "[SOLVED] Subversion -"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-03-07
Hello,

I installing subversion. I am following the instructions on
[https://help.ubuntu.com/community/Subversion#head-d61137b27d149c71fba400fab76c95754c1f1ee2]("https://help.ubuntu.com/community/Subversion#head-d61137b27d149c71fba400fab76c95754c1f1ee2")

Since I am using Ubuntu server addition I do not have a GUI so the following instructions I have to do from command line. It would be nice if someone could verify that my commands are correct


   1. Choose System > Administration > Users and Groups from your Ubuntu menu.
   2. Select the Group tab
   3. Click the 'Add Group' button
   4. Name the group 'subversion'
   5. Add yourself and www-data (the Apache user) as users to this group
*  (Note: in order to see www-data you may need to modify root's htpps/gnome-system-tools/users/showall GConf setting; see GConfEditor)
   6. Select 'OK' to commit your changes and exit the app.

1.- 4. ```
sudo addgroup subversion
```
5.-6.
```
sudo usermod -G subversion -a ben    sudo usermod -G subversion -a apache2

```

Thanks!
Ben

---

### Post by spydon on 2008-03-07
It looks right to me...
But you will have to use the && if you want to execute the last commands on one line:
```
sudo usermod -G subversion -a ben && sudo usermod -G subversion -a apache2
```

---

### Post by dbbolton on 2008-03-07
If you want to install subversion, all you have to do is
```

apt-get install subversion
```

The steps you describe are for setting up an SVN repository. (Your post made me think that you just wanted to install subversion)

---

### Post by ben22 on 2008-03-07
> **dbbolton said:**
> If you want to install subversion, all you have to do is
```

apt-get install subversion
```

The steps you describe are for setting up an SVN repository. (Your post made me think that you just wanted to install subversion)

well, I did this already, but you need to add the users - see tutorial

I just wonder whether it is ```
sudo usermod -G subversion -a www-data

```

OR

> sudo usermod -G subversion -a apache2

---

