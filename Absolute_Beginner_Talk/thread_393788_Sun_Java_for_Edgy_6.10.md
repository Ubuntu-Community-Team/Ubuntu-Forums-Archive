---
title: "Sun Java for Edgy 6.10"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by hosammy on 2007-03-26
I am really a Newbieof Ubuntu of Edgy from Fedora Core 6. In the Firefox Web browser, I need to run the firefox-java plugin, however, after trying my best, I still cannot install my favorite java plugin and cannot run the web page which requires the Sun Java plugin:

In the Firefox version 2.0.0.2, I type "about: plugins" in the URL line, it states, among other things,
[COLOR="Red"]
[FONT="System"]GCJ Web Browser Plugin 0.92

    File Name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

Java(TM) Plug-in Blackdown-1.4.2-02

    File Name:  libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2[/FONT][/COLOR]

Is the file "jre-6-linux-i586.bin" found in [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) is a suitable one for the firefox browser plugin to work?:confused:

---

### Post by mahy on 2007-03-26
try installing the sun-java5-plugin and its dependencies.

---

### Post by josephus on 2007-03-26
i think sun-java6-plugin is in the backport repository

---

### Post by Obor on 2007-03-26
I've used [this > How to install J2SE Runtime Environment (JRE) v6.0 with Plug-in for Mozilla Firefox]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox")

---

### Post by hosammy on 2007-03-27
[COLOR="Red"]I've used this > How to install J2SE Runtime Environment (JRE) v6.0 with Plug-in for Mozilla Firefox[/COLOR]

I follow the instruction hereinabove, and fail at [COLOR="Green"]fakeroot make-jpkg jre-6-linux-i586.bin[/COLOR]

[COLOR="Blue"]sammy@Livingroom:~/Desktop$ ls
GDM-GdmMadTux2.tar.gz  gdm_mad-tux-2      jre-6-linux-i586.bin
GDM-GdmMadTux.tar.gz   ICON-Noia.tar.bz2  nautilus.desktop
sammy@Livingroom:~/Desktop$ fakeroot make-jpkg jre-6-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.wIzSG20485
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

sh: gcc: not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done
sammy@Livingroom:~/Desktop$ [/COLOR]

Please advise... :confused:

---

### Post by josephus on 2007-03-30
you need to install a compiler before you can build stuff.

```
sudo aptitude install build-essential
```

I don't think that you need to follow those steps to get your plugins working properly.

If you just followed the steps in the first section (i.e. sudo aptitude install sun-java6-jre sun-java6-plugin), then you should be good to go.

It might also be necessary to run
```
sudo update-java-alternatives -s java-6-sun
```

which tells the computer to use sun-java6 instead of the alternatives.

---

