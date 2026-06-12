---
title: "Need help installing Kubuntu"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Nile1037 on 2008-04-07
Right now I have one hard drive, partitioned into 4 sections. First is Windows Vista, on a 60 GB partition, with all my documents (music, videos, work etc). Next is Windows XP, on a 20 GB partition. It's only there to run non-Vista compatible programs, and as a backup in case Vista BSOD's again. My 3rd partition is a 50 GB partition, which I use to backup Vista. There's nothing else on it. My last partition is 20 GB, and is empty right now. This is where I want to set up Linux.

When I boot my computer, I have the choice of going into Vista or XP, and my goal is to get Kubuntu into those options. I downloaded Kubuntu off of the official site ([here]("http://mirror.csclub.uwaterloo.ca/ubuntu-releases/kubuntu/gutsy/")). I chose the Desktop CD, and this one: PC (Intel x86) desktop CD.

Before posting here, I asked on another forum which I frequent about how to install Kubuntu, and they mentioned things about how Kubuntu should be your primary drive. I have no idea how to change my primary drive, or what it really means. 

So what I'm asking is for some help on making sure I can boot into Linux just as I do into Vista or XP. I also want Vista and XP to remain fully functional. I tried to install Ubuntu about a year ago and failed miserably, having to reinstall all OS's. 

Thanks in advance for your help.

---

### Post by anjilslaire on 2008-04-07
Boot into Windows (any) and delete the unused partion, so that you have 20gb unused space.
Boot your ubuntu CD and start the installer. When it gets to the partitioning portion, select the option to "use the largest available free space", or whatever it's called. ( I partition manually, so I don't recall what the wizard says).
Before it starts, it'll show you what its going to do, and you can see that your 3 other NTFS partitions are still available. When you're sure it's set right, let it install.

---

### Post by Nile1037 on 2008-04-07
> **anjilslaire said:**
> Boot into Windows (any) and delete the unused partion, so that you have 20gb unused space.
Boot your ubuntu CD and start the installer. When it gets to the partitioning portion, select the option to "use the largest available free space", or whatever it's called. ( I partition manually, so I don't recall what the wizard says).
Before it starts, it'll show you what its going to do, and you can see that your 3 other NTFS partitions are still available. When you're sure it's set right, let it install.

Why would I delete the unused partition if that's where I want to install Kubuntu? Did you mean the 3rd partition that I use for backups? I need that one.:(

---

### Post by anjilslaire on 2008-04-07
No, Linux will create it's own partitions with th unused space. The windows-based partitions are not of any help to the linux installer.

I recommended removing the partition so the installer can just use the free space more easily. I'm talking about the unused 4th 20gb partition. You don't need to lose the other 3.

Linux will create a "/" and swap partitions in the ext3 format, not fat or ntfs like is probably already there.

---

### Post by bodhi.zazen on 2008-04-07
You can do everything from the kubuntu live CD BUT you need to know linux partition terminology.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Use Gparted (it is on the Kubuntu CD), delete the unwanted partition, create a new extended partition (you need two partitions for Ubuntu).

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

Within the extended partition make a swap partition and one for Ubuntu (root or / ). Swap should be RAM X 2, max 1 Gb unless you have a laptop and want to suspend , in which case swap = RAM.

Then make an ext3 logical partition in the remaining space.

Then start the installer and use the above partitions for swap and /

The installer will set up GRUB. You may need to do some post install grub configuration, let us know if you have problems.

---

### Post by mgranet on 2008-04-07
The very first thing you need to do is defrag both XP and Vista. I've heard people who like to defrag multiple times, just to be sure. I've never tried this, but I figure it can't hurt. Next, you need to be aware that GRUB will take precedence as your bootloader. You won't boot to Microsoft's loader anymore, but GRUB will display Vista and XP all the same.
Next, boot to your Kubuntu disk. Select Manual Partition. Your current 20GB partition is probably already in NTFS, so you will need to delete it. Now, you will need to create two new partitions. First, you will need a ext3 partition, mounted as root ("/"). You should also create a swap parititon, ideally twice the size of your installed memory. Select the checkbox to format the ext3 partition"/" , then continue the install.

EDIT: Or what **bodhi.zazen** said. Dang, 6 minutes. I guess I type slow. Or think slow. I don't remember which.

---

### Post by JoshuaRL on 2008-04-07
You are right though mgranet, defrag is very important if you're messing with partition sizes.  If not, it's less important but still a good idea.

And if possible, always back up your data just in case.

---

### Post by mgranet on 2008-04-07
> **JoshuaRL said:**
> You are right though mgranet, defrag is very important if you're messing with partition sizes.  If not, it's less important but still a good idea.

And if possible, always back up your data just in case.

I know. Don't mind me, case of the Mondays.

---

### Post by Nile1037 on 2008-04-07
Thanks guys. :)

I'm defragmenting as I write this. When it's done I'll start the fun part, and if I have problems I'll write back.

---

### Post by D|F on 2008-04-07
Hello, i have some problem here.
i was installed Kubuntu Desktop, but when i login, i mean when i insert my username and password its open the terminal box...
What i have to write in that terminal box to open my Kubuntu?

---

### Post by JoshuaRL on 2008-04-07
> **D|F said:**
> Hello, i have some problem here.
i was installed Kubuntu Desktop, but when i login, i mean when i insert my username and password its open the terminal box...
What i have to write in that terminal box to open my Kubuntu?

Are you sure that you got Kubuntu and not the server?  Kubuntu should load a desktop without inputing anything.

But just to be sure, try:
```

startx

```

---

### Post by D|F on 2008-04-07
I was writed startx ,its coming like this:

xauth: creating new authority file /home/ darknessfall(my username)/ .serverauth.8853

X: user not authorized to run the X server,aborting.
Couldnt get a file descriptor referring to the console

That it... What i have to do now? Please, i need help to open my Ubuntu.

---

### Post by JoshuaRL on 2008-04-07
I would suggest you burn off another disk, making sure to use the slowest burn possible, and reinstall.  It seems that the user and Xwindow is messed up some.  It can usually be fixed from the command line, but it will be easier if you just reinstall if you haven't even got into it yet.

---

### Post by bodhi.zazen on 2008-04-07
> **D|F said:**
> I was writed startx ,its coming like this:

xauth: creating new authority file /home/ darknessfall(my username)/ .serverauth.8853

X: user not authorized to run the X server,aborting.
Couldnt get a file descriptor referring to the console

That it... What i have to do now? Please, i need help to open my Ubuntu.

Or try :

```
sudo cp /root/.Xauthority /home/user
sudo chown user.user /home/user/.Xauthority
```

Change "user" to your log-in name

Then :

```
sudo /etc/init.d/kdm stop
sudo /etc/initld/kdm start
```

---

### Post by Nile1037 on 2008-04-08
I'm now trying to burn Kubuntu on a CD. I think I'm retarded or something, because I can't find the ISO file. :confused:

I unzipped the .zip and I got the folder, and inside is:

[IMG]http://i31.tinypic.com/34xjog3.jpg[/IMG]

Help please :(

---

### Post by Nile1037 on 2008-04-08
Anyone please?

---

### Post by JoshuaRL on 2008-04-08
It isn't a .zip even though winrar sees it as that.  The file you downloaded is in fact an .iso and needs to be burned as such at the lowest speed possible.  If you do that, then insert it into the CD drive and restart the computer.  Make sure you have BIOS set up to boot from the CD drive, and it should let you boot into the Live CD.

---

