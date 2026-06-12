---
title: "Failed to set MokListRT: Invalid Parameter - I am scuppered!"
date: 2021-07-31
forum: Apple Hardware Users
---

### Post by art-titor on 2021-07-31
Hi all,

Really need some help.

I installed Ubuntu 20.04 LTS 4 days ago on an iMac 2008 with Mac OSX 10.6.8 Snow Leopard, as I'd heard was a fantastic upgrade I wanted to try.

Installed from USB.

First install= no wifi access; I ran software updates inside Ubuntu. Fixed wifi. Then Firefox froze desktop. Needed reboot.

On this reboot I got the following message, which persists. Sometimes boots to Ubuntu, sometimes just this message on screen and not further. 

If I hold alt + R on powering up, I get a picture of EFI drive or Time Machine Drive (which is the only drive plugged in). I cannot boot my Mac OS :0(

I have checked the forums; there is one post of the below. Only resolve is a BIOS issue on a Dell machine but nothing else.

I'm not a coding / terminal expert, I'm a paramedic and want my Mac back. Please help!

[COLOR=#000000][FONT=-webkit-standard]"Failed to set MokListRT: Invalid Parameter[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]Could not create MokListRT: Invalid Parameter[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]Importing MOK state has failed: import mok_state() failed: Invalid Parameter[/FONT][/COLOR]
[COLOR=#000000][FONT=-webkit-standard]Continuing boot since secure mode is disabled"

Thanks everyone,

Mickie x

[/FONT][/COLOR]

---

### Post by mikewhatever on 2021-07-31
This looks like a known problem with at least some of mymacs, or whaever they are called. Use any one of your favorite search engines to find a solution. 
He is a link to get you started just in case: 
[https://askubuntu.com/questions/1279602/ubuntu-20-04-failed-to-set-moklistrt-invalid-parameter](https://askubuntu.com/questions/1279602/ubuntu-20-04-failed-to-set-moklistrt-invalid-parameter).

PS: Ubuntu is not an upgrade to mymac osx.

---

### Post by dragonfly41 on 2021-07-31
Try installing ReFIND as suggested in above link.
It will install into /boot/efi/EFI/refind
and *complements* existing boot installation.

---

### Post by Frogs Hair on 2021-07-31
Moved to ***Apple Hardware Users.***

---

