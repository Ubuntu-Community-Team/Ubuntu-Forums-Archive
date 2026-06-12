---
title: "After installing WINE, where do you find it to run it?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-07
I installed WINE some time ago, and just confirmed that by seeing in ADD/REMOVE that Wine is listed as an application I already have. But it is not listed anywhere in the applications drop-down menu. So where do I find it to start it up???

And if you can give me a good weblink that explains how to use it, that would also be very helpful. Thanks!

---

### Post by swarup on 2007-06-07
Also: I am using Ubuntu 7.04

---

### Post by mlentink on 2007-06-07
OPen up a terminal and type
```
wine programtorun.exe

```
where 'programtorun.exe' is your windows program. Usually this will need installtion, which you can do by running it's installer in wine like
```
wine d:\setup.exe
```
(d: is the drive with the installation disk
In windows, as you know, it could also be 'install.exe' or whatever, find out what is the right thing to install the specific program

---

### Post by swarup on 2007-06-07
> **mlentink said:**
> OPen up a terminal and type
```
wine programtorun.exe

```
where 'programtorun.exe' is your windows program. Usually this will need installtion, which you can do by running it's installer in wine like
```
wine d:\setup.exe
```
(d: is the drive with the installation disk
In windows, as you know, it could also be 'install.exe' or whatever, find out what is the right thing to install the specific program

I see. So Wine only runs from within the terminal?

I have a dual boot with Win 98 and Ubuntu 7.04. So now I'm booted up in Ubuntu, and I want Wine to run the program "Bahara" which is sitting in the Windows 98 partition on my hard drive. 

Is that possible to do? If so, how does Ubuntu refer to the Win 98 partition? Does it have a particular drive letter?

Thanks.

---

### Post by Songwind on 2007-06-07
> **swarup said:**
> I see. So Wine only runs from within the terminal?

I have a dual boot with Win 98 and Ubuntu 7.04. So now I'm booted up in Ubuntu, and I want Wine to run the program "Bahara" which is sitting in the Windows 98 partition on my hard drive. 

Is that possible to do? If so, how does Ubuntu refer to the Win 98 partition? Does it have a particular drive letter?

Thanks.

You can start wine using an icon or menu item, there's just no "wine interface" that you run.  Your command looks like what the previous poster says.  But you can create say a desktop icon that launches a windows command.

Your Win98 partition is probably already mounted somewhere, but without knowing your configuration it'd be hard to guess.

I suggest using the terminal command:
```

df -h

```

That will show you free and used space for all the partitions you've got mounted.  Look for one that's the right size and see where it is mounted (in the right-hand column).  If you have an IDE hard drive and Windows, the device is usually /dev/hda1.  If it's sata or SCSI it will be /dev/sda1.

If you have trouble figuring out which drive it is, paste the output from "df" here and we can help.

Anyway, let's assume Ubuntu stuck it in "/media/sda1" (which is where it stuck my Windows partition by default).  Your command (either in the app launcher setup or at the command line) would be:

```

wine /media/sda1/bahara_director/bahara_program.exe

```

Make sense?

---

### Post by swarup on 2007-06-07
As you'll see below, I tried executing the terminal command but it says it "cannot find" the program. Note that I misspelled the program name earlier -- its baraha. And the executable file of the windows program is Baraha.exe

Please see below, and let me know how I should proceed. Thanks!

swarup@swarup-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             5.3G  3.1G  2.0G  62% /
varrun                141M  108K  141M   1% /var/run
varlock               141M  4.0K  141M   1% /var/lock
procbususb            141M   88K  141M   1% /proc/bus/usb
udev                  141M   88K  141M   1% /dev
devshm                141M     0  141M   0% /dev/shm
lrm                   141M   33M  108M  24% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1             3.8G  2.6G  1.2G  70% /media/disk

swarup@swarup-laptop:~$ wine /dev/hda1/baraha_director/baraha_program.exe
wine: cannot find '/dev/hda1/baraha_director/baraha_program.exe'

---

### Post by swarup on 2007-06-07
I thought I might have found the error, but see below-- it still doesn't work.

swarup@swarup-laptop:~$ wine /media/disk/dev/hda1/baraha_director/baraha_program.exe
wine: cannot find '/media/disk/dev/hda1/baraha_director/baraha_program.exe'

---

### Post by pappapump on 2007-06-07
The name of the program you want to run is program.exe?
Are you sure thats the name of the file that starts your program?

---

### Post by Songwind on 2007-06-07
Okay, here's the relevant line.

> /dev/hda1 3.8G 2.6G 1.2G 70% /media/disk

The device name is /dev/hda1, and the device is mounted at /media/disk.

So to access a file that was on your windows partition as C:\foo\bar.exe you would do this in wine:

```

wine /media/disk/foo/bar.exe

```

What's the full path in Windows to the software you want to run?

Also, you might be able to just double-click the file in Nautilus (the file manager).  I know that in Kubuntu w/ CrossOver (a WINE variant) you can do that.

---

### Post by mlentink on 2007-06-07
> **swarup said:**
> I thought I might have found the error, but see below-- it still doesn't work.

swarup@swarup-laptop:~$ wine /media/disk/dev/hda1/baraha_director/baraha_program.exe
wine: cannot find '/media/disk/dev/hda1/baraha_director/baraha_program.exe'

Try: 
```
wine /media/disk/baraha_director/baraha_program.exe
```

Because it looks like /dev/hda1 is mounted on your system as /media/disk (that's where windows is mounted on my laptop as well)

Edit: Come to think of it did you actually install this in Wine? It sounds like you're attempting to run a program previously installed in windows. This will not work, because Wine does not read your windows registry, but keeps its own.
Could you clarify this for me?

---

### Post by mlentink on 2007-06-07
> **Songwind said:**
> Also, you might be able to just double-click the file in Nautilus (the file manager).  I know that in Kubuntu w/ CrossOver (a WINE variant) you can do that.

Or right-click the file and select "run with wine". But that only works with self-contained programs that do not need to be installed.

---

### Post by phr0ze on 2007-06-07
> **swarup said:**
> As you'll see below, I tried executing the terminal command but it says it "cannot find" the program. ... the executable file of the windows program is Baraha.exe
.....
swarup@swarup-laptop:~$ wine /dev/hda1/baraha_director/baraha_program.exe
wine: cannot find '/dev/hda1/baraha_director/baraha_program.exe'

If the name of the executable is baraha.exe why are you using baraha_program.exe?

Edit: This 'installed' program may not work anyways because it wasn't installed to Wine. It really just depends on how the program is coded, but for best chance of success reinstall the program to wine.

---

### Post by swarup on 2007-06-07
> **Songwind said:**
> Okay, here's the relevant line.



The device name is /dev/hda1, and the device is mounted at /media/disk.

So to access a file that was on your windows partition as C:\foo\bar.exe you would do this in wine:

```

wine /media/disk/foo/bar.exe

```

What's the full path in Windows to the software you want to run?

Also, you might be able to just double-click the file in Nautilus (the file manager).  I know that in Kubuntu w/ CrossOver (a WINE variant) you can do that.

Here is the full path in Windows to my executable file: 

c:\Program Files\Baraha 7.0\Baraha.exe

I tried it as seen here below, but it still didn't work:

swarup@swarup-laptop:~$ wine /media/disk/Program_Files/Baraha_7.0/Baraha.exe
wine: cannot find '/media/disk/Program_Files/Baraha_7.0/Baraha.exe'

HEY -- I just tried opening it through the file manager, and it opened right up.  Amazing!!
Does this mean I do not need to bother with Wine??? I can just click on any windows program through the file manager, and it'll open up?

Anyhow, I'm still curious why I could not get  it to run properly through Wine in terminal. Why was my command line wrong?

---

### Post by Songwind on 2007-06-07
For one thing you replaced the spaces with underscores.  Try

```

wine "/media/disk/Program Files/Baraha 7.0/Baraha.exe"

```

And don't forget that Linux is case-sensetive.

As for using the file manager, you are still using wine, you're just launching it in a different way.

---

### Post by mlentink on 2007-06-07
> **swarup said:**
> Does this mean I do not need to bother with Wine??? I can just click on any windows program through the file manager, and it'll open up?
No, it means you have discovered how to run your 'windows program in wine. Because that is what it does.
But no, not every program will work, and some only with quite a bit of tweaking. 
I personally would look for Linux alternatives, which are usually just as good or better and rather more affordable ;-)

---

### Post by Astrodan on 2007-06-08
I think I will add to this a bit.  WINE certainly will not run everything, but, I have found it very useful to run items which are not yet ported to Linux.   I'm not certain to tell that this will work, but, the suggestion that you "right click" and "open with WINE" does work under GNOME.  Typically, I move the package to a directory in my home file area, then open using the right click.  The desktop can be used for single file installs.  You should see the usual program install questions, such as, which directory, etc.  Be PATIENT, the final registering is sometimes a little slow and don't expect the Windows icons or links to always be made.  After the package is installed.  The Applications, Wine, Programs, should take you to the folder, and hopefully, nice things happen.  If you can't see the program, check Places, Home Folder, View, Show Hidden Files,.Wine, Drive_C.  It's in there somewhere if the install worked.

---

### Post by brennydoogles on 2007-06-14
> **swarup said:**
> I thought I might have found the error, but see below-- it still doesn't work.

swarup@swarup-laptop:~$ wine /media/disk/dev/hda1/baraha_director/baraha_program.exe
wine: cannot find '/media/disk/dev/hda1/baraha_director/baraha_program.exe'

The problen you seem to be having is that Baraha is most likely not in a directory called baraha_director. If you have ever used tab completion, try using it to navigate to dev/hda1/Program Files/Baraha/Baraha.exe or something similar to that. Remember to type  in the first two or three letters of your destination, and then hit TAB. If you hit TAB and nothing happens, press it twice and a list of all possible completions will come up, and you can type the next letter or so of the one you want before hitting TAB again. Note that the filepaths ARE case-sensitive, so /dev/hda1/program files/ is not the same as /dev/hda1/Program Files/ I hope that helps!!



*just as a note, if the file you are trying to navigate to isn't either an installer file or a standalone program (one that runs without installation) it is not likely to run in wine in this manner. You would actually need to install the program to your WINE virtual drive C*

---

