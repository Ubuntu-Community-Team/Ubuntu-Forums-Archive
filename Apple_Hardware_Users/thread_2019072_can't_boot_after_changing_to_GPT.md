---
title: "can't boot after changing to GPT"
date: 2012-07-07
forum: Apple Hardware Users
---

### Post by arshb on 2012-07-07
I've installed ubuntu 12.04 on my MBP and then changed the format of my drive back to GPT so I can do EFI now.  However, I can no longer go into my Ubuntu partition without using Grub 2 disc to liveboot.

I know the issue is with the efi file.  I cannot download grub-efi because it says it does not exist.  I've looked around everywhere and nothing has worked.  Any solutions to this?

I have rEFIt installed as well.  I see the Linux penguin and choose it, I just get an error after that.

Everything I've been reading says that in 12.04 there should have been an option to install through EFI but I was never given that option..

---

### Post by yentl on 2012-07-16
Might be worth a try compiling it yourself? Boot into Ubuntu and then follow the instructions here:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
Hopefully that helps.

---

### Post by oldfred on 2012-07-16
Apples efi is not the newer UEFI version 2 standard used by Windows & Ubuntu. Apple uses some sort of hybrid MBR/gpt where the first 4 partitions are MBR just for Windows. 

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

