---
title: "Need HELP transfering files between 2 PC's via a netgear router"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by obscur156 on 2007-08-12
I am a totaly noob at local networking.
Have been using acomputers for about 11 years and never made a local network.

I have 2 pc at home,mine and my girl friend pc.
We are connected to internet trough a netgear router,i want to easely tranfer files between the 2 PC's.
What do i need to do or wich app does i have to install to do that.
Of course i want something easy if possible.

Thanks.

---

### Post by sancho panza on 2007-08-12
I am able to access the windows machines on my home network from ubuntu without doing any tweaking anywhere. But I dunno how it is to access ubuntu from windows.
(we already have a network made using the "setup network" tool in windows).

---

### Post by skymera on 2007-08-12
if you can borrow and external hard drive.
its so much simpler.

use NTFS or FAT32, both can be recognised.
then copy everything over

---

### Post by ridgeland on 2007-08-12
Here my wife and I both use Ubuntu and use NFS for file sharing.  It's easy.
For Linux to Windows we've used Samba.
Search for those two.

---

### Post by 1/0 on 2007-08-12
Are we talking about two Linux computers or one Linux computer and a MAC/MS/BSD? If its only two *nix computers its really simple, just use NFS. I'll give you a link but first let me know what OS we are talkning about.

---

### Post by irish_flu on 2007-08-12
> **obscur156 said:**
> I am a totaly noob at local networking.
Have been using acomputers for about 11 years and never made a local network.

I have 2 pc at home,mine and my girl friend pc.
We are connected to internet trough a netgear router,i want to easely tranfer files between the 2 PC's.
What do i need to do or wich app does i have to install to do that.
Of course i want something easy if possible.

Thanks.

Are they both using Ubuntu, or is one of them using Windows?

---

### Post by obscur156 on 2007-08-12
I forgot to say that we are both using ubuntu now cause i have converted(if i can say that) my girlfriend to ubuntu and she likes it just like me.

Thanks for your help guys and i will start to check that and dont be shy to post more INFOS.

Best regards.

---

### Post by ridgeland on 2007-08-12
I recommend starting with
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
which with a search for NFS can get you to 
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=NFS&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=NFS&titlesearch=Titles)

---

### Post by ridgeland on 2007-08-12
I forgot to mention that I did one setting in my router to fix the address rather than have it dynamically assigned.  This keeps my PC at 192.168.123.110 and my wife's at 192.168.123.112.  You may be able to get around this with wild cards like 192.168.123.*.
Your LAN may use different values.

---

### Post by obscur156 on 2007-08-12
Thanks i will try NFS .

---

### Post by 1/0 on 2007-08-12
I second using NFS. I used [this guide.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server") I recently got my girlfriend to do the same and we're using NFS for all sorts of files. It takes a while to mount the partitions (especially if they are large) so I don't do it automatically at boot. Instead I made a simple script looking like this:

```

#!/bin/sh
mount ip:/path /mount/folder/path
```

Then made it executable by:

```
chmod +x file
```

Execute it by:

```
$ ./file
```

To unmount make a script with umount /mount/folder/part instead of the line above. The folder is unmounted at shutdown anyway so no worries.

---

### Post by obscur156 on 2007-08-12
Thanks for all those valuable infos.
Best regards.;)

---

### Post by jackn on 2007-08-12
Like 1/10, I have a basic script to make sure nfs is mounted. 
In my case, the mount is done automatically, as it is set up in /etc/fstab. Since often only one of the two networked boxes is on, however, the auto mount often fails. 

The script just keeps trying to mount the other box's fs every ten minutes, in case that other box does get started eventually. The script is run from a crontab. All of this is done reciprocally from both machines.

The result is that whenever the two boxes are running, they are automatically mutually mounted. Not all is rosy, however, for (as explained in another [post]("http://ubuntuforums.org/showthread.php?t=521391&highlight=ssh+on+off+padavoine")), for some reason, although the two boxes can always get a network going, several protocols (rsync, nfs, ssh) are randomly on or off, and only in one direction...

Here is the script:

```
#!/bin/sh

# Tests whether the laptop is nfs mounted on the desktop. If not, mounts it.

if test -e != /mnt/other_machine_name/home;
then mount /mnt/other_machine_name;
fi

```

In short, check if other fs is mouned. If not, mount it.

When it works, which is always the case in one direction, and some of the time in the other, it's a treat and a ball.

Good luck, obscure.

jackn

---

### Post by obscur156 on 2007-08-12
Thanks jackn for the info,i will try later on cause i dont have the time for now.
I see that your in France so Salut le cousin francais if your french lolll.Je suis quebecois.;)

Best regards.:)

---

### Post by ridgeland on 2007-08-12
I also found fstab automount was not a good approach.  I made a script then added it to the menu in Menu-> System Tools running it with "gksu mountNFSscript".  This saves my wife from having to use a terminal window, and gksu asks for sysadmin password since only root can run mount.

---

### Post by obscur156 on 2007-08-12
Thanks budy,i will work on that this week,i hope i will be able to accomplish that.
Maybe i will try to with samba cause i am still triple booting and my girl friend dualbooting.
If i cant make it work i will probably buy an external drive so i can go anywhere with it.

Believe me,i am so anxious to get rid of window$,i have enough of MR.Gates.
As soon as i have my tvout working,i will wipe off XP.

Thanks again ,best regards.

---

### Post by 1/0 on 2007-08-13
Just dump XP now. Believe me the SAMBA stuff just gets irritating and difficult. An update and it might not work. Printing and everything, its just messy. The only reason to keep XP is for programs but I've seen more and more guides on how to emulate programs in Linux and its getting easier and easier. For instance [this guide]("http://frankscorner.org/"), [this one]("http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/") or [this.]("http://ubuntuforums.org/showthread.php?t=433359")

---

### Post by obscur156 on 2007-08-13
Thank you very much 1/0,the only time i boot XP is for watching movies on my TV(tvout) for the rest its UBUNTU all the way.

I will try that this week.
Best regards ,have a nice day man.

---

### Post by 1/0 on 2007-08-13
Try these for dual monitors and you're off with the need for XP:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn)

[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

---

### Post by obscur156 on 2007-08-13
Ok ,i will take a look at it but i tried maybe 4 or 5 times and ended with no screen lolll so each time i have reinstall ubuntu.

i am not an expert to edit config in xorg or what ever.
Its sad that hardware  makers are only delivering window$ driver.
If they dont want to do it,well they should just give the source code so developer can built driver for linux or any other distro.I feel like an HOSTAGE of MICRO$OFT. :evil:

Thanks again budy.

---

### Post by 1/0 on 2007-08-13
Just remember to back up your /etc/X11/xorg.conf that way you can always go back. In worst case:

```
dpkg-reconfigure xserver-xorg
```

You're not an hostage, you've only just opened your eyes to a real OS ;-)

---

### Post by jackn on 2007-08-13
ridgeland, Id like to learn more about your approach.

Could you share some more about your goals and means, in some detail?

Thank you.

jackn

---

### Post by ridgeland on 2007-08-13
Jackn,
voici:
My wife's PC has this script (named mountNFS.sh )
```
!/bin/bash
#   mountNFS.sh
#   mount NFS drives
#
sudo mount 192.168.123.110:/z_Data1/Images /NFS_Images
sudo mount 192.168.123.110:/z_Data1/Music  /NFS_Music

```
We use fixed addresses, my desktop is always 192.168.123.110, not dynamic.  The mount points already exist of course (/NFS_...)
Then just edit the main menu (menu -> system -> preferences -> main menu)
Then under System Tools create a new item, give a name and a good icon.  Use the command
gksu mountNFS.sh
Then to mount the NFS files she just clicks on the menu selects System Tools -> mountNFS and it asks her password (sys admin rights) then displays nothing.  Check in Nautilus and the NFS files are there.  It's a negative to get no feedback when mounting. Oh well.  At least she is not complaining about having to use a terminal window.

---

### Post by jackn on 2007-08-14
OK, ridgeland, crystal clear.

I guess what I was wondering about was the GUI side, as I work off of the command line most of the time.

Didn't realize you could add commands to the menus. Nor did I realize the lack of input downside you point out, finally.

One last detail: why do you gksu it? What is the GUI involved that requires you to resort to gksu, as opposed to sudo?

Thanks.

jackn

---

### Post by ridgeland on 2007-08-14
gksu  I think it's because it's in the menu.  To run a item in the menu set it up to run in a terminal and use gksu or gksudo to get the system admin rights before running the program.  If you run a script that in turn calls for "sudo mount" from the menu, rather than ask for root's password it says "no can do".  
An example is gparted.  If it's in the menu as command gparted it never asks for sys-admin password it just fails to read drives.  But it you put it in the menu with "gksu gparted" it asks for the password and opens the drives.
I haven't tried but maybe I could put some echo commands in the script and check for the presence of a folder like .../Music. But to give feedback would mean a pop-up message window to close each time.  Easier to just assume all is well.

---

