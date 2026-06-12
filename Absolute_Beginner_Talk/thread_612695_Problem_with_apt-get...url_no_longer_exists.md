---
title: "Problem with apt-get...url no longer exists"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by babu.csedu5b on 2007-11-14
Hi,
I am using Ubuntu for about 1  year. But I havent tried apt-get before. Today I tried and failed. I got these error msgs:

babu@ubuntu:~$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Actually, the link [http://archive.ubuntu.com/ubuntu/dists/hoary](http://archive.ubuntu.com/ubuntu/dists/hoary) no longer exists.

Can any one help/suggest me to sort out this problem ? 

Regards,
Babu

---

### Post by overdrank on 2007-11-14
> **babu.csedu5b said:**
> Hi,
I am using Ubuntu for about 1  year. But I havent tried apt-get before. Today I tried and failed. I got these error msgs:

babu@ubuntu:~$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Actually, the link [http://archive.ubuntu.com/ubuntu/dists/hoary](http://archive.ubuntu.com/ubuntu/dists/hoary) no longer exists.

Can any one help/suggest me to sort out this problem ? 

Regards,
Babu

Hi and you are testing Hoary you may look here
[http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)

Edit that is what I get for not reading :) Hoary not Hardy

---

### Post by babu.csedu5b on 2007-11-14
> **overdrank said:**
> Hi and you are testing Hoary you may look here
[http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)
Hi,
I went thr but couldnt find soln for the problem i am looking for. 
Actually [http://archive.ubuntu.com/ubuntu/dists/hoary/](http://archive.ubuntu.com/ubuntu/dists/hoary/) doesnt exist now. 
Can anyone tell me whats the new link forubuntu hoary dist?

---

### Post by Caffeine_Junky on 2007-11-14
> **babu.csedu5b said:**
> Hi,
I went thr but couldnt find soln for the problem i am looking for. 
Actually [http://archive.ubuntu.com/ubuntu/dists/hoary/](http://archive.ubuntu.com/ubuntu/dists/hoary/) doesnt exist now. 
Can anyone tell me whats the new link forubuntu hoary dist?

Hey there..

You will need to upgrade to a later version of ubuntu..

Hoary dose not have repositories anymore.

---

