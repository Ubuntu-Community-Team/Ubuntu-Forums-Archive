---
title: "Permissions to write to a folder"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by capera on 2007-10-08
In kind of a bind.

Very new to Linux and enjoying it. 

Problem: I have a dll file that I have on my desktop (linux - Ubuntu) and need to copy it to my /Windows/System32 folder. 

It will not let me. I tried to change the "Permissions" in Linux on the folder, to make it Read and Write.....but it says I do not own the folder and will not allow me to copy it.

Any suggestions.....as I need this dll file to be copied over and I should be able to.....just lost.

Help

---

### Post by PmDematagoda on 2007-10-08
It is most probable you have NTFS as the filesystem on your Windows partition and haven't installed NTFS read and write support for Ubuntu, just go to synaptic and install ntfs-config.

After installation just open ntfs-config which is found in Applications>System Tools and enable write support to internal NTFS volumes and there you are:).

---

### Post by shearn89 on 2007-10-08
I'm assuming you dual boot? Ubuntu can't by default write to ntfs file systems (aka windows) - you'll need to install the ntfs-3g drivers.

EDIT: beaten to it... PmDematagoda's advice seems like a better solution.

---

### Post by capera on 2007-10-08
I have installed NTFS-3g but when it installed, the options in that program did not list my old "C" drive as a possible drive to appy the new changes.....It listed my other partitions (drives). eg:  D: storage   E:Games 

The file I need to copy has to go to my old C: drive    /Windows/System32

When I try to change properties on the "System32 Folder" folder, it says :  

Owner: root

Group: root


and "Folder Access" below each of these titles  is grayed out. Also says.... "You are not the owner. so you cannot change these permissions.


**Actually......**as I try to change the permissions on ANY folder....ANY drive.....same deal. Maybe the NTFS-3g install was bad....or I did it wrong. Wow this is fun....  :popcorn:

Still could use any assistance that may help.

---

### Post by capera on 2007-10-08
> **shearn89 said:**
> I'm assuming you dual boot? Ubuntu can't by default write to ntfs file systems (aka windows) - you'll need to install the ntfs-3g drivers.

EDIT: beaten to it... PmDematagoda's advice seems like a better solution.

Do you have a URL to a working copy of the ntfs-3g driver?

---

### Post by capera on 2007-10-08
Gawd, I'm new to all this. 14 years Windoze experience means diddley in here.

I was able to download   NTFS-3g ......and save it to a folder but have no idea how to install it. 

Sorry for being so new..... all these years lookign for .exe or .com files to exicute and install.......now this.

Can someone tell me how to install this, now that i have the files.

---

### Post by PmDematagoda on 2007-10-08
> **shearn89 said:**
> I'm assuming you dual boot? Ubuntu can't by default write to ntfs file systems (aka windows) - you'll need to install the ntfs-3g drivers.

EDIT: beaten to it... PmDematagoda's advice seems like a better solution.

You can get it using synaptic. The wonders of Synaptic:).

P.S. Sorry for that capera, I forgot that ntfs-config requires ntfs-3g, really sorry.

---

### Post by capera on 2007-10-08
I cannot install all these downloadable links.

Like the last one....synaptic

I found the  link [http://download.savannah.nongnu.org/releases/synaptic/synaptic-0.47.tar.gz]("http://download.savannah.nongnu.org/releases/synaptic/synaptic-0.47.tar.gz")

and all it does is give me the ability to download and save to a directory. That is when I get stuck.....how do I download it, once I have the files?

---

### Post by Griffiss on 2007-10-08
Capera,

Open a terminal and type in ```
gksudo nautilus
```then enter. 

It will bring up a file browser with root permissions. If NTFS-3g is correctly installed then you will be able to write to your windows folder.

Edit: useful info on permissions: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Griff

---

### Post by PmDematagoda on 2007-10-08
Ok, now open up the Synaptic Package Manager in System>Administration.

Once you open it, search for the packages with "ntfs-3g" in their name.

Once you get the names, install:-

ntfs-config

ntfs-3g and

libntfs-3g2

There you go:), you can now make the necessary changes using the GUI ntfs-config found in the location given by me earlier.

---

### Post by capera on 2007-10-08
> **Griffiss said:**
> Capera,

Open a terminal and type in ```
gksudo nautilus
```then enter. 

It will bring up a file browser with root permissions. If NTFS-3g is correctly installed then you will be able to write to your windows folder.

Edit: useful info on permissions: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Griff

Did this.....and the only drive that is avail is "filesystem"

According to install program, I have ntfs-3g installed......but I cannot change permissions on any drives.

---

### Post by PmDematagoda on 2007-10-08
Did you make the changes on NTFS-config?

---

### Post by shearn89 on 2007-10-08
> **capera said:**
> Gawd, I'm new to all this. 14 years Windoze experience means diddley in here.

I was able to download   NTFS-3g ......and save it to a folder but have no idea how to install it. 

Sorry for being so new..... all these years lookign for .exe or .com files to exicute and install.......now this.

Can someone tell me how to install this, now that i have the files.

It doesn't mean nothing, but it comes close! Its just a different way of working, once you get used to it, its much easier!

For installing help, check here:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Edit: "filesystem" is like "my computer". If you go into it, the windows drives should be in a folder called "mnt" if they have been mounted. If not, tell us, and we'll show you how to do it.

---

### Post by Griffiss on 2007-10-08
Your windows folder will be in filesystem if it is mounted. Also, if you use the gksudo command you won't need to change permissions in order to write to the folder.

Maybe this will also help you: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by capera on 2007-10-08
Thanks everybody..... I need to go do some reading. Really appreciate you assistance.

Dave

---

