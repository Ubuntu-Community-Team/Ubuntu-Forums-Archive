---
title: "Vmware and sata drives..."
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-07-23
i just installed the vmware player and i boot in windows using that but for some odd reason it wont read my E:/ that contains all the music and personal files that i have.. how would i make it so i can read it ? i can read it perfect with ubuntu, kind of pointless though because thats why i got vmware is to use cs3 with my psd's. any ideas ?    its a sata drive btw... and the main drive is an ide drive...

---

### Post by nichipet on 2007-07-23
I believe it was suggested earlier to check with VMWare's forums at [http://www.vmware.com/community](http://www.vmware.com/community)

They would have a better idea of how to fix it. Have you searched Google or looked at VMWare's forums?

---

### Post by Likenota on 2007-07-23
ya i looked everywhere...

---

### Post by jkeyes0 on 2007-07-23
I think I understand what you're needing. You want to access your physical drive in a VMware session, right?

The easiest way is to install VMware server instead of player. It's still a free product, you just have to register on the VMware site to get a serial key to use (completely free), and add the Canonical commercial repo to your /etc/apt/sources.list file. [Here's]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html") a link to installing it.

Once you have it installed, add your WinXP machine to the inventory (open existing virtual machine), then edit the settings on it, and add a hard drive. When it asks whether you want to create a new one, tell it you want to use a physical hard drive. It will give you some error message, but should work if you choose the correct drive (not sure how your drives are mapped). I will test this when I get home, as I'm on WinXP myself at work.

Hope this helps!

---

### Post by Likenota on 2007-07-24
YOUR WONDERFUL DUDE!!!!!!! thank you... ill be sure to let you know if i got this working...

---

### Post by Likenota on 2007-07-24
umm.. it keep saying i have to uninstall a previous installation or something with uninstall.pl or something.. whats going on i dont have it installed. ?

---

### Post by nichipet on 2007-07-24
Does it reference vmware-uninstall.pl? Try in a terminal:

```
which vmware-uninstall.pl
```

For that matter, try the which command for the file it references, no matter what it is called. That will tell you where it is.

---

### Post by Likenota on 2007-07-25
it keeps saying theres a previous installation!!! ugh..

---

### Post by nichipet on 2007-07-25
A previous installation of what exactly? Can you copy/paste exactly what it says?

---

### Post by anewguy on 2007-07-25
You have to remove (uninstall) vmplayer before you can install vmserver, and vice-versa.  Try running the uninstall script, or since it is vmplayer, try using synapitcs package manager to do it.:)

---

### Post by Likenota on 2007-07-26
yes ive tried that why would i even be askin that im not that big of a noob. thanks for your help guys something soo simple yet for some reason its reading a previous installation..

---

### Post by anewguy on 2007-07-26
I guess you already know to look, but when I first installed Vmware player, and then wanted to install Vmware server, I didn't know about the uninstall script.  So I went through EVERY piece of the file system (as root) using the "explorer" and removed everything that had vmware, .vmware, etc..  You have to tell the "explorer" to show hidden files or you won't find them all.  It's a LOT of work that way, but it can be done - even I did it!:)

---

### Post by Likenota on 2007-07-26
umm the script still leaves vmware on the system..

---

### Post by anewguy on 2007-07-26
well, I hate to say it, but you may have to start exploring the file system like I did to find references to folders, etc., with names like vmware, .vmware, etc., then remove all of those and any files you find that are similar.  I wish I could remember just exactly where they all were to simplify you work, but it was one of those "I'm only doing this once!" kind of things.  If worse comes to worse, I suppose I could follow exactly what you did to install vmware player, then walk through deleting everything and see if I can come up with some kind of script or something.  This stuff is all new to me, also, but I know there should be a way in a command line to search for any file/folder with vmware in the name and delete it, but I myself don't have that knowledge right now.  I'll see what I can come up with........:)

---

### Post by nichipet on 2007-07-26
Try vm and then hit Tab twice. That may only find executables. Also try

```
locate *vm* | more
```

That will find everything that has vm anywhere in its name and the 'more' will keep it from scrolling off the screen.

---

### Post by anewguy on 2007-07-27
Here's what I just did (it took a while or I would have responded quicker):  I installed vmware player via synaptics, then did the update from the vmware site that vmplayer suggested when it ran.  I then did the following, then download vmware server and installed it.  Open a terminal window and try the following, then report back the results:

[COLOR="Red"] sudo rm /etc/vmware/vmnet1/dhcpd/*.*[/COLOR]

[COLOR="Red"]sudo rmdir /etc/vmware/vmnet1/dhcpd[/COLOR]

[COLOR="Red"]sudo rmdir /etc/vmware/vmnet1[/COLOR]

[COLOR="Red"]sudo rm /etc/vmware/vmnet8/nat/*[/COLOR]

[COLOR="Red"]sudo rmdir /etc/vmware/vmnet8/nat[/COLOR]

[COLOR="Red"]sudo rm /etc/vmware/vmnet8/dhcpd/*[/COLOR]

[COLOR="Red"]sudo rmdir /etc/vmware/vmnet8/dhcpd[/COLOR]

[COLOR="Red"]sudo rmdir /etc/vmware/vmnet8[/COLOR]

[COLOR="Red"] sudo rm /etc/vmware/*[/COLOR]

[COLOR="Red"]sudo rmdir /etc/vmware[/COLOR]

[COLOR="Red"]sudo rm /usr/bin/vm*[/COLOR]

Then go up to the top bar and click on [COLOR="Red"]Places[/COLOR] and select [COLOR="Red"]Home Folder[/COLOR]

When the File Browser opens it will be in your "home" folder.  Click on [COLOR="Red"]View[/COLOR] and then on [COLOR="Red"]Show HIdden Files[/COLOR]

Now just right click on the "[COLOR="Red"]vmware[/COLOR]" folder and select "[COLOR="Red"]Move To Trash[/COLOR]"

Now just right click on the "[COLOR="Red"].vmware[/COLOR]" folder and select "[COLOR="Red"]Move To Trash[/COLOR]"

Now go in to a terminal and (making sure you are in the correct folder!) "[COLOR="Red"sudo .vmware-install.pl[/COLOR]".  Please note, however, that configuration of VMWare Server in Ubuntu 7.04 (Feisty Fawn) will abort.  Please see [This Page"]("http://dfhzn.blogsome.com/2007/04/26/vmware-server-in-ubuntu-feisty-fawn/")  to install to 7.04.

When I did the above I got everything removed and VMWare Server installed.

If you want to run from your existing disk after you get VMWare Server installed, post back and I'll walk you through it.:)

---

### Post by RickKnight on 2007-07-27
I'm trying to do the same thing. I have Kubuntu Feisty and VMware Server. I want to use my WinXP partition as a physical image. Every time I try to make the image I get an error message saying the partition has changed and must be restarted. I can't get a successful finish to the job. It seems VMware doesn't yet support SATA drives as physical images, only SCSI and IDE. Some people have apparently found ways to make it work but so far none of them have worked for me. I ended up using the VMware COnverter make an image of the WinXP partition. I then copied this image to my Kubuntu partition and then used the VMware Server Console to mount the image. It works fine this way. The only problem I've had so far has been with Windows and Office activation. I've had to call MS twice to get activation complete.

If anyone does know a way to get SATA to work with VMware, I'd love to hear how to do it.

Hope this helps some,
Rick Knight

---

### Post by Likenota on 2007-07-30
ummm locate *vm* | more

i get a huge list of stuff... neways i deleted enough and ran the vmware-install.pl file.. and this is what i got...

i just hit enter..  whats a builder and where do i get that? i think thats the problem...



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

