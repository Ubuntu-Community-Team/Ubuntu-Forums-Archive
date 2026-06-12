---
title: "Boot different kernel with yaboot?"
date: 2008-08-22
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2008-08-22
I have all of these kernel images in /boot and I wanted to try booting some of the older ones to see if they correct the issues I still have with Hardy on my TiBook G4,powerpc.
Is there a simple way? Do I need to edit yaboot.conf (I'm sure I do)and if so what do I put in there?
Would something like this work? (The first 2 images are what are in the conf file already and I didn't include the mac boot files.

```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

	root = /dev/hda8
image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
	root = /dev/hda8
image=/boot/vmlinux-2.6.15-52-powerpc
	label=testkernel
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
	root = /dev/hda8
```


Thanks for any help!

---

### Post by tiresia on 2008-08-22
Do not change your yaboot.conf! You do not need.
Just hit TAB when yaboot starts, and you can choose the kernel you want to boot.

---

### Post by ubuntubrian on 2008-08-22
Thanks for the reply. I only have "Linux" and "old", which I have always had. I'd like to boot one of the other kernels in /boot. Here're the contents of /boot:

/boot$ ls
abi-2.6.12-9-powerpc          initrd.img-2.6.15-51-powerpc
abi-2.6.15-20-powerpc         initrd.img-2.6.15-52-powerpc
abi-2.6.15-21-powerpc         initrd.img-2.6.24-19-powerpc
abi-2.6.15-22-powerpc         initrd.img-2.6.24-19-powerpc.bak
abi-2.6.15-23-powerpc         initrd.img-2.6.24-19-powerpc-smp
abi-2.6.15-26-powerpc         initrd.img-2.6.24-19-powerpc-smp.bak
abi-2.6.15-27-powerpc         initrd.img.old
abi-2.6.15-28-powerpc         System.map-2.6.12-8-powerpc
abi-2.6.15-29-powerpc         System.map-2.6.12-9-powerpc
abi-2.6.15-51-powerpc         System.map-2.6.15-20-powerpc
abi-2.6.15-52-powerpc         System.map-2.6.15-21-powerpc
abi-2.6.24-19-powerpc         System.map-2.6.15-22-powerpc
abi-2.6.24-19-powerpc-smp     System.map-2.6.15-23-powerpc
config-2.6.12-8-powerpc       System.map-2.6.15-26-powerpc
config-2.6.12-9-powerpc       System.map-2.6.15-27-powerpc
config-2.6.15-20-powerpc      System.map-2.6.15-28-powerpc
config-2.6.15-21-powerpc      System.map-2.6.15-29-powerpc
config-2.6.15-22-powerpc      System.map-2.6.15-51-powerpc
config-2.6.15-23-powerpc      System.map-2.6.15-52-powerpc
config-2.6.15-26-powerpc      System.map-2.6.24-19-powerpc
config-2.6.15-27-powerpc      System.map-2.6.24-19-powerpc-smp
config-2.6.15-28-powerpc      vmlinux
config-2.6.15-29-powerpc      vmlinux-2.6.12-8-powerpc
config-2.6.15-51-powerpc      vmlinux-2.6.12-9-powerpc
config-2.6.15-52-powerpc      vmlinux-2.6.15-20-powerpc
config-2.6.24-19-powerpc      vmlinux-2.6.15-21-powerpc
config-2.6.24-19-powerpc-smp  vmlinux-2.6.15-22-powerpc
initrd.img                    vmlinux-2.6.15-23-powerpc
initrd.img-2.6.12-8-powerpc   vmlinux-2.6.15-26-powerpc
initrd.img-2.6.12-9-powerpc   vmlinux-2.6.15-27-powerpc
initrd.img-2.6.15-20-powerpc  vmlinux-2.6.15-28-powerpc
initrd.img-2.6.15-21-powerpc  vmlinux-2.6.15-29-powerpc
initrd.img-2.6.15-22-powerpc  vmlinux-2.6.15-51-powerpc
initrd.img-2.6.15-23-powerpc  vmlinux-2.6.15-52-powerpc
initrd.img-2.6.15-26-powerpc  vmlinux-2.6.24-19-powerpc
initrd.img-2.6.15-27-powerpc  vmlinux-2.6.24-19-powerpc-smp
initrd.img-2.6.15-28-powerpc  vmlinux.old
initrd.img-2.6.15-29-powerpc


Any help?

---

### Post by tiresia on 2008-08-23
Sorry, but I had not understood your question. If you compiled a new kernel and you want to try it, yes you should change your yaboot.conf in order to boot a different kernel. Once you are done, don't forget to run```
ybin -v 
```

---

### Post by ubuntubrian on 2008-08-23
Thanks for the quick reply Tiresia! I'm glad I cleared that up for you but....
These are old kernels that have been in /boot since Dapper and I've never removed them. there are a couple of things that I'm trying to accomplish.
the first is to see if I can boot one of the older kernels and if so the question is how do I modify my yaboot.conf file? I have read much on it but am still unsure which is why I included my hypothetical configuration in the first post which references a kernel image in /boot.
I have not compiled a new kernel but may try that as I have Mac-On-Linux installed which will not run with my current kernel 2.6.24-19, but people report will with a Gutsy kernel. Compiling that is a whole other matter that I have never even tried but I'm game.
So, to sum up, are these images in /bott actually bootable and if so just how do I edit my yaboot.conf file to use them?
BTW, I was following this which has good info but for a newbie there's too much ambiguity:[http://www.linuxchix.org/content/courses/kernel_hacking/lesson4](http://www.linuxchix.org/content/courses/kernel_hacking/lesson4)

Many, many thanks!

---

### Post by tiresia on 2008-08-24
First of all, make a backup of your yaboot.conf
```
sudo cp /etc/yaboot.conf /etc/yaboot.conf-backup
```

You need to specify in yaboot.conf following:

1. The filesystem path to the kernel image (image=)
2. The related ramdisk image for the kernel you want to load (initrd=)

Since it seems that you want to boot the kernel 'vmlinux-2.6.15-52-powerpc', make a symlink to that kernel with the name 'vmlinux.oldest' (or whatever you want) and a symlink to its ramdisk image with 'initrd.img.oldest' (or whatever you want):

```
sudo ln -s /boot/vmlinux-2.6.15-52-powerpc /boot/vmlinux.oldest
```
```
sudo ln -s /boot/initrd.img-2.6.15-52-powerpc /boot/initrd.img.oldest
```

Your yaboot.conf should look like this:

```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"
	root = /dev/hda8

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
	root = /dev/hda8

image=/boot/vmlinux.oldest
	label=oldest
	read-only
	initrd=/boot/initrd.img.oldest
	append="quiet splash"
	root = /dev/hda8
```

Save the file and run ybin
```
sudo ybin -v
```

Restart your computer, at the boot: prompt, hit TAB. Now you should see the three kernels, that you can choose: Linux, old and oldest. Type 'oldest' (or the label you hace choosen to select the vmlinux-2.6.15-52-powerpc kernel).

---

P.S. I'm not sure, that your system will work, but you can try anyway&#8230;
I guess you know these links:
[http://mac-on-linux.sourceforge.net/wiki/index.php/Main_Page](http://mac-on-linux.sourceforge.net/wiki/index.php/Main_Page)
[http://mac-on-linux.sourceforge.net/wiki/index.php/Installation_Instructions](http://mac-on-linux.sourceforge.net/wiki/index.php/Installation_Instructions)
[https://help.ubuntu.com/community/MacOnLinuxHowto](https://help.ubuntu.com/community/MacOnLinuxHowto)

---

### Post by ubuntubrian on 2008-08-24
Thanks so much for the clear instructions! this was on some of the wikis, etc. but the actual editing was unclear to me and you cleared it right up tiresia. I realize that the older kernels may not run with Hardy but I can also now install a Gutsy kernel and try that and yes, I am going for MOL as well as trying to get better performance as Hardy is much slower than Dapper was on my TiBook. 
Interestingly, it is now suspending and waking fine and if I leave it booted and don't shut down the performance improves over time. Odd...

---

### Post by ubuntubrian on 2008-08-24
BTW, do you run MOL on Hardy tiresia?

---

### Post by tiresia on 2008-08-24
> **ubuntubrian said:**
> BTW, do you run MOL on Hardy tiresia?
No, unfortunatly I can't, because MOL doesn't run on powerpc64&#8230;
I can only use Qemu to emulate an OS, but it does not work with emulate a powerpc architecture (even if it says it does)

---

### Post by sayad on 2008-08-24
now  a boot loader for PowerPC-based hardware running Linux, particularly New World ROM Macintosh systems. It is built to run within the Open Firmware layer common to most such systems instead of working as a Mac OS 9 program like its predecessor BootX.

---

### Post by ubuntubrian on 2008-08-24
hi Sayad. Is part of your post missing? I don't understand it otherwise.
I have MOL installed and it ran great on Dapper but it will not on Hardy. Actually it's OS X drivers that can't be installed so i guess that OS 9 would run but I don't have that installed.
I have read that various kernel patches and building a kernel allow it to run on Hardy but the simplest is a post that stated that it would run of a Gutsy kernel. I'm not sure how that works yet and if I could just install the drivers once booted into a Gutsy kernel and run MOL or not.
Getting a Gutsy kernel to boot would be a first step.

---

### Post by ubuntubrian on 2008-08-31
Ah well, that didn't work! Installing the Gutsy kernel caused a requested restart, which I did. That created some major errors with the package manager and I had to uninstall the Gutsy kernel and Update Manager requested an update. I did the update, which were kernel updates and some odds and ends, and my sound died. I also lost the "old" yaboot option and by uninstalling the Gutsy kernel I'm left with a link to it from these commands:
> 
Code:

sudo ln -s /boot/vmlinux-2.6.15-52-powerpc /boot/vmlinux.oldest

Code:

sudo ln -s /boot/initrd.img-2.6.15-52-powerpc /boot/initrd.img.oldest



and this is what remains:
```

lrwxrwxrwx 1 root root      35 2008-08-29 10:37 vmlinux.oldest -> /boot/vmlinux-2.6.22-15-powerpc-smp

```

I don't know why the link switched to the 22.15 kernel but that isn't installed anymore. I'd like to remove the link. I created another link to the 15.52 kernel named "Dapper".

Thanks for any help!

---

### Post by ubuntubrian on 2008-08-31
Scary! My yaboot.conf is in tough shape now. I installed an earlier kernel (yes, since last post) from Synaptic as I thought that that shouldn't be an issue. I cleaned up my /boot file by creating links to the older images using:
```
sudo cp /etc/yaboot.conf /etc/yaboot.conf-backup
```
then:
```
sudo ln -s /boot/vmlinux-2.6.15-52-powerpc /boot/vmlinux.dapper
sudo ln -s /boot/initrd.img-2.6.15-52-powerpc /boot/initrd.img.dapper
sudo ln -s /boot/initrd.img-2.6.24-18-powerpc-smp /boot/initrd.img.2.6.24-18-smp
sudo ln -s /boot/vmlinux-2.6.24-18-powerpc-smp /boot/vmlinux.2.6.24-18-smp

```
I edited my yaboot.conf and ran 
```
sudo ybin -v

```

I had installed the image for 2.6.24-19-powermac-smp during the previous update and had fortunately added it to my yaboot.conf. After this I decided to give up rather than further bork my set up and so I uninstalled the 2.6.24-18 and 2.6.24-16 kernels, images and headers through Synaptic as I had used it to install them. Should be safe.
I did the uninstall thinking that I at least still had the vmlinux boot option as well as the 2.6.24-19-smp.
Here's my current yaboot.conf:
```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

	root = /dev/hda8
image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
	root = /dev/hda8

image=/boot/vmlinux-2.6.24-19-powerpc-smp
 	label=24.19-smp
 	read-only
 	initrd=/boot/initrd.img-2.6.24-19-powerpc-smp
	append="quiet splash"
	root = /dev/hda8

```

Upon rebooting I hit tab and had the options of "Linux", "Old" and "24.19-smp". Only the 24.19-smp would boot (in which I have no sound at all).
Here's my /boot file:
```
brianokeefe@ubuntu:/boot$ ls -l
total 203264
-rw-r--r-- 1 root root  208261 2005-10-10 08:47 abi-2.6.12-9-powerpc
-rw-r--r-- 1 root root  244963 2006-04-04 13:02 abi-2.6.15-20-powerpc
-rw-r--r-- 1 root root  245179 2006-04-21 11:09 abi-2.6.15-21-powerpc
-rw-r--r-- 1 root root  248384 2006-05-07 11:03 abi-2.6.15-22-powerpc
-rw-r--r-- 1 root root  248749 2006-05-23 08:10 abi-2.6.15-23-powerpc
-rw-r--r-- 1 root root  249098 2006-09-08 14:15 abi-2.6.15-26-powerpc
-rw-r--r-- 1 root root  249098 2006-12-08 11:13 abi-2.6.15-27-powerpc
-rw-r--r-- 1 root root  249098 2007-07-18 17:14 abi-2.6.15-28-powerpc
-rw-r--r-- 1 root root  249098 2007-09-24 11:41 abi-2.6.15-29-powerpc
-rw-r--r-- 1 root root  249098 2008-02-12 10:16 abi-2.6.15-51-powerpc
-rw-r--r-- 1 root root  249098 2008-07-11 07:44 abi-2.6.15-52-powerpc
-rw-r--r-- 1 root root  427444 2008-08-20 15:50 abi-2.6.24-19-powerpc
-rw-r--r-- 1 root root  430520 2008-08-20 15:52 abi-2.6.24-19-powerpc-smp
-rw-r--r-- 1 root root   46759 2005-08-30 16:01 config-2.6.12-8-powerpc
-rw-r--r-- 1 root root   46817 2005-10-10 08:25 config-2.6.12-9-powerpc
-rw-r--r-- 1 root root   57616 2006-04-04 11:44 config-2.6.15-20-powerpc
-rw-r--r-- 1 root root   57780 2006-04-21 10:44 config-2.6.15-21-powerpc
-rw-r--r-- 1 root root   57939 2006-05-07 09:44 config-2.6.15-22-powerpc
-rw-r--r-- 1 root root   57999 2006-05-23 07:45 config-2.6.15-23-powerpc
-rw-r--r-- 1 root root   58003 2006-09-08 13:50 config-2.6.15-26-powerpc
-rw-r--r-- 1 root root   57992 2006-12-08 10:50 config-2.6.15-27-powerpc
-rw-r--r-- 1 root root   57992 2007-07-18 16:49 config-2.6.15-28-powerpc
-rw-r--r-- 1 root root   57992 2007-09-24 11:18 config-2.6.15-29-powerpc
-rw-r--r-- 1 root root   57992 2008-02-12 09:53 config-2.6.15-51-powerpc
-rw-r--r-- 1 root root   57992 2008-07-11 07:21 config-2.6.15-52-powerpc
-rw-r--r-- 1 root root   72382 2008-08-20 15:50 config-2.6.24-19-powerpc
-rw-r--r-- 1 root root   72101 2008-08-20 15:52 config-2.6.24-19-powerpc-smp
-rw-r--r-- 1 root root 5871736 2005-09-15 20:33 initrd.img-2.6.12-8-powerpc
-rw-r--r-- 1 root root 7314502 2006-04-25 13:02 initrd.img-2.6.12-9-powerpc
-rw-r--r-- 1 root root 7799808 2006-04-28 00:09 initrd.img-2.6.15-20-powerpc
-rw-r--r-- 1 root root 7802526 2006-05-05 22:42 initrd.img-2.6.15-21-powerpc
-rw-r--r-- 1 root root 8072411 2006-05-26 07:38 initrd.img-2.6.15-22-powerpc
-rw-r--r-- 1 root root 8072698 2006-05-29 16:07 initrd.img-2.6.15-23-powerpc
-rw-r--r-- 1 root root 8091421 2006-09-15 00:00 initrd.img-2.6.15-26-powerpc
-rw-r--r-- 1 root root 8091066 2006-12-14 11:11 initrd.img-2.6.15-27-powerpc
-rw-r--r-- 1 root root 8092300 2007-10-28 15:38 initrd.img-2.6.15-28-powerpc
-rw-r--r-- 1 root root 8145517 2007-12-17 11:54 initrd.img-2.6.15-29-powerpc
-rw-r--r-- 1 root root 8146270 2008-02-15 16:10 initrd.img-2.6.15-51-powerpc
-rw-r--r-- 1 root root 8146256 2008-07-15 16:22 initrd.img-2.6.15-52-powerpc
lrwxrwxrwx 1 root root      38 2008-08-30 22:30 initrd.img.2.6.24-18-smp -> /boot/initrd.img-2.6.24-18-powerpc-smp
-rw-r--r-- 1 root root 9618353 2008-08-29 14:11 initrd.img-2.6.24-19-powerpc
-rw-r--r-- 1 root root 9480443 2008-08-08 14:09 initrd.img-2.6.24-19-powerpc.bak
-rw-r--r-- 1 root root 9694652 2008-08-29 14:12 initrd.img-2.6.24-19-powerpc-smp
-rw-r--r-- 1 root root 9694448 2008-08-17 14:04 initrd.img-2.6.24-19-powerpc-smp.bak
lrwxrwxrwx 1 root root      34 2008-08-30 22:28 initrd.img.Dapper -> /boot/initrd.img-2.6.15-52-powerpc
lrwxrwxrwx 1 root root      38 2008-08-29 10:38 initrd.img.oldest -> /boot/initrd.img-2.6.22-15-powerpc-smp
-rw-r--r-- 1 root root  822631 2005-08-30 17:09 System.map-2.6.12-8-powerpc
-rw-r--r-- 1 root root  822587 2005-10-10 08:47 System.map-2.6.12-9-powerpc
-rw-r--r-- 1 root root  667637 2006-04-04 13:03 System.map-2.6.15-20-powerpc
-rw-r--r-- 1 root root  667637 2006-04-21 11:09 System.map-2.6.15-21-powerpc
-rw-r--r-- 1 root root  667637 2006-05-07 11:03 System.map-2.6.15-22-powerpc
-rw-r--r-- 1 root root  667985 2006-05-23 08:10 System.map-2.6.15-23-powerpc
-rw-r--r-- 1 root root  660829 2006-09-08 14:16 System.map-2.6.15-26-powerpc
-rw-r--r-- 1 root root  660335 2006-12-08 11:13 System.map-2.6.15-27-powerpc
-rw-r--r-- 1 root root  661511 2007-07-18 17:14 System.map-2.6.15-28-powerpc
-rw-r--r-- 1 root root  661564 2007-09-24 11:42 System.map-2.6.15-29-powerpc
-rw-r--r-- 1 root root  661564 2008-02-12 10:16 System.map-2.6.15-51-powerpc
-rw-r--r-- 1 root root  661564 2008-07-11 07:44 System.map-2.6.15-52-powerpc
-rw-r--r-- 1 root root  839034 2008-08-20 15:50 System.map-2.6.24-19-powerpc
-rw-r--r-- 1 root root  859699 2008-08-20 15:52 System.map-2.6.24-19-powerpc-smp
-rw-r--r-- 1 root root 4134082 2005-08-30 17:09 vmlinux-2.6.12-8-powerpc
-rw-r--r-- 1 root root 4134050 2005-10-10 08:47 vmlinux-2.6.12-9-powerpc
-rw-r--r-- 1 root root 4258251 2006-04-04 13:02 vmlinux-2.6.15-20-powerpc
-rw-r--r-- 1 root root 4258176 2006-04-21 11:09 vmlinux-2.6.15-21-powerpc
-rw-r--r-- 1 root root 4258176 2006-05-07 11:03 vmlinux-2.6.15-22-powerpc
-rw-r--r-- 1 root root 4262734 2006-05-23 08:10 vmlinux-2.6.15-23-powerpc
-rw-r--r-- 1 root root 4208331 2006-09-08 14:15 vmlinux-2.6.15-26-powerpc
-rw-r--r-- 1 root root 4207807 2006-12-08 11:13 vmlinux-2.6.15-27-powerpc
-rw-r--r-- 1 root root 4209188 2007-07-18 17:14 vmlinux-2.6.15-28-powerpc
-rw-r--r-- 1 root root 4209237 2007-09-24 11:41 vmlinux-2.6.15-29-powerpc
-rw-r--r-- 1 root root 4209237 2008-02-12 10:16 vmlinux-2.6.15-51-powerpc
-rw-r--r-- 1 root root 4209233 2008-07-11 07:44 vmlinux-2.6.15-52-powerpc
lrwxrwxrwx 1 root root      35 2008-08-30 22:31 vmlinux.2.6.24-18-smp -> /boot/vmlinux-2.6.24-18-powerpc-smp
-rw-r--r-- 1 root root 5137620 2008-08-20 15:50 vmlinux-2.6.24-19-powerpc
-rw-r--r-- 1 root root 5355247 2008-08-20 15:52 vmlinux-2.6.24-19-powerpc-smp
lrwxrwxrwx 1 root root      31 2008-08-30 22:27 vmlinux.Dapper -> /boot/vmlinux-2.6.15-52-powerpc
lrwxrwxrwx 1 root root      35 2008-08-29 10:37 vmlinux.oldest -> /boot/vmlinux-2.6.22-15-powerpc-smp

```

I hadn't made a link for the 2.6.24-19-powermac-smp image, just added it to my yaboot.conf as you see above. Luckily it booted.
The question is why did "Linux" disappear from /boot and no longer be a boot option? How do I get it back? How do I clean up /boot to something functional (moreso at least).
thanks for any help!

---

