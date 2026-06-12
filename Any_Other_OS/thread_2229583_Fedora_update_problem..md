---
title: "Fedora update problem."
date: 2014-06-14
forum: Any Other OS
---

### Post by Kupo12 on 2014-06-14
I tried to create an account in Fedora Forums but failed because my seems to have been blocked in there. I installed Fedora in one of my machines but whenever I type:
```
sudo yum update
```
It tells me that no update has been mark. (But there is an updated package, example is Firefox 30)
But if I do this
```
su -
yum clean all
yum update
```

The package (updates) is detected and downloaded.

---

### Post by QIII on 2014-06-14
Hello!

I assume the misspelling of "update" as "udpate" is a typo?

```
yum clean all
``` can actually slow things down a bit on the next update since you lose all of your metadata.

I use

```
su -
```
```
yum -y update
```

where the -y flag is "assume yes".

Assuming you are in the sudoers file, there isn't any practical difference -- except that sudo will give you the typical "are you sure" warnings.  But if you are not in the sudoers file, you'll get told you aren't in the sudoers file, that the incident will be reported and nothing will happen.

Are you getting a message similar to that?

---

### Post by Kupo12 on 2014-06-14
Yup, its a type, lol. It is not the "su -" and sudo that makes the difference. It is the "yum clean all" before "yum update". If I "yum update" only, there is no update detected. But if I "yum clean all", update is detected. It happened twice already in my machine.

---

### Post by QIII on 2014-06-14
I've never encountered that.

But "clean all" means that your metadata has to be refreshed, so it could be that it's not being refreshed otherwise.

---

### Post by Kupo12 on 2014-06-14
Maybe it's just a coincidence. I'll wait for new updates and test again.

---

