---
title: "Installing java JRE 1.3.1_09 on Ubuntu 6.10"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-04-01
Hi,
in Sun documentation I have read that JRE 1.3 is not supported for Ubuntu. I need exactlly this version of JRE because I use one Java applet application that requires exactlly this version of JRE. I have tried this applet by 1.4 and 1.5 JRE and it didn't work properly (windows mess up - looks like somekind of bug in 1.4 and 1.5).

Now I run JRE 1.3.1_09 on Windows XP Firefox 2.0 browser and works properlly. Any idea how to make it work on Ubuntu?
Thanks,
Abcuser

---

### Post by nixclusive on 2007-04-01
Hello there, you should be able to download the self extracting installer from Sun. The installation instruction are on the same page.

Most of the time, by unsupported, it is meant that official technical support is unavailable. However, one can go ahead and try on one's own risk.

Good luck.

---

### Post by LukeCarrier on 2007-04-01
Hi there,
I was struggling to install the Java Runtime Enviroment, and found that the easiest way to do it was to download Automatix, a Google search will throw up many a result.
When you have downloaded and installed it, open it, select the 'Plugins' section, then Java should appear in there.
Hope this helps,
Luke.

---

### Post by zvacet on 2007-04-01
Automatix will not install version you need.Nixclusive is right.Go to the Sun site ask for exact version and you will see download and instalation instructions.

P.S. you don´t need Automatix to download latest Java.It is in the repositories.Just information if you need it someday.

---

### Post by compiledkernel on 2007-04-01
Automatix is unsupported software by the community. These forums do not support it either.

If you are not aware of what automatix is -- "automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu."

---

### Post by kahrytan on 2007-04-01
> **abcuser said:**
> Hi,
in Sun documentation I have read that JRE 1.3 is not supported for Ubuntu. I need exactlly this version of JRE because I use one Java applet application that requires exactlly this version of JRE. I have tried this applet by 1.4 and 1.5 JRE and it didn't work properly (windows mess up - looks like somekind of bug in 1.4 and 1.5).

Now I run JRE 1.3.1_09 on Windows XP Firefox 2.0 browser and works properlly. Any idea how to make it work on Ubuntu?
Thanks,
Abcuser
Goto [Easy Ubuntu ]("http://easyubuntu.freecontrib.org/")([http://easyubuntu.freecontrib.org](http://easyubuntu.freecontrib.org)) page.  And follow the instructions.  Ironically, I just installed JRE with Easy Ubuntu today.  I can now see Java on websites.  There is an Easy Ubuntu 3rd party forum here as well.

*you don't need to do bleed edge.

---

### Post by zvacet on 2007-04-02
Did you installed vesion that LukeCarrier need kahrytan or you installed something else?I belive it is something else.

---

### Post by kahrytan on 2007-04-02
Okay. I found 1.3.1. There is a catch. It is an RPM. 


You can find [JRE 1.3.1 here]("http://rpmfind.net//linux/RPM/freshrpms/redhat/misc/add-ons/sun-jre/jre-1.3.1-fcs.i386.html")  (Rpmfind.net)

1. Download the file. 
2. Open Terminal and execute these commands. 

```
sudo apt-get update
sudo apt-get install alien
```

3.  Execute the command 

```
sudo alien -c /path/to/package.rpm
```

The deb file will be created. Then just open it like any other deb package

If you use  ```
sudo alien -ic /path/to/package.rpm
``` then It will convert, install, and delete deb file created. But you might want to just use the first code. You can then backup deb file for later use. Let me know how it works.

---

### Post by msak007 on 2007-04-02
1.3.1_09 can be downloaded from Sun's archives:

[http://java.sun.com/products/archive/j2se/1.3.1_09/index.html](http://java.sun.com/products/archive/j2se/1.3.1_09/index.html)

There's a link to the JRE and the installation instructions. You guys are missing the point - EasyUbuntu and Automatix will install JRE, but only the newest versions available and not the specific version the abcuser is looking for.

---

### Post by Warpnow on 2007-04-02
I used easy ubuntu and it seems to work fine.

---

### Post by zvacet on 2007-04-02
So,you don´t realy need that version,do you?

---

### Post by kahrytan on 2007-04-02
He is looking for JRE 1.3.1 for some applet that doesnt function right in 1.4 or 1.5.

---

### Post by LukeCarrier on 2007-04-02
> **compiledkernel said:**
> Automatix is unsupported software by the community. These forums do not support it either.

If you are not aware of what automatix is -- "automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu."

It has never failed for me, I use Ubuntu 6.10 and have previously used it under 6.06. And the forums can't support every piece of software can they?

---

### Post by abcuser on 2007-04-02
Hi,
1. I have downloaded JRE 1.3.1_09 from [Sun web page.](https://sdlc2b.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=6684AE3D5E2A9AA03166C41A26548E58;jsessionid=6684AE3D5E2A9AA03166C41A26548E58)
2. According to [Sun documentation](http://java.sun.com/products/archive/j2se/1.3.1_09/jre/install-linux.html) I have asign permisions:
```
sudo chmod a+x j2re-1_3_1_09-linux-i586-rpm.bin
```
3. I have unpack the bin file to get rpm file:
```
./j2re-1_3_1_09-linux-i586.rpm.bin
```
4. Then I executed the following commands:
```
sudo apt-get update
sudo apt-get install alien
```
5. Convert rpm package to deb:
```
sudo alien -c jre-1.3.1_09.i586.rpm 
```
6. Install deb package:
```
 sudo dpkg -i jre_1.3.1_09-1_i386.deb
```

The output of above command is
```

(Reading database ... 110022 files and directories currently installed.)
Preparing to replace jre 1.3.1_09-1 (using jre_1.3.1_09-1_i386.deb) ...
Unpacking replacement jre ...
Setting up jre (1.3.1_09-1) ...
chown: cannot access `/usr/java/jre1.3.1_09/CHANGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/COPYRIGHT': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/ControlPanel.html': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/LICENSE': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/README': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/Welcome.html': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/.java_wrapper': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/.java_wrapper': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/ControlPanel': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/ControlPanel': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/awt_robot': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/awt_robot': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/appletviewer': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/appletviewer': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/extcheck': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/extcheck': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/idlj': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/idlj': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jar': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jarsigner': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jarsigner': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/java': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/java': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javac': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javac': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javadoc': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javadoc': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javah': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javah': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javap': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javap': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jdb': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jdb': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/keytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/keytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/native2ascii': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/native2ascii': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjava': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjava': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjavac': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjavac': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjdb': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjdb': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/policytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/policytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmic': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmic': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmid': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmid': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmiregistry': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmiregistry': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/serialver': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/serialver': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/tnameserv': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/tnameserv': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/java': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/java': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/java_vm': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/java_vm': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/keytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/keytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/policytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/policytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/rmid': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/rmid': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/rmiregistry': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/rmiregistry': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/tnameserv': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/tnameserv': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/realpath': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/realpath': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/java': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/java': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/keytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/keytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/policytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/policytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/realpath': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/realpath': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/rmid': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/rmid': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/rmiregistry': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/rmiregistry': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/tnameserv': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/tnameserv': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/applet': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/applet': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/audio': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/audio': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/audio/soundbank.gm': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/cmm': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/CIEXYZ.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/GRAY.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/LINEAR_RGB.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/PYCC.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/sRGB.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/content-types.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/ext': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/ext': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/flavormap.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/font.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/font.properties.ja': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/font.properties.zh': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/fonts': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaBrightDemiBold.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaBrightDemiItalic.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaBrightItalic.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaBrightRegular.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaSansDemiBold.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaSansDemiOblique.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaSansOblique.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaSansRegular.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaTypewriterBold.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaTypewriterBoldOblique.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaTypewriterOblique.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaTypewriterRegular.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/fonts.dir': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i18n.jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic/Xusage.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic/libjvm.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic/libjvm.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/client': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/client': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/client/Xusage.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/client/libjvm.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/client/libjvm.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/green_threads': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/green_threads': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/green_threads/libhpi.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/green_threads/libhpi.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/hotspot': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/hotspot': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libJdbcOdbc.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libJdbcOdbc.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libagent.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libagent.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libawt.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libawt.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libcmm.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libcmm.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libdcpr.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libdcpr.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libfontmanager.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libfontmanager.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libhprof.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libhprof.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libioser12.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libioser12.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjava.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjava.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjavaplugin_jni.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjavaplugin_jni.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjawt.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjawt.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjcov.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjcov.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjpeg.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjpeg.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjsound.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjsound.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libmlib_image.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libmlib_image.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libnet.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libnet.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libpreemptive_close.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libpreemptive_close.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libverify.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libverify.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libzip.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libzip.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/native_threads': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/native_threads': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/native_threads/libhpi.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/native_threads/libhpi.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/server': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/server': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/server/Xusage.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/server/libjvm.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/server/libjvm.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/images': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/cursors.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/invalid32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_CopyDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_CopyNoDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_LinkDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_LinkNoDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_MoveDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_MoveNoDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/javaplugin.jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/jvm.cfg': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/jvm.hprof.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/jvm.jcov.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/de': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/de': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/de/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/de/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/de/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/es': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/es': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/es/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/es/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/es/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/it': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/it': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/it/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/it/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/it/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/psfont.properties.ja': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/psfontj2d.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/rt.jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/security': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/security': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/security/cacerts': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/security/java.policy': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/security/java.security': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/sunrsasign.jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/tzmappings': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man/ja': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/java.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/keytool.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/rmid.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/rmiregistry.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/tnameserv.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man/man1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/java.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/keytool.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/rmid.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/rmiregistry.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/tnameserv.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns4': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns4': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns4/javaplugin.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns4/javaplugin.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns600': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns600': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns600/libjavaplugin_oji.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns600/libjavaplugin_oji.so': No such file or directory
cp: cannot stat `/usr/java/jre1.3.1_09/man/man1/*': No such file or directory
dpkg: error processing jre (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 jre

```

Do I need to be an owner of /usr/java directory?
Thanks,
Abcuser

---

### Post by kahrytan on 2007-04-02
> **abcuser said:**
> Hi,
1. I have downloaded JRE 1.3.1_09 from [Sun web page.](https://sdlc2b.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=6684AE3D5E2A9AA03166C41A26548E58;jsessionid=6684AE3D5E2A9AA03166C41A26548E58)
2. According to [Sun documentation](http://java.sun.com/products/archive/j2se/1.3.1_09/jre/install-linux.html) I have asign permisions:
```
sudo chmod a+x j2re-1_3_1_09-linux-i586-rpm.bin
```
3. I have unpack the bin file to get rpm file:
```
./j2re-1_3_1_09-linux-i586.rpm.bin
```
4. Then I executed the following commands:
```
sudo apt-get update
sudo apt-get install alien
```
5. Convert rpm package to deb:
```
sudo alien -c jre-1.3.1_09.i586.rpm 
```
6. Install deb package:
```
 sudo dpkg -i jre_1.3.1_09-1_i386.deb
```

The output of above command is
```

(Reading database ... 110022 files and directories currently installed.)
Preparing to replace jre 1.3.1_09-1 (using jre_1.3.1_09-1_i386.deb) ...
Unpacking replacement jre ...
Setting up jre (1.3.1_09-1) ...
chown: cannot access `/usr/java/jre1.3.1_09/CHANGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/COPYRIGHT': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/ControlPanel.html': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/LICENSE': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/README': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/Welcome.html': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/.java_wrapper': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/.java_wrapper': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/ControlPanel': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/ControlPanel': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/awt_robot': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/awt_robot': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/appletviewer': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/appletviewer': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/extcheck': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/extcheck': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/idlj': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/idlj': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jar': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jarsigner': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jarsigner': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/java': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/java': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javac': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javac': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javadoc': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javadoc': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javah': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javah': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javap': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/javap': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jdb': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/jdb': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/keytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/keytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/native2ascii': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/native2ascii': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjava': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjava': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjavac': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjavac': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjdb': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/oldjdb': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/policytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/policytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmic': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmic': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmid': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmid': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmiregistry': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/rmiregistry': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/serialver': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/serialver': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/tnameserv': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/green_threads/tnameserv': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/java': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/java': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/java_vm': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/java_vm': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/keytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/keytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/policytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/policytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/rmid': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/rmid': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/rmiregistry': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/rmiregistry': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/tnameserv': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/native_threads/tnameserv': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/i386/realpath': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/i386/realpath': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/java': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/java': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/keytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/keytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/policytool': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/policytool': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/realpath': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/realpath': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/rmid': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/rmid': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/rmiregistry': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/rmiregistry': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/bin/tnameserv': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/bin/tnameserv': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/applet': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/applet': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/audio': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/audio': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/audio/soundbank.gm': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/cmm': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/CIEXYZ.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/GRAY.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/LINEAR_RGB.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/PYCC.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/cmm/sRGB.pf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/content-types.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/ext': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/ext': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/flavormap.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/font.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/font.properties.ja': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/font.properties.zh': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/fonts': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaBrightDemiBold.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaBrightDemiItalic.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaBrightItalic.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaBrightRegular.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaSansDemiBold.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaSansDemiOblique.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaSansOblique.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaSansRegular.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaTypewriterBold.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaTypewriterBoldOblique.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaTypewriterOblique.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/LucidaTypewriterRegular.ttf': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/fonts/fonts.dir': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i18n.jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic/Xusage.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic/libjvm.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/classic/libjvm.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/client': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/client': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/client/Xusage.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/client/libjvm.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/client/libjvm.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/green_threads': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/green_threads': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/green_threads/libhpi.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/green_threads/libhpi.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/hotspot': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/hotspot': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libJdbcOdbc.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libJdbcOdbc.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libagent.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libagent.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libawt.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libawt.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libcmm.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libcmm.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libdcpr.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libdcpr.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libfontmanager.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libfontmanager.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libhprof.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libhprof.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libioser12.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libioser12.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjava.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjava.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjavaplugin_jni.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjavaplugin_jni.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjawt.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjawt.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjcov.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjcov.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjpeg.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjpeg.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjsound.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libjsound.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libmlib_image.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libmlib_image.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libnet.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libnet.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libpreemptive_close.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libpreemptive_close.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libverify.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libverify.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/libzip.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/libzip.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/native_threads': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/native_threads': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/native_threads/libhpi.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/native_threads/libhpi.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/server': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/server': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/server/Xusage.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/i386/server/libjvm.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/i386/server/libjvm.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/images': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/cursors.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/invalid32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_CopyDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_CopyNoDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_LinkDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_LinkNoDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_MoveDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/images/cursors/motif_MoveNoDrop32x32.gif': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/javaplugin.jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/jvm.cfg': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/jvm.hprof.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/jvm.jcov.txt': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/de': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/de': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/de/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/de/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/de/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/es': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/es': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/es/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/es/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/es/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/fr/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/it': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/it': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/it/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/it/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/it/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ja/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko.UTF-8/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/ko/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/sv/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh.GBK/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW.BIG5/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW/LC_MESSAGES': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW/LC_MESSAGES': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/locale/zh_TW/LC_MESSAGES/sunw_java_plugin.mo': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/psfont.properties.ja': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/psfontj2d.properties': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/rt.jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/security': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/lib/security': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/security/cacerts': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/security/java.policy': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/security/java.security': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/sunrsasign.jar': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/lib/tzmappings': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man/ja': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/java.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/keytool.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/rmid.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/rmiregistry.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/ja_JP.eucJP/man1/tnameserv.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/man/man1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/java.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/keytool.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/rmid.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/rmiregistry.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/man/man1/tnameserv.1': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns4': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns4': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns4/javaplugin.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns4/javaplugin.so': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns600': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns600': No such file or directory
chown: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns600/libjavaplugin_oji.so': No such file or directory
chmod: cannot access `/usr/java/jre1.3.1_09/plugin/i386/ns600/libjavaplugin_oji.so': No such file or directory
cp: cannot stat `/usr/java/jre1.3.1_09/man/man1/*': No such file or directory
dpkg: error processing jre (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 jre

```

Do I need to be an owner of /usr/java directory?
Thanks,
Abcuser
Did you try to use sudo?

Also, did you try my RPM --> DEB package ?

---

### Post by msak007 on 2007-04-02
You don't necessarily have to use the RPM. They provide a self-extracting .bin file for distributions that don't use RPM. I know many people use alien successfully, but I personally hosed my system once trying to install an RPM using alien so I don't particularly recommend that option. When you go to the download page I linked to before, there's 2 options for Linux: RPM and self-extracting file. Choose the self-extracting file.

Once you have the file, these are the instructions:

> **Installation of Self-Extracting Binary**[INDENT] Use these instructions if you want to use the self-extracting  binary file to install the Java 2 Runtime Environment.  If you want to install  RPM packages instead, see [Installation of RPM File]("http://java.sun.com/products/archive/j2se/1.3.1_09/jre/install-linux.html#install-pkg").     [SIZE=+1][COLOR=#ff0000][B]

1.[/B][/COLOR][/SIZE] **Check the download file size**[INDENT] Before you download a file, notice that its byte size is provided on the download page. Once the download has completed, check that you have downloaded the full, uncorrupted software file.  If the file size doesn't match, it probably means the file was corrupted during download.  In that case, try downloading again. 
[/INDENT][SIZE=+1][COLOR=#ff0000]**2.**[/COLOR][/SIZE] **Change to the directory you want to install into.**[INDENT] For example, if you want to install the software in the  /usr/java/ directory, then execute:    cd /usr/java
 [/INDENT][SIZE=+1][COLOR=#ff0000]**3.**[/COLOR][/SIZE] **Run j2re-1_3_1_<version number>-linux-i586.bin and  agree to the license it displays.**[INDENT] Launch the installation script by using the following commands from  the directory in which the script is located:[INDENT]chmod a+x j2re-1_3_1_<version number>-linux-i586.bin

./j2re-1_3_1_<version number>-linux-i586.bin

[/INDENT]The script will display a binary license agreement, which you  will be asked to agree to before installation can proceed. Once  you have agreed to the license, the install script will install  the JRE in a directory called jre1.3.1_<version number> in  the current directory.  **Note about root access** -  If you choose to install the Java 2 Runtime Environment into  system-wide location such as /usr/local, you must first become root to gain the necessary permissions. If you do not have root access, simply install the Java 2 Runtime Environment into your home directory,  or a subdirectory that you have permission to write to.[/INDENT][/INDENT]

---

### Post by abcuser on 2007-04-02
> **kahrytan said:**
> Did you try to use sudo?
What do you mean by that? I have used the above commands. When installing deb package I used sudo command like I have described above.

[QUOTE=kahrytan]Also, did you try my RPM --> DEB package ?[/QUOTE]
Don't know what you mean by this. Can you please post more info.

---

### Post by msak007 on 2007-04-02
> **abcuser said:**
> What do you mean by that? I have used the above commands. When installing deb package I used sudo command like I have described above.


Don't know what you mean by this. Can you please post more info.
Don't worry about it, you did use sudo and by RPM --> DEB package he meant using alien to convert the RPM to a DEB, which you clearly did. Have you tried the BIN?

---

