---
title: "Java applet wont load"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by JustinJS on 2008-04-03
for some reason java seems to be working but what ever i do i can't get my school student information site to work [https://webts.bloomu.edu/txn/stinf](https://webts.bloomu.edu/txn/stinf) , Im using 8.04 and my friend usinf 7.10 also is having this problem. thank you,

---

### Post by Tristam Green on 2008-04-03
silly but obvious question, do you have the java environment installed?

if not, run in a terminal ```
sudo apt-get sun-java6-bin sun-java6-plugin sun-java6-jre
``` and let it take care of dependencies.

good luck ^^

---

### Post by JustinJS on 2008-04-03
yes i do

---

### Post by JustinJS on 2008-04-05
Anyone?

---

### Post by JustinJS on 2008-04-07
bump

---

### Post by spiderbatdad on 2008-04-07
I fixed mine by following the second post in this thread:[http://ubuntuforums.org/showthread.php?t=742715](http://ubuntuforums.org/showthread.php?t=742715)


but another person said his was fixed this way:

Quote:
Originally Posted by cinematography View Post
type this to install the plugin:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

and enter this to remove the plugin that conflicts with the java plugin
Code:

sudo apt-get remove gcjwebplugin
```

Could I ask what exactly was the problem? I could type that in but I still don't really understand what I typed.

---

### Post by JustinJS on 2008-04-07
> **spiderbatdad said:**
> I fixed mine by following the second post in this thread:[http://ubuntuforums.org/showthread.php?t=742715](http://ubuntuforums.org/showthread.php?t=742715)


but another person said his was fixed this way:

Quote:
Originally Posted by cinematography View Post
type this to install the plugin:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

and enter this to remove the plugin that conflicts with the java plugin
Code:

sudo apt-get remove gcjwebplugin
```

Could I ask what exactly was the problem? I could type that in but I still don't really understand what I typed.
It will not load the form and the bottom bar of firefox says "Start: applet not initialized"

---

### Post by JustinJS on 2008-04-08
AnyBody?

---

### Post by spiderbatdad on 2008-04-08
I just tried the link. I believe that page is broken, or improperly coded.  I use java applet windows at numerous sites. Try this link: [http://www.achaea.com/main.php](http://www.achaea.com/main.php)

Click "Play Now" A java applet will open. Wait a minute or two while it loads. If you get a login dialogue, you're java is working fine.

---

### Post by JustinJS on 2008-04-15
yeah it works idk what is wrong with my colleges site but ill guess ill just have to run that in windows

---

