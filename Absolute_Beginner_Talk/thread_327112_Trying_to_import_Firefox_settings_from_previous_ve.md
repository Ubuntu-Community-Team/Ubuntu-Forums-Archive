---
title: "Trying to import Firefox settings from previous version"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-12-28
Hey folks. I've got FF 2.0 now, and have had it for a few weeks now . . .my problem is that I still can't figure out what to do with my little backup folder I created from the previous settings I had . . .I'd like to import them over to this version, because it took me a REALLY long time to customize it to be just right for me. Any thoughts?

---

### Post by bruenig on 2006-12-28
Just replace your new .mozilla directory with the old one. The .mozilla directory is located at /home/username/.mozilla

---

### Post by CheshireMac on 2006-12-29
> **bruenig said:**
> Just replace your new .mozilla directory with the old one. The .mozilla directory is located at /home/username/.mozilla
Okay, so I tried this, and terminal is saying that the directory doesn't exist . . .I've got the settings folder in desktop right now . . .here's what I've got . . .


mac@mac-desktop:~$ mv /mac/desktop/ffsettings ~/home/mac/.mozilla
mv: cannot stat `/mac/desktop/ffsettings': No such file or directory
mac@mac-desktop:~$ mv /home/mac/Desktop/ffsettings ~/home/mac/.mozilla
mv: cannot move `/home/mac/Desktop/ffsettings' to `/home/mac/home/mac/.mozilla': No such file or directory

So . . .what can I do to find out where I need to move it, and how to do it the right way?

---

### Post by bruenig on 2006-12-29
> **CheshireMac said:**
> Okay, so I tried this, and terminal is saying that the directory doesn't exist . . .I've got the settings folder in desktop right now . . .here's what I've got . . .


mac@mac-desktop:~$ mv /mac/desktop/ffsettings ~/home/mac/.mozilla
mv: cannot stat `/mac/desktop/ffsettings': No such file or directory
mac@mac-desktop:~$ mv /home/mac/Desktop/ffsettings ~/home/mac/.mozilla
mv: cannot move `/home/mac/Desktop/ffsettings' to `/home/mac/home/mac/.mozilla': No such file or directory

So . . .what can I do to find out where I need to move it, and how to do it the right way?

Ok I am assuming that you have a directory, what formerly was a .mozilla directory or something similar on your desktop called ffsettings and that your user name is mac. You appear to have confused the ~ and what it means. The ~ literally stands for /home/mac, so when you are doing ~/home/mac, you are actually doing /home/mac/home/mac which is where much of the problem is happening.

What you must do is first remove the current .mozilla directory, you can either move it or rename it if you want to save it for whatever reason. 
To move it do
```
mv ~/.mozilla ~/.mozilla.old
```

or to remove it
```
rm ~/.mozilla
```

Now to move the ffsettings directory on your desktop, remember that ~ is the same as /home/mac, so you can either use ~ or you can type out /home/mac but don't do both because that is redundant and causes you to call on a directory /home/mac/home/mac which doesn't exist.
Ok so to move it
```
mv ~/Desktop/ffsettings ~/.mozilla
```

or 

```
mv /home/mac/Desktop/ffsettings /home/mac/.mozilla
```

Hopefully I have cleared up that ~ confusion.

---

