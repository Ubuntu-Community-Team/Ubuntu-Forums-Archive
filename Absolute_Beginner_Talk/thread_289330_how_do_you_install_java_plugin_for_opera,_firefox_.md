---
title: "how do you install java plugin for opera, firefox and konquerer?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-10-30
I need it for a java ap on a website i tried to let firefox install it for me but it says only manual so I downloaded the bin file from sun how do install it? I tried thru adept and it said it can't install b/c it would cause a break or something.

can someone help me please?

---

### Post by dmizer on 2006-10-30
there's a link to directions on how to install it at the sun site (same location as where you downloaded the code from).  the directions are well written, if you follow them carefully, you should have a working java plug in.

---

### Post by Sef on 2006-10-30
Applications > Add/Remove

then in search type in Sun Java 5.0, check both boxes and then apply.

Note: You have to have the multiverse [enabled]("https://help.ubuntu.com/community/Repositories/Ubuntu") to do download Sun Java.

---

### Post by maddbaron on 2006-10-30
wont allow me to apply

multiverse enabled

---

### Post by dmizer on 2006-10-30
try following these directions for installing the java plugin according to sun's site:
[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

i've not had a problem with using the code downloaded from the sun site rather than using the java plugin obtained from the repos.

---

### Post by maddbaron on 2006-10-31
I attempted to and somehow extracted to my desktop couldnt locate the lib the sun site said "/usr/lib" so now the folder is on my desktop but no way to get it into firefox or any other browser :(

---

### Post by cotcot on 2006-10-31
Do you have 64 bit ? Opera is a 32 bit app and will not work with java 64 bit. In that case you have to install a 32 bit java along the 64 bit.

---

### Post by r4ik on 2006-10-31
Try,

[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

Good luck !

---

### Post by jrings on 2006-10-31
You can let Automatix do the job for you, should work:

[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

---

### Post by maddbaron on 2006-10-31
i dont know what to do, the system says its installed and is most recent. but whenever I go to a site requiring java it says i'm missing the plugin. i truly don't understand this.

---

### Post by DeemanXu on 2006-11-03
> **maddbaron said:**
> i dont know what to do, the system says its installed and is most recent. but whenever I go to a site requiring java it says i'm missing the plugin. i truly don't understand this.

I am having the exact same problem here as well, with both flash and Java. I even went as far as to copy the plugins from /usr/lib/firefox/plugins to ~/mozilla/plugins - still no such luck. Tried with both Automatix, and with SPM, tried symlinks too, but all to no avail, and it is starting to get on my nerves.](*,)

---

### Post by InfernalPenguin on 2006-11-03
type this in your konsole (assuming your repositories are added and updated)

sudo apt-get install sun-java5-jre sun-java5-plugin  

for installing flash type this

sudo apt-get install flashplugin-nonfree
sudo update-flashplugin

or maybe you have to just enable java in your firefox preferences

---

### Post by matchstich on 2006-12-12
ok, i installed java runtime thru add/remove it works in firefox, but doesn't work in opera. why is that?
thanks

---

### Post by RomeReactor on 2006-12-28
matchstich, try opening Opera thru a terminal (in edgy, Applications-->Accesories-->Terminal) **OR** (press ALT+F2, then write:

```
gnome-terminal
```

and press enter). Once the terminal pops up, write in it:

```
opera
```

and press enter. Go to a site that requires the java applet, and see what the terminal tells you; If it complains of not finding libjava.so, then search for it. Close Opera, and in the terminal, write:

```
locate libjava.so
```

and copy the path it returns, except the end, which must be "/libjava.so". Or search from the desktop (Places--> Search for Files...). Change the "Look in folder:" tab to "File System" and search for the renegade:

```
libjava.so
```

and copy the path it returns. In my case, it was in 

```
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386
```

So now, open Opera again, open "Tools-->Preferences-->Advanced-->Content", make sure the "Enable Java" box is checked, then click on "Java options" to specify the path *your* search gave you. Click "Validate Java path", then click "OK". Hope this works for you! :mrgreen:

---

