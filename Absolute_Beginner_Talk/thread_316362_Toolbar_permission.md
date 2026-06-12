---
title: "Toolbar permission"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Cikrum on 2006-12-10
Hello,
I recently downloaded song bird the new media player and I have put it in my home folder. I then put a launcher for it on the top toolbar for easy access.
At first I couldn't open it because it said permission denied. So I used chmod to change the permission and it began to work fine and would run from laucher. When I rebooted the computer I began to get the permission denied error again. I am sure if i were to use the chmod I could change the permission again but I was wondering if there was a way to keep the perission the same. 
Thanks,
Cikrum

---

### Post by taurus on 2006-12-10
Change to the directory where you've saved song bird and paste the output of this command here!

```
ls -la
```

---

### Post by useResa on 2006-12-10
Not sure if this may help, but I used to have songbird installed on a Debian OS and found a very helpful installation guide [here](http://www.debianadmin.com/install-songbird-and-play-your-music.html).

One of the items that is indicated is > 
Now you need to change owner permissions on songbird directory using the following command if you want to run as particular user
 #chown -R ruchi:ruchi songbird
Where you have to replace *ruchi* with your own login name.

---

### Post by Cikrum on 2006-12-10
Well I think I fixed the problem. I believe the problem was with the icon. I used a icon the was used by another program, so when I removed the app and placed a new one there with no icon it worked and continues to work. Thanks for the help.
Cikrum

---

### Post by useResa on 2006-12-11
First of all, glad to read that you have songbird working.  If you would like to use an icon, you will find instructions on how to do this in the link I posted earlier. > Now you need to add this to application menu for this you need to download songbird image from [here]("http://www.songbirdnest.com/download") under buttons section once you download that you need to name it as songbird.png (you can rename any of your choice).Now you need to copy this file to /usr/share/pixmaps directory  #cp songbird.png /usr/share/pixmaps/

---

