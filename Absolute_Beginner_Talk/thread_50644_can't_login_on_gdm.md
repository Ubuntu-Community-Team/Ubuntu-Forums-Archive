---
title: "can't login on gdm"
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by imnuskater on 2005-07-20
Hi There,

I installed on a fresh SATA drive ubuntu(I've got the free cd's ordered v5.04). everything looks fine until I reached the gdm. the resolution of the screen showed me the video card was probably detected but the problem is I can't login.  
as soon as I put the password in  the pc freezes. now i tried to change the session but as soon as i click any radio button (for any of the listed session types) the pc freezes.

any ideas what is wrong? here below is the system description:

P4 2.9 Gz
512 DDR
80 Gb SATA drive
Radeon X600
It is a COMPAQ/HP desktop SR1222NX

I used befora FC3 on this system(with the built-in graphic card though) with no big issues.

Thanks in advance

---

### Post by codejunkie on 2005-07-20
[QUOTE=imnuskater]Hi There,

I installed on a fresh SATA drive ubuntu(I've got the free cd's ordered v5.04). everything looks fine until I reached the gdm. the resolution of the screen showed me the video card was probably detected but the problem is I can't login.  
as soon as I put the password in  the pc freezes. now i tried to change the session but as soon as i click any radio button (for any of the listed session types) the pc freezes.

any ideas what is wrong? here below is the system description:

P4 2.9 Gz
512 DDR
80 Gb SATA drive
Radeon X600
It is a COMPAQ/HP desktop SR1222NX

I used befora FC3 on this system(with the built-in graphic card though) with no big issues.

Thanks in advance[/QUOTE]
i had alot of freezing issues on my compaq/hp SR1103WM when trying to use anything but the onboard video what kind of card is it PCIe, AGP, or PCI also check in the bios and make sure onboard video is fully disabled. and i dont know if this will help you or not but i had to install with the linux acpi=off to keep it from freezing or rebooting during the install, you can test this without reinstalling to see if it helps by passing it grub when you boot up.

---

### Post by imnuskater on 2005-07-20
it is a PCIe card and the onboard video is disabled from bios. i had no troubles during install. maybe i should try install with the acpi off

if i use the recovery mode to boot i see i'm automatically logged in as root! and there's an error saying "Temporary failure in name resolution" 

how can i configure the X server from shell mode?

---

### Post by codejunkie on 2005-07-21
[QUOTE=imnuskater]it is a PCIe card and the onboard video is disabled from bios. i had no troubles during install. maybe i should try install with the acpi off

if i use the recovery mode to boot i see i'm automatically logged in as root! and there's an error saying "Temporary failure in name resolution" 

how can i configure the X server from shell mode?[/QUOTE]

the "Temporary failure in name resolution" is a networking issue that happens if you haven't configured your network access or the ntp server is down i think. and you can reconfigure the xserver with this ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by imnuskater on 2005-07-21
thanks,

i'm using the vesa drivers and now i'm able to login without problems.
i'll see if i can install the ati drivers though.

next step is the sound(there's no audio at this time)

---

