---
title: "Install Windows 8"
date: 2013-03-28
forum: Any Other OS
---

### Post by sasi8998vv on 2013-03-28
Hey everyone, I know this is an old post, but this is probably the most relevant one. currently, I have Windows xp dual booting with ubuntu 12.10, and I now wanna install Windows 8. I have absolutely no clue if my system is gpt or EFI or anything... so im basically a  n00b :P

But I did run this line of code  -  "sudo parted /dev/sda unit s print"
And the result - 
Number  Start      End         Size        Type      File system     Flags
 1      15181s     92162047s   92146867s   extended                  lba
 5      15183s     51828303s   51813121s   logical   ntfs
 6      51828736s  87971839s   36143104s   logical   ext4
 7      87973888s  92162047s   4188160s    logical   linux-swap(v1)
 2      92162048s  195366911s  103204864s  primary   ntfs            boot


Hope that helps.

---

### Post by oldfred on 2013-03-28
Moved to your own thread. Not related to UEFI boot and is Windows install issue.
Only new Windows systems have UEFI with gpt partitioning. Windows 8 systems pre-installed have secure boot. A few systems with Windows 7 have UEFI, but most were CSM/BIOS/Legacy or the old way to boot.
UEFI requires gpt partitioning and Windows only boots from gpt partitioning with UEFI. 
XP does not work with gpt partitioning as it is too new for it to have drivers.

Are you overwriting your existing Windows?

Windows has to boot from a primary NTFS formatted partition, you only have one Primary and the extended with many logical partitions. The extended does count as a primary.

---

