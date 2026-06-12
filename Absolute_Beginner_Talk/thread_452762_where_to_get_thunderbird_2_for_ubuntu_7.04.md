---
title: "where to get thunderbird 2 for ubuntu 7.04?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-23
Hi
What should i do to install Thunderbird 2 in Ubuntu 7.04 ?

Thanks

---

### Post by Gannin on 2007-05-23
The first step is to go get it from [http://www.mozilla.com](http://www.mozilla.com).

---

### Post by Sparkster185 on 2007-05-23
I just check the official repository list ([http://packages.ubuntu.com](http://packages.ubuntu.com)) and it doesn't have 2.X, only 1.5.X.  You're probably going to have to compile it yourself.

---

### Post by legolas_w on 2007-05-23
Thank you for reply.
certainly i am not in a level that i could compile it :-)
I will wait until you guys compile it, maybe i could compile thunderbird 3.0


thanks

---

### Post by Sparkster185 on 2007-05-23
Assuming you have all the dependencies, compiling stuff from source isn't too hard.  The tarball should come with a readme file.  Normally you just need to configure, make, make install and you're done.

---

### Post by dpar on 2007-05-23
I just downloaded it from mozilla. They have install instructions.

---

### Post by Inxsible on 2007-05-23
Got to  [http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/) and download the deb package and store it on the desktop. Then simply double click the deb file that you downloaded. That's what I did.

---

### Post by jbrown96 on 2007-05-23
The easiest way, imho, is to use Automatix. I'm not sure if they have 2.0 for x86_64 Ubuntu, maybe only 1.5. However, I'm using 2.0 for x86 with no problems

---

### Post by legolas_w on 2007-05-23
where you have download your Thunderbird 2 which works in ubuntu?

thanks

---

### Post by crimesaucer on 2007-05-23
I would say the easiest way is to follow this guide: [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

all you have to do is follow the 4 terminal codes and it downloads it with wget, then unpacks it and installs it to the /opt folder, then it creates all of the links from your old Thunderbird folders to point to your new Thunderbird 2.

Then all you have to do is change your icon in your menu to the new location of Thunderbird2.

the 4 commands from that guide:

As of this writing, the latest version is 2.0.0.0
```
wget -c http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz 

```

Extract the zipped archive
```
sudo tar -C /opt -zxvf thunderbird-2.0.0.0.tar.gz 
```

Make launcher command available to all users
```
sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird 
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
```

You can now launch the new version with your old profile from the command-line. By running:
```
thunderbird
```

Then change the icon launcher: 

"You may need to adjust the properties of your Gnome panel & menu launchers accordingly. To modify Gnome panel launchers right click and select Properties. Then change the old command to the new command if you changed it from mozilla-thunderbird to thunderbird. To change your link in the Applications menu, use Applications > System Tools > Application Menu Editor. This lets you use the official icons if you've gone through the trouble of updating them"

---

### Post by Inxsible on 2007-05-25
I have attached the script to download and install the latest thunderbird 2. All you have to do is double click the file. Give it a try.

---

### Post by Eyebee on 2007-05-27
I used Automatix too here.

It was a cinch. Automatix, removed 1.5 and then installed 2.0 and put it in the menu.

---

### Post by pappapump on 2007-05-27
> **Inxsible said:**
> I have attached the script to download and install the latest thunderbird 2. All you have to do is double click the file. Give it a try.

Dude you rock.
Thanx!

---

