---
title: "VMware uninstall"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-27
I installed VMware awhile back using the tar.gz
When I start it up now it tells me there is an update of the VMware server that i have installed, anyone know how I can uninstall the one i have now?

Unfotunately now when I try to start it up (vmware app.) it tries and then disappears.

I saw that you can get vmware through automatix now and I would like to throw a new vmware onto my sys after i get rid of the old one...

I did a search of the forums but could find nothing regarding those that installed using the tar.gz

Im pretty sure that there was an uninstall script but I dont know where it is on my sys.

---

### Post by dmizer on 2006-09-27
as with most aps that you build from source, there's a file in the tarball somewhere that gives you an uninstall script.

however, i caution against using automatix for this.

try this instead.  open a terminal and type: vmware

when it crashes, it will exit with an error, and it will tell you what's wrong.  post that error here, and we will probably be able to correct your current install.

---

### Post by szf on 2006-09-27
VMWare is a really "deep install."  Best of luck to you, but you may not be able to really ferret it out without a significant time expenditure...

---

### Post by diggity on 2006-09-27
The uninstall script from the tar.gz file is in th bin directory of the extracted files.
Try looking in the directory that you extracted the files into. **vmware-player-distrib/bin**
(that's where mine is). There should be a vmware-uninstall.pl script. sudo that and it should uninstall vmware.

---

### Post by charles.g.moore on 2006-09-27
SZF
I actually found the uninstall script and ran it do you think that it is "gone enough" that it won't interfere with a new install?

DMIZER
are you saying that i shouldnt grab it using automatix and download it from the vmware site instead?  Do you know if the vmware from automatix is the server version or the desktop ver.?

---

### Post by szf on 2006-09-27
> **charles.g.moore said:**
> SZF
I actually found the uninstall script and ran it do you think that it is "gone enough" that it won't interfere with a new install?
I'm speaking more from superstition than from experience. I have VMWare installed on Fedora Core and when I performed a kernel upgrade it all went pear-shaped.

After a night of googling around, I let that nagging "try Ubuntu" idea take root...

Now here I am.

---

### Post by dmizer on 2006-09-28
if you ran the uninstall script, it should be gone.

look around a bit, chances are there's a recent debian package out there somewhere you can use if you don't want to compile it yourself.

furthermore, simply using automatix or using an alternative debian package doesn't mean you won't wind up with the exact same problem.

---

### Post by bluefrog on 2006-09-28
your problem came from a kernel update.

when it happens you need to download the linux-header corresponding to the kernel you just upadted, and then you need to run vmware-config.pl again.

James

---

### Post by diggity on 2006-09-28
You will need to use the vmware kernel headers.
IIRC the new linux kernel headers don't work correctly when compiling vmware.

---

### Post by szf on 2006-09-28
> **diggity said:**
> You will need to use the vmware kernel headers.
IIRC the new linux kernel headers don't work correctly when compiling vmware.

Exactly. I don't blame VMWare - this was the Player and it was/is free-as-in-beer.

I will re-install the Player at some point... just not on my main OS.

---

### Post by Mellon on 2006-09-29
Hola a Todos,

I get vmware from automatix in a new ubuntu instalation, but i didnt read that it was vmware player, then i uninstall it with the help of synaptic. 

my problem is that i cant follow the "how to" to install vmware server. 

i get this error when i type:

> edwin@edwin-desktop:~/hdd1/programas/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.


Someone can help me?

if i type vmware in terminal it say:

> edwin@edwin-desktop:~/hdd1/programas/vmware-server-distrib$ VMware
bash: VMware: orden no encontrada


that mean someting like no command found.

Muchas gracias.

---

