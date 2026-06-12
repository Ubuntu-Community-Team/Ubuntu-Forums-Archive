---
title: "boot to uefi shell to fix bios boot option"
date: 2016-07-01
forum: Apple Hardware Users
---

### Post by digilevi2006 on 2016-07-01
Hi everyone. 


I don't know if I'm in the correct section but is there a possibility to boot to a uefi shell using ubuntu and fix my boot options?
I want to bring back the USB and HDD boot options. Right now I have only 3, Windows boot manager, dvd drive, and PXE LAN.
What happened was I accidentally deleted.these options through clover by clicking the option remove all clover entries 
I was toying around with the "bcfg" command through this thread:
      [http://www.tonymacx86.com/threads/guide-remove-extra-clover-bios-boot-entries-prevent-further-problems.175274/](http://www.tonymacx86.com/threads/guide-remove-extra-clover-bios-boot-entries-prevent-further-problems.175274/)
  but then silly me Ive deleted them all
I've installed windows uefi through LAN with SERVA but it cant boot by itself even if I choose the windows boot manager and disable CSM option. Ive tried also wintoUSB but no go.

My plan is to boot Ubuntu by LAN PXE through SERVA so can someone guide me how to do this if it is possible to have a shell and fix bios.
I dont know if booting clover is possible and if it is doable also on SERVA.

please help me, I really need to bring back those boot options.


btw, tried also a win DVD but doesnt boot.

Thanks in advance.

---

### Post by ppatrick on 2016-07-08
you can directly boot into the UEFI shell "also" with Serva.

[http://vercot.com/~serva/an/NonWindowsPXE3.html](http://vercot.com/~serva/an/NonWindowsPXE3.html)
5.9 UEFI Shell

Note: Please consider not all the Shell.efi available out there will be compatible with your UEFI firmware version.

---

