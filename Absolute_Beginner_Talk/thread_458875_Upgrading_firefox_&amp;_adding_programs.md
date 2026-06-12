---
title: "Upgrading firefox &amp; adding programs"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by grj23 on 2007-05-30
Hi

I'm very new to Ubuntu.  I need to upgrade my firefox from 2.0 to 2.0.0.3.  I've downloaded the files, but how do I install them?

Also, when I run Add/Remove... (applications) I get an error about missing repositories, and I'm unable to install anything.

It says:
"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

and lists the following indexes:
"http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz: 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) 403 Forbidden
[http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:) 403 Forbidden
"

---

### Post by Kobalt on 2007-05-30
To simmply install the latest Mozilla programs available (Firefox 2.0.0.3 and others if you want) check out [UbuntuZilla]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla").
About your other problem, could you please post your sources.list file ```
cat /etc/apt/sources.list
```

---

### Post by grj23 on 2007-05-30
So I tried Ubuntzilla, but again came up against the repository problem.

I'm not exactly sure about the request you had for me, but I opened a terminal and ran the line you gave and it gave:
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Thanks

---

### Post by grj23 on 2007-05-30
This is what the ubuntuzilla gave:
Updating repositories list

Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_GB
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_GB              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_GB             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_GB               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release                     
Errhttp://security.ubuntu.com edgy-security/main Packages
  403 Forbidden
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages 
Errhttp://security.ubuntu.com edgy-security/restricted Packages
  403 Forbidden
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages
Errhttp://security.ubuntu.com edgy-security/main Sources
  403 Forbidden
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources  
Errhttp://security.ubuntu.com edgy-security/restricted Sources
  403 Forbidden
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources
Errhttp://security.ubuntu.com edgy-security/universe Packages
  403 Forbidden
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages
Errhttp://gb.archive.ubuntu.com edgy/main Packages
  403 Forbidden
Errhttp://gb.archive.ubuntu.com edgy/restricted Packages
  403 Forbidden
Errhttp://gb.archive.ubuntu.com edgy/main Sources
  403 Forbidden
Errhttp://gb.archive.ubuntu.com edgy/restricted Sources
  403 Forbidden
Errhttp://gb.archive.ubuntu.com edgy/universe Packages
  403 Forbidden
Errhttp://gb.archive.ubuntu.com edgy-updates/main Packages
  403 Forbidden
Errhttp://gb.archive.ubuntu.com edgy-updates/restricted Packages
  403 Forbidden
Errhttp://gb.archive.ubuntu.com edgy-updates/main Sources
  403 Forbidden
Errhttp://gb.archive.ubuntu.com edgy-updates/restricted Sources
  403 Forbidden
Errhttp://gb.archive.ubuntu.com edgy-updates/universe Packages
  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz)  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

My firefox did not update after this.
Thanks

G

---

### Post by jwh400 on 2007-05-31
This is the script you need from ubuntuzilla;

**Install Official Mozilla Build of Firefox**

 The [Ubuntuzilla Firefox script]("http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543") will automatically download and install the newest Firefox for you. It is also able to undo what it has done, and uninstall the Mozilla build of Firefox. 
Here are the steps to use this script to install the Mozilla build of Firefox:[LIST]
[*] Download [installnewfirefox.sh]("http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543"), and save it as *installnewfirefox.sh* to your desktop
[*] Open a terminal ([how?]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#Where_is_this_.22terminal.22_everyone_keeps_talking_about.3F"))
[*] Enter this command to run the script (copy and paste this exactly to avoid typos):[/LIST]bash ~/Desktop/installnewfirefox.sh -install
And, if no errors occur, your new Firefox is ready for use! 

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox)





The script that you download will be named "installnewfirefox_3.2.0.sh" but I had to rename it to "installnewfirefox.sh" before it would work. I just ran this on both the desktop and laptop and it worked wonderfully. 

Thanks for the link Kobalt.:D

---

### Post by aysiu on 2007-05-31
[This should help for your 403 forbidden message](http://ubuntuforums.org/showthread.php?p=1209484#post1209484)

---

### Post by kittyhawk63 on 2007-05-31
You need to "uncomment" the debs via Terminal.
**Applications**->**Accessories**->**Terminal**
Copy and paste the following:
[B]gksudo gedit /etc/apt/sources.list
[/B]It will ask for your password. You will see nothing while typing. just hit >enter? after typing your password. Now, wait. A new page will appear. You need to remove (delete) the **# **before each line that has "**deb**"

Example: These have the **# **
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

Removed #:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

Now, SAVE and exit.

---

