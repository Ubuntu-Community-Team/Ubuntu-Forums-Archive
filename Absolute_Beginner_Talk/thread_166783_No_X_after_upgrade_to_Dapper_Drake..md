---
title: "No X after upgrade to Dapper Drake."
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by PaLoBo on 2006-04-27
Hi all. 

Yesterday I left my system updating to dapper drake using "gksudo "update-manager -d" " as instructed by the wiki. All seemed to go weel but after the reboot i had no X.

In the log file I get a few warnings anf the following errors:

```

(EE) Failed to load /usr/lib/xorg/modules/extensions/libGlcore.so
...
(EE)Failed to load module "Glcore" (loader failed, 7)
...
(EE)Failed to load module "Nvidia" (Module does not exist)
...
No driver available
...
Fatal server error:
 No screens available.

```

If somebody could help out here that would be great.

I had to boot using the liveCD in order to be able to post (maybe there was another way but being a newbie this was my best bet:) )

Also, how can I access my data on /home using the liveCD. How do I mount my file system?

Thanks for any and all help.

Cheers,
P.

---

### Post by Haegin on 2006-04-27
You need to reinstall the latest nvidia driver as the kernel will have changed. From the terminal try the following:
```

sudo apt-get install nvidia-kernel nvidia-glx

```
That should get you up and running I think...
If not then try this:
```

sudo nano /etc/X11/xorg.conf

```
Then uncomment all the lines in the modules section (should be glx and dri i think but dont quote me on that) and change the driver in the device section to "nv" instead of "nvidia"
Then press ctrl+O to save and ctrl+x to exit nano.
Then just restart X using 
```

sudo /etc/init.d/gdm start

```
(assuming you havent done anything odd like install InitNG and you just boot normally...)
If that doesn't work try restarting your computer using 
```

sudo shutdown -r now

```

---

### Post by PaLoBo on 2006-04-27
Thanks!

Reinstalled nvidia drivers and now all seems to be working great!

---

