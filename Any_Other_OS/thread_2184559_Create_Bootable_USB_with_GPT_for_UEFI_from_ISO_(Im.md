---
title: "Create Bootable USB with GPT for UEFI from ISO (Im on Ubuntu 13.04)"
date: 2013-10-29
forum: Any Other OS
---

### Post by jjk5147 on 2013-10-29
So pretty much I am on 13.04 and I need to get this laptop back to windows because I do not believe I am keeping it. I have my windows 8.1 x64 iso and I have a flash drive that I have used to boot uefi before however I am having a difficult time creating a Bootable USB drive with GPT for UEFI from an iso file.
 
(edit)
I searched for a while and most the tutorials i have found are from windows to ubuntu not ubuntu to windows.

Any help is appreciated thanks.

---

### Post by oldfred on 2013-10-29
I do not know if any of the Linux flash drive tools create a UEFI system. The Ubuntu flash drive is both BIOS & UEFI from a FAT32 partition.

You may have to create the efi partition on a gpt formatted flash drive.

This was more for windows 7 but may give some clues.
 Convert Windows BIOS to UEFI - Also command line install of files to efi partition
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[URL="http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI"]http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI
[/URL]
Convert Windows USB flash install to UEFI boot
 [http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

[URL="http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI"]
[/URL]

---

