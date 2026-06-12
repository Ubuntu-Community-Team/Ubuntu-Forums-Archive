---
title: "Newbie questions"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by keno.mentor on 2007-11-17
Hi there,

I have looked online and in this forum for answers to these questions but haven't found exactly what I'm looking for.  I hope someone here may help me with these rather rudimentary questions...

I have downloaded kubuntu 7.10 for my fujitsu-siemens amilo L laptop.  I've run it from the cd thus far.  My questions are:

1) When run from the CD the graphics is not great.  It seems a bit pixelated.  Does the GUI look 'cleaner' when it is installed?  Do I need to install specific graphics drivers after installing kubuntu?

2) I cannot see the files on my harddrive i.e. the files I worked with in windows.  Will I be able to use my MSOffice files in OpenOffice?  Will files created in the windows environment e.g. mp3, jpegs etc work in the kubuntu environment?

3) Does kubuntu support wireless networking or do I need to install drivers for this to work?  I connect to the internet via a wireless connection to an ADSL modem.  Will this automatically work or will it require some special configuration?

Many thanks!
keno

---

### Post by derby007 on 2007-11-17
1) you probable need to tweak your /etc/X11/xorg.cof file, see help in forums with regards to your graphics card/graphics onboard chip.
2)You can read/write to NTFS or FAT32 partitions, depending on what your Windows is partitioned to.
3)It should do, again depending on how new your hardware is.

See: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy")
if you are using Gutsy, ubuntu 7.10.

---

### Post by PmDematagoda on 2007-11-17
I do not know about the 3rd question so I cannot answer it, but for the others:-

1) The graphics do get better after you install Ubuntu/Kubuntu, and do not worry about the drivers, if the VGA card is either a Nvidia or ATi, the Restricted Drivers Manager does the installing for you, but if you have an Intel or other VGA card, then most probably the general or vesa driver will be used.

2) MSOffice files such as .doc, xls, etc do usually work on Open Office, but the very new formats such as .docx, .xslx, etc do not. Though if you do not like Open Office very much then you can use MS Office through a Windows emulator such as Wine or Cross-over Office. Mp3's and other files from Windows will work will work on Linux with no problems. The reason you may not be seeing the Windows drive right now maybe because the Live CD cannot read NTFS partitions, but this will be fixed after installation where the ntfs-3g package allowing Kubuntu/Ubuntu to read NTFS volumes will be automatically installed.

I hope this helps.:)

---

### Post by erfahren on 2007-11-17
this may help a little, see if your notebook is listed here: [https://wiki.ubuntu.com/LaptopTestingTeam/Fujitsu](https://wiki.ubuntu.com/LaptopTestingTeam/Fujitsu)

you might want to search the forums (and google maybe) for your specific hardware along with "gutsy" to see what others have to say about it. Namely your video and wifi cards.

In risk of stating the obvious here, not all hardware works the same, what works for one doesn't always work for another. 

You should be able to get wifi to work, but it may take some configuration. There are usually workarounds no matter what, I haven't heard of any card that absolutely wouldn't work.

You could try getting your wifi running when using the Live CD. I was able to. (It also helps a little to have it up and running while installing - saves a little time later.)  Whether or not you use encryption may be a factor as well. It is sometimes easier to have your SSID set to Broadcast while you set it up.

---

