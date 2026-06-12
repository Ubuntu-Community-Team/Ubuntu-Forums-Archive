---
title: "Opera won't use flash plugin"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Sugi on 2007-12-18
I installed flash plugin for opera.  Everything installed corrently.  I even check if firefox could use the flash plugin and everything worked.  I looked inside of plugins tab for opera and it showed that the flash plugin was installed, but when I go to a website with flash it just shows a gray box.  I hover my mouse over the gray box and it says click to activate.   I click it and nothing happens.

What should I do to fix?

---

### Post by Sugi on 2007-12-19
Im under Gutsy with Opera 9.24.

---

### Post by RomeReactor on 2007-12-19
Hi. Try this: close Opera and open a terminal (Applications->Accessories->Terminal) and run:
```
sudo cp /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/opera/plugins
```
and enter your password. Now open Opera and go to "Tools-->Preferences-->Advanced-->Content-->Plug-in options" and make sure the plugin path only reads /usr/lib/opera/plugins; close Opera and open it again and go to a page that requires flash to see if it's working now.

Please note that this method won't work on Ubuntu 64 bit.

---

### Post by Sugi on 2007-12-19
already did that as well.  I have the flashfile in both firefox and opera.  I even checked the path as well. :-/

---

### Post by RomeReactor on 2007-12-19
Are you using 32 bit Ubuntu? and did you make sure that "Tools-->Preferences-->Advanced-->Content-->Plug-in options->Plugin path" only reads /usr/lib/opera/plugins?

---

### Post by FuturePilot on 2007-12-19
The new version of Flash is currently broken in Opera 9.24 :(

---

### Post by RomeReactor on 2007-12-19
More [bad news]("http://ubuntuforums.org/showthread.php?t=634888&page=2"), then. I guess you can try [Opera 9.50]("http://www.opera.com/download/index.dml?opsys=Linux%20i386&lng=en&ver=9.50b&platform=Linux%20i386&local=y").

---

### Post by LaRoza on 2007-12-19
> **RomeReactor said:**
> More [bad news]("http://ubuntuforums.org/showthread.php?t=634888&page=2"), then. I guess you can try [Opera 9.50]("http://www.opera.com/download/index.dml?opsys=Linux%20i386&lng=en&ver=9.50b&platform=Linux%20i386&local=y").

Thanks. I just recently ran into problems with Opera and Flash, after never experiencing when I did a reinstall of Ubuntu (I repartitioned my hardrives, big makeover).

I am using Opera 9.5b because of your post, Flash works fine now. Thanks.

(Opera works well to, so far, so don't worry about using it!)

---

### Post by magnifica on 2007-12-19
Not sure that it works in 9.5b either.  I just installed 9.5b and no joy.  If anyone does know how to get it working please let us know.

---

### Post by LaRoza on 2007-12-19
> **magnifica said:**
> Not sure that it works in 9.5b either.  I just installed 9.5b and no joy.  If anyone does know how to get it working please let us know.

When I just installed 9.5b, I had not altered any other settings, so if you followed the above instructions, maybe undoing whatever you did will work.

---

### Post by RomeReactor on 2007-12-19
> **LaRoza said:**
> Thanks. I just recently ran into problems with Opera and Flash, after never experiencing when I did a reinstall of Ubuntu (I repartitioned my hardrives, big makeover).

I am using Opera 9.5b because of your post, Flash works fine now. Thanks.

(Opera works well to, so far, so don't worry about using it!)

You're welcome, though all I did was find that thread. :P

magnifica, if you did follow th previous instructions, close Opera and try removing the libflashplayer.so from /usr/lib/opera/plugins:
```
sudo rm /usr/lib/opera/plugins/libflashplayer.so
```
Also delete the **.opera** directory in your home folder:
```
rm -R ~/.opera
```
Then open Opera again.

---

### Post by magnifica on 2007-12-19
Hmm.. i have the flash plugin in the Mozilla folders but not in the Opera plugin folder.  it wont let me extract the flash plugin to the usr/lib/opera/plugin folder.  (because of permission denied or something...  )

is there another way to install this?  i dont know what the root password is...  i didnt make one on install.

---

### Post by LaRoza on 2007-12-19
> **magnifica said:**
>  i dont know what the root password is...  i didnt make one on install.

It is your password.

---

### Post by magnifica on 2007-12-19
OK.. I finally sorted this out by following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=403629&highlight=opera+flash") (thanks RomeReactor!)

---

### Post by Gonkers on 2007-12-19
I have "successfully" installed the latest version of the flash plugin on a fresh install of Ubuntu 7.10. It works fine in firefox, but I just get blank boxes in Opera with a tool tip of "Title: Click to activate and use this control." I have checked the plugins section of Opera and it appears to be installed/recognized but just doesn't work.

application/futuresplash spl
application/x-shockwave-flash swf
/usr/lib/opera/plugins/libflashplayer.so

I have not yet tried v9.50b of Opera, but will try to upgrade.

---

### Post by LaRoza on 2007-12-19
> **Gonkers said:**
> 
I have not yet tried v9.50b of Opera, but will try to upgrade.

Upgrading fixed it for me.

Opera 9.5b is very stable so far, and all the features (and more) are there. Because your settings are stored in you home directory, you can save all your settings without problems (themes, passwords, etc).

I recommend you use it.

---

### Post by Gonkers on 2007-12-19
> **LaRoza said:**
> Upgrading fixed it for me.

Opera 9.5b is very stable so far, and all the features (and more) are there. Because your settings are stored in you home directory, you can save all your settings without problems (themes, passwords, etc).

I recommend you use it.


Flash appears to work with 9.5b, but I don't have sound. Time to track that down. Thanks all.

::UPDATE::
After reinstalling Opera 9.5b video AND sound now work.

---

### Post by GoPool on 2007-12-20
Just copy the mozilla plugins to opera with this command to get flash working in opera.
```
sudo cp ~/.mozilla/plugins/* /usr/lib/opera/plugins
```

---

### Post by brownknight on 2007-12-20
Same experience here. The opera from ubuntu repository doesnt work with flash. After downloading/installing the latest beta from opera flash works now. Thanks to all you guys.

---

### Post by LaRoza on 2007-12-20
> **brownknight said:**
> Same experience here. The opera from ubuntu repository doesnt work with flash. After downloading/installing the latest beta from opera flash works now. Thanks to all you guys.

I didn't know it was in the repos. I always downloaded the .deb.

I noticed the beta does have a few quirks, but nothing major. It is stable and everything works fine, aside from a possible display issue once and a while, and a theme issue for one session.

---

### Post by Presto123 on 2007-12-20
I'm curious...sorry to deviate from the q, but has anyone played with the voice features? I had it when I had Windoze a few months ago and wonder if they improved on it.

---

### Post by LaRoza on 2007-12-20
> **Presto123 said:**
> I'm curious...sorry to deviate from the q, but has anyone played with the voice features? I had it when I had Windoze a few months ago and wonder if they improved on it.

I forgot about that. I will have to try it someday.

I am sure it has been improved in that time. What issues did you have?

---

### Post by Presto123 on 2007-12-20
> **LaRoza said:**
> I forgot about that. I will have to try it someday.

I am sure it has been improved in that time. What issues did you have?

Oh no, none. I don't have it installed. I was just curious. It seemed to be a neat feature, but was a bit buggy a few months ago.

---

### Post by LaRoza on 2007-12-20
> **Presto123 said:**
> Oh no, none. I don't have it installed. I was just curious. It seemed to be a neat feature, but was a bit buggy a few months ago.

I will try it tomorrow hopefully and report back.

---

