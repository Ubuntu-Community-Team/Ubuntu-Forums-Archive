---
title: "Installation help needed"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Skneepa on 2007-06-17
Hi everyone, here I am once more asking beginner questions. I was unable to boot from the 7.04 live cd as I came across this "can't access tty" error. I found a solution in the forums and managed to overcome it (I typed all_generic_ide and everything worked in order) . But what happens after install? I remember seeing that you had to add some lines in a configuration file in order to boot normally every time without the cd. What exactly do I have to add and in which file? How do I edit this file? By opening a terminal? Do I have to boot from cd first in order to access the OS without errors? Please, I would appreciate it if you give as many details as possible! I am a total noob!;) Thanks in advance.

---

### Post by logos34 on 2007-06-17
If you can get through the installation successfully but it won't boot into ubuntu, go back and select the ubuntu kernel at the top of the grub menu, hit 'e' key, and edit the 'kernel' line by adding 'all_generic_ide' to the end. Then hit enter and b to boot.  If it works, open a terminal and type:

cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst.

When it opens add the line as shown below, save and close.

For example, assuming an install of 7.04 Feisty with root on hda1, it would look something like this:

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
[COLOR="Blue"]kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splas[/COLOR]h [COLOR="Red"]all_generic_ide[/COLOR]

...

Instead of 'root=/dev/hda1' you may have a 'root=UUID=[#####]'.  If you still have problems you could try replacing the UUID with the /dev/hda1 format.

---

