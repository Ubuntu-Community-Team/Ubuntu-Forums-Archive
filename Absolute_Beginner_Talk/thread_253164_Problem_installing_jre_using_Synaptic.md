---
title: "Problem installing jre using Synaptic"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by vulturesrow on 2006-09-07
Hi all, 

I recently tried to install the JRE via synaptic. I get the following errors in a popup window:

```
E: /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb: subprocess pre-installation script returned error exit status 2
```

and this is the output from the terminal window:

```
Preconfiguring packages...
(Reading database ... 72707 files and directories currently installed.)
Unpacking sun-java5-re (from .../sun-java5-jre_1.05-0601_all.deb)...
debconf: Unable to load Debconf::Element::Gnome::Note. Failed because: Cant locate I18N/Langinfo.pm in @INC (@INC contains: /et/perl /usr/local/lib/perl/5.8.7
/usr/local/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Element/Gnome.pm line 7, <GEN6> line 5.
Compilation failed in require at (eval 24) line 3, MGEN6> line 5
        ...propogated at /usr/share/perl/5.8/base.pm line 84, <GEN6> line 5
BEGIN failed--compilation aborted at (eval 21) line 2, <GEN6> line 5.

Can't locate object method "new" via package "Debconf::Element::Gnome::Note" at 
/usr/share/perl5/Debconf/FrontEnd.pm line 67, <GEN6> line 5.
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
(--unpack):
 subprocess pre-installation script returned error exit status 2
Unpacking sun-java5-bin (from .../sun-java-bin_1.5.0-06-1_i386.deb) ...
```

Thats actually not all of it but thats all I could bear to type out since I cant seem to copy this from the little terminal window you can open within Synaptic. Hopefully thats enough to give you smart guys a cluse as to what is going on. 

Thanks, 
Chris

---

### Post by davmac on 2006-09-08
Hi,

I can't answer you specific question but I used to Automatix to successfully install JRE.

You can find more info about installing Automatix at [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

Hope this helps,

Dave Mac

---

### Post by xyz on 2006-09-08
OR:
Download it from [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)
and then:
```
sudo chmod a+x jre-1_5_0_08-linux-i586.bin
sudo ./jre-1_5_0_08-linux-i586.bin
cd /usr/lib/firefox/plugins
ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so
cd /usr/lib/mozilla/plugins
ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so
```
Restart your browser.
It's tru that Automatix works fine

Source:  Unofficial Ubuntu 6.06 (Dapper Drake) Starter Guide

---

### Post by ckonrad on 2006-10-13
> **xyz said:**
> OR:
Download it from [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)
and then:
```
sudo chmod a+x jre-1_5_0_08-linux-i586.bin
sudo ./jre-1_5_0_08-linux-i586.bin
cd /usr/lib/firefox/plugins
ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so
cd /usr/lib/mozilla/plugins
ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so
```
Restart your browser.
It's tru that Automatix works fine

Source:  Unofficial Ubuntu 6.06 (Dapper Drake) Starter Guide

my terminal doesnt recognize the ln command.

---

### Post by xyz on 2006-10-13
Then install it with Automatix:
[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

