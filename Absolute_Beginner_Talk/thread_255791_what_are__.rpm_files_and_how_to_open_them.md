---
title: "what are  *.rpm files and how to open them??"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2006-09-12
To install certion software I downloaded *.rpm files

but I'm having difficulty opening them and installing the program. i tried GDebi package installer but it doesn't work( it says file corrupted or I might not have permission). I downloaded the file three times, so I don't think it's corrupted and checked  all permissions in properties of the file.

is there anyother package installer I can use, or what is the command line prompt??


thanks

maneesh

---

### Post by Najand on 2006-09-12
RPMs are special packages for Red Hat Linux as well as other RedHat base distrobutions like SUSE, Mandriva, Fedora, et cetra.
We are using a different style of Packages... DEB which are the default packages for Debian Linux and other debian based linux distributions like ubuntu. I don't recommand you to use rpm packages unless there is no deb package available, What package do you want to install?

---

### Post by Perfect Storm on 2006-09-12
.rpm are packages for distros like redhat, fedora and mandriva. Ubuntu/Debian are using .deb packages.

It is though possible to convert the .rpm to .deb but you're better off to
1. use the package manager (saver and easier)
2. searching for .deb
3. Use the source code.

You can do 
```
sudo aptitude install alien
cd /destination
sudo alien -i XXXXXXXXX.rpm
```

Which application is it?

---

### Post by woody_green on 2006-09-12
You can't open nor install RPM files in Ubuntu unless you have the alien and rpm packages installed. Do those files have DEB versions? Then, by all means, choose them. If not, then you have to convert them.

---

### Post by maneesh77 on 2006-09-12
Confession: it's Limewire I want to install. I know amule and gnutella are better( and I have been using amule) , but this is just a little vanity from a ex windows limewire user ;-)

the lime wire says I need to install the runlime.sh file from my bin folder

but I don't have permission to copy anything into it. it says I'm not the owner

"If you are using this from the LimeWireOther.zip file, you can launch

LimeWire by typing:



    sh ./runLime.sh"

that's what the txt file help says.

I tried running it in terminal but the *.sh file needs to be in the bin. How can I copy t there??, or otherwise install limewire.

"#!/bin/sh
#
# Runs LimeWire.  This script must be executed in your LimeWire
# install directory.

# this should allow starting limewire from
# gui-based explorer interfaces
cd "`dirname "$0"`"
"

---

### Post by Najand on 2006-09-12
I am not really into p2p softwares...  But if all you want is the permission try using "sudo sh /.runLime.sh" and then enter your password.

---

### Post by maneesh77 on 2006-09-12
I extracted limewire in my homefolder (the runlime.sh file is in it. when I run the command  sudo sh /.runLime.sh it says no such file or directory

---

### Post by Najand on 2006-09-12
Sorry, I mistyped... 
Use
```

sudo sh ./runLime.sh

```

---

### Post by maneesh77 on 2006-09-12
still the same result no file or directory found. 

Do I need to transfer the runlime.sh file to some other folder??

this is what happens 

maneesh@maneesh-desktop:~$ sudo sh ./runLime.sh
Password:
sh: ./runLime.sh: No such file or directory
maneesh@maneesh-desktop:~$

I feel like i need to direct it to the folder where I placed limewire. but how??

---

### Post by Najand on 2006-09-12
Is runLime.sh in your home directory or it is in a floder in your home directory?

---

### Post by majesticturkey on 2006-09-12
Use FrostWire if LimeWire has no deb.

FrostWire is a FOSS LimeWire clone that runs on the same network and looks exactly the same. It does have a deb. It's my weapon of choice. Very nice, too. And you don't have to bother with LimeWire Pro.

---

### Post by maneesh77 on 2006-09-12
/home/maneesh/limewire

in a folder in the home directory. I don't have permission to write in the home directory except in the maneesh folder.

---

### Post by Najand on 2006-09-12
Then do
```

sudo sh ./limewire/runLime.sh

```
And if there is some DEB package available using it is very helpful. See the comment above.

---

### Post by maneesh77 on 2006-09-12
/home/maneesh/limewire

that's the location of the runlime.sh file

I don't have permission to copy anything in the home directory . Only in the maneesh folder in the home directory

---

### Post by maneesh77 on 2006-09-12
praise the Lord!!! it works .

thanks 

As for forstwire , i heard it's pretty bad, almost as bad as kazza

---

