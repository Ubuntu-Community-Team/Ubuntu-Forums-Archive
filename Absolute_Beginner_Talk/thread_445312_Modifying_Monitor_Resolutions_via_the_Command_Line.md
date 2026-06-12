---
title: "Modifying Monitor Resolutions via the Command Line"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by fasty on 2007-05-15
I've installed Ubuntu 7.04 Server.

I've installed ubuntu-desktop.

On restart, I got the nice kubuntu starting graphic, but once it was ready to move on, my (lcd) monitor indicated that it couldn't support the mode.

During the setup of desktop I'm pretty sure I only checked modes that would theoretically be valid, but I don't know what refresh it's using, etc., so I want to edit the configuration and take one of the higher resolutions out to see if that helps.

I tried editing /etc/x11/xorg.conf (which is what I've seen tons of references during my hours of searching these forums), but I don't even have a /etc/x11 directory. I guess no x-windows with this setup? Anyway, where would I find the configuration file I need?

Sorry, I'm a complete Linux newbie. I promise I've done a ton of browsing and searching before posting this. Might be super-dense, though, and any pointers would help.

(Also, installed gedit, but can't use it because it can't find the display properly. Can use nano, but it seems super-primitive... is there something else installed that I could theoretically use?)

Thanks very much,
Matthew

---

### Post by John.Michael.Kane on 2007-05-15
If your getting out of sync range after you boot.

You can try hitting Ctrl-Alt-F1 (or F2), you'll be dropped to a virtual console where you should then be able to type ```
sudo nano /etc/X11/xorg.conf
```

From there you can try hand editing your xorg using this method [http://ubuntuforums.org/showpost.php?p=2605716&postcount=2](http://ubuntuforums.org/showpost.php?p=2605716&postcount=2)

Another option while running in virtual console mode is to run 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by fasty on 2007-05-15
Thanks very much for your quick reply.

> **SD-Plissken said:**
> You can try hitting Ctrl-Alt-F1 (or F2), you'll be dropped to a virtual console where you should then be able to type ```
sudo nano /etc/X11/xorg.conf
```

From there you can try hand editing your xorg using this method [http://ubuntuforums.org/showpost.php?p=2605716&postcount=2](http://ubuntuforums.org/showpost.php?p=2605716&postcount=2)
Unfortunately there is no x11 directory inside my etc directory. That's where I think the problem lies.

> Another option while running in virtual console mode is to run 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Same problem, I'm afraid: it says "Package 'xserver-org' is not installed and no info is available."

Is there something I needed to install in addition to the main server install and ubuntu-desktop?

---

### Post by John.Michael.Kane on 2007-05-15
> **fasty said:**
> Thanks very much for your quick reply.


Unfortunately there is no x11 directory inside my etc directory. That's where I think the problem lies.


Same problem, I'm afraid: it says "Package 'xserver-org' is not installed and no info is available."

Is there something I needed to install in addition to the main server install and ubuntu-desktop?

If your building from a server install. 

edit your sources.list file.

```
sudo nano /etc/apt/sources.list
```

Uncomment all repositories by removing # at the beginning of the line. Do not remove double hash mark (##) leave these lines alone.

Save the file.

Next
```
sudo aptitude update
```

Followed by:
```
sudo aptitude upgrade
```

Now run this
```
sudo aptitude install xorg Kubuntu-desktop kdm
```

---

