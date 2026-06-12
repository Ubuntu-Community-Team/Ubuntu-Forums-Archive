---
title: "To uninstall a package + other questions..."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Aine Again on 2007-07-02
Evening, everyone.

I have a few questions for those reading this tonight. 

1.) I recently downloaded "MPlayer Movie Player," and I'd like to uninstall it. However, after using the "Add/Remove" option, it tells me to use Synaptic as it was a package install. How do I know what to delete re: MPlayer, so that I do not mess anything up?

2.) My cursor is acting funny. Whenever I am using a text application, whether this here textbox or OO Word Processor, or GAIM, after a bit, the cursor will shift the blinking "I" to a different place. Or shift the entire webpage downwards. I went to the "Mouse" option (System->Preferences->Mouse) but I cannot find where to disable this annoying feature.

3.) Where would I find a "Terminal Commands 101" page, with your basic commands? 

Cheers!
M.

---

### Post by Raineer on 2007-07-02
> 3.) Where would I find a "Terminal Commands 101" page, with your basic commands? 
Working on it, link in my sig!

---

### Post by wolfen69 on 2007-07-02
```
sudo aptitude update
```
```
sudo aptitude remove mplayer
```

---

### Post by Computer-Geek on 2007-07-02
> 
1.) I recently downloaded "MPlayer Movie Player," and I'd like to uninstall it. However, after using the "Add/Remove" option, it tells me to use Synaptic as it was a package install. How do I know what to delete re: MPlayer, so that I do not mess anything up?

You can Add/Remove applications from "Add/Remove" option or Synaptic Package Manager. First see synaptic if app is there then uninstall it from there or otherewise from "Add/Remove" option.

I guess i helped. Thanks.

---

### Post by wolfen69 on 2007-07-02
> **Raineer said:**
> Working on it, link in my sig!


[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)   <------- a great place to start

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)   <------- basically how to fix or install almost anything

---

### Post by Aine Again on 2007-07-02
This is curious. Here is what the terminal gave me when I typed in "sudo aptitude remove mplayer": 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  devede 
The following packages have been kept back:
  app-install-data-commercial libnautilus-burn4 nautilus-cd-burner 
  python-launchpad-bugs update-manager update-manager-core 
The following packages will be REMOVED:
  mplayer 
0 packages upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 10.2MB will be freed.
The following packages have unmet dependencies:
  devede: Depends: mplayer but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

[B]Install the following packages:
mplayer-nogui [2:1.0~rc1-0ubuntu9.1 (feisty-security)]

Score is -21[/B]

Accept this solution? [Y/n/q/?] 



What do I do with that?

---

### Post by bapoumba on 2007-07-03
Hello,
devede depends on mplayer. Removing mplayer will result in devede not having all the dependencies satisfied. So aptitude will remove devede too.

It looks like devede is broken, for some reason.

I assume you have multiverse repositories enabled as you installed mplayer. What happens is that aptitude offers you a way to fix things. Either you accept it, or you can try to fix the devede package first.

Do you need that package? Try to reinstall it (or remove it if you do not need it) and paste the error message if reinstall or remove do not work.
If either one does work, you should be able to remove mplayer with aptitude again.

---

