---
title: "uninstall programs problem"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2007-05-05
I am trying to uninstall avg antivirus and when I use synaptic package manager and check to uninstall avg it runs a bit then stops and says I have error 150 and will not uninstall avg. Any ideas?
I installed avg just to see if it would work and it will except for updates. 
Thanks

---

### Post by nixclusive on 2007-05-05
Try the command line, open the terminal and enter:```
sudo apt-get remove <package-name>
```Where <package-name> is the name of the package you are trying to uninstall. If you'd like to remove the configuration data as well:```
sudo apt-get --purge remove <package-name>
```

---

### Post by mikewhatever on 2007-05-05
Try this way [http://ubuntuforums.org/showthread.php?t=426070](http://ubuntuforums.org/showthread.php?t=426070)

---

