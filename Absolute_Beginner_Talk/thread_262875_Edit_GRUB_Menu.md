---
title: "Edit GRUB Menu"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by PietreWitobi on 2006-09-22
Can I?  I really like to.

Currently My GRUB menu displays:

Ubuntu, kernel 2.6.15-27-386
Ubuntu, kernel 2.6.15-27-386 (recovery mode)
Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386 (recovery mode)
Ubuntu, kernel 2.6.15-23-386
Ubuntu, kernel 2.6.15-23-386 (recovery mode)
Ubuntu memtest86+
Other operating systems:
Microsoft Windows XP Professional



Thing is, I don't have Windows XP anymore - It's Windows Vista, so I know that the menu item is seperate from what it points to.  I'd like it to read (pointing to Kernel 2.6.15-27-386):

Ubuntu
Ubuntu (reovery mode)
Ubuntu  memtest86+
Other operating systems:
Windows Vista Ultimate


Is it possible?  Thanks ahead of time.

---

### Post by louis_nichols on 2006-09-22
sure it's possible! :)

you have to follow 2 steps:

[LIST=1]
[*]open the right file for editing:
```
gksudo gedit /boot/grub/menu.lst
```
[*]find and edit the relevant text. instructions for how to do this are in the file and all over the web :). In your case, just find the segment "Microsoft windows XP professional" and replace the text with whatever your heart desires. After this, just save the file.
[/LIST]

---

### Post by JAwuku on 2006-09-22
If you want to remove the obselete linux kernels, you can do this via apt-get or synaptic. This automatically removes the items from the Grub menu.

Just issue:

```
sudo apt-get remove linux-image-2.6.15-23-386
sudo apt-get remove linux-image-2.6.15-26-386
```

---

### Post by PietreWitobi on 2006-09-22
Thanks All - I just couldn't figure out where the damn list was.  I tried a search but this turned out well.

Thanks

---

