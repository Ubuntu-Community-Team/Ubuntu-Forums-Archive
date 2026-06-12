---
title: "always slow boot ..."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by phydreamer on 2008-04-17
everything seems to be ok but my boot is really slow... 
i wait about 2:30 minutes to boot up unless i press alt+F2 and ...voila
Also when loading at boot up i just see a complete black screen(unless i press alt+F2 again for the log),i don't see the ubuntu loading bar-i think it has to do with the boot up also...

any suggestions?

---

### Post by spiderbatdad on 2008-04-17
[http://ubuntuforums.org/showthread.php?t=757091](http://ubuntuforums.org/showthread.php?t=757091)

[http://ubuntuforums.org/showthread.php?t=757728](http://ubuntuforums.org/showthread.php?t=757728)

---

### Post by phydreamer on 2008-04-17
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=757091](http://ubuntuforums.org/showthread.php?t=757091)

[http://ubuntuforums.org/showthread.php?t=757728](http://ubuntuforums.org/showthread.php?t=757728)

ok i saw them but i am a bit newbe so i think it would be better if someone lead me step by step...

---

### Post by spiderbatdad on 2008-04-17
You can try it as a one time boot without editing /boot/grub/menu.lst like this:
Restart your system. press esc, if necessary to bring up the grub menu. If it comes up on its own...OK. At the grub menu...if necessary, move, with the arrow key, to the kernel you intend to boot. Press f6. You will see a line beginning with the word 'kernel.'  Use the arrow key to move to the end of the line. Backspace to delete the words 'quiet splash.' Add the word 'lapic.' Hit enter.
Expect a much faster boot. If it fails, try again with the words 'noapic nolapic'  (no quotes.)

---

### Post by phydreamer on 2008-04-17
> **spiderbatdad said:**
> You can try it as a one time boot without editing /boot/grub/menu.lst like this:
Restart your system. press esc, if necessary to bring up the grub menu. If it comes up on its own...OK. At the grub menu...if necessary, move, with the arrow key, to the kernel you intend to boot. Press f6. You will see a line beginning with the word 'kernel.'  Use the arrow key to move to the end of the line. Backspace to delete the words 'quiet splash.' Add the word 'lapic.' Hit enter.
Expect a much faster boot. If it fails, try again with the words 'noapic nolapic'  (no quotes.)

are there any risks i might consider?

---

### Post by spiderbatdad on 2008-04-17
As far as I know this one-time method is completely safe. If your system never boots...just shut down. But I do not think you will have to resort to that.

---

### Post by phydreamer on 2008-04-17
i also came across this...[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
what do you think?

---

### Post by spiderbatdad on 2008-04-17
Absolutely...I believe I suggested the same thing in the second link I provided to you. However this step is later in the process. It will only shave a few seconds off boot time....your problem is related to hardware detection during the boot process.
Did you read the output of your dmesg run in the terminal....why don't you try that. The second link, again, outlines the process.
Here it is again...post # 6, 7, 8....[http://ubuntuforums.org/showthread.php?t=757728](http://ubuntuforums.org/showthread.php?t=757728)

---

### Post by phydreamer on 2008-04-17
tried some things no luck.... if attach on post the dsmeg output would that help?

---

### Post by spiderbatdad on 2008-04-17
sure. be kind and copy/paste it into a text file. Then right click on it and select "archive." Upload the archive using the manage attachment tool below the reply window.

---

### Post by phydreamer on 2008-04-17
ok this is it... waiting..

---

### Post by phydreamer on 2008-04-17
i mean is this the right fight file?
and thnx

---

### Post by spiderbatdad on 2008-04-17
Ok. it looks like you have added 'profile' to the kernel line in the file /boot/grub/menu.lst. You don't want that. It is a one-time command to be run from grub menu at start up...and you would need a space after 'splash.'

Also it looks like the process is hanging at video detection. I suggest this:

Open the terminal: ```
sudo nano /boot/grub/menu.lst
```

use the arrow key to scroll down to a section that looks like this:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro** lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic
]
```

See above where I have highlighted 'lapic pci=routeirq in the line that begins with the word 'kernel.'
Delete the end of the line where you have 'quiet splashprofile...or quiet splash...

Type in noapic pci=routeirq
use ctrl-o to save. Hit enter to confirm the file name, and ctrl-x to exit.
Reboot
If it fails to improve upload another dmesg from that boot.

---

### Post by phydreamer on 2008-04-17
> **spiderbatdad said:**
> Ok. it looks like you have added 'profile' to the kernel line in the file /boot/grub/menu.lst. You don't want that. It is a one-time command to be run from grub menu at start up...and you would need a space after 'splash.'

Also it looks like the process is hanging at video detection. I suggest this:

Open the terminal: ```
sudo nano /boot/grub/menu.lst
```

use the arrow key to scroll down to a section that looks like this:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro** lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic
]
```

See above where I have highlighted 'lapic pci=routeirq in the line that begins with the word 'kernel.'
Delete the end of the line where you have 'quiet splashprofile...or quiet splash...

Type in noapic pci=routeirq
use ctrl-o to save. Hit enter to confirm the file name, and ctrl-x to exit.
Reboot
If it fails to improve upload another dmesg from that boot.

much better now! thnx! so from now on this is how it willl boot?
but can we do something also with the log appearing on boot up? if not it is already ok anyway..

---

### Post by spiderbatdad on 2008-04-17
Yes that is how it will boot now...hopefully you're at 35 seconds or less. I would leave it as is.
Now you can use the "profile" option during your next boot. This is a one-time thing. Do not edit /boot/grub/menu.lst again.

Do you get a grub menu to select operating systems at startup? If not, you need to press escape before the system starts to boot.

Then press 'e' for edit. Use the arrow key to move down a line to the line that starts with 'kernel,' and press 'e' again.  Move to the end of the line. DO NOT delete anything. Add a space and the word profile. Hit enter and press 'b' to boot. The boot will take a few extra seconds this time, while it profiles the procedure.
Cheers.

---

