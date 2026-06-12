---
title: "help uninstalling mplayer"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Jesus4life0412 on 2007-05-30
i live in the usa and i want to uninstall mplayer and just want to use real player for legal reasons. but it wont let me uninstall mplayer.

---

### Post by Warbo on 2007-05-30
If you are trying to uninstall using the Applications > Add/Remove tool then it might not let you due to complex dependencies which it can't handle. If you look in System > Administration > Synaptic Package Manager you will find a more powerful (if less easy to use) program which should work (search for mplayer, look for a likely-sounding package with a green box next to it, click the green box and click "Mark for removal" then click Apply and go through the boxes until it starts uninstalling.

If that doesn't help then more information about the error would be nice :)

---

### Post by daimaru on 2007-05-30
in terminal type:_
```
sudo apt-get remove mplayer
```
done

if that does not satisfy u type:
```
sudo aptitude purge mplayer
```

just took the time to really read ur thread .. what - how can u not uninstall? what did u try? if the apt-get remove method does not work plz post output cause that should not be possible:)

---

### Post by Jesus4life0412 on 2007-05-31
i used add/remove and i get this error. Cannot remove 'mplayer'

One or more applications depend on mplayer. To remove mplayer and the dependent applications, use the Synaptic package manager. i will try the above post  next and post back after the outcome

---

### Post by Jesus4life0412 on 2007-05-31
opening the other package manager worked thank you

---

