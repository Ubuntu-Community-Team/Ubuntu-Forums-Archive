---
title: "can't find 'computer' or 'home' folder"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Geek Sanity on 2006-07-04
In the places menu, I click on 'computer' and my computer acts like it's going to open it, and then it doesn't.  Same with the home folder.  And I still can't get the codecs installed to play mp3s

---

### Post by aysiu on 2006-07-04
What's the terminal output of this command? ```
nautilus
``` Also, can you explain so far what you've tried to get MP3s to play and what error messages (if any) you get if you try to play them?

---

### Post by blackjack6.21.91 on 2006-07-04
Very wierd problem.  Do you have some sort of wierd partitioning scheme set up?
Open a terminal (in gnome, do applications -> acessories -> terminal) and type the word *nautilus*.  The terminal should spit back some text.  Copy it and tell us what it said.

You can install mp3 compatibility via *bumps*.  I have attached a copy to this post.  Download it, unzip it, click the bumps folder, and then double click *bumps*.  Choose the option "run in terminal".  It should be pretty self explanitory from there.

EDIT:  beat me to it, aysiu.  but i attached BUMPS!

Peace,
blackjack

---

### Post by Geek Sanity on 2006-07-04
As far as getting mp3s to play, I have tried downloading the w32 codec packs from mplayer.hu (my friend runs Debian, and suggested it) but I get stuck installing it.

Tried typing nautilus into a terminal, and NOTHING comes up. Just the cursor blinks at me.  I don't think I have any wierd partioning scheme going on

---

### Post by aysiu on 2006-07-04
[QUOTE=Geek Sanity]As far as getting mp3s to play, I have tried downloading the w32 codec packs from mplayer.hu (my friend runs Debian, and suggested it) but I get stuck installing it.[/quote] Well, that's the problem, then. w32codecs is not how you get MP3 working. Try [this](https://help.ubuntu.com/community/RestrictedFormats#head-e18f2d510b1efe975368b818b5aa3ae2b2eee5c8) instead.

> 
Tried typing nautilus into a terminal, and NOTHING comes up. Just the cursor blinks at me.  I don't think I have any wierd partioning scheme going on In other words, you see this? ```
geeksanity@ubuntu:~$ nautilus


``` I'm not sure if this'll solve the problem, but can you try this? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by Geek Sanity on 2006-07-04
[QUOTE=aysiu]

 In other words, you see this? ```
geeksanity@ubuntu:~$ nautilus


``` I'm not sure if this'll solve the problem, but can you try this? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```[/QUOTE]

yes, thats what I see.  pasted it, and still nothing.  It looks like this 
> portia@portia:~$ nautilus
sudo aptitude update
sudo aptitude install ubuntu-desktop


---

### Post by aysiu on 2006-07-04
I was thinking of something more like this: ```
portia@portia:~$ nautilus
portia@portia:~$ 
portia@portia:~$ sudo aptitude update
portia@portia:~$ sudo aptitude install ubuntu-desktop
``` There's a Control-C you have to press after Nautilus to get a normal command prompt back.

---

### Post by Geek Sanity on 2006-07-04
So is this what it's supposed to do?
> portia@portia:~$ sudo aptitude update
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [19.9kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [23.0kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages [19.4kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages [14B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources [5690B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources [14B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages [96.7kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages [3809B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources [24.2kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources [840B]
Fetched 194kB in 5s (37.6kB/s)
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
portia@portia:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
portia@portia:~$


---

### Post by aysiu on 2006-07-04
Yeah, that's what it's supposed to do, but I guess that didn't change anything (i.e., solve your Nautilus-launching problem).

---

### Post by blackjack6.21.91 on 2006-07-04
Make sure nautilus is not popping up in the background.  It does that sometimes.  Also make sure you are not running kubuntu.. If think you may be type konqueror in instead of nautilus.  Otherwize I really don't have much advice, sounds like there is some kind of problem.  EDIT:  I just realized how stupid that sounds.  lol noduh.

peace yo

---

### Post by Geek Sanity on 2006-07-05
How would I know if it's popping up in the background? And no, as far as I know, not running Kubuntu

---

### Post by Geek Sanity on 2006-07-05
*bump* 

I'm afraid to shut down for fear of it doing what it did last time, and I really don't want to have to reinstall again....Sides, I've been told that there are few problems big enough that you would have to reinstall...Was told this AFTER I reinstalled the last time.

---

### Post by Bloch on 2006-07-05
open a terminal.
Do other commands work like:
xterm  or evince?
When you enter 
ls
do you see your files and folders? Can you save a file onto your desktop?

What do you get from entering pwd? (gives the present working directory)
What happens when you enter 
nautilus
?? Is there any error message? 

What disks and partitions show up when you go to
System > Administration > Disks
(it is possible you might have set up some strange partition system)

---

### Post by Geek Sanity on 2006-07-05
ok, here goes:
> portia@portia:~$ xterm
portia@portia:~$ evince
bash: evince: command not found
portia@portia:~$ ls
Desktop  skirt001.jpg  w32codecs_20060611-0.0_i386.deb
portia@portia:~$ mount /mnt /vanyel
mount: only root can do that
portia@portia:~$


so commands are working, some a bit slower than others.  I don't have disks under system/administration.  I didn't think I set up partitions, because it was working fine sunday morning.  I saved soemthing to my /tmp/ and after that I quit being able to access the folders.  And I can't get in there to delete what it is to see if that fixes it

---

### Post by blackjack6.21.91 on 2006-07-05
You can list the files in your /tmp folder by using these two commands.
> cd /tmp
ls
After you have done that, and you know what temp file might be the problem, you can remove it with:
> rm fileinquestion.tmp
or edit it with
> gedit fileinquestion.tmp

If the above doesn't solve the problem, do
> sudo apt-get install thunar
Thunar is like nautilus, and though not the same, you will still be able to navigate folders till you get this problem solved.

---

### Post by Geek Sanity on 2006-07-05
> portia@portia:~$ cd /tmp
portia@portia:/tmp$ ls
errormyE5xz    gconfd-root     mapping-portia  orbit-root      xmms_portia.0
gconfd-portia  keyring-i2WXcB  orbit-portia    ssh-LFigeq6390
portia@portia:/tmp$
portia@portia:/tmp$ sudo apt-get install thunar
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package thunar
portia@portia:/tmp$


Apparently the file I moved into tmp isn't there, so I guess I didn't move it in there.  ARRRGH! I'm about to get really frustrated

---

### Post by Bloch on 2006-07-05
Something strange is going on. Anyone else got ideas from reading through this thread? 

Am I correct: the command 
nautilus
does nothing, and gives no error message.
evince
reports command not found.

Part of your gnome desktop is missing. Maybe some system files got moved to the wrong place. System files can only be moved by the administrator, that is, when the admin (aka root) password is given.

Do you have the gnome desktop? (It's possible you might have installed a different desktop) Do you have Applications  Places System on the top left?  Is there a menu item "About gnome" under the System menu?

Was this a fresh installation? I see when you type 
sudo aptitude update
that your system is being updated from the hoary repositories. Hoary is an earlier version. Since then there has been Breezy Badger and now Dapper Drake. Most people are running Dapper Drake. Why didn't you install from the most recent disc? If you have access to broadband and a CD burner then i would advise downloading and burning the up-to-date disk. (Choose the alternate disk)

---

### Post by blackjack6.21.91 on 2006-07-05
I suggest completely uninstalling nautilus (including config) and then doing
> sudo apt-get install ubuntu-desktop

---

### Post by ed_d on 2006-07-05
What do you get when you type:
#df -h

Post response here. I have seen weird things happen when your filesystems fill up.....

---

### Post by Geek Sanity on 2006-07-05
I installed hoary because it was tghe cd I had...I don't have a cd burner or access to one, otherwise I would have installed Dapper.  Yes I am running gnome.

---

### Post by Geek Sanity on 2006-07-05
Ed_d, t did the same thing as when I typed nautilus.  NOTHING.

> portia@portia:/tmp$ #df -h

and I can't get OUT of my tmp folder now

---

### Post by ed_d on 2006-07-05
ok, You didnt need the # in the command, my bad. # is just the prompt. Ope a new terminal window and just type in df -h

What the command shows is your mounted filesystem with the space they have used and what you have left. Here is what it looks like from my box:

ed@Loki:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              16G  3.3G   12G  22% /
tmpfs                1014M     0 1014M   0% /dev/shm
tmpfs                1014M   13M 1002M   2% /lib/modules/2.6.12-10-686-smp/volatile
/dev/sdb5              34G   14G   19G  42% /multimedia
/dev/sdc5              34G   18G   15G  55% /multimedia/ibm
/dev/sdd5              34G  2.1G   30G   7% /multimedia/wintel
/dev/sde5              34G  7.1G   25G  22% /multimedia/hp_sun
/dev/sdf5              34G  2.7G   30G   9% /multimedia/misc
ed@Loki:~$

---

### Post by Geek Sanity on 2006-07-05
Ok, here we go. 
> 
portia@portia:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             5.7G  1.7G  3.8G  31% /
tmpfs                  62M     0   62M   0% /dev/shm
/dev/hdc1              76G   16G   56G  23% /mnt/vanyel
/dev                  5.7G  1.7G  3.8G  31% /.dev
none                  5.0M  2.8M  2.3M  55% /dev
portia@portia:~$



---

### Post by ed_d on 2006-07-05
OK, that all looks good from the output, nothing close to full. 

Can you run top? to run it just type in top and hit enter, it should show what process is running. not sure if it will answer your main question, but at least we can see whats running.

And just for my sanity, you install Hory, and after install, what packages did you install, or did you run automatix or easy ubuntu?

---

### Post by Geek Sanity on 2006-07-06
> ortia@portia:~$ top

top - 00:43:53 up 2 days,  8:43,  2 users,  load average: 0.57, 0.23, 0.08
Tasks:  81 total,   2 running,  79 sleeping,   0 stopped,   0 zombie
Cpu(s): 26.0% us,  3.2% sy,  0.2% ni, 69.2% id,  1.5% wa,  0.0% hi,  0.0% si
Mem:    125856k total,   123324k used,     2532k free,     5044k buffers
Swap:   297160k total,   129176k used,   167984k free,    29604k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
22441 portia    15   0  106m  37m  13m S 16.3 30.4  70:19.00 firefox-bin
 5468 root      16   0  102m  17m 4376 R  6.7 14.0 123:03.15 Xorg
11848 portia    15   0 30200  10m 7224 S  3.2  8.6   0:04.75 gnome-terminal
 9222 portia    15   0 48104  10m 7336 S  2.1  8.5  14:01.32 gaim
21656 portia    17   0  2080 1040  820 R  0.4  0.8   0:00.16 top
 6461 portia    15   0  4656 1220 1036 S  0.2  1.0   0:10.63 xscreensaver
 6495 portia    15   0 30372 6828 4900 S  0.2  5.4   0:40.46 gnome-panel
 6534 portia    15   0 19548 4776 4136 S  0.2  3.8   0:42.81 mixer_applet2
 7516 cupsys    26  10  6864 1092  956 S  0.2  0.9   0:16.41 cupsd
    1 root      16   0  1552  396  372 S  0.0  0.3   0:00.99 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0
    3 root       5 -10     0    0    0 S  0.0  0.0   0:01.45 events/0
    4 root       6 -10     0    0    0 S  0.0  0.0   0:00.07 khelper
   22 root      15 -10     0    0    0 S  0.0  0.0   0:00.00 kacpid
   95 root       5 -10     0    0    0 S  0.0  0.0   0:01.39 kblockd/0
  131 root      15   0     0    0    0 S  0.0  0.0   0:00.67 pdflush
  133 root       9 -10     0    0    0 S  0.0  0.0   0:00.00 aio/0


I just went through and clicked smart update, and installed what it told me to

---

### Post by Geek Sanity on 2006-07-07
Bump Bump Bump

---

### Post by jordanmthomas on 2006-07-07
I have a few things you can try:

```

sudo aptitude purge nautilus
sudo aptitude install nautilus

```

What this will do is remove anything that has to do with nautilus and then reinstall nautilus.

Then, try to run nautilus:

```

nautilus

```

If that doesn't work, I agree with an earlier post suggesting you install thunar.

---

### Post by Geek Sanity on 2006-07-07
still nothing when I type Nautilus
> portia@portia:~$ sudo aptitude purge nautilus
Password:
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following packages will be automatically REMOVED:
  ubuntu-desktop
The following packages have been kept back:
  login passwd
The following packages will be REMOVED:
  nautilus ubuntu-desktop
0 packages upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 2683kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 66549 files and directories currently installed.)
Removing ubuntu-desktop ...
(Reading database ... 66546 files and directories currently installed.)
Removing nautilus ...
Purging configuration files for nautilus ...
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
portia@portia:~$ sudo aptitude install nautilus
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following packages have been kept back:
  login passwd
The following NEW packages will be installed:
  nautilus
0 packages upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/819kB of archives. After unpacking 2650kB will be used.
Writing extended state information... Done

Preconfiguring packages ...
Selecting previously deselected package nautilus.
(Reading database ... 66520 files and directories currently installed.)
Unpacking nautilus (from .../nautilus_2.10.0-0ubuntu9_i386.deb) ...
Setting up nautilus (2.10.0-0ubuntu9) ...

Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
portia@portia:~$ nautilus



---

### Post by Geek Sanity on 2006-07-09
still no joy yet  I'm getting scared here

---

### Post by Geek Sanity on 2006-07-09
Ok, that worked...Now I know what it is.  I have a severe shortage of RAM, and if something asks for memeory and it's not there, it dies.  So, reboot it is...Thank you everyone who helped me out.  Now I need to go back to page 1 and work on installing bumps

---

