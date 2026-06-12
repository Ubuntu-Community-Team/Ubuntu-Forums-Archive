---
title: "None of the Package/Update Managers working"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by abben on 2007-05-07
Whether it's Update Manager, Add/Remove, Synaptic, they all crash.

My error message:

```
abben@abben-desktop:~$ sudo apt-get install kdissert
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing nautilus-cd-burner (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

Thanks in advance. This particularly sucks because I have re-installed ubuntu (6.10) from a disk that came with my "Ubuntu Bible" handbook i've had for a while, and have not been able to get an install that avoids package manager problems.

---

### Post by justin whitaker on 2007-05-07
Did you try firing up a terminal, typing in autoclean, the apt-get update? (You may need a sudo in there somewhere).

---

### Post by abben on 2007-05-07
Unfortunately those commands only give me the same error!

```
abben@abben-desktop:~$ **sudo apt-get update**
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US     
Hit http://security.ubuntu.com edgy-security Release                          
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://us.archive.ubuntu.com edgy Release  
Hit http://security.ubuntu.com edgy-security/restricted Packages    
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates Release
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
[B]Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing nautilus-cd-burner (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.[/B]
abben@abben-desktop:~$ **sudo apt-get autoclean**
[B]Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing nautilus-cd-burner (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.[/B]
```

thanks for the suggestion though. I like Ubuntu and for a long stretch it was awesome, it's only with this recent re-install that all kinds of nonsense is happening. Any way I can get around these errors and get my package managers working again?

---

### Post by abben on 2007-05-07
any other thoughts?

---

### Post by christhemonkey on 2007-05-07
Delete the file /var/lib/dpkg/status ? Then try apt-get update and apt-get upgrade?

Thats all i can think, you seem to have a broken apt database....
EDIT: See this thread:
[http://ubuntuforums.org/showthread.php?t=114504](http://ubuntuforums.org/showthread.php?t=114504)

---

### Post by abben on 2007-05-07
> **christhemonkey said:**
> Delete the file /var/lib/dpkg/status ? Then try apt-get update and apt-get upgrade?

Thats all i can think, you seem to have a broken apt database....
EDIT: See this thread:
[http://ubuntuforums.org/showthread.php?t=114504](http://ubuntuforums.org/showthread.php?t=114504)

thanks! for the moment, the package managers are looking good. I do try to look around the forums for my answer, but there are thousands of posts etc. etc. and sometimes it is tough to find the answer even if it is right there on the board.

I appreciate it and only wish I had the means and luxury of being able to repay all the awesome help this community offers. But just the same... the fact that it is free is what allows me to use it.

I'll save that for a thesis or something, anyway, thanks much for the help, honestly.

---

