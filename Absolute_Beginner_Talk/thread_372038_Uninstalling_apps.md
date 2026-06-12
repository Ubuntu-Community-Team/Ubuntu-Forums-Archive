---
title: "Uninstalling apps"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by ACF1 on 2007-02-27
What do I type (in the terminal) to uninstall something?  Is it just "sudo aptitude uninstall"  ?  Or something else?  And do I still have to do "sudo aptitude update" before uninstalling something?  Also, will using aptitude get rid of all the dependencies that aren't being used by something else?  Or do I need to type something else in addtion to aptitude?  Thanks.

---

### Post by taurus on 2007-02-27
```
sudo aptitude --purge remove **program_name**
```

---

### Post by Maestro23 on 2007-02-27
> **ACF1 said:**
> What do I type (in the terminal) to uninstall something?  Is it just "sudo aptitude uninstall"  ?  Or something else?  And do I still have to do "sudo aptitude update" before uninstalling something?  Also, will using aptitude get rid of all the dependencies that aren't being used by something else?  Or do I need to type something else in addtion to aptitude?  Thanks.

Apt-get vs. Aptitude: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

If you install with aptitude, you will want to uninstall with aptitude. Aptitude does take care of the dependencies.

*And what Taurus said.

---

