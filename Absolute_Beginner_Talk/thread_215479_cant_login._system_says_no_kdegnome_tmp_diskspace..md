---
title: "cant login. system says no kde/gnome tmp diskspace...HELP"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-07-14
It said login through failsafe with no scripts. did that but my screen is the gnome default color nothing happening.

how can I clear the kde/gnome tmp diskspace?

failsafe gnome doesnt look like its working. 

cant login via kde or gnome.

next option is terminal.

anyone can you please tell me step by step what to do to resolve this?

please?

---

### Post by maddbaron on 2006-07-14
ok i think i understand. but i need help. what is the terminal command line i enter to empty /tmp?  is it sudo empty /tmp  ?

---

### Post by trent dillman on 2006-07-14
log in to recovery mode

```
rm -r /tmp/*
shutdown -r now
```

---

### Post by maddbaron on 2006-07-14
> **trent dillman said:**
> log in to recovery mode

```
rm -r /tmp/*
shutdown -r now
```

ok logged in to recovery bunch of words root@ubuntu: entered the rm -r /tmp/*

was told no such directory existed

shutdown -r now reboted me...

did i do it right? still won't let me in...do i try this code in the failsafe terminal?

---

### Post by maddbaron on 2006-07-14
this is just getting worse.... tried the code in failsafe terminal and was told no such directory. 

1st i did it without sudo in front and it just went to next line.

then i entered the shutdown command and it said I needed to be root to do that. so i retried everything with sudo in front and got the no such file or directory exists.

did i empty it the it time without sudo?

---

### Post by maddbaron on 2006-07-14
back again,

i entered the st code the rm -r code but without the /* at the end and got this message:

rm: remove write-protected regular file '/tmp/.XO-lock'?

if i say yes will it remove it and empty it?

---

### Post by maddbaron on 2006-07-14
....

rm'd tmp finally checked and system said no directory found. 

try to login now i am told:

mkdtemp: private socket dir: access denied.

so i am assuming i have to create a new temp directory? 

so what is code to type into terminal to grant me access to create the directory?

sudo mkdtemp ?

---

### Post by trent dillman on 2006-07-14
hmm.. shutdown -r now is reboot, so that worked. :)

try this:

```
rm -r /tmp
mkdir /tmp
chmod 1777 /tmp
shutdown -r now

```

---

### Post by maddbaron on 2006-07-14
ok doing it now but question when i enter the code and it just goes to the next line does that mean the code was accepted?

such as :

whoever@ubuntu: $ rm -r /tmp
whoever@ubuntu: $

with no dialog after the 1st code is that normal?

---

### Post by maddbaron on 2006-07-14
awwwwwwwwwwwwwwwwwwww...it didnt work.....it said session only last ten seconds. check to see if i am logged out or out of diskspace.

if temp is the problem i dont understand y unless i entered things wrong maybe the sudo was wrong....tmp is a problem.

---

### Post by trent dillman on 2006-07-14
Try also deleting the config files in your home directory:

```
rm -r /home/your-username-here/.[kg]*
```

NOTE: this will remove config files from kde/gnome apps!

And yes, if there was no output, it worked.

---

### Post by maddbaron on 2006-07-14
can i get the config files back? r they important to running the programs? i assume i will just have to reconfig everything again? long as i get to log in i am fine with that but wait. will that undo everything i did to set up my wireless connection? that took me a week to figure out...lol..screw it. long as i get to login i'll redo what needs to be redone.

here's hoping.

---

### Post by maddbaron on 2006-07-14
when i remove the stuff from firefox the .jar/.js/xul is that removing the packages or the actual extensions?

---

### Post by maddbaron on 2006-07-14
i haaaaaaaaave no idea what to do next. zero. just spent last several minutes emptying folders i think and still it says out of space. i am not out of space. my home folder last i saw had the same 4.5 space i originally set it with. i moved all the big files to windows since i have about 12gigs free there.

this is insane. i am so lost as to what to do next. its not even  saying tmp folder anymore just out of diskspace and kde/gnome wont start. but diskspace could be the problem? the root? i havent touched root since i set up ubuntu.

question how many numbers of reboots until the system cleans itself? like defrags itself since i assume thats only way to go now unless i reinstall which i hope not to have to.

this is utterly insane.

---

### Post by trent dillman on 2006-07-14
Since you're asking about firefox, I assume you logged in?

---

### Post by trent dillman on 2006-07-14
what's the output of the following commands:

```
sudo fdisk -l
df -h
cat /etc/fstab
mount
```
?

---

### Post by maddbaron on 2006-07-14
i dont believe this  i tried logging in again and still cant so went to terminal and was told :

bash: cannot create temp file for here document: no space left on device.

What device????

then i tried this from this site
[http://www.cyberciti.biz/faqs/2006/06/delete-or-remove-directory-linux.php](http://www.cyberciti.biz/faqs/2006/06/delete-or-remove-directory-linux.php)

and when i entered sudo rmdir /tmp

it said tmp not empty!

what on earth is going on!

is there an empty command line i can enter? i just dont understand this all.

how can it not be empty after I deleted it and other files?

---

### Post by trent dillman on 2006-07-14
ok, let's go back a little...

```
rm -r /tmp
```

this deletes the /tmp directory, recursively (rmdir only deletes empty directories)

```
mkdir /tmp
```

replace /tmp

```
chmod 1777 /tmp
```

reset permissions

also, post the output of ```
df -h
``` this gives you disk free space info

---

### Post by maddbaron on 2006-07-14
> **trent dillman said:**
> what's the output of the following commands:

```
sudo fdisk -l
[b]fdisk: invalid option -- 1

usage fdisk [-b SSZ] [-u] DISK  Change partition table
      fdisk -1 [-b SSZ [=u] DISK list partition table(s)
      fdisk -s Partition      Give partition siz(s) in blocks
      fdisk -v                Give Fdisk Version
Here DISK is something like /dev/hbd or dev/sda
and partition is something like /dev/hda7
-u: give Start and End inSector (instead of cylinder) units
-b 2048 (for certain MO disks) use 2048-byte sectors[/b]
  
df -h
[b]Files system    Size   Used   Avail  Use%  Mounted on
/dev/hda7          5.8G   5.8G      0    100% /

Everyhing else is normal varrun,varlock,udev all have ample space altho Irm has 202m out of 220 m free its mounted on /lib and says something about volatile.
The remaining of my /dev all have gig's free. i need to empty /dev/hda7 on the / mount but how? [/b]  

cat /etc/fstab
**everything is normal looking except /dev/hda7  on mount / ext3 has errors=mount-ro under the dump and pass sections.**
mount
[b]/dev/hda7 on / type ext3 (rw, errors=mount-ro)
Everything else looks normal[/b]


```
?

so it seems my /dev/hda7 is a problem i need to empty it somehow.

and i asked about firefox cuz when i was emptying stuff from the earlier code in terminal it kept asking mozilla firefox stuff.

sorry it took so long i had to type the screen since i cant upload it

---

### Post by maddbaron on 2006-07-14
> **trent dillman said:**
> ok, let's go back a little...

```
rm -r /tmp
```
[b]rm: remove write-protected regular file '/tmp/.xo-lock' ? I entered Y then got series if operation not permitted 4 times involving /x11-unix,.xo-lock, /tmp/. ICE-unix'
'/tmp/.gdm_socket'[/b]

this deletes the /tmp directory, recursively (rmdir only deletes empty directories)

```
mkdir /tmp
```

replace /tmp

```
chmod 1777 /tmp
```

reset permissions

also, post the output of ```
df -h
``` this gives you disk free space info


```
rm -r /tmp
```
[b]rm: remove write-protected regular file '/tmp/.xo-lock' ? I entered Y then got series if operation not permitted 4 times involving /x11-unix,.xo-lock, /tmp/. ICE-unix'
'/tmp/.gdm_socket'[/b]

---

### Post by trent dillman on 2006-07-14
Looks to me like your hard drive is full, from df -h.

The fdisk -l is an L, not a one. The rest isn't working because you're probably not in recovery mode. I would just empty out your filesystem, mainly removing any music/pictures/etc from your home folder. Ubuntu shouldn't fill that much space unless you've installed a LOT of software, or there's some sort of bug that's writing a ton of info into /var/log/*.....

...which is something to check:

```
du -h /var/log/*
```

---

### Post by maddbaron on 2006-07-14
> **trent dillman said:**
> Looks to me like your hard drive is full, from df -h.

The fdisk -l is an L, not a one. The rest isn't working because you're probably not in recovery mode. I would just empty out your filesystem, mainly removing any music/pictures/etc from your home folder. Ubuntu shouldn't fill that much space unless you've installed a LOT of software, or there's some sort of bug that's writing a ton of info into /var/log/*.....

...which is something to check:

```
du -h /var/log/*
```


when I set up ubuntu I messed up b/c I have each section its own space like /home is /dev/hda6 with 4.5 gigs of that only 3.9 is free thats where I store pictures. music n movies I moved to windows part, i use windows as a big folder.  the / is /dev/hda7 and the only one out of space... the remaing /dev/hda's until 9(windows has 3 partitions hda 1,2,4 and linux has the remaining) are all free with space.

somehow the / folder got full of stuff...i dont even know what the /folder does. but can i empty it somehow? i will go back to recovery and start from scratch again but /home cant be the problem it by itself has 3.9 gigs free. but incase i do need to remove the pic files is their a way to reformat /dev/hda7 without touching anything else? i assume once reformated all the info there will be removed?

somehow dev/hda7 needs to be emptied.

i gave linux 20gigs of space dev/hda7 is full at 5.45gig's so i have about 14gig's free give or take 2 to 3 gigs apread out.

dev/hda7 is the prob it houses my temp folder so time to go into recovery again and figure this out....

---

### Post by maddbaron on 2006-07-14
ok I know what filled up my /tmp folder. I downloaded a film that was 1.2 gigs. whenever i tried to open with different players it didnt work except 4  vlc and mplayer and each time it said it was copying from my windows partition where it was housed to .kde/tmp  i remember the extension is there a way to delete that temp of it? or it is safe to just remove /?

---

### Post by maddbaron on 2006-07-14
> **trent dillman said:**
> log in to recovery mode

```
rm -r /tmp/*
shutdown -r now
```

ok, i left ubuntu alone for at least 12 hours. came back and redid this part over it worked but i had to remove thr /* at the end of /tmp.  it accepted the command. and then i entered the shutdown. and system rebooted. so far so good. then the partition in question, /dev/hda7 was checked as my root "/" on the screen and it said clean then stuff about blocks and check in 5 mounts. then system went to main page i tried logging in and was told 
"Your session only lasted less than 10 seconds, if you have no logged out yourself, this could mean there is some installation problem or that you may be out of diskspace. try logging in with one of the failsafe sessions to see if you can fix this problem."

then while that window was up i clicked view details 
everything started correctly until the mkdtemp: private socket dir: permission denied.

so now am i right to assume that after i enter the rm code i should enter a make temp directory code? and enter a code to allow permission? 

but also if i go into failsafe terminal can i apt-get a temp file cleaning program and run it within terminal?

I tried failsafe gnome but all i got was the auburn screen.

the problem it seems is the root partition. all its gig's are filled somehow. i ran the 

> du -h /var/log/*
code 
and i have a lot of logs taking up massive space.

mainly an old xorg log thats taking 56k, scroll keep logs taking up a total of 88k, sys log taking over 600k and user log.gz taking up 4mb's 3 times. and unattended upgrades taking up 4mb's

i see some conf logs that look important like the xorg and wdialconf but the rest are just space taking it seems.

is there a way to terminal or recovery mode remove all these logs? basically everything in the root file?

and when the system restarted it said check mount 5 more times. does that mean after 5 reboots it will clear itself out?

can anyone help me with this?

---

### Post by trent dillman on 2006-07-17
I would do the following:

First, make a new partition from one of the others. Not an expert on this, so I'd google for 'splitting ext3 partition'.

Then, I'd determine which part of my system needed it's own partition (probably /usr):

```
sudo du -h --max-depth=1 /
```

Then, copy your old folder to the new partition.
Now, boot into a live linux cd and move /usr to something like /usr_backup, then make an empty /usr directory. Edit /etc/fstab to mount your new partition to the empty /usr folder, then reboot into your system. If it boots right, you should be able to delete the /usr_backup.

---

