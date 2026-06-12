---
title: "Booting my PPC Install"
date: 2006-05-31
forum: Apple PPC Users
---

### Post by worldgoesround on 2006-05-31
Hi everyone,

I am trying to install Ubuntu on my blue Mac G3; however, after the install, I can't get the computer to boot off the hard drive. I think it has something to do with apple firmware. Has anyone had any issues with bootinig linux on their ppc?

Thanks!

---

### Post by autocrosser on 2006-05-31
Give us some more info about what your G3 is doing--black screen?? You might also look in the 5.10 forums--I know that there is a wealth of G3 info there--I haven't used a Blue&White in 6 years;)--Good unit--is it a 300/350 or a 400?

---

### Post by godard on 2006-06-01
I've been having issues with my G4 booting dapper [http://www.ubuntuforums.org/showthread.php?p=1075216#post1075216](http://www.ubuntuforums.org/showthread.php?p=1075216#post1075216)

On a whim i tried putting the HD in my old B&W, trying to select the ubuntu drive spewed out a bunch of error messages after i selected 'L'. I tried rebooting, if i patiently waited, i got an os x apple firmware message with options, but the system was locked up forcing me to force shutdown.

---

### Post by fra.sa on 2006-06-01
Maybe you are having my same problems!
Please take a look at this:

[http://www.ubuntuforums.org/showthread.php?t=121214]("http://www.ubuntuforums.org/showthread.php?t=121214")

(one of the last posts).
I'm tryng at the moment to compile a new 2.6.15 dapper kernel with a hack suggested here:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

bye 
francesco

**Updated**

I've just tried the new compiled kernel and I can confirm that the system now starts flawlessly!

Is there hope to see this change in the official kernel soon, and in the iso images also, so us, poor owner of these old imac, can have the chance to boot and install dapper without many troubles?

cheers 
francesco

---

### Post by kingred on 2006-06-01
[QUOTE=fra.sa]Maybe you are having my same problems!
Please take a look at this:

[http://www.ubuntuforums.org/showthread.php?t=121214]("http://www.ubuntuforums.org/showthread.php?t=121214")

(one of the last posts).
I'm tryng at the moment to compile a new 2.6.15 dapper kernel with a hack suggested here:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

bye 
francesco

**Updated**

I've just tried the new compiled kernel and I can confirm that the system now starts flawlessly!

Is there hope to see this change in the official kernel soon, and in the iso images also, so us, poor owner of these old imac, can have the chance to boot and install dapper without many troubles?

cheers 
francesco[/QUOTE]


that seems a bit complex for an extreme n00b like me. 

how would i do it on a imac 233mhz tray loader with 64 meg of ram

---

### Post by fra.sa on 2006-06-01
[QUOTE=kingred]that seems a bit complex for an extreme n00b like me. 

how would i do it on a imac 233mhz tray loader with 64 meg of ram[/QUOTE]

you are right it's a bit complex for an extreme n00b!

But I posted this msg in the hope that someone of the ubuntu developers read it and provide an upgraded kernel either in the dapper repositories and in the cd iso images that let you install or try the distribution. 
So you have two chance:

1) wait for the upgraded kernel (and cd images) - (the easy thing)

2) learn how to patch and compile a kernel, but I think you have to know programming a bit.

bye francesco

---

### Post by rottenmac on 2006-06-01
I *just* got sucked into this by someone.

I installed this for the first time on my G4/450 and now I can't seem to start up from it. what do I do here? I am without question a n00b, and would like to learn more.

If i hold down the OPT key, the drive with ubuntu on it shows up, and I can choose it, but then..... nuthin.

what can we all do to grow the support for OS X dorks like us?
HELP !

---

### Post by kingred on 2006-06-01
[QUOTE=rottenmac]I *just* got sucked into this by someone.

I installed this for the first time on my G4/450 and now I can't seem to start up from it. what do I do here? I am without question a n00b, and would like to learn more.

If i hold down the OPT key, the drive with ubuntu on it shows up, and I can choose it, but then..... nuthin.

what can we all do to grow the support for OS X dorks like us?
HELP ![/QUOTE]
mate your better off installing a badger of the breezy flavour ubuntu while dapper gets its stuff sorted for us mac folks.

to boot from cd, on startup hold down c (or as i do hammer it) untill you get a boot option from hdd or cd then install from teh cd.

---

### Post by rottenmac on 2006-06-02
I DID install from the CD, thats the thing. Im not a complete idjit, but I cant seem to get it to start up from the drive i installed it on. Also, OSX does not recognize the drive. It asks me if i want to initialize or ignore it.

I just want to use the damn software.

---

### Post by phibxr on 2006-06-02
[QUOTE=rottenmac]I DID install from the CD, thats the thing. Im not a complete idjit, but I cant seem to get it to start up from the drive i installed it on. Also, OSX does not recognize the drive. It asks me if i want to initialize or ignore it.

I just want to use the damn software.[/QUOTE]

The Live CD kernel usually boots fine, while the installed kernel does not. We're waiting for the developers to implement the patch in a kernel update right now. Unfortunately, it didn't make it in time for the Dapper release, but if you read the bug report mentioned earlier in this thread, you'll find that the developers are working on this.

---

### Post by BoneKracker on 2006-06-03
On my G4, it frequently stalls at stage 2 bootup (I get the ELF notice that it's loading the image, and then white screen and blank screen).  

The good news... If I reboot enough times, it boots up.  Sometimes it boots on first try, sometimes second, but it has taken as many as five.  Do give it a good wait though, before rebooting.  Sometimes there's  delay of 30 seconds or more before it starts.  

Neither mkofboot nor ybin seem to have any effect - I think it's got to be something with how the kernel image is loaded.

I haven't checked it boots from OF prompt or graphical bootloader every time or not.

---

