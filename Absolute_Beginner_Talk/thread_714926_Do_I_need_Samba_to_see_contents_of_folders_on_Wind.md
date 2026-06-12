---
title: "Do I need Samba to see contents of folders on Windows machines?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by jstevans on 2008-03-04
Hi all, I'm new a Ubuntu and Linux, trying hard to get up to speed.  I have Ubuntu up and running on my Sony Z505 JEK laptop, not tons faster than its prior OS of Windows 2000 Pro but that's mostly due to a fairly slow CPU and the tiny amount of RAM the machine supports.  But, as an educational experience, this is fine.

When, on the Ubuntu laptop which is wired to the home network which I run as a workgroup, I try to see my Windows machines here's what happens:
[LIST]
[*]I click on "Places -> Network" in the main Ubuntu menu
[*]That opens up the network file browser which displays an icon for "Windows network"
[*]When I double-click on that icon the display changes to show an icon for "HOME" which is the name of my home network
[*]When I double-click on the "HOME" icon the window's display area clears, the machine churns for thirty seconds or so and eventually an error message appears that says "The folder contents could not be displayed"
[/LIST]

I've read a lot of other posts related to this topic and I often see Samba mentioned.  What I cannot figure out is whether I need Samba up and running on the Ubuntu laptop in order to see the contents of the folders on the Windows PCs connected to the network.

Bye the way - each of the five Windows machines on the network see each other and can browse the contents of all shared folders - no problems there.  So, I take that to mean the permissions and whatever else are set fine within the Windows PCs.

---

### Post by zerhacke on 2008-03-04
You don't need Samba.

You need the smbfs package, and then use the man pages on it to see how smbfs is used.  Smbfs will install two utilities, mount_smbfs and mount_cifs.  I would use cifs.

Then when you have smbfs installed you use the mount command or edit /etc/fstab and then sudo mount -a.

---

### Post by dstew on 2008-03-04
You only need Samba if you want to serve files from your computer, but not if you only want to see files on other computers.

---

### Post by jstevans on 2008-03-04
Thanks for the replies.  I understand that I need the smbfs package.  So, I went to Ubuntu's "Add/Remove" application but could not find it available.  I found SMB4K but that's for KDE and I'm on Gnome (the default, I believe, for Ubuntu).

Please forgive my not knowing this but - where do I get the smbfs package?

Thanks again.

---

### Post by Oldsoldier2003 on 2008-03-04
> **jstevans said:**
> Thanks for the replies.  I understand that I need the smbfs package.  So, I went to Ubuntu's "Add/Remove" application but could not find it available.  I found SMB4K but that's for KDE and I'm on Gnome (the default, I believe, for Ubuntu).

Please forgive my not knowing this but - where do I get the smbfs package?

Thanks again.
from a terminal
```
sudo apt-get install smbfs
```

---

### Post by js3862 on 2008-03-11
> **Oldsoldier2003 said:**
> from a terminal
```
sudo apt-get install smbfs
```


Hello, completely new to K/Ubuntu and the forums and I had been searching for a bit to find this answer.  I'm glad I did because I was honestly starting to get pretty discouraged.   ](*,)

I'm currently evaluating Kubuntu and PCLinux for use on the home computer.  I probably wouldn't have ever needed this package except for the fact that I have a Windows 2003 domain I use for testing and need to mount a share from the domain controller.  However, I was surprised that this package was part of the PCLinux distribution but wasn't part of any of the Ubuntu distributions.  Not a biggy, just thought it was a bit of a miss.

Also, I'm curious if anyone knows why this package would be available in Synaptic but not Adept.  I have downloaded and installed Synaptic on Kubuntu which is how I was able to find the package but, I'm wondering why since they are both sharing the same repositories the package wouldn't show up in Adept.

Thanks!

---

### Post by dwblas on 2008-03-11
> I'm curious if anyone knows why this package would be available in Synaptic but not AdeptThe repositories, that is /etc/apt/sources.list could be different in Ubuntu vs. KUbuntu, so it's not available to Adept.  Being a Synaptic user I would assume that Adept would also have an option in the pull down menus to enable extra repositories.  Also, if the sources.list file has changed in any way you would have to "reload" first, or download the lastest set of packages before any new package could be found.

---

