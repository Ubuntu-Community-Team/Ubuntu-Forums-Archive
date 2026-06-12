---
title: "Lost login"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by backflip on 2008-02-28
Hi
I was trying to get scrolling to work on my synaptics touchpad and installed and then removed gsynaptics. When it removed   through synaptics package  manager it took other stuff with it. Now I can't log-in. Ubuntu boots to the ubuntu logol with the running bar beneath, but after a very short time it reverts to a text based interface which wants my login and password. Once I supply that it remains in text mode. How do I get back to the graphical interface? I'm having to use my desktop to post this.
Thanks

---

### Post by glennric on 2008-02-28
Try the following from a command line.
Type 
```
sudo nano /var/log/apt/term.log
```
Go to the end of the file and see what it was that was uninstalled with gsynaptic.
The reinstall all of that with
```
sudo apt-get install pgknames
```
Then type
```
sudo /etc/init.d/gdm restart
```
If that doesn't work, then we will see what else is wrong.

---

### Post by backflip on 2008-02-28
Is this what you mean, I'm completely unsure:-
'preparing to replace linux-image-2.6.22-14-generic 2.6.22-14 47
Done
Unpacking replacement linux-image 2.6.22-14-generic........
running postrm hook script /sbin/update-grub
searching for grub installation directory......found:  /boot/grub
searching for default file.........found: /boot/grub/default
testing for an existing Grub boot menu.lst file..........found: /boot/grub/menu.lst
searching for menu image.........none found, skipping
found kernal: /boot/vmlinuz-2.6.22-14-generic
found kernal: /boot/memtest86+.bin
updating /boot/grub/menu.lst.....done

There follows a list about replacing firefox gnome support 2.0.0.11+2nobinonly-OubuntO. 7.10
and unpacking replacement firefox-gnome support.

There are about 15 similar lines followed by 'inpacking replacement linux-headers 2.6.22.-14-generic

---

### Post by glennric on 2008-02-28
Try typing
```
sudo tail -n 25 /var/log/apt/term.log > ~/apt-term
```
After doing this there should be a file name "apt-term" in your home directory.
Post that file for me to look at.

---

