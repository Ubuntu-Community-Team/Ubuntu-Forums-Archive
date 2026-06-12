---
title: "problems installing flash"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by maggiejs on 2007-01-14
I am having problems installing flash on my ubuntu box.

it says the administrator needs to remove the xpti.dat file from the components directory of the mozilla browser.

I have no idea what this means, and have searched the other posts in the forums, and have not found them helpful.

Can anyone explain how to remove this file? 

thanks!

---

### Post by taurus on 2007-01-14
Applications -> Accessories -> Terminal
```
sudo rm **filename**
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by maggiejs on 2007-01-14
thanks ,i tried that and it told me 
No Such File Or Directory


any other ideas?

thanks

---

### Post by marx2k on 2007-01-14
This worked for me:
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by taurus on 2007-01-14
What is that file, xpti.dat, that you want to remove?  You need to change to that directory first  before you run the "sudo rm filename" to remove it.  And if you want to install flash, then install automatix2 first and use it to install flash and other goodies for your machine.

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by maggiejs on 2007-01-14
I don't know what the file is that it says i need to remove...
it just says the adminisrator needs to remove it, i'm assuming that flash won't work unless it is removed?

---

### Post by recrispi on 2007-02-06
Hello!
I think the file it's talking above is located in .mozilla/firefox/<strangecode>/xpti.dat
When I installed flash 9  got the same error, but then I installed it as root and it worked ok (no need to remove the xpti.dat file, because it's created again). So you should use:
> sudo ./install_flash_player_9_linux
and follow instructions.
Hope this helps.

---

