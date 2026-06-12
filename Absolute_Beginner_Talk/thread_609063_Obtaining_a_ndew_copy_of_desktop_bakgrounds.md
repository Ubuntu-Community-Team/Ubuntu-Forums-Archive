---
title: "Obtaining a ndew copy of desktop bakgrounds"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-11-10
Shortly after installing Ubuntu [7.04] I customized the Human theme desktop background, making it impossible to revert to it. I've decided to go back to the Human theme. Is there a file I can download that would enable me to restore the background that goes with the Human theme?

Thanks

---

### Post by Nano Geek on 2007-11-10
Running this should put the wallpapers in your home folder.```
apt-get source gutsy-wallpapers
```To put them back where Ubuntu can find them run this.```
 sudo mv ~/gutsy-wallpapers-0.17/elephant-skin.jpg /usr/share/backgrounds

``` Or ```
 sudo mv ~/gutsy-wallpapers-0.17/warty-final-ubuntu.png /usr/share/backgrounds

```Depending on which one you want to copy over.

---

### Post by Eric Weir on 2007-11-12
> **asjdfwejqrfjcvm msz34rq33 said:**
> Running this should put the wallpapers in your home folder.```
apt-get source gutsy-wallpapers
```

I haven't upgraded to gutsy, yet. Maybe I should put up with the wallpaper I have  for the time being. I assume when I do upgrade I'll have the default set of wallpapers available to me.

Thanks

---

