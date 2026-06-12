---
title: "CD command is not working/Installing Gutenprint"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-30
Hi,
The latest Gutenprint drivers are out and they support many of the latest Epson Printers, which is great news !!

See [http://sourceforge.net/project/showfiles.php?group_id=1537](http://sourceforge.net/project/showfiles.php?group_id=1537) 


Now,, the only thing is installing the tar.bz2 folder. I extracted it and I get desktop directory ok, but no matter what I do, it won't give me a directory for the folder itself. I've tried entering all of these:

cd gutenprint-5.1.1

or 

cd Gutenprint-5.1.1

or 

cd gutenprint-5.1.1.tar.bz2

or 

cd Gutenprint-5.1.1.tar.bz2

I always get a response that there is 'No Such File or Directory'

Does anyone know what I'm doing wrong?

I appreciate any help. I'd love to get my printer right with Linux,....Thanks, Frank

---

### Post by Sparkster185 on 2007-05-30
Try doing this:

```

cd ~
find . -type d -name "*gutenprint*"

```

That will search your entire home directory (recursively) for folders (-type d) containing the string "gutenprint".

---

### Post by moredhel on 2007-05-30
type

 ls

which shuold give you a list of everything there.

find out whether it is a G or g, then type the first letter, then press tab.

beaten. try the above first...

---

### Post by kernel tom on 2007-05-30
well if u extracted it to ur desktop

then go to the terminal and type

cd Desktop/gutenprint-5.1.1/

the caps do matter, if it's extracted as 'G' be sure to use the capital


or you can go into the folder on ur desktop, right click and use "open terminal here"

---

### Post by pxwpxw on 2007-05-30
You might find it by:

```

sudo find / -name  '*utenpr*'

```

Too late.

---

### Post by Brightbelt on 2007-05-30
Thanks Kernel Tom, and everybody else as well. Since I already had a Desktop$ directory, I had no idea I had to enter the Desktop command again to get to the file directory on the desktop. 

So, cd Desktop/filename worked. NOW>>>>>>.............the make command worked, but I got an error on the 'make install', any idea what may have happened?

I did go thru the System/Admin/Printer interface to check if maybe, the RX 580 was added successfully, but it's still not there.

I will try rebooting; does anyone else have any ideas? 

Many Thanks for helping, Frank

---

### Post by Sparkster185 on 2007-05-30
Pretty much every make script I've ever used requires you do execute it as root.  You need to put "sudo " in front of it, then you'll be prompted for your password.

If that still errors, copy/paste the output for us.  If it scrolled off the screen, you can re-direct it to a file and then examine that

```

sudo make install > ~/make_output.txt

```

the file "make_output.txt" will be in your home directory.

---

### Post by Brightbelt on 2007-05-30
OK, A lot of Thanks, the sudo seemed to make the difference. 

NOW,...I do have the 2 new gutenprint drivers (simple version/regular vs.) in the System/Admin/Printer interface. BUT, my RX580 is STILL not listed. I've tried the RX 510 with the new driver and it didn't work. I may try the RX600.

Other than that, are there any other ideas?? Many Thanks for following up with me, Frank

---

