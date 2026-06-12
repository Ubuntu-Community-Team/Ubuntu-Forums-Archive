---
title: "iMac G3 Kubuntu live problem"
date: 2006-01-17
forum: Apple PPC Users
---

### Post by xandizzle on 2006-01-17
I'm trying to run the live kubuntu disk on my iMac G3 and it's gotten to a point where the screen is just black.  I heard the cd rom making noise for about 30 minutes with no result and just now it stopped and it's stuck on a black screen.  Everyonce in a while it'll make a quick sound and then go back to ideling.  I mean the cd is spinning you can here it whirlling but the computer doesn't seem to be reading it.  Is it a screen resolution problem?  Maybe it just can't display it correctly.  I don't know,

how bout you


xan

---

### Post by Ptero-4 on 2006-01-17
Is it one of the early iMac models. Because those are known to have display configuration problems and the LiveCD requires some command-line tricks to get to the GUI on those iMacs.

---

### Post by linear on 2006-01-17
The command line tricks are as follows:

After booting is complete (you are at the black screen):
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/kdm restart (return) to restart KDE

At the very least you'll need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

If you restart KDE and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

### Post by iMacUser on 2006-04-04
Can you help a complete newbie who is having the same problem, I am really struggling to understand what to do.  

I am trying to run the live kubuntu 5.10 CD on my iMac 266Mhz G3 and get the same problem as xandizzle.  I have tried to follow the command line tricks posted by linear, but find that when I type: sudo nano /etc/x11/xorg.conf the file is empty (shown as a "new file" in the editor).  So there is no monitors section to modify.

Once/if I manage to find and modify this file, does step 6 complete the launching of the GUI? or is there something else to do next?

Thanks for any help - I'd really like to try out Kubuntu on my iMac.

---

### Post by linear on 2006-04-04
Linux is case sensitive, so that's a capital "**X**" in **sudo nano /etc/X11/xorg.conf** . "x11" and "X11" are not the same.
 
Once you complete the steps, you should be back to the gui. Just watch out for the problem with DRI; don't know if your model is affected.

---

### Post by iMacUser on 2006-04-04
Great - I can edit xorg.conf now.  I also disabled DRI and can now get as far as seeing the desktop background and the taskbar (after about 15 minutes).  However, after about 20 minutes of CD ROM activity, I have a KDE desktop error "There was an error in process KDE desktop".

After that I can do nothing, except move the mouse around the desktop.  The only recourse I could see was to switch off the iMac.

Thanks once again for any help anyone can give.

---

### Post by linear on 2006-04-04
The extreme slowness is what you might get if you _didn't_ disable dri, so this is puzzling. Just to confirm, you commented out (or deleted) the line that reads "load dri" in xorg.conf?

---

### Post by iMacUser on 2006-04-06
Yes, I deleted the line that reads "load dri" in the modules section of xorg.conf.  So I'm not sure what to do next?

---

### Post by linear on 2006-04-06
I'm not sure either. Do you have a Ubuntu Live CD (Gnome instead of KDE) as well? That might be worth a try.

---

### Post by iMacUser on 2006-04-07
Tried a Ubuntu live CD this evening - took about 50 minutes to get to the desktop.  I had ensured that dri was disabled, changed the monitor settings (HorizSync and VertRefresh) in /etc/X11/xorg.conf and restarted gdm.  Couldn't see any taskbar, just the wallpaper, CD-ROM icon and File Manager.  If I clicked on anything it took about 5 minutes to get a response.

Would it be any better to install Kubuntu or Ubuntu onto my hard drive - if it would, how would I partition the drive to do this?

---

### Post by linear on 2006-04-08
Hard to say if an install would be better. But if you want to try...

First read these:

[https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

This worked for me:

1. Back up OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively. Make the partition at least 5GB, but bigger is better if you really plan to use it.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

### Post by iMacUser on 2006-04-21
Thanks linear for the great support.

Following your suggestions, I have successfully installed Kubuntu and set up to dual boot with Mac OS 8.6. 
Kubuntu worked fine once installed, even better now I have added more RAM to my iMac (now 288MB, up from 96MB).

My future plan is to try installing an 80GB hard disk to replace the original 6GB one, and then install both Mac OS 8.6 and Kubuntu.  But for now, everything seems to be working fine.

---

### Post by Quetzalyo_Coyotl on 2006-10-13
I've been trying to install ubuntu live 6.06 on a G3 imac with a new hard drive (40gb) I've already thrown in 256 ram as the website required, also, I followed the steps all the way thru 5, thats where I hit ctrl-x but it doesn't exit back to the command line. When going thru step 4 and I hit return it tells me that I don't have permission to write the file. I'm stuck! Help! Is there another trick up someones sleeve?

                             THX.

---

### Post by linear on 2006-10-15
> **Quetzalyo_Coyotl said:**
> it tells me that I don't have permission to write the file.

Are you sure you typed "sudo nano", not just "nano"?

---

### Post by johnca on 2006-11-02
> **linear said:**
> The command line tricks are as follows:

After booting is complete (you are at the black screen):
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/kdm restart (return) to restart KDE

At the very least you'll need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

If you restart KDE and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

I'm actually using ubuntu 6.10, but this thread described my problem almost exactly, trying to boot live on a G3 iMac (500MHz). I edited and saved xorg.conf, but now i can't seem to restart gdm. "gdm -restart" and "gdm-restart" don't work, the gdm man page wasn't helpful, neither was looking at /etc/init.d/gdm. Somewhere else i saw to try ctrl-backspace (nothing), and killing gdm processes and just running gdm (the processes die, but "gdm" doesn't start the window manager or return any message, i just get another command line prompt).

Help?

---

### Post by johnca on 2006-11-02
> **johnca said:**
> I'm actually using ubuntu 6.10, but this thread described my problem almost exactly, trying to boot live on a G3 iMac (500MHz). I edited and saved xorg.conf, but now i can't seem to restart gdm. "gdm -restart" and "gdm-restart" don't work, the gdm man page wasn't helpful, neither was looking at /etc/init.d/gdm. Somewhere else i saw to try ctrl-backspace (nothing), and killing gdm processes and just running gdm (the processes die, but "gdm" doesn't start the window manager or return any message, i just get another command line prompt).

Help?

Even "sudo gdm restart" wasn't working, but i got an answer on IRC (#ubuntu) - "sudo killall gdm" then "sudo gdm start".

---

### Post by oswaldkelso on 2006-11-02
Thanks worked a treat (Edubuntu 610) imac 333mhz. Only problem is as the screen was black I did not enter a user name or password!!! 

back to the forum 

Answer was 

control option F1

*sudo adduser yourusername*

answer the questions and your password when happy y to accept.

I had to 
[I]
sudo killall gdm[/I]

then

[I]sudo gdm start
 [/I]

to get the GUI back

PS. The big flaw is that I can use the disc and sudo ok but when I try to install a box pops up to ask for a root password

pps. Taken from [http://ubuntuforums.org/showthread.php?t=75604&page=3&highlight=imac](http://ubuntuforums.org/showthread.php?t=75604&page=3&highlight=imac)

Thanks linear

OK, I think I have a solution now - the reason we couldn't restart Gnome is that it never actually stopped. The "* Stopping GNOME Display Monitor [ ok ]" message is false, as the gdm process is still running afterwards.

So instead, try this:

To stop the process, use:

sudo killall gdm

Then make your edits to xorg.conf. Now start gdm:

sudo /etc/init.d/gdm start

It should work. Good luck!
Reply With Quote this worked for me I got the install icon on the desktop and am installing now.

---

