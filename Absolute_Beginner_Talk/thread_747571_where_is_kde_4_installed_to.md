---
title: "where is kde 4 installed to?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Drone4four on 2008-04-06
How do I find out where on my HD KDE 4 is installed to?

---

### Post by Drone4four on 2008-04-06
someone in #ubuntu on FreeNode pointed out that I can use the dpkg -L kde[autocomplete] command.  Here is some output:
```

mary@ubuntu:~/cloudcity$ dpkg -L kdebase-bin
kdebase-bin       kdebase-bin-kde4  
mary@ubuntu:~/cloudcity$ dpkg -L kdebase-bin-kde4 
/.
/usr
/usr/lib
/usr/lib/kde4
/usr/lib/kde4/bin
/usr/lib/kde4/bin/kdialog
/usr/lib/kde4/bin/keditfiletype
/usr/share
/usr/share/doc
/usr/share/doc/kdebase-bin-kde4
/usr/share/doc/kdebase-bin-kde4/changelog.Debian.gz
/usr/share/doc/kdebase-bin-kde4/copyright
/usr/share/doc/kdebase-bin-kde4/AUTHORS
/usr/share/doc/kdebase-bin-kde4/README.

```

And some more:

```

mary@ubuntu:~/cloudcity$ dpkg -L kde4-core 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/kde4-core
/usr/share/doc/kde4-core/README.Debian
/usr/share/doc/kde4-core/copyright
/usr/share/doc/kde4-core/changelog.gz

```

So this answers my question.  However, only now do I realize that I don't really need to know where KDE4 is installed.  I need to know where Qt4 is installed.  Here is a command given to me from unop in #ubuntu:```

mary@ubuntu:~/cloudcity$ dpkg -l | grep -i qt | cut -c 3-30
  gtk-qt-engine             
  gtk2-engines-gtk-qt       
  gtk2-engines-qtcurve      
  gtk2-engines-qtpixmap     
  libavahi-qt3-1            
  libdbus-qt-1-1c2          
  libqimageblitz4           
  libqt3-headers            
  libqt3-mt                 
  libqt3-mt-dev             
  libqt4-core               
  libqt4-gui                
  libqt4-qt3support         
  libqt4-sql                
  libqthreads-12            
  libsoprano4               
  libstrigiqtdbusclient0    
  qt3-dev-tools    

``` 
What this command does iis it searches all the installed pakcages for packages with "qt" in it.  I am unsure what cut -c 3-30 does, but oh well.  The command gives me what I am looking for.  Now:```

mary@ubuntu:~/cloudcity$ dpkg -L libqt4-core 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libqt4-core
/usr/share/doc/libqt4-core/changelog.Debian.gz
/usr/share/doc/libqt4-core/copyright
/usr/share/doc/libqt4-core/changelog.gz
/usr/share/doc/libqt4-core/GPL_EXCEPTION_ADDENDUM.TXT.gz
/usr/share/qt4
/usr/share/qt4/translations
/usr/share/qt4/translations/assistant_de.qm
/usr/share/qt4/translations/assistant_ja.qm
/usr/share/qt4/translations/assistant_pl.qm
/usr/share/qt4/translations/assistant_zh_CN.qm
/usr/share/qt4/translations/designer_de.qm
/usr/share/qt4/translations/designer_ja.qm
/usr/share/qt4/translations/designer_pl.qm
/usr/share/qt4/translations/designer_zh_CN.qm
/usr/share/qt4/translations/linguist_ja.qm
/usr/share/qt4/translations/linguist_pl.qm
/usr/share/qt4/translations/linguist_zh_CN.qm
/usr/share/qt4/translations/qt_ar.qm
/usr/share/qt4/translations/qt_de.qm
/usr/share/qt4/translations/qt_es.qm
/usr/share/qt4/translations/qt_fr.qm
/usr/share/qt4/translations/qt_iw.qm
/usr/share/qt4/translations/qt_ja_jp.qm
/usr/share/qt4/translations/qt_pl.qm
/usr/share/qt4/translations/qt_pt.qm
/usr/share/qt4/translations/qt_ru.qm
/usr/share/qt4/translations/qt_sk.qm
/usr/share/qt4/translations/qt_sv.qm
/usr/share/qt4/translations/qt_uk.qm
/usr/share/qt4/translations/qt_zh_CN.qm
/usr/share/qt4/translations/qtconfig_pl.qm
/usr/share/qt4/translations/qtconfig_zh_CN.qm
/usr/share/qt4/translations/qvfb_pl.qm
/usr/share/qt4/translations/qvfb_zh_CN.qm
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libqt4-core
/usr/lib
/usr/lib/libQtCore.so.4.3.2
/usr/lib/libQtNetwork.so.4.3.2
/usr/lib/libQtXml.so.4.3.2
/usr/lib/libQtTest.so.4.3.2
/usr/lib/libQtDBus.so.4.3.2
/usr/lib/libQtScript.so.4.3.2
/usr/bin
/usr/bin/qdbus
/usr/lib/libQtCore.so.4
/usr/lib/libQtCore.so.4.3
/usr/lib/libQtNetwork.so.4
/usr/lib/libQtNetwork.so.4.3
/usr/lib/libQtXml.so.4
/usr/lib/libQtXml.so.4.3
/usr/lib/libQtTest.so.4
/usr/lib/libQtTest.so.4.3
/usr/lib/libQtDBus.so.4
/usr/lib/libQtDBus.so.4.3
/usr/lib/libQtScript.so.4
/usr/lib/libQtScript.so.4.3

```

Ta-da: This is the file and location I am looking for: /usr/lib/libQtCore.so.4.3.2

---

