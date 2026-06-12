---
title: "Tailored help putting Ubuntu on External HDD Please"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Lokiducks on 2007-02-12
Hey everyone,

I got a copy of Ubuntu called Ubuntu Ultimate Edition. It's Edgy with a bunch of built-in apps and stuff. 

Anyway, my hope is to put this on an external harddrive to boot from so i can mess around with it and maybe ditch windows.

In any case, i've tried a few times and run into some problems. I've done a lot of searching here and on the Google, but i've seen so many different and conflicting things i don't know what to try anymore. So hopefully you guys can help and this post won't just get deleted. So let me bring you up to speed...

My BIOS does seem to support USB booting.
I burned a bootable CD based on the Ubuntu Ultimate Edition iso that i downloaded.
I have been able to use Ubuntu from the Live CD (i think that's the term).
I first tried installing with the NTSF Formatted external mounted.
Installation failed at 15%.
I then disabled "Mount Removable Media when hot-plugged" "Mount Removable Media when inserted" and "Browse Removable Media when Inserted."
This allowed the installation to proceed further than before. 
Installation failed at around 90%.

I chose to have the partitioning to be automatically be done by the installer, choosing the external harddrive, which was known as "/dev/sda"

Then in step 6/6 of the installer, it asks where the boot-loader (is this the right term? i forget it) should go. It defaults as "(hd0)" i believe, and i change this to "/dev/sda/" so that it is put on the external drive (i have also tried this putting "/dev/sda" in parentheses.)

Both of the last two attempts ended in errors. One of which was "supbrocess pre-removal script returned error exit status 1"



So can anyone help me out. I know this is a lot to read through, but i'm trying to be as specific as i can so you guys can help me out as specifically as you can!

I appreciate any help you can offer me :)

Thanks,


Chris

---

### Post by Lokiducks on 2007-02-12
bump'd

---

