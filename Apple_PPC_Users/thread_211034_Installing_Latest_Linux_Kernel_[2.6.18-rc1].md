---
title: "Installing Latest Linux Kernel [2.6.18-rc1]"
date: 2006-07-07
forum: Apple PPC Users
---

### Post by zachws on 2006-07-07
How does one go about installing 2.6.18-rc1 on the PPC architecture?

I know this is bold, but is it possible?

---

### Post by mlind on 2006-07-07
Yes it's possible. There are few HOWTO's on forums about building kernel 'the Debian way' from upstream and few useful wiki articles too.

Basically you 
[LIST]
[*]add yourself to src group to gain write permissions to /usr/src folder (not mandatory)
[*]download a kernel from upstream to /usr/src and extract it
[*]copy your current kernel's config form /boot to the root of the extracted kernel tree, as .config
[*]issue make oldconfig
[*]make xconfig/menuconfig and tweak the settings
[*]install kernel-package -package using aptitude
[*]make kernel_image target
```

make-kpkg --initrd --revision MyTastyVanillal.01 kernel_image

```
[/LIST]

in a nutshell atleast.

---

### Post by zachws on 2006-07-11
I appreciate the response... but can you be a wee bit more specific? (sorry)

can someone throw me a bone on this? (i have looked around the forum and done my own research but I just need some PPC specifics so I don't go and crash my system).

thanks

---

### Post by mlind on 2006-07-11
> **zachws said:**
> I appreciate the response... but can you be a wee bit more specific? (sorry)

This is untested, but something like this

```

#prerequisits, maybe older gcc too
sudo aptitude install build-essential fakeroot kernel-package
sudo adduser $USER src
su $USER

#get newest kernel and extract it
cd /usr/src
rsync -avz --progress rsync://kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.4.tar.bz2 .
tar -jxvf linux-2.6.17.4.tar.bz2
ln -sf linux-2.6.17.4 linux
cd linux

#for xconfig you need libqt3
sudo aptitude install libqt3-mt-dev
fakeroot make-kpkg clean

#use existing kernel configuration as template
cp /boot/config-$(uname -r) .config
make oldconfig
make xconfig

(edit what you like, and save)

#create kernel image
make-kpkg --rootcmd fakeroot --initrd --revision vanilla.01 binary-arch

#binary-arch will build both image and headers
#to see other targets use make-kpkg --targets

```

---

### Post by zachws on 2006-07-11
no luck. how do i login as root? is that required?

---

### Post by mlind on 2006-07-11
> **zachws said:**
> no luck. how do i login as root? is that required?

You're supposed to perform those commands as normal user, no root login is required. You'll need sudoing privileges though.
su $USER is just for relogin.

Is there something that's not working?

---

### Post by zachws on 2006-07-12
> **mlind said:**
> You're supposed to perform those commands as normal user, no root login is required. You'll need sudoing privileges though.
su $USER is just for relogin.

Is there something that's not working?



Well, there certainly is. I get to step 2, i.e.:


> #get newest kernel and extract it
cd /usr/src
rsync -avz --progress rsync://kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.4.tar.bz2 .
tar -jxvf linux-2.6.17.4.tar.bz2
ln -sf linux-2.6.17.4 linux
cd linux

Before it downloads (the terminal being it)... It says I do not have permission to save it there, and then it downloads the file but will not extract it there as I do not have permission. Here is what I have done. 

I downloaded the source, and unpacked it to my desktop. Can i copy it to /usr/src ? I assume I can I just am  not sure how with the proper permissions.

Thanks for your continued assistance and if we can get this going it would help out a lot of PPC users who always need more hardware compatability via the latest kernels. Are you on PPC?

---

### Post by mlind on 2006-07-12
> **zachws said:**
> Well, there certainly is. I get to step 2, i.e.:

Before it downloads (the terminal being it)... It says I do not have permission to save it there, and then it downloads the file but will not extract it there as I do not have permission. Here is what I have done. 


Adding your useraccount to **src** group grants you write permission to /usrc/src, but that change is only valid for new interactive login shells. For example, gnome terminal is not a login shell.

You must do **su** *yourusername* to relogin on that terminal (or restart Xserver).

> **zachws said:**
> 
I downloaded the source, and unpacked it to my desktop. Can i copy it to /usr/src ? I assume I can I just am  not sure how with the proper permissions.


You can basically do the steps on any other folder too, but I guess /usr/src is the common place.


> **zachws said:**
> 
Thanks for your continued assistance and if we can get this going it would help out a lot of PPC users who always need more hardware compatability via the latest kernels. Are you on PPC?

Sure, no problem at all. I'm on i386 arch, but I need to use newer kernel for some exotic hardware.

---

### Post by rasec on 2006-07-12
zackws, to become root you need to "sudo su -". If you assign root a password than you can su into the account, but its probably best if you leave it as it is.

---

### Post by mlind on 2006-07-12
> **rasec said:**
> zackws, to become root you need to "sudo su -". If you assign root a password than you can su into the account, but its probably best if you leave it as it is.

I'm using su here to only force relogin. Configuring kernel tree as root user is not good practice.

---

### Post by zachws on 2006-07-12
UPDATE: TYPO... fixed on my own sorry everyone.

I'm up to here:

> cp /boot/config-$(uname -r) .config

When i type that I get...

> zachws@zachws-laptop:/usr/src/linux$ cp /boot/config-$(uname -r).config
cp: missing destination file operand after `/boot/config-2.6.15-23-powerpc.config'
Try `cp --help' for more information.


Almost there...:mrgreen:

---

### Post by mlind on 2006-07-12
> **zachws said:**
> When i type that I get...



Almost there...:mrgreen:

There's supposed to be whitespace between $(uname -r) and .config. Command is for copying your current (running) kernel's configuration from /boot as .config file to current folder (which should be /usr/src/linux). 

(You can copy over any other config file too, or start from scratch without doing so)

You can test that config-$(uname -r) expands to certain filename on your /boot folder
```

ls /boot/config-$(uname -r)

```

---

### Post by zachws on 2006-07-12
your instructions were great but I received quite a shock once i typed 'make config'! An endless slew of questions about how to optimize the kernel. I guess this really is for the big boys. Anyway, I did it. after the first series of questions I just hit enter until they went away (no patience). I restarted but it brought me back to 2.16.15.23 (the current ubuntu one). I updated to 2.16.15.25 but it didnt work I guess (read threads about this, must be PPC bug). Any ideas?

---

### Post by mlind on 2006-07-12
> **zachws said:**
> your instructions were great but I received quite a shock once i typed 'make config'! An endless slew of questions about how to optimize the kernel. I guess this really is for the big boys. Anyway, I did it. after the first series of questions I just hit enter until they went away (no patience). I restarted but it brought me back to 2.16.15.23 (the current ubuntu one). I updated to 2.16.15.25 but it didnt work I guess (read threads about this, must be PPC bug). Any ideas?

You can happily accept all the defaults, just keep pressing enter. Why it prompts you is that all those options are **new**, and not included on the .config file you just copied.


You dont need to make any changes at first, just accept defaults, **make xconfig** to see what it looks like and then move to kernel building part. You'll be still using Ubuntu defaults (because you made **oldconfig**) and some addional modules perhaps came along.

Just take one step at time, and when you feel brave enough, start adjusting what get's built and what not. When you make xconfig, there's usually good information what values you should change and what not.

I warn you that there's too many options to at first sight, but you don't need to change values you don't know what they mean.

---

### Post by mlind on 2006-07-12
The last thing I didn't write on the instuctions, is that you need to install the kernel .deb after it's been built. Building part will take ages, but if it's succesfull, you'll find your vanilla kernel package at /usr/src folder.

You probably know how to install it. Sometimes grub bootloader is not updated when new kernel is installed (it should but it's not), so you may have to run *sudo update-grub* if you don't see your new kernel on the grub menu.


/edit
You didn't seem to do all the steps on the instuctions? You restarted after just make oldconfig?

---

### Post by zachws on 2006-07-12
I did follow all of the instructions BUT after the first 'make' I was blown away by all the questions being asked in the terminal... do i want SMB? Altivec? and after that a bunch (50 plus) of things I didnt understand at all.

Also, I am in yaboot (as this is a PPC situation), not GRUB. Any ideas? Thanks for your ongoing support.

---

### Post by mlind on 2006-07-13
> **zachws said:**
> I did follow all of the instructions BUT after the first 'make' I was blown away by all the questions being asked in the terminal... do i want SMB? Altivec? and after that a bunch (50 plus) of things I didnt understand at all.

Also, I am in yaboot (as this is a PPC situation), not GRUB. Any ideas? Thanks for your ongoing support.

Just press and hold enter for those questions to accept the defaults.
I don't know about yaboot, sorry. I guess you'll just have to find out.

---

### Post by rasec on 2006-07-13
zackws, I have a working 2.6.17.1 .config from back when I was trying to get my airport extreme working. Its somewhat tailored to my powerbook, in that the only thing I removed from the default ubuntu config were some x86 motherboard chipset drivers. Let me know if you want it. By the way, SMB is a the windows network share protocol, I think you ment SMP which is support for multiprocessors, something which you don't need because you have a ibook. And Altivec is the name of the special instruction set found in the G4 processors, which you could do without, but certain applications like fftw run faster when its enabled. 

I explained how to make yaboot entries in a different thread, but I believe the general consensus is to modify the vmlinux and initrd syslinks instead. Just make sure that you don't screw up your backup kernel symlinks in the process. Or better yet, make sure that you can boot into your backup kernel before you modify your vmlinux syslinks. Don't worry too much though, if you do happend to screw up your symlinks, you can always use the livecd to correct them.

---

