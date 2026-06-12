---
title: "freeze on login screen"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by viblo on 2006-04-03
Today I installed ubuntu on an old computer (amd with a geforce 2 agp version) I have. However, it hangs on the loginscreen. I had almost the exact same problem when I tried to install ubuntu on another computer, (p4 2Ghz, geforce 4600), but then it worked after I followed the guide on how to install nvidia drivers here:
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)
However, not this time. After I tried to do step 4 in the problems section of that guide (entered the red lines into xorg.conf) the freezing did not occur directly. Instead I could enter name/password ok, but then the screen went brown with mouse pointer visible and nothing more happend and the keyboard not responding.
Any ideas?

---

### Post by ndhskp on 2006-04-03
[quote=viblo]Today I installed ubuntu on an old computer (amd with a geforce 2 agp version) I have. However, it hangs on the loginscreen. I had almost the exact same problem when I tried to install ubuntu on another computer, (p4 2Ghz, geforce 4600), but then it worked after I followed the guide on how to install nvidia drivers here:
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")
However, not this time. After I tried to do step 4 in the problems section of that guide (entered the red lines into xorg.conf) the freezing did not occur directly. Instead I could enter name/password ok, but then the screen went brown with mouse pointer visible and nothing more happend and the keyboard not responding.
Any ideas?[/quote]Okay, what kind of specific video card do you have and what resolutions does your monitor have.

---

### Post by viblo on 2006-04-04
video: Geforce 2 GTS
Im not completley sure the exact resolutions my monitor can handle, but I know it can use 1024x768@75Hz. I tried to delete all entries of 1280x in my xorg.conf file, and also different (low) settings when trying do run dpkg-reconfigure xserver-xorg as someone suggested in a post here somewhere, but it didn't help.

---

### Post by Stealth on 2006-04-04
Ok, for this one you did use the second command right?

```
sudo apt-get install **nvidia-glx-legacy** nvidia-settings linux-restricted-modules-`uname -r`-nvidia-legacy
```

That's the main part in bold, I'm sure a Geforce2 will need those instead of *nvidia-glx*

---

### Post by trent dillman on 2006-04-04
Also, log in command line, and go to the /tmp folder and delete /tmp/gconf-(whatever your username is)

ex.:```
rm -r /tmp/gconf-jeff/
```

Just in case :-P

---

### Post by viblo on 2006-04-04
Yes, I used the legacy-part.
There was no folder gconf* in the tmp folder to delete.

---

### Post by Pragmatist on 2006-04-04
please attach your /etc/X11/xorg.conf  file here.

---

### Post by viblo on 2006-04-04
oki

---

### Post by ndhskp on 2006-04-04
[quote=viblo]oki[/quote]Try runing dpkg-reconfigure xserver-xorg again but this time select the video driver "nv"  this is an open source driver.  Let's see how that works.  Also edit your xorg.conf file manully to remove the "1280x1024" entries.  I only bring up the higher resolutions because they require more computing power in your card.  Get the lower resolutions working then we can try "1280x1024".

---

### Post by viblo on 2006-04-04
It didn't help. Still freezes on the login screen. I think nv was selected from the beginning before I tried to install the nvidia drivers.

---

### Post by ndhskp on 2006-04-04
[quote=viblo]It didn't help. Still freezes on the login screen. I think nv was selected from the beginning before I tried to install the nvidia drivers.[/quote]Okay.  It shows the screen and mouse.  Do they have any visual corruption, if not maybe this don't have anything to do with the video drivers.  Can you <Ctrl-Alt-F2> to the tty2 terminal at the freeze.  If you can get to tty2 terminal, then login on the tty2 terminal and type "top" and look at the processes near the top and see what they are.  Also try running "ps fax" and see what shows up there.  This won't work you say, try <Ctrl-Alt-F2> to the tty2 terminal at the login screen before loging in.  Then type this "sudo /etc/init.d/gdm stop".  Then type "startx" and reoprt back as to what happened with "startx".

---

### Post by viblo on 2006-04-04
[QUOTE=ndhskp]Okay.  It shows the screen and mouse.  Do they have any visual corruption, if not maybe this don't have anything to do with the video drivers.  Can you <Ctrl-Alt-F2> to the tty2 terminal at the freeze.  If you can get to tty2 terminal, then login on the tty2 terminal and type "top" and look at the processes near the top and see what they are.  Also try running "ps fax" and see what shows up there.  This won't work you say, try <Ctrl-Alt-F2> to the tty2 terminal at the login screen before loging in.  Then type this "sudo /etc/init.d/gdm stop".  Then type "startx" and reoprt back as to what happened with "startx".[/QUOTE]

No, Ctrl-Alt-F2 doesn't work (even pressing num lock won't lit the num-light on the keyboard). Also, I don't see any corruption, the screen just shows the normal login screen.

---

### Post by Mustard on 2006-04-04
Further down in the guide you were using (the link you showed in your first post), there is a 'Problems Section'.  In item 4. of the Problems section there are instructions for dealing with a problem that sounds very close to your problem.  I would suggest you try the options in your xorg.conf described in that section of the How To.

---

### Post by viblo on 2006-04-04
[QUOTE=Mustard]Further down in the guide you were using (the link you showed in your first post), there is a 'Problems Section'.  In item 4. of the Problems section there are instructions for dealing with a problem that sounds very close to your problem.  I would suggest you try the options in your xorg.conf described in that section of the How To.[/QUOTE]

I have already tried item 4, but I did another try. However, same result, still freezed on the login screen. However, the nvidia logo is displayed a short moment before if that can help?

---

### Post by Pragmatist on 2006-04-04
I'm assuming you can access your system indirectly, or you wouldn't be able to give us your xorg.conf file :)

If it were me, I would first try booting into single-user mode.  You do this by setting your default runlevel to 1  in your /etc/inittab file.  There are other ways too.

If that works, then I would try without using GDM.  You can do this without uninstalling it, by moving the links in the /etc/rcN.d directories.  Just make a note on paper of what links were where (they are easy to recreate).  You could alternatively probably just rename the /etc/init.d/gdm script to /etc/init.d/gdm-test  or something memorable.  This way the links in the /etc/rcN.d directories won't find the /etc/init.d/gdm script.  When your done, just rename it back to gdm.

---

### Post by Mustard on 2006-04-04
[QUOTE=viblo]I have already tried item 4, but I did another try. However, same result, still freezed on the login screen. However, the nvidia logo is displayed a short moment before if that can help?[/QUOTE]

Note:- This is a pretty useless post, as I lost track of what the problem was, but I'll leave it here as a reminder of my sometimes very ordinary troubleshooting skills. :P

Hmmm..there is certainly a known problem with nvidia that causes this type of lockup, but there is also an unrelated problem that causes lock ups too.  This other problem is related to the .ICEauthority and .Xauthority (hidden files in your $HOME folder) becoming owned by root.  I'm wondering whether we should be eliminating that as a cause so that the finger can be confidently pointed at it being a nvidia driver issue.

I wonder if you could just do this command so we can get that potential cause out of the way and concentrate on the nvidia issue.

Here is what my system returns
```
mustard@slave:~$ ls -al .*authority
-rw-------  1 mustard mustard 5135 2006-04-05 08:38 .ICEauthority
-rw-------  1 mustard mustard  165 2006-04-05 08:38 .Xauthority

```

Systems which have the corrupted files will return that these files are owned by 'root', rather than owned by the user.  It's quite likely that is **not the issue**, as you say you have only just installed and haven't been able to get into the desktop yet. I'm running out of ideas, so its an angle to try anyway. :)

-edit-

The more I think about your problem the stranger it seems.  So you are saying it locks up **at the login screen** not **after logging in**?

---

### Post by viblo on 2006-04-05
Pragmatist: I used the ftp command to upload it to another computer I have at home (with winxp :) after selecting recovery in the boot menu. Dont think that is what you mean by indirectly, but I tried to set the runlevel anyway. Then the computer freezed on the ubuntu loadin screen. The last line says "Sendin all processes the TERM signal".

Mustard: No, they both where owned by me. However, all other commands Ive done like apt-get have been done from the root you get when you login in "recovery"-mode. Can this be a problem?
Yes, the lock is at the login screen, where you usually enter the login name.

---

### Post by Mustard on 2006-04-05
[QUOTE=viblo]<snip>Mustard: No, they both where owned by me. However, all other commands Ive done like apt-get have been done from the root you get when you login in "recovery"-mode. Can this be a problem?
Yes, the lock is at the login screen, where you usually enter the login name.[/QUOTE]

Yeah, the symptoms that I was thinking about happen **after login**.  I didn't think about that until after I had typed it all out, and then went back to reread the previous posts.  I'm still really not sure what's going on.  The message you are recieving about "Sendin all processes the TERM signal" reminds me of shutdown message, which is quite a strange message to be appearing at the login screen.

---

### Post by Pragmatist on 2006-04-05
> 
 Originally Posted by: **viblo**
 [QUOTE]Pragmatist: I used the ftp command to upload it to another computer I have at home (with winxp :smile: after selecting recovery in the boot menu. Dont think that is what you mean by indirectly, **but I tried to set the runlevel anyway.** Then the computer freezed on the ubuntu loadin screen. The last line says "Sendin all processes the TERM signal".
 [/QUOTE]
 
 By indirectly I mean: However you got us the /etc/X11/xorg.conf  file.  I use ssh or a LiveCD, ftp is good too.
 
 What exact steps did you take to "try and set the runlevel"?
 
 I'm fairly sure that getting the line "Sending all processes the TERM signal." Isn't specific to shutting down.  Instead I think it is specific to changing runlevels.  Shutting down is just one runlevel (runlevel 0).  If you reboot (runlevel 6) you'll get the same line.
 
 From what I've heard so far, combined with some similar experiences I've had recently, I believe your problem is with X (X server).  On all Linux systems there is at least one runlevel that lets you boot into a system that is entirely text-based (no GUI).  X is a GUI.  So, that is why I'm suggesting changing your runlevel in your /etc/inittab file and then rebooting.  NOT typing the command "runlevel".
 
 What I did when my keyboard/monitor were both frozen, was that I ssh into my frozen machine from another computer and then used the shutdown command.  That was the only way out (even reboot didn't work right).  So, what I would do is edit the /etc/inittab file and set the default runlevel to 1.  Then I would shutdown the computer.  Then I would physically turn the machine off (if shutdown didn't do that already).  Then I would physically turn the machine on.

---

### Post by viblo on 2006-04-06
What I did was to boot into recovery mode and then change the 2 in runlevel line  in inittab to an 1. 

After Ive read your new post, I tried to install ssh ([https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)) and then ssh to it from my winxp computer after it had frozen at the login screen. That didn't work, the computer didn't respond at all. So I guess that even if the problem is with X, when it locks at the loginscreen everything is frozen, not only the visual part.

---

### Post by Pragmatist on 2006-04-06
Once you setup ssh did you also setup the ssh server on the Ubuntu machine?  You must do that for it to work.
 
 It is possible that the problem is not X related, although I personally doubt it.  Whatver the problem is, you have two broad choices:
 
 1.) Gather more information.
 2.) Start over by reinstalling.
 
 If it were me, I would try number 1.  Since you were able to get us the /etc/X11/xorg.conf file, I'm assuming you can get us some files (even without ssh).  So, here are some files we need. These are all in the **/var/log** directory:

**auth.log**
boot
 daemon.log
 debug
**dmesg**
kern.log
**messages**
**syslog**
user.log
**xorg.0.log**

Anything in /var/log/debian-installer directory  (if there is anything there)

We probably won't need all of this, but it is not hard to attach them.  If you don't feel like attaching all of them, then attach the ones in bold.

---

### Post by viblo on 2006-04-06
I don't think it will help to reinstall, Ive already tried that :)

Anyway, I attached the files you asked for. However, I couldn't find the file boot, and I skiped the debian-installer/cdebconf folder, because it was over 4MB.

---

### Post by Mustard on 2006-04-06
I take it you have attempted to use the 'vesa' drivers again?  Or it was the vesa drivers that wouldn't work initially hence the switch to nvidia drivers?

Looking through the logs I haven't spotted anything yet that is actually informative in terms of giving a direction to go. There are a number of sections in which it is obvious from the error messages that gdm is continously crashing and it seems it gets caught in an unresolvable situation at that stage, as its usually followed by messages relating to shutting down or rebooting the machine (which I assume is user intervention when the lock up occurs).

/me reads some more of the logs...

This is a strange section of the syslog..

```
Apr  3 15:24:22 localhost gdm[7277]: gdm_slave_xioerror_handler: Ã\226desdigert X-fel - Startar om :0
Apr  3 15:24:26 localhost gdm[7854]: gdm_slave_xioerror_handler: Ã\226desdigert X-fel - Startar om :0
Apr  3 15:24:26 localhost gdm[7123]: deal_with_x_crashes: KÃ¶r skriptet XKeepsCrashing
Apr  3 15:25:05 localhost gdm[7123]: Misslyckades med att starta X-server ett flertal gÃ¥nger under en kort tidsperiod, inaktiverar display :0
Apr  3 15:44:10 localhost -- MARK --
Apr  3 15:56:23 localhost kernel: [4296644.219000] nvidia: module license 'NVIDIA' taints kernel.
Apr  3 15:56:23 localhost kernel: [4296644.234000] NVRM: The NVIDIA GeForce2 GTS/GeForce2 Pro GPU installed in this system is
Apr  3 15:56:23 localhost kernel: [4296644.234000] NVRM:  supported through the NVIDIA Legacy drivers. Please
Apr  3 15:56:23 localhost kernel: [4296644.234000] NVRM:  visit http://www.nvidia.com/object/unix.html for more
Apr  3 15:56:23 localhost kernel: [4296644.234000] NVRM:  information.  The 1.0-7667 NVIDIA driver will ignore
Apr  3 15:56:23 localhost kernel: [4296644.234000] NVRM:  this GPU.  Continuing probe...
Apr  3 15:56:23 localhost kernel: [4296644.234000] NVRM: No NVIDIA graphics adapter found!
Apr  3 15:56:32 localhost shutdown[8098]: shutting down for system reboot
Apr  3 15:56:32 localhost init: Switching to runlevel: 6
```

It seems to be saying its going to use nvidia-legacy drivers and then decides there is **no nvidia graphics adapter found**. o_0

-edit-
Or is it saying it wants the legacy drivers?  (I have trouble understanding log messages :) )

-edit2-

Ok..well that error occurs on April 3rd, but doesn't seemed to be repeated again on April 7th, so I'm assuming that something changed during that time. :)

/me keeps hunting through the logs..

---

### Post by wesman83 on 2006-04-08
I've had the same issues but it only happens when ive changed settings in gnome. if you remove .gconf/ and .gconfd/ (or move them to .gconf.old/ and .gconfd.old/) it will boot with no problems, however you will not have any gnome settings.... it seems like its not a nvidia driver problem then.

---

### Post by viblo on 2006-04-08
Mustard: Yes, I've tried a number of settings on my own, some which made the gdm unable to start and showed an error, so Im not supprised if there is a lot of stupid errors in the logs :)

wesman83: I have not been able to start gnome yet, so I havnt changed any settings (afaik).. But I tried to remove the folders anyway, but it didn't help.

---

### Post by Pragmatist on 2006-04-08
If you disable GDM, X won't be started and you'll end up in a text console.  The easiest way to do this is by moving the gdm script so the runlevel scripts can't access it.  You can always put it back:

This next command will move the gdm script to your home directory
```
sudo mv /etc/init.d/gdm $HOME
```

Now shutdown and the restart the computer.  Let us know what happens.

---

### Post by viblo on 2006-04-08
It worked fine.

Edit: Do you think that another linux dist would work better?

---

### Post by Pragmatist on 2006-04-08
[quote=viblo]**It worked fine.**

Edit: Do you think that another linux dist would work better?[/quote]

What worked fine?  Tell us exactly what happened.

---

### Post by Pragmatist on 2006-04-08
Ok, assuming you can get to a text console and login, try this:

```
startx
```

Let us know what happens.

---

### Post by viblo on 2006-04-08
Yep, I got a text console and could log in just fine. I then tried startx and it switched to a black/white-noise background and an x as mouse pointer. I could move the mouse pointer for a few sec, and then it froze.
Edit: I didn't reboot the computer right away, but waited some minutes to see if it really was frozen.

---

### Post by Pragmatist on 2006-04-08
Try this after logging in, do the same thing (i.e. type startx)  then when your machine appears to be frozen, do this:
 
 ```
CTRL-ALT F1
```  
If CTRL-ALT-F1 doesn't take you to a login screen with a login prompt, try using, F2, F3, F4, F5, or F6 instead. X is located on F7 What your looking for is a screen with a login prompt. Once you find one, login like you did before and do this:
 
Let's first get some information on what processes are actually running:

```
ps -ef >>pstext.txt
``` ```
pstree >>pstree.txt
``` 
Now let's kill X:

 ```
ps -ef |grep X
```  
 make sure you use a capital 'X' in the above command.  You'll get something that looks like this:
 [B]
root      7659  7658  3 08:24 ?        00:08:47 /usr/bin/X11/X -dpi 100 -nolisten tcp[/B]
 
 What you do now is kill it by typing the first 4-digit number (7659) along with the kill command:
 
 ```
kill 7659
```  
 Your process ID will probably be something other than 7659, so obviously use yours.
 
Give us those two files (pstext.txt and pstree.txt)
So report back. If you can do this, it just means that we are really homing in on your problem. Next, we will try and run GNOME.

---

### Post by viblo on 2006-04-08
Nothing happens when I press ctrl-alt-f1 (or ctrl-alt-f2 or..)

---

### Post by Pragmatist on 2006-04-08
Ok, so instead of running startx Let's first get some information on what processes are actually running. Once your done, give us the files here.
     [LEFT]```
ps -ef >>process.txt
``` ```
pstree >>process.txt
``` 

Also, let's get some information on what drivers are loaded and some of your PCI cards:
```
lsmod >>hardware.txt
``` ```
lspci >>hardware.txt
``` 

And, some info on your interrupts and I/O ports and memory:
```
cat /proc/ioports >>proc.txt
``` ```
cat /proc/interrupts >>proc.txt
``` ```
cat /proc/meminfo >>proc.txt
``` 

Finally, let's see your partition table (I'm mostly interested in your swap partition, but let's see it all) This assumes your system is on the first IDE hard drive /dev/hda  If not, adjust accordingly:
```
sudo fdisk -l /dev/hda >>partition.txt
``` 
[/LEFT]

---

### Post by Pragmatist on 2006-04-08
In that thread you linked in your original post. The howto for Nvidia drivers. In looking at your xorg.conf file, I see that you have these modules:

Section "Module"
        Load    "bitmap"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Whereas in the howto, he recommends this:
> 
 Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 #[COLOR=Blue]Load "dri"[/COLOR]
 #[COLOR=Blue]Load &#8220;GLcore&#8221;[/COLOR]
 Load "extmod"
 Load "freetype"
[COLOR=Lime]Load "glx"[/COLOR]
 Load " int10"
 Load "record"
 Load "type1"
 Load "vbe"   
Why not add the one's your missing?

Load "dbe"
Load "ddc"
#[COLOR=Blue]Load "dri"[/COLOR]
#[COLOR=Blue]Load &#8220;GLcore&#8221;
[/COLOR]Load "record"
And, as he mentions, try the one's in blue if necessary

---

### Post by Pragmatist on 2006-04-08
One more thing.  You asked whether or not you should try another distribution of  Linux.  If it were me, I would use Knoppix.  You don't have to install it since it runs off of the CD (it is a LiveCD).  Knoppix is highly-regarded for it's ability to test hardware.

---

### Post by viblo on 2006-04-09
I tried with the modules from the guide, but it didn't worked. I also tried some other options (like running dpkg-reconfigure xserver-xorg) in betweeen following the guide and uploading the file, so I guess it has been overwritten. I could of course edit the file to match the state it was directly after the guide if you think it will help.

Edit: I actually found 3 different LiveCDs I already had burned. One with Knoppix and two with Morphix. I should have thought of them myself :) Anyway, I tried to boot from each one of them, and Knoppix froze at the screen I think is shown while X is loaded. But, both morphix-dists worked (except for the mouse, couldnt move it at all in one of them, and move it up-down in the other)! I tried to read what it printed while it booted, and from what I could see, knoppix said something about using nv as graphics driver, and at least one of the morphix cds said something about a tainted nvidia.o? The LiveCDs are a couple of years old.

---

### Post by Mustard on 2006-04-09
Sheesh, its seems like your system is one of those systems that just doesnt like linux. :)
(At least on the disply side of things)

It might be worth either getting a more recent version of Knoppix, or even trying Kanotix, which in my opinion, is a litte more polished than Knoppix.

They are very useful as rescue CD's too.  I've found them very useful for getting around some difficult problems with linux.

While we are on the subject of live CD's and rescue CD's, I'd recommend another one that I first saw recommended by Pragmatist in another thread, if I recall correctly, the Super Grub Disk.

Anyway, I'll stop dragging the thread too far off subject now. ;)

---

### Post by viblo on 2006-04-11
Maybe it is possible to read out which settings Morphix uses?

---

### Post by Pragmatist on 2006-04-11
[quote=viblo]Maybe it is possible to read out which settings Morphix uses?[/quote]

Sure you can.  Just mount your hard drive's partition and then copy information from the LiveCD to your hard drive.  By default you are inside morphix/knoppix directory tree.  As I understand it, these LiveCDs are using RAM to store their information (thus the idea of a ramdisk).  So, for example, if you wanted to use the xorg.conf file that morphix is generating, you do this:

1.) mount your hard drive partition
2.) copy /etc/X11/xorg.conf to your mounted hard drive

That should be it!

---

### Post by viblo on 2006-04-12
I started morphix and mouted the hard drive, that worked fine. However, there was no xorg.conf file in /etc/X11. However, there were two other files, XF86Config and XF86Config-4 which had a similiar construction. I have attached them whith this message.

---

### Post by Mustard on 2006-04-12
Hmmm..well the XF86Config-4 file is not that far removed from what xorg.conf looks like.  I wonder what the specific differences in them might be.  The second one XF86Config looks like some type of template for the creation of the first one (XF86Config-4).

/me peruses the files..

Comparing these to my xorg.conf file I wonder whether these lines are going to be different in xorg.conf for Ubuntu.  I certainly don't see them mirrored in my xorg.conf.  The reference to 'Speedo' is definitely missing in the my font path, and no 'Speedo' exists at that location.

```
Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath     "/usr/X11R6/lib/X11/fonts/Speedo"
	FontPath     "/usr/X11R6/lib/X11/fonts/PEX"
# Additional fonts: Locale, Gimp, TTF...
	FontPath     "/usr/X11R6/lib/X11/fonts/cyrillic"
#	FontPath     "/usr/X11R6/lib/X11/fonts/latin2/75dpi"
#	FontPath     "/usr/X11R6/lib/X11/fonts/latin2/100dpi"
# True type and type1 fonts are also handled via xftlib, see /etc/X11/XftConfig!
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/ttf/western"
	FontPath     "/usr/share/fonts/ttf/decoratives"
	FontPath     "/usr/share/fonts/truetype/openoffice"
	FontPath     "/usr/X11R6/lib/X11/fonts/defoma/CID"
	FontPath     "/usr/X11R6/lib/X11/fonts/defoma/TrueType"
```

I suppose with some mucking around you could get it to work as a xorg.conf file.  The mode lines and resolution settings look quite similar to how xorg.conf would use them.  I'd be tempted to take your current xorg.conf and then just take from the XF86Config-4 file just the stuff you need to set the resolutions.  Mind you when I look at it, its a fiddly job to work out what goes where.

I'm also curious whether an more recent version of Morphix would use Xorg instead of XFree86, as it seems to me that many distros have switched to Xorg.

---

