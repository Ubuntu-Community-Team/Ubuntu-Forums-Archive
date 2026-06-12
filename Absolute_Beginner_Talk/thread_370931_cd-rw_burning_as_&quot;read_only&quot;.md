---
title: "cd-rw burning as &quot;read only&quot;?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by doogg on 2007-02-26
over the weekend i was using open office to set up a spreadsheet to manage my checking and savings accounts.  i don't want to save these files on the hard drive so i thought i would save them to a cd-rw, that way i could edit as necessary and then resave.
     all went well until i reopened the newly burned files to edit a few things and found that i can't edit due to them/cd being "read only".  i tried to change the properties but it won't let me.  i don't recall being prompted as to whether i wanted them saved as read only or not.
     i'm new to ubuntu and so far am enjoying using it but i'm still feeling my way around.
     did the burning using *places>cd/dvc creator>write to disc*.
     how do i/can i format a cd-rw to behave like a floppy so i can open, edit, and resave files?
     is there software in the repositories that will suit my pupose better?
     i don't think it's open office doing this; i think the burning program is defaulting to read only, not sure though.
     the up side is the info in these files is nothing that can't be easily replaced.
     i'm running 6.06. this is the first snag i've had, been going about a week or so, just internet & such, no conflicts at all.  installation and internet set up went without a hitch.
      i'm only fairly computer literate and new to ubuntu, so please be gentle.

---

### Post by Quintin Riis on 2007-02-26
sudo apt-get install k3b

Also, for this kind of thing,  you should be using a USB flash drive, no?

---

### Post by netkid91 on 2007-02-26
CD-RW discs, while can be rewritten and erased, are not designed to be used as dynamic filesystems.  They were made to be burned like regular CD's, and then erased when needed again.  Don't burn until it's finished, and erase it when you need to burn again.

---

### Post by bodhi.zazen on 2007-02-26
General comment :

Be careful with rw disks. The technology is not very stable, even in windows, and data loss is possible, even frequent.

If the data is sensitive at all you should go ahead and burn the disk.

> **netkid91 said:**
>  Yeah, sure....pirated copies of Windows XP are free. So is Ubuntu, and it's LEGAL!

I am not sure this hits home with many "pirates". 

The fact that up to 50 % of pirated copies of M$ have root kits (the OS has been provided for "free" so others may have access to your box) may interest them ...[/QUOTE]

---

