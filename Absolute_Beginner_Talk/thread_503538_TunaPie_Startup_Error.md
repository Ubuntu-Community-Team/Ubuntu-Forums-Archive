---
title: "TunaPie Startup Error"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-07-18
Hello, everyone.

Anyone out there using TunaPie?  I just installed ti via apt-get, but when starting it I receive this error (in terminal):

```

Traceback (most recent call last):
  File "/usr/share/tunapie/Tunapie.py", line 23, in <module>
    import wxversion
ImportError: No module named wxversion

```

Any ideas on this one?  I'm stumped.

Thanks, everyone.

Take care.

---

### Post by DirtDawg on 2007-07-18
Hi RK. Do you have python-wxversion installed? If not, install it and try again.
```
sudo apt-get python-wxversion 
```

Please let us know if it works.

---

### Post by RKCole on 2007-07-18
Okay, I got this figured out.

python-wxversion was installed, but I have the wxPython repo in my /etc/apt/sources.list file, so ti was updated to version 2.8.4.0, but apparently TunaPie needs version 2.6.

I ran the command:
```

locate pythin-wxversion

```

which showed that there was still a .deb package for the older python-wxversion in

```

/var/cache/apt/archives/

```

I proceeded to uninstall python-wxversion (v2.8.4.0), then changed to the directory mentioned above and ran:

```

sudo dpkg -i python-wxversion_2.6.3.2.1.5ubuntu6_all.deb

```

Everything works great now.

Hope this may be of some help to others.

Guess I'm getting a little better at this Linux thing, eh? :)

Thanks, DirtyDawg, you definitely helped point me in the right direction.

Take care.

---

### Post by DirtDawg on 2007-07-18
> **RKCole said:**
> 

Thanks, DirtyDawg, you definitely helped point me in the right direction.

Take care.

Sure. Nice work.

---

