---
title: "Java6 installed, but broken links in /bin and /alternatives"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Cubby on 2008-04-12
Hi,

When I go to >Places>Search for Files and type in java of which there is listed 299 files, I notice in /etc/alternatives for java.1.gz, javaws, java_vm, java says, link (broken), and
in /usr/bin for javaws, java and java_vm says, link (broken)

I have both Firefox and Swiftweasel browsers and java does work for both, but I don't like having those broken links.  Should I just ignore them? 

When I do java -version I get this:
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found

Sorry, I don't know how to set Paths.  Is it not finding it because of the broken links?

I also notice I don't have the following folder: /usr/java, and from my search, many say this is where java should be installed, but not so for me.  

From doing a search on this, one person said this is a common error with feisty fawn ubuntu.  

I went ahead and installed sun-java6 bin file via terminal from ubuntugeeks website [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html) on how to install java.  I did that because when I installed sun-java5 via synaptic package manager, java wouldn't work for either browser.  So I uninstalled java5 and installed java6 manually using dpkg.

Here is a partial listing of java folders, with notable files highlighted: I appreciate anyone's help with this!
```
/var/cache/apt/archives/sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb
/var/cache/apt/archives/sun-java6-fonts_6-00-2ubuntu2_all.deb
/var/cache/apt/archives/sun-java5-jre_1.5.0-11-1ubuntu2_all.deb
/var/cache/apt/archives/sun-java6-bin_6-00-2ubuntu2_i386.deb
/var/cache/apt/archives/sun-java6-plugin_6-00-2ubuntu2_i386.deb
/var/cache/apt/archives/java-common_0.25ubuntu2_all.deb
/var/cache/apt/archives/sun-java6-jre_6-00-2ubuntu2_all.deb
/var/cache/apt/archives/openoffice.org-java-common_2.2.0-1ubuntu5_all.deb
/var/lib/doc-base/info/java-policy.status
/var/lib/doc-base/info/java-policy.list
/var/lib/doc-base/info/debian-java-faq.status
/var/lib/doc-base/info/debian-java-faq.list
/var/lib/dpkg/alternatives/javaws
/var/lib/dpkg/alternatives/firefox-javaplugin.so
/var/lib/dpkg/alternatives/java
/var/lib/dpkg/alternatives/java_vm
/var/lib/dpkg/alternatives/mozilla-javaplugin.so
/var/lib/dpkg/alternatives/iceape-javaplugin.so
/var/lib/dpkg/alternatives/iceweasel-javaplugin.so
/var/lib/dpkg/info/sun-java6-bin.postrm
/var/lib/dpkg/info/libjaxp1.3-java.list
/var/lib/dpkg/info/sun-java6-jre.postinst
/var/lib/dpkg/info/java-common.postinst
/var/lib/dpkg/info/sun-java6-jre.preinst
/var/lib/dpkg/info/libxalan2-java.md5sums
/var/lib/dpkg/info/sun-java6-bin.preinst
/var/lib/dpkg/info/openoffice.org-java-common.list
/var/lib/dpkg/info/libhsqldb-java.md5sums
/var/lib/dpkg/info/sun-java5-bin.list
/var/lib/dpkg/info/libhsqldb-java.list
/var/lib/dpkg/info/libjaxp1.3-java.md5sums
/var/lib/dpkg/info/sun-java6-jre.list
/var/lib/dpkg/info/sun-java6-fonts.postinst
/var/lib/dpkg/info/sun-java5-bin.postrm
/var/lib/dpkg/info/java-common.md5sums
/var/lib/dpkg/info/sun-java6-jre.config
/var/lib/dpkg/info/libservlet2.3-java.md5sums
/var/lib/dpkg/info/sun-java6-plugin.list
/var/lib/dpkg/info/libjline-java.list
/var/lib/dpkg/info/libxerces2-java.md5sums
/var/lib/dpkg/info/libxalan2-java.list
/var/lib/dpkg/info/sun-java6-plugin.prerm
/var/lib/dpkg/info/sun-java6-bin.templates
/var/lib/dpkg/info/libxerces2-java.list
/var/lib/dpkg/info/sun-java6-plugin.postinst
/var/lib/dpkg/info/libjline-java.md5sums
/var/lib/dpkg/info/sun-java6-fonts.prerm
/var/lib/dpkg/info/libhsqldb-java.postrm
/var/lib/dpkg/info/libhsqldb-java.postinst
/var/lib/dpkg/info/sun-java6-jre.postrm
/var/lib/dpkg/info/sun-java6-fonts.list
/var/lib/dpkg/info/sun-java6-jre.md5sums
/var/lib/dpkg/info/sun-java6-bin.conffiles
/var/lib/dpkg/info/sun-java6-bin.prerm
/var/lib/dpkg/info/sun-java6-jre.templates
/var/lib/dpkg/info/sun-java6-bin.postinst
/var/lib/dpkg/info/sun-java6-fonts.conffiles
/var/lib/dpkg/info/sun-java6-bin.list
/var/lib/dpkg/info/java-common.conffiles
/var/lib/dpkg/info/java-common.prerm
/var/lib/dpkg/info/openoffice.org-java-common.md5sums
/var/lib/dpkg/info/libservlet2.3-java.list
/var/lib/dpkg/info/openoffice.org-java-common.postinst
/var/lib/dpkg/info/java-common.list
/var/lib/dpkg/info/sun-java6-bin.md5sums
/etc/alternatives/javaws.1.gz [COLOR="SeaGreen"]link (broken)[/COLOR]
/etc/alternatives/javaws [COLOR="SeaGreen"]link (broken)[/COLOR]
/etc/alternatives/firefox-javaplugin.so
/etc/alternatives/java [COLOR="SeaGreen"]link (broken)[/COLOR]
/etc/alternatives/java_vm [COLOR="SeaGreen"]link (broken)[/COLOR]
/etc/alternatives/mozilla-javaplugin.so
/etc/alternatives/java.1.gz [COLOR="SeaGreen"]link (broken)[/COLOR]
/etc/alternatives/iceape-javaplugin.so
/etc/alternatives/iceweasel-javaplugin.so
/etc/java-6-sun
/etc/java-6-sun/security/java.security
/etc/java-6-sun/security/java.policy
/etc/java
/etc/java/security/security.d/1000-gnu.java.security.provider.Gnu
/etc/java/security/security.d/1004-gnu.javax.security.auth.callback.GnuCallbacks
/etc/java/security/security.d/1001-gnu.javax.crypto.jce.GnuCrypto
/etc/java/security/security.d/1002-gnu.javax.crypto.jce.GnuSasl
/etc/java/security/security.d/1003-gnu.javax.net.ssl.provider.Jessie
/etc/java-1.5.0-sun
/etc/java-1.5.0-sun/security/java.security
/etc/java-1.5.0-sun/security/java.policy
/etc/defoma/hints/sun-java6-fonts.hints
/usr/sbin/update-java-alternatives
/usr/bin/javaws [COLOR="SeaGreen"]link (broken)[/COLOR]
/usr/bin/java [COLOR="SeaGreen"]link (broken)[/COLOR]
/usr/bin/java_vm [COLOR="SeaGreen"]link (broken)[/COLOR]
/usr/share/applications/sun-java6-javaws.desktop
/usr/share/applications/sun-java6-java.desktop
/usr/share/pycentral/python-xml/site-packages/_xmlplus/dom/javadom.py
/usr/share/pycentral/python-xml/site-packages/_xmlplus/sax/drivers2/drv_javasax.py
/usr/share/icons/sun-java6.png
/usr/share/icons/sun-java6.xpm
/usr/share/application-registry/sun-java6-web-start.applications
/usr/share/application-registry/sun-java6-archive.applications
/usr/share/java-common
/usr/share/java-common/java-common.sh
/usr/share/doc/openoffice.org-java-common
/usr/share/doc/java-common
/usr/share/doc/java-common/debian-java-faq
/usr/share/doc/java-common/debian-java-faq/ch-debian-java-sarge.html
/usr/share/doc/java-common/debian-java-faq/ch-debian-java-woody.html
/usr/share/doc/java-common/debian-java-faq/ch-browser-java.html
/usr/share/doc/java-common/debian-java-policy
/usr/share/doc/java-common/dummy-packages/java2-compiler-dummy.control
/usr/share/doc/java-common/dummy-packages/java2-runtime-dummy.control
/usr/share/doc/java-common/dummy-packages/java1-runtime-dummy.control
/usr/share/doc/java-common/dummy-packages/java-compiler-dummy.control
/usr/share/doc/java-common/dummy-packages/java-virtual-machine-dummy.control
/usr/share/doc/libxerces2-java
/usr/share/doc/libhsqldb-java
/usr/share/doc/libxalan2-java
/usr/share/doc/libservlet2.3-java
/usr/share/doc/libservlet2.3-java/api/javax
/usr/share/doc/python-xml/examples/test/test_javadom.py.gz
/usr/share/doc/python-xml/examples/test/output/test_javadom
/usr/share/doc/sun-java6-jre
/usr/share/doc/sun-java6-jre/JAVA_HOME
/usr/share/doc/sun-java6-fonts
/usr/share/doc/libjaxp1.3-java
/usr/share/doc/sun-java6-bin
/usr/share/doc/libjline-java
/usr/share/doc/sun-java6-plugin
/usr/share/java
/usr/share/java/openoffice/java_uno.jar
/usr/share/java/openoffice/ScriptProviderForJavaScript.jar
/usr/share/java/openoffice/java_uno_accessbridge.jar
/usr/share/java/openoffice/ScriptProviderForJava.jar
/usr/share/mime-info/sun-java6-web-start.mime
/usr/share/mime-info/sun-java6-archive.keys
/usr/share/mime-info/sun-java6-web-start.keys
/usr/share/mime-info/sun-java6-archive.mime
/usr/share/mime/application/x-java-jnlp-file.xml
/usr/share/mime/application/java-archive.xml
/usr/share/mime/application/x-java.xml
/usr/share/mime/application/x-java-archive.xml
/usr/share/mime/application/javascript.xml
/usr/share/mime/packages/sun-java6-jre.xml
/usr/share/mime/text/x-java.xml
/usr/share/gtksourceview-1.0/language-specs/javascript.lang
/usr/share/gtksourceview-1.0/language-specs/java.lang
/usr/share/man/man8/update-java-alternatives.8.gz
/usr/share/man/man1/javaws.1.gz
/usr/share/man/man1/java.1.gz
/usr/share/java-6-sun-1.6.0.00
/usr/share/nano/java.nanorc
/usr/share/control-center-2.0/capplets/sun-java6-controlpanel.desktop
/usr/share/control-center-2.0/capplets/sun-java6-policytool.desktop
/usr/share/gimp/2.0/patterns/java.pat
/usr/share/menu/libhsqldb-java
/usr/share/menu/sun-java6-bin
/usr/share/doc-base/debian-java-faq
/usr/share/doc-base/java-policy
/usr/share/lintian/overrides/sun-java6-jre
/usr/share/lintian/overrides/sun-java6-bin
/usr/share/gedit-2/plugins/snippets/java.xml
/usr/share/gedit-2/plugins/snippets/javascript.xml
/usr/share/omf/debian-java-faq
/usr/share/omf/debian-java-faq/debian-java-faq-C.omf
/usr/share/omf/java-policy
/usr/share/omf/java-policy/java-policy-C.omf
/usr/share/app-install/icons/_usr_lib_j2se_1.4_jre_plugin_desktop_sun_java.png
/usr/share/app-install/icons/_usr_share_icons_ia32-sun-java6.xpm
/usr/share/app-install/icons/_usr_share_icons_sun-java6.xpm
/usr/share/app-install/icons/_usr_share_icons_sun-java5.xpm
/usr/share/app-install/desktop/ia32-sun-java6-javaws.desktop
/usr/share/app-install/desktop/javaws1.4.desktop
/usr/share/app-install/desktop/java1.4.desktop
/usr/share/app-install/desktop/sun-java5-jconsole.desktop
/usr/share/app-install/desktop/sun-java5-plugin.desktop
/usr/share/app-install/desktop/ia32-sun-java6-java.desktop
/usr/share/app-install/desktop/sun-java6-javaws.desktop
/usr/share/app-install/desktop/sun-java6-jconsole.desktop
/usr/share/app-install/desktop/sun-java5-java.desktop
/usr/share/app-install/desktop/sun-java6-java.desktop
/usr/lib/mozilla/plugins/libjavaplugin.so
/usr/lib/mime/packages/sun-java6-bin
/usr/lib/iceape/plugins/libjavaplugin.so
/usr/lib/iceweasel/plugins/libjavaplugin.so
/usr/lib/python2.5/site-packages/_xmlplus/dom/javadom.py
/usr/lib/python2.5/site-packages/_xmlplus/dom/javadom.pyc
/usr/lib/python2.5/site-packages/_xmlplus/sax/drivers2/drv_javasax.pyc
/usr/lib/python2.5/site-packages/_xmlplus/sax/drivers2/drv_javasax.py
/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-6-sun-1.6.0.00
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws[COLOR="SeaGreen"] link to executable[/COLOR]
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/javaws
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/javaws[COLOR="SeaGreen"] executable[/COLOR]
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java [COLOR="SeaGreen"]executable[/COLOR]
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java_vm [COLOR="SeaGreen"]executable[/COLOR]
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/desktop/sun_java.desktop
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/desktop/sun_java.png
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/ko.UTF-8/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/it/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/fr/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/zh_HK.BIG5HK/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/zh.GBK/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/ja/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/zh/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/ko/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/es/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/de/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/zh_TW.BIG5/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/sv/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/locale/zh_TW/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/security/java.security
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/security/javaws.policy
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/security/java.policy
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/deploy/java-icon.ico
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/desktop/applications/sun-javaws.desktop
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/desktop/applications/sun_java.desktop
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/desktop/applications/sun-java.desktop
(a bunch of fonts I removed from the list at this point)
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/desktop/mime/packages/x-java-jnlp-file.xml
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/desktop/mime/packages/x-java-archive.xml
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjava_crw_demo.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjavaplugin_jni.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjavaplugin_nscp.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjavaplugin_nscp_gcc29.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjava.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/javaws.jar
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/man/ja/man1/javaws.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/man/ja/man1/java.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/man/man1/javaws.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/man/man1/java.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/javaws [COLOR="SeaGreen"]link to executable[/COLOR]
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java [COLOR="SeaGreen"]link to executable[/COLOR]
/usr/lib/jvm/java-6-sun-1.6.0.00/man/ja/man1/javaws.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.00/man/ja/man1/java.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.00/man/man1/javaws.1.gz
/usr/lib/jvm/java-6-sun-1.6.0.00/man/man1/java.1.gz
/usr/lib/openoffice/share/config/javavendors.xml
/usr/lib/openoffice/share/registry/schema/org/openoffice/Office/Java.xcs
/usr/lib/openoffice/share/registry/modules/org/openoffice/Office/Writer/Writer-javamail.xcu
/usr/lib/openoffice/share/Scripts/java
/usr/lib/openoffice/share/Scripts/java/Highlight/HighlightText.java
/usr/lib/openoffice/share/Scripts/java/HelloWorld/HelloWorld.java
/usr/lib/openoffice/share/Scripts/java/MemoryUsage/MemoryUsage.java
/usr/lib/openoffice/share/Scripts/javascript
/usr/lib/openoffice/program/javaldx
/usr/lib/openoffice/program/libjava_uno.so
/usr/lib/openoffice/program/javavm.uno.so
/usr/lib/openoffice/program/sunjavaplugin.so
/usr/lib/openoffice/program/libjava_uno
/usr/lib/openoffice/program/java-set-classpath
/usr/lib/openoffice/program/javaloader.uno.so
/usr/lib/firefox/plugins/libjavaplugin.so
```

---

### Post by Diabolis on 2008-04-12
> When I do java -version I get this:
The program 'java' can be found in the following packages:
* j2re1.4
* gij-4.1
* kaffe
* jamvm
* java-gcj-compat
* cacao
* sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found

If you are sure that you have installed JAVA, then the message says that you have to add it to your PATH variable otherwise you need to install JAVA.

You can add any directory or file to your path. Open this file:
```
gedit .bashrc
```

 At the end of it you can add any variables you want and modify existing ones. I added JAVA to my path and also a folder were I store self made scripts, so I can execute them directly from terminal without having to type the path to them. Have a look at it:
```
# User specific environment and startup programs

JAVAHOME=/home/gaston/jdk1.6.0_03/bin
GASTONBIN=/home/gaston/misDocumentos/bin
PATH=$PATH:$GASTONBIN

```

Note that the folder that you add for java is the **bin** folder.

---

### Post by Cubby on 2008-04-12
Thank you, Diabolis, 

You are kind to take the time to share with me how to repair this.  I thought as much that I would have to set a PATH which is new for me to do. 

And, that I should have java in bin folder is helpful as I was confused where it should be.

I will work on this in the upcoming week.

Warmest regards!

---

