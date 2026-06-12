---
title: "Can't load windows"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2007-02-15
this may be more a windows related problem, but im trying to load it from ubuntu boot loader. So, here is my story. I was living life fine and dandy, but my evil dell had contracted a virus on windows, so i delete windows, accidentally deleting my ubuntu partition as well. So i angrily had to reinstall and update everything. Several ours later, i got everything to work all nice and everything. My drive has 5 partitiotions, linux~33gb, linux swap~512mb, emptyfat32~5gb, extended partition ~20gb, and windows~20gb. Here is the code

(this is current)
```
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3882    31182133+  83  Linux
/dev/hda2            3883        3943      489982+  82  Linux swap / Solaris
/dev/hda3   *        3944        4554     4907857+   7  HPFS/NTFS
/dev/hda4            4555        7293    22001017+   f  W95 Ext'd (LBA)
/dev/hda5            4555        7293    22000986    7  HPFS/NTFS
```

After i had everything working, i foolishly used gparted, and feormated hda3 to a fat32. Evil windows had to change hda3 to ntfs for no apparent reason. When i could load up windows, hda3 was C:/. The windows disk was I:/. The only files in C:/ were some files that were accidentally placed there as i was installing the drivers (damn u windows...) Anyways, i copied those to I and it still worked. After i reformated hda3(C:/) to fat32, windows simply would not load. I later tried to reformat hda3 back to ntfs, yet windows simply would not load. When i start the computer, windows is still in the boot menu, but when i click on it, it says it does not recognize hda5 filesystem. I tried setting the loader to load on hda3 4 and 5, but none worked. AAAAAAA. i hate you windows...

Please tell me what to do all mighty forum people. I BEG U

ah, one more question. I love google earth. It is very nice, i can be a pshychopath and look up were people lve. Yippy! But besides that, it will not work for me. It gives me this message everytime i load it up 
> Google Earth is unable to identify your graphics card. This is most likelybecause the driver for your graphics card has not been installed. You maycontinue but the Google Earth unlikely to work until you upgrade yourdriver. For detailed driver download and detailed instructions please see ourGoogle Earth Online Help Center using the link below:
[http://earth.google.com/support/bin/answer.py?answer=21482]("Http://earth.google.com/support/bin/answer.py?answer=21482") 

Well, i didnt care much for there "Online Support Centre". How do i install drivers for ubuntu. I installed the nvidi thingy from automatix, but aparently that didn't work. I have some sort of nvidi driver about 62megs (i know it sucks, its a dell). So, all you people that are smarter than me, please offer your help.

---

### Post by chuckyp on 2007-02-15
Well I know from experience windows does not play well unless it is on C:.  In the future your best bet would be to install windows first leaving free space for ubuntu.  Then install ubuntu and let grub handle the boot menu.  That way nix and windows will play nice.

Also automatix is not supported here.  Its also not recomended.  To install proper drivers for your video card just "sudo aptitude install nvidia-glx"

---

### Post by Cardmaster91 on 2007-02-15
ok, well is there a way i can fix this little problem, w/o wiping everything

---

