---
title: "No Video when booting to CL"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Bendrx on 2008-04-12
I've got this posted in the general help section and while looking for an answer came across a post suggesting to  post here.

I've got Gutsy setup to boot to CL instead of X. The problem is when it first boots there is no video at all. Just a blank screen. I assumed it was booted to a usable state and was able to log in and start X, I just couldn't see a prompt or anything else until I loaded X. When I log out of X I have a prompt and everything works fine. Upon reboot the same thing repeats. I'm running the latest Nvidia drivers. I've looked around in the forums/google but I'm not really sure what to look for. I assume that the other run levels 3-5 are working as they would out of the box but I haven't tried them. I can't recall the exact name but I removed the link to S30GDM per a post I found on setting the system to not load X on boot. Any help or direction will be greatly appreciated.

Thanks,
Bendrx

---

### Post by Jose Catre-Vandis on 2008-04-12
Please describe exactly what you did to allow booting to prompt, i think i see but be more explicit...

---

### Post by Bendrx on 2008-04-12
In etc/rc2.d there was a link to load gdm. I deleted the file called S30gdm. After that I started having the issue, but I did succeed in booting to CL not the GUI. I've since copied it from runlevel 3 and now it logs back into Gnome and everything like it used to. I guess really I would like to know how to enable video independently of X11/GUI.

---

### Post by spiderbatdad on 2008-04-12
> **Bendrx said:**
> In etc/rc2.d there was a link to load gdm. I deleted the file called S30gdm. After that I started having the issue, but I did succeed in booting to CL not the GUI. I've since copied it from runlevel 3 and now it logs back into Gnome and everything like it used to. I guess really I would like to know how to enable video independently of X11/GUI.

Never tried this, but how about moving 'gdm' out of /etc/init.d  and locating it in /opt/. Then your terminal command would be /opt/gdm

---

### Post by Jose Catre-Vandis on 2008-04-12
I have used this in the past (on Dapper and Edgy) which I think does much the same as you have done, which stops gdm from loading in the first place. have not tried this out on Fiesty or Gutsy (or Hardy!) and do not know the reverse command:
```
sudo update-rc.d -f gdm remove
```

[edit] this is still a valid command. To put the startup back you first need to know where to put it, so the command would be SOMETHING like this```
sudo update-rc.d gdm defaults 12 30
```


So, suggest:

You could always use these two commands manually, or add one or the other to your start up scripts:
```
sudo /etc/init.d/gdm stop
```
and

```
sudo /etc/init.d/gdm start
```

---

