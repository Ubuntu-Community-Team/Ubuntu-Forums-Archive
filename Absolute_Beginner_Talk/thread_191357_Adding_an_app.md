---
title: "Adding an app"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Mark Roberts on 2006-06-07
I just new enought to Ubuntu to be dangerous. I know PC very well, but am trying to slowly convert to Linux (Ubuntu) and loading apps as I need them.

I need to load a html editor and have found one called "Blulefish". the site says:

"Debian and Ubuntu users just run apt-get install bluefish and Bluefish will be downloaded, configured and installed on your system."

Ok, this is great. Just where do I enter this apt-get command.

I tried terminal and that didn't work. Thought I would get a starting point before I screwed up something that I could fix. 

Any Assistance would be appreciated. Thanks.

---

### Post by Jagot on 2006-06-07
The package for Bluefish is in a repository which is not enabled by default with your installation - the universe repository.  You can find out about enabling it in these links:

[http://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](http://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)
[http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

After enabling, you should then be able to install using this command in terminal:

```
sudo apt-get install bluefish
```

You can also use Synaptic, which you can find in System, Preferences, Synaptic Package Manager.  Just search for bluefish and you can install there.

Having said that, probably the easiest way to get Bluefish is to go to the Applications menu, then click Add/Remove at the bottom.  Now in the program that pops up go to the Programming section.  On the right tick the box to make it show unsupported applications and Bluefish is there for you to install.

---

### Post by Delkster on 2006-06-07
You could also just use the "Add/remove" option in the Applications menu (it will find Bluefish if you have the universe repository enabled).

---

### Post by Mark Roberts on 2006-06-07
thanks for your suggestions, I will give them a go.

I tried just adding through add/remove and got an error. Maybe it was because of the universe respository think. I will chech that as well.

Again, thanks for your assistance.

---

### Post by mostwanted on 2006-06-07
[QUOTE=Mark Roberts]thanks for your suggestions, I will give them a go.

I tried just adding through add/remove and got an error. Maybe it was because of the universe respository think. I will chech that as well.

Again, thanks for your assistance.[/QUOTE]

Mark, every time you get an error message and decide to post about it, post the error as well! Otherwise, people won't know what to do to help you.;)

---

