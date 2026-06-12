---
title: "[SOLVED] How to install skype ?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by arai on 2007-09-04
How to install skype (in ubuntu edgy 6.10) ? i downloaded the skype version from [www.skype.com](www.skype.com) (that is made for ubuntu feasy fawn 7.04). should i install it or not ?

---

### Post by MWilliams13 on 2007-09-04
Your question"Should I install it or not?" Is really up to you. If yuo want to do it. If not. don't

---

### Post by -SpaZ on 2007-09-04
> **arai said:**
> How to install skype (in ubuntu edgy 6.10) ? i downloaded the skype version from [www.skype.com](www.skype.com) (that is made for ubuntu feasy fawn 7.04). should i install it or not ?

Consult [here]("https://help.ubuntu.com/community/Skype") for information

---

### Post by arai on 2007-09-04
I meant could I install the package that is made for feisty fawn?

---

### Post by -SpaZ on 2007-09-04
> **arai said:**
> I meant could I install the package that is made for feisty fawn?

I'm not sure.  That's why I told you to consult there.

---

### Post by splintercellguy on 2007-09-04
Sure, sudo dpkg -i <name of package>? Or you could do the whole repo thing as mentioned in the Skype guide.

---

### Post by arai on 2007-09-04
I right clicked and selected this "Open with GDebi Package Installer" and i got this error ([screenshot]("http://img159.imageshack.us/img159/5671/screenshotsn3.png"))

---

### Post by aktiwers on 2007-09-04
Try download and doubleclick this deb
[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/skype_1.3.0.53-1medibuntu1+b1_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/skype_1.3.0.53-1medibuntu1+b1_i386.deb)

---

### Post by arai on 2007-09-04
Under the Internet menu I now have Skype. But it is not opening. Now I need to remove this first and then try reinstalling as said by aktiwers. Anybody know how to remove this non working skype version ?

---

### Post by aktiwers on 2007-09-04
Wont a :
```
sudo apt-get remove skype
``` do the trick?

Or open synaptic and search for Skype.

---

### Post by arai on 2007-09-04
i uninstalled skype. then installed it from your link. again it is showing the same error. (new [screenshot]("http://img49.imageshack.us/img49/2275/screenshot1ab8.png")).

---

### Post by aktiwers on 2007-09-04
Then do a:
```
sudo apt-get install libasound2
```

Or open Synaptics and search for "libasound2" (without the quotes) and install it.

---

### Post by arai on 2007-09-04
this is what i get 

> sudo apt-get install libasound2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 176 not upgraded.


also since i get [librte1 Dependency not satisfiable]("http://img49.imageshack.us/img49/2275/screenshot1ab8.png") i did this

> sudo apt-get install librte1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package librte1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package librte1 has no installation candidate

---

### Post by aktiwers on 2007-09-04
Oops.. sorry, I looked at the old screenshot.. this is what you should type:
```
sudo apt-get install librte1
```Or open Synaptics and search for "librte1" (without the quotes) and install it.

Edit:
Though I believe Ubuntu should install these automatically when you try to install skype... Oh well lets do it manually then (as mentioned above).
If this becomes too much trouble, download and install Automatix instead.. it will let you install lots of apps automatically.
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by arai on 2007-09-04
How to proceed with skype installation now. I did that what you said. Please see the my previous post updated above. thanks.

still it is showing librte1 not satisfiable.

---

### Post by aktiwers on 2007-09-04
Hmm okay.. thats strange.. because those libs are working here!
Can this be because you dont have univers repo's open?
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Else try the automatix way then, I guess thats the easiest way.. coz I have to go to bed soon :(

---

### Post by arai on 2007-09-05
aktiwers, i will try as it is said in the link. thanks for your time. i am installing the repos now.

[COLOR="Red"]Update [/COLOR]: Skype is working. [this document]("https://help.ubuntu.com/community/Skype") was helpful.

---

