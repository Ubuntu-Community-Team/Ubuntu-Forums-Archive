---
title: "gksudo makes controls look funny!"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-10-11
When i say gksudo nautilis then the window controls look like windows 95 instead of my cool theme!

---

### Post by JonahRowley on 2006-10-11
This is because it's using root's gtk theme, which should be Human.  You can try running the theme switching program with sudo or copying your gtkrc file to root's directory or something.  I personally wouldn't worry about it, how much do you actually run as root?

---

### Post by systemintheglitch on 2006-10-11
hmmm.. i dont ever remember running the theme switcher as root, so how do i run it as root and then change root's theme>?..

---

### Post by systemintheglitch on 2006-10-11
ALSO: WHERE is root's directory? I thought I was root.. There are no other user folders in home.

---

### Post by systemintheglitch on 2006-10-11
WAIT: I dont think thats whats going on.. When i change to another theme,
everything is fine when i run gksudo commands.. Its just this one theme.. Whats wrong with this one theme?

---

### Post by jordanmthomas on 2006-10-11
I create links to my .fonts, .icons, and .themes folders in root's home folder 
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts

```

Now, using gksudo-run programs will look like whatever theme you are using.

---

### Post by systemintheglitch on 2006-10-11
Okay, that worked but why..

Why doesnt root just automatically use the same.. How do you choose root's theme?

Why does adding those links fix it?

---

### Post by jordanmthomas on 2006-10-11
To change root's theme, you would need to actually log on as root because of the way gnome-settings-daemon works (someone correct me if I'm wrong)

browse to /root in nautilus and show hidden files.
When you go to .themes or one of the links, it actually goes to your home folder.

The programs looked bad because the GTK apps were looking in /root/.themes for the current theme, and it wasn't there.  When you put the links, everything appears to be there.

I'm not sure why root doesn't automatically use the same, but I'm sure there does exist a reason.  If nothing else, it at least lets you know you're running as root (though I doubt that's the reason)



Instead of creating the links, you also could have copied the themes into /usr/share/themes I believe.

---

