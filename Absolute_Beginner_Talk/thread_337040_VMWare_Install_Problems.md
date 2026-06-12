---
title: "VMWare Install Problems"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-01-12
[B]I HAVE RESTRUCTURED THE POST, I HAD A MAJOR ISSUE WITH VMWARE SERVER AND GOT ERRORS SUCH AS:
Unable to get the last modification timestamp of the destination file /etc/vmware/ssl/rui.key.

If this applies to you, don't worry, this solution has worked for me, and now for several others, and also added is a solution from btmspox - I don't run the 64bit version, but that solved an issue he had.
[/B]

PROBLEM 1:
```

**Error code returned:**
Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.

Execution aborted.

```
Solution:
```

sudo touch /etc/vmware/ssl/rui.key
sudo touch /etc/vmware/ssl/rui.crt

```

PROBLEM 2:
```

**Error Code returned:**
Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  XXXXX-XXXXX-XXXXX-XXXXX
sh: /usr/lib/vmware/bin/vmware-vmx: not found
The serial number XXXXX-XXXXX-XXXXX-XXXXX is invalid.

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:

```
Solution:
```

sudo apt-get install ia32-libs
sudo /usr/bin/vmware-config.pl

```

And btmspox's fixes:

PROBLEM 3:
```

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

```
Solution (AS FOR MY SECOND PROBLEM):
```

sudo apt-get install ia32-libs

```

PROBLEM 4:
```

Unable to get the last modification timestamp of the destination file /etc/vmware/ssl/rui.key.

**From the vmware-config.pl examination:**
tech@db3:/usr/lib/vmware/bin$ ldd openssl 
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7f17000)
        libc.so.6 => /lib32/libc.so.6 (0xf7de3000)
        /lib/ld-linux.so.2 (0xf7f22000)


tech@db3:/usr/lib/vmware/bin$ ./openssl 
-bash: ./openssl: No such file or directory

```
Solution:
This was solved by btmspox via:
```

sudo apt-get install libc6-i386

```

Well there you go, everything tidied up to the first post so you don't have to go through all the issues I had while solving the problem. Should you want to/need to see some of the extra posts, including btmspox's post, do go through the rest of this thread.

Hope it continues to be helpful til whatever causes this problem is fixed.
Il

---

### Post by Bachstelze on 2007-01-12
Didn't you say you were running Win XP in your virtual machine ? If so, all you need to do is to select "Install VMware tools" in the VM menu, while WIndows is running.

---

### Post by jvc26 on 2007-01-12
No no different person. My issue is getting the whole VMWare server to install in the first place, which is currently throwing up the above error at me (I've had a right nightmare with this programs install, it worked the first time, then died when I updated (wouldnt let me reconfigure) and now its not letting me reinstall!
Thanks for help,
Il

---

### Post by jvc26 on 2007-01-13
Hey there anyone got any ideas?
Il

---

### Post by fsando on 2007-01-13
Just an idea:
delete the .vmware folder in your $HOME folder (/home/your name/.
It starts with a period which makes hidden - in nautilus you go to **view** menu and change to **show hidden files**. It worked when I had troubles reinstalling. 
I believe you could do from a console:
```
rm /home/your name/.vmware
```Also delete vmware folder in /usr/lib/.
Hope it helps

---

### Post by jvc26 on 2007-01-13
Hi there thanks for the advice,
The sudo ./vmware-install.pl removed that entry, but went and removed the one from /usr/lib myself. However, on a reinstall I once again get this error:
```

The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.

Execution aborted.

```
Any other ideas?
Il

---

### Post by Bachstelze on 2007-01-13
Have you tried running the uninstall script ?

```
sudo ./bin/vmware-uninstall.pl
```

---

### Post by stijn_pol on 2007-01-13
Did you install ssh and openssh-server?
( sudo apt-get install ssh openssh-server )
For vmware server: check this guide: [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

---

### Post by jvc26 on 2007-01-13
> 
Did you install ssh and openssh-server?
( sudo apt-get install ssh openssh-server )
For vmware server: check this guide: [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

From that article:
> 
If you have another computer available, install ssh-server and use a ssh client like putty to access the server remotely; copying and pasting the commands below is easier than typing them out.

I dont have another computer available :)

> 
Have you tried running the uninstall script ?

Of course, I have installed and uninstalled several times now trying to fix this.

I have since looked at [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server) and put on the packages which it said I needed (some of which I didnt have before) However, once again my good friend comes back to haunt me:

```

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.

Execution aborted.


```

I'm also not the only one to have these problems by the looks of it:
[http://www.vmware.com/community/thread.jspa?threadID=67628&tstart=0&messageID=549781#549781](http://www.vmware.com/community/thread.jspa?threadID=67628&tstart=0&messageID=549781#549781)

Thanks for the help... any other ideas?
Il

---

### Post by jvc26 on 2007-01-13
Right through a random mission I managed to get the next bit sorted:
via:
```

sudo touch /etc/vmware/ssl/rui.key
sudo touch /etc/vmware/ssl/rui.crt

```
Then the installer works a bit more, getting me to the step:
```

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  XXXXX-XXXXX-XXXXX-XXXXX
sh: /usr/lib/vmware/bin/vmware-vmx: not found
The serial number XXXXX-XXXXX-XXXXX-XXXXX is invalid.

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:      

**Please note, XXXXX-XXXXX-XXXXX-XXXXX is not my serial, I just put that in for this post.**

```

Note:: There is a file at /usr/lib/vmware/bin/vmware-vmx so not sure why its throwing errors at me.
What next? Any ideas?
Il

---

### Post by jvc26 on 2007-01-13
Done a few searches on vmware-vmx and tried to open it - not having any of it, and the google search returns are cryptic to say the least or apply to ubuntu hoary! Anyway... any ideas?
Thanks again,
Il

---

### Post by jvc26 on 2007-01-13
Bingo! I have the issue solved. If anyone wants to know how I got round these problems here it is:

PROBLEM 1:
```

**Error code returned:**
Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.

Execution aborted.

```
Solution:
```

sudo touch /etc/vmware/ssl/rui.key
sudo touch /etc/vmware/ssl/rui.crt

```

PROBLEM 2:
```

**Error Code returned:**
Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  XXXXX-XXXXX-XXXXX-XXXXX
sh: /usr/lib/vmware/bin/vmware-vmx: not found
The serial number XXXXX-XXXXX-XXXXX-XXXXX is invalid.

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:

```
Solution:
```

sudo apt-get install ia32-libs
sudo /usr/bin/vmware-config.pl

```

And there you go, all works now :) Hope that helps anyone with the same problem :)
Il

---

### Post by dughutch on 2007-03-21
Bump.

Thanks for the excellent work.  Suffered under same problems... utilized your suggestions and everything is now working.

Thanks again for the strong work!

---

### Post by btmspox on 2007-04-16
```
Unable to get the last modification timestamp of the destination file /etc/vmware/ssl/rui.key.
```

I looked at vmware-config.pl and saw it was running openssl, but noticed it was from it's own libdir.

```
tech@db3:/usr/lib/vmware/bin$ ldd openssl 
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7f17000)
        libc.so.6 => /lib32/libc.so.6 (0xf7de3000)
        /lib/ld-linux.so.2 (0xf7f22000)


tech@db3:/usr/lib/vmware/bin$ ./openssl 
-bash: ./openssl: No such file or directory

```

/lib/ld-linux.so.2 didn't exist. I'm on amd64 platform. 

```
 sudo apt-get install libc6-i386
```
solved that problem. At this point another bug in vmware-config.pl was corrected that I was ignoring, and it told me about some missing libraries when I first ran it, whereas before it said:

```
tech@db3:/usr/bin$ sudo ./vmware-config.pl 
/usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory
ldd: /lib/ld-linux.so.2 exited with unknown exit code (127)

```

Next problem:

```
/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
```

resolved as described by:

```
sudo apt-get install ia32-libs
```

---

### Post by dzjowk on 2007-04-30
Solved my problems as well !

thx !

---

### Post by soan on 2007-10-18
Sweet Thanx for this post it sorted my problem.:)

---

### Post by bashir on 2007-10-20
Quick post to say thanks for the information.
sorted my problems with the vmware installation

---

### Post by linux4all on 2007-11-05
after this

sudo ./vmware-install.pl

I got this

A previous installation of VMware software has been detected.

Failure

Execution aborted.

This is a new install of gutsy. no home folder .vmware. no etc.
Any Help?!


Solved today. 6/11 thanks

---

### Post by oriongr on 2007-12-16
Perfect..it solved the same problems to my Ubuntu 7.11 adm64 machine...

---

### Post by k999 on 2008-01-04
Beware of following solution 1. Touching the certificate files caused me some really strange issues with vmware server console, and after several hours of pulling my hair out I discovered that the problem was just that the certificate files were empty and didn't contain valid certificates! I'm not going to reinstall to test from scratch now, but I have since installed openssl, and when running vmware-install.pl again the files were populated with certificates, and now everything appears to work.

I've documented this here as well:

[http://communities.vmware.com/thread/119798](http://communities.vmware.com/thread/119798)

As you can see from the thread, I solved it in the middle of writing it. Typical, it always helps to explain the problem to someone. :)

---

### Post by mrn00ne on 2008-01-11
Hello,

The installation of the VMware VmPerl Scripting API succeeded.

```
Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? [/Virtual 
Machines] 

sh: /usr/lib/vmware/bin/vmware-vmx: not found
Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:       

sh: /usr/lib/vmware/bin/vmware-vmx: not found
The serial number XXXXX-XXXXX-XXXXX-XXXXX is invalid.

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  

You cannot power on any virtual machines until you enter a valid serial number.
To enter the serial number, run this configuration program again, or choose 
'Help > Enter Serial Number' in the virtual machine console.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed

The configuration of VMware Server 1.0.3 build-44356 for Linux for this running
kernel completed successfully.
```

```
apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 but it is not installable
             Depends: lib32z1 but it is not installable
             Depends: lib32stdc++6 but it is not installable
             Depends: lib32asound2 but it is not installable
             Depends: lib32ncurses5 but it is not installable
E: Broken packages
```



any idea ?

Linux falkor 2.6.22-14-server #1 SMP Tue Dec 18 05:52:24 UTC 2007 x86_64 GNU/Linux

---

### Post by dcstar on 2008-01-11
Vmware server is now available in the repositories, and there is now a separate Virtualization forum where issues like this should be, so could people not keep opening this obsolete and misplaced thread?

---

### Post by mealan on 2008-01-15
corrected problems for me as well, quad core 64 bit intel w/ 8gb of ram.

THANK YOU!!!!!

yeah, um, didnt read above post, please delete

---

### Post by n8bounds on 2008-05-20
Thanks man, your notes solved everything for me.

---

### Post by sunbird on 2008-05-31
*Sorry, misposted.*

---

### Post by aboud on 2008-06-24
thank for the usefull instruction, 
but i still have strange problem 


```

Unable to get the access rigths of source file "./vmware-vix/bin"

```

this file doesn't exists at all.
i tryied chmod every thing inside ./vmware but no way..

---

