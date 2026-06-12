---
title: "/efi/redhat/grub.efi in my refit menu?"
date: 2011-08-19
forum: Apple Hardware Users
---

### Post by Nevalite on 2011-08-19
I just finished installing Windows 7 and Scientific Linux on my 2011 MBP along with Lion and my triple boot is finally working. The only thing is that I have 4 options in my refit menu...The first option is this /efi/redhat/grub.efi thing and I have no idea how it got there. The next 3 are osx, linux and windows and they all work fine.

How can I get rid of this first item? What is it?

---

### Post by Nevalite on 2011-08-19
After doing some research it would seem that somehow I installed grub to my mbr? Is that possible? When I installed scientific linux I told it specifically to install grub to the same partition as the linux install so I don't know how it got there.

How can I remove grub? Will removing it mess up my triple boot? In theory there should be another grub installed on my linux partition right?

Thanks

---

### Post by Nevalite on 2011-08-19
So I have located the file, it is /boot/efi/EFI/redhat/grub.efi

What is this file?

If I just delete it will it go away from my refit?

---

### Post by pindar on 2011-08-20
I had this file/directory as well after installing fedora, so I'm guessing it's the redhat/fedora installer which puts it there. You can simply remove it, and it won't show up again in your refit boot screen.

---

### Post by Nevalite on 2011-08-20
Thanks for the advice. I went ahead and deleted the directory, the item is gone from refit and all my os still boot fine. :)

---

