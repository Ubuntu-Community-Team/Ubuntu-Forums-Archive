---
title: "Ubuntu on a MacBookPro 9,1 different not working boot possibilities in ReFind"
date: 2015-10-02
forum: Apple Hardware Users
---

### Post by bartatubuntu on 2015-10-02
Hello 

Installed Ubuntu 14.04.3 on a MacBook Pro 9,1 and working almost like it have to be. 
But in the ReFind menu i get different boot options and none is working like it have to be: 


1
Boot EFI\ubuntu\grubx64.efi on EFI
---> boots after a long time 
see attachment: MacBookPro_Ubuntu_Boot_EFI\ubuntu\grubx64.efi.jpg
[ATTACH=CONFIG]264790[/ATTACH]

2
MacOS X (Mavericks)
---> boots normal

3
Boot boot\vmlinuz-3.19.0-25-genric.efi.signed on EFI
see attachment: MacBookPro_Ubuntu_Boot_boot\vmlinuz-3.19.0-25-genric.efi.signed.jpg
---> boots never, freezes after a list of functions
[ATTACH=CONFIG]264791[/ATTACH]

4
Boot Linux from whole disk volume
see attachment: MacBookPro_Ubuntu_Boot_Linux_from_whole_disk_volume.jpg
---> boots never, almost direct black screen with: "No bootable device -- insert boot disk and press any key _"
But grub seams to be installed in EFI partition.
[ATTACH=CONFIG]264792[/ATTACH] 

I need help to get this properly working with direct boot from the "Boot Linux from whole disk volume" in ReFind menu. 
If possible without reinstall because i have already done a lot of reinstalls to get this fixed, every time resulting in a complete mess. 


Another question out of interest: 
Is "Start MOK utility at EFI\ubuntu\MokManager.efi in the ReFind menu after installing Ubuntu a kind of recovering disk? 
Never seen that in ReFind menu before. 
[ATTACH=CONFIG]264793[/ATTACH]

---

### Post by bartatubuntu on 2015-10-05
Nobody can help with this or can give a hint were to search?

---

