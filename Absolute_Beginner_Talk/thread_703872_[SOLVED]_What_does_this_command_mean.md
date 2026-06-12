---
title: "[SOLVED] What does this command mean?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by DingsBumps on 2008-02-21
I am currently following a guide to install the 8.2 catalyst control center on ubuntu ([here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually")), but I have have a problem with: 

> ```
sudo dpkg -i xorg-driver-fglrx_8.455.2-0*.deb fglrx-kernel-source_8.455.2-0*.deb fglrx-amdcccle_8.455.2-0*.deb
```

    * Note: If you have a 64 bit install, the above dpkg command will likely complain that "Errors were encountered while processing: fglrx-amdcccle". This is because of a dependency of the amdccle package on 32 bit libraries. If you receive this error, issue the following command after the above dpkg command, which will force the installation of all of the 32 bit dependencies, and then the amdccle package: 
```

sudo apt-get install -f

```

What do I do with the second command? Where do I put it? Just running it after the first one does nothing (At least I think they don't, cause further instructions in the guide don't work)

---

### Post by ace007 on 2008-02-21
the dpkg command is an install command for the files *.deb that are listed.  They should be "depackaged" or installed with the dpkg command.  Whatever they will install will not work if launched if they're dependencies are not present.  So the sudo apt-get install -f command will search for any dependencies that aren't installed and install them.  The command should be run in the terminal after the dpkg command has finished,

---

### Post by r4ik on 2008-02-21
Try,

sudo dpkg -i xorg-driver-fglrx_8.455.2-0*.deb fglrx-kernel-source_8.455.2-0*.deb fglrx-amdcccle_8.455.2-0*.deb && sudo apt-get install -f

Just copy and paste in the terminal.
Hope it helps.

Good luck !

---

### Post by GSF1200S on 2008-02-21
> **DingsBumps said:**
> I am currently following a guide to install the 8.2 catalyst control center on ubuntu ([here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually")), but I have have a problem with: 



What do I do with the second command? Where do I put it? Just running it after the first one does nothing (At least I think they don't, cause further instructions in the guide don't work)


The second command is telling APT (your package manager) that it needs to fix all dependency issues for any packages currently not configured properly. The first command is the CLI version of the Gdebi Package installer. Can you post a reply with the exact error message from the terminal so we can help you?

You could try navigating to the .deb package in your home folder and installing it with Gdebi, as it should do dependency hunting for you...

---

### Post by DingsBumps on 2008-02-21
This is the exact output:
```
marc@marc-desktop:~$ sudo dpkg -i xorg-driver-fglrx_8.455.2-0*.deb fglrx-kernel-source_8.455.2-0*.deb fglrx-amdcccle_8.455.2-0*.deb 
dpkg: error processing xorg-driver-fglrx_8.455.2-0*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.455.2-0*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.455.2-0*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.455.2-0*.deb
 fglrx-kernel-source_8.455.2-0*.deb
 fglrx-amdcccle_8.455.2-0*.deb
marc@marc-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
marc@marc-desktop:~$ 

```

@ace007: Running the command right after does nothing (see above)
@r4ik: Running the commands together produces the same result as only running the first command alone.

> 
You could try navigating to the .deb package in your home folder and installing it with Gdebi, as it should do dependency hunting for you... 
How can I try this?

---

### Post by r4ik on 2008-02-21
> **GSF1200S said:**
> The second command is telling APT (your package manager) that it needs to fix all dependency issues for any packages currently not configured properly. The first command is the CLI version of the Gdebi Package installer. Can you post a reply with the exact error message from the terminal so we can help you?

You could try navigating to the .deb package in your home folder and installing it with Gdebi, as it should do dependency hunting for you...

I think you have got the better solution here, thanks.

---

### Post by DingsBumps on 2008-02-21
THIS POST IS RESOLVED: SEE LATEST EDIT

> You could try navigating to the .deb package in your home folder and installing it with Gdebi, as it should do dependency hunting for you...
[QUOTE]I think you have got the better solution here, thanks. [/QUOTE]

How can I find the .deb package. Is it hidden (can you do this in ubuntu like you can in Windows?). I open my home folder (from that places menu) but there are definitely no .deb files, only folders and the original .run file used to create the .deb packages.

Now that I read what I just wrote, it seems possible that I never created the packages correctly. I'll check that.... and yep, theres my problem. Running the command to create the .deb packages gives me an error!

```
marc@marc-desktop:~$ sudo sh ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.Xw5929
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.455.2....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Resolving build dependencies...
./packages/Ubuntu/ati-packager.sh: 311: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/fileJEQRYy': not found
Unable to resolve  ia32-libs.  Please manually install and try again.
Removing temporary directory: fglrx-install.Xw5929

```

If someone could explain what that means, or how to fix it (even better), that would be great.

Edit: and of course, I open a new terminal and just run it without the sudo before the command, and a little window opens up and starts DL'ing the dependencies :) . Very nice

---

### Post by DingsBumps on 2008-02-21
Final post, issue resolved.
The problem was that I had never built the .deb packages. I don't really understand why I hadn't (did i skip the step? did the command run wrong? etc.), but after properly running it, the rest of the steps went silky-smooth. 

AKA: I made a stupid mistake.

---

### Post by r4ik on 2008-02-22
Never mind you fixed it nice to know :)

---

