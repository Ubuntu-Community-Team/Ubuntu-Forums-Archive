---
title: "How can I install the &quot;Greek&quot; locales in Ubuntu?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-01-12
Hello!

I have a problem using the program **ntfs-3g**.
It seems that I am NOT able to view Folders/Files whose Filename is using Greek characters.
These files/folders remain hidden when trying to view them by using the program **ntfs-3g**.

According to the **ntfs-3g** site's support, I need to do the following:

> **Why can't I see all file names with national characters?**
or
**Why do I get "Skipping unrepresentable filename (inode XXXXX) ..." messages?**
    The 'locale' mount option isn't set, or it's not correctly set, or the locale you set doesn't exist. When this happens then some file names can't be converted to UTF8, so they won't be visible.

    Solution: Set the correct value using the 'locale' mount option. You can see what locales you have by using the following command:

    locale -a

    If you can't find the preferred setting then you must generate it, however this is fairly distribution dependent. To do so, a package like glibc-i18ndata (openSUSE, Mandriva, ...) or locales (Debian, Ubuntu, ...) must be installed and enter the below command as root to generate for example the Brazilian locale:

    localedef -i pt_BR -f UTF-8 pt_BR.UTF-8

    Then you can use the "locale=pt_BR.UTF-8" option during mount.

    If some of your softwares are not UTF8 ready then they will not show correctly the UTF8 file names. Please consult your distribution documentation about how to enable full UTF8 support.

    Status: Transparent conversion handling is planned. 



According to the above, I need to add my "Greek" characters to Ubuntu's "locale" database.

When I perform a "**locale -a**", I get the following results:

> dimitris@dimitris-desktop:~$ **locale -a**
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

How can I add the "Greek" locale?
Should I perform a:

```
localedef -i pt_GR -f UTF-8 pt_GR.UTF-8
```

Note:
All I do is replace the "BR" (e.g. Brazil) to GR (e.g. Greece), in the above provided example...
Is this the right way to do this?

Thanks.

---

### Post by annda on 2007-01-12
i think it's el_GR that you need to substitute for pt_BR

do you have Modern Greek language packages installed? (System/Administration/Languages)

p.s. i don't understand Greek one bit but maybe you should look here:
[http://www.adslgr.com/forum/showthread.php?t=61604](http://www.adslgr.com/forum/showthread.php?t=61604)
[http://www.adslgr.com/forum/showthread.php?p=820957](http://www.adslgr.com/forum/showthread.php?p=820957)

---

### Post by ciscosurfer on 2007-01-12
> **dvarsam said:**
> Hello!

I have a problem using the program **ntfs-3g**.
It seems that I am NOT able to view Folders/Files whose Filename is using Greek characters.
These files/folders remain hidden when trying to view them by using the program **ntfs-3g**.

According to the **ntfs-3g** site's support, I need to do the following:



According to the above, I need to add my "Greek" characters to Ubuntu's "locale" database.

When I perform a "**locale -a**", I get the following results:



How can I add the "Greek" locale?
Should I perform a:

```
localedef -i pt_GR -f UTF-8 pt_GR.UTF-8
```Note:
All I do is replace the "BR" (e.g. Brazil) to GR (e.g. Greece), in the above provided example...
Is this the right way to do this?

Thanks.Go into a Terminal, and issue the following```
sudo aptitude update && sudo aptitude install language-support-el
```Then to be sure that the locale took, issue the following```
sudo dpkg-reconfigure locales
```If you get stuck, [this link]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way") should help out.

---

