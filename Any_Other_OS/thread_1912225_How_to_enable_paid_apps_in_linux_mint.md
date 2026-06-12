---
title: "How to enable paid apps in linux mint"
date: 2012-01-20
forum: Any Other OS
---

### Post by Aleksandar222 on 2012-01-20
The title says it all :D

---

### Post by nothingspecial on 2012-01-20
Thread moved to Other OS/Distro Talk.

---

### Post by xyzzyman on 2012-01-20
What exactly are you requesting? Did you purchase an application somewhere's and you don't know how to install it? If so we need more information of what you meant.

---

### Post by cpatrick08 on 2012-01-20
> **xyzzyman said:**
> What exactly are you requesting? Did you purchase an application somewhere's and you don't know how to install it? If so we need more information of what you meant.

i think the original  poster bought the apps in Ubuntu software center and wants to use them in mint

---

### Post by xyzzyman on 2012-01-20
Source: [http://www.upubuntu.com/2011/12/how-to-install-ubuntu-software-center.ht](http://www.upubuntu.com/2011/12/how-to-install-ubuntu-software-center.ht)


 If you want to port Ubuntu Software Center to a system running Linux Mint 12, then it would be possible if you follow these instructions:

1. Under Linux Mint 12, launch the terminal and install Ubuntu Software Center with this command:
```
sudo apt-get install software-center
```
2. Run now this command to create the LinuxMint.py file:
```
sudo cp -r /usr/share/software-center/softwarecenter/distro/Ubuntu.py /usr/share/software-center/softwarecenter/distro/LinuxMint.py
```
3. Edit now this file with this command:
```
gksudo gedit /usr/share/software-center/softwarecenter/distro/LinuxMint.py
```
4. Find now this line:

```
>> class Ubuntu(Debian)
```

And replace it with this line:
```
>> class LinuxMint(Debian)
```



5. Save your file and exit. You can now use Ubuntu Software Center on Linux Mint 12.

---

### Post by Aleksandar222 on 2012-01-21
@xyzzman
It did not help,paid apps still not avaialable.
I "bought" Marble Arena 2 ( costs 0 $ ) and would like to play it again,but I cannnot
due to paid apps category being empty.

---

### Post by xyzzyman on 2012-01-21
> **Aleksandar222 said:**
> @xyzzman
It did not help,paid apps still not avaialable.
I "bought" Marble Arena 2 ( costs 0 $ ) and would like to play it again,but I cannnot
due to paid apps category being empty.

Marble Arena 2 is free. What happens when you just search for it and click 'buy'? Most likely the apps that cost money won't work in Mint as the software store probably does more checks in preventing piracy, etc... You'll probably have to just run Ubuntu or install it manually from Marble Arena 2's website.

---

