---
title: "Moving Ubuntu to different hard drive"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by codeblue315 on 2007-06-24
Hi there! I recently installed Ubuntu as I've been looking for an alternative to Vista, and I absolutely love it! I wanted to know, however, as I'm deleting the Vista partition, I wanted to know how I could move the Ubuntu partition over to the hard drive I was using for Vista. I'm an organization nerd, so to be able to do this would be pretty much awesome. Thanks!

-Cody

---

### Post by eljalill on 2007-06-25
Well, you can easily move your home directory through just copying it onto the old vista drive. Moving the / directory will be harder as far as I know, because then grub might have to know, what you did and where the boot files are now. If you really want to move all of it, you could safe your home directory including all configuration files (they are hidden, so make sure, you catch them all. Cntl+H makes them visible) on an external drive. Then make a fresh install onto the desired location and copy your home directory to their too. This way all you configurations will be saved. But you will have to reinstall programs that you already installed....

Well, it's not very elegant, but it should work. But maybe someone else knows something better :) .

cheers

---

### Post by codeblue315 on 2007-06-25
I was hoping I wouldn't have to do that, but it does seem to be the only way. Thanks anyway!!!

---

### Post by Shazaam on 2007-06-25
You can clone it using the gparted livecd. Or dd the install. Search "clone" on the forums here for answers.
Check out the gparted forum too. [http://gparted-forum.surf4.info/](http://gparted-forum.surf4.info/)

---

### Post by lazyart on 2007-06-25
In the long run you're probably better off just moving /home.  This way you can install a new version without overwriting your settings and files.

---

### Post by codeblue315 on 2007-06-25
Ok, thank you all so much for your help. I think I'm just going to reinstall Feisty Fawn and just copy the Home folder. 

Now where did that external hard drive go....? ;)

---

