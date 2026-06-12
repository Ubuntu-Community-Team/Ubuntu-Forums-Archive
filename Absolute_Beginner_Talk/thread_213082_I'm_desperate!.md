---
title: "I'm desperate!"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Endow on 2006-07-10
Guys I relaly need help.My sister is having some trouble with her laptop...winddows is corrupted...I can't even boot...

She has very important files in there and I need to get those into a flash drive I have.

I'm not beeing able to solve it using the XP cd so I thought since I have a Ubuntu 5.10 Live CD I could perhaps boot Ubuntu and somehow access the windows partition in order to recover her files.

Is that possible in anyway??
Please help me as soon as/if you can since those files are realy VIP.


](*,)

---

### Post by nalmeth on 2006-07-10
Yes this should be doable

Do you have your own PC were you can perhaps download and burn a knoppix CD?

Knoppix might be a better choice for this type of thing, because it will automatically mount the windows partition on the desktop, whereas ubuntu will not.

If you can't do this, then we can use the Ubuntu CD, it will just require a couple of steps and terminal work. Don't worry, it won't be intensive.

So can you download a knoppix CD?

---

### Post by IYY on 2006-07-10
Of course. Just use the LiveCD, and mount the filesystem.

---

### Post by John.Michael.Kane on 2006-07-10
Anyone of these should allow you to recover said files.

[**[COLOR="Red"]SystemRescueCd[/COLOR]**]("http://www.sysresccd.org/Main_Page")
[**[COLOR="Blue"]Inside Security Rescue Toolkit[/COLOR]**]("http://www.inside-security.de/insert_en.html")

---

### Post by lazyd2 on 2006-07-10
Yeap, Knoppix is a lifesaver...

---

### Post by Endow on 2006-07-10
I could download Knoppix I thiink  butid rather not...Is it that difficult to use Ubunut live cd?


What excatly do I need to do?

---

### Post by John.Michael.Kane on 2006-07-10
Endow if your unwilling to download the tools to save you. then you must not be desperate! as you say.

---

### Post by RRS on 2006-07-10
If the windows partition is still sound you shouldn't have a problem mounting it from the live cd. 

If that works for you then you can copy her files to another drive, either another computer over a network or a USB device.

You might also download and burn a [Knoppix]("http://www.knopper.net/knoppix/index-en.html") live cd as it has a few more "rescue" tools then 5.10.

Also, if her drive has room you could install Ubuntu as dual boot with a Fat32 partition and copy her files there. That's how I ended up with Ubuntu on my primary machine, still haven't got around to fixing windows, don't really miss it.

Hope one of these suggestions helps, good luck :)

---

### Post by Endow on 2006-07-10
I never know what to download when all those folders appear (im tlaking about a mirror site for Knoppix)!

Why isn't there a .sio file?How should I download Knoppix?



I understand I'm sounding a bit ridiculous what with the naive questions and all but I actually had this folder problem before when trying to dowload other distros...

---

### Post by nalmeth on 2006-07-10
I'll make it easy for you, here is a download link for 5.0.1
[ftp://ftp.kernel.org/pub/dist/knoppix/KNOPPIX_V5.0.1CD-2006-06-01-EN.iso](ftp://ftp.kernel.org/pub/dist/knoppix/KNOPPIX_V5.0.1CD-2006-06-01-EN.iso)

---

### Post by John.Michael.Kane on 2006-07-10
Endow download the KNOPPIX iso file to the desktop, and burn it to a cd-rw. thats all. theres no need to save the iso to a folder.

---

### Post by Endow on 2006-07-10
No you dind't get it....I couldn't(before nalmeth helped me anyways:) ) see any .iso file....


The http thingy teleports me to one of thoe index thingies ( :p) with lots of folders ...all apparently part of knoppix...


Nevermind...its cool now...

While I download Knoppix can anyone tell me what is it about moutning the harddrive with the Ubuntu Live Cd??




PS:Sorry about my english...when I'm itchy I tend to speak in what I call deformed endow english :p (my native tongue is portuguese anyways)

---

### Post by jpmorelli on 2006-07-10
Hi Endow, I'm sorry about my english, I'm from Argentina, hope you understand my explication.
You can boot with Ubuntu 5.10 live CD but you have to mount the disk partition containing windows, the command:

mount -t vfat /dev/hdaX /mount_point

where X is the number of the partition of the first disk and "mount_point" is the directory you want that the partition is going to be mounted.

Good Luck !

---

### Post by GaijinOnline on 2006-07-10
Hi Endow, I was in the *same* situation as your sister many times and I must say that the knoppix live cd have saved my life many times!! Just boot in knoppix (it will be the KDE interface) the windows partition will be auto-mounted to the desktop and use K3B to burn you important files. After that maybe you could check if her MBR (master boot record) isn't corrupted with the windows cd.

Good Luck

---

### Post by Endow on 2006-07-10
Thanks everyone.It appears I have solved my problem via the Windows way :p

Anyways thanks again

---

