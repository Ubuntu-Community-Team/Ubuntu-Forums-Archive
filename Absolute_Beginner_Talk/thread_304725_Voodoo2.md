---
title: "Voodoo2"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2006-11-22
Ok got this little Dell running great with Ubuntu so I decided to load up the old V2 and no boot. Stalls about 65% any ideas anyone? The V2 is a diamond if that helps. I take it back out and the sys boots fine.:-k

---

### Post by J11Gyro on 2006-11-23
Happy Thanksgiving to all who celebrate it. If you are bored and have any ideas on how to get a voodoo2 working with Ubuntu, please reply heh this is not working for me at all. It should load right up I thought. Any help would be appreciated.

---

### Post by Bachstelze on 2006-11-23
I don't have a voodoo myself but certainly [this](http://dri.freedesktop.org/wiki/3dfx) will help.

---

### Post by J11Gyro on 2006-11-23
Found some drivers at the following link but am not sure how to get them to install LOL old dog new tricks again.

[http://www.3dfxzone.it/index.php:-k](http://www.3dfxzone.it/index.php:-k)

---

### Post by taurus on 2006-11-23
Are you talking about this one?

[http://www.3dfxzone.it/Voodoo3/linux/v3linux.zip](http://www.3dfxzone.it/Voodoo3/linux/v3linux.zip)

Well, you can unpack it with 

```
unzip -x v3linux.zip
```
Looks like they are in .rpm and for XFree86 (back in 2002).  Ubuntu and most other Linux distros are using Xorg so I don't know if it would work or not...  Otherwise, try

```
sudo aptitude update
sudo aptitude install alien
alien <filename>.rpm
sudo dpkg -i <filename>.deb
```

---

### Post by Bachstelze on 2006-11-23
It will. Xorg is just another implementation of XFree86 and is totally backward-compatible as far as my personal experience go.

---

### Post by J11Gyro on 2006-11-24
Been trying to load but with the voodoo2 it hangs about 78-80% on boot and just sits there. But I will not give up on it that is for sure. This box has only 4 mg video onboard and no agp slots and I have 5 Voodoo2 boards not in use lol. If I can get one to work I will try to SLI the second and see what happens. If it works anything like old 3.11 it will give a slight boost all the way around video wise. Even if it doesn't work I will keep it running Ubuntu and just use it as a Net box, since winblows is so secure:) Heh I wish I had gotten a 3 way VKM switch now.

---

### Post by J11Gyro on 2006-11-25
This is great got the Voodoo2 working, not sure how but at least system boots and it is showing up in hardware. Now how to test it?Thanks for the help, it is greatly appreciated.:-D

---

