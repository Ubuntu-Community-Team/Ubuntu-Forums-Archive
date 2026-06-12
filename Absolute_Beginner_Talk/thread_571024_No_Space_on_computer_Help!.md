---
title: "No Space on computer? Help!"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by SkipBlue on 2007-10-08
I was trying to install a game, but it seems I didn't have enough space on my computer, a pop-up came up telling me there was no space left. I deleted most of those files, and some others, but it seems there has not been an improvement in space. When I try jack@jack-laptop:~$ gksudo gparted
I get
No space left onjack@jack-laptop:~$
and the pop-up "Failed to run gparted as user root.

Unable to copy the user's Xauthorization file."

any help?!?!:confused:

---

### Post by shad0w_walker on 2007-10-08
It sounds stupid, but when after you deleted the files, did you empty the trash bin?

---

### Post by llamakc on 2007-10-08
can you get a Terminal open? Run:

df -h

and post the results.

---

### Post by SkipBlue on 2007-10-08
This sounds stupider, but, I'm new, how do I get to the trash?

---

### Post by llamakc on 2007-10-08
> **SkipBlue said:**
> This sounds stupider, but, I'm new, how do I get to the trash?

Are you using Ubuntu or Kubuntu or Xubuntu?

---

### Post by SkipBlue on 2007-10-08
> **llamakc said:**
> can you get a Terminal open? Run:

df -h

and post the results.

jack@jack-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4             3.7G  3.5G   12K 100% /
varrun                252M  232K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   96K  252M   1% /proc/bus/usb
udev                  252M   96K  252M   1% /dev
devshm                252M   20K  252M   1% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1              26G   22G  3.5G  87% /media/hda1
/dev/hda2             7.5G  6.6G  856M  89% /media/hda2
jack@jack-laptop:~$

---

### Post by Blah3 on 2007-10-08
Is you hard drive like thinking that its stuffed and can't eat one more bite or is it just not enough to install the game (if so, game and audio files are usually very large...)?

---

### Post by SkipBlue on 2007-10-08
> **llamakc said:**
> Are you using Ubuntu or Kubuntu or Xubuntu?

Ubuntu

---

### Post by SkipBlue on 2007-10-08
> **Blah3 said:**
> Is you hard drive like thinking that its stuffed and can't eat one more bite or is it just not enough to install the game (if so, game and audio files are usually very large...)?

it thinks it can't eat one more byte

---

### Post by shad0w_walker on 2007-10-08
You can get to the Trash folder by clicking the little Trash icon in the bottom right corner of your screen (Thats the default position) Its a little orange and white trash can. You can either right click on the icon and select empty trash, or click the icon and select the empty trash icon in the window it opens.

---

### Post by SkipBlue on 2007-10-08
> **shad0w_walker said:**
> You can get to the Trash folder by clicking the little Trash icon in the bottom right corner of your screen (Thats the default position) Its a little orange and white trash can. You can either right click on the icon and select empty trash, or click the icon and select the empty trash icon in the window it opens.

I see no trashcan on my desktop (ask for screenshot if you wish)

---

### Post by llamakc on 2007-10-08
/dev/hda4             3.7G  3.5G   12K 100% /

In the terminal type: 

sudo apt-get clean

and then re-run the `df -h` command and see if that cleared up some space. The `apt-get clean` command removes the old *.deb packages.

---

### Post by Blah3 on 2007-10-08
Ah, then don't delete your files for fun, a recently added file or program could be doing this, or you could be getting haxed, or of course you could just have a problem in you hardware.  I guess I'm a doubting that its the ubuntu-izzle if you don't have a super buggy version.

---

### Post by SkipBlue on 2007-10-08
> **llamakc said:**
> /dev/hda4             3.7G  3.5G   12K 100% /

In the terminal type: 

sudo apt-get clean

and then re-run the `df -h` command and see if that cleared up some space. The `apt-get clean` command removes the old *.deb packages.

jack@jack-laptop:~$ sudo apt-get clean
Password:
jack@jack-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4             3.7G  3.4G  145M  96% /
varrun                252M  232K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   96K  252M   1% /proc/bus/usb
udev                  252M   96K  252M   1% /dev
devshm                252M   20K  252M   1% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1              26G   22G  3.5G  87% /media/hda1
/dev/hda2             7.5G  6.6G  856M  89% /media/hda2
jack@jack-laptop:~$ 

i think that worked, eh?

---

### Post by llamakc on 2007-10-08
> **SkipBlue said:**
> jack@jack-laptop:~$ sudo apt-get clean
Password:
jack@jack-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4             3.7G  3.4G  145M  96% /
varrun                252M  232K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   96K  252M   1% /proc/bus/usb
udev                  252M   96K  252M   1% /dev
devshm                252M   20K  252M   1% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1              26G   22G  3.5G  87% /media/hda1
/dev/hda2             7.5G  6.6G  856M  89% /media/hda2
jack@jack-laptop:~$ 

i think that worked, eh?

Well you only have 4% of free space. You may have to clear more space.

---

### Post by shad0w_walker on 2007-10-08
If you post a screen shot that would be helpful to show you where the icon is. If you want to just add one to the tool bar then you can do so like this:

1. Right click on one of the panels (Top or bottom panel, your choice)
2. Click Add to panel... This will open up a dialog with a selection of different applets you can add.
3. Find the section marked 'Desktop and Windows' in the list of applets (It's the second section on my list)
4. Click and drag the Deleted Items applet icon onto one of the panels

You can follow my previous instructions from this point to empty the trash.

---

### Post by SkipBlue on 2007-10-08
> **llamakc said:**
> Well you only have 4% of free space. You may have to clear more space.

o, rly???

:( 

how?? (clear trash i guess but I don't have the trash icon :( )

---

### Post by King_Critter on 2007-10-08
> **SkipBlue said:**
> I see no trashcan on my desktop (ask for screenshot if you wish)

It's not actually on your *desktop* -- it's on the bottom *panel*.

---

### Post by SkipBlue on 2007-10-08
> **King_Critter said:**
> It's not actually on your *desktop* -- it's on the bottom *panel*.

The panel with the time, etc? thats on the top for me, and I don't see a trashcan there either...

---

### Post by llamakc on 2007-10-08
> **SkipBlue said:**
> o, rly???

:( 

how?? (clear trash i guess but I don't have the trash icon :( )

The top line of that output:

```

/dev/hda4             3.7G  3.4G  145M  96% /

```

Shows that you have 145M free with 96% usage. Since you do not have a separate /home directory, do you have stuff that can be moved elsewhere in your /home/jack directory? I see you have two other partitions mounted in /media.

---

### Post by shad0w_walker on 2007-10-08
On a default install of Ubuntu you have a panel at the top and bottom of the screen. Either you have been changing things around or you aren't actually using Ubuntu.

---

### Post by llamakc on 2007-10-08
> **SkipBlue said:**
> The panel with the time, etc? thats on the top for me, and I don't see a trashcan there either...

If you don't see the TrashCan, or you have modified the standard Default desktop, open the terminal and do this:

cd ~/.Trash

Now, look at the stuff in there before deleting it:

ls

If you can live with all of it going bye-bye, do:

rm -R *

IT IS VERY IMPORTANT THAT YOU ARE IN THE ~/.Trash directory when removing the files.

---

### Post by SkipBlue on 2007-10-08
> **llamakc said:**
> The top line of that output:

```

/dev/hda4             3.7G  3.4G  145M  96% /

```

Shows that you have 145M free with 96% usage. Since you do not have a separate /home directory, do you have stuff that can be moved elsewhere in your /home/jack directory? I see you have two other partitions mounted in /media.

I really wish I knew what that meant...

---

### Post by shad0w_walker on 2007-10-08
Labeled for you:

Filesystem            Size      Used   Avail   Use%   Mounted on

/dev/hda4             3.7G     3.4G    145M  96%     /

Basically it means you have 96% used on your root partition (By default where everything goes)

---

### Post by SkipBlue on 2007-10-08
> **llamakc said:**
> If you don't see the TrashCan, or you have modified the standard Default desktop, open the terminal and do this:

cd ~/.Trash

Now, look at the stuff in there before deleting it:

ls

If you can live with all of it going bye-bye, do:

rm -R *

IT IS VERY IMPORTANT THAT YOU ARE IN THE ~/.Trash directory when removing the files.



[email]jack@jack-laptop:~/.Tras[/email]h$ rm -R
rm: missing operand

---

### Post by shad0w_walker on 2007-10-08
You missed the

*

from the rm -R command

---

### Post by SkipBlue on 2007-10-08
> **shad0w_walker said:**
> You missed the

*

from the rm -R command

[email]jack@jack-laptop:~/.Tras[/email]h$ rm -R*
rm: invalid option -- *

---

### Post by Jem00 on 2007-10-08
> **SkipBlue said:**
> [email]jack@jack-laptop:~/.Tras[/email]h$ rm -R
rm: missing operand

You have to put the asterisk (*)

---

### Post by shad0w_walker on 2007-10-08
There is a space in the command, just copy and paste it:

```
rm -R *
```

---

### Post by SkipBlue on 2007-10-08
> **shad0w_walker said:**
> There is a space in the command, just copy and paste it:

```
rm -R *
```

[email]jack@jack-laptop:~/.Tras[/email]h$ rm -R *
rm: remove write-protected regular file `bcm43xx-gtk-installer-0.2.1/ndiswrapper-1.47/driver/pnp.o'?

---

### Post by shad0w_walker on 2007-10-08
[SIZE="4"]Warning[/SIZE] Be absolutely sure you are in the right directory and you do not need any of the files you are about to delete.

Try running this:


```
sudo rm -R *
```

---

### Post by llamakc on 2007-10-08
> **SkipBlue said:**
> [EMAIL="jack@jack-laptop:%7E/.Tras"]jack@jack-laptop:~/.Tras[/EMAIL]h$ rm -R *
rm: remove write-protected regular file `bcm43xx-gtk-installer-0.2.1/ndiswrapper-1.47/driver/pnp.o'?

Yeah it's going to ask you about each individual file. There's a way to force it to do all of them without questioning you but it's probably better for you to do it one by one until you're more comfortable with the command line and the commands.

---

### Post by Beggar on 2007-10-08
Same warning as everyone else is saying, use this with care.

To empty your trash from the command line:

```

sudo rm -rf ~/.Trash/*

```

---

### Post by SkipBlue on 2007-10-08
thanks! that worked
still dont have alot of space, but have some... 
/me grumbles about how small the partition is...

---

### Post by Beggar on 2007-10-09
Please mark as solved.

---

