---
title: "Grub Bootloader Question"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Spydr4590 on 2008-01-18
I've figured out how to set the count down to zero so that it doesn't tell you to press escape to enter the bootloader.. However if you do press escape you can still goto the bootloader. How do I disable the escape key for grub during boot up?

---

### Post by gn2 on 2008-01-18
> **Spydr4590 said:**
> I've figured out how to set the count down to zero so that it doesn't tell you to press escape to enter the bootloader.. However if you do press escape you can still goto the bootloader. How do I disable the escape key for grub during boot up?

Why would you want to?
How would you boot in recovery mode if you did that?

---

### Post by Spydr4590 on 2008-01-18
I don't want to be able to boot into recovery mode. I like to live dangerously :D

---

### Post by fatality_uk on 2008-01-18
I guess it's technically possible, maybe a post-bios dos app :)
But as gn2 said, not really a good idea. Playing Russian Roulette is fun untill you lose ;)

---

### Post by biohypnotix on 2008-01-18
I'm not sure if you can totally disable ESC to enter GRUB although you can password protect GRUB boot loader. I haven't tried it yet myself. I just have my BIOS prompt for password before GRUB loads. You could have both the BIOS and GRUB password protected. Google or use search feature on these forums. I'm sure someone has instructions on how to password protect GRUB.

---

### Post by c0met on 2008-01-18
Here's a couple of ideas...

In the file, /boot/grubmenu.lst, the following appears...

> 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu


I'd imagine that if you remove the # sign as below, then the bootmenu will be hidden. As I haven't tried this, I am not sure what it does but my experience tells me that the #-lines are there to give you ideas about how to use commands in GRUB.

> 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Blue"]hiddenmenu[/COLOR]


And even though you like to live dangerously, you can still get into it by hitting ESC. If you pretend you didn't read that, though, you will never know so you can keep on living dangerously :) 

[COLOR="Purple"]**THE EASIEST APPROACH**[/COLOR]
In [COLOR="DarkRed"]**System >> Administration >> Startup Manager**[/COLOR] and then in the[COLOR="DarkRed"] Boot Options[/COLOR] tab, there is a checkbox to disable bootloader (presumably that does something with the "hiddenmenu" command.)

Tomosaur here on UbuntuForums has a great article on GRUB that you might want to look through. The URL is
[Tomosaur's Grub Page]("http://ubuntuforums.org/showthread.php?t=228104")

Lastly, here is the Grub manual
[Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html")

---

### Post by Spydr4590 on 2008-01-18
Thanks Comet. I've already did that though :)

---

### Post by dstew on 2008-01-18
Grub is, I believe, open source software. You could edit the code and compile your own version that did not have the esc option.
EDIT: See [Hacking Grub for Fun and Profit]("http://phrack.com/issues.html?issue=63&id=10&mode=txt").

---

