---
title: "bootable CD"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by nkingcade on 2005-09-26
I have a small question or problem. I have downloaded the cd(iso) image from the mothership. However, the image is not bootable. I am certain I have the image and not a file. I have an message digest file included in the image. How do I check the MD. What do I need to do to make my boot problems go away? I read an earlier thread and it trailed to nowhere. Help, please. Thanks.:confused:

Neal

---

### Post by KingBahamut on 2005-09-26
Did you burn the ISO as an image or did you just cut the ISO on as a data file?

---

### Post by cayamara on 2005-09-26
You should compare the md5sum given from the download location with the iso you have downloaded. Under linux, you most likely have the program. Just type "md5sum something" into a console. Under Windows, there are a couple of md5sum tools too for which you can google. That way you can check whether you downloaded the cd correctly

---

### Post by buraq on 2005-09-26
I think it is about how you burn it.Did you try burning image to disk with nero?

---

### Post by nkingcade on 2005-09-27
All,

I have a mountable .iso. I downloaded it from the UBuntu site. Does this constitute an image? If so, what do I do with what I downloaded. It is not bootable???:confused: I am assuming that the download is an image. Is that a bad assumption?? If there is time, please explain the two or more forms of an .iso. thanks.

Neal

---

### Post by Kapre on 2005-09-27
[QUOTE=nkingcade]All,

I have a mountable .iso. I downloaded it from the UBuntu site. Does this constitute an image? If so, what do I do with what I downloaded. It is not bootable???:confused: I am assuming that the download is an image. Is that a bad assumption?? If there is time, please explain the two or more forms of an .iso. thanks.

Neal[/QUOTE]

Nkingcade - if you're on Windows, check if you have a burning software (eg NERO) and then select the option in the program that says something like "burn ISO or image file". Select this and click on the .ISO file that you've downloaded. After the burn, make sure that your PC BIOS is set to boot from CDROM, after that follow the instructions.

K

---

### Post by byen on 2005-09-27
you know...ive suggested this to many be4 and this seems to have worked..if you have downloaded the ISO on Windows.go to [www.downloads.com](www.downloads.com) and get the program called "Deep Burner". Its a good iso burning program(free) made with ISO burning in mind!! so try it out...let us know if this works....Goodluck!

---

### Post by nkingcade on 2005-09-27
Friends,

I have burned the downloaded image from Ubuntu to a cd-rom using Nero. I used the Burn ISO option. I now have a mountable, yet unbootable, .iso image. I placed the image CD in a PC that has nothing on it. No partitions, no formatting. I then configured the BIOS config to look at the CD rom first. The part I'm having a problem with does not appear to be the image, but how to make my system recognize that a disk has the files to be installed. So, I think my question should be "how do I make my image file or the media upon which it resides bootable?" Does this make sense? Come Back, thanks.

Neal

---

### Post by Wolki on 2005-09-27
[QUOTE=nkingcade]So, I think my question should be "how do I make my image file or the media upon which it resides bootable?" Does this make sense? Come Back, thanks.[/QUOTE]

The ISO should be bootlable automatically. Try comparing the MD5 of the iso with the one listed by Ubuntu, and if they match burn the install disk again at a lower speed.

---

### Post by Nihilist on 2005-09-27
ive heard that a program that emulates cd drives would allow you to use iso files directly from a windows desktop by fooling the system into beleiving that it had another cd drive and the iso was a correctly burnt cd. sorry if that sounds sloppy i just wanted to phrase it in a way most would understand.

---

### Post by nkingcade on 2005-09-27
BTW, another question. What are the hash values used for in the image? I know from my experience that normally a hash is used for ensuring the integrity of information. Is this the case here? Is this for the signing of the modules?

Neal

---

### Post by Scuddie on 2005-09-27
This is how logical mapping works in Windows.  You start out with a program like Daemon Tools or Nero ImageDrive.  When that program is configured, it registers a false SCSI drive to Device Manager.  While an ISO, BIN, NRG, etc is mounted, the program reads the data from the image, and sends the information to the logical SCSI device.  Windows doesn't see anything except the 'device', so the process is quite transparent.

Anyhow, lets talk about the way you burned it using Nero.  First of all, put the CD you burned into your drive, and look at the contents of it.  If you only see one large file (the ISO), then you didn't burn the image contained in the ISO, you burned the ISO itself.  ISO is nothing more than a container format, like zip.  It would be like putting a box inside of a box.

However, if you see about 8 directories and a couple small files, you burned the image, but it was probably done incorrectly.  Essentially, the disc should be burned a certain way to ensure the most compatibility.  First, make sure the recording method is Disc at Once (Disc at Once/96 is best if your burner supports it).  Track at once has some issues of its own, but I wont go into that.  Also, make sure to select the finalize disc checkbox.  If you did it on a CD-RW, that could be your problem all by itself, many drives dont support boot from CD-RW.

See if you went by those instructions, then post back.

---

### Post by moominboy on 2005-09-27
really sorry to just jump in another thread but ive got a problem on the same line.
i managed , eventually, to make a bootable version. which installs happily until half way thru when it says it cant load certain files(pool/main/l/linux-source/acpi modules xxxx-xxx-x-x-xxx udeb failed md5 checksum)

i tried various mirrors in case the file was damaged, tried different speeds too, down to x4. and im running out of discs!

any help would be much appreciated, thanks.

---

### Post by SilentCacophony on 2005-09-27
Hello. I just thought I'd post a link to a simple cd burner meant only to burn cd images as disc at once. It's a freeware utility for Windows called BurnCDCC at 

[http://www.terabyteunlimited.com/utilities.html]("http://www.terabyteunlimited.com/utilities.html").

It's quite simple, and requires no installation. Just run it from where you unpack it. I used that to burn several .iso's of linux distros at 8x, with no problems in booting them.

Anyhow, Scuddie posted the easy way to see if you burned them using the correct method.

---

### Post by moominboy on 2005-09-28
ok fellas,downloaded it again, and ran it thru fastsum,a checksum program?

and this is what was shown when it finished 77A1A8BE45E0CC93A14C9B9BF00F6648 *ubuntu-5.04-live-i386.iso

but if i follow it right it should be
487c576eeb732f31ec2624a46017c8af  ubuntu-5.10-preview-live-i386.iso

just noticed that the version number is different and the original doesn't say preview but it 's the same site which i got the download that i found the md5 data?

anyone know whats going on?

---

### Post by nkingcade on 2005-09-29
All,

I still have no solution to this bootable CD problem. To date, I have an image, I have a hash match, and all the files and folders I'm supposed to have. Does anyone have an idea which folder contains the executable for the install?

---

### Post by moominboy on 2005-10-01
it should come up automatically mate. when you insert the disc thru windows it allows you to have a look at some software, ie, the gimp,audacity,thunderbird and firefox. 

but if you re-boot with the disc in and have changed your bios settings it'll boot to the ubuntu install procedure.

---

### Post by xmastree on 2005-10-01
[QUOTE=nkingcade]I still have no solution to this bootable CD problem.[/QUOTE]What do you see on the CD if you look at it on the computer on which you burned it?
Look at [**this**]("http://www.xmastree.34sp.com/ubuntu/burn") to see how it ought to be done.

---

### Post by nkingcade on 2005-10-01
Salamat Internet Cafe,

I have booted the image. Do you have any links to information that would help in my understanding exactly what I  did when I burned the image from the  ISO?

Neal

---

