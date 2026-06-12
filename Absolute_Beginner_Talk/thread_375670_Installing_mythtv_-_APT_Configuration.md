---
title: "Installing mythtv - APT Configuration?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by burnt1ce85 on 2007-03-04
Hi. I'm new to Linux and im trying to get mythtv installed.

The following link explains so:[URL="http://parker1.co.uk/mythtv_ubuntu.php"]
http://parker1.co.uk/mythtv_ubuntu.php[/URL]

But im having trouble applyling the APT Configuration. I'm not sure what to do with the given sources.list. If anybody can tell me that would be great. 

THanks!

BTW, im using Ubuntu 6.10

---

### Post by Scorpuk on 2007-03-04
you will have a sources.list file in the same location:

```
/etc/apt/
```

If you don't want to replace your copy with the one from the site then just add the following three lines from it:

```
# Universe and multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe multiverse
```


It won't matter where you put it, but easiest to place it at the end.


If you're not sure how to add them then open a terminal window and type the following commands:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

sudo gedit /etc/apt/sources.list
```

The first one to backup your sources.list incase you make a mistake. Always a good idea. :-)

You will be asked for your password. This will be the same one you used to log into your computer with and it won't be displayed on the screen so don't worry.

The second command will open a text editor with your sources.list file.

Once you add those lines save and close the file.


To make sure everything is ok now type the following command:


```
sudo apt-get update
```

and then just follow his instructions...



BTW: Once you add the universe and multiverse repositories mythtv will be listed in synaptic package manager. But I do highly recommend Garry Parkers site as it helped me a great deal when I installed mythtv.

---

