---
title: "the eye book aint right"
date: 2006-08-06
forum: Apple PPC Users
---

### Post by TheEye on 2006-08-06
ok here is what the live cd gives me when i boot it on my ibook g3 300mhz 512 ram  and type in live or live-powerpc or any other that will boot it or text install it in any way shape or form...:

Can't allocate initial device-tree chunk 

apple ibook ver2.2 (bios info boot rom ver. ect)

Welcome to Open Firmware 

type Mac-boot for a mac boot or Shut-down to shut down 

0>



what the is this¿ 

why doesnt any of the boot options on the cd work right ¿ 

and how do i get it to work¿

~the Eye of Rah

---

### Post by 3rdalbum on 2006-08-07
Sorry. This is a bug in something that Linux uses to start up on PPC. It seems to have been introduced shortly before Dapper shipped.

Unfortunately, there's no way for you to get it to work. The screen you're getting is actually Apple's Open Firmware prompt, not anything to do with Ubuntu or Linux.

Just out of interest: Are you using a downloaded CD or one from ShipIt? My ShipIt CD actually works in my iMac, yet other people with the same model of computer have no problems.

---

