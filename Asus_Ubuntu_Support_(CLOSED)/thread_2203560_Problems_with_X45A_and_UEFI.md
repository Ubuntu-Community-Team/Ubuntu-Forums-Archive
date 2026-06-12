---
title: "Problems with X45A and UEFI"
date: 2014-02-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by debaseoperations on 2014-02-04
Now I have a small problem with an ASUS that I picked up second hand. Windows 8 was preinstalled but it was buggy as hell, system restore was down and you couldn't install any new programs. Now hearing only bad things about the OS I decided to wipe it and start a fresh.
I chose to run Ubuntu 12.4 64 bit because I had it laying about. So I went through the UEFI and turned of the bells and whistles, and started up in legacy without the security. Live from USB worked straight off the bat no problems. It's still working fine. But the problem started after I had installed Ubuntu and did a reboot. It simply didn't have any option to boot from HDD, none. In fact there were no boot options. I replaced the USB and Live booted up fine again. I looked at all my partitions and they were there. I did some reading about and tried a program called root-repairer. I ran that successfully - [http://paste.ubuntu.com/6871116/](http://paste.ubuntu.com/6871116/) is the log.
After that I recieved an option of Windows loader. but after pressing that it would just return me to the bios screen.
This is the flashiest computer I have owned, as in the newest as most of the computers I've been running are ancient in today's terms. I've been reading about but it seems no one has had a problem exactly like mine.
It's quite perplexing.  Thanking anyone who can point me in the right direction.
Cheers Dwuan

---

### Post by ajgreeny on 2014-02-04
Follow the instructions at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") to install in UEFI mode which I think has some advantages over BIOS.  You already have an **efi **partitionso can use that but make sure it has the boot flag on it, or delete that one and make a new one which will remove the boot option for windows, which is now not available to boot.

It is simpler than it looks at first glance as you will not have windows to worry about, so have a long careful read of that link and see if it is any help.

I note you seem to have Mint 15, not Ubuntu 12.04, but it should be very similar, I thnk, so far as installing is concerned.

---

### Post by oldfred on 2014-02-04
You have a UEFI install.
Did you turn on secure boot in UEFI, as your Linux install is not a secure boot version. 
OR did you turn on legacy only boot as you have no legacy installs and that would not work.
You show a couple of Windows efi boot files in efi partition but no Windows install, so those boot entries will not work.

Some UEFI only boot Windows. Vendors modify descriptions in UEFI to look only for Windows to boot. Boot-Repair has a work around for that if that is your case.

But since you have only one install you will not normally get grub menu. It will just auto boot defautl entry. But then you may have video issues or other issues that prevent booting and you really do not know if or where issue is.
If you hold shift key from UEFI/BIOS do you get grub menu? Or with some UEFI you have to use escape key.

Also many new UEFI systems work better if you use the newest version of Ubuntu or 13.10. Also 12.04.4 will be out in a week or two and both have major improvements in UEFI Linux support.
Also vendors are making major changes to improve UEFI, so often good idea to update UEFI/BIOS from vendor to newest version.

You also show no entry in UEFI.
```
 chroot /mnt/boot-sav/sda2 efibootmgr -v
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0003,0004,0001,0002
Boot0001  CD/DVD Drive 	BIOS(3,0,00)AMGOAMNO........o.H.L.-.D.T.-.S.T. .D.V.D.R.A.M. .G.T.7.0.N....................A...........................>..Gd-.;.A..MQ..L.Y.K.C.O.B.7.5.1.3.8. .3. . . . . . . . ......AMBO
Boot0002  Network Card 	BIOS(6,0,00)AMGOAMNO........k.R.e.a.l.t.e.k. .P.X.E. .B.0.3. .D.0.0.........................rN.D+..,............<..Gd-.;.A..MQ..L.R.e.a.l.t.e.k. .P.X.E. .B.0.3. .D.0.0......AMBO
Boot0003* UEFI: Lexar USB Flash Drive 1100	ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(2,0)HD(1,20,1d3ffe0,c3072e18)AMBO
Boot0004* Hard Drive 	BIOS(2,0,00)AMGOAMNO........}.L.e.x.a.r. .U.S.B. .F.l.a.s.h. .D.r.i.v.e. .1.1.0.0....................A.............................J..Gd-.;.A..MQ..L.L.e.x.a.r. .U.S.B. .F.l.a.s.h. .D.r.i.v.e. .1.1.0.0......AMBO


```

---

