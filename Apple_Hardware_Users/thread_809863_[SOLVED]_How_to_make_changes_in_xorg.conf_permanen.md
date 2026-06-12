---
title: "[SOLVED] How to make changes in xorg.conf permanent?"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by a1234 on 2008-05-27
Here is the sit:

I have a partition on my mBP3 as an ubuntu persistence and is doing well except for the changes made in xorg.conf to enable scrolling for my BT mouse. Every time I reboot xorg.conf updated itself and made a copy of my change with some 12 digit # in thhe folder X11. Even though I stop trying it is still generating copies.

Question 1) Anyway of making the changes permanent?
         2) If not how to stop the copy from forming?
         
        
Thanks below is the link to the changes. Apparently no problem with regular install. Just unique in Persitence!

[http://peterc.org/2008/64-how-to-enable-vertical-mouse-wheel-scrolling-in-ubuntu-hardy-on-vmware-fusion.html](http://peterc.org/2008/64-how-to-enable-vertical-mouse-wheel-scrolling-in-ubuntu-hardy-on-vmware-fusion.html)

---

### Post by a1234 on 2008-05-30
No taker?

---

### Post by frog_pilot on 2008-05-31
you need root privileges to change the files outside your home folder. It should be documented in almost any ubuntu-wiki available on the web.

for gnome execute
```
sudo gedit /etc/X11/xorg.conf
```


for kde
```
sudo kate /etc/X11/xorg.conf
```



now you will have write access to xorg.conf.

---

### Post by a1234 on 2008-06-01
> **frog_pilot said:**
> you need root privileges to change the files outside your home folder. It should be documented in almost any ubuntu-wiki available on the web.

for gnome execute
```
sudo gedit /etc/X11/xorg.conf
```


for kde
```
sudo kate /etc/X11/xorg.conf
```



now you will have write access to xorg.conf.

That was the first thing I did to enable scrolling. My problem is the editting is ?archived by the ?Xserver like so

ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# cd /etc/X11
root@ubuntu:/etc/X11# ls
app-defaults             xkb                       Xresources
cursors                  xorg.conf                 xserver
default-display-manager  [COLOR="Red"]xorg.conf.20080601060008[/COLOR]  Xsession
fonts                    [COLOR="Red"]xorg.conf.20080601060705[/COLOR]  Xsession.d
rgb.txt                  [COLOR="Red"]xorg.conf.2008060106171[/COLOR]4  Xsession.options
X                        [COLOR="Red"]xorg.conf.20080601155619[/COLOR]  Xwrapper.config
xinit                    [COLOR="Red"]xorg.conf.20080601160029[/COLOR]
root@ubuntu:/etc/X11# 

As you can see the gedited ones are  in red and the xorg.conf is the unedited one generated everytime I reboot. As you can see from the user that this is in persistence mode. I am assuming that editting the xorgconf is not possible. Any thought ?

---

### Post by frog_pilot on 2008-06-01
Not the ```
ls
``` of the folder is the thing...

What do you do on saving your changes? Choose "save as" and type ```
xorg.conf
```

Or figure out your preferred xorg.conf backup and execute e.g.

```
sudo cp /etc/X11/xorg.conf.20080601155619 /etc/X11/xorg.conf
```

BTW You dont need to log in as root in ubuntu at all. ```
sudo -s
sudo -su
``` doesnt meet the ubuntu policy... :)

---

### Post by a1234 on 2008-06-04
Thanks for the advise. I did this to make the changes permanent.

#! /bin/sh
### BEGIN XORG INFO
# Provides: xorg.onf
# Required-Start:
# Required-Stop:
# Default-Start: S
# Default-Stop:
# Short-Description: enable same xorg.conf
### END XORG INFO

cp -rf /etc/X11/xorg.conf.20080604052700 /etc/X11/xorg.conf

It did the trick. But the scrolling is still not working.

---

### Post by russo.mic on 2008-06-06
I still don't understand why you don't just execute gedit or kate to edit xorg.conf directly.  or nano, or whatever.  

Your editing the backup copies then copying them over xorg.conf.  

Seems like a roundabout way of getting there. as long as you execute the edit command with sudo in front, there should be no trouble.

Russo

---

### Post by cyberdork33 on 2008-06-06
I think that the main thing everyone is missing here is that he is running in persistence mode... I think that means he is running Ubuntu from the LiveCD, and storing session data on a thumbdrive or something (a partition on his hard drive it sounds like). 
[http://rootprompt.org/article.php3?article=10142](http://rootprompt.org/article.php3?article=10142)

He edits xorg.conf, but then when he starts up again, xorg.conf is regenerated replacing his customized file. Now, he is essentially copying the backup back over the original on each boot so that he gets his custom config back.

nano vs kate vs gedit, etc doesn't matter. You whatever editor you want.

---

