---
title: "[SOLVED] Install Menu Items"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by measekite on 2007-10-18
Hi

I know this has been asked before but I would appreciate an updated detailed step by step answer for the current version of Thunderbird 2.x that is up to date for October 2007 for users running Feisty.

i downloaded Thunderbird 2.x from the official Mozilla site (the repository only offers 1.5) and i want to install it, after untarring, there is no install file (ie setup.exe in windows), providing for the installation and subsequent installation of links, icons and menu entries.how to install it and make shortcuts and icons ???

I would also like to update Firefox in the same manner.  It seems that the version of Firefox that gets installed will not allow you to update from the Firefox menu.


Thanks in advance.

---

### Post by constrictor on 2007-10-18
The tar ball contains an executable file called firefox. On right clicking on this you should come up with it's properties, click on the permissions tab and make sure that "Allow exectution of this program" checkbox is selected. And just double click that and you should have firefox running. In other words there is no installer it just runs by itself. But i think the firefox upgrade to the fiesty version should come with the entire OS upgrade...

---

### Post by measekite on 2007-10-18
> **constrictor said:**
> The tar ball contains an executable file called firefox. On right clicking on this you should come up with it's properties, click on the permissions tab and make sure that "Allow exectution of this program" checkbox is selected. And just double click that and you should have firefox running. In other words there is no installer it just runs by itself. But i think the firefox upgrade to the fiesty version should come with the entire OS upgrade...

What abut thunderbird.  Where do I find the file to rt click.  Is it in the tar file?  And then how do I get it into the menu system?

---

### Post by stchman on 2007-10-18
> **measekite said:**
> Hi

I know this has been asked before but I would appreciate an updated detailed step by step answer for the current version of Thunderbird 2.x that is up to date for October 2007 for users running Feisty.

i downloaded Thunderbird 2.x from the official Mozilla site (the repository only offers 1.5) and i want to install it, after untarring, there is no install file (ie setup.exe in windows), providing for the installation and subsequent installation of links, icons and menu entries.how to install it and make shortcuts and icons ???

I would also like to update Firefox in the same manner.  It seems that the version of Firefox that gets installed will not allow you to update from the Firefox menu.


Thanks in advance.


The .tar.gz is a pre-compiled binary.

I have a script that installs TBird 2.0.0.6 on your Feisty system.  It also creates a menu item as well.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

[http://www.stchman.com/tools/thunderbird/thunderbird_install.sh](http://www.stchman.com/tools/thunderbird/thunderbird_install.sh)

Be sure to make the script executable.

You do not need to update Firefox as the latest version for Linux is there.  2.0.0.7 is a Windows only update and has no impact to Linux.

---

### Post by measekite on 2007-10-19
> **stchman said:**
> The .tar.gz is a pre-compiled binary.

I have a script that installs TBird 2.0.0.6 on your Feisty system.  It also creates a menu item as well.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

[http://www.stchman.com/tools/thunderbird/thunderbird_install.sh](http://www.stchman.com/tools/thunderbird/thunderbird_install.sh)

Be sure to make the script executable.

You do not need to update Firefox as the latest version for Linux is there.  2.0.0.7 is a Windows only update and has no impact to Linux.

I downloaded the script.  I placed it in /home/scripts.  Tbird is in some other folder.  Does the script need to be in the same folder as Tbird or do I give the script the path?

---

### Post by measekite on 2007-10-20
> **measekite said:**
> I downloaded the script.  I placed it in /home/scripts.  Tbird is in some other folder.  Does the script need to be in the same folder as Tbird or do I give the script the path?

I am not sure that I ran the script properly and I do not know the details on running  a script with 755.  Here is what I did and what happened.

[COLOR=Red]**Where do I go from here?**[/COLOR]
```

root@mypc:/~# cd communication/download/scripts
root@mypc:/~/communication/download/scripts# sh thunderbird_install.sh
--21:49:47--  http://www.stchman.com/tools/thunderbird-2.0.0.6.tar.gz
           => `thunderbird-2.0.0.6.tar.gz'
Resolving www.stchman.com... 209.205.39.25
Connecting to www.stchman.com|209.205.39.25|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:49:48 ERROR 404: Not Found.

tar: /root/thunderbird-*: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

---

### Post by measekite on 2007-10-20
> **measekite said:**
> I am not sure that I ran the script properly and I do not know the details on running  a script with 755.  Here is what I did and what happened.

[COLOR=Red]**Where do I go from here?**[/COLOR]
```

root@mypc:/~# cd communication/download/scripts
root@mypc:/~/communication/download/scripts# sh thunderbird_install.sh
--21:49:47-- [COLOR=Red] http://www.stchman.com/tools/thunderbird-2.0.0.6.tar.gz[/COLOR]
           => `thunderbird-2.0.0.6.tar.gz'
Resolving www.stchman.com... 209.205.39.25
Connecting to www.stchman.com|209.205.39.25|:80... connected.
HTTP request sent, awaiting response...[COLOR=Red] 404 Not Found[/COLOR]
21:49:48 ERROR 404: Not Found.

tar: /root/thunderbird-*: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

I changed this
```

wget http://www.stchman.com/tools/thunderbird-2.0.0.6.tar.gz
```[COLOR=Red]**TO THIS**[/COLOR]

```
wget http://www.stchman.com/tools/thunderbird/thunderbird-2.0.0.6.tar.gz
```A menu item was created and I was able to invoke Thunderbird.  I will now configure and test it.

[COLOR=Red]** One thing I do not understand.  The menu item for Update is grayed out.  It just so happens that the equivalent item in Firefox "update" is also grayed out.  In Windows these are available.  Does anybody know why.**[/COLOR]

---

