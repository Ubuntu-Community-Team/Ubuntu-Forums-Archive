---
title: "howto remove winxp ?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-11-01
my girlfriend has given me permission to install ubuntu on her HP laptop, that is currently running winxp! i want to completeley remove micr0$haft, but the recovery boot disc does not give me this option - only repair or install. i was freed from wind0ws 6 months ago & never looked back, hence i have little time for this problem.
any idea's people?  thank you :KS

---

### Post by akiratheoni on 2007-11-01
Just install it over the whole disk and it will get rid of XP.

---

### Post by Bakon Jarser on 2007-11-01
if you're getting rid of xp altogether then there is no need to uninstall it.  you can install ubuntu (or any other os) right over the top of it.

make sure you back up all the files you need first.

---

### Post by illbashu on 2007-11-01
1) download the ubuntu iso make an live cd 
2) put it in
3) follow instructions
4) when u get to the pratition part select use whole drive and it will format everything and install ubuntu

---

### Post by jon zendatta on 2007-11-01
thanks for the speedy replies, i wondered if that may work & now i know..now to impress the girlfriend

---

### Post by jon zendatta on 2007-11-01
ok so i'm as far as 10 minutes into booting the Ubuntu cd, got the prompt etc but now i'm staring at a blank screen - seems to be slower than when i installed on a clean hard drive. would this be because of wind0w$ beneath? thanks

---

### Post by dRock1286 on 2007-11-01
theres a program out there called window washer...supposed to completely format a windows harddrive or something like that...i've never used it but you might wanna try that...


edit::nevermind that.  I'm looking for what the program is really called....

---

### Post by ghostwalk.with.me on 2007-11-01
Although this is not necessary in order to install ubuntu, you might want to use a utility like Kill Disk to get rid of any detritus left over from the xp installation. Although, I've installed ubuntu over a  windows partition with no incident, I've noticed that it there's fewer errors on the hard disk if it's scrubbed clean beforehand with such a utility.

---

### Post by dRock1286 on 2007-11-01
if you want to pay money (which you probably don't) I found this...  [http://www.whitecanyon.com/wipedrive-erase-hard-drive.php]("http://www.whitecanyon.com/wipedrive-erase-hard-drive.php").

I'll look for a more free version of something...

---

### Post by jon zendatta on 2007-11-01
yes i would prefer not to pay for it. need a dos self-destructing command or something! when i used ubuntu cd, halfway through(pre-gui) the screen becomes grey. you'd think they'd($) have the decency  to offer uninstall.

---

### Post by Bakon Jarser on 2007-11-01
Ha ha!  You just reminded me of my first job.  In an IT department wiping hard drives with a DOS bootdisk with a program called wipe added to it.

You can get a dos bootdisk here.

[http://www.allbootdisks.com/disk_contents/dos.html](http://www.allbootdisks.com/disk_contents/dos.html)

Not sure if this is the wipe program I used back in the day but it's free and looks like it will fit on a dos boot disk.  

[http://www.freedownloadscenter.com/Utilities/File_Splitting_Utilities/Free_Disk_Wipe.html](http://www.freedownloadscenter.com/Utilities/File_Splitting_Utilities/Free_Disk_Wipe.html)

good luck

---

### Post by jon zendatta on 2007-11-01
but it s a fresh install of winxp that hasn't been touched yet, so there is nothing to clean anyway- that OS just needs to be removed as my Ubuntu disk can't overwrite it.

---

### Post by daengbo on 2007-11-01
The Ubuntu disk can completely wipe the install. Just choose "Use Entire Disk." The CD and resulting installation won't be any faster or slower with/without Windows on the disk. The CD doesn't use the disk at all while booting.

Make sure you have enought memory and check the hardware compatibility before starting.

---

### Post by jon zendatta on 2007-11-01
windows still here! i have checked quality of cd. problem is it gets halfway through live install then the screen goes blank. so i tried safe mode, which initially says "failed to start the X server ,would you like to view the X server output."   but i,m lost as to what commands to enter. next i get "the X server is now disabled, restart GDM when it is configured correctly.??

---

### Post by maybeway36 on 2007-11-01
Use the Alternate CD, I guess.

---

### Post by Adam_GUI on 2007-11-01
Start>Run>cmd
format C:\
Yes

That should nuke out XP pretty good.
From there your install should be fine.

---

### Post by Rich78 on 2007-11-01
Just boot using the live CD and use the partition manager to reformat the hard drive.  It should be pretty straight forward.

You could also partition the hard drive to dual boot it if you felt so inclined.

---

### Post by Paqman on 2007-11-01
If you're having trouble completing the install i'd advise against completely wiping out XP unless you've got an install CD and valid code for it. You don't want to be left without a working OS unless you have a thing for expensive paperweights (and arguments with your girlfriend)

You can always delete the XP partition after you get Ubuntu installed.

---

### Post by Rich78 on 2007-11-01
Agreed, maybe even just play with the Live CD for a bit to get used to Ubuntu.  

If you're new to Ubuntu or Linux in general I'd advise trialling the Live CD first, not everyone prefers Linux and your girlfriend may not thank you for removing Windows if she doesn't get on with it.

---

### Post by jon zendatta on 2007-11-01
i will look into allboot shortly thanks just gotta work out what version of dos this is.

i tried that 'format C:\'  invalid command.

like i've said i'm using the live install cd but i don't even get as far as the GUI after the disk has checked computer hardware/etc (ok). so i tested a fedora core cd & i get the same problem. so at this stage i can't even run live cd option, that is why i think window$ is the problem. :confused:

---

### Post by ukripper on 2007-11-01
Can you post full spec of your Girlfriend's HP laptop including model number.

Do you get any error after the hardware check?

---

### Post by jon zendatta on 2007-11-01
hp pavilion
dv4201tx
intel pentium m processor 760(2 ghz)
intel pro/wireless 2200 802.11bg wlan & bluetooth
80gb(5400rpm)
wxga high definition
512mb ddr2 sdram
ati mobility radeon x700 with 128mb ddr
etc

help please

---

### Post by ukripper on 2007-11-01
what happens when your type ```
startx 
```after hardware check? Problem seems to be  ati drivers

---

### Post by jon zendatta on 2007-11-01
vesa(0) no matching modes
screen found but none have a usable configuration

failed server error:
no screen found
X10: fatal 10 error 104 (connection reset by peer) on X server ":0.0" after 0 requests ( 0 known pr0cessed) with 0 events remaining.

ok. now i must go to work, thanks in advance for any help people.

---

### Post by Rich78 on 2007-11-01
Having Windows installed will have no issue with booting from a Live CD.

Sounds very much like a driver issue but strange to not be able to even use the Live CD.

Which version of Ubuntu are you trying?  7.10?

Maybe try 6.06 LTS?

I know you said you tried Fedora which really points to a hardware issue.

Does Windows still boot up ok?

---

### Post by ukripper on 2007-11-01
> **jon zendatta said:**
> vesa(0) no matching modes
screen found but none have a usable configuration

failed server error:
no screen found
X10: fatal 10 error 104 (connection reset by peer) on X server ":0.0" after 0 requests ( 0 known pr0cessed) with 0 events remaining.

ok. now i must go to work, thanks in advance for any help people.

Looks like xserver-xorg  needs to reconfigured with correct resolution but for time being try booting using safe boot mode.

When you reboot your machine, at boot screen select option  Safe boot.

---

### Post by jon zendatta on 2007-11-02
i was attempting to install  fiesty as that's what i'm comfortable with. ok i try safe mode shortly..surely it ain't a driver issue as any other cd  works fine.this is doing my head in.

---

### Post by jon zendatta on 2007-11-02
no i tried safe graphics mode this morning, which i noted in a previous post there were issues with xserver.   kill bill

---

### Post by ukripper on 2007-11-02
Does it imply, it is  working in safe mode?

---

### Post by jon zendatta on 2007-11-02
it does not imply its working in safe mode - just get the the X sever is absent message then i'm staring at a command prompt, unsure what i should type(in fact no idea).
yesterday i went into computer repair shop but the technician couldn't understand why i'd want remove window$, but he also wondered if it could be a driver issue.
the thing is the window$ bootable cd functions correctly, just not linux.

---

### Post by ukripper on 2007-11-02
> **jon zendatta said:**
> it does not imply its working in safe mode - just get the the X sever is absent message then i'm staring at a command prompt, unsure what i should type(in fact no idea).
yesterday i went into computer repair shop but the technician couldn't understand why i'd want remove window$, but he also wondered if it could be a driver issue.
the thing is the window$ bootable cd functions correctly, just not linux.

try this command :
```
sudo dpkg reconfigure xserver-xorg
```

Select VESA

 and while follwoign steps at some point change following

HorizSync       31-80
VertRefresh     55-90

then after reconfigured:

at terminal type command:
```
startx
```

---

### Post by jon zendatta on 2007-11-02
big shouts to Ukripper for all the replies & assistance  but now it cannot boot from win-cd either, as it could up till this morning..i guess this means your earlier diagnosis of sick driver, could be the one. i'll go to repair man when shop opens as this is weekend & may not have answer till monday.
thanks again i'll let you know the outcome. :confused:

---

### Post by wpshooter on 2007-11-02
Jon:

Please get and learn how to use the KILLDISK program at [www.killdisk.com](www.killdisk.com) and then WIPE that drive completely CLEAN and then try to install Ubuntu from your LIVE CD.  Make sure that the first thing you do when you boot to the LIVE CD is to check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

If you still can not get a successful installation of Ubuntu after doing the above then please download and and burn the ALTERNATE (text based) version of Ubuntu and try the same procecss as described above to see if you can get a successful installation.

Good luck.  Let us know how it goes.

Thanks.

---

### Post by ukripper on 2007-11-03
Jon I completely agree with above post you should try killdisk first it is not difficult to master at all.. just follow steps given in the link.

---

