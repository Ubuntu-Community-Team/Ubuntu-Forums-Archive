---
title: "Run ubuntu/linux FROM the CD?"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Badmonkey005 on 2006-06-30
Hello everyone. While doing a system restore and installing SP2 my computer decided to commit suicide (hooray windows). My computer will not boot up - I, am happy.

I have partition recovery CD's which will restore my HD to factory settings, however my D: partition has my Web Design portfolio of more than three years which I can NOT lose.

So, short of ripping my HD out and finding another PC to plug it into (booting from THAT computers HD and accessing mine to back up the data) another OS is my only option. A friend told me about you guys, however he said something about linux actaully running from the CD. Can this be done? Or do I have to install it? And if I do install it will it leave my partitions and just find free space to install?

If I cannot run ubuntu from the CD itself is there some other version of linux that I can do this with?

Thank you in advance for the help!

Oh, and I am an advanced PC user so no need to go into in depth explination on anything.

---

### Post by IYY on 2006-06-30
Yes, this can be done. In fact, that's the default way in which the Ubuntu CD works. You just put it in the CD drive, reboot and you have your desktop.

If you choose to install it, it can be done in many ways. You could wipe the whole thing, or create a new partition. Just be careful when you do it, and follow the instructions (although if your data really is that important, I wouldn't suggest this without having a back-up).

---

### Post by catlett on 2006-06-30
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/) Go here and download the Desktop PC Version. It is a live cd and an install cd.
Live cds are the big thing in linux now. You can run a linux OS directly from the cd. Your hard drive is not touched. The OS basically uses the cd as a hard drive.
I would use the live cd capability first just to be safe. It sounds like your hard drive isn't very healthy right now. So I would recover your data first and then run the installer.
The only thing is you will need 2 cd drives if you want to transfer the data to cd because the live cd will occupy 1 drive the whole time. Or you could use a usb flash drive if you didn't have 2 drives.

About install. It can make it's own partitions and leave your other ones alone. It is usually very safe and simple but I don't know why your computer crashed so I couldn't sau it will partition and install fine.

---

### Post by Badmonkey005 on 2006-06-30
Awesome! Do you know if ubuntu will detect my 30 GB Ipod Video? This was my only real plan on how exactly to backup the data. I <3 my Ipod

---

### Post by catlett on 2006-06-30
Yes it will. Just plug it in after the desktop comes up. It will mount with an icon on the desktop. After that you can use that space for the data recovery. 
You can drag and drop the data but you may have permission issues. If you launch the file browser (it is called nautilus. It can be launched by going to the top panel and selecting Places<Computer) Then you just double click your ipod icon and drag and drop if that is easiest for you (there are commands that are easier if you want to try).

If you get a permissions error just launch nautlilus like this. Open a terminal (go to the top panel again and select Applications<Accessories<Terminal) this is similar to getting a command prompt in windows. Enter this```
 gksudo nautilus
``` This launches nautilus as root (root is administrator in linux.) so you will have the proper permission to move the files.

Just post here when you run the live cd and someone can walk you through it.

P.S. The live cd default login username is ubuntu and the default password is nothing just press enter.

---

### Post by Badmonkey005 on 2006-06-30
wow! awesome support, thanks guys!

Just one more thing... the CD installation is an ISO

Do I burn this directly to the CD or do I need a special program? I'm on my dads Windows 98 which has some crappy CD burner program and probobly can't handle anything more than that.

[edit] yeah yeah yeah, I called myself and advanced PC user but I don't know much about ISO's. Sue me :-P

---

### Post by catlett on 2006-06-30
Nobody is born knowing everything so don't sweat the iso issue.
In mjy signature (i.e. the stuff written at the bottom of my posts with the [COLOR="Red"]@[/COLOR]) There is a link to a how to. The link is "How-to install Ubuntu" Select the "Live Cd Install". This takes you to a great how to. The how to tells you how to download and install a cd burning application and how to use that application to burn an iso. Just follow the guide.
After you recover your data with the live cd you can use that how to as a guide for installation.

P.S. Always post any question you have. It is an old corny saying but it is true "The only stupid question is the question not asked"

---

### Post by Badmonkey005 on 2006-06-30
Thank you - unfortunatley that guide has no hope for my in terms of WIndows 98

I wouldn't even want to try installing anything on this computer.

---

### Post by catlett on 2006-06-30
Why don't you put your dead hard drive in the windows 98 computer as a slave drive and try to access it through win 98?
If you never did it it isn't very hard to do.

---

### Post by IYY on 2006-06-30
> Do I burn this directly to the CD or do I need a special program? I'm on my dads Windows 98 which has some crappy CD burner program and probobly can't handle anything more than that.


You should try. I think that even a crappy CD burner program will support ISO.

---

### Post by Badmonkey005 on 2006-06-30
catlett: because in my condition I should not be anywhere near the inside of a computer (just had wisdom teeth out - doped up on vicodin)

IYY: i'll try that - wish me luck

thanks again guys

---

### Post by Badmonkey005 on 2006-06-30
WOW, either the server is really slow or my dad's internet is becasue it was about to take six hours to download that!

And it's 714 MB... the CD's I have are 700 - what's up with that?

---

### Post by catlett on 2006-06-30
I just started a download to check. The ubuntu servers are running slow tonight. I was only downloading at 200kb but it estimated 59minutes to finish. But more importantly the file size was only 697.8mb. Did you download from the link I gave you? Did you select 
> Ubuntu 6.06 LTS (Dapper Drake)
Select an image

Ubuntu is distributed on three types of images described below.
Desktop CD

The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use. You will need at least 192MB of RAM to install from this CD.

See the release notes for known issues installing from this CD. This image is not suitable for upgrading from previous releases; see the upgrade instructions for that.

There are three images available, each for a different type of computer:

[COLOR="Red"]PC (Intel x86) desktop CD[/COLOR] 

---

### Post by Badmonkey005 on 2006-06-30
yeah I tried a different mirror and it is going a little faster

the download manager says it's more...

<3 Windows 98

/sarcasm

Downloading... Preying that "B's Clip GOLD 5" will burn an iso... lmao

[Edit] Hey wow, this computer has WINrar - if I just extract the ISO to a folder and burn the contents of the folder I think it will work. Correct me if you think i'm wrong.

---

### Post by IYY on 2006-07-01
> [Edit] Hey wow, this computer has WINrar - if I just extract the ISO to a folder and burn the contents of the folder I think it will work. Correct me if you think i'm wrong.

You're wrong. An ISO is more than just a bunch of files on a CD, and this method will not work.

---

### Post by Badmonkey005 on 2006-07-01
well luck would have it that this program DOES support image burning. But I accedently downloaded the alternate download. Is it worth downloading the original? Or does the alternate just have extra stuff to it?

---

### Post by Badmonkey005 on 2006-07-02
OK. I downloaded and burned ubuntu

I got home and put it in my drive and it starts to boot up. Everything's peachy. All of a sudden I get an error: 
> "Failed to start the X server (your graphical interface). It is likley that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

Could this be because of a corrupted download? It worked fine on the computer that I burned it on. I also ran the "Check disk for errors" and no errors were found. All the checksums came out OK.

I also tried running nautilus and it said it couldn't open the display - which would make sense.

Where do I go from here?

THank you!

[edit]

Sony VAIO:
Intel Pentium 4: 2.4 GHz
512 MB RAM
80 GB Hard Drive

---

### Post by IYY on 2006-07-02
This nothing to be worried about. Ubuntu just didn't properly recognize your video card and so it could not load the GUI. To fix this, you can do one of the following:

1. run the command 

```
sudo dpkg-reconfigure xserver-xorg
```

and enter the information about your video card, monitor, etc.

2. same as above, but enter 'vesa' as the driver

3. (I find it to be the simplest, but it requires configuring a file): run the command

```
sudo nano /etc/X11/xorg.conf
```

this is a text editor. Find the line that says 'Driver' and change the driver to vesa.

(Driver "vesa")

---

### Post by Badmonkey005 on 2006-07-02
wow that's a lot of complicated info

I have an ATI Radeon 9250 256MB Video Card

I'm looking at the manual and cannot see that information. I am seriously consitering pulling the damn thing out and using my OnBoard

---

### Post by Badmonkey005 on 2006-07-02
OK, I enterd in all of the information and set the driver as the "vesa"

So I am back at the command promt - what now?

Also - did this info get saved on my HD or will I have to do this again if I use Live CD again?

Thank you.

---

### Post by Daremo on 2006-07-02
great reply.
This is why Unbunu i s such a great distro!

---

### Post by Badmonkey005 on 2006-07-02
someone call the cops my thread just got hijacked!

to anyone actually trying to help me - the important info is on the end of page 2...

---

### Post by catlett on 2006-07-02
If you enter the live cd again just plug your monitor into your built in video card.
If everything  is configured correctly enter ```
startx
``` will start up the gui (i.e. ubuntu)
Actually if it says** ubuntu login** instead of **root@ubuntu** Then you have to login first. Enter ```
ubuntu
``` Then enter nothing just press enter at the prompt for a password. Meaning there is no password for the live cd. Just ubuntu for the login name and press enter for the password.
```

``` And then enter startx when you get root@ubuntu

---

### Post by codejunkie on 2006-07-02
[quote=Badmonkey005]someone call the cops my thread just got hijacked!

to anyone actually trying to help me - the important info is on the end of page 2...[/quote]
after you have changed the driver to vesa, and are back at the command prompt run ```
sudo /etc/init.d/gdm restart
```this will restart the gui using the new driver.

---

### Post by IYY on 2006-07-02
> Also - did this info get saved on my HD or will I have to do this again if I use Live CD again?

It doesn't touch your HD (for safety reasons), so you'd have to do it again.

---

### Post by Badmonkey005 on 2006-07-02
you guys weren't quick enough - I got impatient and just ripped my video card out - hoping it will detect my onboard

it's booting up now

edit: my impatience paid off - it booted up fine and I am at the desktop

I am now plugging in my Ipod and starting nautilus

---

### Post by Badmonkey005 on 2006-07-02
I have good news and bad news. Good news: I am currently posting from ubuntu

Bad news: I cannot open any of my partitions. I get an error saying it cannot mount the drive.

What now?

Thank you!

---

### Post by aysiu on 2006-07-02
Are these Windows partitions or Linux partitions? Well, either way...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by catlett on 2006-07-02
You only need to mount it for this session so this command will work. But first I need to know how many partitions you have. I'll post the commands anyways. But if they don't work post the output of this```
 sudo fdisk -l
```
But for now I will assume you have 2 partitions. So just cut and paste these commands into the terminal. You get the terminal by going to the top panel and selecting Applications<Accessories<Terminal.
First you have to make a place to mount the partitions 
```
sudo mkdir /media/windows1
```
```
sudo mkdir /media/windows2
```
Then you have to mount them
```
sudo mount /dev/hda1 -t ntfs /media/windows1
```
```
sudo mount /dev/hda2 -t ntfs /media/windows2
``` This assumes you have 2 windows partitions on one ide hard drive and that they are formatted to ntfs. If there is a problem, run sudo fdisk -l and cut/paste the output in a reply

---

### Post by Badmonkey005 on 2006-07-02
I got it and it looks like everything worked.

Thank you everyone! Especially IYY

Wish me luck on restoring windows now.... ugh

---

