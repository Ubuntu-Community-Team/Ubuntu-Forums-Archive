---
title: "ubuntu 7.10"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by jbalazs on 2007-12-14
At boot up I get this on my screen, it keeps coming back at boot up, how can I get it to stop ?

[IMG]http://i5.photobucket.com/albums/y176/foxhunter2/Screenshot.png[/IMG]

---

### Post by stchman on 2007-12-14
You could try reconfiguring your xorg.conf file.

```
sudo dpkg-reconfigure xserver-xorg
```

Give that a try and let us know if that worked.

---

### Post by jbalazs on 2007-12-15
No it's not working, it comes back every time I boot up. Any other  thoughts ?

Thanks

---

### Post by Riffer on 2007-12-15
Yeah had this problem too, quite easy to fix.  Go to the drop down menus, "System--->Preferences-->Keyboard" , I think in your case you need to set it to pc101 keyboard, try it its easy to switch if you have to.

---

### Post by jbalazs on 2007-12-15
Yes it was quite easy, it's working good now, thanks for you nice help

---

