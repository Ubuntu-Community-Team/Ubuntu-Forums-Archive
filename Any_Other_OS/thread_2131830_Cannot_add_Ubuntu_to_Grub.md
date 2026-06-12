---
title: "Cannot add Ubuntu to Grub"
date: 2013-04-02
forum: Any Other OS
---

### Post by bashhimup on 2013-04-02
I accidentally installed grub from arch linux, and I had to put entries on it. I did it with Windows Vista, and it works fine, but I tried with Ubuntu, and it didn't work. This is what I typed in in /boot/grub/custom.cfg:

```
menuentry "Ubuntu" {
set root=(hd0,5)
linux /boot/vmlinuz
initrd /boot/initrd.img
}
```

Is this right, or do I have to type in something else? Thanks.

---

### Post by mamamia88 on 2013-04-02
did you try the simple way of using os-prober first to generate a grub.cfg automatically?  Also if anything can help this is it [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)

---

### Post by oldfred on 2013-04-02
+1 on mamamia88 post
It looks like you have to install os-prober with Arch to use it. And that is the easiest way.
You have to have version number of the kernel as it is in /boot. You should be able to look at the grub.cfg in your Ubuntu boot/grub folder in sda5, if that is your Ubuntu install.

You can also boot from the links Ubuntu puts into / (root), these links are updated to be the most current kernel.

 menuentry "Ubuntu on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}


 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by bashhimup on 2013-04-03
But, Pacman won't download os-prober. It shows this:

```
warning: failed to retrieve some files from community
error: failed to commit transaction (download library error)
Errors occurred, no packages were upgraded.
```

And this happens for anything I download.

---

### Post by mamamia88 on 2013-04-03
> **bashhimup said:**
> But, Pacman won't download os-prober. It shows this:

```
warning: failed to retrieve some files from community
error: failed to commit transaction (download library error)
Errors occurred, no packages were upgraded.
```

And this happens for anything I download.

first make sure you have a working internet connection. then update the mirrors list.   

```
ping -c 3 www.google.com
``` then use the script found here to automate the rotation of a new pacman mirror list based on up to date info.  [https://wiki.archlinux.org/index.php/Mirrors#Script_to_automate_use_of_Pacman_Mirrorlist_Generator](https://wiki.archlinux.org/index.php/Mirrors#Script_to_automate_use_of_Pacman_Mirrorlist_Generator)  just copy and paste that into a text editor,save it somewhere that you'll remember, cd to that directory, chmod +x file, ./file, and hit yes when asked to replace old mirrorlist.   I hope that helps you.

---

### Post by bashhimup on 2013-04-03
> **mamamia88 said:**
> first make sure you have a working internet connection. then update the mirrors list.   

```
ping -c 3 www.google.com
``` then use the script found here to automate the rotation of a new pacman mirror list based on up to date info.  [https://wiki.archlinux.org/index.php/Mirrors#Script_to_automate_use_of_Pacman_Mirrorlist_Generator](https://wiki.archlinux.org/index.php/Mirrors#Script_to_automate_use_of_Pacman_Mirrorlist_Generator)  just copy and paste that into a text editor,save it somewhere that you'll remember, cd to that directory, chmod +x file, ./file, and hit yes when asked to replace old mirrorlist.   I hope that helps you.

Oh, I just forgot to connect to the internet. Thanks!

So, I just started os-prober, and it says that my Ubuntu installation is actually on /dev/sda6. So do I just change it in /boot/grub/custom.cfg, or what?

---

### Post by mamamia88 on 2013-04-03
check the wiki entry on grub2. Not particulary sure since when I used arch I made sure it was correct the first time and never bothered to tinker with it. It was also the only os on my computer at the time.

---

### Post by bashhimup on 2013-04-03
I figured out how to use os-prober. Just generate the grub.cfg. I can boot into ubuntu again! Thank you! The only tiny problem is that there is no ubuntu loading screen, just a blinking underscore, but that's pretty much nitpicking. Thanks guys! :)

---

