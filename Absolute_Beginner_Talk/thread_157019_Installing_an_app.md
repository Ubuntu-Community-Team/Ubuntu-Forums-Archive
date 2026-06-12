---
title: "Installing an app"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by DavidFourer on 2006-04-08
Questions about how to properly intalling an application.

I wanted the current version of Mozilla-Thunderbird mail.  I removed the existing build using System>administration>add applications.  The version in Synaptic Package Mgr, with all depositories enabled, seemed older than the one on the tbird web site.  I downloaded thunderbird-1.5.tar.zip (which actually produced a file called thunderbird-2.5.tar.zip).  I decompressed this, which created a thunderbird folder with an executable and many other files (I assume the icon with gears is my executable).  I want to put this folder where it belongs in my file organization.  /usr/bin/thunderbird looks like a reasonable place, but I don't seem to have permission to put it there.  I can't find any instructions with the download or on the tbird web site about "installing" for linux.  I also want to have an icon to launch this when I'm done.  

I looked at ubuntu wiki site, which is usually very helpful.  It seems that the really basic stuff is where I get into trouble.  Yes, I'm the guy who spent hours trying to find the hidden mail files in my home directory!

Please advise.

---

### Post by 5-HT on 2006-04-08
Haven't installed Thunderbird from Mozilla's binaries myself.
I'd suggest putting the whole directory into /opt just so it doesn't get mixed up.
About not having write permissions to /usr/bin, you need to escalate your privileges using 'sudo' to write outside your home directory.

What I'd do would be:

1. Copy Thunderbird directory into /opt
```
 sudo mv <thunderbird directory> /opt/ 
``` 
2. Make a symbolic link in /usr/bin pointing to the thunderbird directory
```
 sudo ln -s <path to thunderbird executable> /usr/bin/thunderbird 
``` 
3. Make a desktop shortcut to Thunderbird:
Right click on menu > create launcher > enter "thunderbird" for the command.

*Note: the way I've done this, you should also be able to start it by just entering 'thunderbird' in a terminal.

Hope this helps.

---

### Post by Stone123 on 2006-04-08
rambo3@ubuntu:~$ apt-cache policy mozilla-thunderbird
mozilla-thunderbird:
  Installerad: (none)
  Kandidat: 1.5-0ubuntu6
  Versionstabell:
     1.5-0ubuntu6 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
So there is 1.5 in dapper, i dont know about breezy.
First search reposotories, then backports multi and universe. If nothing there try dapper one that is allready built. 
[http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5-0ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5-0ubuntu6_i386.deb)

---

### Post by DavidFourer on 2006-04-08
Can we look at this a little closer?  

I went into sys>admin>Synaptic p m
I made sure backports multi, universe are checked
I searched globally for "Thunderbird"
I came up with version 1.07 ubuntu build--don't really know if that is different from v. 1.5 regular build.  

I don't understand the difference between dapper and breezy.  However,
you found this link:
[COLOR="Blue"][COLOR="Red"]http://archive.ubuntu.com/ubuntu/poo...untu6_i386.deb[/COLOR][/COLOR]
which leads to a download of:
[COLOR="Red"]mzla-tbird_1.5-Oubuntu6_i386.deb[/COLOR]
and a dialog box that suggests I open with:
[COLOR="Red"]/usr/lib/mime/debian-view (default)[/COLOR]
or save to disk.
I see that "debian-view" is an executable file.  I looked for it under [COLOR="DarkRed"]sys>help>manual pages>[applications,config files,overviews,sys admin][/COLOR]
Not finding it, I looked in ubuntu-wiki and I googled it, but didn't find it. (can that be???)
I'm guessing it installs a package (properly) but can you tell me?

As it happens, I read the previous post and downloaded tbird for linux from the tbird web site.  I decompressed it in [COLOR="DarkRed"]/opt/[/COLOR].  I created a symbolic link and a shortcut, imported my mail and address book, and it seems to work fine.  Could I have a reason to go to the trouble to redo this using  the .deb file and debian-view?

On my installation of ubuntu 5.10 for PC,the line:
[COLOR="Blue"]david@davidf:~$ apt-cache policy mozilla-thunderbird[/COLOR]
gets    (apt-cache -h gets some info on this)
[COLOR="Blue"]mozilla-thunderbird:
  Installed: (none)
  Candidate: 1.0.7-0ubuntu05.10
  Version table:
     1.0.7-0ubuntu05.10 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
        100 /var/lib/dpkg/status
     1.0.7-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages[/COLOR]

Does anyone care to provide some more insight into what this is all about?  Some reccomendations?

---

### Post by 5-HT on 2006-04-08
[quote=DavidFourer]Can we look at this a little closer?

I don't understand the difference between dapper and breezy....

...As it happens, I read the previous post and downloaded tbird for linux from the tbird web site. I decompressed it in /opt/. I created a symbolic link and a shortcut, imported my mail and address book, and it seems to work fine. Could I have a reason to go to the trouble to redo this using the .deb file and debian-view?...

...Does anyone care to provide some more insight into what this is all about? Some reccomendations?[/quote] 
Glad you got it working from the binary provided on Mozilla's site.

As to your other questions, Dapper will be the next release of Ubuntu (slated for June). Currently, it is still in development, though it is available for download.

Every Ubuntu release goes through an application freeze just prior to release. This means that what ever applications are included at the time of the freeze will not be updated to newer versions at a later time (only security updates are available). Because of this, Breezy has thunderbird 1.0.7 included whereas 1.5 is available for Dapper.

When you followed the link provided by Stone123, it was the link to packages available in Dapper. That's why 1.5 was available, but only 1.0.7 was found when you searched apt (using your Breezy repositories).

Unfortunately, you cannot just install the .deb of Thunderbird 1.5 from the Dapper repositories and install it. You will not have the necessary dependencies as they too have been updated since Breezy (trying to install them all will most likely only break your system).

The method I provided is a good one as it lets you run Thunderbird on Breezy (in fact, it is the only way to get FireFox 1.5 working in Breezy). The only problem is that it is not system-wide, and cannot be updated through apt. This is not an issue as 1) you now have a shortcut for it 2) you can always set it as your preferred mail client (somewhere in the menu there should be an option for this. Just put "thunderbird" if you really want 3) Thunderbird has it's own update feature.

A little more about Thunderbird's updater: you will need to run the program as root. You can do this by typing 'gksudo thunderbird' in a terminal. Be careful though to NOT send/receive/read any mail while operating as root, just update and close.The good thing though is that by typing 'gksudo thunderbird', it will use root's profile, so you won't have an account set up for it (your account will be under the profile of your user).

The reason not to do anything apart from updating as root is that the program then has unlimited access to the system (which is necessary while updating if files need to get edited). So if you were to open an email attachment that happened to be a rootkit (very unlikely), it would have free reign only if you were running Thunderbird as root.

As an aside: if you want to install a .deb, you can simply type: ```
 dpkg -i <path to .deb> 
```

---

