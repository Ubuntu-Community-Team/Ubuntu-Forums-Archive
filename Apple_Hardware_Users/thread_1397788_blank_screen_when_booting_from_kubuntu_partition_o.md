---
title: "blank screen when booting from kubuntu partition on macbook"
date: 2010-02-03
forum: Apple Hardware Users
---

### Post by stallrich42 on 2010-02-03
I am trying to install kubuntu on my macbook. I am able to boot from the CD and install fine, but when I try to boot from the linux partition the cursor blinks for a while, then the screen goes blank.

I have used the rEFIt partition utility, but when I try to reinstall the grub bootloader as described here: [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11), it says "sudo: grub: command not found"

When it try "grub", it says:
"The program 'grub' is not currently installed. You can install it by typing:
sudo apt-get install grub"

I do this, but the installation fails.

---

### Post by stallrich42 on 2010-02-03
I got grub to install, but now when I enter
> find /boot/grub/stage1
it says "Error 15: File not found"

---

### Post by Eddy RL on 2010-02-05
That's it.
You can "sudo chroot /mnt/ubuntu /bin/bash" to get into your installed ubuntu OS, in case you've already mounted it.
And then, you can "sudo apt-get install grub", or any other cmds to change current installed os, after which, you can type "exit" to log into the CD-Rom os.

Unfortunately, these guided commands don't do any good to the booting problems you've met.
And I'm trying to figuring it out.
Good luck

---

### Post by ed12348 on 2010-02-07
i had the same issue in ubuntu on my macbook 5,2 where i would get a flashing cursor then a blank screen and nothing else. Have you tried pressing 'e' in grub when selectin linux, and then at the end of the kernal entry adding acpi=off

this worked for me. I hope it has been of some help :D

---

### Post by stallrich42 on 2010-02-07
I tried adding acpi=off, but the same thing happens: the cursor blinks a few times, and the the screen goes blank.

---

