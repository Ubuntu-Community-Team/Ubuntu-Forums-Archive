---
title: "[SOLVED] please help me resolve this error in synaptic"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by arjayes on 2007-10-06
i tried to install second life binary  from getdeb.net it must have been broken . Anyway now I can't open synaptic or run apt  commands I get this error dialog box when i try to open synaptic 


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package secondlife-install needs to be reinstalled, but I can't find an archive for it.'

and this comes when i try to run apt-get install <> 
The package secondlife-install needs to be reinstalled, but I can't find an archive for it[-o<[-o<:-|


please help
[-o<[-o<:-|

---

### Post by shae on 2007-10-06
Try reinstalling the package from getdeb.

---

### Post by ryanVickers on 2007-10-06
Can you at least remove the package somehow?  try looking in /tmp or that folder that has a lot of deb packages stored as cache or something... does anyone remember? :p

---

### Post by arjayes on 2007-10-06
tried  reinstalliing .doesn't help.

---

### Post by arjayes on 2007-10-06
I deleted the package from /tmp still no change . 
:confused:

---

### Post by ryanVickers on 2007-10-06
I would really try to find that folder with all the packages as cache!!! I'll look again... :p

---

### Post by ryanVickers on 2007-10-06
ahh, here we are! /var/cache/apt/archives :) see if it's there, and if deleting it helps...

---

### Post by arjayes on 2007-10-06
its not there either 
theres just a file called "lock"
and a folder:" partial " which is empty



:confused:

---

### Post by forestpixie on 2007-10-06
try this 

```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```

---

### Post by SpiritIsReality on 2007-10-06
howdy
Ive seen this on the forums.
[http://www.google.ca/search?hl=en&q=%22The+package+*+needs+to+be+reinstalled%2C+but+I+can%27t+find+an+archive+for+it%22&btnG=Google+Search&meta=]("http://www.google.ca/search?hl=en&q=%22The+package+*+needs+to+be+reinstalled%2C+but+I+can%27t+find+an+archive+for+it%22&btnG=Google+Search&meta=")
[http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html)
[http://ubuntuforums.org/archive/index.php/t-504924.html](http://ubuntuforums.org/archive/index.php/t-504924.html)
so 
sudo dpkg --remove --force-remove-reinstreq  secondlife-install
should work, if not try the 
Type sudo apt-get -f install; sudo dpkg --configure -a but do it twice if it doesn't work the first time.
and another solution I've seen is to cd to /var/lib/dpkg/info and find the file name, in this case, secondlife-install , and mv to a different directory, or rm it.
buds

forestpixie ... haha! way to go.

---

### Post by arjayes on 2007-10-06
thanks all of you 
"sudo dpkg --remove --force-remove-reinstreq secondlife-install" worked

---

### Post by forestpixie on 2007-10-06
glad to hear it :)

can you mark thread as solved - thread tools

---

### Post by DJ_Peng on 2007-10-07
Personally I just use SL from their website. Otherwise when they bring out a mandatory upgrade you're completely off SL until it gets into the repos, which can be a few days at least. The way I do it it's always in my home folder and I can get the new versions up and running in a couple minutes longer than it takes me to download it.

I rename the folder simply SecondLife so I can have a launcher on my desktop that always points to that folder. I can also have older versions if I want in case the optional updates screw things up too much.

---

