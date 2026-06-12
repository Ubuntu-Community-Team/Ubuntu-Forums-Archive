---
title: "driver investigations"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by isandir on 2005-12-03
Hey,  

It is likely that my topic has been covered somewhere once, but when you do any search with the word driver in it.... well good luck.  I tried and now I am here.  I know ubuntu showed me what drivers my nic was using when it auto detected in the install.  Now that i have my computer set up is there anyway to easily see what driver each of my components is using?  I am really asking this because I may want to install other distros on different partitions, and they dont usually auto detect as well as ubuntu.  The problem is they are more than willing to give me a list of 100+ drivers to try with no hint at what might be appropriate.   

To sum it all up i would like to know if there is a nice way to view the drivers in use so I know the name to pick off the list of device drivers in other distros.

---

### Post by Kyral on 2005-12-04
```
lsmod
``` will give you a list of modules currently loaded (drivers tend to be called modules)

---

