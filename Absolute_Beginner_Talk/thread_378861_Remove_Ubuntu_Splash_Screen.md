---
title: "Remove Ubuntu Splash Screen"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by lilpaul on 2007-03-07
I really don't like the ubuntu splash screen and would like to remove it, if possible would like to see whats loading up during boot like other distro's

Can anyone help me with this, just instaled linux for the first time today and love it, except for the splash screen.

There are many posts on how to change it, but how do i remove it.

---

### Post by o_fortuna on 2007-03-07
Are you talking about removing the splash screen at bootup and having scrolling text? If so, it's actually not too hard. Press Alt+F2 and type

gksudo gedit

Enter your password and then open /boot/grub/menu.lst

Once in this file, locate the area under

## ## End Default Options ##

You will see the word "title"; two lines below that is "kernel." At the end of that line, simply remove "quiet" and "splash." That will revert you to your scrolling text.

---

### Post by codejunkie on 2007-03-07
> **lilpaul said:**
> I really don't like the ubuntu splash screen and would like to remove it, if possible would like to see whats loading up during boot like other distro's

Can anyone help me with this, just instaled linux for the first time today and love it, except for the splash screen.

There are many posts on how to change it, but how do i remove it.

run ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.orig
```in a termianl to backup the grub menu just for safety, then run ```
sudo gedit /boot/grub/menu.lst
```in a terminal, find the entry for your ubuntu kernel and remove the words quite and splash for example change
```

title		Ubuntu, kernel 2.6.10-5-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

```
to
```

title		Ubuntu, kernel 2.6.10-5-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

```
save the file and close the text editor and the splash will be gone.

---

### Post by lilpaul on 2007-03-07
Thanks for the prompt responce, will give it a go when i get home after night shift.

Roll on 7am :)

---

### Post by komputes on 2008-04-01
Go to :
 
```
     cd /boot/grub/
 
     sudo nano menu.lst
```
 
 change:   *' # defoptions=quiet splash '*  to:   ' *# defoptions=quiet nosplash* '
 
 then:
 
```
     sudo update-grub
```
 
 to make changes take effect on boot-commands.
 
 
[I] Be careful of the #'s, #'s are grub commands in the .lst file.  ##'s are comments.

 Look at this page for more info:

      [https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer)[/I]

---

