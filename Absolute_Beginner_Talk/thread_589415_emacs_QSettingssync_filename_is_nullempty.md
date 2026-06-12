---
title: "emacs QSettings::sync: filename is null/empty"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by barna on 2007-10-24
Hi,
I surely did not expect that afer upgradingn t Gutsy, I will have problems editing files.
If I try to open a file in emacs from the shell, saying:

emacs filename.txt

where filename.txt is an EXISTING file, then I get the error message 
QSettings::sync: filename is null/empty
and an empty file is displayed in emacs. What the hell is this? Does anybody have an idea?
Thanks
Daniel

ps: I tried the same with kate, it issues the same error messages (7 times), but it opens the file at least.
Once I manage to fix my problems, I think I will never upgrade/update anything anymore, since it always introduces more problems than what it solves.

---

### Post by realvz on 2007-10-24
This happens because QSettings cannot open the settings file.

The problem can be that the settings file is not present in any of the locations searched, or that the user does not have the correct permissions to read or write the file.

There is no universally accepted place for storing application settings under Unix. In the examples the settings file will be searched for in the following directories:

    * SYSCONF - the default value is INSTALL/etc/settings
    * /opt/MyCompany/share/etc
    * /opt/MyCompany/share/MyApplication/etc
    * $HOME/.qt

Files are searched as follows:

    * When reading settings, the files are searched in the order shown above, with later settings overriding earlier settings. Files for which the user does not have read permission are ignored.
    * When saving settings QSettings works in the order shown above, writing to the first settings file for which the user has write permission.

Note: INSTALL is the directory where Qt was installed. This can be modified by using the -prefix argument in the configure script.

If you want to put the settings in a particular place in the file system you could do the following:

settings.insertSearchPath( QSettings::Unix, "/opt/MyCompany/share" );

But in practice you may prefer not to use a search path for Unix. For example the following code:

settings.writeEntry( "/MyApplication/geometry/width", width );

will write the "geometry/width" setting to the file: $HOME/.qt/myapplicationrc,

assuming that the application is being run by an ordinary user, i.e. not by root.

[http://trolltech.com/developer/knowledgebase/642/](http://trolltech.com/developer/knowledgebase/642/)

---

