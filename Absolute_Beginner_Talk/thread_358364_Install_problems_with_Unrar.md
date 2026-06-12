---
title: "Install problems with Unrar"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by ZeroXR on 2007-02-10
I have been trying to install Unrar and it's been stumping me with the following dialog...

```
zeroxr@ZeroXR-Linux:~$ cd Desktop
zeroxr@ZeroXR-Linux:~/Desktop$ rm unrarsrc.tgz
zeroxr@ZeroXR-Linux:~/Desktop$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Hit http://us.archive.ubuntu.com edgy Release  
Hit http://us.archive.ubuntu.com edgy-updates Release               
Hit http://security.ubuntu.com edgy-security/main Packages          
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
zeroxr@ZeroXR-Linux:~/Desktop$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[b]Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate[/b]

```

What am I doing wrong? I can't unrar anything with Archive Manager or XArchive... Can someone shed some light here? I just made the jump about 6 hours ago from Windows XP and I have searched extensively for solutions.

---

### Post by Maestro23 on 2007-02-10
You need to enable some extra repositories. This thread will help you with rar/unrar: [http://www.ubuntuforums.org/showthread.php?t=358030&highlight=rar](http://www.ubuntuforums.org/showthread.php?t=358030&highlight=rar)

---

### Post by jordanmthomas on 2007-02-10
Do you need to be able to create rar archives or just open them?
If you just need to unrar
```
sudo apt-get install unrar
```
should do you nicely.  Otherwise I believe you need to get rar from rarlabs themselves.

---

### Post by ZeroXR on 2007-02-11
> **Maestro23 said:**
> You need to enable some extra repositories. This thread will help you with rar/unrar: [http://www.ubuntuforums.org/showthread.php?t=358030&highlight=rar](http://www.ubuntuforums.org/showthread.php?t=358030&highlight=rar)

Actually, your solution was right on the dot! My thanks for the help! That was actually the thing that was blocking me from installing Unrar.

After that, Jordan's command worked nicely!

I think I am beginning to love my conversion from XP already! :biggrin:

---

### Post by Maestro23 on 2007-02-11
> **ZeroXR said:**
> Actually, your solution was right on the dot! My thanks for the help! That was actually the thing that was blocking me from installing Unrar.

After that, Jordan's command worked nicely!

I think I am beginning to love my conversion from XP already! :biggrin:

Good deal man, glad it helped.  This community is by far the best that I have seen for a distro when it comes to helping people.  One of the many reasons I plan to use Ubuntu for a long time.:)

---

