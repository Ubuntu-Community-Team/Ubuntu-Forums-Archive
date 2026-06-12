---
title: "Remap the 'eject'-key to 'delete forward'"
date: 2013-05-18
forum: Apple Hardware Users
---

### Post by ole01 on 2013-05-18
Hi all,

is there a way to remap the useless 'eject'-keyto the 'delete forward'-function on my macbook pro keyboard?
I already searched for a way to do this, but as I figured out, xev is not getting a keycode when using the eject key.
Maybe some of you have had the same issue. I'm looking forward to hearing or reading any useful hints.
My OS is Ubuntu 13.04 (64 bit) on a MacBook Pro 9,2 (mid 2012).

Thanks in advance and good night.

---

### Post by BDenis on 2013-06-03
Macbook keyboard is painful.
Apple made excellent notebook. Best screen that I ever seen, unibody, long battery life, keyboard lighting!
But keyboard layout... It's not bad, it's just TERRIBLE! Small enter, bad fn position, no delete, small cursor keys, no home, end, pg_up, pg_dw.

Ok, let's do something with this.
Ugly keyboard — ugly hack! I patch hid_apple module and now it provide to parametrs: swapctrfn & use_ejectcd_as_delete.
swapctrfn must be provided on module load (like "insmod hid_apple swapctrlfn=0"), use_ejectcd_as_delete you can change on the fly (echo 1 > /sys/module/hid_apple/parameters/use_ejectcd_as_delete).

In attached file you can found kernel 3.8 amd64 compiled module, patch and patched module source.

To compile module follow this steps:
1. Download kernel source code.```
apt-get source linux-source-3.8.0
```
2. Place hid-apple.c from attach to ~/linux-3.8.0/drivers/hid/ (it must replace original one).
3. Go to hid drivers dir.
```
cd linux-3.8.0/drivers/hid/
```
4. Compile hid modules.
```
make -C /usr/src/linux-headers-`uname -r`  M=`pwd`  modules
```
5. Try load compiled module.
```
sudo rmmod hid_apple && sudo insmod ./hid-apple.ko swapctrlfn=1 use_ejectcd_as_delete=1 fnmode=2
```

For permanent effect do following:
1. Replace original kernel module.
```
sudo cp hid-apple.ko /lib/modules/3.8.0-23-generic/kernel/drivers/hid/
```
2. Add startup parametrs.
```
sudo echo options hid_apple fnmode=2 swapctrlfn=1 use_ejectcd_as_delete=1 > /etc/modprobe.d/hid_apple.conf
```
3. Update initramfs.
```
update-initramfs -u
```

---

### Post by r-jan on 2013-11-27
Hello and thanks for your reply to OP. I really need to get my Apple Wireless keyboard to work like a proper keyboard.

However, I'm having some trouble following your guide. At step 4, when I have to compile the module, I get the following console output:
```
**user@user:/usr/src/linux-headers-3.8.0-33-generic$ sudo make -C . modules**
[sudo] password for user: 
make: Entering directory `/usr/src/linux-headers-3.8.0-33-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --silentoldconfig Kconfig
make: Leaving directory `/usr/src/linux-headers-3.8.0-33-generic'
make: Entering directory `/usr/src/linux-headers-3.8.0-33-generic'
make[1]: *** No rule to make target `/usr/src/linux-headers-3.8.0-33-generic/arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'.  Stop.
make: *** [archheaders] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-33-generic'
user@user:/usr/src/linux-headers-3.8.0-33-generic$ cd
user@user:~$ make -C /usr/src/linux-headers-`uname -r`  M=`pwd`  modules
make: Entering directory `/usr/src/linux-headers-3.8.0-33-generic'
scripts/Makefile.build:44: /home/user/Makefile: No such file or directory
make[1]: *** No rule to make target `/home/user/Makefile'.  Stop.
make: *** [_module_/home/user] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-33-generic'

```

I'm currently using Ubuntu 13.10, 64 bit.

I apologies if I follow the tutorial wrong, since I'm pretty new to Linux, but I really hope you can help me :)

r-jan

---

### Post by runningduck on 2014-10-05
> **ole01 said:**
> Hi all,

is there a way to remap the useless 'eject'-keyto the 'delete forward'-function on my macbook pro keyboard?
I already searched for a way to do this, but as I figured out, xev is not getting a keycode when using the eject key.


Here is an easy answer and does not require recompiling the kernel.

[LIST=1]
[*]Clear the eject button functionality
[LIST]
[*]Load _System Settings_
[*]Select _Keyboard_
[*]Select _Shortcuts_ tab
[*]Select the _Sound and Media_ group
[*]Click on _Eject_ line
[*]Hit the _Backspace_ key to disable the eject function mapping
[*]
[/LIST]

[*]Map the delete function
[LIST]
[*]Add "keycode 169 = Delete" to ~/.Xmodmap file
[*]Make sure the .Xmodmap file gets loaded upon login
[*]To load mapping immediately type: xmodmap ~/.Xmodmap
[*]
[/LIST]

[*]
[/LIST]

As a note, once the functionalilty is cleared in Gnome's keyboard shortcuts the button will generate a keycode when using the xev command.

---

