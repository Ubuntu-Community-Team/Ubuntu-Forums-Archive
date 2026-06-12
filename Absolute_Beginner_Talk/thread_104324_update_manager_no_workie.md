---
title: "update manager no workie"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by mcopeland@pobox.com on 2005-12-15
The notifier works fine but when I click on the icon or try to manually start UM nothing happens. 
Any suggestions?

thanx
Mike

---

### Post by Qrk on 2005-12-15
Try running it in the terminal and see what errors pop out. Post them here so everyone cany help you as well.

```
gksudo update-manager
```

For the time being; don't worry. Its not an important app. Just use 

```
sudo apt-get update
sudo apt-get upgrade
```

instead.

---

### Post by darth_vector on 2005-12-15
sudo apt-get dist-upgrade

is a better option (rather than just upgrade) since it "intelligently handles changing dependencies with  new  versions  of  packages".

---

