---
title: "Beryl installation woes on intel 915 gm"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by hyby on 2006-10-13
Hello, i have tried to install Bery XGL/Compiz from the Bery wiki installation guide. However, i have been unsucessful in gettingthe fancy thing to work. I was wondering has anyone managed to get it to work on an Intel 915 gm onboard videocard?

Also, during the downloading of the files from the repositories, i got this error;
```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) deb Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Get:5 [http://media.blutkind.org](http://media.blutkind.org) dapper Release.gpg [189B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://media.blutkind.org](http://media.blutkind.org) dapper Release
Err [http://media.blutkind.org](http://media.blutkind.org) dapper Release

Get:6 [http://media.blutkind.org](http://media.blutkind.org) dapper Release [5402B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper/main Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) deb Release
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper/aiglx Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:7 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release [5402B]
Hit [http://media.blutkind.org](http://media.blutkind.org) dapper/main Packages
Hit [http://media.blutkind.org](http://media.blutkind.org) dapper/aiglx Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) deb/http://media.blutkind.org/xgl/ Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) deb/dapper Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) deb/main Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) deb/aiglx Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/aiglx Packages
Err [http://www.beerorkid.com](http://www.beerorkid.com) deb/http://media.blutkind.org/xgl/ Packages
  404 Not Found
Err [http://www.beerorkid.com](http://www.beerorkid.com) deb/dapper Packages
  404 Not Found
Err [http://www.beerorkid.com](http://www.beerorkid.com) deb/main Packages
  404 Not Found
Err [http://www.beerorkid.com](http://www.beerorkid.com) deb/aiglx Packages
  404 Not Found
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/aiglx Packages
Fetched 11.2kB in 15s (711B/s)
Reading package lists... Done
W: GPG error: [http://media.blutkind.org](http://media.blutkind.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems
hyby@hyby:~$
```

then when i run 
sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes

my update asks to reupdate some of the files, so i press ok. I then introduce the xgl link to the serssion manager thingy, and select when i reboot.

When i enter ubuntu desktop there is the red emerald, and when i open programs it is extremely slow, and i can not get the cube to function

---

### Post by nik on 2006-10-13
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -

to add the key from beerorkid. You also need to add some stuff to xorg.conf and make a new session to run aiglx. Head over to the beryl forums and wiki to find out how :)

Also, yes, it works fine :)

---

### Post by jordanmthomas on 2006-10-13
Works brilliantly on an i915, I might add.

...except water.  It stopped working, but it's not that useful anyway.

---

### Post by hyby on 2006-10-13
Thanks guys, i actually followed the wiki instructions... but sort of had problems.

Does it lag when you run the program?

---

### Post by jordanmthomas on 2006-10-14
Turn off the blur plugin.  It's faster than it used to be, but it's still much faster without it.

---

### Post by hyby on 2006-10-14
Thanks guys it doesnt work...when itype the wget line do i also type the sudo get in the same line?

aslso when i go for update it says that the link is dead

---

### Post by foureight84 on 2006-10-26
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

---

