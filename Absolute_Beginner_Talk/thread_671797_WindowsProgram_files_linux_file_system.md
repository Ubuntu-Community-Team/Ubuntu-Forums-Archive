---
title: "Windows/Program files linux file system"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by donniezazen on 2008-01-18
I have just installed Ubuntu. And downloading all the softwares i can for which i have unzipped most of files either on desktop or home folder. I want to delete unnecessary installation files but i am not sure if its safe. Can you guys tell me which files are safe to delete and is there any folder like windows system or program file which i should not touch? Can you also explain Linux file system?

Thanks

---

### Post by jleaker01z on 2008-01-18
You can pretty much delete anything in your home folder with no effect on the system.  Generally speaking when you install something it goes into the 'file system' and doesnt depend on the files within your home directory.  There may be a few exceptions to that, but I havent run into one yet in the 8 months or so Ive been using Ubuntu.

---

### Post by thelatinist on 2008-01-18
> **soham_1207 said:**
> I have just installed Ubuntu. And downloading all the softwares i can for which i have unzipped most of files either on desktop or home folder. I want to delete unnecessary installation files but i am not sure if its safe. Can you guys tell me which files are safe to delete and is there any folder like windows system or program file which i should not touch? Can you also explain Linux file system?

Thanks

Why have you been downloading programs and unzipping them?  Nearly all programs you could possibly want or need are in the repositories and can be installed just by using Applications > Add/Remove or Synaptic.  Ubuntu isn't like Windows; it provides you with safe and tested versions of software through its repository system.

---

### Post by PeterJS on 2008-01-18
The first thing to keep in mind is that linux has a real file permission system in place, so if you can delete it with out administrative rights (using sudo), then it wasn't critical in the first palce.

Files in linux are laid out according to the Filesystem Hierarchy Standard, wikipedia has a pretty complete article on it here:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
If you've got time to burn and want to learn more about the layout of files than you ever wanted to know here is the complete standard straight from the authors.
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

What software did you install that you had to manually download and extracted? Most everything you'd ever need should be in the repositories and installable with one of the apt tools (apt-get, aptitude, Synaptic, Add/Remove programs).

---

### Post by ryanVickers on 2008-01-18
I agree - anything that you can delete without using root is probably not important.  All the software you'll ever need (with the exception of maybe 2 or 3 apps) is in the repositories.

---

### Post by bwtranch on 2008-01-18
Pretty much agree with the above posts. Why are you un-zipping? You can do that when you need to...

But, anyway, you can do whatever you want. I would suggest that you get to know your terminal, console, whatever you want to call it and type

sudo apt-get update
sudo apt-get upgrade

/ is root
ls lists the contents of a dir
cd changes the dir

So, for example:

jim@jim-desktop:~$ cd /
jim@jim-desktop:/$ ls
bin                                  home            mnt   tmp
boot                                 initrd          opt   usr
cdrom                                initrd.img      proc  var
cupswrapperdcp1000_1.0.2-1_i386.deb  initrd.img.old  root  vmlinuz
cupswrapperDCP1000-1.0.2-1.i386.rpm  lib             sbin  vmlinuz.old
dev                                  lost+found      srv
etc                                  media           sys
jim@jim-desktop:/$ cd home
jim@jim-desktop:/home$ ls
EnergyPlusV210  jim  SetEPlusV210023-lin.exe
jim@jim-desktop:/home$ sudo su
[sudo] password for jim:
root@jim-desktop:/home# exit
exit
jim@jim-desktop:/home$ 

The sudo su made me root. This is something that you should be very careful with. sudo la la to do da day is one thing, but sudo su  means you remain absolute root. I find it useful to be root absolute for a session, but, if you don't know what you are doing you can compromise your system and possibly create a security risk.

Unix is a command based structure that was developed by the military for security. It inherently has safeguards built in. In short, get to know your filesystem and you will be the master of your own system and not owing to someone else.

---

### Post by ryanVickers on 2008-01-19
> **PeterJS said:**
> The first thing to keep in mind is that linux has a real file permission system in place, so if you can delete it with out administrative rights (using sudo), then it wasn't critical in the first palce.

Files in linux are laid out according to the Filesystem Hierarchy Standard, wikipedia has a pretty complete article on it here:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
If you've got time to burn and want to learn more about the layout of files than you ever wanted to know here is the complete standard straight from the authors.
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

What software did you install that you had to manually download and extracted? Most everything you'd ever need should be in the repositories and installable with one of the apt tools (apt-get, aptitude, Synaptic, Add/Remove programs).

wow I have too much time on my hands - I just read that second link completely from start to finish :D

---

