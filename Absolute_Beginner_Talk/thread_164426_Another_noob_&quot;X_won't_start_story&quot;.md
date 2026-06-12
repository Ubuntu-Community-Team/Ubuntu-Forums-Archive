---
title: "Another noob &quot;X won't start story&quot;"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Usually Lurking on 2006-04-22
Hello,

I've been lurking around here for about a month and finally registered so I could do forum searches.  Now that I finally got Ubuntu installed and starting without error codes I can not get x to start.  I've read through other threads and tried what I could, all to no avail.  When I try "startx" it tries to run but I'm getting the following error codes:

skipping /usr/x11r6/lib/modules/extensions/libGLcore.a:m_debug_clip.0";
skipping /usr/x11r6/lib/modules/extensions/libGLcore.a:m_debug_norm.0";
skipping /usr/x11r6/lib/modules/extensions/libGLcore.a:m_debug_xform.0";

(EE) No devices found
--------------------------------------------------------------------------
I've tried "sudo dpkg-reconfigure xserver-xorg" and when I get to the part where I choose the 24-bit color and then <enter> the following comes up:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.200604221639

So at that point I assume it's normal and type "sudo /etc/init.d/gdm restart"
At which point I get the above error code followed by:

fatal server error
no screens found
XIO: fatal IO error104 (connection reset by peer) on Xserver "0:0"

I saw and tried the "sudo cat/var/log/xorg.0.log | grep EE" that someone posted in another thread and it told me it was not a recognized command.

To keep from turning this into more of a novel, I've tried every tip I can find.  Could my system just not be compatible with Ubuntu (or any other linux application)?  System main features are as follows: AMD3500+, ASUS A8N-SLI Deluxe, 1G PC3200, 2x BFG 7600GT OC's, 76GB WD Raptor (Windows XP install), 160GB WD for Ubuntu install.  The dual booting part works fine.

I'd really like to move away from XP as much as possible but all this rebooting to search the forum and then rebooting into Ubuntu to test is driving me nuts.  

Oh, and I saw somewhere to check my /var/log/xorg.0.log file and I can get to the directory where that file is but how in the world am I supposed to open it?

Thanks to all who took the time to read all this,
UL

---

### Post by johnny2211 on 2006-04-22
No screens found is the problem. Please post your xorg.conf file it is in the /etc/X11 directory


Also the "sudo cat/var/log/xorg.0.log | grep EE" doesn't work because "cat" is a command and the rest is just options so they need a space in between:-)

"sudo cat /var/log/xorg.0.log | grep EE" will work.;)

---

### Post by Usually Lurking on 2006-04-22
[QUOTE=johnny2211]No screens found is the problem. Please post your xorg.conf file it is in the /etc/X11 directory[/QUOTE]

Can you tell me how I can get that file from my XP boot or how to copy it while Ubuntu is the OS and transfer to Windows?


[QUOTE=johnny2211]Also the "sudo cat/var/log/xorg.0.log | grep EE" doesn't work because "cat" is a command and the rest is just options so they need a space in between:-)

"sudo cat /var/log/xorg.0.log | grep EE" will work.;)[/QUOTE]

Ah, now that makes sense.

---

### Post by johnny2211 on 2006-04-22
To look at the linux partitions under windows you need a program for that. Try a search on ubuntuformus. For egsample: win mount ext3. I think there is a program named ext2fsd or something.


But what we need from the xorg.conf is to see if there are sections named Screen defined.

---

### Post by jpkotta on 2006-04-22
There are ext2fs drivers for WinXP.  I used one called ext2ifs, and it seemed to work pretty well.  Alternatively, use a USB drive.  If you're going to be dual booting quite a bit, you might want a FAT32 partition for swapping files between OSes.

---

### Post by Usually Lurking on 2006-04-22
[QUOTE=johnny2211]To look at the linux partitions under windows you need a program for that. Try a search on ubuntuformus. For egsample: win mount ext3. I think there is a program named ext2fsd or something.


But what we need from the xorg.conf is to see if there are sections named Screen defined.[/QUOTE]

Thanks.  I've found the program but must step away for a bit.  Once I return I will post the contents of the file.

---

### Post by Mustard on 2006-04-22
I can't work out what graphics card you've got from your first post.

---

### Post by Usually Lurking on 2006-04-22
[QUOTE=Mustard]I can't work out what graphics card you've got from your first post.[/QUOTE]

There are two (SLI) 7600GT's OC'd from the manufacturer which is BFG.


[quote=johnny2211]No screens found is the problem. Please post your xorg.conf file it is in the /etc/X11 directory[/quote]

attached is the file. (At least I think I got the file attached).

[edit] hey it worked, the file really did attach,cool!

---

### Post by Mustard on 2006-04-22
Have you tried using the generic 'vesa' drivers as a temporary workaround, so that you can at least get a gui?

---

### Post by Usually Lurking on 2006-04-22
[QUOTE=Mustard]Have you tried using the generic 'vesa' drivers as a temporary workaround, so that you can at least get a gui?[/QUOTE]

No I haven't.  Does that mean when I reconfigure the xserver I would select "vesa" instead of "nv"?

---

### Post by IYY on 2006-04-22
Yes. If you want, you can just make the change in the file itself, just replace "nv" with "vesa".

---

### Post by Usually Lurking on 2006-04-23
Well I must have goofed up something because this morning I couldn't even boot into ubuntu.  So, new install, same X won't start problem, reconfigure xserver to vesa driver and \\:D/, up pops the login screen!  The desktop screen is off just like in XP before I install the latest nVidia drivers but hey, ubuntu is now up and running.  In fact I had to make myself stop exploring to let you all know that using the Vesa driver solved my problem.

Thanks to all for your help it is greatly appreciated.  The fact that my thread was on page after only 12 hours just shows how wonderful the level of community support is here.  Again, thanks to all that posted help.

UL

---

### Post by Mustard on 2006-04-23
Good news. :)

Well done.

---

