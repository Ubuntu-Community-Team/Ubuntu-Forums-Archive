---
title: "Locale issue"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by saginandkishore on 2007-04-10
Hi All ,

    I have just now installed the ubuntu OS and I was trying to check the perl version installed and I ran into Locale errors. I have already did some searching in google and tried the following steps with no avail.

(1.) export LC_ALL=En_Us

(2.) sudo dpkg-reconfigure locales

(3.) sudo apt-get remove localeconf

But after doing all the above steps I still see the following erros

******************************************************************************************
nandkishore@HomePC:/opt/ActivePerl-5.8/bin$ ./perl -v
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = "En_Us",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

This is perl, v5.8.8 built for i686-linux-thread-multi
(with 30 registered patches, see perl -V for more detail)

Copyright 1987-2006, Larry Wall

Binary build 820 [274679] provided by ActiveState [http://www.ActiveState.com](http://www.ActiveState.com)
Built Jan 22 2007 20:52:36

Perl may be copied only under the terms of either the Artistic License or the
GNU General Public License, which may be found in the Perl 5 source kit.

Complete documentation for Perl, including FAQ lists, should be found on
this system using "man perl" or "perldoc perl".  If you have access to the
Internet, point your browser at [http://www.perl.org/](http://www.perl.org/), the Perl Home Page.

nandkishore@HomePC:/opt/ActivePerl-5.8/bin$
**************************************************************************************

Please let me know what I am missing.

Thanks and Regards
Nand Kishore Sagi

---

### Post by VoodooSteve on 2007-04-11
I'm having the same issue.
Try: ```
sudo apt-get install language-pack-en
```

---

### Post by zvacet on 2007-04-11
[https://help.ubuntu.com/community/LocaleConf]("https://help.ubuntu.com/community/LocaleConf")

---

### Post by avogadro on 2007-04-11
have you guys found a solution? if so can you give feedback as I have a similar problem. Cheers!:guitar:

---

### Post by zvacet on 2007-04-12
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way")

---

