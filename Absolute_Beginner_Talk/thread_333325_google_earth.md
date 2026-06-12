---
title: "google earth"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-07
Would someone be so kind as to tell me how to remove google earth.  They tell how to do it in w---- but can't find anything for ubuntu

Thanks

---

### Post by The Joe on 2007-01-07
Did you install it through Synaptic/Adept? If so just go back to it in the GUI and remove it, or sudo apt-get remove {Google Earth here}

---

### Post by squrl on 2007-01-07
I think it was direct from goole. I went there and only see how to remove from w----

---

### Post by taurus on 2007-01-07
Where did you install it?  You can use the "**sudo rm -rf directory_name**" to move it if you wish.

---

### Post by wildkarde on 2007-01-07
google earth is most likely installed in /opt/google-earth.

You can find it by typing:

```
whereis googleearth
```

In that directory, you will find a file called uninstall.

run it by typing:

```
sudo ./uninstall
```

hope this helps

EDIT:::::::

What taurus said might not the best thing because googleearth has links for example in /usr/local/bin.  Removing the directory where googleearth is installed might leave dead links....

---

