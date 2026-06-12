---
title: "How to intall Sun Java"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by shawnjes on 2008-01-30
Hello,

anyone have any step by step beginner insructions for installing Java for a PC runing Ubunto 7.10?  I figured out how to use the console to unstuff it into a folder.  However, the browser still needs a plugin (don't have permissions to simply copy it into mozilla's plugins folder) and I still can't run any Java apps?

I've found directions on how to install using the built-in installer application, it doesn't work, tells me that my packages have dependencies and can't be installed?  Most of the directions I've found online ask me to log into Root, which it also doesn't seem to allow.

Please help very frustrated.

---

### Post by FuturePilot on 2008-01-30
The best way is to install Java from the repositories. That way you won't have to worry about keeping it up to date and such. But you said it gave you errors. Can you post them?

---

### Post by emarkd on 2008-01-30
I agree with FuturePilot.  In Synaptic, Click on Settings > Repositories and enable everything but Source Files..  Save and click reload on the main page, then search for sun-java6 and you'll find everything you need.

Root is disabled by default in Ubuntu for security purposes.  You can perform root commands by prefacing them with 'sudo' when you run them, but MAKE SURE you know what you're doing.  Linux won't hold your hand and will do whatever you ask of it, whether it's a good thing or not.

---

### Post by jan quark on 2008-01-30
```
sudo apt-get install sun-java6-bin sun-java6-jre
``` into the terminal

should work
or read here
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by shawnjes on 2008-01-30
Thanks ,however the console command line that you provided gives me the following:

The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not installable
                 Depends: libstdc++5 but it is not installable
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
E: Broken packages
linux@linux-desktop:~$ 


I'll the try the package installer and let you know how it goes.

Much appreciated!

---

### Post by shawnjes on 2008-01-30
Thanks,

package installer worked this time! Not sure why it worked this time?

Java apps and online java content is working great.

Thanks to all.

---

### Post by stchman on 2008-01-30
> **shawnjes said:**
> Hello,

anyone have any step by step beginner insructions for installing Java for a PC runing Ubunto 7.10?  I figured out how to use the console to unstuff it into a folder.  However, the browser still needs a plugin (don't have permissions to simply copy it into mozilla's plugins folder) and I still can't run any Java apps?

I've found directions on how to install using the built-in installer application, it doesn't work, tells me that my packages have dependencies and can't be installed?  Most of the directions I've found online ask me to log into Root, which it also doesn't seem to allow.

Please help very frustrated.

I have had excellent success with Sun Java 5 so here goes:

```
sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

If you prefer to use Sun Java 6 then substitute 6 for 5.

---

### Post by ubuntu-freak on 2008-01-30
Best way is to install the restricted-extras package.
 
Install the "Essential Packages" in my easy [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Make sure you do this after
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
Nathan

---

