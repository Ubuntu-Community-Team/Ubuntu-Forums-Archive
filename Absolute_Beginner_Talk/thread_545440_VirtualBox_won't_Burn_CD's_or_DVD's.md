---
title: "VirtualBox won't Burn CD's or DVD's"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-07
Currently I'm running Ubuntu 7.04  Feisty Fawn
in VirtualBox on Windows XP Pro.

I'd like to back up my Home Folder to a Data CD or DVD but
every program I try can't see that my optical drives are Writers.
I'm thinking that it's because it's running in VirtualBox and more than
likely using some generic driver.

In Gnome Baker, my drive shows up as 
VBOX CD-ROM

Any idea how to fix this?

---

### Post by nonewmsgs on 2007-09-07
i have seen this before and as far as i know virtualbox cannot burn cds, BUT it is possible to make a shared folder that the virtualbox sends to in your /home

in order to do this set the configuration before you try to start the virtual machine and in settings it's an option and at the bottom of the page if gives the command to make it appear as a network folder.  it starts with net use i think.

---

### Post by dca on 2007-09-07
It's not much help but you did install the add'l tools or whatever their called?
 
In VM Ware it's just called VMWare tools...

---

### Post by Orbital75 on 2007-09-07
Yep, They're called the " Guest Additions "

---

### Post by funrider on 2007-09-07
if you have shared folder in your VM, here is a work around:

backup your file by DVD burning program which support virtual image (*.nrg file as nero or *.iso in other program) and set the destination as your shared folder. That way, you just have to burn the dvd or cd image from your main ubuntu OS.

make sense to you?

---

### Post by Orbital75 on 2007-09-07
Yea, that makes perfect sense, the only issue is I don't have file sharing enabled on
windows.  I think I may just back it up to a thumb drive.  I was hoping I could
get the disc burning to work normally without any work arounds but it doesn't 
look like thats possible.

---

### Post by nonewmsgs on 2007-09-07
you dont need file sharing enabled.  all you need is to set it to store the data on the "remote folder"

---

### Post by Orbital75 on 2007-09-08
Ah, I may just give that a try then.
By the way, is it smart to copy all the .invisible files?

---

