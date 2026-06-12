---
title: "rEFIt or GRUB2 ?"
date: 2010-02-22
forum: Apple Hardware Users
---

### Post by johnlocke2342 on 2010-02-22
Hi.
I stood away from Linux for a few months and now I'm back there's the new GRUB2, and I'm a little bit lost with it.
I've always been using rEFIt on my macbook 4.1, but the current version doesn't recognize a Linux OS with GRUB2 as a Linux OS. I don't really like it even if everything else works fine. I read about hacks, and on the rEFIt patches page, I found a .diff patch resolving the problem, but I don't know how to use it (I guess I should build GRUB2 from source with this patch but I'm not sure how to do this). Also, I saw GRUB2 has the ability to use a graphical menu, so I don't really know which one to choose: A hacked GRUB2/rEFIt displaying Linux as Linux or just GRUB2?

Thanks in advance.

---

### Post by Bachstelze on 2010-02-22
Just install GRUB .97, that's what I did. ;)

```
sudo apt-get install grub
```

---

### Post by johnlocke2342 on 2010-02-22
Thanks, but I already tried this, but it installs grub-common 1.97, so it doesn't solve the problem.

---

### Post by heluani on 2010-02-22
For what it's worth, I'm currently running only grub2 and it works like a charm. I ended up wiping the whole OSX partition, but if you want to keep it, just compile grub2 under linux and install the modules in /efi of your mac os X partition.

R.

---

### Post by dennis123123 on 2010-02-22
> **heluani said:**
> For what it's worth, I'm currently running only grub2 and it works like a charm. I ended up wiping the whole OSX partition, but if you want to keep it, just compile grub2 under linux and install the modules in /efi of your mac os X partition.

R.

nvidia? binary driver? 

I'm looking for more information on this, because at the moment I understand its still not possible to get the proper nvidia driver through efi booting, just the partial nouveau or nv.

---

### Post by heluani on 2010-02-22
> **dennis123123 said:**
> nvidia? binary driver? 

I'm looking for more information on this, because at the moment I understand its still not possible to get the proper nvidia driver through efi booting, just the partial nouveau or nv.

These are two separate issues, to boot you can boot with different framebuffer drivers (I currently boot with video=efifb) and then after the kernel is up you can launch x with any driver you want. In particular I am running nvidia 190.53-r1 on GeForce 9400M.

R.

---

### Post by dennis123123 on 2010-02-23
> **heluani said:**
> These are two separate issues, to boot you can boot with different framebuffer drivers (I currently boot with video=efifb) and then after the kernel is up you can launch x with any driver you want. In particular I am running nvidia 190.53-r1 on GeForce 9400M.

R.

:shock: X with full accel?! cool!

would you fancy making a quick tutorial? I think many members of the community would appreciate that, i know I certainly would :)

---

### Post by heluani on 2010-02-23
The first two google hits are already good enough for installing grub 2 (the very first one is what I followed)

[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

---

### Post by dennis123123 on 2010-02-23
Hmmm thats what I used before, and it wouldnt load the kernel fully :( Maybe I got a bad snapshot that day. I'll try again!

Would you mind posting your grub.cfg then please? to see what fakebios/biosdump/etc you used to get a working boot on the nvidia hardware.

---

### Post by heluani on 2010-02-23
Somehow I believe you're making too much of a deal of installing grub2. Here's my (really simple) grub.cfg:
```

timeout=10
menuentry "Linux" {
root=(hd0,3)
linux /boot/linux agp=off video=efifb
}

menuentry "Old Linux" {
root=(hd0,3)
linux /boot/old agp=off video=efifb
}

menuentry "Mac OSX" { 
root=(hd0,2)
chainloader /usr/standalone/i386/boot.efi -v
}
```

and my nvidia-based macbook Air

```
#lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)
```

Note the agp=off doesn't really matter with the nvidia-drivers... perhaps you're worried about something like this?
```
$ glxinfo | grep direct
direct rendering: Yes
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,
```

---

### Post by johnlocke2342 on 2010-02-23
OK so I finally found out how to remove GRUB2 and install GRUB legacy instead thanks to the documentation.
Thanks anyway

---

