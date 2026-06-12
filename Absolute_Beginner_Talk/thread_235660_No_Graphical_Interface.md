---
title: "No Graphical Interface"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by ooolongT on 2006-08-13
Admittedly, I am out of my league with Ubuntu.  I am now cursing the fact that I didn't do a dual installation with Windows, but I was hoping that I could avoid windows altogether.

Here's my situation.  I have a copy of Ubuntu 5.04 for Intel x86.  I also have an old laptop on which I was trying to install it.  The laptop is a Toshiba Satellite 2065CDS.  I put in the install disk and went through the installation process, and didn't seem to have any problems.  However, for some reason, I get no graphical interface when I start the computer.  All I get is a prompt that says:

t@ubuntu:~$

The one thing that I notice when I start it is that i get a message saying that there is a

"ror * Temporay failure in name resolution    [fail]" 

So I put in the installation disk and was going to try to reinstall Ubuntu, figuring that there was something wrong with the install, but while I can hear the disk spin up during start-up, I cant seem to get to the CD drive and it is not booting from it. 

So then i tried booting in safe mode.  That doesn't seem o help at all, I get the same prompt.

I tried:

sudo /etc/init.d/gdm start 

but it says command not found

So THEN I tried:

sudo aptitude update
Sudo aptitude install 

Both of which seemed to go alright, so then I used:

sudo aptitude install sysv-rc-conf 

and as it was running, all kinds of errors started until it finally said 

Processing was halted because there were too many errors.
Reading package lists... done
Building dependency tree
Reading extended state information
Initializing package states... Done
t@ubuntu~$

Darn!  Sooo....What do I do now?  Why is the graphical interface not coming up?  How can I make it come up?

---

### Post by foolsh on 2006-08-13
did you use the server option to install it?
if so sudo apt-get install ubuntu-desktop should fix that

---

### Post by kebes on 2006-08-13
Any particular reason you are using the 5.04 version? Perhaps try downloading the latest version: Ubuntu 6.06 LTS (Dapper Drake). This version acts as both an install CD and a LiveCD. When you boot off the CD, you should be brought into a fully-functional Linux environment (complete with GUI), which will let you check your hardware compatibility. You can also then install directly from this graphical environment.

The newest Ubuntu may also have fixed any bugs from the previous version. The newest version is of course a free download, which you can burn to a CD easily.

Make sure you get the standard version and not the "alternate" or "server" version which don't necessarily install a graphical environment.

---

### Post by foolsh on 2006-08-13
you might have to "sudo apt-cdrom add" first though

---

### Post by foolsh on 2006-08-13
"error * Temporay failure in name resolution [fail]"
is just ubuntu trying to set the time with the time server I imagine

---

### Post by ooolongT on 2006-08-13
> **foolsh said:**
> did you use the server option to install it?
if so sudo apt-get install ubuntu-desktop should fix that

I did not (at least not intentionally)  install the server option.

However, by typing "sudo apt-cdrom add" I got it to read the CDROM which is a start, so I put the installation disk in and it said found 2 package indexes, and one signature, and identified the disk as Ubuntu 5.04 _Hoary_Hedgehog_ - Release i386 (20050407).  Then it said that it was a good image etc.  But then I'm back to my beloved t@ubuntu:~$ prompt.  so nothing is changed except it did get the CDROM working, so that's a step in the right direction!

---

### Post by ooolongT on 2006-08-13
> **kebes said:**
> Any particular reason you are using the 5.04 version? Perhaps try downloading the latest version: Ubuntu 6.06 LTS (Dapper Drake). This version acts as both an install CD and a LiveCD. When you boot off the CD, you should be brought into a fully-functional Linux environment (complete with GUI), which will let you check your hardware compatibility. You can also then install directly from this graphical environment.

The newest Ubuntu may also have fixed any bugs from the previous version. The newest version is of course a free download, which you can burn to a CD easily.

Make sure you get the standard version and not the "alternate" or "server" version which don't necessarily install a graphical environment.

To answer your first question, I am using it becuase this is the disk that my professor gave me.  No reason other than that. (no, this is not a class project he just hooked me up with it and said that it was a good version of linux for beginers)

If I do download the new version, and throw the disk in, will it boot automatically (I jsut restarted with my 5.04 version and it did not)?  Is there something that I can type at my ubuntu:~$ prompt to get it to reinstall once I get the new version?

---

### Post by kebes on 2006-08-13
Typically to boot a LiveCD or install CD you need to change a setting in your BIOS. So during boot you press some "magic key" (usally the "Delete" key although on some computers it is "F8" or something else), which brings you to a settings page. There you can set the "Boot device priority" and tell it to "Boot from CD-ROM" (obviously the settings will look a bit different on your computer).

That may fix the "not booting from CD" problem. With the newest Ubuntu, when you boot from CD you are brought directly into a nice graphical environment, and don't have to worry about the "ubuntu:~$" prompt if you don't want to.

I have found that generally the latest Ubuntu is great at doing hardware detection and booting into the graphical environment, so it's worth a shot if you have easy access to internet and a CD-burner.


If you're able to mount your current install CD, though, that's a  good start. You can try doing:
```
sudo aptitude install ubuntu-desktop

```
which should install the graphical environment that you are lacking. If it says "everything already installed" then you should be able to jump into the graphical environment by doing:
```
gnome-session
```
(or perhaps you're supposed to type "startx" ...)

---

### Post by ooolongT on 2006-08-13
> **kebes said:**
> Typically to boot a LiveCD or install CD you need to change a setting in your BIOS. So during boot you press some "magic key" (usally the "Delete" key although on some computers it is "F8" or something else), which brings you to a settings page. There you can set the "Boot device priority" and tell it to "Boot from CD-ROM" (obviously the settings will look a bit different on your computer).

I was unable to get into the bios, by pressing wither delete or F8, what did happen was I went to the Grub screen that allows me to start in different modes.  I tried editing them but I don't know how to tell it to boot from CD by editing it. So I tried the recovery mode, which didn't help, all it got me was the root@ubuntu:~# prompt.  Remember, this computer no longer has Windows on it, so maybe that's why getting to the BIOS is difficult?

I do have the Internet and a burner, do I need special burning software to create a disk that Ubuntu can read? I will be on a desktop PC with XP home on it

I tried :
```
sudo aptitude install ubuntu-desktop

```

and it returned a bunch of messages like this:
```
ide failed opcode was : unknown
end-request: I/O error, dev hda, sector 6068911
hda: dma_intr: status = 0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=6069172, sector=6069167

```

So then I tried
```
gnome-session
```
And it said 
```
 gnome-session: error while loading shared libraries: libxrandr.so.2: cannot open shared object file: No such file or directory
```
and returned me to the root@ubuntu:~# prompt.  

Sigh.

---

### Post by Kurt` on 2006-08-13
> The one thing that I notice when I start it is that i get a message saying that there is a

"ror * Temporay failure in name resolution [fail]" 
Yeah, don't worry about that error. Ubuntu tries to sync your system clock with a known correct value (via Network Time Protocol). That error means you're not connected to the internet (aka, no working DNS).

---

### Post by kebes on 2006-08-13
> **ooolongT said:**
> I was unable to get into the bios, by pressing wither delete or F8, what did happen was I went to the Grub screen that allows me to start in different modes.  I tried editing them but I don't know how to tell it to boot from CD by editing it.

Look at this article on the Toshiba website:
[http://askiris.toshiba.com/ToshibaSupportSite/search.do?cmd=displayKC&docType=ex&bbid=bb66&url=&dialogID=13164187&stateId=1%200%2013160839](http://askiris.toshiba.com/ToshibaSupportSite/search.do?cmd=displayKC&docType=ex&bbid=bb66&url=&dialogID=13164187&stateId=1%200%2013160839)

It says that to boot from CD you should hold down the 'C' key while the computer is starting up (with the CD in the drive of course). It also explains how to enter setup mode (it says that on Toshiba laptops the key will be F2 or F12 probably). Use that guide to boot from the CD.


> I do have the Internet and a burner, do I need special burning software to create a disk that Ubuntu can read? I will be on a desktop PC with XP home on it

That's all you need. Go to:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
pick your location and downlad the "PC (Intel x86) desktop CD" version. To burn it to a CD you just open up your CD-writing software, and make sure that you select "New CD from Saved Disk Image" (or something like that). Don't just copy the big file onto a CD--you have to burn the CD image! Every burning software can do this, you just have to make sure you select the correct option. (Sometimes it is called "make CD copy" and then you select "saved image..." and pick the file.)


> end-request: I/O error, dev hda, sector 6068911
hda: dma_intr: status = 0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=6069172, sector=6069167


Those errors sound pretty bad. Looks to me like either your hard drive is not working properly, or your installation didn't proceed properly. I would reinstall Ubuntu entirely, either using your previous disk or after downloading the latest version.

Typically it is not this difficult to get Ubuntu installed correctly, so I'm worried the hard drive may be buggy. During the install, let Ubuntu do a full disk reformat (assuming you don't have any important data on the drive).

---

### Post by ooolongT on 2006-08-13
I want to thank Foolsh, Kurt', and most of all Kebes for taking the time to help me with this, and for not being hard on an obviously not-too-bright noob.  You guys have been great.  Thank you so much!  

Unfortunately, I have determined that this laptop has physical problems with the disk, hence all of the errors I was getting.  I will be replacing the hard drive, and I'm sure you will be hearing from me again then!

Thanks for your help!

---

### Post by kebes on 2006-08-13
You're quite welcome for all the help. Sorry to hear that the disk is bad.

Feel free to come back to the forums with more questions if/when you attempt another Ubuntu install.

---

