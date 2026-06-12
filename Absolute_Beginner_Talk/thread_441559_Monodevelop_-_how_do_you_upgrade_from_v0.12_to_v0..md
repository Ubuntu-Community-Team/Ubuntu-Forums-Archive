---
title: "Monodevelop - how do you upgrade from v0.12 to v0.13????"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-12
I have Monodevelop installed on my Ubuntu Feisty Linux.
It is v0.12.
I downloaded and installed the v0.13 Monodevelop but the version still indicates v0.12.

Later, in Monodevelop, I selected Tools->Add-in Manager to install some stuff but it complains that v0.13 is required to install.

Anyone else note this?  Any fixes?

Carl

---

### Post by FuturePast on 2007-05-12
When you install an application from the Ubuntu repository, its version (e.g. 0.12) will stay fixed (apart from bug fixes) until the next major Ubuntu release.

If you have installed a newer version from the project website, then you should follow the instruction on that website on how to run the app.

Can you explain the steps you took to install the newer version, please.

---

### Post by cwmoser on 2007-05-12
I downloaded Monodevelop from [http://www.monodevelop.org/Download](http://www.monodevelop.org/Download).

I downloaded the rpm file  - monodevelop-0.13.1-0.novell.noarch.rpm

After downloading, I ran:

$ sudo alien monodevelop-0.13.1-0.novell.noarch.rpm

$ sudo apt-get install  monodevelop-0.13.1-0.novell.noarch.deb


Then when I startup Monodevelop and go to Help -> About, it states that it is version 0.12


Carl

---

### Post by FuturePast on 2007-05-12
Ok, now can you post the results of:
```
$ dpkg -s monodevelop
$ dpkg -L monodevelop
$ which monodevelop
```

---

### Post by cwmoser on 2007-05-13
Here is the results - thanks for looking -- Carl


carl@klaatu:~$ dpkg -s monodevelop
Package: monodevelop
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 5548
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: all
Version: 0.12+dfsg-1ubuntu1
Provides: monodoc-viewer
Depends: mono-runtime (>= 1.1.8.1), libgconf2.0-cil (>= 2.15.0), libgecko2.0-cil (>= 0.11-3), libglade2.0-cil (>= 2.9.0), libglib2.0-0 (>= 2.12.0), libglib2.0-cil (>= 2.9.0), libgnome2.0-cil (>= 2.15.0), libgtk2.0-0 (>= 2.10.3), libgtk2.0-cil (>= 2.9.0), libgtksourceview1.0-0 (>= 1.7.2), libgtksourceview2.0-cil (>= 0.10), libgtksourceview2.0-cil (<< 0.11), liblog4net1.2-cil (>= 1.2.8), liblog4net1.2-cil (<< 1.2.10), libmetacity0 (>= 1:2.14), libmono-cecil0.4-cil (>= 0.4.3), libmono-corlib1.0-cil (>= 1.0), libmono-corlib2.0-cil (>= 1.2.2), libmono-sharpzip2.84-cil (>= 1.0), libmono-system-runtime2.0-cil (>= 1.0), libmono-system-web2.0-cil (>= 1.0), libmono-system1.0-cil (>= 1.0), libmono-system2.0-cil (>= 1.2.2), libmono-winforms2.0-cil (>= 1.2.2), libmono1.0-cil (>= 1.2.2), libmono2.0-cil (>= 1.2.2), monodoc-base (>= 1.0), mono-mcs (>= 1.1.10), monodoc-manual (>= 1.1.9), pkg-config, gnome-icon-theme (>= 1.1.3), xterm | x-terminal-emulator, metacity, firefox
Suggests: monodevelop-boo, monodevelop-java, monodevelop-nunit, monodevelop-versioncontrol, monodevelop-query, nemerle, mono-gmcs, mono-xsp, mono-xsp2
Description: C#/Boo/Java/Nemerle/ILasm/ASP.NET Development Environment
 MonoDevelop is a GNOME IDE primarily designed for C# and other .NET
 languages.
 .
 Features: Debugger Integration, Class Browser, Monodoc Integration,
 Code Completion, Embedded HTML viewer, Gettext support, Boo project support,
 Java project support, Nemerle project support, ILAsm project support,
 ASP.NET project support.
Original-Maintainer: Mirco Bauer <meebey@meebey.net>
carl@klaatu:~$ 





carl@klaatu:~$ dpkg -L monodevelop
/.
/usr
/usr/lib
/usr/lib/monodevelop
/usr/lib/monodevelop/bin
/usr/lib/monodevelop/bin/MonoDevelop.Dock.dll
/usr/lib/monodevelop/bin/NRefactory.dll
/usr/lib/monodevelop/bin/MonoDevelop.Core.dll
/usr/lib/monodevelop/bin/MonoDevelop.exe
/usr/lib/monodevelop/bin/MonoDevelop.exe.config
/usr/lib/monodevelop/bin/mdhost.exe
/usr/lib/monodevelop/bin/mdrun.exe
/usr/lib/monodevelop/bin/mdrun.exe.config
/usr/lib/monodevelop/AddIns
/usr/lib/monodevelop/AddIns/MonoDevelop.Core.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.Components.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.Core.Gui.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.Core.Gui.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.Projects.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.Projects.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.Projects.dll.config
/usr/lib/monodevelop/AddIns/MonoDevelop.Documentation.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.Documentation.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.Projects.Gui.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.Projects.Gui.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.Ide.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.Ide.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.SourceEditor.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.SourceEditor.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.SourceEditor.dll.config
/usr/lib/monodevelop/AddIns/MonoDevelop.Autotools
/usr/lib/monodevelop/AddIns/MonoDevelop.Autotools/MonoDevelop.Autotools.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.Autotools/MonoDevelop.Autotools.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.Autotools/Makefile.am.project.template
/usr/lib/monodevelop/AddIns/MonoDevelop.Autotools/Makefile.include
/usr/lib/monodevelop/AddIns/MonoDevelop.Autotools/autogen.sh.template
/usr/lib/monodevelop/AddIns/MonoDevelop.Autotools/configure.ac.template
/usr/lib/monodevelop/AddIns/MonoDevelop.Autotools/exe.wrapper.in.template
/usr/lib/monodevelop/AddIns/MonoDevelop.Autotools/package.pc.template
/usr/lib/monodevelop/AddIns/BackendBindings
/usr/lib/monodevelop/AddIns/BackendBindings/CSharpBinding.dll
/usr/lib/monodevelop/AddIns/BackendBindings/CSharpBinding.addin.xml
/usr/lib/monodevelop/AddIns/BackendBindings/CSharpBinding.Autotools.dll
/usr/lib/monodevelop/AddIns/BackendBindings/ILAsmBinding.dll
/usr/lib/monodevelop/AddIns/BackendBindings/ILAsmBinding.addin.xml
/usr/lib/monodevelop/AddIns/BackendBindings/VBNetBinding.dll
/usr/lib/monodevelop/AddIns/BackendBindings/VBNetBinding.addin.xml
/usr/lib/monodevelop/AddIns/prj2make-sharp-lib.dll
/usr/lib/monodevelop/AddIns/prj2make-sharp-lib.addin.xml
/usr/lib/monodevelop/AddIns/WelcomePage
/usr/lib/monodevelop/AddIns/WelcomePage/WelcomePage.dll
/usr/lib/monodevelop/AddIns/WelcomePage/WelcomePage.addin.xml
/usr/lib/monodevelop/AddIns/WelcomePage/mono-bg.png
/usr/lib/monodevelop/AddIns/WelcomePage/mono-logo.png
/usr/lib/monodevelop/AddIns/WelcomePage/WelcomePage.css
/usr/lib/monodevelop/AddIns/WelcomePage/WelcomePage.xsl
/usr/lib/monodevelop/AddIns/ChangeLogAddIn
/usr/lib/monodevelop/AddIns/ChangeLogAddIn/ChangeLogAddIn.dll
/usr/lib/monodevelop/AddIns/ChangeLogAddIn/ChangeLogAddIn.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.GtkCore
/usr/lib/monodevelop/AddIns/MonoDevelop.GtkCore/MonoDevelop.GtkCore.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.GtkCore/MonoDevelop.GtkCore.dll.mdb
/usr/lib/monodevelop/AddIns/MonoDevelop.GtkCore/MonoDevelop.GtkCore.addin.xml
/usr/lib/monodevelop/AddIns/MonoDevelop.GtkCore/libstetic.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.GtkCore/libsteticui.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.GtkCore/libstetic.dll.config
/usr/lib/monodevelop/AddIns/MonoDevelop.GtkCore/libsteticui.dll.config
/usr/lib/monodevelop/AddIns/MonoDevelop.DesignerSupport
/usr/lib/monodevelop/AddIns/MonoDevelop.DesignerSupport/MonoDevelop.DesignerSupport.dll
/usr/lib/monodevelop/AddIns/MonoDevelop.DesignerSupport/MonoDevelop.DesignerSupport.addin.xml
/usr/lib/monodevelop/AddIns/AspNetAddIn
/usr/lib/monodevelop/AddIns/AspNetAddIn/AspNetAddIn.dll
/usr/lib/monodevelop/AddIns/AspNetAddIn/AspNetAddIn.addin.xml
/usr/lib/monodevelop/data
/usr/lib/monodevelop/data/options
/usr/lib/monodevelop/data/options/DefaultEditingLayout.xml
/usr/lib/monodevelop/data/options/MonoDevelopProperties.xml
/usr/lib/monodevelop/data/options/MonoDevelop-templates.xml
/usr/lib/monodevelop/data/options/MonoDevelop-tools.xml
/usr/lib/monodevelop/data/options/TipsOfTheDay.xml
/usr/lib/monodevelop/data/resources
/usr/lib/monodevelop/data/resources/css
/usr/lib/monodevelop/data/resources/css/MsdnHelp.css
/usr/lib/monodevelop/data/resources/css/SharpDevelopStandard.css
/usr/lib/pkgconfig
/usr/lib/pkgconfig/monodevelop.pc
/usr/share
/usr/share/locale
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/monodevelop.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/monodevelop.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/monodevelop.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/monodevelop.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/monodevelop.mo
/usr/share/locale/ja_JP
/usr/share/locale/ja_JP/LC_MESSAGES
/usr/share/locale/ja_JP/LC_MESSAGES/monodevelop.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/monodevelop.mo
/usr/share/locale/tr
/usr/share/locale/tr/LC_MESSAGES
/usr/share/locale/tr/LC_MESSAGES/monodevelop.mo
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/monodevelop.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/monodevelop.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/monodevelop.mo
/usr/share/locale/zh_CN
/usr/share/locale/zh_CN/LC_MESSAGES
/usr/share/locale/zh_CN/LC_MESSAGES/monodevelop.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/monodevelop.mo
/usr/share/locale/sl_SI
/usr/share/locale/sl_SI/LC_MESSAGES
/usr/share/locale/sl_SI/LC_MESSAGES/monodevelop.mo
/usr/share/locale/ca
/usr/share/locale/ca/LC_MESSAGES
/usr/share/locale/ca/LC_MESSAGES/monodevelop.mo
/usr/share/applications
/usr/share/applications/monodevelop.desktop
/usr/share/pixmaps
/usr/share/pixmaps/monodevelop.png
/usr/share/mime
/usr/share/mime/packages
/usr/share/mime/packages/monodevelop.xml
/usr/share/doc
/usr/share/doc/monodevelop
/usr/share/doc/monodevelop/NEWS.Debian.gz
/usr/share/doc/monodevelop/changelog.gz
/usr/share/doc/monodevelop/README
/usr/share/doc/monodevelop/copyright
/usr/share/doc/monodevelop/changelog.Debian.gz
/usr/share/menu
/usr/share/menu/monodevelop
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/monodevelop.1.gz
/usr/bin
/usr/bin/monodevelop
/usr/bin/mdtool
carl@klaatu:~$ 




carl@klaatu:~$ which monodevelop
/usr/bin/monodevelop
carl@klaatu:~$

---

### Post by FuturePast on 2007-05-15
Well, all I can say is, this line:
$ sudo apt-get install monodevelop-0.13.1-0.novell.noarch.deb
didn't succeed, and the version you are running is the original 0.12.

Unfortunately it's unreliable to install packages (especially non-debs) from 3rd parties.

---

### Post by DaleEMoore on 2007-05-19
Hi All,

I too would like to be a little closer to the fast changing mono development tools. I'm especially looking forward to the soon-to-be-re-available mono-debugger integration to mono-develop.

Does anyone within the sound of my voice :) have any experience at staying closer to the mono development releases?

Many thanks for any help you can provide,
Dale E. Moore

---

### Post by DaleEMoore on 2007-05-19
Hi All,

I found this [http://lists.ximian.com/pipermail/mono-devel-list/2007-May/023416.html]("http://lists.ximian.com/pipermail/mono-devel-list/2007-May/023416.html") link has some insight.

Good luck,
Dale E. Moore

---

