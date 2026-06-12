---
title: "Re: lubuntu 16.04 64 bit on macbook 3,1: boot problem after installation"
date: 2017-11-18
forum: Apple Hardware Users
---

### Post by erotavlas on 2017-11-18
Hi,
I have a problem with the installation of lubuntu 16.04 LTS 64 bit on a macbook 3,1 late 2007. I already installed the same operating system into a different notebook of the same series without any big troubles. So I repeated the same installation procedure by installing the UEFI version with GPT partition table with four partitions: fat32 with flags boot and eps for EFI boot mounted /boot/efi, ext4 main operating system mounted at /, swap and ext4 home partition mounted at /home.
The installation procedure completes successfully, but after the first reboot at grub the keyboard does not work. After the grub timeout the operating system gets stuck with blank screen.
I already tried to boot a live lubuntu and I changed the linux kernel option on /mounted_partiton/etc/default/grub file by removing quiet splash options and by adding nomodeset. I saved the file and I reboot without any success. I also tried to install grubcustomizer on live lubuntu and I changed from there the options, but it still did not worked.
Do you have any suggestion?
Thank you

P.S.
I know that maybe this is not the most appropriate forum section, however the admin here are always able to solve my problems.

Hi,
I made some progresses, but I was not able to solve the problem.
After the installation of lubuntu 16.04 LTS 64 bit, the grub appears and the keyboard does not work. Then after timeout it stays forever with the blank screen.
If I enter in the boot menu by using the option keyboard of the mac, with inserted a live USB of lubuntu 16.04 LTS 64 bit, I have the following three options:
```

Windows
EFI Boot
EFI Boot

```
the windows does not boot and the other two boot into live USB.
So I tried to install many different distributions without success (lubuntu 16.04 LTS 32 bit, lubuntu 14.04 LTS 64 bit, debian 9.2 64 bit, elementary OS 64 bit) and finally I decided to try with fedora 27 64 bit. Now with fedora live USB in the boot menu, I have the  following four options:
 ```

Windows
fedora media
EFI Boot
EFI Boot

```
If I select fedora media, the grub appears, the keyboard works, I can boot to lubuntu and it works perfectly.
I do not know how to avoid to use the fedora USB live and I'm quite sure that is something related to how the grub is launched.
Do you have any suggestion?

P.S.
I also checked sudo efibootmgr -o 0000,0080 as explained [here.]("https://help.ubuntu.com/community/MacBookPro12-1/Wily")

Hi,
I tried to install [rEFInd boot manager]("http://www.rodsbooks.com/refind/") without success. I still have to use a fedora live USB in order to boot to lubuntu.
I'm loosing my last hopes and I think I have to throw into the waste my old macbook. :(

---

### Post by erotavlas on 2017-11-29
Hi,
I solved in very simple way that I forgot to try. I just reset the [NVRAM]("https://support.apple.com/en-us/HT204063") of the Mac and I reinstalled the operating system.

---

### Post by howefield on 2017-11-29
Thread moved to the "*Apple Hardware Users*" forum.

---

