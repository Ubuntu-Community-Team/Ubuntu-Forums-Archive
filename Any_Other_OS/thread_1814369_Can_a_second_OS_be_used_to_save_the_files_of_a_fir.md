---
title: "Can a second OS be used to save the files of a first OS?"
date: 2011-07-29
forum: Any Other OS
---

### Post by jiri2 on 2011-07-29
Right now, I'm trying to figure out how to add network connection to my Ubuntu I'm going to install next to my Windows, and just want to know if I'm not wasting my time.

Also, if I can do this with Ubuntu, surely I could do this with any OS, including installing a second Windows to save my first Windows?

Is there anything wrong with this thought process?

---

### Post by ajgreeny on 2011-07-29
> **jiri2 said:**
> Right now, I'm trying to figure out how to add network connection to my Ubuntu I'm going to install next to my Windows, and just want to know if I'm not wasting my time.

Also, if I can do this with Ubuntu, surely I could do this with any OS, including installing a second Windows to save my first Windows?

Is there anything wrong with this thought process?
Nothing wrong with it at all!

It is one of the first things that live OSs like Knoppix were used for, and IO sduspect that few users ever installed it to disk, they just used it as a live system to rescue another OS.

Just like SystemRescue and probably seevral others, but it can also be done using Ubuntu, though you may need to add packages specifically to run rescue missions.  It will depend on exactly what it is you need to rescue.

---

### Post by mikewhatever on 2011-07-29
From what I understand, you want to save the Windows files by installing another instance of Windows. That doesn't make much sense, cause what's so important in the system files if you are reinstalling. I'd also like to know what you want to save them from. What's the problem exactly?

---

### Post by jiri2 on 2011-07-29
> **mikewhatever said:**
> From what I understand, you want to save the Windows files by installing another instance of Windows. That doesn't make much sense, cause what's so important in the system files if you are reinstalling. I'd also like to know what you want to save them from. What's the problem exactly?


Well, I'm getting 'can not open recover.dat file' error.

I know what you're thinking ](*,)

I clicked on a hazar loader of those for win7 and switched the windows registration key, or something along those lines.

I wasnt aiming to do it for my host which is actually OEM, just for a guest in my virtual box, only i forgot to put it in there!!! I couldnt believe it lol!

Right now, I dont know what the situation is exactly. The first thing I read was someone who used Ubuntu to access c:/ and erase a w7ldr file and it was working great for him because he didn't even have to restore. I erased a 7ldr file and, just in case, all the loaders i had sitting around, but no luck.

So I read around further and they talked about using the DVD recovery that came with windows. Mine didnt come with a recovery dvd, but seems to have an option available at boot, if i press F8 that allows me to restore to factory installation. I'm all the more uncertain because I cant even boot in safe mode, so I want to make sure I don't lose my files by installing another OS, in another partition, and dragging all the files in the partition of the OS at risk into the new OS, or better still, network it on my home grid to transfer them to another PC.

Some people say to erase the partition with the factory OS, but i'd like to avoid that because a torrented win7, which I'd need if the erasing didnt work, would probably have difficulties recognising the pc's BIOS.

This is because rar files aren't saved in a factory backdate. Also, just in case.

What do you guys recommend?

Right now I'm strugging to get Ubuntu to recognise the internet, as you can see in []("http://ubuntuforums.org/showthread.php?t=1814047")[another thread]("http://ubuntuforums.org/showthread.php?t=1814047") and [another]("http://ubuntuforums.org/showthread.php?t=1814273")_._ I actually haven't figured it out, there's something in the passwords I must be getting wrong.

However, if another OS the ones mentioned by ajgreeny can remain untouched in their own partition by a OS factory install backdate, then I might do it that way. If the OS can take the files from the old Win7 and make them wait for a move back to the new Win7, that'll be good.

My worry about this is the windows 7 factory backdate may not recognise this OS's partition and wipe it out too!

---

### Post by jiri2 on 2011-07-29
> **ajgreeny said:**
> Nothing wrong with it at all!

It is one of the first things that live OSs like Knoppix were used for, and IO sduspect that few users ever installed it to disk, they just used it as a live system to rescue another OS.

Just like SystemRescue and probably seevral others, but it can also be done using Ubuntu, though you may need to add packages specifically to run rescue missions.  It will depend on exactly what it is you need to rescue.


Which OS is the best for this? Or will any do?

How do I transfer the files from the old OS's partition to the partition of my new OS?

I'll try with ubuntu just to see, but my experience is only with virtual machines, and there I believe new partitions are created, but I can't just drag and drop 

I'll install ubuntu now and see. As I understand it from [this thread]("http://ubuntuforums.org/showthread.php?t=1814047"), i'll see how it goes.

---

### Post by drawkcab on 2011-07-29
I do this for my friends all the time.

---

### Post by oldfred on 2011-07-29
I would make sure I have backed up my data to another device. The factory restore is just an image of the hard drive as of the day they shipped it, it erases everything and makes it just like brand new.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by mikewhatever on 2011-07-29
> **jiri2 said:**
> Well, I'm getting 'can not open recover.dat file' error.

I know what you're thinking ](*,)

I clicked on a hazar loader of those for win7 and switched the windows registration key, or something along those lines.

I wasnt aiming to do it for my host which is actually OEM, just for a guest in my virtual box, only i forgot to put it in there!!! I couldnt believe it lol!

So, you broke a W7 installation and want to fix it, right? And the idea is to use a second OS, right?
If that's the case, Ubuntu is not the tool. I don't think it can fix Windows registration keys, and you should really ask for help on a W7 forum. 
I didn't understand most of the rest, so if someone can translate that into intelligible English, I'd appreciate.

---

