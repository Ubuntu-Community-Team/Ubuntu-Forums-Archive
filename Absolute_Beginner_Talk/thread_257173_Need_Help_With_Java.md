---
title: "Need Help With Java"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by kcgreg on 2006-09-14
Hi All, 

Need help with installation of Java as this process is very complicated and for a neophyte in Linux this is all too much for my little head. HELP!:confused:

I am using Ubuntu v.6.06 I think.

---

### Post by Architeuthis on 2006-09-14
Installing Sun Java
Ubuntu 6.06

    *

      Sun Java5: Install it from the Applications -> Add/Remove... menu making sure to check the unsupported and proprietary software checkboxes, or install the sun-java5-bin package.
    *

      Blackdown Java2 1.4 packages: Install the j2re1.4 package, available in the multiverse repositories. Install it from the Applications -> Add/Remove... menu, or install the j2re1.4 package.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) 

this should be what you need, you can also check synaptic for everything sun related, there you can also find a plugin for firefox.

---

### Post by welshboy on 2006-09-14
Hey there,

I had the same hassle on my machine.  I'll assume that you're using the Gnome version?

If so, then do the following.

1. Go to System ---> Administration ----> Synaptic Package Manager
2. You may need to enter your password at this point
3. Look at the list on the left hand side, you should have Developement(Multiverse) there, if not you'll need to enable it by doing the following: 
  a. Click on Settings --- > Repositories
  b. Change the LTS (Backports i think) to Multiverse and universe
  c. Click on close and then click on Reload 
  d. the program will go haywire for a bit, but once it's done                  you should have the option down the left hand side.

4. If it's there, then scroll through and you should have sun-java5-jdk there.  If so, right click and select mark for installation

And that should be it

However you may need to uninstall gij, linux's version of java first.  I did and it sorted a great deal of problems for me.  That can be found in the Developement option.

I'm a newbie at this as well, so if someone else would like to confirm or correct what I've said then please do.  I use to use KDE which was a bit easier when changing multiverse and universe things.

Anyways, hope all this mush helps a little.

welshboy

---

### Post by Sef on 2006-09-14
Have you added universe and multiverse to your repositories?

If not, [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

To download anything, [click here.]("http://monkeyblog.org/ubuntu/installing/")

Note: You cannot install java unless you have added multiverse.

Also here is a ubuntu site about restricted formats and adding them.  [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by kcgreg on 2006-09-14
Hey Welshboy,

Thanks a lot for the help and it is much appreciated!!!:p 

Cheers,

kcgreg

---

### Post by kcgreg on 2006-09-14
> **Sef said:**
> Have you added universe and multiverse to your repositories?

If not, [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

To download anything, [click here.]("http://monkeyblog.org/ubuntu/installing/")

Note: You cannot install java unless you have added multiverse.

Also here is a ubuntu site about restricted formats and adding them.  [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

:) Hey Sef,

Thanks for that. Do I add for all the repositories????? I am in the process of getting the hang of it. Why do we add multiverse & universe to the repositories???

Cheers,

kcgreg

---

### Post by Dinerty on 2006-09-14
**Originally created by **Artificial Intelligance**, with slight modification from me to adapt the new version

If you want the latest version:

Download Java Runtime Environment (JRE) 5.0 Update 8: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick Linux self-extracting file. Download it to your Desktop.

```

cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_08-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update08_i386.deb
sudo update-alternatives --config java

```

When asking for which version you want to choose pick;

```
 3        /usr/lib/j2sdk1.5-sun/bin/java
```

Testing;

```
java -version
```

Making a Launcher for Java Control Center;

```
sudo gedit /usr/share/applications/java.desktop
```

fill in;


[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;


Save and exit.
You can find it now under Applications tab ---> System Tools.
__________________

---

