---
title: "Discs wont boot?"
date: 2010-10-19
forum: Apple Hardware Users
---

### Post by Comzee on 2010-10-19
I have a macbook specs here: [(>^_^)>]("http://store.apple.com/us/product/FC240LL/A")

I have discs for Ubuntu + Kubuntu, 10.04 and 10.10 for both. When I put these discs in the computer, it reads them and I can boot from them, although when I get to the initial screen where it asks you what to do, like install ect, , , , after I select an option the screen just goes black, I've waited up to 30 minutes but nothing. I can't troubleshoot anything because nothing comes up. I've tried searching online for similar problems to no avail. Any help?


Thanks in advance!!!

---

### Post by Comzee on 2010-10-21
Bamp

---

### Post by avtolle on 2010-10-21
I'm guessing here that the problem is with the video card and linux driver therefor. As I don't have that hardware, all I can do is suggest you look for others with the same video/graphics hw who had issues. It might be you need to add a boot parameter like 'nomodeset' to the kernel line. HTH.

---

### Post by Comzee on 2010-10-21
> **avtolle said:**
> I'm guessing here that the problem is with the video card and linux driver therefor. As I don't have that hardware, all I can do is suggest you look for others with the same video/graphics hw who had issues. It might be you need to add a boot parameter like 'nomodeset' to the kernel line. HTH.

Yea I researched that, and I've already tried the nomodeset parameter while installing, same issue. ;(

---

### Post by avtolle on 2010-10-21
The only other suggestion I have is to grab an alternate install iso, burn it to a CD-R at a slow speed after checking the md5 sum to be sure the download wasn't corrupted, and try to install that way (if that's what you have in mind). This is a text based install, and can work when the normal "desktop" installer (which uses graphics, as you obviously know) doesn't.  From there you might be able to boot into the system, etc. Hopefully, one with more knowledge about this hardware combo can come along and give better assistance than I.

---

