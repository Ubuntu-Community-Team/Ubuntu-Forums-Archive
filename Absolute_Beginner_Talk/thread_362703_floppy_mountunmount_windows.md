---
title: "floppy mount/unmount windows"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by frog3764 on 2007-02-15
Greetings to the Group - I am having trouble understanding the floppy drive in Ubuntu.  Do I have to mount each time I insert a floppy to use, then unmount when I take it out?  By doing this, does this screw up the floppy so Windows XP can't read it?  That seems to be my problem.  Please walk me through this as I need to copy a few jpegs to the floppy so someone else can get them  off of Windows.  The only files I am referring to would be .txt, jpeg, or maybe pdf.  Any and all information will be appreciated.  

Thanks in advance,
Jim

---

### Post by crispy_420 on 2007-02-15
Go to Places -> My Computer from top bar on Gnome.
For me the floppy was listed as the first drive.

Write click and format, it should be the last option there.

Select "High Density 3.5" (1.44MB)" --- assuming you are using a standard/modern floppy

Select "DOS (FAT)" --- So windows can read/write. I don't see any reason to name it.

Formatting Mode: I'm into a full format so I went with the "Thorough" option.

Now that you have a clean disc, exit that window. Now you can mount it. So from Places -> My Computer, right click and select mount. Now you should be able to add files.

Quick question, with only 1.44MB of storage, why not just email the files?

---

### Post by frog3764 on 2007-02-15
Hey thanks Crispy,  I am in the Philippines and my nephew needs to furnish some documents for a new job he has applied for.  I scanned them and he wants them on a floppy so that his new manager can pull them off.  They may not have an email address.  He has about 6 docs and I can put them on a couple of floppys.  After doing what you said, will a Windows system still be able to read the files, as long as they are txt or jpegs?

---

### Post by crispy_420 on 2007-02-17
Windows should not have a problem. First of all it will be a DOS (FAT32) format, native to windows. And as long as you use a standard format (eg. .txt/.jpg/etc.), I don't a problem at all.

Just to be on the safe side, I have to boot my WinXP system later and I'll test it. Give me a few hours and I'll get back to you. I'll test three different Windows installs (WinXP Pro, WinXP Home and Win2000).

---

### Post by rusty4r on 2007-02-17
I just tried it with a .jpg, a .gif and a .txt file that I created with gedit. Then I started up Open Office writer and saved a file as .txt, and as .doc, and as .html, and as .rtf.

I then unmounted the floppy moved it to my wifes pc with xp. I was able to read all the text files and view the pics.

Just realized that I forgot to try a pdf.

Anyway I started by formatting the floppy as dos fat using the thorough option

---

### Post by crispy_420 on 2007-02-17
Didn't get a chance to try yet but it looks like it was a success. There is no reason a pdf would not work though. If Windows can read it, you've won the battle. I don't think you need any more help from me.

Tell your nephew good luck on the job!

---

### Post by frog3764 on 2007-02-18
Hey guys, thanks.  I will try it again, but so far it's a bust.  I must be  doing something wrong.  I'll report back.

---

### Post by rusty4r on 2007-02-18
my mount point for floppies is /media/floppy1 I don't know what the "1" means but your fstab file ( /etc/fstab ) will tell you where yours is. When I open places in the top menu bar and choose My Computer my nautilus browser opens with a list of places on the left including floppy1.

I right click floppy1 and format using the directions above, then I right click and mount, then add my files, right click and unmount, and remove the floppy. This floppy is readable in windows.

---

### Post by crispy_420 on 2007-02-19
Good to see it worked as I just never tried it myself until you brought it up. Maybe I really am starting to be a true geek!  :)

---

