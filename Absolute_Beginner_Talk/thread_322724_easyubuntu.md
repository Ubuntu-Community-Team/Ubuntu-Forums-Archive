---
title: "easyubuntu"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by cbiscuit on 2006-12-20
Hello, I am trying to install easyubuntu.  starting from >applications>system tools>
after I select what I want to install and click okay in the easy ubuntu box, I get the following error messages.  Is there someone who can tell me how to fix this?

Error message #1

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.bz2:](http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.bz2:](http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

Error message #2
The following problems were found on your system:
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Error message #3
The following problems were found on your system:
W: Duplicate sources.list entry [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages (/var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_dapper_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages (/var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_dapper_non-free_binary-i386_Packages)

Error message #4
Could not apply changes!
Fix broken packages first.

Thanks!

---

### Post by K.Mandla on 2006-12-20
You seem to be connecting to Medibuntu repositories. Is that correct? Are you using Medibuntu?

---

### Post by cbiscuit on 2006-12-20
i am using ubuntu 6.06 dapper drake.  i do not know what medibuntu is.  I keep hearing that easyubuntu is so easy to install but i'm no having any luck at all.  
I also tried to install several other things such as the debian menu but i have no idea where the programs go once i install them from the synaptic manager.  its like they disappear and i dont' know where to find them or how to use them.

Thanks
CNG

---

### Post by Sef on 2006-12-21
> i am using ubuntu 6.06 dapper drake. i do not know what medibuntu is. I keep hearing that easyubuntu is so easy to install but i'm no having any luck at all.
I also tried to install several other things such as the debian menu but i have no idea where the programs go once i install them from the synaptic manager. its like they disappear and i dont' know where to find them or how to use them.


1) [EasyUbuntu Home Page]("http://easyubuntu.freecontrib.org/")

2) What are you trying to download?

3) Have you added [universe and multiverse repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")?

4) EasyUbuntu is located in the medibuntu repository.

5) What programs were you installing?  In general, look under the Applications menu.

---

### Post by randiroo76073 on 2006-12-21
I think that for your purposes Synaptic should give you what you want. Main menu-System-Administration, try that :)
If you try to install any KDE apps you need to install KDE base first or you'll be missing dependencies.  Sometimes you have to use "Alacarte Menu Editor" to enable apps in menu.  If it's not there then it probably didn't install properly.

---

