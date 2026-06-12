---
title: "[SOLVED] JRE problem"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-25
I installed JRE today for FF b4. When i opened FF b4 again  and it didnt work.So i tried after rebooting but again not working.How do i uninstall it?

---

### Post by kpkeerthi on 2008-03-25
> **adi_das said:**
> How do i uninstall it?
So you want to uninstall firefox or jre?

---

### Post by adi_das on 2008-03-25
Jre

---

### Post by jan quark on 2008-03-25
if you mean java

then this should remove the firefox plugin

```
sudo apt-get remove sun-java6-plugin
```

how did you install it? and please be more specific than only JRE... thank you

---

### Post by adi_das on 2008-03-25
No. I have downloaded jre from java website and installed it

---

### Post by jan quark on 2008-03-25
did the code worked?
can you please post the link to the download location?

---

### Post by adi_das on 2008-03-25
[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

I installed 	Linux (self-extracting file)  filesize: 18.83 MB  by following the instructions

---

### Post by jan quark on 2008-03-25
did you also create the symbolic link as described in the instructions?



> Firefox

   1. Go to the plugins sub-directory under the Firefox installation directory
      cd <Firefox installation directory>/plugins

   2. In the current directory, create a symbolic link to the JRE ns7/libjavaplugin_oji.so file Type:
      ln -s <JRE installation directory>/plugin/i386/ns7/libjavaplugin_oji.so

      Example:
          * If Firefox is installed at this directory:
            /usr/lib/firefox-1.4/
          * And if the JRE is installed at this directory:
            /usr/java/jre1.6.0
          * Then type at the terminal to go to the browser plug-in directory:
            cd /usr/lib/firefox-1.4/plugins
          * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
            ln -s /usr/java/jre1.6.0/plugin/i386/ns7-gcc29
            /libjavaplugin_oji.so

      In the command line above, use ns7-gcc29 if Firefox was compiled with gcc2.9.

      If you install Firefox 1.5 or later, you can enable the Java Console menu item in the Tools menu. Change directories to the Firefox extensions directory, then unzip ffjcext.zip there.

      cd /usr/lib/firefox-1.4/extensions
      unzip /usr/java/jre1.6.0/lib/deploy/ffjcext.zip

   3. Start the Firefox browser, or restart it if it is already up.

      In Firefox, type about:plugins in the Location bar to confirm that the Java Plugin is loaded. If the version is Firefox 1.5 or later, click the Tools menu to confirm that Java Console is there


perhaps if you still want to remove it
you can do it via synaptic 
search for 
```
 jre1.6.0
```

---

