---
title: "java, java, java..............."
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-14
java not working for me...once again
i had installed firefox 1.5.0.3 through automatix, but since java didn't work in there, i tried to install it manually from the website. it was a success, but java still doesn't work...:(
i tried 
```
echo 3 | sudo update-alternatives --config java 
``` but none of the four options work, i think. i'll list them anyway:
```
echo 3 | sudo update-alternatives --config java 
Password:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java
 +    4        /usr/lib/j2se/1.4/bin/java

Press enter to keep the default
[*], or type selection number: Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.

``` is there something wrong here or which one should i be using?
also what does the plus sign mean, as in the number 4 alternative?

---

### Post by mlind on 2006-05-14
That another java is probably installed by Automatix. I don't know which one 
you installed, but use java 1.5 (known as 5.0) as the default one.

the plus sign marks the current 'best' version, which comes from highest **priority**.
if you look output of *update-alternatives --help*, you'll see that when adding new
entries with --install parameter, you also have to supply priority as an integer.

Just remove existing java 1.4. If it was the one you manually installed, remove both java installations
and reinstall only 1.5.

```

sudo apt-get install build-essential java-package
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
sudo dpkg -i j2re-1.5.deb
sudo update-alternatives --configure java

```

---

### Post by user1397 on 2006-05-16
i fixed it!
i just uninstalled blackdown java and sun java, and reinstalled sun java using the ubuntu wiki

---

