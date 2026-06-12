---
title: "A new Mac-on-Linux version with KVM support is available"
date: 2014-09-20
forum: Apple Hardware Users
---

### Post by xeno74 on 2014-09-20
[IMG]http://gnuart.onshore.com/images/mol/png/mol_a_big.png[/IMG]

Hi All,

Just for info: A new Mac-on-Linux version with KVM support is available. 

Installation:

You have to compile  Mac-on-Linux from svn (svn checkout svn://svn.code.sf.net/p/mac-on-linux/code/trunk mac-on-linux-code).

Screenshot:

[[IMG]http://www.supertuxkart-amiga.de/amiga/Mac-on-Linux_G3_KVM-PR_A1-X1000-thumbnail.jpg[/IMG]]("http://www.supertuxkart-amiga.de/amiga/Mac-on-Linux_G3_KVM-PR_A1-X1000.jpg")

QEMU/PPC with KVM also supports Mac OS X in a virtual machine. But Mac OS X is slower on QEMU/KVM than on MoL/KVM.

Screenshots:

[[IMG]http://www.supertuxkart-amiga.de/amiga/Mac_OS_X_Tiger_PPC_G4_on_QEMU_with_KVM-PR_A1-X1000-thumbnail.jpg[/IMG]]("http://www.supertuxkart-amiga.de/amiga/Mac_OS_X_Tiger_PPC_G4_on_QEMU_with_KVM-PR_A1-X1000.jpg")

[[IMG]http://www.supertuxkart-amiga.de/amiga/Mac_OS_X_Tiger_PPC_G3_on_QEMU_with_KVM-PR_A1-X1000-thumbnail.jpg[/IMG]]("http://www.supertuxkart-amiga.de/amiga/Mac_OS_X_Tiger_PPC_G3_on_QEMU_with_KVM-PR_A1-X1000.jpg")

---

### Post by xeno74 on 2014-09-21
There is a special thread in the Amigaworld forum about MoL: [http://amigaworld.net/modules/newbb/viewtopic.php?mode=viewtopic&topic_id=37652&forum=34&start=120&viewmode=flat&order=0#740661](http://amigaworld.net/modules/newbb/viewtopic.php?mode=viewtopic&topic_id=37652&forum=34&start=120&viewmode=flat&order=0#740661) :-)
You can ask your questions there. ;-)

---

### Post by tgalati4 on 2014-09-21
So if I have an old PowerBook G4 with Tiger 10.4, I could create a partition to add a Debian PPC linux distro (MoL in this case) and point to my Tiger OS X drive and run it?

---

### Post by xeno74 on 2014-09-21
> **tgalati4 said:**
> So if I have an old PowerBook G4 with Tiger 10.4, I could create a partition to add a Debian PPC linux distro (MoL in this case) and point to my Tiger OS X drive and run it?

Yes, it is. If you use an old version of Debian with kernel 2.X then you can compile MoL with kernel modules. But if you work with a new Debian distribution like Wheezy, Sid etc, you need a Linux kernel with KVM kernel modul and a compiled MoL with KVM support.

_Edit_:

Configure instructions to start MoL/KVM-PR

**AmigaOne/Power Mac/IBM POWER8:**

> [FONT=Verdana][SIZE=1][COLOR=#4D4D4D]modprobe kvm-pr[/COLOR][/SIZE][/FONT]

> [FONT=Verdana][SIZE=1][COLOR=#4D4D4D]ifconfig tun1 192.168.41.1[/COLOR][/SIZE][/FONT]

> [FONT=Verdana][SIZE=1][COLOR=#4D4D4D]/etc/init.d/tinyproxy status[/COLOR][/SIZE][/FONT]

**MoL/KVM:**

> [FONT=Verdana][SIZE=1][COLOR=#4D4D4D]sudo kextload MolEnet.kext[/COLOR][/SIZE][/FONT]

> [FONT=Verdana][SIZE=1][COLOR=#4D4D4D]sudo kextload MolAudioDevice.kext[/COLOR][/SIZE][/FONT]

---

### Post by xeno74 on 2014-09-22
[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1370&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1370&mode=view")

---

### Post by xeno74 on 2014-09-22
[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1371&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1371&mode=view")

---

### Post by xeno74 on 2014-09-23
Just for info: I have updated Mac OS X to version 10.4.11 on MoL/KVM-PR. :-)

[[img]http://www.supertuxkart-amiga.de/amiga/kernel_3.17-rc6_Mac-on-Linux_KVM-PR_with_10.4.11-A1-X1000-thumbnail.jpg[/img]](http://www.supertuxkart-amiga.de/amiga/kernel_3.17-rc6_Mac-on-Linux_KVM-PR_with_10.4.11-A1-X1000.jpg)

---

### Post by xeno74 on 2014-09-24
Quote Alexander Graf: 

> 
The MOL kernel module was designed with PPC32 hosts and guests in mind.

While that's all great when running on PPC32 hosts, it makes life really
hard on PPC64 hosts, as the MOL kernel module doesn't work there.

Furthermore it also never got upstreamed. So every new kernel revision
might break it.

Recently I implemented KVM for PowerPC64 though. So we now have a common
virtualization framework inside the kernel that gives us easy virtualization
access to PPC32 and PPC64 guest VMs.

This patch implements a simple backend module to interact with KVM. That way
KVM can be used to virtualize the CPU. Everything else still goes through
MOL.

With this patch applied and my recent patches to KVM (see the kvm-ppc ML
archive) I'm happily running a 10.4.11 Mac OS X VM on a 970MP system.
This should also enable G5 and PS3 hosts, though I haven't tried it out
there yet.

Please keep in mind that you need to run 32 bit userspace with a 64 bit kernel
for this to work.
MOL heavily relies on sizeof(guest GPR) == sizeof(void*) == sizeof(int)

---

### Post by rsavage on 2014-09-26
Thanks Christian for sharing this.

I've had a quick go and mol does indeed compile when you select kvm.  What networking compile options did you choose and can you explain more about the ifconfig and tinyproxy commands you've suggested?

Unfortunately the Ubuntu 32 bit SMP kernel doesn't have KVM compiled so for my quick test I installed the last non-smp kernel from oneiric (11.10).  I haven't got a Mac OS X operating system installed yet, but mol seemed to start up.  

I haven't got a kvm-pr module, my module is just called kwm.  I don't know much about kvm/kvm-pr, what is the difference and did you do anything to compile it?

I'll probably compile a non-smp version of the the precise kernel (or maybe a newer version).

---

### Post by este.el.paz on 2014-09-26
> **rsavage said:**
> Thanks Christian for sharing this.

I'll probably compile a non-smp version of the the precise kernel (or maybe a newer version).


@r:

I'd agree that for PPC 12.04 is probably your best choice in the use of your time . . . 14.04 still seems wonky on my iBook G4 . . . .

e.e.p.

---

### Post by rsavage on 2014-09-26
Finally got it working!  (well I've yet to get fullscreen console mode working....but hey)Attached is the proof!

---

### Post by xeno74 on 2014-09-27
> **rsavage said:**
> Finally got it working!  (well I've yet to get fullscreen console mode working....but hey)Attached is the proof!

Congratulation!!!!! 

Here are the answers of your questions:

> 
**KVM**
[LIST=1]
[*]Exploits HW virtualization facilities
[*]970 in “non-Apple” mode, POWER, FSL
[*]Best performances
[*]Requires bare metal access -> No underlying hypervisor
[/LIST]

**"PR" KVM**
[LIST=1]
[*]Runs the guest with user priviledges
[*]Emulation of most priviledge instructions
[*]Runs on almost everything -> Issues when running under PowerVM -> HV calls caught by pHyp
[*]Slower -> Perf improved with paravirt tricks
[/LIST]


More about KVM vs "PR" KVM -> [2012-forum-PowerKVM2012.pdf]("http://www.linux-kvm.org/wiki/images/a/a2/2012-forum-PowerKVM2012.pdf")

Network:

[LIST=1]
[*]MoL needs a tun kernel modul and you will need to install tinyproxy. After that you have to edit the tinyproxy.conf. Put the ip address of your Mac OS X guest to the access list:
```
Allow 192.168.41.2
```
[*]If MoL runs, then there is a tun1 network interface. This network interface needs an ip address:
```
ifconfig tun1 192.168.41.1
```
[*]In the Mac OS X guest you have to install the MoL driver package or you have to load the MolEnet kernel modul.
```
sudo kextload MolEnet.kext
```
[*]Add the ip address to the proxy settings in the system preferences of Mac OS X (System Preferences -> Network -> Built-in Ethernet -> Configure ...-> Proxies -> Web Proxy (HTTP) -> 192.168.41.1:8888
[/LIST]

On which Mac did you install MoL/KVM?

---

### Post by este.el.paz on 2014-09-27
Gents:

Could someone explain the benefits of "Mac-on-Linux" . . . on Apple machines, I'm supposing?  I get it if it's for PC machines, but is it just to eliminate the reboot time for dual boot?  I'm assuming that even if "Mac-on-linux" is open source, OSX would still have to be purchased or obtained?

e.e.p.

---

### Post by rsavage on 2014-09-28
@xeno

Thanks for the info.  It's a G4 iBook.

Do we need this [https://www.mail-archive.com/kvm@vger.kernel.org/msg105074.html](https://www.mail-archive.com/kvm@vger.kernel.org/msg105074.html) patch?  I'm getting a lot of errors in my kern/syslog when run in console mode (which doesn't work......it's the same as you describe in your other thread).

@eep, MOL is ppc only.  It allows Mac OS X to be run on non-apple ppc hardware, and yes you have to own a purchased copy.

---

### Post by xeno74 on 2014-09-28
> **rsavage said:**
> @xeno

Do we need this [https://www.mail-archive.com/kvm@vger.kernel.org/msg105074.html](https://www.mail-archive.com/kvm@vger.kernel.org/msg105074.html) patch?  I'm getting a lot of errors in my kern/syslog when run in console mode (which doesn't work......it's the same as you describe in your other thread).

Unfortunately, this patch is already in the kernel. It doesn't solve our fullscreen issue. I installed MoL/KVM-PR on Lubuntu 12.04.5 yesterday. Unfortunately this installation has the fullscreen issue too.

---

### Post by rsavage on 2014-09-28
Can you use fullscreen when running a really old kernel and the MOL module (i.e. can we determine if this is a KVM issue)?  I've done a search and can't find this issue described before.

Do you get errors in kern/syslog?

If you run molvconfig and don't probe the current mode, but just the TFT modes then the selected mode label has a 60 Hz.....but it still doesn't work and there is no change.

---

### Post by este.el.paz on 2014-09-28
> **rsavage said:**
> 
@eep, MOL is ppc only.  It allows Mac OS X to be run on non-apple ppc hardware, and yes you have to own a purchased copy.

@r:  Thanks for that data . . . looks like you are having fun with it . . . .  e.e.p.

---

### Post by xeno74 on 2014-10-01
Mac OS X boots on an AmigaONE X1000 (YouTube video):

[[IMG]http://i.ytimg.com/vi/7alchoY6kzY/default.jpg[/IMG]]("http://youtu.be/7alchoY6kzY")

---

### Post by xeno74 on 2014-10-02
Hi All, 

I have created a MoL/KVM deb package for these following systems: 

- A-EON Live Remix Distribution 
- Lubuntu 12.04 
- Lubuntu 14.10 

Download: [mol-kvm_0.9.73.0-ubuntu_powerpc.deb]("http://www.xenosoft.de/mol-kvm_0.9.73.0-ubuntu_powerpc.deb") 

If you want to allow normal accounts to run MoL through startmol script,  you have to use dpkg-statoverride: 

> sudo dpkg-statoverride --update --add root root 4755  /usr/local/lib/mol/0.9.73/bin/mol 

Rgds, 

Christian

---

### Post by xeno74 on 2014-10-03
I have figured out, that Mac OS X only boots with the **RC1 of kernel  3.17 or higher**. Mac OS X _doesn't_ boot with kernel 3.14 and  3.15. I could boot Mac OS X 10.3.4 Panther with the kernel 3.17 too.

Debian Sid PowerPC with Mac OS X 10.3.4 Panther:

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1383&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1383&mode=view")

Yeah, Lubuntu **14.10** _Utopic Unicorn_ PowerPC with Mac OS X 10.4.11 Tiger:

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1382&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1382&mode=view")

---

