---
title: "Captive, headers, prepmod, and so on"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by AdmiralSenn on 2005-07-09
Well, I'm not a complete newbie, but I might as well be since it's been so long since I last used anything ("anything" was RH9). 

Okay, trying to install captive. I get to the point where I mount the drive:

sudo mount -t captive-ntfs /dev/hda1 /media/windows
Captive NTFS v1.1.5.  Check a new version at: [http://www.jankratochvil.net/](http://www.jankratochvil.net/)
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
lufs module not loaded: Try running /usr/share/lufs/prepmod to see more. at /usr/bin/captive-lufsd line 180

So I go to /usr/share/lufs/, and type:

 sudo ./prepmod

Which gives me:

+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.10-5-386 (base version 2.6.10)
Destination module directory: /lib/modules/2.6.10-5-386/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.10-5-386/build
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; cd /var/lib/lufs; /usr/bin/gcc -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -D__KERNEL__ -DMODULE -DLINUX -DKBUILD_MODNAME=lufs   -I/lib/modules/2.6.10-5-386/build/include -I/lib/modules/2.6.10-5-386/build/include/asm-i386/mach-default -DMODVERSIONS -include /lib/modules/2.6.10-5-386/build/include/linux/version.h -include /lib/modules/2.6.10-5-386/build/include/linux/modversions.h -c /usr/share/lufs/2.6/proc.c /usr/share/lufs/2.6/inode.c /usr/share/lufs/2.6/dir.c /usr/share/lufs/2.6/file.c /usr/share/lufs/2.6/symlink.c; /usr/bin/ld -r -o /var/lib/lufs/lufs.ko proc.o inode.o dir.o file.o symlink.o; /bin/rm -f proc.o inode.o dir.o file.o symlink.o
+ /bin/rm -rf /lib/modules/2.6.10-5-386/kernel/fs/lufs; /bin/mkdir -p /lib/modules/2.6.10-5-386/kernel/fs/lufs; /bin/ln -s /var/lib/lufs/lufs.ko /lib/modules/2.6.10-5-386/kernel/fs/lufs/lufs.ko
+ /sbin/rmmod lufs 2>/dev/null; /sbin/insmod /lib/modules/2.6.10-5-386/kernel/fs/lufs/lufs.ko 2>/dev/null
Failed to prepare lufs.ko module for your Linux kernel 2.6.10-5-386.
Detected Linux kernel sources "/lib/modules/2.6.10-5-386/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.10-5-386/build
                /usr/src/kernel-headers-2.6.10-5-386
                /usr/src/linux-2.6.10-5-386
                /usr/src/linux-2.6.10
                /usr/src/linux
                /usr/src/kernel-source-2.6.10-5-386

Now, I've done a good bit of searching, and using synaptic and apt-get I installed the headers for my kernel (which I verified by running uname -a). I have installed the headers.. over and over.. no dice. 

Any ideas, anyone? And is there any other information I need to post?

Other than this and a few other odd problems (like getting wine working), I'm loving Ubuntu. Everything seems to work, and best of all it has a strong community and DOCUMENTATION.. I search for a generic headers download on google and ubuntuforums.org comes up  :) . 

Thanks in advance, everybody.

---

### Post by AdmiralSenn on 2005-07-09
I guess I'll bump this, since it's dropped to the second page already.

---

### Post by AdmiralSenn on 2005-07-09
Oh well, since nobody's able to help me (or nobody that can is reading this), I might as well add some more problems.

libc6 is severely broken. I have so many issues when I try to install things. Trying to get splashy requires me to get more packages, none of which work. Mplayer through synaptic requires like fifty packages, none of which work because they depend on other ones that are "not installable" for some reason. Mplayer by the HOWTO method works fine, however. 

Someone want to help me with that?

---

### Post by AdmiralSenn on 2005-07-11
Oh come on, someone has to have an idea. Is there a better forum for these questions?

---

### Post by AdmiralSenn on 2005-07-13
Ooookay, I guess I'll just try clearing out the ubuntu partitions and reinstalling from scratch. I don't know what else to do at this point.

---

### Post by Hairy_Palms on 2005-07-24
id love to say id found a solution but im only here to say ive got the exact same problem, it would appear that the kernel headers are broken, but i dont know anywhere to get a working set of headers or compile them myself if anyone knows how

---

### Post by poofyhairguy on 2005-07-25
Captive NTFS? As in the thing that allows for writing to NFTS partitions? Thats definately not a beginner thing. Try the "other software" part of the forum. I'll move this there if you want.

In fact, I would be really afraid if my beginners tried to use that unstable mess. It should be called "nuke your ntfs paritions."

---

### Post by Hairy_Palms on 2005-07-25
ive found a workaround for this, the problem is that from the 2.6.10 kernal onwards it doesnt declare kill_proc_info ive made it work on my machine by doing this
1. install captive 
2. run /usr/share/lufs/prepmod
3. open /usr/share/lufs/prepmod/2.6/inode.c
4. look for a line that says "kill_proc_info(SIGUSR1, &info, GET_INFO(sb)->server_pid);" and change it to say
 kill_proc(SIGUSR1, &info, GET_INFO(sb)->server_pid);
now if u run prepmod you can mount and read/write ntfs partitions

---

### Post by AdmiralSenn on 2005-07-25
[QUOTE=poofyhairguy]Captive NTFS? As in the thing that allows for writing to NFTS partitions? Thats definately not a beginner thing. Try the "other software" part of the forum. I'll move this there if you want.

In fact, I would be really afraid if my beginners tried to use that unstable mess. It should be called "nuke your ntfs paritions."[/QUOTE]

Now I'm mildly disturbed. I take it you don't think that installing Captive is a good idea  :-#. Isn't the 2.6 kernel supposed to include ntfs read/write support anyway? 

And if you want to move this, go ahead. I probably should have thought out where I posting a little better.

---

### Post by poofyhairguy on 2005-07-26
[QUOTE=AdmiralSenn]Isn't the 2.6 kernel supposed to include ntfs read/write support anyway? [/QUOTE]

Nope. All of the NTFS drivers are outside the kernel. No really stable way to write to NTFS exists. Its better to just convert the partition to FAT32.

---

### Post by AdmiralSenn on 2005-07-29
I would convert it if I could, but I don't have the space to back everything up to. Not even the critical stuff.

---

### Post by Hikaru79 on 2005-07-31
[QUOTE=Hairy_Palms]ive found a workaround for this, the problem is that from the 2.6.10 kernal onwards it doesnt declare kill_proc_info ive made it work on my machine by doing this
1. install captive 
2. run /usr/share/lufs/prepmod
3. open /usr/share/lufs/prepmod/2.6/inode.c
4. look for a line that says "kill_proc_info(SIGUSR1, &info, GET_INFO(sb)->server_pid);" and change it to say
 kill_proc(SIGUSR1, &info, GET_INFO(sb)->server_pid);
now if u run prepmod you can mount and read/write ntfs partitions[/QUOTE]
You're a genius, man. Worked like a charm, I love you! :D

---

### Post by dmerrill on 2005-08-10
I think I've got it working with a freshly updated Hoary system.

I had to make sure that I had the correct kernel headers installed..  I thought that I had installed the correct ones with Synaptic by installing linux-headers-2.6.10-5, but that still wasn't working. So I looked again (after doing "uname -a" to have a look at exactly what I was running), and realized that I have a 686 system apparently.. So I installed linux-headers-2.6.10-5-686, which is a *different* package.. (go figure)

Then, the only other thing I did was to make a symbolic link to the new headers in /usr/src:

>ln -s /usr/src/linux-headers-2.6.10-5-686 /usr/src/linux-headers-2.6.10

I did this because /usr/src/linux-headers-2.6.10 is one of the directories that prepmod says it's looking in, so I figured that I would make a link from there to the actual headers.

I also did the trick mentioned earlier about updating the line in inode.c, though I'm not sure if that contributed to making this work or not.. But like I said, this seems to be working.

---

### Post by bucksgt on 2005-08-10
step 3 should be: open /usr/share/lufs/2.6/inode.c

pretty sure this was just a typo/auto-completion gone wrong.

thanks tho, helped a bunch.

-qk.

[QUOTE=Hairy_Palms]ive found a workaround for this, the problem is that from the 2.6.10 kernal onwards it doesnt declare kill_proc_info ive made it work on my machine by doing this
1. install captive 
2. run /usr/share/lufs/prepmod
3. open /usr/share/lufs/prepmod/2.6/inode.c
4. look for a line that says "kill_proc_info(SIGUSR1, &info, GET_INFO(sb)->server_pid);" and change it to say
 kill_proc(SIGUSR1, &info, GET_INFO(sb)->server_pid);
now if u run prepmod you can mount and read/write ntfs partitions[/QUOTE]

---

