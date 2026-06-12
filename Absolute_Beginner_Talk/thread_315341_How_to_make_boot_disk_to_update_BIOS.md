---
title: "How to make boot disk to update BIOS"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by DapperMe17 on 2006-12-09
My OS is Ubuntu Edgy

I'd like to flash the BIOS. Therefor, I need to format a bootable floppy.

I have the boot disk file...FDOEM.144.

What terminal command do I enter in order to make the floppy bootable?

I tried...sudo dd if=FDOEM.144 of=/dev/fd

...but it delivers the error...dd: opening `FDOEM.144': No such file or directory


Some help would be appreciated,
Thanks

---

### Post by K.Mandla on 2006-12-09
I'm not sure if this is any help, but you can get images of bootable, driver-free floppies at [www.bootdisk.com]("http://www.bootdisk.com").

Edit: Oops, I think I misunderstood your post. Sorry. :(

---

### Post by DapperMe17 on 2006-12-09
There's a ton on that site...which one do you suggest, DOS 6.22?

Will Smart Boot Manager(open source) do what I need it to?

---

### Post by DapperMe17 on 2006-12-09
Anyone out there:p

---

### Post by houstonbofh on 2006-12-09
Is it a compressed image?  For example, I use this command to build firewalls.
> gzcat /usr/m0n0wall/generic-pc-1.11.img | dd of=/dev/ad0 bs=16k
You can try your command with the full path, or try cat or gzcat piped to dd.

---

### Post by DapperMe17 on 2006-12-09
Sorry, very new to Ubuntu/Linux. No compression.

File is on desktop, want it on floppy.



Terminal entry...

cat /home/xxxxx/desktop/FDOEM.144 | dd of=/dev/fd0

...No such file or directory




What is the correct command?

---

### Post by DapperMe17 on 2006-12-09
Update!!!

Floppy has been formatted with FreeDOS fine. 

I was able to copy the .exe BIOS file fine.

But, when I boot, the FreeDOS prompt appears but doesn't run the .exe file.


Is there a command that has to be entered to run the file????

---

### Post by bulldog on 2006-12-09
It will not run by itself :D  you have to put it after the prompt.

A:\some.exe or if it is in a directory you have to change to that directory with cd\somedirectory.

Long time sins I have being a DOS user though :D

---

### Post by DapperMe17 on 2006-12-09
Thanks, but...:???:-? 

I was able to enter the .exe file name fine...found the file, but returned a reply similar to "unable to run file type in DOS" or something very similar to that.

Can I run a .exe BIOS update file in FreeDOS?


Baby steps...

---

### Post by bulldog on 2006-12-09
Maybe you have the wrong .exe file.
I know you can do this running windows,and such a file won't run in a DOS environment.

---

### Post by DapperMe17 on 2006-12-09
It's definitely the right one for the mobo...downloaded directly from manufacturer's site (HP). Originally Win98 PC.

---

### Post by bulldog on 2006-12-09
Wait a minute here,normally there's a application which you need to open the BIOS file.
You only nee DOS to make a bootable disk.

---

### Post by OBnascar on 2006-12-09
> **bulldog said:**
> Wait a minute here,normally there's a application which you need to open the BIOS file.
You only nee DOS to make a bootable disk.

That is correct, just put the Bios Flash exe on your windows desktop, double click the icon and from that point you need not do anything.....

---

### Post by Duck2006 on 2006-12-09
If you need to boot of a disk at start up. You need a bootable disk with a autoexec.bat file to boot the exe file with. but as OBnascar typed from the desk-top is the easy eay to do it just don't have a power failure or the system will be a door stop

---

### Post by DapperMe17 on 2006-12-10
Lads,

I'm on Ubuntu...not Win98. 

1) I have the BIOS update, an .exe file. 
2) I have a floppy formatted with FreeDOS
3) I have the BIOS .exe file on that floppy
4) I am able to boot to the FreeDOS startup, as well as type in the .exe file       name to execute
5) Here's my stump...when I enter the name of that .exe file, I get a FreeDOS message similar to "FreeDOS is not able to execute this type of file", or somthing very similar to that.


What could I be doing incorrectly?

Thanks for your replies:-D

---

### Post by ezsurfer on 2006-12-10
I don't think the manufacturer's Bios flash will run under anything OTHER THAN a DOS disk.  Flashed several older systems before, you need the exe file they give you, and the .bin (binary) file that you are upgrading to.  The command is usually 

flasher.exe thenewbuild.bin

Substitute the manufacturer's names for flasher exe file and the binary file name, normally alphanumeric.  

they only work on a vanilla boot, no OS running at the time of the flash, other than DOS.  

That's my recollection.  Good luck.

---

### Post by OBnascar on 2006-12-10
post deleted

---

### Post by DapperMe17 on 2006-12-10
I thought that's what FreeDOS is for?  Just stick the .exe file there & enter it at boot, then it should just work. 

If it's easier, just tell me how to "simply" update my BIOS from scratch.

---

### Post by DapperMe17 on 2006-12-11
Anyone?

---

### Post by houstonbofh on 2006-12-11
> **DapperMe17 said:**
> Anyone?
Since you seem stuck, try some boot disks from here;
[http://www.bootdisk.com/](http://www.bootdisk.com/)
There is one for BIOS flashing I have used to good effect.

---

### Post by CatKiller on 2006-12-11
As ezsurfer says, normally there are two files - the flashing utility (.exe) and the BIOS update itself (.bin). There should be instructions on how to perform the update with these programs on the page where you got the update from. Perhaps if you provided a link to that page, someone here might be able to interpret them for you or fill in the gaps. As it is, we're just speculating based on other flashes of other machines at some point in the past.

Good luck.

---

### Post by ciscosurfer on 2006-12-13
I have written a HOWTO discussing how to flash your BIOS.  You can find it here: [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")

---

