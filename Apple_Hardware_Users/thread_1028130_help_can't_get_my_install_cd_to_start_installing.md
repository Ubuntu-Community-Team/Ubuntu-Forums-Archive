---
title: "help can't get my install cd to start installing"
date: 2009-01-02
forum: Apple Hardware Users
---

### Post by chrisginger26 on 2009-01-02
Hi Guys 

I have a blue and white G3 Revision 1 350mhz  with 448meg of ram and 6gig hard drive.

I have downloaded a powerpc version of xubuntu 6.06 alternate cd and when I place the cd in the drive and boot holding 'c' down I get:

/pci/pci@d/mac-i0@5/ata3@20000/disk@0:2,yaboot.conf:Unknown or corrupt filesystem.

can't open file 

welcome to yaboot version 1.3.13

Enter "help" to get basic usage inf

By typing cd @ boot the drive spins but I then get a message of 

cd:2,/vmlinux:Unknown or corrupt filesystem 

To try and get the cd to run I have also tryed these two commands with no luck
cd:2,installer/yaboot,/install/powerpc/vmlinux

Unknown or corrupt filesystem 

cd:2,/installer/powerpc/vmlinux initrd=/installer/powerpc/initrd.gz

Unknown or corrupt filesystem 

I know that the cd's good because when I do the same on my g4 imac I get the option to type live video=ofonly and then the cd starts runing the installer.

any ideas would be great is this something to do with the old and new world mac thing and open firmware? 

love to be able to bring the old blue and white back to life!

---

### Post by tiresia on 2009-01-02
Have you tried to boot the g3 with another CD, e.g. with MacOS?
Are you sure that the CD-ROM is still working?

---

### Post by chrisginger26 on 2009-01-02
Hi tiresia

Yes I have had the system running mac os tiger up untill now but it freezes and crashes to much to run it as a full time os. Looking for something more scaled down that will be a bit more stable.

thanx 

chris

---

### Post by mkvnmtr on 2009-01-02
Your burn may not be good. You need to check the download in disk utility. I think they call it verify. Then when you burn you need to burn as an image. If you are using the mac to burn when you open disk utility click on burn and import the ISO. It will then tell you to insert a disk. Use a cd read only disk. Everyone seems to have better luck with those disks.When you restart hold down the "c" key until you see first the mac icon come up and then the linux icon come up. There should be no commands to type. Click on the linux icon and then the arrow.

---

### Post by chrisginger26 on 2009-01-02
Hi mkvnmtr

I am using the alternate cd which works in a kinda comand prompt and works on my Imac G4 but won't boot on the G3 both the macs are new world according to what I have read.

thanx chris

---

### Post by mkvnmtr on 2009-01-02
6.06 should boot right up but I never used the alt disk. When you restart and the first words com up press the tab key, If it is like the live disk you should see a whole page of options. First try the one closest to "live=nosplash". If that doesn't work try the others one at a time. You will have to restart and use the same procedure each time. After you type in the option  remember to press enter.

I f you don;t have any luck try the live disk.

---

### Post by chrisginger26 on 2009-01-02
Hi mkvnmtr

I Have just tryed the Tab button which comes up with the same Unkown or corrupt filesystem 
after that I tryed "live=nosplash" and "live=nosplash-powerpc" which gave me the same Unknown or corrupt filesystem.

My only question is will the live d work on a blue and white g3 I was under the impression that you had to use the alternate text based installer on it ?

I will download and try one though 

thanx chris

---

### Post by chrisginger26 on 2009-01-02
Hi mkvnmtr

I am now downloading the mac powerpc version of desktop cd from here

[http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)

hope this is the right version I thought I would try ubuntu instead just to rule it out 

thanx again chris

---

### Post by chrisginger26 on 2009-01-02
Hi Guys

I Have just tryed my new cd in the G3 with the same results as before.

I then put the cd in my imac g4 (1.25ghzg4 1.25gigram 17inch usb 2) and it boot to the results below:

Welcome to Ubuntu 6.06.19(dapper drake) 

This is a ubuntu live cdrom

built on 2006006.1

the default option is 'live'

If the system fails to boot at all (the typical symtom is a white screen that does not go away), use live video=ofonly'
***********************************************************
Press the tab key for a list of option or type 'help' for help 
***********************************************************

If in doubt ,just press enter, and if theat dosen't work type live 'video=ofonly'

Welcome to yaboot version 1.3.13
Enter help to get some basic usage info 
boot: (I pressed) tab 

boot:check(Ithen pressed)

The g4 then booted to the ubuntu logo with dodgy graphics but its  ran all the way through with a result of  checksum complete 0 failed 

press any key to reboot 

I think that this proves that the cd is ok as it has got this far on my imac.

The question that I am starting to ask myself is it something to do with the G3's bus and the way its set there is a DVDrom and a zip on the same bus and the hard drive is on the other bus?

Is it worth trying disconnecting the zip do I need to point yaboot in the direction of the cdrom / linux installer files ?

Is that what" /pci/pci@d/mac-i0@5/at3@20000?disk@0:,yaboot.conf:Unknown or corupt filesystem " means as I know its not corrupt as it works in the g4 so does this mean it can't find the file to boot ?

anyone got any ideas I'm desparatly stabbing in the dark !!!!!!!!

thanx 

chris

---

### Post by mkvnmtr on 2009-01-02
I am at a lose as to how to help with your G3. You should have enough ram to install. The disk seems to be good if you can install on the G4. Can you read the mac install disk when you put it in? You see I am thinking you might have a problem with your cd drive. Did you burn the disk on the same machine?

---

### Post by stream303 on 2009-01-02
Make sure your CD-R is burnt at a VERY low speed, such as 1X or maybe 2X for that old G3.  The G4 you are burning it on may be burning it too fast.  If you can change the speed on your G4 to the lowest it will go, try that.  OR, use a windows box and a burning utility that allows for setting the burn speed to 1 or 2X max.

---

### Post by chrisginger26 on 2009-01-02
Hi mkvnmtr

I don't think there is anything wrong with the cdrom as it will boot the mac os x installer cd  and after having a look at the open firmware (comand-option-o-f instead of c on start up) 

pci/pci@d/mac-i0@5/ata3@20000/disk@0

This stands for the cdrom drive and it seems to be a problem with it finding /executing the yaboot.conf file to boot the linux kernal I'm starting to wonder if the version of yaboot is not compatible with blue and white G3. Although all documentation points to it being a new world mac.

It runs on openfirmware 3.0.0 and it was built on 11/06/98.  The New world stuff did'nt start untill jan 1999 with imacs?

I will try disconnecting the zip and putting in anoth cd drive to make sure.

Other than this I don't know what else to do

thanx chris

---

### Post by chrisginger26 on 2009-01-02
Hi stream303

OK will give it a try 

thanx chris

---

### Post by chrisginger26 on 2009-01-02
Hi stream303

I have tryed writing the disc at 8x which is the slowest my g4 will do with disc utility and the slowest my pc will go with nero and stilll got the same problem.

What difference does the write speed make?

thanx again chris

---

### Post by tiresia on 2009-01-02
How is your DVD-ROM connected? 
Did you add any 'not original' hardware to your machine?
My question before was if you are able to start the computer with a MacOS (9 or X), just to understand if the DVD-ROM is bootable.
I do believe that the Installer-CD is OK, but it can't find the correct path to CD-ROM

---

### Post by chrisginger26 on 2009-01-02
Hi tiresia 

Here is what I think is the device list in openfirmware 

Open firmware 3.0.0 

ide0 pci/@d/mac-io/ata-3@20000/
cd     pci/@d/mac-io/ata-3@20000/disk@0
zip   pci/@d/mac-io/ata-3@20000/disk@1
ide1 pci/@d/pci-ata@1/ata 400
hd    pci/@d/pci-ata@1/ata 400/disk@0

the cd and the zip are on the second ide bus cd is master and zip is slave (i think  will check as I am going to pull out the zip to save confusing) things and the hard disc is master on its own bus.

the dvdrom is not the original apple one I don't have the original .

I was considering resetting the pram and the nvram ??

thanx guys 

again

chris

---

### Post by tiresia on 2009-01-02
Yes, you can reset the PRAM/VRAM.
Before trying to access the CD via OpenFirmware, a stupid question.
Which CD's are you using, are they CD+R or CD-R?
Can your CD-ROM read both types?

---

### Post by chrisginger26 on 2009-01-02
Hi tiresia

Yes, you can reset the PRAM/VRAM.

pram and nvram reset as per instructions on the apple site

Before trying to access the CD via OpenFirmware, a stupid question.

tryed to boot cd from openfirmware 

0>boot cd:,yaboot MACPART (not-interposed) not supported load-size=0alder32=1 

load size is too small 

Which CD's are you using, are they CD+R or CD-R?
Can your CD-ROM read both types?

they are cd-r but if it can't read both types how does it get to welcome to yaboot version1.3.13

how can I find out nothing mark on top of drive?

the drive is set to master and is now the only device on the bus zip drive now disconnected 

sorry did'nt mean to sound cocky really  appriciate your 

thanx again chris

---

### Post by mkvnmtr on 2009-01-02
You say you think it is a new world machine. I have no idea. Can you Google it up and find out for sure? It might make a difference.

---

### Post by stream303 on 2009-01-03
Ok, here's your machine right?

[http://www.everymac.com/systems/apple/powermac_g3/stats/powermac_g3_350_bl.html](http://www.everymac.com/systems/apple/powermac_g3/stats/powermac_g3_350_bl.html)

I'm not familiar with your startup problem, but want you to be aware of possible further issues beyond that.

That machine might have multiple disk controllers - I might suggest using Ubuntu Intrepid 8.10 as a starting point as yaboot has been improved for disk / controller detection.  (someone correct me if I'm wrong).  And, stick to Ubuntu for the initial install - try Kubuntu and Xubuntu *later* if you want to.

Also, what monitor are you driving?  Do you know the horizontal, vertical freqs, and also the native resolution if it is lcd?  That will help when it comes time configure your /etc/X11/xorg.conf.

And is the battery dead?  You may need to replace that motherboard battery if the date is consistently wrong.

And sorry about the reference to using a very low burn speed - while still advisable, on that machine I suspect that a faster 8x (or whatever read-speed your dvdrom can handle) will do.  When I see G3, I automatically go into *imac* mode, and sometimes forget we are dealing with a B&W....

---

### Post by chrisginger26 on 2009-01-03
Hi stream303

Yes this is my G3 [http://www.everymac.com/systems/appl...g3_350_bl.html](http://www.everymac.com/systems/appl...g3_350_bl.html) it is one of the very early revision1 G3 with an ata/ide controller that cannot handel disks over 20gig it has read problems above this as you say it may have multiple disk controllers i'm not sure.

Where can I download Ubuntu Intrepid 8.10 as I can only find a powerpc download for the server edition?

The moniter is an old crt how would I find out about horizontal and vertical frequencies will this affect the install or will i need to deal with this after my install ?

realy would love to breathe life into the old beast as its my garage jukebox/net  machine 

thanx again

chris

---

### Post by pxwpxw on 2009-01-03
Ubunut 810 Server is fine, it just gives you a text console initially, then you can install a desktop after that is working. Its also quicker and easier. You dont install the extra server packages when it asks you.

---

### Post by chrisginger26 on 2009-01-03
OK  Guys 

Just tryed 8.10 alternate cd with same result the disk boots on my G4imac and thats the third version I have tryed now. 

Does it matter what os I had installed before?

I have been reading this article here [https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs) 
about bootx etc I know my G3 is not surposed to be an old world?

What else can I try ?

thanx again guys

chris

---

### Post by chrisginger26 on 2009-01-03
Hi Guys

I'm racking my brains trying to get this to work and I havr stumbled across this thread about getting cd drivers to work [http://ubuntuforums.org/showthread.php?t=1001310](http://ubuntuforums.org/showthread.php?t=1001310)

At the end of his question caffine writes "I would try another CD drive, but the Apple drive is the only drive that loads the installer at all.
Suggestions?" 

Could this be my problem as it is not the original apple drive ?

thanx again 

chris

---

### Post by tiresia on 2009-01-03
Your Mac is New World. If you need a proof, look for a USB connection. If you have a factory built-in USB port, as I believe you have, it is a New World Mac. Therefore you don't need BootX.
....... 
These are my suggestions, at least what I would do at your place:
1. Remove any extra hardware (PCI-USB Cards etc.)
2. Reset PRAM/NRVAM via Open Firmware after each hardware change (if you don't know how to do, please, ask us)
3. Try to boot with MacOS9 and make an Firmware Upgrade, if any
4. Try another Linux Distro (Debian); but it seems that it didn't work with Ubuntu Intrepid Server
5. You can have a look in Open Firmware. Following Commands can help you (most probably you know them):
```
printenv
```
To see which variables are set
```
devalias
```
To know the alias for every devices
```
cd
words
```
If you find among the 'words' the word 'open' the device should be bootable.
6. Try to install Linux via USB. Here is a link with some help:
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)

---

### Post by chrisginger26 on 2009-01-03
Hi tiresia

It turns out that my father has 2 G3's as mine and he has the same problem as I do on one of his but when he trys the ubuntu live cd in his secon/main g3 with a mac compatible dvdrw drive it boots right through to the live desktop it turns out that the apple drives have some kind of open firmware drivers built into them. Both the macs that don't boot have non apple dvd drives in them which work with os x but not ubuntu! I am going to give the install from a usb pen drive a try though to see if I can get it installed anyway as I do not have the orighinal drive and he does hes in paris and i'm in heathfield uk !!!!

thanx again will keep you posted on install from usb pen drive. 

chris

---

### Post by stream303 on 2009-01-03
Just remember to take a kind of zen attitude with this project when there is 3rd-party hardware involved, and no record of what has really been done to it.  Bricking it is entirely possible. :)

One thing I do know is that when you move / change apple hardware, one usually wants to do pram/nvram resets as well as resetting the pmu (power management unit).  In addition to the usual apple docs, I found some interesting stuff here:

[http://www.geocities.com/texas_macman/pram.html](http://www.geocities.com/texas_macman/pram.html)

It isn't geared towards linux in particular, but has some good info.

One thing I do remember from the ppc archived forum, is that video for linux on B&W's should be connected to the TOP slot, and not the bottom.  While a video card connected to the bottom slot works with mac-os, only the top slot works with Linux.  At least that's what I read - maybe something to try in case you have two cards, or the card is in the bottom slot.

This is definitely going to be an adventure. :)

---

### Post by mkvnmtr on 2009-01-03
I would really like to see your installation written up and maybe put in the wiki on ppclinux. I have seen these problems before in the forum but there are so many posts the get lost. I would like to read about someones success.

---

### Post by chrisginger26 on 2009-01-04
Hi stream303

just remember to take a kind of zen attitude with this project when there is 3rd-party hardware involved, and no record of what has really been done to it. Bricking it is entirely possible. 

One thing I do know is that when you move / change apple hardware, one usually wants to do pram/nvram resets as well as resetting the pmu (power management unit). In addition to the usual apple docs, I found some interesting stuff here:

I HAVE ALREADY RESET THE PRAM AND NVRAM DO YOU THINK RESETTING THE 
PMU WILL SORT OUT THE CDROM I WILL TRY REPLACING THE BATTERY AND RESETTING IT NEXT?

[http://www.geocities.com/texas_macman/pram.html](http://www.geocities.com/texas_macman/pram.html)

It isn't geared towards linux in particular, but has some good info.

One thing I do remember from the ppc archived forum, is that video for linux on B&W's should be connected to the TOP slot, and not the bottom. While a video card connected to the bottom slot works with mac-os, only the top slot works with Linux. At least that's what I read - maybe something to try in case you have two cards, or the card is in the bottom slot.

THE GRAPHICS CARD IS IN THE TOP SLOT AND IT IS THE ONLY I HAVE A WIRELESS ADAPTER IN THERE A I WAS HOPING TO GET THAT GOING IF I CAN GET IT TO BOOT

This is definitely going to be an adventure. 


YES AS YOU LINUX/UBUNTU GUYS SAY LEARNING ALL THE TIME!!!!!

AS mkvnmtr SUGGESTED DOCUMENTING I WOLUD LOVE TO IF HAVE SUCCESS I AM WAITING FOR MY FATHER TO TRY AN APPLE CDROM IN HIS 2ND G3 TO PROVE THE POINT. CAN IT BE DOCUMENTED AND IF SO HOW DO I DO IT ?

THANX AGAIN GUYS 

chris

---

### Post by mkvnmtr on 2009-01-04
Sure you can document it. Just write up what you have done annd how you got it to work. There is a wiki at the site ppclinux that would love to have your input on installing on your mac. In fact on all the macs your father has as well. {http://www.ppclinux.info/} is the page. The link is in the bottom of streams posts also.

---

### Post by chrisginger26 on 2009-01-05
Hi mkvnmtr

Thanx for the link I will document everything as soon as I can get hold of a genuine drive my fathers a bit busy at the mo but as soon as we can confirm everything then I will do a post 

thanx again 

chris

---

### Post by chrisginger26 on 2009-01-18
Hi Guys 

I don't kknow if anyone is still looking at my thread but I have just managed to get hold of the genuine ape cd rom drive and I atill cannot get this to boot.

I get exactly the same error message as the start of my thread and also in open firmware I get 

boot cd:,yaboot MAC-PARTS LOAd(non- interposed)not support load-size=0 alder32=1

load size is too small

I have tryed reseting the nv-ram and pram on several ocassions and this has no effect what else can I try as I do not have a another computer running linux to set up a usb stick.

can any one help can I buy a bootable ubuntu powerpc stick or something don't no what to do next and almost at the point of giving up I thought the cd ro drive would sort the problem

thanx again guys 

chris

---

### Post by chrisginger26 on 2009-01-18
Hi Guys 

Ok I'm going to an extreme now would the  g3 boot if i installed the hard drive in my imac and ran the installation on there then put it back in the g3 ?

---

### Post by mkvnmtr on 2009-01-18
It seems you have a good attitude. I have one more idea. There is a minimal install disk. I just used it today to install on a acer laptop with limited memory. I was in a hurry and you cant buy ram on Sunday.I one before used the minimal instal on my G4. It is only 14Mb. On both it booted up great and detected the hardware with no problems.It takes so little time to download I would give it a try. Google Ubuntu minimal install and you will find it and some tutorials on what to do if it succeeds.

---

### Post by chrisginger26 on 2009-01-19
Hi mkvnmtr

I have downloaded the 8.04 minimal cd will burn it slow and see it makes a difference.

Thanx again 

chris

---

### Post by chrisginger26 on 2009-01-19
Hi mkvnmtr

Just tryed the mini iso of 8.04 burnt it at 8x through disk utility in mac (the apple cdrom in the g3 is 24x read speed) and I still have the same problem I am starting to think that it is something to with the version of the open firmware 3.0.0 ? my dads is newer and it will boot to a live cd on that do you think that is possible ?

thanx again

chris

---

### Post by pxwpxw on 2009-01-19
> **chrisginger26 said:**
> Hi mkvnmtr

Just tryed the mini iso of 8.04 burnt it at 8x through disk utility in mac (the apple cdrom in the g3 is 24x read speed) and I still have the same problem I am starting to think that it is something to with the version of the open firmware 3.0.0 ? my dads is newer and it will boot to a live cd on that do you think that is possible ?

thanx again

chris

you could probably do a network install from usb stick -

[http://ubuntuforums.org/showpost.php?p=6574837&postcount=9](http://ubuntuforums.org/showpost.php?p=6574837&postcount=9)

---

### Post by mkvnmtr on 2009-01-19
The minimal install disk gives you a network install. You start with less than 14Mb. and then install everything from the repositories. It is nice there are no updates when you finish.
But the problem you are having is beyond me.In mac is not there something called target disk install where you install from another machine. Maybe something like that would work. I do not know maybe it is just for later models. Gee good luck.

---

### Post by chrisginger26 on 2009-01-21
Hi Guys

Heres an update !!!

Having finaly got hold of a mac os 8.6 retail start up I found that I could not boot from that either!

This made me think that there was something wrong with the hardware on the board as I have tryed several different drive and copies of cd etc!

I then went back to reseting the pmu which I thought would happen by removing the battery but actualy what did it was these instructions (at the bottom of the page is a diagram of where the button is on the mother board)[http://support.apple.com/kb/HT1939](http://support.apple.com/kb/HT1939) 

After doing this mac os 8.6 will now boot and install.

BUT UBUNTU IS STILL GIVING ME THE SAME THING ON START WITH CD !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

So I figure now I have the original firmware that came with the machine so I was going to try updating that as there is one update for the g3 and one for 24x cdrom drives.

The reason I got to this is a friend at work said they installed os x to a g4 when it was(os x to try it new) and they could not then reinstall back to os 9.1 which leads me to believe that this is some thing to do with mac os x updating the firmware in some way and this stops any thing else booting on older hardware perhaps ???? maybe an apple thing to force an up grade of hardware perhaps ????

thanx again guys 

chris

---

### Post by tiresia on 2009-01-21
When you try to boot ubuntu, do you still get the same message 'load size is too small'?  If so, start again the computer and access Open Firmware (cmd-opt-O-F)
```
printenv
```
Which values you have for load-base and for real base?

---

### Post by chrisginger26 on 2009-01-21
Hi tiresia

I did as you said in openfirmware and the results are below hope I got it right

Apple Power mac 1,1 1.0b4 11/06/98 at 9.04.50

real base    -1   -1
real size     -1   -11
load base 0x800000     0x800000


what does this mean  ????

thanx again 

chris

---

### Post by tiresia on 2009-01-21
As I understand this: those values show where OF look for the the file to boot and how much big it should be. Do not change those parameters in OF 3 (they were fixed from Apple), because you could make you system unbootable (well, it is already unbbotable). 
Also because they look OK (I think you mis-tipped the real-base, it should be -1 -1)

Anyway, can you please just try now```
boot cd:\yaboot
```
Can you boot yaboot? Or try following:
```
 boot cd:,\install\yaboot

```

---

### Post by chrisginger26 on 2009-01-22
Ok Guys 

I've cracked it I just did the G3 Firmware update from 1.0b4 to1.1f4 and after that the system booted to yahoo bootloader the 6.06live cd failed but I have read that that is the case with the live cd on my machine I am going to download the alternate cd of 6.06 as I also had a little trouble with 8.10alternate it could'nt find the cd drivers and it asked for a floppy with it on but the g3 dosen't have one I wasn't sure about how to manualy add it. 

thank again guys 

chris

---

### Post by avtolle on 2009-01-22
Chris, on 8.10 alternate; when you get that message, go to another virtual terminal (Ctrl+Alt+F2) and hit enter to activate it; then type in ```
sudo modprobe ide-scsi
```and when the prompt returns, hit Ctrl+Alt+F1 to return to the original screen; "Yes" should be highlighted, click on it, and (based upon my experience) the installation should proceed.

---

### Post by chrisginger26 on 2009-01-24
Hi avtolle/guys

I've tryed "when you get that message, go to another virtual terminal (Ctrl+Alt+F2) and hit enter to activate it; then type in
Code:
sudo modprobe ide-scsi
and when the prompt returns, hit Ctrl+Alt+F1 to return to the original screen; "Yes" should be highlighted, click on it, and (based upon my experience) the installation should proceed."

on 8.10 alternate and I managed to get it to install but on the first boot I had an issue with graphics and the ubuntu telling me that it needed to run in low graphics mode for this boot only it did and when I reached the desktop none of the apps would work and the hard disk was working overtime.

I did not expect to run the latest and greatest ubuntu (as the G3 is fairly underpower for 3d graphics ,compiz fusion,etc)  so on this note I did not try to go any further with 8.10.

So I downloaded the alternate cd for 7.10 xubuntu and the install ran fine up untill it failed on installing finding software and installing at this point I asked it to do it again and it completed the instalation BUT !!!

On first boot I got this what do I do next ???

"loading, please wait......

Kinit:name_to_dev_t(/dev/hdc4)=hdc4(22,4)
Kinit:trying to resume from /dev/hdc4
Kinit:No resume image, doing normal boot 

Ubuntu 7.10 garage tty1

garage login :[143.379465]pmac_zilog 0.00013000:ch-b: irda_setup tyimed out on get version byte 

[143.443986]pmac 0.0001300:ch_d: irda_setup timed out get version byte 
[144.166925]pmac 0.0001300:ch_d: irda_setup timed out get version byte 
[144.385557]pmac 0.0001300:ch_d: irda_setup timed out get version byte 

at this point the machine just sits there whith hd doing overtime again!!!

I tryed pushing enter after waiting about 20minutes and got 

Ubuntu 7.10 garage tty1

garage login :-

thanx again guys 

chris

---

### Post by chrisginger26 on 2009-01-24
Hi Guys 

Am I stabbing in the dark or is this a graphics issue and do I sort by setting the xorg.conf  file up wht should the settings be ??

Have come so far with this and stuck at the last herdal

thanx again 

chris

---

### Post by chrisginger26 on 2009-01-24
Hi Guys 

Finaly sucess I can now boot into the gnome and everything is working except the internet I think the wireless is out of range !!!!

I did it with the 6.06 live cd just did'nt realise I needed to wait a while after raid services failed on start up it dosen't actualy mean that the install has failed it just means that one thing has failed.

So next I've got to bring it indoors and connect to my network and install the relevant repoistories for mp3's etc 

thanx again for all your help 

chris

---

