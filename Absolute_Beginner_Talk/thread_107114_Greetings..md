---
title: "Greetings."
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Tillerman on 2005-12-22
Just a few words to introduce myself to the forum.  I am new to Ubuntu. I have used Red Hat in my business without a hitch for 5 years.  No problems, no data lost.
I upgraded to SUSE only to have many problems that I could not fix, and then tried Ubuntu at the recommendation of a friend.

So far I really like the software despite two real problems:

1.  I can't get the floppy to work even at the terminal.  I have viewed many of the threads but get lost in the bug fixes.

2.  Printer will not fire up.  It worked well in RH but will not respond.  I've changed ports, changed printer cords, even changed printers.  The message says that the test page has been sent but the printer ignors the prompt and stays on the ready mode.

Lexmark IBM 4039 16L

Thanks for help in advance.

Tillerman

---

### Post by bscbrit on 2005-12-22
There seems to be a few printer problems around today.

I do not know your printer.  How is connected USB, parallel, serial, ethernet?

---

### Post by Tillerman on 2005-12-22
[QUOTE=bscbrit]There seems to be a few printer problems around today.

I do not know your printer.  How is connected USB, parallel, serial, ethernet?[/QUOTE]


It is connected by parallel port.  I had a network guru look at the setup and he aproved.  I briefly checked to see if I had a firewall problem.  It seemed to check out ok.  

I agree that it's lack of knowlege that limits the use of Linux.  I'm here to learn.

Tillerman

---

### Post by bscbrit on 2005-12-22
Ok, I gather by the time differences that we are several timezones apart.  I should have been in bed about an hour ago!  Anyway, nice to hear from you again.

According to the manufacturer's datasheet, the parallel port is the default setting for your printer.  Assuming that you haven't made any changes then we will accept that it is correct.  If you manual shows you an easy way of confirming that the parallel is selected then I would suggest that you check it - we might spends hours chasing an non-existant problem.

Then System -> Administration -> Printing, select your 4039 and right click to Properties.  Check that your printer is set as default, the driver is what you expect, and that the Connection tab shows that you have CUPS selected.

Let me know how you get on.

---

### Post by Tillerman on 2005-12-22
Went and did as you suggested.  Actually I have repeated these steps several times in order to get the printer to accept the print job.

The printer remains in the ready mode while the print screen shows that the job has been sent.

I did notice when setting things up that cupps would only highlight if I selected the printer for use as a network printer.  Under "Local Printer" the field was not available.
I am using this printer as a local printer.

Tillerman

---

### Post by bscbrit on 2005-12-22
Yes, you're quite right but it is the end of a long day......  And I apologise for asking you to check again, but you will probably understand that some newbies miss the obvious and then ask for help.

The first thing that I am tempted to do is to remove the current driver and re-install it.  I have no scientific justification for this other than it has worked many times in the past.  But I suspect that you have already been down this route as well.

Is the printer on a dual-boot computer or are you able to confirm that the printer is still functional by temporarily connecting it to another computer?

Have you checked 'dmesg' to see if your parallel port has been identified (look for 'parport')?

Have you got a choice of parallel ports?  Can you try to use the printer on the another one?

I'm just brushing up on the locations and names of drivers for this printer but I think I am going to have to get a few hours sleep before I go much further.  I should be back online in 8 hours or so, if no one else comes along to help.

---

### Post by futz on 2005-12-22
[QUOTE=Tillerman]1.  I can't get the floppy to work even at the terminal.  I have viewed many of the threads but get lost in the bug fixes.[/QUOTE]
There may be a GUI way to do it, but I don't know about it. Anyway, it's trivially easy to do in command line. The floppy is already defined in fstab, so you don't have to modify that at all.

In a terminal, type 'mount /media/floppy0' (without the apostrophes). That's all there is to it. To unmount it, type 'umount /media/floppy0'. Yes, that's 'umount' without an 'n'.

If you use floppies a lot, you can build your own custom launcher to mount the floppy. Or better yet, you can right click on the upper panel (or any panel) and select 'Add To Panel' and select 'Disk Mounter'. This tool mounts and unmounts all types of removable media. Use your middle mouse button to move the new launcher icon to where it suits you.

---

### Post by Tillerman on 2005-12-22
The first thing that I am tempted to do is to remove the current driver and re-install it.  I have no scientific justification for this other than it has worked many times in the past.  But I suspect that you have already been down this route as well.

I have not attempted to remove the driver.  I really wouldn't know how to.  I suspect that the problem is elsewere because in the past, the wrong drive would result in the printer firing up and sending out computer code.  With this setup, the printer never seems to get the signal - it just sits there in the ready mode.

Is the printer on a dual-boot computer or are you able to confirm that the printer is still functional by temporarily connecting it to another computer?

The computer is a single boot.  Following your suggestion I hooked the printer to a IBM laptop under a Win 95 os and it printed fine.


Have you checked 'dmesg' to see if your parallel port has been identified (look for 'parport')?

I just did this - not knowing really what I was doing. An unbelievable amount of data came over the terminal  " Use 'setkeycodes e02a <keycode>' to make it known." repeated over and over.

Have you got a choice of parallel ports?  Can you try to use the printer on the another one?

Only one paralle port.

I'm just brushing up on the locations and names of drivers for this printer but I think I am going to have to get a few hours sleep before I go much further.  I should be back online in 8 hours or so, if no one else comes along to help.[/QUOTE]

Thank you very much for taking time to help me sort these matters out.

Tillerman

---

### Post by Tillerman on 2005-12-22
[QUOTE=futz]There may be a GUI way to do it, but I don't know about it. Anyway, it's trivially easy to do in command line. The floppy is already defined in fstab, so you don't have to modify that at all.

In a terminal, type 'mount /media/floppy0' (without the apostrophes). That's all there is to it. To unmount it, type 'umount /media/floppy0'. Yes, that's 'umount' without an 'n'.

If you use floppies a lot, you can build your own custom launcher to mount the floppy. Or better yet, you can right click on the upper panel (or any panel) and select 'Add To Panel' and select 'Disk Mounter'. This tool mounts and unmounts all types of removable media. Use your middle mouse button to move the new launcher icon to where it suits you.[/QUOTE]

I have attempted to mount the floppy as you suggested several times.  The floppy sounds as though it is engaged and then the screen returns the message 
" mount: I could not determine the filesystem type, and none was specified".  Entering the "mount" command shows that the fd0 is not mounted. 

One thread pointed out that since the terminal was looking for a file type that "msdos" should be entered.  I did this and got no further.

Switching floppies to an unformatted disc I get the message "mount: /dev/fd0 is not a valid block device"

Tillerman

---

### Post by Tillerman on 2005-12-22
If you use floppies a lot, you can build your own custom launcher to mount the floppy. Or better yet, you can right click on the upper panel (or any panel) and select 'Add To Panel' and select 'Disk Mounter'. This tool mounts and unmounts all types of removable media. Use your middle mouse button to move the new launcher icon to where it suits you.[/QUOTE]


I just attempted to do this as per your suggestion.  Actually, I was looking for a launcher button to mount the floppy before your posting but couldn't find it.
Now I get the error message"given UDI is not a mountable volume.

Tillerman

---

### Post by nitricacid on 2005-12-22
Just curious, why did you switch from using REDHAT to Ubuntu if everything was working fine?

---

### Post by futz on 2005-12-22
[QUOTE=Tillerman]I just attempted to do this as per your suggestion.  Actually, I was looking for a launcher button to mount the floppy before your posting but couldn't find it.
Now I get the error message"given UDI is not a mountable volume.[/QUOTE]
How strange. Better post your fstab file here so we can have a look. You'll find the file at /etc/fstab

Here's how mine looks, and I have zero trouble mounting anything at all, including cd's, dvd's, hard drives, usb hard drives, usb sticks, floppies. It all works perfect.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/sda4	/home/futz/drive2	ext3	defaults	0	0
/dev/sdb1	/home/futz/big_drive	reiserfs	defaults	0	0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
Yours may have some differences if you aren't running SATA hard drives like me. The big thing is that your /dev/fd0 line should look the same as mine.

---

### Post by jimrz on 2005-12-22
[QUOTE=Tillerman]I have attempted to mount the floppy as you suggested several times.  The floppy sounds as though it is engaged and then the screen returns the message 
" mount: I could not determine the filesystem type, and none was specified".  Entering the "mount" command shows that the fd0 is not mounted. 

One thread pointed out that since the terminal was looking for a file type that "msdos" should be entered.  I did this and got no further.

Switching floppies to an unformatted disc I get the message "mount: /dev/fd0 is not a valid block device"

Tillerman[/QUOTE]

Did you have a formatted floppy in the drive when you tried to mount? If not, try it with one in the drive...sounds as though it needs to see a file system [from the disk,which if formatted in windows is probs FAT] in order to mount the drive.

---

### Post by Tillerman on 2005-12-22
[QUOTE=nitricacid]Just curious, why did you switch from using REDHAT to Ubuntu if everything was working fine?[/QUOTE]

I'm starting to wonder that myself.  Actually, I had used the same distro for 4 years and was interested in upgrading and trying something new.  Ubuntu looked pretty impressive, and I actually enjoy it ........just got to get past these few gliches.

Tillerman

---

### Post by Tillerman on 2005-12-22
[QUOTE=jimrz]Did you have a formatted floppy in the drive when you tried to mount? If not, try it with one in the drive...sounds as though it needs to see a file system [from the disk,which if formatted in windows is probs FAT] in order to mount the drive.[/QUOTE]


Thankyou Thankyou,

I went back through the steps, as you suggested and realized that I had formatted the disk without selecting the native linux formate.  I failed to select the correct format.  Now I can format the disk in the terminal but it still fails to respond graphically with the disk launcher.  

I therefore, just made a custom launcher with the command "mount /media/floppy0" and everything seems to be working OK.

Now if I can just get this printer to work.  

Thanks again for your time and input.

Tillerman.

---

### Post by jimrz on 2005-12-22
glad I could help...wish could help on the printer. I, too, am using Lexmark (not a very *nix friendly brand, which is strange since they have their roots in IBM) but fortunately Breezy saw it on initial install and selected a driver - lxm320-tweaked  (recommended) (Suggested) which is working fine.

---

### Post by bscbrit on 2005-12-23
Removing and reinstalling the driver is not difficult, in fact, it is very simple but we will look at the results of 'dmesg' first.  

It is always tricky providing advice on a forum. Too little information and the problem doesn't get solved or one's advice doesn't do what was required, too much and some people feel that they are being spoken down to.  My fault, I erred on the side of too little....

To have time to read the output of dmesg, type the following

dmesg | less

The middle character is uppercase '\' down in the bottom left of the keyboard - well it is on mine!  This will allow you to page up, page down or quit 'q'.  First of all, I am looking at the setkeycode message. I know what it means but i do not know why it is occurring in your file.  Can you find where it first occurs and cut and paste that and a few lines preceding it in your next reply? [Tip: if you have a 3 button mouse, this can be most easily achieved by highlighting the text that you want to copy, switching to the place where you want to insert the copy, and pressing the middle mouse button. Whatever is highlighted will appear at the cursor position, ]  
To get to the relevant part of the output relating to the parallel ports, try the following:

dmesg | grep parport

This combination 'pipes' (or sends, if you like) the output of one command (dmesg) to the input of another command (grep).  You are asking grep to find all the lines containing the word 'parport', which is the reference to the parallel port, and to display just those lines on your screen.  Let me know the results of this command also please.

---

### Post by bscbrit on 2005-12-23
I've also just noticed the following thread has started up:

[http://ubuntuforums.org/showthread.php?t=107300](http://ubuntuforums.org/showthread.php?t=107300)

and I'm wondering if the two problems with lexmark printers are related.

---

### Post by bscbrit on 2005-12-23
The next 'problem' that I have found is that, on my machine at least, there is no driver available for your specific printer.  Did you manage to find one on your computer or did you use the Lexmark 4039 10plus driver?  I'm still Googling for more information.

---

### Post by bscbrit on 2005-12-23
Links to the drivers:

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?category=Software&ccs=229:1:0:44:0:0&os_group=Redhat&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?category=Software&ccs=229:1:0:44:0:0&os_group=Redhat&searchLang=en)

which leads to:

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:44:0:0&emeaframe=&fileID=729&searchLang=en&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:44:0:0&emeaframe=&fileID=729&searchLang=en&searchLang=en)

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:44:0:0&emeaframe=&fileID=906&searchLang=en&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:44:0:0&emeaframe=&fileID=906&searchLang=en&searchLang=en)

---

### Post by Tillerman on 2005-12-23
[QUOTE=bscbrit]Removing and reinstalling the driver is not difficult, in fact, it is very simple but we will look at the results of 'dmesg' first.  

It is always tricky providing advice on a forum. Too little information and the problem doesn't get solved or one's advice doesn't do what was required, too much and some people feel that they are being spoken down to.  My fault, I erred on the side of too little....

Please don't worry about talking up or down to me.  I just appreciate the time and effort you are putting into a problem of someone whom you have never met.  I am rather thick skinned to begin with, and over the years Linux os has further humbled me.

To have time to read the output of dmesg, type the following

dmesg | less

The middle character is uppercase '\' down in the bottom left of the keyboard - well it is on mine!  This will allow you to page up, page down or quit 'q'.  First of all, I am looking at the setkeycode message. I know what it means but i do not know why it is occurring in your file.  Can you find where it first occurs and cut and paste that and a few lines preceding it in your next reply? [Tip: if you have a 3 button mouse, this can be most easily achieved by highlighting the text that you want to copy, switching to the place where you want to insert the copy, and pressing the middle mouse button. Whatever is highlighted will appear at the cursor position, ]  
To get to the relevant part of the output relating to the parallel ports, try the following:on isa0060/serio0).
[4429714.503000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429714.612000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429714.612000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429714.783000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429714.783000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429714.891000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429714.891000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429714.974000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429714.974000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429715.083000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429715.083000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429715.254000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429715.254000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429715.362000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429715.362000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429715.445000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429715.445000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429715.553000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429715.553000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429715.636000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429715.636000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429715.745000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429715.745000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429715.827000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429715.827000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429715.936000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429715.936000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.062000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429716.062000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.127000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429716.127000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.209000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429716.209000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.318000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429716.318000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.445000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429716.445000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.509000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429716.509000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.636000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429716.636000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.745000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429716.745000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.827000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429716.827000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429716.936000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429716.936000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429717.062000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429717.062000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429717.127000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429717.127000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429717.254000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429717.254000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429717.318000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429717.318000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429889.577000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429889.577000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429889.774000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429889.774000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429889.905000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429889.905000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429890.058000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429890.058000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429920.429000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429920.429000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429920.537000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429920.537000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429920.841000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429920.841000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429920.949000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429920.949000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429921.253000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4429921.253000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4429921.361000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4429921.361000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4430323.909000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4430323.909000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4430324.018000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4430324.018000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4430324.410000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4430324.410000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4430324.519000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4430324.519000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4430324.778000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4430324.778000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4430324.931000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4430324.931000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4430436.573000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4430436.573000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4430436.681000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4430436.681000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4467943.933000] cdrom: open failed.
[4468379.141000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468379.141000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468379.249000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468379.249000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468382.399000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468382.399000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468382.552000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468382.552000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468382.944000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468382.944000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468383.096000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468383.096000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468383.355000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468383.355000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468383.552000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468383.552000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468383.723000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468383.723000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468383.876000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468383.876000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468384.010000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468384.010000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468384.162000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468384.162000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468384.289000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468384.289000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468384.442000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468384.442000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468384.568000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468384.568000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468384.677000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468384.677000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468384.766000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468384.766000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468384.919000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468384.919000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468458.031000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468458.031000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468458.140000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468458.140000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468458.843000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468458.843000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468458.995000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468458.995000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468522.312000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468522.312000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468522.421000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468522.421000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468522.729000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468522.729000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468522.881000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468522.881000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468523.318000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468523.318000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468523.426000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468523.426000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468581.352000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468581.352000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468581.549000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468581.549000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468583.631000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468583.631000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468583.828000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468583.828000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468584.265000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468584.265000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468584.726000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468584.726000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468584.987000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468584.987000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468586.207000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468586.207000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468845.945000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468845.945000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468846.643000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468846.643000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468847.304000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468847.304000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468847.413000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468847.413000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468851.228000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468851.228000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468851.342000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468851.342000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468883.085000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468883.085000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468883.237000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468883.237000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468892.886000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4468892.886000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4468892.995000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4468892.995000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.


I hope this is what you wanted.  It seems like a lot of information to me.


dmesg | grep parport

This combination 'pipes' (or sends, if you like) the output of one command (dmesg) to the input of another command (grep).  You are asking grep to find all the lines containing the word 'parport', which is the reference to the parallel port, and to display just those lines on your screen.  Let me know the results of this command also please.[/QUOTE]


The command "dmesg | grep parport" yielded a blank screen.


Tillerman

---

### Post by Tillerman on 2005-12-23
[QUOTE=bscbrit]The next 'problem' that I have found is that, on my machine at least, there is no driver available for your specific printer.  Did you manage to find one on your computer or did you use the Lexmark 4039 10plus driver?  I'm still Googling for more information.[/QUOTE]


I used the Lexmark 4039 10plus driver.  This is the same driver that was available on Linux Red Hat and it seemed to work well.

---

### Post by Tillerman on 2005-12-23
[QUOTE=bscbrit]Links to the drivers:

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?category=Software&ccs=229:1:0:44:0:0&os_group=Redhat&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?category=Software&ccs=229:1:0:44:0:0&os_group=Redhat&searchLang=en)

which leads to:

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:44:0:0&emeaframe=&fileID=729&searchLang=en&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:44:0:0&emeaframe=&fileID=729&searchLang=en&searchLang=en)

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:44:0:0&emeaframe=&fileID=906&searchLang=en&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:44:0:0&emeaframe=&fileID=906&searchLang=en&searchLang=en)[/QUOTE]


Yes, I found that driver also and downloaded it to my desktop.  I got no farther than that. I'll gunzip and tar -x it now into a folder - but I'm sure I won't have a clue what to do with it next.

Tillerman

---

### Post by bscbrit on 2005-12-23
Tillerman - well I wasn't expecting quite that much data!  It suggests that something is seriously amiiss with the configuration but I must confess at being at a loss of knowing how to pin it down.  And the fact that dmesg doesn't seem to find a parallel port would explain why you are not having any joy getting the printer to burst into life.

Can you show me the output of the following command, please:

lsmod

I'm going to do some reading, but I think that the next thing we will try (subject to the results of the previous 'lsmod') will be a removal and reinstallation of the driver software.  But first, I think we have to confirm that your parallel port is found.

---

### Post by bscbrit on 2005-12-23
You are not alone.....

[http://www.ussg.iu.edu/hypermail/linux/kernel/0401.3/0676.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0401.3/0676.html)

[http://ubuntuforums.org/archive/index.php/t-76271.html](http://ubuntuforums.org/archive/index.php/t-76271.html) (this is well worth a read!)

---

### Post by Tillerman on 2005-12-23
[QUOTE=bscbrit]Tillerman - well I wasn't expecting quite that much data!  It suggests that something is seriously amiiss with the configuration but I must confess at being at a loss of knowing how to pin it down.  And the fact that dmesg doesn't seem to find a parallel port would explain why you are not having any joy getting the printer to burst into life.

Can you show me the output of the following command, please:

lsmod

I'm going to do some reading, but I think that the next thing we will try (subject to the results of the previous 'lsmod') will be a removal and reinstallation of the driver software.  But first, I think we have to confirm that your parallel port is found.[/QUOTE]

The result of the command is:

bash: Ismod: command not found

Sorry, that doesn,t seem to be very helpful.  What is Ismod?

Tillerman

---

### Post by nitricacid on 2005-12-23
[QUOTE=Tillerman]I'm starting to wonder that myself.  Actually, I had used the same distro for 4 years and was interested in upgrading and trying something new.  Ubuntu looked pretty impressive, and I actually enjoy it ........just got to get past these few gliches.

Tillerman[/QUOTE]

hah, In my opinion and travels through the linux world over the years I have come to realize that if it isn't broke and everything runs fine don't change it.

I know there hasn't been a new release for RH in years but I know you can still update everything about it. If I were you I would have just left well enough alone.
But, since you have switched to Ubu I wish you the best of luck and hope you enjoy it, SInce I can't say anything bad about Ubu myself and only ever ran into one glitch when installing Ubu I know you will come to like it just as much as you did RH.

---

### Post by bscbrit on 2005-12-23
I had just typed a major response and somehow lost it - damn!  OK, I'll retype it again.....

lsmod is a command to list the installed modules.  I was hoping to find some indication that the parallel port had been detected and that the appropriate driver module was installed.  We didn't get it.  The fact that lsmod isn't even found suggests that the original installation did not go as planned.

Could you please show me the results of the following commands:

echo $PATH
whereis lsmod

My search of the internet shows me others who have seen the same symptoms but none that gives me a solution.  Maybe an expert on the hardware forum can help

[http://www.ubuntuforums.org/forumdisplay.php?f=98](http://www.ubuntuforums.org/forumdisplay.php?f=98)

but I am at the limits of my knowledge.

How much of a problem would a full install be to you?  Would you be risking valuable data?  If the result of that installation is the same as this then it might be that there is an incompatability between your hardware and ubuntu.  I cannot think why that should be but there is certainly something wrong.

However, the installation might go perfectly or, at least, give some indication of what is going on.  But the majority of the effort will be yours with occasional encouragement from this end!

---

### Post by Tillerman on 2005-12-23
Could you please show me the results of the following commands:

echo $PATH
whereis lsmod

 echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
rm@ubunturm:~$ whereis Ismod
Ismod:

Hope this helps.


How much of a problem would a full install be to you?  Would you be risking valuable data?  If the result of that installation is the same as this then it might be that there is an incompatability between your hardware and ubuntu.  I cannot think why that should be but there is certainly something wrong.


I would be willing to do a complete reinstall of Ubuntu.  All of my data is tarred and on CD's.  The question is, should I do a reinstall with the CD I have, or should I suspect it to be bad and start a new download and burn an ISO image? 

I suspected that the install was somehow corrupted when several things went wankey.  Many things (like email, internet, add on programs) were installed flawlessly.

Tillerman.

---

### Post by Tillerman on 2005-12-23
Yes, I have had a hand in creating most of my "hard times" over the years.  I love Linux, and the concept of open computing.  I've never been schooled in computers or programing - I just aproach it like I would any other problem in life.

I suspect that when the dust settles I will be happy that I made the switch and streched out a little bit past my comfort zone.

Tillerman.

---

### Post by bscbrit on 2005-12-23
From what you say, it sounds as though the CD is corrupted, although I would have expected it to show errors during the installation.

Download a new copy, or do a checksum of the copy you have downloaded.  Presumably, the copy is on a Windows system?  Not sure how you do an MD5 checksum under windows but if you Google for it then I'm sure that something will come up.  When you burn the CD (as an iso image) pick a fairly slow speed and not the fastest that the computer says it will do.  Faster speeds tend to give more errors.  Waiting a few extra minutes for a slow burn shouldn't make much difference when you consider the time that you might lose fault finding again.

But, whatever, I'd be grateful if you let me know how you get on.  Sorry I haven't managed to solve your problem on this occasion.

---

### Post by Tillerman on 2005-12-23
Download a new copy, or do a checksum of the copy you have downloaded. Presumably, the copy is on a Windows system? Not sure how you do an MD5 checksum under windows.......


How do you do a checksum in Ubuntu..  that is the system I will be using to download a new ISO.


Tillerman.

---

### Post by bscbrit on 2005-12-23
This is how you verify MD5 check sums under Linux:

   1. In the shell of your preference, type the command "md5sum Archivename.tar.gz"
   2. Compare the calculated checksum with the one listed for the downloaded iso.
   3. If the checksums do not match then there is a difference between the two files

---

### Post by bscbrit on 2005-12-23
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

might also be useful.

---

### Post by nitricacid on 2005-12-23
[QUOTE=Tillerman]Yes, I have had a hand in creating most of my "hard times" over the years.  I love Linux, and the concept of open computing.  I've never been schooled in computers or programing - I just aproach it like I would any other problem in life.

I suspect that when the dust settles I will be happy that I made the switch and streched out a little bit past my comfort zone.

Tillerman.[/QUOTE]

DITTO all the way, dude. :)

---

