---
title: "Mediatomb Media Server"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by Swanbot on 2009-01-22
Hello I am trying to install Mediatomb to stream media from my computer to my PS3 and I am getting some errors. Was just hoping some more informed eyes might know what is going on here. I am actually running off of OSX but I have Ubuntu on another computer, and the Terminal works the same. Anyway after installing Mediatomb I get this:

--->  Fetching mediatomb
--->  Verifying checksum(s) for mediatomb
--->  Extracting mediatomb
--->  Applying patches to mediatomb
--->  Configuring mediatomb
--->  Building mediatomb
--->  Staging mediatomb into destroot
--->  Installing mediatomb @0.11.0_0+ffmpeg+sqlite3+taglib
******************************************************
* To use UTF-8 filename and metadata on Mac OS X, add:
*   <filesystem-charset>UTF-8-MAC</filesystem-charset>
*   <metadata-charset>UTF-8-MAC</metadata-charset>
* to <import> section of ~/.mediatomb/config.xml.
******************************************************
--->  Activating mediatomb @0.11.0_0+ffmpeg+sqlite3+taglib
--->  Cleaning mediatomb

Now that looks good to me, doesn't seem to be any errors... but when I run Mediatomb in Terminal after that I get:

MediaTomb UPnP Server version 0.11.0 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2009-01-22 17:37:04    INFO: Loading configuration from: /Users/swan/.mediatomb/config.xml
2009-01-22 17:37:04    INFO: Checking configuration...
2009-01-22 17:37:04    INFO: Setting filesystem import charset to UTF-8
2009-01-22 17:37:04    INFO: Setting metadata import charset to UTF-8
2009-01-22 17:37:04    INFO: Setting playlist charset to UTF-8
2009-01-22 17:37:04    INFO: Configuration check succeeded.
2009-01-22 17:37:04   ERROR: Error while accessing sqlite database file (/Users/swan/.mediatomb/mediatomb.db): Permission denied

Any ideas what this error means? How to fix it maybe? Thanks!

---

