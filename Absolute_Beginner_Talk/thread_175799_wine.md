---
title: "wine"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-05-13
I have Wine installed, but can't figure out what I'm supposed to now.  The wiki doesn't make it clear to me how I'm supposed to get a Windows program (Zen Nano Plus) off the installation CD on to the hard drive.  Also, the wiki says that (once it is installed) I simply use the command line to say 'wine Zen Nano Plus.exe' to run the new program through wine.  The only .exe on the installation CD is the setup.exe.  I',m really confused at this point.  A little help, please?

---

### Post by nanotube on 2006-05-13
[QUOTE=Guns90]I have Wine installed, but can't figure out what I'm supposed to now.  The wiki doesn't make it clear to me how I'm supposed to get a Windows program (Zen Nano Plus) off the installation CD on to the hard drive.  Also, the wiki says that (once it is installed) I simply use the command line to say 'wine Zen Nano Plus.exe' to run the new program through wine.  The only .exe on the installation CD is the setup.exe.  I',m really confused at this point.  A little help, please?[/QUOTE]
well, trying "wine setup.exe" seems like a good thing to try. :) that should install the zen nano software under wine into its "fake" c drive. then you can run the actual zen exe with wine.

---

### Post by Guns90 on 2006-05-13
gary@ubuntu:~$ wine setup.exe
wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found
gary@ubuntu:~$

---

### Post by Omnios on 2006-05-13
Did you config wine. After installing it you have to config it with 
```
winecfg
```

[[COLOR="Blue"]Configing wine[/COLOR]]("http://www.winehq.com/site/docs/wineusr-guide/config-wine-main#USING-WINECFG")

 I have a zen micro and I am using gnomad2 to run it in linux. As for the wine install you might have a problem mounting the usb in it but not shure.

---

### Post by Guns90 on 2006-05-13
Omnios, yes I did run winecfg.  I just went back in and setup.exe is on the applications page.  

I guess I'm just not understanding Linux at all at this point.  Everything I've been able to find in wiki, howto's, and the beginner talk, I understood That MP3's will not/cannot run in Linux packages.  Therefore, I assumed (yeah, I know) that I had to do it through Windows; hence my trying wine.

---

### Post by uteck on 2006-05-13
You can use wine to run the setup.exe.  From the command line, do 'wine /path/to/exe'  Or you can use the file browser and right-click on the setup file and choose to run it with wine.

---

### Post by YokoZar on 2006-05-13
[QUOTE=Guns90]I have Wine installed, but can't figure out what I'm supposed to now.  The wiki doesn't make it clear to me how I'm supposed to get a Windows program (Zen Nano Plus) off the installation CD on to the hard drive.  Also, the wiki says that (once it is installed) I simply use the command line to say 'wine Zen Nano Plus.exe' to run the new program through wine.  The only .exe on the installation CD is the setup.exe.  I',m really confused at this point.  A little help, please?[/QUOTE]
Try opening the setup.exe on the CD drive with Wine.

Right click the executable, and select "open with Wine".  This should be familiar to a Windows user, as to run an application you must find it and open it :)

Alternatively, from the terminal, you can navigate *to the directory where the program you want to run is*, then run "wine (program name).exe".  If you try and do that from a different directory, the system won't know where to look for the program, so by default Wine will try it's own system folder.  Your application is on the CD, so Wine didn't find it there.

---

### Post by YokoZar on 2006-05-13
[QUOTE=Guns90]Omnios, yes I did run winecfg.  I just went back in and setup.exe is on the applications page.  

I guess I'm just not understanding Linux at all at this point.  Everything I've been able to find in wiki, howto's, and the beginner talk, I understood That MP3's will not/cannot run in Linux packages.  Therefore, I assumed (yeah, I know) that I had to do it through Windows; hence my trying wine.[/QUOTE]
By the way, MP3 playback works perfectly and easily if you install it.

I highly recommend you try the Automatix script:
[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)

---

### Post by Guns90 on 2006-05-13
Okay, I had some success getting into it; however, while it was trying to install on my current window, the terminal window kept showing multiple error messages.  The current window said the installation was successful, but the terminal was still posting multiple err messages.  It seemed to be locked, so I rebooted.  There is no Zen Nano Plus .exe anywhere.  Maybe I'll give the gnomad2 package a try till I maybe someday get better in Linux.  Thanks for help guys.  I'll let you know if I have any luck with gnomad2.

---

### Post by Scunizi on 2006-05-14
I know what you're going through.  I installed Wine and it took me almost a week to find out what I needed to do.  Run wincfg from the consol and make sure all your drive are designated properly.  Change the basic emulation type to Win 98 or ME or 2000.  Back out and run winefile from the consol.  From there you'll be able to look at a cd and double click on a setup.exe file and install the app.  some will run... some will not... good luck!

---

### Post by nanotube on 2006-05-14
[QUOTE=Guns90]gary@ubuntu:~$ wine setup.exe
wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found
gary@ubuntu:~$[/QUOTE]
that should be
```
wine /full/path/to/setup.exe
```
then it will find it.

---

### Post by YokoZar on 2006-05-14
> **Guns90]Okay, I had some success getting into it said:**
> 
Most of Wine's terminal output are actually benign warning messages indicating that the program has called a function that isn't fully complete in Wine - many will still run anyway, particularly installers.

>  It seemed to be locked, so I rebooted.
Welcome to Linux!  Please leave your Windows habit of rebooting at the door.

You can simulate a windows reboot with Wine by running "wineboot" in the console, however this is generally unneeded.

Anyway, you can generally kill an application running in a terminal window by pressing ctrl-c.  Alternatively, for Wine, you can open up a new terminal and type *killall -9 wine-preloader*.  This command will completely destroy the helpless wine application processes, allowing you to do whatever you want.

[quote]There is no Zen Nano Plus .exe anywhere.  Maybe I'll give the gnomad2 package a try till I maybe someday get better in Linux.  Thanks for help guys.  I'll let you know if I have any luck with gnomad2.It's likely hidden away somewhere in Wine's virtual Windows drive: ~/.wine/drive_c/ is where your virtual C drive is.



By the way, I know a lot of the above sounds really unituitive, and it is.  This is why I'm working on integrating all of this stuff into a neat little Wine package for the next version of Ubuntu after Dapper (Edgy), where we'll have nice obvious buttons for stuff like Simulate Windows Reboot and Explore Virtual Windows Drive.

---

### Post by Scunizi on 2006-05-15
I probably should have cought on to this in the beginning ... but... there are other programs that will allow your Zen Nano to work with Linux instead of using their software...

---

