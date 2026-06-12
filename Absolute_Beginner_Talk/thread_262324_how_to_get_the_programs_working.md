---
title: "how to get the programs working ?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by GoneWithTheWind on 2006-09-21
There must be a lot of people like me on here, looking for very simple and easy ways to get Ubuntu up and running.  I've succeeded with installation, and am now trying to get the programs to work.  Everything I see keeps saying how easy it is to get the programs working (some every say they already are), and then go on to list web pages full of things to type or paste into the terminal to get this and that things that I need -- translation: I'm totally lost.

What I see a lot of on the various forums is someone asking a question like, "how do I turn on the computer" and the answers are:  "Have you read all the FAQ yet?", "Read the guildelines!", "Try the search feature", "If you don't know that, you're not ready to turn on the computer" etc etc etc, which I'm sure drive most people away after a few hours.  Certainly it would be easier for someone who has no clue at all if the answer was simply something like, "See that big button on the front?  Press that".  I seriously think that even getting Ubuntu installed puts me way ahead of most people who've tried unsuccessfully to use Linux.  A friend of mine who's been a computer tech for the last 20 years, has downloaded Linux several times and always gave up because she never could figure out how to use it.

Yesterday I went to YouTube with Ubuntu/Firefox.  I'd already downloaded the Firefox extension to be able to d/l videos from there but was just visiting sites.  Anyway Youtube wouldn't even let me see anything and said I needed another extension for Firefox.  So I clicked to add the extension and Ubuntu wouldn't add it (at least I didn't know how to do it}.  

I went to [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) which says "Don't worry, installing software, themes and other things on Ubuntu is actually very easy!"  Well I'm sure it's easy once you know how to do it, but not before that!  :sad: 

Perhaps some of us who have NO clue about how to get all the programs up and running can get together on this thread and exchange newbie notes, questions, and direction etc.  If anyone is interested in this let me know.  :)

---

### Post by Kilz on 2006-09-21
That page you linked to is actualy very basic and has lots of good information and pictures to help. Exactly what application do you want to get going or install?

---

### Post by GoneWithTheWind on 2006-09-21
The issue is that I don't know (1) what Ubuntu has loaded automatically, vs (1) what I should/need to download to tweak it.  

I'm just looking for the basic stuff at this point.

My interpretation is there is some kind of a basic library to download, but I'm confused about whether I need to pick and choose every single program and/or extension that I need, or if this is done rather automatically when I type something in.

---

### Post by Brunellus on 2006-09-21
youtube wants Flash.  Flash is available for Linux, but not included with Ubuntu for a number of reasons outlined [here](http://wiki.ubuntu.com/RestrictedFormats).

Ubuntu ships only with Free, Open-source software.  Your rule of thumb is:  if you used it in Windows, and it came in a shrink-wrapped package--it doesn't come with Ubuntu.   For downloaded programs, the rule of thumb is:  If the windows version asked you to click I AGREE to an obscure legal document, it doesn't come with Ubuntu.

---

### Post by Sentinel83 on 2006-09-21
If you are looking for setting up codecs and other plugins, there is easyubuntu (all over these forums)
[http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")

That will help setup your machine to run your music and video files.  Not sure on the themes...

---

### Post by dannyboy79 on 2006-09-21
if you are wondering what you have installed on your default Ubuntu installation, go to the System pull down (third from the left along the top menu bar, i think it's labeled "system"), then go down to "Administration", then find Synaptic Package Manager or something with the word Synaptic in it, I think it's Synaptic, look for something very close if this isn't it. A box will ask for super users password, which when you use su (su=super user, in linux this means the administrator. In linux we log in with limited privalages not like windows) you can enter your username's password to temporarily get root privaliges. Once Synaptic opens, you'll see catagories down the left side and a list of software or programs down the right side, they have a brief description along with the name. If you click on one, it'll show you even more detailed desciption. if you right click and go dowen to properties you can learn even more, like dependcies, the version of the software, etc etc. Think of Synaptic as youd add remove programs but it is showing you ALL available programs that can be retrieved from the repositories in your /etc/apt/sources.list file. Repositories are websites or servers that have all the files that make up the programs. I am sure you are confused now if you're new to linux. I was at one time also. If I am using terms that you aren't familar with, go to gogle and type them in like, "what is sources.list" try to find a website that is ubuntu for newbies and you can read all about all of this stuff. Ok, back to seeing what is installed on your system, look at the lower left hand side and you'll see a button that says custom, these buttons down here are filters so that you can filter the list on the right to only contain certain things, click on the custom one,  then toward the top left you'll see installed packages. Click it, now you'll see every program you have installed! Another way to see some of them is to click on Programs, then accessories, then Alacarte Menu Editor, then in each of the sections, like Internet, it'll show you programs that got installed and are grouped within the internet section. You can use Alacarte Menu Editor to add more software to your main menu becuase it currently doesn't show yuou everything you have installed. I know this is long but I had to do it. You should really try to find a website about the basics of linux first.

---

### Post by GoneWithTheWind on 2006-09-21
> **Sentinel83 said:**
> If you are looking for setting up codecs and other plugins, there is easyubuntu

Thanks.

I installed this and was able to d/l flash but it's not working yet.

"Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Click here to get the latest flash player."

---

### Post by GoneWithTheWind on 2006-09-21
> **dannyboy79 said:**
> if you are wondering what you have installed on your default Ubuntu installation, go to

Thanks much.  I've browsed through that a few times since installation, hence part of the confusion as stated above, i.e. to get Ubuntu working basically well do I need to:

(1)  Download everything from the repositories;

(2)  Download something basic from the repositories (no clue what);

(3)  Ubuntu is complete the way it was downloaded, and anything else is an extra but not needed for basic operation and use.

---

### Post by GoneWithTheWind on 2006-09-21
> **Brunellus said:**
> for a number of reasons outlined [here](http://wiki.ubuntu.com/RestrictedFormats).

Good explanation and lots of links there.

Thanks much.

---

### Post by GoneWithTheWind on 2006-09-22
It looks like basic things must be downloaded, but not everything.
So far I've gotten "easyubuntu" and "automatix", the latter which took an hour or so to complete.  

Youtube is now working.  :D   
I might have everything I need at this point, and can spend more time transitioning.

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

[http://www.getautomatix.com/](http://www.getautomatix.com/)

My next question, which I've not seen mentioned anywhere, is there a way to "transfer" what I've used on windows to Ubuntu.  For example, I'm using Thunderbird for email.  Do I need to:

1) start over with TB in Ubuntu, or can I somehow 

2) move TB from /windows to ext3 /home, so as to keep my mail files intact?

Also can I do the same with any other (Ubundu compatible) program that I've been using in windows, or do I need to start over with them on ext3 with Ubundu.  Thanks much.

---

### Post by steve.horsley on 2006-09-22
Have you managed to mount the windows disk in Ubuntu so you can read it yet? If not, read this howto:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

Try this procedure:
1) Install Thunderbird on Ubuntu (use Synaptic to do this).
2) Run Thunderbird just once (and exit) to get the settings folders created.
3) Start a nautilus file browser window, type Ctrl-H to enable seeing hidden files and open a folder called either .thunderbird or .mozilla-thunderbird (I forget which).
4) Delete the folder called default.
5) Open another nautilus browser window and find the thunderbird settings folder on your windows drive. I don't remember exactly where it goes now (it's been a while), but I think it was something like C:\Users\Documents and settings\steve\mozilla\thunderbird.
6) Copy the default folder to the other nautilus window where you deleted a default folder.
7) Start Thunderbird. If you're lucky, all your stuff will be there.

It is possible to get ext2 drivers for windows, so you could then actually reconfigure your windows thunderbird to use teh same folder as your Ubuntu thunderbird does. I shared a thunderbird install this way for a while. You have to fanny around with the profile settings to get it to use the other folder though, and I don't remember the painful details.

---

### Post by GoneWithTheWind on 2006-09-22
I've done none of these things, so will see about doing them.

Thanks for your helpfulness.  :)

Update:  This is what I get when typing "mount" at terminal:

$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda3 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)

Going to "mount windows" now (not sure what that does).

---

### Post by GoneWithTheWind on 2006-09-23
The windows mount link says:

e.g. Assumed that **/dev/hda1** is the location of Windows partition (NTFS) 
Local mount folder: /media/windows 

* To mount Windows partition 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

- - -
My windows partition is **/media/hda1** though.  Should I type this instead?

sudo mkdir /media/windows
sudo mount /media/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222 
- - -

---

### Post by steve.horsley on 2006-09-23
Every disk and partition is represeted by a device file in /dev/ For instance, your hard disk is /dev/hda. There will also be a device file for each partition, /dev/hda1, /dev/hda2 etc. It is possible to read/write directly to the drive (the bytes on the disk) by reading/writing these files. DON'T DO THAT!  They provide low-level byte access, and are unaware of any filesystem that's been written on the disk.

Once a filesystem has been written on the partition, it is possible to mount that partition and see the structure of the filesystem, directories and files. This is done by making the disk filesystem look like a folder in the root file system. The folder where the disk contents is made to appear is called the mount point. It is the job of the mount program to arrange that a particular partition, accessed through its /dev/* device file appears as a folder at the required mount point.

You can see the actual disks and partitions with the command:
**sudo fdisk -l**
and can see the mounted ones (along withe what the mount point is) with:
**mount**
Looking back now, I can see that you already posted the output of **mount** and that your windows partition is /dev/hda1 and is **already** mounted at /media/hda1. If you want it at /media/windows instead, you need to unmount it and remount it in the new place like this:
[B]sudo umount /dev/hda1
sudo mkdir /media/windows
sudo mount -t ntfs -o nls=utf8,umask=227,gid=46 /dev/hda1/media/windows[/B]

You could edit the file /etc/fstab so that it always gets mounted at /media/windows instead of /media/hda1. Use this command:
**gksudo gedit /etc/fstab**
to start the editor on that file, and be careful - a mistake could leave Linux unbootable.

---

### Post by GoneWithTheWind on 2006-09-23
> **steve.horsley said:**
> your windows partition is /dev/hda1 and is **already** mounted at /media/hda1. If you want it at /media/windows instead, you need to unmount it and remount it in the new place like this:
sudo umount **/dev/hda1**
sudo mkdir /media/windows
sudo mount -t ntfs -o nls=utf8,umask=227,gid=46 /dev/hda1/media/windows

For clarification, should this be?

sudo umount **/media/hda1**
sudo mkdir /media/windows
sudo mount -t ntfs -o nls=utf8,umask=227,gid=46 /dev/hda1/media/windows

> **steve.horsley said:**
> You could edit the file /etc/fstab so that it always gets mounted at /media/windows instead of /media/hda1. Use this command:
**gksudo gedit /etc/fstab**
to start the editor on that file, and be careful - a mistake could leave Linux unbootable.:shock: :-({|= :( 

I don't quite understand about /etc/fstab .  I guess it's not moved automatically, so I need to move it?

(Reading up about /etc/fstab)

Update:

Is /media/hda1 to /media/windows just a name change and does the same thing?

Or does changing the name do something else?

---

### Post by xpod on 2006-09-23
I just this minute installed "automatix"..again on a new install and it took it`s usual 5 minutes to run through the how to

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Dont know what took an hour for you mate???

EDIT...Dont know what happened to the link either but it was much the same as all the others
EDIT2:...I happened to it....fixed now.

---

### Post by GoneWithTheWind on 2006-09-23
> **xpod said:**
> Dont know what took an hour for you mate???

I don't know either.  :|

---

### Post by xpod on 2006-09-23
Sorry.....I gathered that but it just seems weird.(unless you got some slow internet i suppose)
Im still using "automatix" myself 3 installs and two-ish months later
cause it`s the quickest way to get the 6 or 7 things i use from it.

I had meant to NOT use it this time but .....had enough trouble in the last couple o days so took the easy option....again:oops: 

GOOD LUCK ANYWAY...KEEP AT IT....IT`S WELL WORTH IT!!!

---

### Post by GoneWithTheWind on 2006-09-23
Thanks, you too!  :) 

I loaded everything except one file from automatix.

Internet is 756/128 dsl.

---

### Post by xpod on 2006-09-23
Is THAT good??????????
Does that mean you got it all sorted then????

I would`nt know what to do with half the stuff it has:confused: :D 
It did me for the flash\java thing,firestarter,beagle,gdesklets, and one or two others ...AND of course the "debian menu" which is great for showing all app`s as some tend not to show up in the main menus after install with synaptic or the terminal....even after using "alacarte".

Something for everything...AND everyone

---

### Post by steve.horsley on 2006-09-24
> **John Rupp said:**
> For clarification, should this be?

sudo umount **/media/hda1**
sudo mkdir /media/windows
sudo mount -t ntfs -o nls=utf8,umask=227,gid=46 /dev/hda1/media/windows

You can unmount a partition by naming either the partition (/dev/hda1) or the place where it is mounted (/media/hda1) - it really depends on that you're thinking of when you decide you want to do it.
> 
I don't quite understand about /etc/fstab .  I guess it's not moved automatically, so I need to move it?

(Reading up about /etc/fstab)

Update:

Is /media/hda1 to /media/windows just a name change and does the same thing?

Or does changing the name do something else?

The choice of /media/hda1 or /media/windows is purely a choice of name. I think windows makes more sense, although I have /media/C and /media/E personally. (D is the cd-rom in Windows.)

The tradidional mounting point for unix is /mnt/*  rather than /media/*. Ubuntu treats these differently in that anything mounted under /media (and only things mounted under /meda) is awarded an icon on the desktop. I think /media is really intended for removable stuff like CDs, cameras, USB sticks. And I lied above, I mount my windows stuff under /mnt not /media because I don't want a desktop icon.

/etc/fstab is a list of which partitions to mount and how, that the O/S reads at boot time. It is not read again unless you use the mount command. Off the top of my head, **mount -a** says mount everything in fstab. If you say **mount /dev/hda** or **mount /media/C** it looks in fstab to see if it can work out exactly what you mean - get the rest of the details it needs.

---

### Post by GoneWithTheWind on 2006-09-24
Thanks, I appreciate your helpful explanations.

It looks like I'm okay as to the windows disk being mounted then.

Update:

Trying to figure the other stuff out now.

---

### Post by GoneWithTheWind on 2006-09-25
Thunderbird is installed but I've having a hard time "finding" it and getting it to open.  I typed "thunderbird" in the terminal and nothing happened (command not found).  I typed alt-F2 run: thunderbird and it says "the file or location could not be found".

Update:

Clicked "add" under applications > internet, "okay".  Still not showing up.  Hopefully getting closer.  Ah I needed to check the box and click "apply".  I think it will show up in a minute.  Strange, it says "installing" but synaptic said it was already installed (though not showing up anywhere).  Now it is showing up under applications > internet!

Going to sleep then looking at the next steps tomorrow.

---

### Post by GoneWithTheWind on 2006-09-25
> **steve.horsley said:**
> 1) Install Thunderbird on Ubuntu (use Synaptic to do this).
**2) Run Thunderbird just once (and exit) to get the settings folders created.**
3) Start a nautilus file browser window, type Ctrl-H to enable seeing hidden files and open a folder called either .thunderbird or .mozilla-thunderbird (I forget which).
4) Delete the folder called default.
5) Open another nautilus browser window and find the thunderbird settings folder on your windows drive. I don't remember exactly where it goes now (it's been a while), but I think it was something like C:\Users\Documents and settings\steve\mozilla\thunderbird.
6) Copy the default folder to the other nautilus window where you deleted a default folder.
7) Start Thunderbird. If you're lucky, all your stuff will be there.

I'm not sure what to do on step 2) now.

The first choice is to "import" all information.  I clicked exit but now it doesn't show that choice anymore and asks me to set up the account information.  Do I do this (same as in windows) or just click it off and go to step #3?

> **steve.horsley said:**
> Start a nautilus file browser window, type Ctrl-H to enable seeing hidden files and open a folder called either .thunderbird or .mozilla-thunderbird (I forget which).
4) Delete the folder called default.

After looking around for a few days, I'm guessing the nautilus file browser window is at "places > computer".  Hidden files are enabled (ctrl-h).  I clicked "search", typed in variations of .thunderbird and .moxilla-thunderbird, while selecting different options on the left, and nothing is happening.

---

### Post by steve.horsley on 2006-09-25
Import if you like, but you will overwrite it later.
If you got to the create an account wizard, that's far enough. .mozilla-thunderbird will have been created in your home folder. 

If you open places->home folder, .mozilla-thunderbird will be there.

---

### Post by meernabeel on 2006-09-30
I downloaded few programs from the repository, they were downloaded and synaptics showed them being installed, no errors, but they are not bieng shown in the Applications menu, how do i access them. I downloaded a bittorrent client, Amsn and a movie player, but cant find them anywhere.

---

### Post by podunk on 2006-09-30
I have the same problem. 

I am *sure* this is not the right way to do it, but I get around the problem by:

```
sudo updatedb
```

I then type 
locate filename | less

This gives a list of everything remotely related to the program. I look the list over, things like games can go on for screen after screen, find what looks like a likely candidate and use nautilus to browse there and right click it and choose open. If what ever opens and it's what I want I say ah ha! I've got you now my pretty!

I right click on the desktop and chose “Create Launcher.”  I browse to the file and double click. I give it a name and an icon and click close. I then drag it to the launch area on the top menu bar.

Some programs have file names completely unrelated to what the file use name is. for instance Ark Manager is what you see on a menu, but the real file name is file-roller.  I installed Legacy Doom last night and there is nothing executable even remotely related to Doom that I can find. I'm going to look on the net for a tar ball that I can compile so I'll be able to find the program.

---

