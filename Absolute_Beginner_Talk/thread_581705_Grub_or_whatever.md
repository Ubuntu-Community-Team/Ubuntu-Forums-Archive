---
title: "Grub or whatever"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by brokenlighter on 2007-10-19
When I start my computer I get to the list of what I can boot too or whatever. But the list is like.

> 
Ubuntu 20.16
Ubuntu 20.16 Recovery
Ubuntu 17.12
Ubuntu 17.12 Recovery
Ubuntu 17.10
Ubuntu 17.10 Recovery
Ubuntu memtest+
Other Operating Systems
Windows XP

How do I make it so that it is just Ubuntu and then Windows?

I only want two options.

---

### Post by Duck2006 on 2007-10-19
Edit your menu,lst

gksudo gedit /boot/grub/menu.lst

---

### Post by molly_001 on 2007-10-19
From the Console (Terminal), type:

sudo gedit /boot/grub/menu.lst    [Enter]

After a moment, a text editor will appear, with a long text file.  Near the bottom you will find all of the OS boot choices.

Put a number sign (#) in front of the lines for any you wish to not appear.
Please note you need a (#) sign in front of each of the lines for each choice.  There are usually three of four lines related to each boot option.

Save the file.  Reboot.

---

### Post by Pumalite on 2007-10-19
gksudo gedit.....-

---

### Post by brokenlighter on 2007-10-19
Thank you very much Duck and Molly

---

