---
title: "[SOLVED] ABSOLUTE beginner KDE Gutsy Questions"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2007-12-20
Hey,

I'm pretty new to UNIX based OS's.

I'm running Kubuntu Gutsy on a pretty old machine since Windows was being messed up...

I have a few questions...which I'm sure are obvious as hell, but aren't to me..things that I have searched for, I usually search for stuff, but some stuff, as you know, doesn't go anywhere when it comes to searching.

A)  Whenever I try to modify some stuff that uses the Adept database, it gives me an error message saying the Adept database is already in use.  Well I can't find which process is using it, any help, reasoning?  I'm sure there's no task manager :P.

- NVM, the Adept update manager had a thing in the bottom right - no problem there.

B)  Okay, I'm not "completely"  new to linux based stuff, but I'm new to using it (yeah I know that makes no sense, but it is what it is).  Though one thing I don't understand is how the programs are setup.

Obviously on a PC the setup file installs programs and libraries into the "Program Files" which gets accessed whenever you run the program, on Macs they use a UNIX based system now (OS X) which runs everything as Apps...so on and so forth.

Linux programs seem to be able to be ran from ANYWHERE.  Now coming from a Windows system that's a CRAZY concept.  

I'm talking program commands such as Emacs (Java editor), try (program we use to upload files at school on the solaris machines..might be school exclusive), Adept-installer, so on and so forth - you can just type the name in terminal, regardless of where you are - not like Windows's Command prompt where you'd need to be in the folder.  What gives?  How are the program set up, program files stored, and how is that stuff accessed?  Any comparisons help me a lot in understanding stuff).

C)  I put in my favorite (and probably only) DVD, Pink Floyd's P.U.L.S.E album.  A friend of mine recommended two video programs on top of VLC (which I use for windows, but isn't the best for scrolling through movies, only watching one beginning to end), those programs were media player (totem), and mplayer.  Both encounter a problem when I try to play a DVD (automatically mounted).

"There is no plugin to handle this movie."

I also got a similar message when I went to play an .avi file (off my other hard disk) - I'm guessing I don't have the right codecs?  Anybody know where I can find codec packs or recommend one?  I'm looking for one with the most file types while consuming the least resources - obviously.

D)  I have an external Buffalo 750GB hard drive (2 375's) which I have lots of media, programs, etc. on.  I plugged it in (USB 1.0 interface...yes...1.0 b/c this computer's pretty old, I thought it had 2.0 ports, but windows recently couldn't detect them, so maybe I don't have them).  Anyways, it recognized the drives instantly, but they both show empty (0 bytes).  They're formatted in NTFS and it reads my other NTFS hard drive perfectly.  So it can definitely read NTFS, but it doesn't want to read these hard drives?  What gives?

PS:  I just checked with my USB Flash drive to see if it was a problem with the USB ports ,it reads my USB drive 100%.  Any help is appreciated here, I can't afford to format my main external.

E)  (MOST IMPORTANT):
As I just realized when I opened some pictures of a mustang (I'm a HUGE car guy) that are about 2xxx x xxxx resolution (large), I am in major lack of video drivers :P.

I have an ATI Radeon Rage 9550 (yeah, I know, so sue me) - I downloaded a driver from ATI's site - called "ati-driver-installer-7-11-x86.x86_64.run" - Three important things to note on this file:  A)  According to the basic UNIX **** I head to learn for Java programming I (software engineering major, just switched) is the permissions on it I just happened to notice (looked at the bottom) are -rw--r--r - which confuses me because if I remember correctly there should be an E or an X (execute) in that first blank - I'm the only user, the administrator, etc.  Is there any way to set the GUI interface to sudo administrator?  Or is the only way to send terminal to it and "sudo filename" and B)  What the heck do I do with this stupid thing?  I clicked it and it gave me some error message about overwriting something and I was like "O.O" and closed the window.  C)  Why's it say x86 and _64, that bothers me, I don't have a 64 bit processor but that seems to be the driver for it...?? ?? 

So yeah, any help on any (or all) of these problems would be appreciated.

Please, I'm not very linux forum savvy, so if you're gonna use acronyms that are very UNIX forum specific, explain if you catch it.  The only other thing I ask is that you don't start crap with me for "not knowing" this stuff or "not googling" stuff, not researching, so on and so forth.  I'm 100% wet behind the ears newb when it comes to UNIX based equipment and it seems the majority of Linux users A)  Hate newbs more than they hate life, and B)  Think they never had to learn it, they were simply willed the knowledge by God and that was that.

Any and all help = thanks...

THANKS!!!

(PS:  I realize there's like 450,000 questions here)

---

### Post by lintoon on 2007-12-20
Maybe you should try googling for the answer because you really should know this.  Only joking :)

Check out EasyUbuntu for the easy way to install any missing codecs etc.

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

The x86 and _64 on your ati drivers would suggest it is for a 64 bit system so I would try to find alternative drivers.  There seems to be a lot of ati posts and from what I've seen they can be a bit of a pain.

Your error "Adept database is already in use".  Are you sure there are no other package management applications running.  Eg is it updating.  Sorry, had to ask.  

Hopefully someone more linux savvy can help explain the linux filesystem better to you.

---

### Post by PeterJS on 2007-12-20
> **Syndacate said:**
> Hey,
B)  Okay, I'm not "completely"  new to linux based stuff, but I'm new to using it (yeah I know that makes no sense, but it is what it is).  Though one thing I don't understand is how the programs are setup.

Obviously on a PC the setup file installs programs and libraries into the "Program Files" which gets accessed whenever you run the program, on Macs they use a UNIX based system now (OS X) which runs everything as Apps...so on and so forth.

Linux programs seem to be able to be ran from ANYWHERE.  Now coming from a Windows system that's a CRAZY concept.  

I'm talking program commands such as Emacs (Java editor), try (program we use to upload files at school on the solaris machines..might be school exclusive), Adept-installer, so on and so forth - you can just type the name in terminal, regardless of where you are - not like Windows's Command prompt where you'd need to be in the folder.  What gives?  How are the program set up, program files stored, and how is that stuff accessed?  Any comparisons help me a lot in understanding stuff).

This is on of the best explainations of the file system layout I've seen:
[http://en.wikipedia.org/wiki//etc#Directory_structure](http://en.wikipedia.org/wiki//etc#Directory_structure)

Also Emacs is more than just a text editor, it's an operating system unto itself, and subject of a epic flame war that borders on religious fanaticism. Google for emacs vs vi. As an aside, at the risk of bringing the war here, I'd suggest looking at kate for programming it, it does syntax highlighting, code folding, and some basic auto completion.

> 
C)  I put in my favorite (and probably only) DVD, Pink Floyd's P.U.L.S.E album.  A friend of mine recommended two video programs on top of VLC (which I use for windows, but isn't the best for scrolling through movies, only watching one beginning to end), those programs were media player (totem), and mplayer.  Both encounter a problem when I try to play a DVD (automatically mounted).

"There is no plugin to handle this movie."

I also got a similar message when I went to play an .avi file (off my other hard disk) - I'm guessing I don't have the right codecs?  Anybody know where I can find codec packs or recommend one?  I'm looking for one with the most file types while consuming the least resources - obviously.
There are some legal issues with DVDs and linux, congress got sloppy with their wording, there really is no legal way to play DVDs under linux. But everybody looks the other ways, as who in their right mind is going to take this to court.

As for media players/codecs, just forgo the whole mess and use VLC. It plays everything under the sun. The only short coming I've heard of is that is doesn't handle separate subtitle files as well as mplayer, but that doesn't look like an issue for you.

> 
E)  (MOST IMPORTANT):
<ATI Drivers>
Firstly, I'm sorry, the ATI drivers kinda suck. The easiest way to install any  (extra) driver is with the restricted drivers manager. Well I just looked and apparently there's no K menu entry for the restricted driver manager, so pop open a terminal and enter:
```

sudo restricted-manager-kde

```Good luck, I'll be around if you need me.

---

### Post by Syndacate on 2007-12-21
> **PeterJS said:**
> This is on of the best explainations of the file system layout I've seen:
[http://en.wikipedia.org/wiki//etc#Directory_structure](http://en.wikipedia.org/wiki//etc#Directory_structure)

Also Emacs is more than just a text editor, it's an operating system unto itself, and subject of a epic flame war that borders on religious fanaticism. Google for emacs vs vi. As an aside, at the risk of bringing the war here, I'd suggest looking at kate for programming it, it does syntax highlighting, code folding, and some basic auto completion.

Cool, I'll read that link after I post this.

Haha about the whole "war" on what emacs is, I thought it was just a program, but what about other stuff, any program you want, like alsamixer or apt-get, or ANY other callouts can be made from anywhere, that's all I was saying that.  Like you can type glxgears anywhere and it'll bring it up, doesn't matter if you're at the root or the desktop.

PS:  Google emacs vs vi?  They both suck, eclipse ftw!

> **PeterJS said:**
> There are some legal issues with DVDs and linux, congress got sloppy with their wording, there really is no legal way to play DVDs under linux. But everybody looks the other ways, as who in their right mind is going to take this to court.  

Fixed the DVD problem - VLC = Win...like it does on Windows...

All theoretically of course...because I would never do anything to infringe on our needed and understandable copyright legal ********.

> **PeterJS said:**
> As for media players/codecs, just forgo the whole mess and use VLC. It plays everything under the sun. The only short coming I've heard of is that is doesn't handle separate subtitle files as well as mplayer, but that doesn't look like an issue for you.

This might sound weird, but I'm looking for something that's "LIKE" Windows Media Player for Windows.  Loads fast, tracks fast, scrolls fast.  VLC takes some time to load, then the volume doesn't stay, then if you had a diff video open It like, cancels that **** out and makes a new instance of the window...and forget clicking on a scroll bar to get to a different part of the movie, then it just goes ape ****.  It's good for watching a whole movie, beginning to end, not much else.  I need something that plays on the fly like Windows Media Player does, that loads fast, can track fast, and is versatile.

> **PeterJS said:**
> Firstly, I'm sorry, the ATI drivers kinda suck. The easiest way to install any  (extra) driver is with the restricted drivers manager. Well I just looked and apparently there's no K menu entry for the restricted driver manager, so pop open a terminal and enter:
```

sudo restricted-manager-kde

```Good luck, I'll be around if you need me.

I got the drivers working using the code you listed - thanks.  glxgears works !!

Now I find myself presented with a new problem:
I plugged in my External Hard disk, and they show up, but it shows 2 hard drives with 0 data and at the bottom of the window an error message saying saying:  ```
hal-storage-removable-mount-options refused uid 1000
```

Any help here?  I thought it couldn't read NTFS or something but I plugged in my flash drive and it recognized it 100%.

Any idea what gives?

The hard drives btw is a buffalo encasement with dual 375GB hard drives.  I can't really afford to reformat them.

Thanks for all the other info by the way, I got most of the kinks worked out.

---

### Post by PeterJS on 2007-12-21
> **Syndacate said:**
> 

This might sound weird, but I'm looking for something that's "LIKE" Windows Media Player for Windows.


Hmm, you might look at installing totem, it's the default movie player for gnome. It loaded up pretty quick for me, and it looks superficially like wmp. It's got a play list bar over on the right side. Not the most sound recommendation I've made, but I'm an avid VLC user and never looked at other players.

> 
Now I find myself presented with a new problem:
I plugged in my External Hard disk, and they show up, but it shows 2 hard drives with 0 data and at the bottom of the window an error message saying saying:  ```
hal-storage-removable-mount-options refused uid 1000
```Any help here?  I thought it couldn't read NTFS or something but I plugged in my flash drive and it recognized it 100%.
That hasn't been the case for at least a year, heck these days, NTFS writing is even pretty reliable. Take a look at KMenu > System > NTFS Config Tool.

> 
Any idea what gives?
Yes and no. I got the exact same error, I posted a thread about it , got no replies. Gave up and resigned to the fact that KDE and HAL hate each other, and "solved" the problem by using the XFCE file manager, thunar, to manage mounting and unmounting drives that didn't come up automatically.

---

### Post by Syndacate on 2007-12-21
> **PeterJS said:**
> Hmm, you might look at installing totem, it's the default movie player for gnome. It loaded up pretty quick for me, and it looks superficially like wmp. It's got a play list bar over on the right side. Not the most sound recommendation I've made, but I'm an avid VLC user and never looked at other players.

K, I'll look around, that part's not completely important to me, just a convenience thing.

> **PeterJS said:**
> That hasn't been the case for at least a year, heck these days, NTFS writing is even pretty reliable. Take a look at KMenu > System > NTFS Config Tool.

Oh, well this is pretty bad then :(.

> **PeterJS said:**
> Yes and no. I got the exact same error, I posted a thread about it , got no replies. Gave up and resigned to the fact that KDE and HAL hate each other, and "solved" the problem by using the XFCE file manager, thunar, to manage mounting and unmounting drives that didn't come up automatically.

One word:  Fu8k.

I have to go back to Windows if I can't get that external drive to function properly.

Now my priority just switched from getting my GFX drivers to work (fixed) to getting this to read that external USB hard drive.

I NEED to get it to read that hard drive or it's back to a long day of programs not responding and blue screen errors with windows.

NTFS Config Tool did Nothing - didn't even open.
Thundar failed to mount either drive with the same error.

After all that about how good and new linux is on the gutsy distro it can't even read an external hard drive?

Think priorities are mis-placed or something :(

---

### Post by PeterJS on 2007-12-21
> **Syndacate said:**
> 
Thundar failed to mount either drive with the same error.

Well, it helps if I actually read before replying.

EDIT:

Ok, this isn't a no go situation. It's just going to take a bit of configuration set up to get working. There's a configuration file name /etc/fstab (the File System TABle), which contains a listing of all the preconfigured hard drives the system knows about, the purpose of HAL is to automatically set up the configuration for anything that isn't in fstab. So if HAL isn't working, then we should put the disks in fstab so you won't need to use HAL to manage that disk. In fstab disks are identified by their UUID, to find the UUID of the partitions in question plug in the external disk and run:
```

blkid /dev/sd*

```Once you have the UUID open up kate with elevated privilages:
```

sudo kate /etc/fstab

```Down at the bottom add a line that looks like:
```

UUID=F4F447C2F4478638 /media/sda1 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8 0 1

```Replace the UUID with the one for your drive and change the mount point (the "/media/sda1" part) to where you want the drive to show up on your system.

Once that is done, after plugging in the drive you can run mount /some/location to mount it, or it should work under thunar then.

---

### Post by Syndacate on 2007-12-21
> **PeterJS said:**
> Well, it helps if I actually read before replying.

:(

I refuse to believe there's no way for kubuntu to recognize this external hard drive.

---

### Post by Syndacate on 2007-12-21
Awww, c'mon, bump, anybody??

---

### Post by Syndacate on 2007-12-21
[quote=PeterJS]Ok, this isn't a no go situation. It's just going to take a bit of configuration set up to get working. There's a configuration file name /etc/fstab (the File System TABle), which contains a listing of all the preconfigured hard drives the system knows about, the purpose of HAL is to automatically set up the configuration for anything that isn't in fstab. So if HAL isn't working, then we should put the disks in fstab so you won't need to use HAL to manage that disk. In fstab disks are identified by their UUID, to find the UUID of the partitions in question plug in the external disk and run:
```
blkid /dev/sd*
```

Wow, I'm sorry, I didn't realize you edited your post :P.

Once you have the UUID open up kate with elevated privilages:

When I try to do that, I get this error message:
/etc$ sudo kate fstab
Error: "/var/tmp/kdecache-syndacate" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-syndacate" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-syndacate" is owned by uid 1000 instead of uid 0

It opens though but won't save.  It gives me some crap about me not having the admin privileges to do that (I think I had to type it w/o sudo the first time to get it to work).  It opened fine in KEdit though, and saved fine.

[quote=PeterJS]```
sudo kate /etc/fstab
```

Down at the bottom add a line that looks like:

```
UUID=F4F447C2F4478638 /media/sda1 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8 0 1
```

Replace the UUID with the one for your drive and change the mount point (the "/media/sda1" part) to where you want the drive to show up on your system.

Once that is done, after plugging in the drive you can run mount /some/location to mount it, or it should work under thunar then.[/quote]

I did this, and no-go, neither drive will still mount in thundar.

This is what my fstab file looks like (what I added)

# /dev/sdb5
UUID=C18E2B918E2A0C6 /media/sdb5 ntfs-3g 	defaults,nonauto,user,locale=en_US.UTF-8 0 
# /dev/sdc5
UUID=E45C77555C77220A /media/sdc5	ntfs-3g	defaults,nonauto,user,locale=en_US.UTF-8 0 1

Upon opening KEdit it gave me the following error in the terminal, but opened anyways:
Error: "/tmp/kde-syndacate" is owned by uid 1000 instead of uid 0

It's editing it and saving fine, (or seemed to) despite it's lil error there, but what's up with this UID 1000??  How do I change mine, I'm the only one who uses this computer and such...

In any event it doesn't work, I can't mount it with Thundar

---

### Post by PeterJS on 2007-12-21
UID 1000, is the user id for your system. That's just where the numbering system starts. 0 is root, and 1-999 are reserved for system accounts that are needed for the system to function and/or good security practices. You really don't want to change your UID or use a lower one, it would firstly break security very badly, and even a few applications.

What happens if you plug the drive in and enter:
```

mount /media/sdc5/

```

---

### Post by Syndacate on 2007-12-21
Well that problem is sorta fixed...but as with most things, a new problem comes up as soon as one goes away.

I booted Windows and unmounted the drive in windows, and then restarted kubuntu, and it mounted under Thundar (still wouldn't read plug and play), now some new **** happens, it's only reading ONE OF THE HARD DRIVES (it's a dual drive enclosure with 2 375's).

Before it was reading both fine, but it couldn't access them.  Now I unmounted them and I can only access one (because that's all that it's reading) with Thundar, and I get these error messages when I try to do what you stated through terminal:

syndacate@syndacate-desktop:~$ mount /media/sdb5
[mntent]: warning: no final newline at the end of /etc/fstab
Failed to access '/dev/disk/by-uuid/C18E2B918E2A0C6': No such file or directory
syndacate@syndacate-desktop:~$ mount /media sdc5
mount: only root can do that

God, what the hell???

:(

Any help is thx...

PS:  I booted back into windows and both drives still show up...iono what the deal is...

---

### Post by hyper_ch on 2007-12-21
> **Syndacate said:**
> Hey,
Linux programs seem to be able to be ran from ANYWHERE.  Now coming from a Windows system that's a CRAZY concept.  
As it's already pointed out you sort of have a unified hierarchie about where goes what part and piece of a program to. This allows to have PATH environment to most binaries (as they reside mostly in the same couple of directories). By having /usr/bin et al. in your path environment, whenever you want to run a binary from the terminal, it will look upon those paths and probably find it.
In Windows you sort of have c:\programs\PROGRAM1, c:\programs\PROGRAM2, c:\programs\PROGRAM3, ... --> you'd have to add each program path to your path environment in windows.

---

### Post by Syndacate on 2007-12-21
There's that crap with the harddrives, then there's the:

"Sound won't work after reboot" problem.

Just doesn't work, no go.

Then mysteriously it just turns on.

Is there any command to like "re-activate" the sound drivers or anything in terminal that I can put in whenever it tries to pull this crap?

---

### Post by Syndacate on 2007-12-21
There's that crap with the harddrives, then there's the:

"Sound won't work after reboot" problem.

Just doesn't work, no go.

Then you switch jacks (from onboard audio to sound card) and it works.

Though if it's in the sound card it won't work, you have to switch it to onboard (mb) audio.

Why??

Why does it not work in whatever jack it starts off in?  I'm assuming it can't decide which sound card to use.  If that's the case how do I "tell it?"

---

### Post by The Cog on 2007-12-21
> **Syndacate said:**
> 
syndacate@syndacate-desktop:~$ mount /media/sdb5
[mntent]: warning: no final newline at the end of /etc/fstab
Failed to access '/dev/disk/by-uuid/C18E2B918E2A0C6': No such file or directory
syndacate@syndacate-desktop:~$ mount /media sdc5
mount: only root can do that

God, what the hell???

1)
I think you probably mis-typed the ID of the second disk. You can check by running the command **blkid** or **ls /dev/disk/by-uuid** and comparing with the output from **cat /etc/fstab**.

2) 
The warning is that you didn't hit Enter at the end of the last line in /etc/fstab. This is not critical, just a nicety.

3)
To allow all users to mount the disks (by default only root is allowed to do it), find this field in /etc/fstab:
**defaults,noauto,user,locale=en_US.UTF-8**
and add the option user (comma separated, no spaces), like this:
**defaults,user,noauto,user,locale=en_US.UTF-8**
Also, the word **defaults** is only a placeholder for when no other options are not specified (to keep the right number of columns) and could be dropped if you prefer.

4)
Re: Launching programs from anywhere. 
This is normal. When you type a command, the command interpreter searches for an executable of that name in several places. You can see the list of places by typing the command:
**echo $PATH**
DOS and Windows work the same except for these differences I can think of:
 - The command is **echo %PATH%**
 - Windows also searches the current directory "." without is being in the list.
 - Windows uses ";" and "\" rather than ":" and "/".
In both systems you can launch a program that's in a place not listed on the search path by giving the full pathname to the executable, e.g. C:\python24\python.exe.

5) In Linux, I think the executable file that launches a program is placed in /usr/bin (or /bin if its a system executable), and the rest of the program files go in /usr/share/ or /usr/lib/.

6)
There is probably a copnfiguration setting somewhere to tell you whcih sound card to use. In Gnome, you right-click the speaker icon and choose Preferences. I don't know where it is in KDE, but it must be there somewhere.

---

### Post by Syndacate on 2007-12-21
> **The Cog said:**
> 1)
I think you probably mis-typed the ID of the second disk. You can check by running the command **blkid** or **ls /dev/disk/by-uuid** and comparing with the output from **cat /etc/fstab**.

2) 
The warning is that you didn't hit Enter at the end of the last line in /etc/fstab. This is not critical, just a nicety.

3)
To allow all users to mount the disks (by default only root is allowed to do it), find this field in /etc/fstab:
**defaults,noauto,user,locale=en_US.UTF-8**
and add the option user (comma separated, no spaces), like this:
**defaults,user,noauto,user,locale=en_US.UTF-8**
Also, the word **defaults** is only a placeholder for when no other options are not specified (to keep the right number of columns) and could be dropped if you prefer.

4)
Re: Launching programs from anywhere. 
This is normal. When you type a command, the command interpreter searches for an executable of that name in several places. You can see the list of places by typing the command:
**echo $PATH**
DOS and Windows work the same except for these differences I can think of:
 - The command is **echo %PATH%**
 - Windows also searches the current directory "." without is being in the list.
 - Windows uses ";" and "\" rather than ":" and "/".
In both systems you can launch a program that's in a place not listed on the search path by giving the full pathname to the executable, e.g. C:\python24\python.exe.

5) In Linux, I think the executable file that launches a program is placed in /usr/bin (or /bin if its a system executable), and the rest of the program files go in /usr/share/ or /usr/lib/.

6)
There is probably a copnfiguration setting somewhere to tell you whcih sound card to use. In Gnome, you right-click the speaker icon and choose Preferences. I don't know where it is in KDE, but it must be there somewhere.

**1), 3)**Alright, I looked at the lines in fstab, and they were incorrect (I had nonauto instead of noauto, and there was a 0 after the 8 on each of them..possibly a few more things, I straightened it out so it's right).

In any event, I unplugged it, then plugged it back in, they BOTH show up now, but still, only ONE is mountable, neither mounts automatically (whatever) and Thundar can't mount the second one, and the reason gives this error:

```
fuse:  failed to access mountpoint /media/sdc5:  No such file or directory FUSE mount point creation failed Unmounting /dev/sdc5 (HD-WIU2)
```

Now taking that error into account the "no such file or directory" I double checked the UUID in that code.  The UUID in /etc/fstab does match the UUID given in the command **blkid**.

After I checked that I tried changing the /media/ to /dev/ in the fstab - no go there either, same thing happened, mounted the one drive fine, couldn't mount the second one.  I changed it back to /media/.  The hard drive name is right too (sdb5 and sdc5, for both hard drives matches each respective hard drive in **blkid**.  

Here's my last 2 lines (plus the comments) of the bottom of **fstab** vs the report on **blkid**.  I figure it's gotta be a discrepancy here:

blkid:
```
/dev/sdb5: UUID="C18E2B918E2A0C6" LABEL="HD-WIU3" TYPE="ntfs"
/dev/sdc5: UUID="E45C77555C77220A" LABEL="HD-WIU2" TYPE="ntfs
```

fstab:
```
# /dev/sdb5
UUID=C18E2B918E2A0C6 /media/sdb5 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8
# /dev/sdc5
UUID=E45C77555C77220A /media/sdc5 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8
```

I see that defaults is a place holder to keep the columns, makes sense, but since I don't have/know anything else to put there, I might as well leave it there.

**2)**  What do you mean I didn't hit enter?  I had to hit enter to execute the command...?  What should I have typed?

**4), 5)**  Ah, I C, I didn't think the hierarchy tree of what he showed me really had anything to do with what I was inquiring about.  So basically all the executables are in a sub folder out of /bin/ and that's where it searches for when you just type the command without a file name like that?

Windows will do that too off of start >> run if the program exists in C:\windows - I do that a lot (create shortcuts there and name them efficiently) so I just hit "windows key + R" >> "gaim" and pidgin starts up - so on and so forth for most of my programs, or "word" - etc. - though you can't just name those out from anywhere in the command prompt, you have to be in the directory, or specify the path to the directory, not like this where you can be in the subbest sub folder and call it out without a path and bam O.O.

So my understanding of what you guys have told me is that most of the files being executed are in the /bin/ directory (or some sub folder) and when you type a name like that it simply searches those?  It's funny, I never realized until I started digging around where OS X came from - I knew it was UNIX based, I didn't know it was the same exact thing but dumbed down - everything is verrrrrrrrrry similar.  Though I guess since UNIX systems are free distros and very stable they were a smart move on Mac's part...**** mac. - Anyways.

**6)**  Yeah, in KDE you can control which sound card the mixer is controlling - though that's not "setting" one.  I was just making a hypothesis as per the reasoning of the problem, I don't know why it's happening.  Though it switches, it's on my SB Live! right now, if I was to restart I would have no sound and I'd have to plug it into my mobo sound card.  Very weird problem, though like I said, my hypothesis (and only that) is that it has something to do with the fact there's two and both are reading fine, which begs the question: "Is one set as default?" - Probably not, but minor problem none-the-less.  There doesn't seem to be a device manager like Windows where I could just "disable" the onboard mobo sound (or SB Live!).

Wow, thanks a lot you guys, you really have no idea how boned I would be without your help.  One of the error messages Kubuntu was telling me before was that a possibly reason for not being able to mount was that it wasn't unmounted properly last time, and that if it came from windows I should go into windows and unmount it - so I did, that's how I got it to recognize one.  Though in my short time in windows was painful - I remembered that whenever I restart out of windows I lose USB support, so I can't select an OS (windows or kubuntu) to boot without a PS2 keyboard if I boot from windows, or I have to hardboot, and then it'll hang when it says "starting windows" if my external hard drive is plugged in.  Then when I tried opening the device manager to unmount it from windows, explorer crashed!  So I ended explorer, and tried to start explorer back up again (new process >> explorer.exe) and rundll32.exe (dll runner) ******* crashed too, which had the library files for the unmounting program, so I couldn't unmount, and it took like 10 minutes to straighten itself out.  So I just sat down on my bed and watched it have a ****-fit and I simply said to myself: "And this is why I'm using a member of the UNIX family..." - Then I'm not gonna even bother saying that there's barely nothing over of a firewall/anti-virus/browser/FTP/HTTP server on windows over there...

Yeah, off topic, but yeah.  Thanks a lot you guys,  you guys are reallllly helping me out with this stuff.  You'd think it being so popular there'd be a lot of stuff to google but the two problems I run into are A)  Everybody uses Gnome, nobody fu8king uses KDE, and the ways to do stuff through GUI are different, and B)  A lot of stuff is kinda hard to explain to google then if you do find something it's usually written in ambiguous linux terms that don't tell ya much :P.

So thanks guys, you guys are really helpin me along with this.  I just gotta get these hard disks working, I don't care if I have to mount them each time with Thundar, small price to pay for the data needing constant access on these disks.

PS:  There any way to make them NOT show up on my desktop when I plug them in?  It's good and all (nice shortcut) for USB, but for harddrives I just don't want them there, I mean it's all open source, there's gotta be a way to "not show on desktop" - but that's just minor tuning ****, I don't like to keep stuff on my desktop except main folders.

---

### Post by Syndacate on 2007-12-21
> **hyper_ch said:**
> As it's already pointed out you sort of have a unified hierarchie about where goes what part and piece of a program to. This allows to have PATH environment to most binaries (as they reside mostly in the same couple of directories). By having /usr/bin et al. in your path environment, whenever you want to run a binary from the terminal, it will look upon those paths and probably find it.
In Windows you sort of have c:\programs\PROGRAM1, c:\programs\PROGRAM2, c:\programs\PROGRAM3, ... --> you'd have to add each program path to your path environment in windows.

Yeah, I mis-understood it.

When I first looked at the link provided I thought he mis-understood my question and that that wasn't what I was inquiring about.

I get what you guys are saying now, so it is sorta the same...sorta - basically what I'm getting from it is that when you type a name on the fly like that such as kedit or emacs (okay, bad example), or kate, or anything like that it searches the /bin/ or /user/bin directories (and some sub-folders) for a name match?  So it's quite similar to windows when you hit start >> run searching in C:\Windows? - in DOS it's different from the fact that you have to either A)  Be in the directory, B)  Tell it to where to find the file (navigate/run), or C)  Have a shortcut in C:\Windows.

Thank you.

---

### Post by Syndacate on 2007-12-22
Bump, anybody?? :(

---

### Post by Syndacate on 2007-12-22
C'mon, Bump, somebody's gotta know.... :(

---

### Post by The Cog on 2007-12-23
> **Syndacate said:**
> C'mon, Bump, somebody's gotta know....:(

Sorry for the delay - I was vising my Mum for the weekend.

1), 3), fstab and mount points:
Does the directory /media/sdc5 actually exist? mount will not create a directory to mount the disk on - it will only mount to an already existing directory. An interesting point is that doing this makes the original contents of the directory invisible until the disk is unmounted again. By convention, no files are kept in the mount point directories - it makes for too much confusion.

I think that with KDE you will have to live with mounting the disks by hand. Make a launcher icon on the desktop to do it if you like. Gnome will mount USB disks automatically, and make the desktop icons appear - maybe KDE doesn't do this (maybe KDE4 will?). I normally use Gnome at the moment.

In Gnome, the icons only appear on the desktop if the disks are mounted in /media. The other conventional place to mount disks is under /mnt, e.g. /mnt/sdc5, and gnome doesn't make desktop icons for those. Maybe KDE is similar? 

2)
The fstab file. Can you move the cursor down to a blank line below the last line of text? If not, then there is no LineFeed character at the end of the last line. This is what the warning is about - theoretically, the file could have lost its end and there is no way to know. a LF at the end of the line removes any doubt. But it's not really important.

4), 5)
Dos/Windows is the same - its not just a unix thing. The command 
echo %PATH% in Windows shows where Windows will search. I forgot to add that when you issue a command in Windows, it will look in the path for files matching that command and either .COM, .EXE or .BAT extensions. So when you type the command:
**notepad myfile.txt**
you know it will look for NOTEPAD.EXE, NOTEPAD.COM, NOTEPAD.BAT in several places. Windows is perhaps unique in requiring that executables must have particular endings to their names.

If you were to add the directory where gaim.exe lives to the path, then you would then be able to launch it just by entering **gaim**. Or put a file gaim.bat in a directory that is in the path, and make the bat file do:
**/wherever gaim really lives/gaim.exe**



Yup, I use Gnome mostly, so I don't know where that setting for the choice of sound card is on KDE. I'll have a look after posting this. But Gnome does have such a setting, so I would expect KDE to have it too, somewhere. See attached screenshot.

P.S. I have heard that some people like to disable the on-board sound card in their BIOS settings, which would probably solve your problem there.

UPDATE:
I can't find an equivalent sound card setting in KDE. There is a dialog tha tallows choosing the sound system, but it only offers ALSA or OSS or other software drivers, it doesn't allow you to select the hardware sound card. Perhaps KDE4 will have the option. I intend to give KDE4 a good try-out when Kubuntu 8.04 is released.

---

### Post by Syndacate on 2007-12-23
> **The Cog said:**
> Sorry for the delay - I was vising my Mum for the weekend.

1), 3), fstab and mount points:
Does the directory /media/sdc5 actually exist? mount will not create a directory to mount the disk on - it will only mount to an already existing directory. An interesting point is that doing this makes the original contents of the directory invisible until the disk is unmounted again. By convention, no files are kept in the mount point directories - it makes for too much confusion.

I think that with KDE you will have to live with mounting the disks by hand. Make a launcher icon on the desktop to do it if you like. Gnome will mount USB disks automatically, and make the desktop icons appear - maybe KDE doesn't do this (maybe KDE4 will?). I normally use Gnome at the moment.

In Gnome, the icons only appear on the desktop if the disks are mounted in /media. The other conventional place to mount disks is under /mnt, e.g. /mnt/sdc5, and gnome doesn't make desktop icons for those. Maybe KDE is similar? 

2)
The fstab file. Can you move the cursor down to a blank line below the last line of text? If not, then there is no LineFeed character at the end of the last line. This is what the warning is about - theoretically, the file could have lost its end and there is no way to know. a LF at the end of the line removes any doubt. But it's not really important.

4), 5)
Dos/Windows is the same - its not just a unix thing. The command 
echo %PATH% in Windows shows where Windows will search. I forgot to add that when you issue a command in Windows, it will look in the path for files matching that command and either .COM, .EXE or .BAT extensions. So when you type the command:
**notepad myfile.txt**
you know it will look for NOTEPAD.EXE, NOTEPAD.COM, NOTEPAD.BAT in several places. Windows is perhaps unique in requiring that executables must have particular endings to their names.

If you were to add the directory where gaim.exe lives to the path, then you would then be able to launch it just by entering **gaim**. Or put a file gaim.bat in a directory that is in the path, and make the bat file do:
**/wherever gaim really lives/gaim.exe**



Yup, I use Gnome mostly, so I don't know where that setting for the choice of sound card is on KDE. I'll have a look after posting this. But Gnome does have such a setting, so I would expect KDE to have it too, somewhere. See attached screenshot.

P.S. I have heard that some people like to disable the on-board sound card in their BIOS settings, which would probably solve your problem there.

Yes, the path does exist:  system:/media/sdc5/

It recognizes my USB flashdrive fine, automatically mounted and everything.  Though that's not where I have the problem, the problem is with this hard drive.  I have no problem mounting everything manually, I just want it to **be able to mount**, which at the current time, is not possible.  

It makes the icons in the same place (and on the desktop), /media/sdc5 would be the path, clickable but not readable until you mount it - in which case only one is mountable (using Thundar).

I added a line at the bottom awhile ago, and stopped getting that error message.

In windows, it's easier just to create a shortcut to the original executable and put it in the C:\Windows folder, then just rename it what you want the command to be (ie.  I type "windows key + R" >> "gaim" - and that will execute the shortcut which will in turn execute the executable.  Though I understand what you're saying, thanks for the explanation on that.

Yeah, I have absolutely no problem mounting the drives each time through Thundar, but the problem is one of the hard drives is NOT mounting.  One is ALWAYS mounting, with Thundar (not if you right click and press mount, then it refuses), the other one gives the following error when I try and mount it using Thundar, PS:  All flash drives log up and mount up fine:
```
Details:  fuse: failed to access mountpoint /media/sdc5: No such file or directory FUSE mount point creation failed Unmountin g/dev/sdc5 (HD-WIU2
```

It doesn't make any sense, the code from "blkid"
```
/dev/sda1: UUID="8488FCAA88FC9BBC" TYPE="ntfs"
/dev/sda2: UUID="b834416b-750c-4981-93bb-95b9f2931908" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda3: TYPE="swap" UUID="2dd4d720-d740-4d7c-b193-b39d1b1d0aac"
/dev/sdb5: UUID="C18E2B918E2A0C6" LABEL="HD-WIU3" TYPE="ntfs"
/dev/sdc5: UUID="E45C77555C77220A" LABEL="HD-WIU2" TYPE="ntfs"
```

And from "cat /etc/fstab/"
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b834416b-750c-4981-93bb-95b9f2931908 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8488FCAA88FC9BBC /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=2dd4d720-d740-4d7c-b193-b39d1b1d0aac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# /dev/sdb5
UUID=C18E2B918E2A0C6 /media/sdb5 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8
# /dev/sdc5
UUID=E45C77555C77220A /media/sdc5 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8
```

As you can see they're identical, it doesn't make any sense.

---

### Post by The Cog on 2007-12-23
I wonder if the mount points are different somehow. Can you make sure that both disks are unmounted, and then post the output from this command:
**ls -l /media**
and we can see if the permissions are different somehow. That's all I can think of.

---

### Post by Syndacate on 2007-12-24
> **The Cog said:**
> I wonder if the mount points are different somehow. Can you make sure that both disks are unmounted, and then post the output from this command:
**ls -l /media**
and we can see if the permissions are different somehow. That's all I can think of.

They seem to be all in order, full permission on each one...

```

lrwxrwxrwx 1 root       root          6 2007-12-20 08:24 cdrom -> cdrom0
dr-xr-xr-x 4 4294967295 4294967295  136 2006-05-05 04:30 cdrom0
lrwxrwxrwx 1 root       root          7 2007-12-20 08:24 floppy -> floppy0
drwxr-xr-x 2 root       root       4096 2007-12-20 08:24 floppy0
drwxrwx--- 1 root       plugdev    8192 2007-12-21 02:54 sda1

```

Though I don't know what good that does, when they're both unmounted neither will show up... ?

---

### Post by VinceJohn on 2008-02-18
I got the same error sticking in my USB harddrive:

hal storage removable mount all options refused uid 1000

This does not happen with a FAT disk, though. 

Was this problem ever resolved...?

---

### Post by candtalan on 2008-02-18
I am a regular user of Kubuntu, although I do not know enough to help much  I  think.
The file fstab is pretty important for mounting easily, if at all, afaik. I noticed that earlier there was a return newline missing at the end of the fstab at that stage. It was mentioned later, and was said to be not too important. I wanted to say that it would be worth making sure that it does exist now, just in case it is preventing the last line of fstab from being recognised. Whatever the significance of that return newline, iirc it was included in the fstab information such as man fstab (use a terminal) when I originally looked.

While I think most users do use ubuntu, I put kubuntu onto all my machines, even old slow ones, it has a lot of conveniences which I like. However, I often also install ubuntu-desktop package (using adept, say) and I can choose which session I want at login time. There are some advantages with having ubuntu available too.

hth

---

### Post by Syndacate on 2008-02-20
> **VinceJohn said:**
> I got the same error sticking in my USB harddrive:

hal storage removable mount all options refused uid 1000

This does not happen with a FAT disk, though. 

Was this problem ever resolved...?

It was, i don't recall how, exactly.  It's not even right, that's for sure.

They're named wrong, one's named sdc5 and the other HD-WIU3 - go figure.

Since they're working at the moment I haven't tried messing with the fstab file to try to make them work properly, though I think the fact that it was windows mounted had something to do with it - I'm pretty sure I booted windows and "safely removed" each one and then it worked (well it read both of them, previous it only read one out of the two (1 box, 1 cable, 2 drives in that box)).

---

