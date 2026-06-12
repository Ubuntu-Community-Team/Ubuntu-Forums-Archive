---
title: "Printer Driver"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by harerama on 2006-09-11
Hello,

Until two weeks ago I was using windows Me and now I am trying to shift to ubuntu. My printer is 
 canon pixus/pixma 2200 and driver for linux is not available both on ubuntu also from canon.

I think my option is I have to wait until it is available from some source.
Or maybe it is available somewhere? Do you have any suggestions?

Thank you.

---

### Post by kidders on 2006-09-12
I did a quick Google search for you, and [http://gentoo-wiki.com/Canon_pixma_series](http://gentoo-wiki.com/Canon_pixma_series) popped up. Since it's a Gentoo HOWTO, it's quite technical, but it does suggest your printer can be made to work ... even if it isn't all that straightforward.

Depending on how new to Linux you are, translating the HOWTO to Ubuntu speak might be tricky -- let me know if you need a translator (I use Gentoo too :P )

---

### Post by harerama on 2006-09-12
Actually I have seen this page and yes I didn't understand much. I don't have     
 time today anymore. I will try hard to understand this and seek your help again as soon as I can.

Thank you.

---

### Post by kidders on 2006-09-12
Kewl :cool:

If you're working off that page already, here are some quick pointers for when you find another chance to try it. Together, we can work on a Ubuntu-specific HOWTO, maybe :-P

[LIST]
[*]Ignore references to USE flags
[*]Gentoo's apt-get is called "emerge"
[*]By "making a portage overlay" and "emerge --digest"-ing things, the author is referring to turning code for another Linux into a package your system can understand.
[/LIST]

---

### Post by snakyjake on 2006-09-12
Might want to give this site a try:  [http://www.linuxprinting.org]("http://www.linuxprinting.org")

---

### Post by harerama on 2006-09-12
Hi, I took a hard look at this page.
([http://gentoo-wiki.com/Canon_pixma_series](http://gentoo-wiki.com/Canon_pixma_series)) 

Honestly I think I need a step by step help from you.

 First of all my pc is x86 so the page says
download from this page.
([http://bugs.gentoo.org/show_bug.cgi?id=130645)](http://bugs.gentoo.org/show_bug.cgi?id=130645)).

 I took a really hard look at this page but which one I have to download? Where I can find it?


PS,
One more question, Installation instruction on the page says 
"Make sure your Kernel supports either usb or parallel (whatever your printer is connected to)"
I assumed that Kernel supports usb. Am I right. 

Thanks

---

### Post by kidders on 2006-09-13
Hi there,

[http://shan.byethost33.com/cnijfilter-2.60-r1.tbz2](http://shan.byethost33.com/cnijfilter-2.60-r1.tbz2) seems to be the right link.

Once you've downloaded the tarball, you need to unpack it into your root filesystem, but don't do that right away. You see, the other garbage on the link I posted originally was to do with creating a "package" out of the tarball, so that your system is aware of what went where. The most obvious advantage to doing that is being able to uninstall the thing!! If you read up on Ubuntu's package management, you can do this for yourself :-)

Anyhow, installing the tarball scatters files throughout your /usr directory. The theory is that, once that's done (and you've restarted CUPS), it should magically know all there is to know about your Cannon. Personally, I find CUPS very confusing, so I'm not 100% sure how much help I can be if it *doesn't* work for you :-(

Fingers crossed!

---

### Post by harerama on 2006-09-13
Thanks. It seems there are things I have to know before I start. I'll be working on it later when I have a little bit of time.

---

### Post by slimdog360 on 2006-09-13
I have an official linux driver for a canon ip2200. Is that the same thing?

---

### Post by harerama on 2006-09-13
---------------------------------------------------------------------------
I have an official linux driver for a canon ip2200. Is that the same thing?
---------------------------------------------------------------------------
Where can I find it? Please let me know.

Thanks

---

### Post by slimdog360 on 2006-09-13
> **harerama said:**
> ---------------------------------------------------------------------------
I have an official linux driver for a canon ip2200. Is that the same thing?
---------------------------------------------------------------------------
Where can I find it? Please let me know.

Thanks

I sent you a message but for anyone else who may see this and want a driver here is the page which has the canon ip1000, ip1500, ip2200, ip4200 drivers.

[http://www.canon-europe.com/support/software/linux/index.asp]("http://www.canon-europe.com/support/software/linux/index.asp")

part of the disclaimer on the site: 
"Due to the changing nature of Linux distributions Canon Europe can not guarantee the compatibility of the driver in all Linux distributions."

---

### Post by harerama on 2006-09-14
I downloaded the file and its guide says.
-------------------------------------------------
Software

Fedora Core 4

Novell SUSE Linux 10.0

X Window System is necessary to use the GUI mode
-------------------------------------------------
So ubuntu is not included isn't it. Am I still able to install this driver somehow?

Thank you

---

### Post by slimdog360 on 2006-09-14
> **harerama said:**
> I downloaded the file and its guide says.
-------------------------------------------------
Software

Fedora Core 4

Novell SUSE Linux 10.0

X Window System is necessary to use the GUI mode
-------------------------------------------------
So ubuntu is not included isn't it. Am I still able to install this driver somehow?

Thank you

it should be fine. Just add a printer and manually choose the driver.

---

### Post by harerama on 2006-09-14
Honestly I have no idea how to proceed even though I have looked at the user's guide which I downloaded

The guide says
---------------------------------------------------------------------
Installation

Instructions for installing Print Filter are explained for each Linux distribution package.

If you want to install Print Filter, start Linux and log in as root.

Novell SUSE Linux 10.0

Fedora Core 4

Installation Files and Installation Locations
-----------------------------------------------------------------------

So I have to follow the last one which says.
-----------------------------------------------------------------------
Installation Files and Installation Locations

Installation files of iP2200

Listed below are the files to be installed in iP2200 and the installation locations of those files.

Common package

[Execution files]
/usr/local/bin/cngpij (cngpij command program)
/usr/lib/cups/filter/pstocanonij (CUPS filter)
/usr/lib/cups/backend/cnij_usb (CUPS backend-USB)

Model-specific package

[Execution files]
/usr/local/bin/cifip2200 (filter program)
/usr/local/bin/printuiip2200 (UI program)
/usr/local/bin/lgmonip2200 (language monitor)
/usr/local/bin/cngpijmon (status monitor for CUPS)

[PPD file]
/usr/share/cups/model/canonip2200.ppd (ppd file for CUPS)

[UI data]
/usr/local/share/printuiip2200/printui.glade (Glade file)
/usr/local/share/printuiip2200/printui.res (character string resource)
/usr/local/share/printuiip2200/locale-table (locale table)
/usr/local/share/printuiip2200/black_bar.xpm (pixmap file)
/usr/local/share/printuiip2200/cyan_bar.xpm (pixmap file)
/usr/local/share/printuiip2200/magenta_bar.xpm (pixmap file)
/usr/local/share/printuiip2200/yellow_bar.xpm (pixmap file)
/usr/local/share/printuiip2200/okptn_ip2200.xpm (pixmap file)
/usr/local/share/printuiip2200/ngptn_ip2200.xpm (pixmap file)
/usr/local/share/printuiip2200/nozl_ip2200.utl (print pattern file)
/usr/local/share/printuiip2200/regi_ip2200.utl (print pattern file)

/usr/local/share/locale/cs/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/da/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/de/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/el/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/es/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/fi/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/fr/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/hu/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/it/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/ja/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/ko/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/nl/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/no/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/pl/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/pt/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/ru/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/sv/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/th/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/tr/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/zh/LC_MESSAGES/printuiip2200.mo (catalog file)
/usr/local/share/locale/zh_TW/LC_MESSAGES/printuiip2200.mo (catalog file)

[Status monitor data]
/usr/local/share/locale/cs/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/da/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/de/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/el/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/es/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/fi/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/fr/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/hu/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/it/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/ja/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/ko/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/nl/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/no/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/pl/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/pt/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/ru/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/sv/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/th/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/tr/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/zh/LC_MESSAGES/cngpijmon.mo (catalog file)
/usr/local/share/locale/zh_TW/LC_MESSAGES/cngpijmon.mo (catalog file)

/usr/local/share/cngpijmon/pixmaps/Icon_Low.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Icon_Out.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Icon_Refill.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Icond_Low.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Icond_Out.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Icond_Refill.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Iconw_Low.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Iconw_Out.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Iconw_Refill.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink26b.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink26bb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink26c.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink26cy.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink26ma.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink26pc.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink26pm.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink26sb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink26ye.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24b.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24b1.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24b2.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24b3.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24bf.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24c.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24c1.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24c2.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24c3.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_24cf.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_Level_00.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_Level_10.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_Level_40.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_Level_70.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_Level_uk.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_bb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_bk.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_cy.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_el.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_er.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_gr.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_low.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_low010.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_low040.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_low070.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_low_bb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_ma.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_out.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_out_bb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_pb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_pc.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_pm.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_re.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_sp.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Ink_ye.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkd_Level_00.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkd_Level_10.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkd_Level_40.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkd_Level_70.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkd_Level_uk.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg26b.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg26bb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg26c.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg26cy.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg26ma.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg26pc.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg26pm.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg26sb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg26ye.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_bb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_bk.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_cy.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_el.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_er.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_gr.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_ma.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_pb.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_pc.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_pm.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_re.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_sp.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkg_ye.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkw_Level_00.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkw_Level_10.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkw_Level_40.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkw_Level_70.xpm (pixmap file)
/usr/local/share/cngpijmon/pixmaps/Inkw_Level_uk.xpm (pixmap file)

[Shared libraries]
/usr/lib/libcnbpcmcm256.so.6.31.1 (Command Complex shared library)
/usr/lib/libcnbpess256.so.2.2.2 (ESS shared library)
/usr/lib/libcnbpcnclui256.so.3.2.0 (CNCLUI shared library)
/usr/lib/libcnbpcnclapi256.so.3.2.0 (CNCLAPI shared library)
/usr/lib/libcnbpcnclbjcmd256.so.3.2.0 (Native shared library)
/usr/lib/libcnbpo256.so.1.01.1 (Output shared library)

/usr/lib/libcnbpcmcm256.so (symbolic link to /usr/lib/libcnbpcmcm256.so.6.31.1)
/usr/lib/libcnbpess256.so (symbolic link to /usr/lib/libcnbpess256.so.2.2.2)
/usr/lib/libcnbpcnclui256.so (symbolic link to /usr/lib/libcnbpcnclui256.so.3.2.0)
/usr/lib/libcnbpcnclapi256.so (symbolic link to /usr/lib/libcnbpcnclapi256.so.3.2.0)
/usr/lib/libcnbpcnclbjcmd256.so (symbolic link to /usr/lib/libcnbpcnclbjcmd256.so.3.2.0)
/usr/lib/libcnbpo256.so (symbolic link to /usr/lib/libcnbpo256.so.1.01.1)

[Databases by printer]
/usr/lib/bjlib/cnbpname256.tbl (library name database)
/usr/lib/bjlib/cnb_2560.tbl (database)
/usr/lib/bjlib/cifip2200.conf (command option data)
-------------------------------------------------------------------------

Can you help me how to install this? or Is this too much for a complete beginner like me to follow?

Thank you.

---

### Post by slimdog360 on 2006-09-14
Im using kde and Im assuming your using gnome, so the setup is different. You should go into system(up the top)-->add printer-->then set up your printer that way. While setting it up you should be abe to choose a driver to install. Do it that way.

If your still not sure perhaps you should start a new thread asking how to install a printer driver in gnome.

---

### Post by harerama on 2006-09-14
Good idea. I would follow your advice.

Thanks.

---

### Post by topgi on 2006-09-25
Hello guys,
I installed the ip2200 driver from canon using alien for the conversion from RPM to DEB but doesn't work. I got the Ip2200 in th e list, but when I try to print, the file is not even in the queque.

Any clue ? Somebody manage to make them work ?

---

