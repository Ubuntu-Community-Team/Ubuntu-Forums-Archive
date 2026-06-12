---
title: "vmware-server"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by lawson23 on 2007-05-16
followed this guide:
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

I setup the Canonical Commercial Repositories and installed using.
apt-get install vmware-server

The first time doing this something happened with my session when I got caught up in something and had to leave my ssh session when I got back the "end user license agreement" screen was locked and I couldn't get to the ok button.

I closed the session and didn't (newb) know how to get back into the install so I just did the install again.

said something about repairing or something (hard to remember) dpkg and gave me a command to run.
Then I ran the Install again this time it gave me the popups.
Anyways eventually I got through the second message screen and now I get this:
```
What is the location of the "make" program on your
machine?

The answer "" is invalid.  It must be the complete name of a binary file.

Invalid default answer!
Execution aborted.

dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so now this is all I ever get and can't get vmware-server installed.  Even if I try to install some other package it is like it tries to run this one again.

How can I fix my issue and get vmware-server installed?  PLEASE HELP

Background on my system is Feisty Mythtv frontend backend server style setup.

---

### Post by honeydew on 2007-05-17
I had this problem before as well on edgy.. for the longest time I couldnt figure out what was going on.. did you use automatix to install?  I would go into synaptic, and remove the packages related to vm-ware.. if that dosnt work let me know I will try and brain storm a bit to figure out what I actually did to fix it.  Also I dont know what your needs are but VirtaulBox works really well for me, has features that I appreciate a bit more than vmware as well. good luck!

---

### Post by Bachstelze on 2007-05-17
Do you have build-essential installed ?

---

### Post by lawson23 on 2007-05-17
I don't believe I have build-essentials installed does it install with the Alternate disk setup as a command- line system.

Also using the command line how do I remove it from synaptic?

---

### Post by starcraft.man on 2007-05-17
> **lawson23 said:**
> I don't believe I have build-essentials installed does it install with the Alternate disk setup as a command- line system.

Also using the command line how do I remove it from synaptic?

Synaptic isn't command line... Go System > Administration > Synaptic Package Manager, put your password in, then click on the search button and type in "vm" or "vmware" might do both to make sure you get everything, then uncheck all the boxes that are related to vmware to remove them from your system. Then apply.

As for build essential, its not installed with alternate or live installations. You have to get it manually with this command in the terminal (Applications > Accessories > Terminal):

```
sudo aptitude install build-essential
```

That should do it, after you remove vmware via synaptic tell us if you can put it back in properly :)

---

### Post by lawson23 on 2007-05-17
OK but I don't have a gui so no synaptic

---

### Post by starcraft.man on 2007-05-17
Sorry, my bad... I was reading off honeydew and missed your bit about not having gui. You want to use this command it should get it all out:

```
sudo apt-get remove --purge vmware-server
```

I think that should get it out. Hope it works, if not post back... will have to think something else. >.>

---

### Post by lawson23 on 2007-05-17
Ok this runs through some things and appears to do some removing of Vmware items.

So after doing this I tried installing vmware again and it just fails in the same method as listed above.

so I have left with running the uninstall.  Any ideas?

---

### Post by Bachstelze on 2007-05-17
Does it still ask for the location of make ? As I told you, you need ot install the build-essential package to have that program.

---

### Post by starcraft.man on 2007-05-17
You did run my command above to get build essential right? Otherwise you can't install vmware I don't think...

Edit: hehe, Hi there hymn... beating me by a few miliseconds as usual :p

---

### Post by Bachstelze on 2007-05-17
By the way, it you do have b-e installed, you can find the full path to make with the *which* command. For example :

```
$ which make
/usr/bin/make
```

So I shoudl answer /usr/bin/make when prompted for it's location.

---

### Post by lawson23 on 2007-05-17
Yes it still ask for the Make location.

---

### Post by lawson23 on 2007-05-17
```
which make
```
returns nothing

so I guess I need to install that package.

---

### Post by Bachstelze on 2007-05-17
Of course you do ! Why do you think we've been telling you to install it ?

---

### Post by starcraft.man on 2007-05-17
*smacks own forehead, then sneaks up behind lawson and gives him the Italian back hand to back of his head* :p

---

### Post by lawson23 on 2007-05-17
I never said I wasn't newb (or hard headed).

Anyways it now shows the location of make with the which command.

I will try the vmware install now.

---

### Post by lawson23 on 2007-05-17
Well I made it to the enter your serial screen which I never made it to before.

Thank you both of you very much!  Now hopefully everything else continues smoothly.

---

### Post by mcallahan01 on 2007-05-17
Okay I'm not trying to hyjack the discussion but I figured rather then fill the forums another VMware install question I'd just drop it in here.

 I am a novice (read total noob) when it comes to Linux but I've gone ahead and made the plunge and am trying to set up an Ubuntu server to run VMware but have been befuddled by the below error when I run the vmware-config.pl. If anyone can give me a bit of help I would much appreciate it.

root@Ununtu:/bin# /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps] Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca


/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!


Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:80:
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â€˜...â€™ before â€˜compat_exitâ€™
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â€˜...â€™ before â€˜exit_codeâ€™
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to â€˜intâ€™ in declaration of â€˜_syscall1â€™
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

root@Ununtu:/bin#

---

### Post by Bachstelze on 2007-05-17
Did you install vmware with the tarball downloaded from vmware.com ? If so, there's just a little patch to apply. Do you remember where you extracted the tarball to ? The directory should be named vmware-server-distrib.

---

### Post by starcraft.man on 2007-05-17
> **lawson23 said:**
> Well I made it to the enter your serial screen which I never made it to before.

Thank you both of you very much!  Now hopefully everything else continues smoothly.

No problem, glad to help. Hymn was doing lots of it, I'm mostly around for little things and keeping everyone smiling :D

Best of luck with VMware, good product you got there. I been using workstation for a long time and never been disappointed.

As to mchallan, I'll leave ya in the hands of hymn, lots of people to help and I'm sure shes got ya covered :)

---

### Post by Pollywoggy on 2007-05-17
I am having a problem...  when I try to install vmware-server, it wants to remove xinetd and install inetd.
I do not want to allow that.  Is there a way around that?

---

### Post by Bachstelze on 2007-05-17
No. That's the way the package is setup. Just install with the tarball from vmware.com.

---

### Post by Pollywoggy on 2007-05-17
That was a quick reply, I was about to ask if I could install from the tarball.  I seem to recall having tried that and that the modules would not compile in Feisty.  The tarball did not like the kernel sources, IIRC.

---

### Post by Bachstelze on 2007-05-18
Yes, vmware doesn't like the Feisty kernel. Yes, it is a known problem. Yes, it it very easily fixable. Yes, I've written a patch for it. Do you still have the tarball ?

---

### Post by Pollywoggy on 2007-05-18
> **HymnToLife said:**
> Yes, vmware doesn't like the Feisty kernel. Yes, it is a known problem. Yes, it it very easily fixable. Yes, I've written a patch for it. Do you still have the tarball ?

Yes I have the tarball.

VMware-server-1.0.0-28343.tar.gz

BTW I have this installed, should I remove these packages?

ii  vmware-server-kernel-modules-2.6.20-15     2.6.20.5-15.20                             vmware-server modules for Linux (kernel 2.6.
ii  vmware-tools-kernel-modules-2.6.20-15      2.6.20.5-15.20                             vmware-tools modules for Linux (kernel 2.6.2
ii  xserver-xorg-video-vmware                  10.15.0-0ubuntu1                           X.Org X server -- VMware display driver

---

### Post by Bachstelze on 2007-05-18
OK so it will be fairly easy. First, cd to the dir you extracted the tarball in, it should be called vmware-server-distrib and when you ls in it, you should get this :

```
[mfb@ana vmware-server-distrib]$ ls
FILES  bin  doc  etc  installer  lib  man  sbin  vmware-install.pl  vmware-vix

```

now, get the patched source for the vmon module :

```
wget http://fkraiem.free.fr/vmmon.tar
```

And copy it to the correct location :

```
sudo mv vmmon.tar lib/modules/source
```

Now run the installer again :

```
sudo ./vmware-install.pl
```

you're there :)

---

### Post by Pollywoggy on 2007-05-18
> **HymnToLife said:**
> OK so it will be fairly easy. First, cd to the dir you extracted the tarball in, it should be called vmware-server-distrib and when you ls in it, you should get this :

.....

you're there :)

Thanks, I will try it.

---

### Post by Bachstelze on 2007-05-18
By the way, the tarball you have is pretty old, current version is 1.0.3 so I'd grab it first if I were you (and yes, you can remove those packages).

---

### Post by Pollywoggy on 2007-05-18
> **HymnToLife said:**
> OK so it will be fairly easy. First, cd to the dir you extracted the tarball in, it should be called vmware-server-distrib and when you ls in it, you should get this :

```
[mfb@ana vmware-server-distrib]$ ls
FILES  bin  doc  etc  installer  lib  man  sbin  vmware-install.pl  vmware-vix

```

now, get the patched source for the vmon module :

```
wget http://fkraiem.free.fr/vmmon.tar
```

And copy it to the correct location :

```
sudo mv vmmon.tar lib/modules/source
```

Now run the installer again :

```
sudo ./vmware-install.pl
```

you're there :)


Something did not go well:
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-15-generic).  Even if the module were to
compile successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

---

### Post by Pollywoggy on 2007-05-18
> **HymnToLife said:**
> By the way, the tarball you have is pretty old, current version is 1.0.3 so I'd grab it first if I were you (and yes, you can remove those packages).

Maybe that is why it did not work.  I will remove this attempt and start with a newer tarball.

thanks

---

### Post by Bachstelze on 2007-05-18
No. It did not work because you do not have the headers for your current running kernel installed.

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

### Post by Pollywoggy on 2007-05-18
> **HymnToLife said:**
> No. It did not work because you do not have the headers for your current running kernel installed.

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

No, those are installed.

I had a newer VMware Server tarball in a different directory but I am downloading the latest one now and deleting the others.

---

### Post by Pollywoggy on 2007-05-18
Thank you for all the help and for the patch.  It's working now.

---

### Post by lawson23 on 2007-05-23
Ok I hope my last question but after installing I get an invalid username and password when trying to access vmware-server from a console.
> There was a problem connecting:
Login (username/password) incorrect

I have installed this fix:
Until [WWW] bug #115295 is fixed, edit /etc/pam.d/vmware-authd to read as follows:

    *

      #%PAM-1.0
      auth required pam_unix_auth.so shadow nullok
      account required pam_unix_acct.so
           



Any ideas?

---

### Post by lawson23 on 2007-05-24
Found some information with those experiencing the same but don't really understand if they figured it out.
[http://ubuntuforums.org/showthread.php?p=2716220](http://ubuntuforums.org/showthread.php?p=2716220)

---

### Post by 56seeker on 2007-05-26
After following all the advice in this thread I've managed to install VMserver on Ubuntu desktop; and it seems to run just fine.

However, I've two issues outstanding:

1) During the install I recieved error messagews about the program icon placement; and indeed I've no program icons on the applications menu. The consol does however start just fine if I type "vmware" into a terminal window. How do I make/get an icon for VMware on the application menu?

2) I can't access the web based administration tool: vmware-mui. I've tried the following:

[https://192.168.2.110:8333](https://192.168.2.110:8333)
[http://192.168.2.110:8333](http://192.168.2.110:8333)
[https://127.0.0.1:8333](https://127.0.0.1:8333)
[https://localhost:8333](https://localhost:8333)

All return Firefox can't establish a connection to the server at 

I'm a newcomer to Linux and Ubuntu in particular so any help will be very appreciated

I can see from "top" that vmware is running (as if having the console open wasn't enough!) but I'm not experienced to know if I'm missing anything such as a web server service or similar

---

### Post by lawson23 on 2007-08-07
Sorry for the delayed response 56seeker.

I'm also a linux newb.  I can't really answer your question though because I'm running the package as a server only without any desktop environment.

My issue is related to communicating to the server from a different box (I believe you are talking on the same box) using the console software only.

I hope someone here can help you out and maybe this bump will get you your response.

---

### Post by lawson23 on 2007-08-22
My username problem has been resolved with the help of this post:
[http://ubuntuforums.org/showpost.php?p=3226353&postcount=15](http://ubuntuforums.org/showpost.php?p=3226353&postcount=15)

---

### Post by s[_]spect on 2007-09-05
> **HymnToLife said:**
> 
now, get the patched source for the vmon module :

```
wget http://fkraiem.free.fr/vmmon.tar
```



Is this patch available somewhere else? I get 404 on the url quoted?
Any help appreciated

---

