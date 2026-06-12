---
title: "Plextor 712SA DVD burner"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by agatha on 2007-01-12
Hi
I have recently converted this PC to Ubuntu with a great deal of success, but I am stumped with this problem and would appreciate any assistance in the plainest possible language as I am still coming to terms with *basic* Linux commands. 

I have used this PC and its peripherals under XP Pro for over 2 years without probs, so I know that the hardware works.

I use a SONY CRX 320E DVD player and the PLEXTOR DVD writer.
When I installed Ubuntu it detected the SONY OK first up, because its a PATA device, whereas the PLEXTOR is a SATA device, like the extra HD drives (the boot disk is a simple 80Gb IDE)

Whilst I managed to mount the SATA HDs OK I can't get the PLEXTOR to work.
I have tried to edit /etc/fstab to no avail following instructions posted on tuXfile.

The error/debug messages I get from software (GnomeBaker, K3B,Acidrip) is consistently similar to:

" :-( unable to TEST UNIT READY: Input/output error
:-( unable to SYNCHRONOUS FLUSH CACHE: Input/output error " ,and

" :-[ WRITE@LBA=30h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/sr0: flushing cache
:-( unable to TEST UNIT READY: Input/output error
:-( unable to SYNCHRONOUS FLUSH CACHE: Input/output error"

Please help .

Thank you

---

