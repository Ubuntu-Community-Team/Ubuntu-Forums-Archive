---
title: "Favorites from Windows"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by TheNemeses on 2006-11-27
o.k. since i am moving over to linux, ubuntu 6.10, i copied all my favorites from windows IE onto a usb drive, i get onto linux and it cant read them right, it wont open it up in firefox as a bookmark or w/e is there a special way to import them or convert them to make them viewable in firefox? thanks.

---

### Post by Bachstelze on 2006-11-27
Maybe install Firefox in Windows, it will convert your favourites from IE to FF, than you can copy them to use in FF in ubuntu.

---

### Post by seshomaru samma on 2006-11-27
Another way is to install IE 6.0 in Ubuntu (it's called IE4Linux) and import the favourites into it.
However , HymnToLife's suggestion of installing Firefox in Windows is much better cause it's easier and anyway you would want to use Firefox in Ubuntu and not IE (which is an inferior browser anyway ,more so on Linux)

---

### Post by d3v1ant_0n3 on 2006-11-27
I had a quick Google, and the best suggestion would seem to be something like already suggested.

Use Windows Firefox to grab al your firefox bookmarks.
Then install Foxmarks extension for firefox (found [ HERE](https://addons.mozilla.org/firefox/2410/).
Sync your bookmarks to it's server.
THen when you install ubuntu, install Foxmarks again, and resync your bookmarks. Et voila! All your bokmarks. Magic. If somewhat cumbersome.

---

### Post by wyldstryker on 2006-11-27
Firefox has a import option in it's bookmark manager ( Bookmarks/ Manage Bookmarks) that should allow you to  simply import the html favorites from the USB drive. All you should have to do is point to that directory. :-k

---

### Post by meng on 2006-11-27
Has anyone tried the Export Favorites function on IE6? (under File > Import & Export ...) I wonder if that would work.

---

### Post by richardward101 on 2006-11-27
Make a folder called links in your home directory and put all the .url files in it, open a terminal window and type:

```

cd links

```

now copy and paste the following command EXACTLY (its all one line):
```
rm ielinksforfirefox.html;for i in *.url; do url=`cat "$i"|dos2unix| grep -v .URL |grep URL |sed s/URL=*//g`;name=`echo $i|sed  s/'\..*'//g`;echo "<a href=\"$url\">$name</a>">>ielinksforfirefox.html;done
```
now there should be a file in the links folder with your bookmarks in it. Open firefox, go to manage bookmarks, import, from file, and select ielinksforlinux.html from the links folder in your home directory, and voila. Now you can delete the links directory.

This is slightly convoluted but it works and is easier than installing ies4linux or rebooting twice.

---

### Post by wyldstryker on 2006-11-27
> **wyldstryker said:**
> Firefox has a import option in it's bookmark manager ( Bookmarks/ Manage Bookmarks) that should allow you to  simply import the html favorites from the USB drive. All you should have to do is point to that directory. :-k


](*,)  please disreguard my method... it only works with bookmark files from firefox..     

sorry. :-#

---

