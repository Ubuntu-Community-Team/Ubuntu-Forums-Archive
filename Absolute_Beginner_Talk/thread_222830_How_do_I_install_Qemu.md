---
title: "How do I install Qemu?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-25
So how do I do it? What's the difference between Vmware & Qemu!!!

---

### Post by JoWilly on 2006-07-25
This has been posted many times. Use the search feature. ;)

---

### Post by moma on 2006-07-25
Install older version (v0.8.0) of QEMU without KQEMU accelerator.
$ sudo apt-get install qemu 

Install the latest version of QEMU (v0.8.2) with KQEMU accelerator.
[http://ubuntuforums.org/showthread.php?t=213327]("http://ubuntuforums.org/showthread.php?t=213327")
Browse down to "Install latest QEMU and KQEMU (accelerator) as instructed..." 

Install VMware Player or WMware Server.
[http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")
You will find URLs at the bottom of this page.

Emulation(QEMU, BOCHS) and Virtualization(VMware, XEN)
[http://www.futuredesktop.com/hpc_linux.html#VM]("http://www.futuredesktop.com/hpc_linux.html#VM")

// moma

---

### Post by aysiu on 2006-07-25
Before you can install either Qemu or VMWare, [you need extra repositories enabled](http://www.psychocats.net/ubuntu/sources).

Once that happens, you can do ```
sudo aptitude update
sudo aptitude install qemu vmware-player
```

Qemu is a bit slower, and it tries to set up a virtual environment, but it isn't fully functional (for example, you can't partition or install anything with Qemu).

VMWare allows you to create a virtual hard drive so you can actually install another operating system within Ubuntu (or Windows). Of course, that means you actually have to create that virtual hard drive.

---

### Post by kris2pe on 2006-07-25
how slow is emulation w/ Windows in Linux?

---

### Post by JoWilly on 2006-07-25
> **kris2pe said:**
> how slow is emulation w/ Windows in Linux?

It is not "emulation" as you run the native windows on top of a virtual hardware layer with direct calls to your hardware.

Speed depends on your hardware (ram is also an important point). On a decent P4 3 ghz class system winxp in vmware will be only a little slower; perfectly fine to work with. Winxp will boot faster than real in vmware.

---

### Post by kris2pe on 2006-07-25
Ok! But its weird coz Mac's paralels can play & run xp quite well! Y is that?

---

### Post by JoWilly on 2006-07-25
> **kris2pe said:**
> Ok! But its weird coz Mac's paralels can play & run xp quite well! Y is that?

:confused: 

Did I say it doesn't run quite well ?

It runs very well, almost as fast as native with faster boots.

---

### Post by kris2pe on 2006-07-25
Ok I'll try! Will it run smoothly if I only have one 1gig of ram? Just wonderin! Ok I will try Vmware then!

---

### Post by JoWilly on 2006-07-25
> **kris2pe said:**
> Ok I'll try! Will it run smoothly if I only have one 1gig of ram? Just wonderin! Ok I will try Vmware then!

Yes 1 gig will be fine.

You can assign 384 to 512 mb to the virtual machine (this is about what xp needs on any system to work properly).

---

### Post by kris2pe on 2006-07-25
I tried to copy the repository list on the link 
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
I copied & pasted all of it but after 
aptget update 

I get this error:
```

W: Duplicate sources.list entry http://archive.ubuntu.com dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

I know it means that I have entered duplicate files but what should I remove?

---

### Post by aysiu on 2006-07-25
Did you paste it *after* your current sources.list or *over* your current sources.list?

---

### Post by kris2pe on 2006-07-26
Well I have added other lines in the repos that I think will I might need!
Anyways I will paste it over my previous thanks.
On the VMware download site I notice that there are alot of files required to run program. 
There's 
VMware Server for Linux. 
Management Interface.
VMware Server Windows client package
VMware Server Linux client packag

Should I download all of it? 
I just want a normal Xp desktop!

BTW I heared about parallels but is it better than Vmware?

---

### Post by kris2pe on 2006-07-26
I just finish downloading the vmware linux tar. 
But after extracting it I get an erro saying 

```

mv: will not overwrite just-created `/home/tope/VmWare/vmware-authd' with `/tmp/fr-N19Gcd/vmware-server-distrib/etc/pam.d/vmware-authd'
mv: will not overwrite just-created `/home/tope/VmWare/vmrun' with `/tmp/fr-N19Gcd/vmware-server-distrib/lib/bin/vmrun'
mv: will not overwrite just-created `/home/tope/VmWare/vmware-remotemks' with `/tmp/fr-N19Gcd/vmware-server-distrib/lib/bin/vmware-remotemks'
mv: will not overwrite just-created `/home/tope/VmWare/vmware-vmx' with `/tmp/fr-N19Gcd/vmware-server-distrib/lib/bin/vmware-vmx'
mv: will not overwrite just-created `/home/tope/VmWare/vmware' with `/tmp/fr-N19Gcd/vmware-server-distrib/lib/bin/vmware'
mv: will not overwrite just-created `/home/tope/VmWare/LWP.pm' with `/tmp/fr-N19Gcd/vmware-server-distrib/lib/perl5/site_perl/5.005/Bundle/LWP.pm'
mv: will not overwrite just-created `/home/tope/VmWare/https.pm' with `/tmp/fr-N19Gcd/vmware-server-distrib/lib/perl5/site_perl/5.005/URI/https.pm'
mv: will not overwrite just-created `/home/tope/VmWare/ftp.pm' with `/tmp/fr-N19Gcd/vmware-server-distrib/lib/perl5/site_perl/5.005/URI/ftp.pm'
mv: will not overwrite just-created `/home/tope/VmWare/gopher.pm' with `/tmp/fr-N19Gcd/vmware-server-distrib/lib/perl5/site_perl/5.005/URI/gopher.pm'
mv: will not overwrite just-created `/home/tope/VmWare/file.pm' with `/tmp/fr-N19Gcd/vmware-server-distrib/lib/perl5/site_perl/5.005/URI/file.pm'

```
the list goes on & on!!!

---

