---
title: "Ubuntu Live Boot Problem"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by rjacobsen on 2005-06-21
I just downloaded the Live CD iso and burned a CD, when I boot my computer from the CD it will stop and just have a blinking hyphen after the following point in the boot process. The last entry that shows in command line is:

ata1: command 0xa0 timeout, stat 0xd0 host_stat 0x21

I thought it might be that I have a secondary SATA drive. I disabled the drive in BIOS and tried again, It still stops at that point. I have a Dell Demension 8400 that is 2 months old. It has a 3GHZ P4 630,  2 SATA HDs, 1GB 533 DDRAM, CD RW and DVD RW drives. I would appreciate any advice anyone has.

Thank You,
rjacobsen

---

### Post by rjacobsen on 2005-06-21
I just tried booting again and it went further through the boot process than before. I had plugged in the USB cable to the card reader after the first time I tried booting, ubuntu recognizes it in the boot process but will stop when it's searching scsi devices. I then disconnected the USB cables for both the card reader and my printer and the boot process would stop where it did initially. With the printer and media card reader attached it wil stop at this point in the commandline:

Attached scsi removable disk sdc at scsi1, channel 0, id 0, lun 2

---

### Post by rjacobsen on 2005-06-21
I forgot to say in my last post that I don't have any scsi devices with my computer. In my BIOS there is nothing affiliated with scsi. I only have SATA and IDE devices in my BIOS! 

I've been trying to contact tech support through the IRC (Chat) and get "The page cannot be displayed.". I joined ubuntu and logged in and I still continue to get that message page from IE. 


Thanks in advance for any suggestions,
rjacobsen

---

### Post by xmastree on 2005-06-21
[QUOTE=rjacobsen]Thanks in advance for any suggestions[/QUOTE]Are you sure your CD is ok? You didn't say if you checked it using md5.

[**Here**](http://www.irnis.net/gloss/md5sum-windows.shtml) is one alternative (which I haven't used, so I can't say how well it works), but there are plenty more out there. Just google for md5sum windows.

If it fails, it could be a bad burn or a damaged ISO, so run md5sum on the ISO.

---

### Post by rjacobsen on 2005-06-21
Thanks a million xmastree, I didn't even know about md5. I deleted the file from my secondary drive after I burned the CD. I just went to the link you gave me and also ran a search in google on it and got instuctions on using md5. I will try and decihper them and give it a shot. Maybe you can tell me how to run the program to check the CD. Drive D is my CD drive.
Thanks, rjacobsen

---

### Post by xmastree on 2005-06-21
[QUOTE=rjacobsen]Maybe you can tell me how to run the program to check the CD. Drive D is my CD drive.[/QUOTE]I use a command line version of md5sum for windows, I think it's [this one](http://www.etree.org/md5com.html)
If you look in the root directory of the CD you made you will see a file called md5sum.txt
This lists the md5sums for all the files on the disc.
To check it, put md5sum.exe somewhere on your path, and do this:
```
d:
md5sum -c md5sum.txt
```That should compare every file on the CD with its listing in md5sum.txt

---

### Post by rjacobsen on 2005-06-22
I tired the program you first suggested but it was a trial version and I didn't understand it so I uninstalled it and restored the computer. I just went to the etree.org site that you posted in your second reply and I'm checking out the program. It states the folowing on the site:

Windows 95/98/Me: Download md5sum.exe to c:\windows\command

Windows NT/2000: Download md5sum.exe to your c:\winnt\system32 

It dosen't say anything about XP, which I'm running! You have to excuse my ignorance of Linux, I have limited experience with it. I had studied it in college over 3 years ago for 1/2 of a semester. I like working with command line but I don't have a lot of experince with it. I ocassionaly use it with windows for different things. I downloaded the program to my secondary drive E, I don't know where the folder is suppose to be so I tried putting it in C:\Windows and running it in command line. I can't get it to work because I don't know how to enter the right commad line for it. Where am I suppose to put the the file? I don't quite unerstand what you meant by" To check it, put md5sum.exe somewhere on your path, and do this:
Code:
d:
md5sum -c md5sum.txt

I was able to view the md5.txt file on the CD, which is drive D, from command line with no problem. I've read the instructions at etree.org on the program also but I'm not sure how to use it properly.
Thanks, rjacobsen

---

### Post by xmastree on 2005-06-22
[QUOTE=rjacobsen]Windows 95/98/Me: Download md5sum.exe to c:\windows\command

Windows NT/2000: Download md5sum.exe to your c:\winnt\system32 

It dosen't say anything about XP, which I'm running!


Where am I suppose to put the the file?
I don't quite unerstand what you meant by" To check it, put md5sum.exe somewhere on your path, and do this:[/QUOTE]Basically, you can put the file anywhere but those suggested locations are on the 'path' which means that if you type that command from within any directory, it can be run. I would suggest for XP, you put the file in c:\Windows\System32
Then, with the CD in drive d, open up a Command prompt and type d: <enter>
that should switch you to the CD, try typing dir <enter> to see the files on the CD.
Once you see the name of the md5sum file (md5sum.txt I think) you can type:
```
md5sum -c md5sum.txt
```
and sit back and watch it run. Any errors will be listed at the end.

> I downloaded the program to my secondary drive EIn that case, run it like this:
```
e:\md5sum -c md5sum.txt
```


If you want to be able to see all the results, you need to send the output to a file so you would type this:
```
e:\md5sum -c md5sum.txt > c:\filename.txt
```

Then you can browse to that file and view it.

---

### Post by rjacobsen on 2005-06-22
Thank you very much for the reply! I ran md5sum from e: and compared it to the CD, 2 files were not right. I made a file called md5comp.txt in c:\, I copied and pasted the 2 results below.

./install/netboot/pxelinux.cfg/default: FAILED open or read
./install/netboot/pxelinux.0: FAILED

In the command prompt the results showed up like this at the end:

c:\md5sum: WARNING: 1 of 1109 listed files cold not be read

c:\md5sum: WARNING: 1 of 1108 computed checksums did NOT match

I naturally assume by this that the CD is no good. I will download the iso file again. This time I will check the iso file before I burn it. I have some audio files on the e: drive that I will move to my c: drive and then the e: drive will be blank. I assume then I would look in e: drive in command prompt and run the md5sum program to compare it. Let me know if you have any suggestions.
Thank You,
rjacobsen

---

### Post by rjacobsen on 2005-06-22
I dowloaded the iso file to my e: drive and looked at the directory for the drive in command prompt. This is what shows in the command prompt:

06/22/2005  09:59 AM       655,259,648 ubuntu-5.04-live-i386.iso
               1 File(s)    655,259,648 bytes
               0 Dir(s)  203,192,025,088 bytes free

I'm going to go ahead and burn a new CD and see how it turns out. If you know how to check an iso file please let me know. 
Thank You,
rjacobsen

---

### Post by rjacobsen on 2005-06-22
I just got done burning the new CD, ran the md5sum and it turned out the same as the first CD. 

./install/netboot/pxelinux.cfg/default: FAILED open or read
./install/netboot/pxelinux.0: FAILED

In the command prompt the results showed up like this at the end:

c:\md5sum: WARNING: 1 of 1109 listed files cold not be read

c:\md5sum: WARNING: 1 of 1108 computed checksums did NOT match

---

### Post by rjacobsen on 2005-06-23
exmastree,
I got my HP Pavillion laptop back from a buddy of mine and ran the Live CD on it and it works perfectly fine. Dell has there own bios and I surmise there might be some kind of conflict. I would like to be able to run it on my new Dell Demension 8400 because it's at least 3 times as powerful as my laptop. I can at least check out ubuntu on the laptop though and it's good enough for now. Let me know what you think.
Thank You,
rjacbosen

---

### Post by xmastree on 2005-07-03
[QUOTE=rjacobsen] ran the Live CD on it and it works perfectly fine.[/QUOTE]Hi, sounds like you're getting somewhere. Sorry I couldn't reply sooner, I'm on vacation just now so I'm not on the net much.
If you're still having problems, I'm sure there are others here who can help you.

---

