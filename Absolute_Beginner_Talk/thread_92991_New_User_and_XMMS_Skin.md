---
title: "New User and XMMS Skin"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by bluevoodoo1 on 2005-11-20
Greetings all. 

I have finally installed and configured a dual boot Ubuntu and XP system. Hopefully XP will be gone in the future... Now that the difficult part is (hopefully) through. I thought I would start with some "easy" software installation. I got XMMS through Synaptic and it's running beautifully... I have my .OGG and .mp3 files going, so I thought I'd do something basic like changing the skin.
I downloaded a skin and read around here that I just have to put it in ~/.xmms/Skins folder. Well, I'm not seeing that folder at all. Did I do something wrong with the installation? I tried messing around with one of its folders usr/share/xmms but it said I "did not have permission to write to this folder." Does that have something to do with "root"? If needed, a step-by-step guide with the code through the terminal would be great. Any suggestions or help would be greatly appreciated. Thank you.

---

### Post by fuscia on 2005-11-21
sudo mv location/filename /usr/share/xmms/Skins/ 

(notice upper case 'S'). if you want a skin that comes in a .zip file, you have to install unzip, first, which you can do from the synaptic package manager.

---

### Post by public_void on 2005-11-21
the directory your looking for in hidden, it is /home/YourUserName/.xmms/Skins. Make sure the directory shows hidden folders. I think its in the "View" menu (not sure of that though).

---

### Post by bluevoodoo1 on 2005-11-21
Thanks! All I had to do was adjust the view to allow hidden files like mentioned!

---

### Post by xmastree on 2005-11-21
Did you know that XMMS can use Winamp skins?

[http://www.ubuntuforums.org/showpost.php?p=307231&postcount=7](http://www.ubuntuforums.org/showpost.php?p=307231&postcount=7)

---

### Post by bluevoodoo1 on 2005-11-21
[QUOTE=xmastree]Did you know that XMMS can use Winamp skins?

[http://www.ubuntuforums.org/showpost.php?p=307231&postcount=7](http://www.ubuntuforums.org/showpost.php?p=307231&postcount=7)[/QUOTE]

Very nice! I'll be sure to get some more skins!

---

### Post by fuscia on 2005-11-21
is there anyway to use the .wal skins?

---

### Post by fribacka on 2006-11-19
I like Xmms because it's simple and fast. But, the buttuns and the text are to small. Does any one know about a skin witch is clearer?

---

### Post by Perfect Storm on 2006-11-19
> **fribacka said:**
> I like Xmms because it's simple and fast. But, the buttuns and the text are to small. Does any one know about a skin witch is clearer?

See if there's something that fits your needs: [http://gnome-look.org/index.php?xcontentmode=130&PHPSESSID=a5a34e1707147c2937f93dfa52c50648](http://gnome-look.org/index.php?xcontentmode=130&PHPSESSID=a5a34e1707147c2937f93dfa52c50648)

---

