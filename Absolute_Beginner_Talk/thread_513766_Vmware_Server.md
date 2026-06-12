---
title: "Vmware Server"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-07-30
why does it give me this error when i try to install vmware server.... ? whats a compiler im confused.. please answer my question it always takes forever to get some responses. seeing how many people are here the responses should be a bit quicker. ;).
```

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

---

### Post by anewguy on 2007-07-30
(a) did you remove vmware-player first?

(b) why are you installing source that must be compiled?  You can download vmware-server for free from vmware.com.  All you have to do is register (free) to receive a registration number (free).

Try to remove what you've done, then go in to synaptic package manager, enable the ubuntu commercial repository, then just install vmware-server (be sure to get the registration key).

It might be that going through the synaptic package manager to install it will also clean up the old vmware stuff you have.:)

---

### Post by Likenota on 2007-07-31
umm no. did all that. and of course i uninstalled it. i suppose i will keep on trying until couple days later when someone else responds to this thread and i end up figuring it out like every other thread or majority of posts / threads ive made.

---

### Post by forestpixie on 2007-07-31
you might need to also ensure that any vmware folders are gone as well before you try to reinstall

[http://ubuntuforums.org/showthread.php?t=445571&page=2](http://ubuntuforums.org/showthread.php?t=445571&page=2)

---

### Post by Likenota on 2007-07-31
i already did that through the console... ;) rm -r vmware  i now get an error when i try to install the vmware server... like i stated before..


```
In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

---

### Post by spam10707 on 2007-07-31
I had a similar problem when I installed VM-Ware Server.  A friend of mine gave me this link, let me know if this helps: [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

---

### Post by anewguy on 2007-07-31
If you do the locate vmware  and remove all the files and folders, then you should be able to do the following.  I found this on the net somewhere but I haven't been able to find it again to point you to the link:

- enable the commercial repository in synaptics package manager
- locate, click for installation and apply   for vmware-server
- exit the package manager
- edit your /etc/vmware/pam.d/vmware-authd file to look like this:

#%PAM-1.0
auth       sufficient       %pamdir%/pam_unix2.so shadow nullok
auth       required         %pamdir%/pam_unix_auth.so shadow nullok
account    sufficient       %pamdir%/pam_unix2.so
account    required         %pamdir%/pam_unix_acct.so

That's all I did and I've been able to use server fine.  When I first tried server a couple of weeks ago, I went through the same hassles of trying to get rid of vmware-player and any other hanging-on vmware files/directories.  Then I followed the long way to install as shown by the link earlier in this post.  I had to reinstall Ubuntu due to a screw up by me, and found these instructions much much simpler for getting vmware-server to work in Ubuntu 7.04.

BTW - I don't remember if in your previous post or in this one if you said what your hardware configuration was, so, could you tell us if you are using scsi?

I know it's frustrating - I, along with many others, have gone through the same thing you are going through.  You really should try what I've said, even though you don't seem to want to.

I will be contacting an individual who is an expert on the virtual machines and seeing if I can get him to post something for you here.:)

---

### Post by Likenota on 2007-07-31
WOW thank you!!! thats waht im talking about guys thanks soo much lemme try this out wish me luck.. i really really hope i can get it to work.. o and i got ide and sata drives..

---

### Post by anewguy on 2007-08-01
Contacted the expert my personal messaging - he said it looks like the problem is solved, so I guess if you follow the instructions you will HOPEFULLY be able to get things running.:)

Please post back with any more problems or if you get it to work!!:)

We are rooting for you!

---

### Post by Likenota on 2007-08-01
umm at least i managed to uninstall vmware player .... and well umm....

To tell you guys the truth this is really startin to piss me off i try to install the vmware server and it gives me the error
```

E: vmware-server: subprocess post-installation script returned error exit status 1

```

the vmware server is there under applications system tools but when i click it, doesnt work.. 
also the vmware-authd file already has that stuff in there...  im soo confused and getting more and more closer to failure forever... i really want this to work.

idk if this will help but everytime i try to run that vmware-any-any-update-109 i get this error:

```
Unable to find the database file (/etc/vmware/locations)
```

same thing when i run this command...

 sudo vmware-config.pl

---

### Post by liverpoolfc2 on 2007-08-01
Just started using ubuntu, so just getting the hang of things, installed vmware server today so i can get use XP without all the rebooting. This is how I managed to do it.

1. sudo kate /etc/apt/sources.list  ( BTW Kate is Kubuntu change to what you use should work the same)

2. add the following line save and exit

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

3. Now you need to update Ubuntu Source List using the following command

sudo apt-get update

4. sudo apt-get install vmware-server vmware-tools-kernel-modules

Now during my install I got this

WARNING: you don't have an init script for the original
inetd anymore! You may need to reinstall the netkit-inetd
package to get it back.

So all I done was

Sudo apt-get netkit-inetd

then I done

Sudo apt-get install vmware-server

I then went with default settings as vmware was installing and everything worked perfectly.


One other thing I tried the package install and it just would not work for me, vmware gave a complaint about another version of vmware being installed, so I just cd to the vmware folder I was using and used the uninstall option. Then everything went perfectly.

As I said I'm really new to this, but in all honestly i didn't find it to difficult to work out.

Good Luck.

---

### Post by Likenota on 2007-08-01
i was anxious to try this ... i really thought it would work but this command didnt....

Setting up vmware-tools-kernel-modules (2.6.20.16.28.1) ...
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


okay wjhat!? i dont ujnderstand this why wont it let me do that it does that with toher things too like when i try to do sudo apt-get install vmware-server..


i did that and now i see the server icon in the system tools menu but when i click it it doesnt work nor when i go to terminal and type vmware it doesnt boot up.

---

### Post by anewguy on 2007-08-01
Were you using the dpkg command to install things, apt-get, or the synaptics package manager?  Also - I forgot about the inetd thing - I did have to install that first.

When I installed using the "long way", including the patch, I had problems as I have mentioned earlier.  When I installed from the synaptics package manager (after removing everything again), I didn't have any problems.

I do have a suggestion for you for something to try first:

Since the server shows under applications/system but doesn't start, I wonder if you have had a permissions problem along the line.   Try opening a terminal window and typing:

[COLOR="Red"]sudo vmware[/COLOR]

If it starts then, it would indicate a permissions problem - perhaps something to do with the groups management.  I'm trying to remember, but I believe you have to add yourself to the group "disk" or "disks" for one of the vm's - I just don't remember if it vmware or virtualbox.

Try the sudo thing and let us know what happens.

BTW - how much stuff do you have in Ubuntu so far - i.e., would it be a disaster if we asked you to remove Ubuntu and reinstall it s we can start the vmware-server installation completely on a raw installation of Ubuntu? (You can have your sound, video, wireless, etc., working, just don't do anything with any vm product after you reinstall until you post back here). 

I know it's a big hassle removing things and reinstalling, believe me we've all been there (some of us - read "me" in this case!:) - more than once!   We will help you get this working, just try to hang in there.  We really are familiar with the frustration (I think almost any one who is relatively new to Linux gets that frustration at one point or another, but it does get better!!).

Since you have sata, are you installing to it or to IDE?  Is this a dual-boot system or just Ubuntu?  Does the system boot from the IDE or sata?   Thanks for those answers as well, as I think it can make a difference depending on what you are doing.

Hang in there - we will get it one way or the other!:)


EDIT:   I checked my userid and it doesn't appear I am in any group of "disks" or "disk" or even "vmware", so I'm guessing that IF it's permissions it at least won't be that.   Sure hope you don't mind me keep answering - I went through the same hassles but I sure like vmware-server now that it is installed and working, and I'd like to think we can get you there as well!   I've even set up other vm's in vmware-server  (currently I have Windows XP and also one for Fedora) so I can try out other versions of Linux, etc. -it's kind of fun because you don't have to burn installation CD's since you can install from ISO images on your hard drive!

---

### Post by Likenota on 2007-08-01
```
likenota@likenota-desktop:~$ sudo vmplayer
Password:
sudo: vmplayer: command not found

```


i apperciate all your help. very nice to see people helping others...


anyways i got ide with windows xp on it and ubuntu doing dual boot. then i have another drive that has all my music and personal files.. this drive being a serial ata drive.  umm also uninstalling ubuntu just for one program! ? ugh.. i got compiz working and i dont even know what i did to get that working, besides that beryl site is down and well i cant get that without the command or w,e and idk that seems a hassle over one program.. whats the diff between server and vmplayer? i just want vmplayer to read my sata drive ! ugh. welll is there any way if i can use vmplayer i can access my drive ?

i want something like this really bad im in love with this youtube video... i like how it has profiles when he double clicks thee icon and he can auctually move   WINDOWS FILES AND LINUX FILES! coolness.
[http://youtube.com/watch?v=yT8YiWX43uU](http://youtube.com/watch?v=yT8YiWX43uU)

---

### Post by anewguy on 2007-08-01
Hi again,

VMWare-Server allows you to create as well as play virtual machines.  VMWare-Player on the other hand can only play a virtual machine, it does not allow you to create or edit it, so you normally have to have a copy of a pre-configured virtual machine, and normally these are going to require some editing to get to work depending on your system.

Are you trying to use a virtual machine with your IDE drive installation of Windows as the physical disk, or are you wanting to create a virtual disk to install Windows into and then boot your virtual machine with it?

If you want to copy files back and forth between Windows and Linux, I know you can already do that if the Windows file system is fat32, for example.  I have seen references on this forum that you can do the same with Windows NTSF as well when you install some package or patch.  I think that for the time being it isn't "officially" supported by Ubuntu itself.

Since it doesn't know the "vmware" command when you tried it with "sudo", I can only assume it really didn't install.  If it shows on your applications menu, I would use add/remove in the applications menu and just uncheck it there so it doesn't show on your menu right now.

Since it sounds like you already have a lot of stuff in Ubuntu, then if none of the links for installing VMWare-Server have worked, I would do the difficult job of doing the "locate vmware" and manually deleting (you'll need either root access to the gui file browser,  or else you'll need to use a terminal and "sudo" everything.  Once "locate vmware" not longer shows anything, then be sure to delete the "vmnet" files as well.  Hopefully "locate vmware" and "locate vmnet" will then return empty.  When you get to there, let us know.

You probably also know that VirtualBox is free, and we could always try to get what you want working in that if all else fails.:)

Sorry there doesn't seem to be an easy way for you!:)

---

### Post by anewguy on 2007-08-02
Hmmmmm........did you try mounting the sata drive?:)

---

### Post by Likenota on 2007-08-02
no i didnt try mounting the sata drive.. what does that mean?.... i have a virtual machine already setup for the windows xp thats on my ide drive i have dual boot and i can run my existing installed windows xp on the vmware player... the reason i needed vmware server was kuz i want to be able to read my serial ata drive in vmware... and i thought that if i had vmware server that i could do something to make it read it.  my linux works and reads the sata drive perfect.

---

### Post by anewguy on 2007-08-02
Okay, now I see what you want to do.  If you have Windows working in a VM, then what you want to do is add the sata drive to your vm.  Indeed, with VMWare-Server that would be easy.  Is the Windows VM still working or is that just sitting there since the problems with VMWare-Player/VMWare-Server?   If you remove all of vmware, you could still save the vm-specific files first and restore them after you get everything straightened out, or you can just recreate that VM simply with VMWare-Server.  I really do think you're going to have to do the deleting the hard way:

-  in a terminal,   "locate vmware"

- for each folder of    somepath/vmware/restof path:

- sudo rm -r somepath/vmware

- do the locate vmware again

- using sudo, rm all the remaining files

If you set down to do this it should only take you maybe 20 minutes or so.

Once you've done that, post back and we'll install VMWare-Server via the repositories.:)

---

### Post by anewguy on 2007-08-03
Have you seen [[COLOR="Red"]this?[/COLOR]]("https://help.ubuntu.com/community/VMware/Server#head-4e9a466bc9b9bb8a16513719d0dd72fe126bb2f5")

The troubleshooting section says:

....................

Troubleshooting

    *

      Error: When I try to install VMware Server I get the following error message:
          o

                A previous installation of a VMware product has been detected.
                If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before proceeding.
                If it was installed through Ubuntu, you must purge (completely remove) the old package.
               

            Solution: First of all, unsure that you "Completely Removed" vmware-player/vmware-server and all its modules. To unsure that, run the following command:

                sudo aptitude purge vmware-server vmware-player vmware-tools-kernel-modules
               

            If you still keep getting the above error, run the following command:

                sudo rm -r /etc/vmware*
               

            Source: [WWW] [http://ubuntuforums.org/showthread.php?t=491854](http://ubuntuforums.org/showthread.php?t=491854)

.....................


Maybe you can try that, then try what it says at the beginning to install to 7.04:


.....................

Installation and Quick Start

    *

      Ubuntu 7.04 (Feisty Fawn)

From Ubuntu packages

   1.

      Get a serial number by registering (for free) at [WWW] [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)
   2.

      Add the universe, multiverse, and commercial repositories to your Ubuntu 7.04 install [WWW] Directions.
   3.

      Uninstall vmware-server if it is already installed according to the section in this document titled "Transitioning from a Source Install."
   4.

      Install the vmware-server package
   5.

      Until [WWW] bug #115295 is fixed, edit /etc/pam.d/vmware-authd to read as follows:
          *

            #%PAM-1.0
            auth required pam_unix_auth.so shadow nullok
            account required pam_unix_acct.so
                 

   6.

      Start the remote access console by going to Applications > System Tools > VMWare Server Console in the menus (or run vmware from the command line). From there you will be able to access vmware servers locally or remotely, and create/open VMware virtual machines. Login with your regular username and password.

For troubleshooting see the [WWW] troubleshooting section in this document.


....................


Maybe this will help??:)

---

### Post by bengood24 on 2007-08-04
Apparently there is a header file with some extra commas in the tarball from the vmware site. Check this out: [http://ubuntuforums.org/showthread.php?t=506743](http://ubuntuforums.org/showthread.php?t=506743)

---

### Post by anewguy on 2007-08-04
I installed (read as "my latest install") VMWare-Server using the directions as in my previous post (i.e., getting from the repositories) and everything went smooth.  No hassles, no aborts.

---

### Post by rockstar82 on 2007-08-04
There is a patch.

[http://www.go2linux.org/node/30](http://www.go2linux.org/node/30)

---

### Post by anewguy on 2007-08-04
You don't need the patch if you follow the thread I posted showing how to install it Feisty, at least I don't remember putting it in when I did my last install.:)

---

### Post by Likenota on 2007-08-06
okay god damn finally i got it to install!!! okay now how do i go about putting the drive ?

---

### Post by anewguy on 2007-08-06
Run the server, then either open an existing vm or make a new one.  When doing so, chose to add a device of type disk and you should be able to find the extra disk from there.

Glad you got things uninstalled and the server installed - that's a big step for this thread!:)

Post back if you have questions, problems, and if you get it to work.

---

### Post by Likenota on 2007-08-07
ya well im totally confused on how i go abbout and adding the new drive...? i got it to run in the virtual machine no problem. another question is there a way to make it so i can drag and drop files from winxp and linux ,, ?  like this video...  [http://youtube.com/watch?v=yT8YiWX43uU](http://youtube.com/watch?v=yT8YiWX43uU) (p.s. if you can give me a song name of that song id be amazed!_)

---

### Post by anewguy on 2007-08-07
Since you have VMWare-Server installed now, when you open VMWare Server instead of running your virtual machine, click on the edit this virtual machine instead.  Once the screen comes up, click on add, the select disk then it should let you select the disk you want to add.  Close out of the edit and just start the virtual machine.

As far as dragging and dropping files from XP to Ubuntu, as long as the drive is mounted in Ubuntu you should be able to do that now.  As an example, I can just open up the file browser (Places on the top menu bar) and after it is open I click on my Windows drive, then I can just drag a file off that to my desktop.  Now, if I had 2 file browsers running I could drag from Windows to a given place in my Ubuntu file system.  If you want to drag back to Windows, you first need write access to the Windows drive/partition.  For me that is not automatically there, and I've read some posts on this forum for how to enable write access to a NTFS partition (if it is FAT32 there is no problem, as I already do that).

The point I would like to make here is you don't have to have Windows running in a virtual machine just to drag and drop files - you can do that in Ubuntu only as long as the drive/partition is mounted (and in rewrite/write if you want to drag files there).  I don't have a clue what happens in regards to file types - things like mp3, etc., I would assume should be ok, but anything with a Linux file format won't work in Windows, and most Windows file formats won't work in Linux.:)

---

### Post by anewguy on 2007-08-07
BTW - if you don't already know, that video shows someone who is running beryl or compiz - hence the cube they rotate.  

What do I get for telling you that the song is "One Love" by U2.  I'm not sure, but it might be the version they did with Mary J. Bilge (sp??), but that's the song for sure.  Do a Yahoo search on 

U2 one love

And a link will show where you can go and play parts of each version.:)

---

### Post by Likenota on 2007-08-08
wow thank you... igot everything running.. doing good! :) thanks.. but i hate to ask once again ive been having trouble with the sound in the virtual system i will work on that but apperciate all the help.. hmm also is it safe to leave the virtual machine running all night ?i have some stuff i usually download and it be cool just to download through windows but be in linux.

---

### Post by anewguy on 2007-08-08
You know, I've never tried leaving a vm of Windows on that long.  I would think it would work if you do a few things first in Windows:  disable any time outs (such as you might find in the power section of Windows.and maybe even the screen saver.  I think I would consider doing the same in Ubuntu while you are doing this in the VM.  You would sure hate (and I don't know what would happen) if one timed out.

Also, for sound, I remember something simple for enabling it (I think when you edit the virtual machine you change the sound device to something like dlp or some such set of initials).  If I find it again I'll let you know.  I have temporarily removed my VM stuff to do some other "work"  (read playing around), but plan to reinstall it all in the next week or so.:)

Glad you got everything where you wanted it.  I know it was a lot of work, but having been there before (more than a few times no less) for this same problem, I knew if you hung in there we'd get things working.:)

Not bad that a fifty+ year old would know the song, huh??

---

### Post by bluevoodoo1 on 2007-08-11
Thanks, this worked very well.


> **liverpoolfc2 said:**
> Just started using ubuntu, so just getting the hang of things, installed vmware server today so i can get use XP without all the rebooting. This is how I managed to do it.

1. sudo kate /etc/apt/sources.list  ( BTW Kate is Kubuntu change to what you use should work the same)

2. add the following line save and exit

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

3. Now you need to update Ubuntu Source List using the following command

sudo apt-get update

4. sudo apt-get install vmware-server vmware-tools-kernel-modules

Now during my install I got this

WARNING: you don't have an init script for the original
inetd anymore! You may need to reinstall the netkit-inetd
package to get it back.

So all I done was

Sudo apt-get netkit-inetd

then I done

Sudo apt-get install vmware-server

I then went with default settings as vmware was installing and everything worked perfectly.


One other thing I tried the package install and it just would not work for me, vmware gave a complaint about another version of vmware being installed, so I just cd to the vmware folder I was using and used the uninstall option. Then everything went perfectly.

As I said I'm really new to this, but in all honestly i didn't find it to difficult to work out.

Good Luck.

---

### Post by anewguy on 2007-08-21
Glad you got it to work, bluevoodoo1, but as I mentioned in my previous posts in this thread, and I think this is important for any one new to VMWARE, if you follow the post I mentioned you will not get the error about the inetd or xinetd.  Once you have the commercial repository enabled, you merely run synaptics package manager, select vmware server for installation, and it will automatically pickup any dependencies - i.e., you don't have to add anything.  All you do afterward is merely do the edit mentioned - it completely replaces the existing file.  I have done this MANY times with 7.04 and never had any problem.  No extra packages to add, no dependencies to get, no patch needed.  Just simply follow the instructions in the link.  It is extremely easy, and takes so very little effort  (or for that matter, knowledge).:)

---

