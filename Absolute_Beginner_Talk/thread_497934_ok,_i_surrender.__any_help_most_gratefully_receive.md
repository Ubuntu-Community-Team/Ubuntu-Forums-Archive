---
title: "ok, i surrender.  any help most gratefully received!!"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-07-10
(hey, i like the thing that matches the title of your new thread to other potential ones .. sweet :))

right, what i'm doing is this.

I'm currently running version 7.04 of ubuntu in VMWare on a Windows XP system.  My XP setup is 160gb hard drive, 1gb Ram.

I'm playing around with it with a view to installing it as my main operating system, but the deal breaker for me will be wether or not I can install and run Informix Dynamic server.

So I downloaded the Linux version from the IIUG website (totally legal, just in case ..) and unzipped the necessary files.

I set up a shared folder on my XP system and copied the Informix files there, and then, on ubuntu, I set up a connection to a winshare folder, entered the IP address for the connection and copied the files across with no problems.

Due to space issues, i'm assuming because it's a virtual machine, I had to do a little bit of jiggery pokery with the main installation shell script and place some of the CPIO files on other disks, but it all worked and went through the installation procedure no problem.

Then, I get to the final part where it has to install and brand the directories and I get this error ..

"/etc/brand: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: no such file or directory"

now, since i'd encountered a similar error on fedora, i knew there must be an equivalent command to "yum", so i googled around and found the following possible fix ..

"sudo apt-get install libstdc++2.10-glibc2.2"

I ran the command, and got this ..

"Reading package lists... Done"
"Building dependency tree"
"Reading state information... Done"
"E: couldn't find package libstdc++2.10-glibc2.2"

And that did it for me.   I've been grappling with this for 2 days now, working it out as I go along, but there just came a point where my enthusiasm had been chipped away enough that I had to ask for help :)

I'm obviously missing the libstdc++ libraries, i can assume, so if this is the case, is there a way of uploading them ?.

Or am I generally on a hiding to nothing since i'm running it in a VMWare setup ?

Any help would be most gratefully received.  Thankyou !!

---

### Post by Moop on 2007-07-10
Does Synaptic Package Manager work when running Feisty as a guest? I'm not to familiar with virtual machines. It's just one package and it's available on my list in Synaptic. If it's not in yours then it's just a matter of adding the source.

---

### Post by glennric on 2007-07-10
Try installing libstdc++2.10-glibc2.2
Type
```
sudo apt-get install libstdc++2.10-glibc2.2
```

Duh, that is what you did.  You must need to enable the correct repository.  I believe it is in the universe repository.
Add the line
```
deb http://us.archive.ubuntu.com/ubuntu feisty universe
```
to the file /etc/apt/sources.list.  Then type
```
sudo apt-get update
```
Then try to install libstdc++

---

### Post by jasonwatkins on 2007-07-12
thanks again for the help

i started getting errors regarding the GLIB_C libraries (if that's the correct name) so I actually though i'd give fedora one more try.

through a slice of luck and a few late nights googling my **** off, i actually found the correct libc++ library i needed and how to install it.  

i then had to take a giant crash course in database administration, and the upshot of everything is, that i managed to get informix dynamic server version 10 installed and running !

but i still like ubuntu .. honest .. :):)

---

