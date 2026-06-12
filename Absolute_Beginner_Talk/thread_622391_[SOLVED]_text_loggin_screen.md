---
title: "[SOLVED] text loggin screen"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by SteveNorman on 2007-11-24
I have been using 7.10 fine for awhile,,all of a sudden when I try to log in I get a text screen versus the graphic screen I usually get. I tried to use an older version in grub but get the same thing. What do I need to do to get my GUI back? I am on a different computer now. I am very new to linux and dont really know where to start with this

---

### Post by jken146 on 2007-11-24
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mali2297 on 2007-11-24
Do you get any error messages?

If you can login via the text console, then you can try starting the graphical interface with
```

startx

```
(Temporary solution.)

---

### Post by SteveNorman on 2007-11-25
I tried both,, with the sudo command I get to the config screen, but I cant get anything to happen when I press enter. Its as if the keyboard isnt there all of a sudden. I cant choose between yes and no, cant press enter..etc

With the startx command I get this:
x: Cannot stat/tmp/.x11-unix(permission denied)
abrting
giving up
xinit: connection refused (errno111): unable to connect to x server
xinit: no such process(errno 3): server error

I have a nvidia gforce 6600 card, which ubuntu found a driver for,

---

### Post by SteveNorman on 2007-11-25
I did an update last night,, I guess I lost my driver for the graph card? Can I get it back from the text screen since I cant seem to run the reconfig screen?

---

### Post by dwhitney67 on 2007-11-25
There might be a clue or two in the file /var/log/Xorg.0.log.  This file is a log of what transpires when X (windows) is started.

Btw, did you try to startx as sudo?

```
$ sudo startx
```

---

### Post by SteveNorman on 2007-11-25
No I didnt,,Im pretty new to all this,,great way to learn I guess. I am having to switch between computers so this is going to take abit. (Only have one monitor keyboard etc.), I'll try in a bit and post the results. What do I do if the sudo  startx works?

---

### Post by mali2297 on 2007-11-25
Boot in failsafe mode, and try
```

dpkg-reconfigure xserver-xorg

```
again. (sudo shouldn't be needed in failsafe mode.)
When asked about graphics driver, choose **vesa**, it will work most of the times (I think). By the way, what graphics card do you have?

If you don't want to switch computers while working on the problem, you can try a text mode web browser:
```

w3m ubuntuforums.org

```
**Shift-H** gives you a list a keyboard shortcuts, **q** quits the browser.

---

### Post by SteveNorman on 2007-11-25
nvidia gforce fx 6600
ddr 512M

PCI-E

---

### Post by SteveNorman on 2007-11-25
Nothing has worked,, cant get the text browser to work,, nothing. I just dont get what I am doing wrong. Maybe Im to comp illiterate to use linux. What I really dont get is that I had everything working great up till 2 days ago. Rotating cube, the whole ball of wax. Then when I would switch users, I would get a blank greyish screen instead of the login,, but a reboot fixed it. Then all I get are text logins. Exactly what happens is this:
Power On, get the usuall bios readings
Get the Ubuntu logo with colors on a black screen with an orange load bar,,
then text and a text login

Do I need to take the 3d card out of the comp?

---

### Post by SteveNorman on 2007-11-25
The sudo starx gets the same reaction as the startx alone,,
the sudo config gets to the blue config screen with <yes> hilighted in red, but nothing happens when I press enter

I am at a loss here

---

### Post by sailor2001 on 2007-11-25
sounds like wrong resolution.......   sudo dpkg-reconfigure -phich xserver-xorg   with my nvidea driver in gutsy, I had to put in 1280x1024 rather than what I had been using under Feisty = 1024x768

---

### Post by jken146 on 2007-11-25
Try ```
dpkg-reconfigure -phigh xserver-xorg
```

Use TAB to move around the options in the blue screens and enter (or maybe spacebar?? as well) to choose them,


If it is your resolution it should be easy enough to edit xorg.conf directly and add your resolution to the list of resolutions already there,  ```
sudo nano /etc/X11/xorg.conf
```

---

### Post by marinesrock.1990 on 2007-11-25
Try this web-page:

[http://ubuntuforums.org/archive/index.php/t-94864.html]("http://ubuntuforums.org/archive/index.php/t-94864.html")

---

### Post by mali2297 on 2007-11-25
> **SteveNorman said:**
> The sudo starx gets the same reaction as the startx alone,,
the sudo config gets to the blue config screen with <yes> hilighted in red, but nothing happens when I press enter

I am at a loss here

Did you boot in failsafe mode? Do you get any error messages during boot?

It seems really strange that the keyboard doesn't respond. :-k
Did you try other keys besides Enter?

---

### Post by SteveNorman on 2007-11-25
I tried all the keys and got nothing, By booting in fail safe mode, do you mean recovery option in grub? I may have done that wrong

---

### Post by mali2297 on 2007-11-25
> **SteveNorman said:**
> I tried all the keys and got nothing, By booting in fail safe mode, do you mean recovery option in grub? I may have done that wrong

Yes, my bad. #-o I meant **recovery mode**.

---

### Post by SteveNorman on 2007-11-25
Mairnesrock I did try that thread and had problems with the gedit command.BTW I was USMC 87-93 0351. If I had my SMAW I would have solved this issue a bit ago;] I will try the fail safe when I fig  out how, and the different reconfigure. Thanks for the quik responses all

---

### Post by mali2297 on 2007-11-25
> **SteveNorman said:**
> Mairnesrock I did try that thread and had problems with the gedit command.

You can't use gedit without a graphical interface, use nano instead.

---

### Post by SteveNorman on 2007-11-25
recovery mode gave me the same thing,,a text log in. Should I try the whole shebang from there? I am pretty sure I did last night to no effect..but I will try again when I change off this comp. Is there any way to try and get the driver installed from the text or do I have to run synaptic?

---

### Post by SteveNorman on 2007-11-25
Just replace gedit with nano? I'll try that to. Is there any onther text browser to try?

---

### Post by SteveNorman on 2007-11-25
Alright,,Im gonna print this thread, change out the tower, and have another go...

---

### Post by SteveNorman on 2007-11-25
Alright here we go

Started in recovery mode
last few lines of text:

*Starting the Firestarter firewall   [Failed]
mkdir: `/tmp/.X11-unix':permission denied
rm : cannot remove `/tmp/.clean`: permission denied

Sudo startx gave same permission denied results as previous attempts
Sudo dpkg with the phgh xserver line got me to a screen with card options,,I tries nvidia once with these results:
xserver -xorg postinst warning: overwriting possibly -customized configuration file;back up in /etc/x11/xorg.config.20071125151805

dexconfig:error: cannot vreate temporary work directory; "/tmp/" does not exist or is not a directory

xserver-xorg postinst warning: error while preparing new xorg xserver configuration file in /etc/x11/xorg.conf.dpkg-ew; not attempting to update existing configuration



I also tried the sudo nano /etc/x11/xorg.conf to change the resolution. I hit x to escape,,and ended up having to reboot to get out of it,,I think I screwed something up in there, because when I went back in later it said new file and didnt have the info that was in there the first time.  The loggin errors are the same as they have been the last couple of days,, so even tho I may have caused a new problem, I dont think this is the cause of all this mess




-

---

### Post by SteveNorman on 2007-11-25
I dont know why that face is in my text above,, but it sums up my day,It should say permission denied.
 I have had enough for now,, be back later

---

### Post by mali2297 on 2007-11-26
OK, it seems strange that you don't get permission to /tmp even in recovery mode. Try the advice in this post:
[http://ubuntuforums.org/showthread.php?t=248857?post=#2](http://ubuntuforums.org/showthread.php?t=248857?post=#2)
That is, check available disk space and reset permissions of /tmp.

Also, post the output of
```

ls -l / | grep tmp

```
before and after.

---

### Post by SteveNorman on 2007-11-26
Will do, Is there a way to print from the text screen so I dont have to write it all down?

---

### Post by mali2297 on 2007-11-26
> **SteveNorman said:**
> Will do, Is there a way to print from the text screen so I dont have to write it all down?

It's only one line, should look like this
```

ls -l / | grep tmp
drwxrwxrwt   7 root root  4096 2007-11-26 20:48 tmp

```
Of course, the time will be different.

---

### Post by SteveNorman on 2007-11-26
Thanks,,also is there another way to get to this forum from the text screen so I dont have to keep switching towers?

---

### Post by mali2297 on 2007-11-26
> **SteveNorman said:**
> Thanks,,also is there another way to get to this forum from the text screen so I dont have to keep switching towers?

You can try lynx,
```

sudo apt-get install lynx
lynx ubuntuforums.org

```
But I doubt that will work better than w3m. By the way, did you try w3m in recovery mode?

Do you have a Live CD that you could use?

---

### Post by SteveNorman on 2007-11-26
I dont remember what mode I tried it in (w3m),I will make another pass at it when I switch over towers. I tried using the live cd of 7.04 but it locked up with somekind of graphic error,,It was on the ubuntu start page with the orange loading bar and it froze with blurred images of the logo etc. This is what made me figure out it was the 3d graphix card. I am thinking about taking the  nvidia card out and trying to log in with the motherboard card. Should I be trying to apt-get somekind of driver? this all happened after I upgraded to 7.10. It seem that a lot of people are having similar issues due to losing there restricted drivers.. Also I have a usb keyboard, maybe thats why I cant move around in xconfig?

Not really knowing, but cant I just get get a driver installed and reboot to get back to normal?

I also dont have a problem wiping the hard drive clean and reinstalling ubuntu if that will get me back up and running,, the only thing on that tower is ubuntu. Installed 3 weeks ago or so, and I dont have anywork or paid for software on it.

---

### Post by mali2297 on 2007-11-26
If I understood you correctly, you did manage to navigate through *dpkg-reconfigure xserver-xorg* the last time, but got an error about */tmp*?
Same thing when trying startx etc. I don't think you would get that kind of error messages if it was just the driver.

Of course, you can always reinstall ubuntu. But it would be good to find the cause of the problem so that you don't have to worry about going through the same thing again.

---

### Post by SteveNorman on 2007-11-26
I agree,, I will try and be patient and solve the issue properly. Do you think the usb keyboard is why I cant navigate xconfig from normal login mode? Im gonna switch towers over in a few hours, about 10ish Seattle time. My wife needs to use this comp a little longer.

---

### Post by SteveNorman on 2007-11-26
One thing I dont know if you caught from my earlier posts is that I got into x11 and hit a bad key I dont know how to fix. I am wondering if I did an apt-get update I could get a new x11 file to replace the one I screwed with?

---

### Post by SteveNorman on 2007-11-29
Status, I cant get either w3m or lynx to work
I cant figure out what  the  vertical line in the command " ls -l / | grep tmp " just before grep is on my keyboard. (I or L or1?)

I did a sudu apt-get  for nvidia drivers and setting, so I know It can get online. Not only does the keyboard not work in  dpkg recofig,,the computer is pretty much locked up. 

I cant boot from the live cd,,

how do I wipe my hard drive and re-install? I need this computer to work pretty soon here.

I see that when I boot I get this as well

15.891378 MP-BIOS bug: 8254 timer not connected to IO-APIE. I really want to solve this,, but I need to get moving on this thing,,and since I cant reach the forum from my linux comp I really just want to try and start over versus having to switch peripherals from one tower to the next over and over.

---

### Post by mali2297 on 2007-11-29
> **SteveNorman said:**
> Status, I cant get either w3m or lynx to work
I cant figure out what  the  vertical line in the command " ls -l / | grep tmp " just before grep is on my keyboard. (I or L or1?)


From this [picture]("http://upload.wikimedia.org/wikipedia/en/5/51/KB_United_States-NoAltGr.svg"), it seems that you should press Shift-\.

> 
I cant boot from the live cd,,


How far do you come? Where in the boot sequence does it fail?

> 
I see that when I boot I get this as well

15.891378 MP-BIOS bug: 8254 timer not connected to IO-APIE. 

From this [link]("http://http.download.nvidia.com/XFree86/nforce/1.0-0301/KnownProblems.html"):
> 
If the kernel console boot trace (viewable using dmesg) contains messages such as these:

..MP-BIOS bug: 8254 timer not connected to IOAPIC
...trying to set up timer (IRQ0) through the 8259A . failed.
...trying to set up timer as Virtual Wire IRQ... failed.
...trying to set up timer as ExtINT IRQ... works.

then the incorrect ACPI table entry is present. On 2.6 kernels, this can be worked around by specifying the 'acpi_skip_timer_override' boot line option. An alternative workaround is to disable ACPI in the BIOS or by using the 'acpi=off' boot line option. 


See this [doc]("https://help.ubuntu.com/community/BootOptions#head-911967eb7a39d6fd7179d049f60ec6a5a5b89c1f") on how to specify boot line options.

Also, did you check disk space?

---

### Post by SteveNorman on 2007-11-29
I Okay,,the success first. 

I changed my bios statup device to my dvd and tried to reboot with the live cd. after changing the boot line to acpi=off I was able to log onto the live cd. I had a gui and everything. The only thing I could not do was get on line. I had to change the network settings to static address last time, And I didnt have my current IP. Subnet or Default gateway. But ubuntu  worked from the cd! So the live cd issue was partially from the drive I guess, but I dont know why I had to change the startup drive.

II what didnt work,,and this is gonna be painful...

Adding the acpi=off without the cd did no change. 

I now have new mesages and cannot get into the textbased log at all.

I get a root only command prompt.

So to run this down:
1   results of df -h

/dev/sda1  71g,  3.8g,  64g,  1%,  /
varrun       506m, 4k,   506m, 1%, /var/run
varlock      506m, 0, 506m,      0%,  /var/lock
vdev         506m, 408k, 506m, 1%, /dev
devshm     506m, 0, 506m, 0%, /dev/shm



2    attempted chmod 777/tmp results:
chmod: cannot access `/temp': Input/output error


3     when I boot every time now I get this:

/dev/sda1 contains a file system w/errors check forced
wait while it does something, then gives me a message about starting a maintenance shell then gives me the root Cmdprmpt


4   result of ls -1 / | grep temp:
tmp

nothing else,,just "temp"

trying to change the boot line without the cd gives me a red astricked file system check of root system faild msgg, followed by a broen astricked "root system mounted in read only mode" message with about 10 bash: bad things messages.

that about covers it for now,,


If I didnt know better I would say I have a virus....

---

### Post by mali2297 on 2007-11-30
> **SteveNorman said:**
> I Okay,,the success first. 

I changed my bios statup device to my dvd and tried to reboot with the live cd. after changing the boot line to acpi=off I was able to log onto the live cd. I had a gui and everything. The only thing I could not do was get on line. I had to change the network settings to static address last time, And I didnt have my current IP. Subnet or Default gateway. But ubuntu  worked from the cd! So the live cd issue was partially from the drive I guess, but I dont know why I had to change the startup drive.

Good news, then you can work on the problem from the LiveCD. 

> 
1   results of df -h

/dev/sda1  71g,  3.8g,  64g,  1%,  /
varrun       506m, 4k,   506m, 1%, /var/run
varlock      506m, 0, 506m,      0%,  /var/lock
vdev         506m, 408k, 506m, 1%, /dev
devshm     506m, 0, 506m, 0%, /dev/shm

OK, the problem doesn't seem to be disk space.

> 
2    attempted chmod 777/tmp results:
chmod: cannot access `/temp': Input/output error

Note that it should be
```

chmod 777 /tmp

```
(/tmp not /temp and a space before). Perhaps you typed it correct in the terminal though.
 

> 
3     when I boot every time now I get this:

/dev/sda1 contains a file system w/errors check forced
wait while it does something, then gives me a message about starting a maintenance shell then gives me the root Cmdprmpt


Try to do a file system check from the LiveCD, see here:
[http://ubuntuforums.org/showpost.php?p=2714208&postcount=14](http://ubuntuforums.org/showpost.php?p=2714208&postcount=14)
(Of course, you should change /dev/sda2 with /dev/sda1.)

> 
4   result of ls -1 / | grep temp:
tmp

nothing else,,just "temp"

It should be **ls -l** (lower case L), not ls -1.

> 
trying to change the boot line without the cd gives me a red astricked file system check of root system faild msgg, followed by a broen astricked "root system mounted in read only mode" message with about 10 bash: bad things messages.

that about covers it for now,,


If I didnt know better I would say I have a virus....

Did you have Automatix installed? It doesn't contain a virus or anything but has been reported to cause problems. See the warnings here:
[https://help.ubuntu.com/community/Automatix](https://help.ubuntu.com/community/Automatix)

It might also be hardware problem, I don't know.

---

### Post by SteveNorman on 2007-11-30
Yes I have automatix. I used the book ubuntu for non-geeks to load this initially with feisty. It had us download it for something. Can I remove it?

---

### Post by LowSky on 2007-11-30
```
sudo apt-get remove automatix
```

but I suggest doing a fresh install with a Gutsy LiveCd

---

### Post by mali2297 on 2007-11-30
The cause might have been Automatix,  though I don't know how one would be able to confirm that.
Anyhow, perhaps it's time for a fresh install without any trace of Automatix.

---

### Post by SteveNorman on 2007-11-30
2 questions,,Should I wipe the hard drive first then install?
Is it okay to load feisty vrs gutsy?

okay 3

should I turn off acpi in bios, or was that due to the automatix or whatever error?

---

### Post by mali2297 on 2007-12-01
> **SteveNorman said:**
> 2 questions,,Should I wipe the hard drive first then install?

You get the chance to reformat the drive during the install, that should be enough.

> 
Is it okay to load feisty vrs gutsy?

It's up to you. Since everything worked in Gutsy until the misfortune, perhaps you should try it again.
Stay away from Automatix and let us hope that the problem won't reappear. Again, I can't be certain that Automatix is to blame but it is my best guess. 

> should I turn off acpi in bios, or was that due to the automatix or whatever error?
Turn off acpi only if it is needed to boot, use the method of *trial and error*. 
I think that error is separate from the main problem. 

Good luck. :-)

---

### Post by SteveNorman on 2007-12-01
reloaded with feisty since I had the cd already. Online with it right now! YAY!

thanks for all the help!, should I mark this as solved? I could try re-updating to gutsy and see if it works,, what do you think?
Steve

---

### Post by mali2297 on 2007-12-01
> **SteveNorman said:**
> reloaded with feisty since I had the cd already. Online with it right now! YAY!

thanks for all the help!, should I mark this as solved? I could try re-updating to gutsy and see if it works,, what do you think?
Steve

It should be OK, If the problem reappears then you should [file a bug]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by SteveNorman on 2007-12-01
thanks, I'll mark it solved

---

