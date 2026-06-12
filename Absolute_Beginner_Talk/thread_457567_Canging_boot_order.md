---
title: "Canging boot order"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-05-28
Hi, i have MANNY boot possibility now, fills the whole screen. It's about 9 or 10 options i think....
How do i change so that i get Ubuntu studio low latency on top and vista under that?

---

### Post by JetSirus on 2007-05-28
I would love to know how to do this as well.

---

### Post by starcraft.man on 2007-05-28
Ok, this is an easy question. First off, always back up files when you edit important ones like grub.

To do that open terminal (Applications > Accessories > Terminal) and then type this command in to back up:

```
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup1
```

[Link]("http://www.linuxcommand.org/lts0050.php#cp") for further explanation. 

Then you can use this command to graphically edit the list.

```
gksudo gedit /boot/grub/menu.lst
```

Then be careful, read the text at the top of each of the sections so you understand, your gonna look for when the sections start to read like this. Thats my first boot entry, should be more than 100 lines down the text file.

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=99aae1ba-ce90-4d24-af9d-afd2282ec156 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

Thats my first entry. Each one of these "sets" of lines is an entry in the grub, you can then move them around in the order you like (far as I know). Remember to copy the whole set of lines, they are a group of options, can't split them up. When you finish changing the order, save. then Reboot. 

If you mess up, you can always boot up the live CD, mount your drive if its not mounted, and then reverse the order of the cp command in the terminal and you'll restore the old boot options. Like so:

```
cp /boot/grub/menu.lst_backup1 /boot/grub/menu.lst 
```

That would then restore your file copying it over top of the old one. Thats the end of the tut, I think I covered everything. Take it slow and easy. Feel free to read more of the linuxcommand site :).

I hope I got everything right and some mod (like taurus :p) doesn't appear to correct a silly mistake :)

Edit: Oh and one more thing, if you want the option just to not appear, put #'s before all the lines of a given set, it won't appear next time you boot up.

---

### Post by antoz on 2007-05-28
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by starcraft.man on 2007-05-28
> **antoz said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

Arg, right, well har at least I put the effort and typed out a guide :p. Anyway, ya, I forgot hermanzone had a page on it. Read that too, I just explained only what ya needed, that explains all of the options I think >.>.

Anyway, off to help others/hunt Zerg :p

---

### Post by greybirds on 2007-05-28
If there are too many linux versions showing at boot, you can have grub (the boot loader) only display the most recent few.

A word of warning, though. This involves editing a file that, if corrupted, can be a major pain to get back in working order. 

Open a terminal (Applications > Accessories > Terminal).
Type the following: 
```

cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

```

You'll be prompted for your password, and the file that controls your boot menu will open in the text editor.

About half way down you will see a section where every line starts with ## and #. Search for a line like this:

# howmany=all

Change the word "all" to the number of ubuntu kernel versions you want in the menu. Be certain to leave the # at the beginning.

Save the file, exit the editor, and then type the following in the terminal:
```

sudo update-grub

```

Before you quit the editor, scroll below the section with all the ##'s and you'll find the entries in your boot menu. **Don't edit them!** They're generated automatically from the options above, the lines starting with ## and #. The first bit of code and the modification you made change those options, and the second bit of code (update-grub) re-generates the menu list. A nice system, in my opinion. There's a few other useful options in there, but it's best to leave them as-is until you're comfortable with recovering your system ;).

---

