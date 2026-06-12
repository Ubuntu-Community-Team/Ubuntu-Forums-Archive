---
title: "Trying an install"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by brute on 2007-11-21
Hello, I am a newbie to the Ubuntu forums. So far, 7.10 is working perfect for me. I am running a dual boot with XP. My question really is not about Ubuntu, but rather doing a triple boot, only problem is, I do not see an install option in ArtistX.

Is anyone familiar with this distro, and if so, how would one go about installing it to a hardrive? Keep up the great work!

---

### Post by Pumalite on 2007-11-21
[http://distrowatch.com/?newsid=04596](http://distrowatch.com/?newsid=04596)

---

### Post by brute on 2007-11-21
Hello, and thanks for the post. I have the system it is a live dvd but it has an install option, that does not work, in other words I can only run it live. I have tried to fine some info from the artistx site but keep getting an error message. I am a debian fan and would really appreciate any advise on install or even if it is possible to do a triple install.
Thanks!

---

### Post by Pumalite on 2007-11-21
Do md5sum on your iso, reburn at 4x if md5sum OK.

---

### Post by brute on 2007-11-21
Hello, checked MDsum and it is OK. Burn is fine. I had my sister download and burn it on her machine and it does the same thing. Have you downloaded the latest version yet? It has everything  but the kitchen sink on it. Really nice distro, and would be great along Ubuntu, but it is driving me nuts on the install. Let me know what you come up with, and thanks for the return post.

---

### Post by Pumalite on 2007-11-21
Don't forget to clean the lens in your burner or change if necessary. You have to try YOUR CD's in a different computer.

---

### Post by brute on 2007-11-22
I don't believe it is the drive because I burn all my Distros the same way. I believe it may be Artistx itself. If you try their website you will get an error message. I also get an error 15 when I try an install. I am wondering if maybe the install feature was not implemented in this version. I am use to Ubuntu and Mint having a live with the option to install after you are running it. Artistx gives you that install option at boot. If anyone gets a chance, download it and try it for yourself and then post back.:(

---

### Post by epyonx1 on 2008-03-31
> **brute said:**
> I don't believe it is the drive because I burn all my Distros the same way. I believe it may be Artistx itself. If you try their website you will get an error message. I also get an error 15 when I try an install. I am wondering if maybe the install feature was not implemented in this version. I am use to Ubuntu and Mint having a live with the option to install after you are running it. Artistx gives you that install option at boot. If anyone gets a chance, download it and try it for yourself and then post back.:(


I get the same exact error when I try to install ArtistX 0.4 into a virtual machine, using VirtualBox. It looks like a very useful distribution (though I guess,if you wanted, you could install the useful programs ArtistX has into your Ubuntu). I would still rather virtualize it, personally. So I'm going to try to press E (to edit commands before booting) or C (for command line) at the grub menu. Maybe we can run the installation manually. :\

---

### Post by epyonx1 on 2008-03-31
> **epyonx1 said:**
> I get the same exact error when I try to install ArtistX 0.4 into a virtual machine, using VirtualBox. It looks like a very useful distribution (though I guess,if you wanted, you could install the useful programs ArtistX has into your Ubuntu). I would still rather virtualize it, personally. So I'm going to try to press E (to edit commands before booting) or C (for command line) at the grub menu. Maybe we can run the installation manually. :\

This seemed to START the installation process for me but there were still KERNEL mismatch issues...

ArtistX 0.4
GNU GRUB version 0.97

On the GRUB menu, scroll down.
Highlight the "install" option (Debian GNU/Linux - install)
Press ENTER
If it gives you Error 15, that's okay. Don't panic.
Go back to the GRUB menu
Press 'e' (to edit the commands before booting)
Highlight 'kernel /vmlinuz vga=normal quiet' and press 'e'
Change this line to 'kernel /install/gtk/vmlinuz vga=normal quiet'
Press ENTER to go back
Highlight 'initrd /initrd.gz' and press 'e'
Change this line to 'initrd /install/gtk/initrd.gz'
Press ENTER to go back
Highlight the 'kernel /install/gtk/vmlinuz vga=normal quiet' option
Press 'b' to boot

The installation process should START right up... finishing it is another story altogether :(

---

