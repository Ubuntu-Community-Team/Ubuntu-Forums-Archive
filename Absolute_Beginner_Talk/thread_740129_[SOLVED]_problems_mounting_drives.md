---
title: "[SOLVED] problems mounting drives"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by bryncoles on 2008-03-30
hi folks. Im running a packard bell easynote r4360 with gutsy gibbon on it, and quite enjoying myself in the process.

but this weekend, its developed an odd behaviour with the dvd rw drive. basically, it seems to be randomly unmounting it  -and telling me i dont have a dvd rw drive anymore.

the drive is then rendered unreadable until i reboot. making matters worse, one my laptop decides that it cant mount the dvd drive, it also refuses to mount my external hard drives. all i want to do is burn some data files to dvd, but its looking like this isnt so simple a task!

can anyone help me investigate this problem? find out why my dvd drive keeps unmounting, and how to remount it when it does, and better yet, stop it unmounting in the first place?

bryn

---

### Post by Michael.Godawski on 2008-03-30
can you please post the result of the terminal commands
```

cat /etc/fstab
```

---

### Post by mgmiller on 2008-03-30
A quick way to try remounting it is:
```
sudo mount -a
```
This assumes it's an internal drive that is mentioned in your /etc/fstab

---

### Post by bryncoles on 2008-03-30
hi guys! thanks for the speedy responses. is 'sudo mount -a' a global command then? ill try that next time it goes down. the drive is currently mounted (fingers crossed - i dont want to put the curse on it / give it ideas!)

heres the output requested:

bryn@bryn-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=81b72f41-fdaf-4bc5-9b40-d7e712e6934e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f82ba6db-46e1-44e3-b07e-b41cdb3e7186 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

#a line i added: to stop shared memory allowing files to be exectuted.
tmpfs     /dev/shm     tmpfs     defaults,noexec,nosuid     0     0
bryn@bryn-laptop:~$ 

oooh - i forgot i added that last line... should i try removing it....?

---

### Post by Michael.Godawski on 2008-03-30
this line you added, did you invent if for yourself :) or did you follow a guide?

just being curious. no idea if this can interfere somehow with the DVD drive

---

### Post by bryncoles on 2008-03-30
i dream of the day when i can invent lines of code like that! no - i found it in a guide. just dont ask me which one! it was somewhere here, in the ubuntu forums though, and it certainly seemed like a good idea at the time!

---

### Post by Michael.Godawski on 2008-03-30
you can always comment a line out and see if the change well... changed something for the better :)

---

### Post by mgmiller on 2008-03-30
> is 'sudo mount -a' a global command then?

Yes.  It will cause any drives mentioned in your /etc/fstab to be remounted.
Since your DVD drive is mentioned there;
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```
it should remount it.

> oooh - i forgot i added that last line... should i try removing it....?

You could just try commenting it out by putting a # at the start of the line.

---

### Post by bryncoles on 2008-03-30
ah, good thinking. i just tried that, and the problem reoccurred! so its not my editing thats caused a problem. also: sudo mount -a didn't seem to resolve the issue either. 

i think i can smell another reboot coming my way!

i tried putting a dvd into the drive - the simplest way i can think to check to see if my drive is working. the drive whirls around, then does nothing. booting gxine (my favourite dvd viewing thing), it tells me theres an error reading from dev/dvd.

K3b also tells me theres no cd/dvd drive.

---

### Post by Michael.Godawski on 2008-03-30
Can you please post the result of 

```
lspci 
```

to identify your dvd rom. Perhaps there are some compatibility issues with your current model and linux.

---

### Post by bryncoles on 2008-03-30
no sweat - here it is

bryn@bryn-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
bryn@bryn-laptop:~$ 


s'funny, i installed this buntu in january and the dvd drive used to work fine.

---

### Post by bryncoles on 2008-03-30
well, ive also noticed that i can at least still boot from a live cd... so the drive is working. just not in ubuntu!

---

### Post by mgmiller on 2008-03-30
Just for fun, lets try making a small change to your /etc/fstab.
first, make a backup of the one you have:
```
sudo cp /etc/fstab fstab.backup
```

Next, open the file in gedit:
```
sudo gedit /etc/fstab
```

go to the line that says:
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

and change it to:
```
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

save the file and try the:
```
sudo mount -a
```

and see if it works.  (Maybe try a reboot too.)

If things get fracked up, change it back by doing:
```
sudo cp /etc/fstab.backup fstab
```

good luck....:popcorn:

---

### Post by bryncoles on 2008-03-31
now thats interesting.... i changed the code this morning, after seeing my dvd rom drive still wasnt loading. i put in the 'sudo mount -a', and no effect. after rebooting though, my dvd rom is back, and reading disks!

now im curious, why would this change make a difference? why would my dvd drive work for almost three months before conking out?

ill give it a few days, and see if my dvd drive works consistently (it twice has unmounted after about an hour). if we've sorted the problem, then ill mark as solved!

right now im very happy though! thanks!

:-D

---

### Post by mgmiller on 2008-03-31
You're welcome.

It occurs to me after all of the above, I never asked what kind of drives they are.  Meaning SATA, PATA, etc.  Are you sure the jumpers are set correctly (if PATA) on the drives?  

I have seen optical drive weirdness start when the jumper on a hard drive is set to master and the optical drive is set to cable select.  My brother bought a Sony desktop that came that way with WinXP and it worked fine for a few months also and then started losing its optical drive for "no reason".  I set the jumpers to master and slave and it has been fine for the last few years.

If they are both PATA and are on the same cable, make sure the HDD is master and the Optical drive is slave.

If the optical drive is on its own cable make sure the jumper is master.  Most optical drives come with the jumpers set to cable select by the factory, so you need to actually look if you haven't already.

Lastly, if all else fails, see if there may be a firmware update for the optical drive &/or a BIOS update that mentions your specific problem from the mobo maker.  (I wouldn't mess with the BIOS update if everything else is working properly and the update does not specifically mention your problem.)  Sometimes it makes a difference.

If you would like to thank me "officially", click the little 5 pointed star to the left of the quote button in the lower right corner of one of my posts.  I get a nice Ubuntuish feeling when someone does that.

---

### Post by bryncoles on 2008-03-31
cool. thats good stuff to know. 

how do i check to see if its sata or pata? how would i check the lead? do you mean physically take the back off and look with my eyes? i wouldnt even know what i was looking at / for! and how would i set one to master, and one to slave? 

incidentally, dvd hasnt unmounted itself yet! :-D

*edit*

phooey! drive has unmounted! 'sudo mount -a' still seems not to do owt...

rebooting hasn't helped either... though i have noticed that the naming convention has changed. when the drive is mounted, its called something like 'cd / dvd +- rw drive'. when its failed to mount properly, its called 'cd-rom 1'. 

is that significant?

---

### Post by mgmiller on 2008-03-31
> how do i check to see if its sata or pata? how would i check the lead? do you mean physically take the back off and look with my eyes? i wouldnt even know what i was looking at / for! and how would i set one to master, and one to slave?

Good questions.  

You will have to take the cover off and get your eyeballs in there.  You may need to physically remove a drive to examine it.
Make sure the machine is turned off and if your power supply has a rocker switch on it, turn that off too.  If it does not have a rocker switch, unplug the power supply from the wall.  Once the cover is off, ground yourself by touching a part of the metal case before touching anything else inside the case.

Look at the pictures below, the first one shows 3 cables.  The red cable on the left is a typical SATA cable.  It is possible to see them in other colors.  The Middle grey cable is a typical PATA (IDE) ribbon cable and the Black cable on the right is a more expensive "round type" PATA (IDE) cable.  The last 2 function the same, note the large connector.  The SATA has a very small connector.  One other difference is the SATA cable will only connect to one drive, the PATA cables can connect to either 1 or 2 drives, depending on its having a second drive connector.

The next picture is the back of a typical DVD rom drive.  You can see the wide area where the PATA cable would plug in.  to the left of it is a smaller area where the jumpers are.

The 3rd picture is a close up of the jumper area with the jumper pulled out slightly to enhance clarity.  You can see the markings for master, slave and cable select.  In this case the jumper is on the slave setting.  Sometimes the diagram for the jumper settings is printed on a lable on the top of the drive, rather than being embossed on the back.

I did not include a picture of a hard disc, because the connectors will vary with the brand, but if it is PATA, it will have a wide connector for the data just like the optical drive.  Also, the jumper positions are not so cut and dried.  Sometimes they are ase easy and obvious as on the optical drive, sometimes this is not the case.  If you tell me the brand of the drive, I can tell you how to set the jumpers.

If one or both of the drives are PATA (use the wide connectors), Then you should check and adjust the jumper positions accordingly.  If both drives are SATA, there are no jumpers to adjust and your problem may be in the BIOS for the mobo. 

Let me know how your hardware is configured & I can guide you further.  It makes a difference if both drives are on the same cable or on different cables.
:popcorn:

---

### Post by bryncoles on 2008-04-01
ok cool, i shall have a look and a play around with that when i get home from work. just to be clear though, i am using a laptop computer... so this advise still applies, yes?

---

### Post by mgmiller on 2008-04-01
Sorry, I didn't know you were on a laptop.  
I'm afraid the info I gave in the last post does not apply to laptops.

Have you tried removing and reinstalling the optical drive a few times to clean the contacts?  It should pop in and out easily by sliding a little tab on the bottom somewhere.

---

### Post by bryncoles on 2008-04-01
probably my fault about not knowing its a laptop - i should have been clearer! i havent tried tried reinstalling the drive - its something that never occured to me ha ha! im guessing i still need to take the bottom off the machine (ive just had a look at the underside and theres no obvious way to slide anything out). ive never installed / removed hardware myself before... this will be breaking new ground (and hopefully not my laptop!)

if its any help to you helping me, the laptop is:

[http://support.packardbell.com/uk/item/index.php?m=home&pn=PB17B00201](http://support.packardbell.com/uk/item/index.php?m=home&pn=PB17B00201)

but its not the original dvd drive anymore. that broke about a year and a half ago and was replaced. but the current drive always worked under ubuntu before. 

is there anything else you can think of that i should mention?

oh - and let me just say i really am appreciating your help! ;-)

---

### Post by mgmiller on 2008-04-01
I took a quick look at the documentation for your laptop, but they don't mention optical drive removal.  

On laptops, this **_usually_** doesn't require any tools or even opening the case at all.  Somewhere near the drive, on the side or bottom is a little sliding switch that releases the drive and it slides right out.  

That being said, some laptops require a disassembly to remove/replace the optical drives.  These machines are built like Chinese puzzles.  They are all different and some can be tricky to open up. 

You mention the drive was replaced in the past.  It is possible the new drive has failed as well.  Who did that work?  Can you return the laptop to him/her for additional service?

---

### Post by bryncoles on 2008-04-01
its a local computer shop who did the work. i could take it back to them and get them to have a look... i have the laptop as a dual boot with windows xp (i never got round to removing that), so i could also try booting in that and see if it works there. think is, sometimes the drive reads, and sometimes it doesnt! so it could work in windows but still be dodgey....?

*edit*

just booted it into windows, and there was no dvd drive there either. does that smell like a dodgey drive then? (ive booted back into 'buntu to type this ;-))

*edit 2*

just booted into windows again, and the drive was there. then booted back into 'buntu, and the drive was there again too. wonder for how long till it un-mounts?

the only pattern i can think of at the moment is that each time before the drive reappears, i pop into fstab, change something, change it back then reboot. 

significant.....?

*edit 3*

got home from work, rebooted in windows and then 'buntu again and no drive present in either. took it physically out of the computer (theres a little screw you take out then it just oozes out!) and put it back in again to no avail!

---

### Post by mgmiller on 2008-04-02
The fact that it also fails in Windows leads me to believe it's a hardware problem.  The last thing I would try before returning it to the repair shop would be to use a cleaner on the contacts of the drive when you remove it.  Since it seems to be fairly easy to slip the drive in and out, here's what I would do...

Obtain a product from Radio Shack called Deoxit.  This consists of 2 spray cans, one has a cleaner and the other a preservative for gold plated contacts.
Here is a link to the product:
[http://www.radioshack.com/product/index.jsp?productId=2104746]("http://www.radioshack.com/product/index.jsp?productId=2104746")


Remove the drive and spray a little of the cleaner on the exposed contacts on the drive and insert/remove it a few times.  Next repeat the procedure with the  gold contact protector.

Screw the drive back in and keep your fingers crossed.

I live on an Island surrounded by salt water and everything corrodes here.  
Don't worry about getting this stuff inside the computer. 
I have used it extensively to clean the contacts for the connector of my keyboard inside my lap top and also on memory and pci cards inside various desktop computers.  It seems microscopic corrosion can take place even on gold plated contacts and this product removes it.  I can tell you it's the only thing that got my laptop going again and it fixed several instances of intermittent hardware things like "bad memory" that I used to get on desktops.  I have used it to stop scratchy noises on telephones by spraying the contacts of the phone cords.  I have used it to clean the contacts on chargers for TV remote control or cordless phones that seem to require jiggling or lots of on and off to get them to charge, you know the type, they just lay in a cradle and there are exposed gold contacts.

If you still have the same problem after using the Deoxit kit, then the next step would be to replace the drive.

Good luck.

---

### Post by bryncoles on 2008-04-02
ok, thats cool. ill try cleaning the contacts, and if i meet no joy ill see if i can find a new drive - a quick squint online reveals they're about £50 a pop, which isnt so bad (its not the price of a laptop!)

whatever developments happen, ill post back so you know whats happened.

---

### Post by bryncoles on 2008-04-04
well, i cleaned the drive, yesterday, and it worked yesterday. but today, while it shows up in the computer with the correct lable, i get the message 'invalid mount option when attempting to mount the volume'. 

i googled, and found this thread 'http://ubuntuforums.org/showthread.php?t=650697', which seems to think its an endemic problem, and blames vista. for me, discs that previously worked in ubuntu or were burned in ubuntu are not working though. 

i havent looked to see if its working in windows yet though...

typing 'sudo mount -t udf /dev/cdrom/ /media/cdrom0' as suggested in the other thread (im trying not to double post here)

gets me 

'mount: block device /dev/cdrom is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so'

does that mean anything to anyone?

scratch that - the drives back to 'cant mount because it doesnt exist', and doesnt show up in windows either. think it must be duff then! phooey!

---

### Post by mgmiller on 2008-04-04
Sorry to hear that.  In my opinion, you probably have a bad drive.  I assume it also acts erratically in a live CD session?

It would be interesting to see how it is listed in /etc/fstab in the live session and then making your actual install look the same,  but I suspect, replacing it is probably your best bet by now.

---

### Post by bryncoles on 2008-04-05
it did act equally erratically in a live cd session - sometimes it would boot, sometimes not! i thought about the live session fstab too, and wondered if changing my normal fstab to read the same would help. i tried it, and it didnt help ha ha ha!

so today i bought a new drive, from my favourite local computer shop (M and M computers in case anyone from lancaster, uk is reading!). Its a sony NEC dvd plus/minus rw blah blah blah etc!

with this drive in, all my problems have gone away - it works fine, reads dvds and data cds fine. so i think it was a duff drive after all, though i appreciate your help in ruling out software issues. and as i always say, i have learned a lot about how the OS works, which leaves me more capable for the future!

actually, there is one or two things left now which need fixing. now when i go to 'places -> computer', it lists my dvd drive as 'cd-rw /dvd +- drive', and this is the one which mounts any discs which i put in. it also lists another, non-existent drive as 'cdrom 1', this one doesnt exist! how do i get rid of the false positive? 

also, while vlc player, k9copy and k3b both recognise the cd/dvd drive, amarok and gxine (my preferred apps) dont! is it just a matter of reconfiguring them to tell them the new file path for the new dvd drive?

the fstab currently looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=81b72f41-fdaf-4bc5-9b40-d7e712e6934e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f82ba6db-46e1-44e3-b07e-b41cdb3e7186 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#
#a line i added: to stop shared memory allowing files to be exectuted.
#tmpfs     /dev/shm     tmpfs     defaults,noexec,nosuid     0     0

---

### Post by mgmiller on 2008-04-05
I'm glad the new drive is working out.  Hopefully, this one will be more reliable for you.

> actually, there is one or two things left now which need fixing. now when i go to 'places -> computer', it lists my dvd drive as 'cd-rw /dvd +- drive', and this is the one which mounts any discs which i put in. it also lists another, non-existent drive as 'cdrom 1', this one doesnt exist! how do i get rid of the false positive?
The first thing I would try is changing your /etc/fstab back to what it was before.  Then do a reboot just to be sure.

> also, while vlc player, k9copy and k3b both recognise the cd/dvd drive, amarok and gxine (my preferred apps) dont! is it just a matter of reconfiguring them to tell them the new file path for the new dvd drive?

After the reboot, if your amarok is still giving you trouble, start amarok and go to Settings > Configure Amarok > Engine.  Then on  the right side you will see the audio CD configuration.  In default device, change it to whatever you need it to be.

I don't know about gxine, but I bet there is a similar configuration option in it somewhere.

---

### Post by bryncoles on 2008-04-06
winner! i put the fstab back to how it was, and now the false positive in the 'computer' folder is gone!

after a bit of faffing about i found the path i needed to put in to get gxine and amarok recognising cds and dvds respectively - i did that by opening one of the programs that still recognised the dvd drive and seeing where it looked. turns out that it was the first entries in the fstab - '/dev/scd0'. 

now everything is working properly again, so thank you for all your help!

---

### Post by mgmiller on 2008-04-06
:lolflag:

Glad I could help.

:guitar:

---

