---
title: "Java for my iBook G3 (Xubuntu 7.10 Gutsy Gibbon)"
date: 2008-01-09
forum: Apple PPC Users
---

### Post by fouba on 2008-01-09
The thing is how can I get Java for my iBook G3 with Xubuntu 7.10 Gutsy Gibbon on it.

And I just like to say that I have searched the forums but I didn't find the way to get Java. And the reason why I want java is a game in address [http://www.kiekko.tk](http://www.kiekko.tk) and it needs Java.

---

### Post by frog_pilot on 2008-01-09
look for the ppc faq of this site.
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

you have to install the package ```
ibm-j2re1.5
``` from the medibuntu repository.

After installing it, I mentioned the following:

There was no java support at all after installing ibm-j2re1.5. I found, that the symbolic link to the java-plugin-library in /usr/lib/mozilla-firefox/plugins points to /usr/lib/j2re1.5-ibm/jre/bin/ns7/libjavaplugin.so. But there is no such folder /ns7/ and there is also no such library libjavaplugin. In the java-doc is written, that the right plugin-lib for firefox is libjavaplugin_oji.so. You can find it in /usr/lib/j2re1.5-ibm/jre/bin/. I think, this is a major bug, because this was a default installation of ibm-j2re1.5. To fix this problem, you have to run in a terminal:
```
sudo rm /usr/lib/mozilla-firefox/plugins/libjavaplugin.so
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/lib/j2re1.5-ibm/jre/bin/libjavaplugin_oji.so
```

thats afaik the only java for ppc-linux.

---

### Post by fouba on 2008-01-09
> **frog_pilot said:**
> look for the ppc faq of this site.
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

you have to install the package ```
ibm-j2re1.5
``` from the medibuntu repository.
Done.

> **frog_pilot said:**
> ```
sudo rm /usr/lib/mozilla-firefox/plugins/libjavaplugin.so
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/lib/j2re1.5-ibm/jre/bin/libjavaplugin_oji.so
```
Done.

Java still not working, when I go to site where I need java it says, check for plug-ins or something like that but cant find any..

---

### Post by frog_pilot on 2008-01-10
enter in your firefox url-field ```
about:plugins
```. all available plugins will be listed in this window. maybe your site won't function because it requires a newer java version. bet there isn't one for ppc-linux.

And did you proove that ist necessary to create the new symbolic link before executing the code I provided you? maybe this bug was fixed...

Verify if the libjavaplugin_oji.so is in the folder /usr/lib/j2re1.5-ibm/jre/bin/. If it is there you did the right thing executing the provided code. If not, you can execute the commands once more with the matching files and folders for your system.

---

### Post by fouba on 2008-01-10
> **frog_pilot said:**
> enter in your firefox url-field ```
about:plugins
```. all available plugins will be listed in this window. maybe your site won't function because it requires a newer java version. bet there isn't one for ppc-linux.

And did you proove that ist necessary to create the new symbolic link before executing the code I provided you? maybe this bug was fixed...

Verify if the libjavaplugin_oji.so is in the folder /usr/lib/j2re1.5-ibm/jre/bin/. If it is there you did the right thing executing the provided code. If not, you can execute the commands once more with the matching files and folders for your system.When I put about-plugins does it tell me all the available plugins that I can get to my Computer or does it tell what I have at the moment?

At the moment there is only Shockwawe Flash at the site about-plugins for me.

And how do I verify about the libjavaplugin thing? What do I put to Terminal or what will I do?

---

### Post by oswaldkelso on 2008-01-10
> **frog_pilot said:**
> look for the ppc faq of this site.
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

thats afaik the only java for ppc-linux.

there is ibm java.according to this post on the debian forums

ref: peter.makholm.net
Java on Linux-PPC

April 16, 2007 at 8:44 pm · Filed under Debian

One step nearer removing OS X form my iBook. Now I got java running so I can log on to my net banking account. The following works on my Debian Etch (-ish):

   1. Download IBM’s java-package from [http://www-128.ibm.com/developerworks/java/jdk/linux/download.html](http://www-128.ibm.com/developerworks/java/jdk/linux/download.html) (registration required) - you need the 32bit iSeries/pSeries version in tgz format
   2. Make sure that the package includes …/jre/bin/libjavaplugin_oji.so (somehow I got a package which didn’t have the file)
   3. install java-package
   4. run make-jpkg <tgz file>. If it complain about “no matching plugin was found” look in /usr/share/doc/java-package/SUPPORTED and rename you tgz file to something supporte of almost the correct version.
   5. Install the resulting package and restart firefox (whatever it is named today)

I downloaded a file called ibm-java2-jre-5.0-4.0-linux-ppc.tgz and renamed it to ibm-java2-jre-50-linux-ppc.tgz and it seems to work.

Permalink
2 Comments 
*EDIT*

After installing the libstdc++5 and gcc-3.3-base packages everything is peachy. Very Happy

---

### Post by fouba on 2008-01-10
> **oswaldkelso said:**
> 4. run make-jpkg <tgz file>. If it complain about “no matching plugin was found” look in /usr/share/doc/java-package/SUPPORTED and rename you tgz file to something supporte of almost the correct version.This is the stage I got stuck.. How can I get this make-jpkg working?

---

### Post by frog_pilot on 2008-01-10
> **oswaldkelso said:**
> 
I downloaded a file called ibm-java2-jre-5.0-4.0-linux-ppc.tgz and renamed it to ibm-java2-jre-50-linux-ppc.tgz and it seems to work.

This is exactly the java-version suggested by me. You can find it - as stated above - in the medibuntu-repo as a dab-package. And you can simply install it using synaptic or apt-get. there is no need to compile it from source.

---

### Post by frog_pilot on 2008-01-10
> **fouba said:**
> When I put about-plugins does it tell me all the available plugins that I can get to my Computer or does it tell what I have at the moment?
It shows you only the plugins which are installed on your system.

> **fouba said:**
> At the moment there is only Shockwawe Flash at the site about-plugins for me.
That means your java plugin (if you installed the ibm-j2re1.5 deb) isnt linked to firefoxes plugins directory

> **fouba said:**
> And how do I verify about the libjavaplugin thing? What do I put to Terminal or what will I do?
 you can use nautilus to browse to the folder ```
/usr/lib/mozilla-firefox/plugins
``` (the firefox plugins folder) look for a symlink to the java plugin similar to this ```
libjavaplugin.so
``` find out to which folder it points. Verify if this folder really exists. The real plugin file should be in a similar location to this ```
/usr/lib/j2re1.5-ibm/jre/bin/

``` If you have found the file```
libjavaplugin_oji.so
``` create a new symlink to it inside the firefox plugins folder (this is the meaning of the commands I suggested some posts earlier):```
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /<wherever>/<your>/<javaplugin>/<is>/<located>/libjavaplugin_oji.so
```

---

### Post by fouba on 2008-01-10
> **frog_pilot said:**
> 
 you can use nautilus to browse to the folder ```
/usr/lib/mozilla-firefox/plugins
``` 
What is nautilus and how do I use it ? 
> **frog_pilot said:**
> (the firefox plugins folder) look for a symlink to the java plugin similar to this ```
libjavaplugin.so
```  
What is symlink and how do I use it?
> **frog_pilot said:**
> find out to which folder it points. Verify if this folder really exists. The real plugin file should be in a similar location to this ```
/usr/lib/j2re1.5-ibm/jre/bin/

```  
How can I find out where it points?
> **frog_pilot said:**
> If you have found the file```
libjavaplugin_oji.so
``` create a new symlink to it inside the firefox plugins folder (this is the meaning of the commands I suggested some posts earlier):```
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /<wherever>/<your>/<javaplugin>/<is>/<located>/libjavaplugin_oji.so
```

I hope you dont get that feeling that I'm just trying to be unpolite, because I'm just noob and trying to solve this problem. And there were some terms that I didn't understand :confused:

---

### Post by Auria on 2008-01-10
> 
What is nautilus and how do I use it ? 


He meant you can just navigate it by double-clicking folder icons, no need to use the terminal

---

### Post by fouba on 2008-01-10
> **frog_pilot said:**
> ```

sudo ln -s /<wherever>/<your>/<javaplugin>/<is>/<located>/libjavaplugin_oji.so
```
How can I found out where my javaplugin is located?

---

### Post by frog_pilot on 2008-01-11
Ok, if this is the point, some words for introduction:

Everything I say is for the gnome-desktop-environment (if you installed ubuntu (and not kubuntu or xubuntu) you have the gnome-desktop)

Nautilus is the program similar to finder in OSX or explorer in windows. If you go to the places-menu and you click on an item there, a nautilus window will open up.
//edit: OK, its evident but I missed it... you running xubuntu--- thunar is the xubuntu equivalent for nautilus. symlinks also exist in xubuntu... and with firefox and its plugins its also the same deal..

If you executed the commands I suggested in my first reply, lets first have a look, if the created symbolic link is valid. (A symlink or symbolic link is like an alias in OSX - it is not a file itself but rather a link to a real file)

If you did, you created in the folder ```
/usr/lib/mozilla-firefox/plugins
``` a link to the file ```
libjavaplugin_oji.so
``` in the folder ```
/usr/lib/j2re1.5-ibm/jre/bin/
``` This is the meaning of the two commands> cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/lib/j2re1.5-ibm/jre/bin/libjavaplugin_oji.so

That's why you have to browse by nautilus to the folder ```
/usr/lib/j2re1.5-ibm/jre/bin/
``` and look for the file ```
libjavaplugin_oji.so
```

First try to follow these instructions and post the result. After it I can suggest you the following steps...

---

