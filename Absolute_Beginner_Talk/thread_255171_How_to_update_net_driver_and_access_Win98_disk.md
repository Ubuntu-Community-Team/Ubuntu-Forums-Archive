---
title: "How to update net driver and access Win98 disk"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by nitewing98 on 2006-09-11
Hi, I'm not exactly a newbie, I've used Linux before but it was several years ago.  My Dad is fed up with Windows (he's had several virus/spyware infections despite my constant help) and liked the Live CD, so I am installing it for him (after backing up his files on a CD with my burner).

Dad has an older PC that is on my home network with my iMac and a Comcast router.  The iMac is directly connected to the router, but Dad's machine has a Netgear MA111 USB wireless adapter.

I should also add that I partitioned Dad's drive and have Win98 on one partition, Ubuntu on the other.

Here's the problem: Although the Netgear wifi widget is listed in the Device Manager, it isn't listed in the Networking Admin list as an available device.  I've read some of the older posts here and got the impression that 
A) I need the linux source code for this distro and
B) I need the linux-wlan driver  and
C) I need to compile the driver with the linux source.

Ordinarily in this situation, I'd use the working Win98 installation to get the files I need, reboot in linux, mount the Win98 partition and pull the files I need into Ubuntu so I can do the compile.  But when I try to mount the Win98 partition, Ubuntu says it can't.  And when I try to enable that partition in Disk Admin, it won't enable.  

What am I doing wrong?

---

### Post by monktbd on 2006-09-11
what do the commands 
> 
sudo fdisk -l
and
> cat /etc/fstab
say?

---

### Post by nitewing98 on 2006-09-11
Nevermind! :) I got them mounted.  I had forgotten all about fstab and someone else's post reminded me that I had to add the partition.

Now, where can I get the linux source for this distro?  Keep in mind I can't fetch it from Ubuntu, since the network card doesn't work.  I've seen folks using apt commands to get the source, but that won't work in Windows 98! :( 

Thanks for any help you can give me.  Although I use a Mac myself, I'm excited for Dad to get Linux.  My Mac's OS is also a flavor of unix, and now we'll be speaking the same language!

---

### Post by Najand on 2006-09-11
> **nitewing98 said:**
> My Mac's OS is also a flavor of unix, and now we'll be speaking the same language!

Hmm ,I don't think Mac's Darwin is similar to Linux. It is more Unix, I think....

---

### Post by monktbd on 2006-09-11
getting all the sources you need by hand...
this can get quite tedious i guess..

important would be to know what you all need.
since i dont know your problem well i can only guess about what you might need to recompile a wireless driver module:

first you need the build environment (compiler, headers, etc..)
this is usually done with the
> 
sudo apt-get install build-essential


as far as i know this is already on the cd so you can get it from there.

then if you need the linux source of the kernel the package is called linux-source and points to the correct package for the kernel you use.

> uname -a 
gives a ways the kernel number.

look at 
[http://at.archive.ubuntu.com/ubuntu/pool/main/l/](http://at.archive.ubuntu.com/ubuntu/pool/main/l/)
for the source you will need.
maybe change the "at" in the link to your country/area.

there is a directory there with the name of the kernel and with a lot of files in there.
get all the debs in there for your architecture (probably i386) and install the debs then with dpkg in ubuntu.

then you can try to compile the driver as needed and maybe there are other packages still missing and it might happen more than once.

this can get very tedious but right now i cannot think of an easier way to do it.
maybe it might be easier to just plug your fathers computer to the net and get all the needed things there before finally putting it back to wireless.

edit: maybe looking for an ubuntu dvd image might also help.

---

### Post by monktbd on 2006-09-11
> **Najand said:**
> Hmm ,I don't think Mac's Darwin is similar to Linux. It is more Unix, I think....

mac os x is a BSD derivate. so one can argue how similar that is to linux. or how similar linux is to unix :).
mac os x is actually quite similar to ubuntu in the way administrative things are handled (sudo).

---

### Post by Najand on 2006-09-11
> **monktbd said:**
> mac os x is a BSD derivate. so one can argue how similar that is to linux. or how similar linux is to unix :).
mac os x is actually quite similar to ubuntu in the way administrative things are handled (sudo).

Linux is a GNU Project and I think everyone knows that GNU started by the motto "GNU's not Unix" : You can still find that on the GNU.org homepage. MAC OS X is not similar to linux becuase it has a close source which is closed even worse than Mizrosoft Windows (Microsoft is starting to develope few open-source softwares recently.). That makes MAC OS X a Unix Machine not a Linux machine.

---

### Post by monktbd on 2006-09-11
> **Najand said:**
> Linux is a GNU Project and I think everyone knows that GNU started by the motto "GNU's not Unix" : You can still find that on the GNU.org homepage. MAC OS X is not similar to linux becuase it has a close source which is closed even worse than Mizrosoft Windows (Microsoft is starting to develope few open-source softwares recently.). That makes MAC OS X a Unix Machine not a Linux machine.

i know all that :).
i am not talking about OS the open and closed source way in this matter but just how basically the OS functions.
linux was developed having a unix in mind, a proper stable multiuser OS.

gnu is not intended to be against unix.
it is just saying that that software was not developed by the developers of unix themselves (ok to clarify to be not bundled with the non free OS, the developers probably developed for both).

read the hisory of e.g. richard stallman and how he started out in the seventies programming with and for unix.

if you know your way around linux (on the commandline) , you will know your way around some unix based OS as well.
quite a few applications for linux were actually first developed on a unix environment and are much much older than linux (vi, emacs, also cdrecord,...)

so to be short
gnu (gnu's not unix) does not mean it is linux, gnu just means it is not unix.

mac os x ripped of the very free BSD license to have a stable unix background and add all the fnacy easy to use desktop environment and programs.

---

### Post by az on 2006-09-11
> **nitewing98 said:**
> 
Now, where can I get the linux source for this distro?  Keep in mind I can't fetch it from Ubuntu, since the network card doesn't work.  I've seen folks using apt commands to get the source, but that won't work in Windows 98! 
 
You don't need to download anything.  Linux-wlan-ng is on the install cd.  Just insert the cd when you are  at the desktop and the package manager will start.  Then, search and install linux-wlan-ng

You will need to edit your interfaces file, since the networkting tool does not speak the same language.


[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28prism2%29](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28prism2%29)


sudo gedit /etc/network/interfaces

Add the following to your wlan0 stanza:

wireless_mode managed
wireless_enc on
wlan_ng_key0 xx:xx:xx:xx:xx



where "xx:xx:xx:xx:xx" is you WEP seperated by colons, like this  "11:22:aa:bb:cc" for example.

---

### Post by nitewing98 on 2006-09-11
Azz,

Thanks for the info! :)

After reading the how-to, I see that my Dad's wireless card is an MA111v2, rather than a v1.  Is there some voodoo that I can use to make it work also, or am I dead in the water?

Also, my network currently has 128 bit encryption, so my WEP key is longer (13 pairs instead of 5 pairs of digits).  Is that a problem?  I can ratchet it down to 64 bit if I need to.

---

