---
title: "Right Clicking"
date: 2009-06-22
forum: Apple Hardware Users
---

### Post by balt11t on 2009-06-22
Well, I just set up and installed Ubuntu on a salvaged iBook G4 and it's running great. I was just wondering if there was some way to have like a Super + Click thing similar to Mac OS X. I have a Windows mouse, but it is wired and not very mobile, so if there is nothing I can do it's not that big of a deal.

---

### Post by tiagobt on 2009-06-23
I'm not sure these instructions still work, but you might give them a try:

[https://help.ubuntu.com/community/MacBook2-1/Hardy#Right/Middle%20Clicking](https://help.ubuntu.com/community/MacBook2-1/Hardy#Right/Middle%20Clicking)
[https://help.ubuntu.com/community/MacBook3-1/Jaunty#Middle&Right%20Click%20with%20Left&Right%20Cmd%20Keys](https://help.ubuntu.com/community/MacBook3-1/Jaunty#Middle&Right%20Click%20with%20Left&Right%20Cmd%20Keys)

---

### Post by balt11t on 2009-06-23
Everything works fine until I get to 
> 
Save and close gedit.
 Make the script executable and install xkbset: 
chmod u+x $HOME/.startup
sudo apt-get install xkbset

When it says the package xkbset doesn't exist.

---

### Post by tiagobt on 2009-06-23
The package xkbset is available in the Universe repository, which is not enabled by default. To enable it, do the following:

1. Open the file /etc/apt/sources.conf in gedit:
```
sudo gedit /etc/apt/sources.conf
```

2. Uncomment the four lines related to the Universe repository, removing the character # from the beginning of each line. The lines should look like this:
```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
```

3. Save the file and close gedit.

4. Update your application sources:
```
sudo apt-get update
```

5. Try to install xkbset again:
```
sudo apt-get install xkbset
```

---

### Post by 3rdalbum on 2009-06-24
If I remember correctly, you can right-click by pressing F12, and middle-click by pressing F11.

---

