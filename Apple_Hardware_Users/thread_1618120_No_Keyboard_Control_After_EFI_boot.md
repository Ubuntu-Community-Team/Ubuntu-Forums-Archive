---
title: "No Keyboard Control After EFI boot"
date: 2010-11-10
forum: Apple Hardware Users
---

### Post by Ubuntious on 2010-11-10
[I]Machine: 2008 Mac Pro
Keyboard: Aluminum/wired/numeric keypad/US layout
Kernel: 2.6.35-22-generic x64 (maverick)
Bootloader: GRUB 1.99 Beta[/I]

I have been trying to EFI boot Ubuntu since June - without success. My goal, for 
now, is to boot into an initramfs environment succesfully. 

I'm booting with these grub commands:

insmod efi_uga
linux (hd1,gpt1)/ubuntu/vmlinuz-2.6.35-22-generic video=efifb noefi
initrd (hd1,gpt1)/ubuntu/initramfs-2.6.35-22-generic

If "noefi" is missing, the screen goes blank and stays blank. I suspect the kernel is 
hanging (no disk noise).

After I boot into the initramfs, there is no keyboard control. That makes it hard to 
diagnose the problem.

I have tried other kernels (with apple_hid compiled in). Same problem.

The keyboard is connected to the USB hub on an Apple Cinema Display, and the ACD 
is connected via a USB cable to the Mac Pro. It's not practical here to make a direct
connection, but that the above setup is common with this machine.

Although the keyboard doesn't work in  the initramfs, and the CAPS LOCK light won't 
go on there when the key is pressed, the keyboard does work before that inside GRUB.

Any help very much appreciated, as I'm on the verge admitting defeat, which I'd 
prefer not to do :-)

Thanks.

---

### Post by pieterberlijn on 2011-01-23
Currently running into the same problem. Did you happen to find a fix?

---

### Post by srs5694 on 2011-01-23
Despite the claim that it's "not practical" to connect the keyboard directly to the computer, that would be my first suggestion. Even if it's just an awkward test configuration, hook up a keyboard directly to see if that helps. If it does, you can work from there to find a better solution. If not, then you've at least rule out one possible cause.

Another option is to configure the computer (using BIOS boot mode, if necessary) to run an SSH server. You can then boot and log in using that for debugging. Be sure to test with the "noefi" option removed from GRUB, too; it's possible that just the video is hanging and that you'll be able to log in remotely and find the cause of the video problems.

Also FWIW, I've got a [Web page on EFI-booting Ubuntu on a Mac Mini.](http://www.rodsbooks.com/ubuntu-efi/index.html) I didn't run into this specific problem so I can't address it, but perhaps you could compare your approach to getting it done to my approach. If they're different enough, perhaps my method would bypass the issues you're having.

---

### Post by pieterberlijn on 2011-01-23
Unfortunately a USB keyboard also fails to work (for me at least). It says it has found a usb device, but does not recognize it as a keyboard. How would one debug/edit the modules loaded by initramfs?

---

### Post by srs5694 on 2011-01-23
> **pieterberlijn said:**
> Unfortunately a USB keyboard also fails to work (for me at least). It says it has found a usb device, but does not recognize it as a keyboard. How would one debug/edit the modules loaded by initramfs?

What does "it" refer to in "it says it has found..."? What is the precise error message you're getting? Are you logging in via a network connection or do you just see error messages on the screen?

---

### Post by pieterberlijn on 2011-01-24
Sorry. 'it' refers to what I believe to be initrd; Since copying it is not possible (and the machine is currently not here), it reports something along the line: [xx.xx] high-speed usb device found at 3-1. Tests with other machines show the same line when plugging in a keyboard, but a report that it has been recognized as a keyboard.

Will post more detailed information later, thanks for the help so far.

---

