---
title: "Azureus problem"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-05
When I fire it up I get these:

---

### Post by lazyd2 on 2006-07-05
> There will most likely be a permission problem when Azureus tries to update.To avoid this problem change the following permissions: Note: Replace "username" with your username.  
```
sudo chown -R username:username /opt/azureus/plugins
```;-)

Or if the above does not work for you, try starting azureus with "sudo"...

---

### Post by rbalfour on 2006-07-05
do you have the unzip app installed?
It's not native to ubuntu.

---

### Post by Drakkor on 2006-07-05
Yes, I have unzip installed in Synaptic, sudo azureus does nothing ,
drakkor@drakkor:~$ sudo chown -R drakkor:drakkor /opt/azureus/plugins
Password:
chown: cannot access `/opt/azureus/plugins': No such file or directory
drakkor@drakkor:~$
This is my plugins directory:

---

### Post by bruenig on 2006-07-05
this kept happening to me, I decided to download it and install it manually. After doing that, I just chmod 777 all of the files and folders containing it and worked great.

---

### Post by Drakkor on 2006-07-05
bruenig,please explain for a noob. Thank you ! :mad:

---

### Post by doris.houng on 2006-07-05
Instructions for how to install Azureus plugins manually: [http://www.azureuswiki.com/index.php/InstallPlugins](http://www.azureuswiki.com/index.php/InstallPlugins)

And this is the plugin that you need to download: [http://azureus.sourceforge.net/plugin_details.php?plugin=azupdater](http://azureus.sourceforge.net/plugin_details.php?plugin=azupdater)

---

### Post by Drakkor on 2006-07-05
Thank You, Doris I got it installed.....   :D

---

### Post by doris.houng on 2006-07-05
No problem.  And by the way, you can call me Dorie if you'd like.  It's what most of my friends call me.  :)

---

### Post by Drakkor on 2006-07-05
Well that's just Hunky Dorie with me,lol  :-P

---

