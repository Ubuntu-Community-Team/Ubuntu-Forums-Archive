---
title: "installing ubuntu on mac g3 tower (a little bit of a different isue)"
date: 2011-03-15
forum: Apple Hardware Users
---

### Post by yesfullfull man on 2011-03-15
OK i didn't see this on the forums but if i missed it please direct me to it.
also i am not good with grammar and spell please bear with me.

OK now i have a g3 tower and I'm sick of the os crapping out on me. so i wanted to put ubuntu on it since I'm pretty sure it works. now here's my problem i put the cd into the disc tray(after putting ubuntu on it of corse) and when i try to boot it up holding down all the different key comboes thats supost 2 work and it would eject it back out. and to me that means it can't read it so i tried it again getting anoyed and this time when it ejected i pushed it back in and held the option key down and yes finaly ubuntu (desktop version 10.04) then it says an error for some panic kerrnal so after dealing with hours of this im pissed so i download the alternate install. so once i get that working i get to the partitioning stage. it does the partition i think. it shows the loading bar then it goes to text going up like its loading stuff and it says reset in 180 second on the bottom. so when it reboots it the cd ejects i put it back in and it loads the cd again starting from the beginning so i get stuck in a loop. so what do i do or what am i doing wrong? i'm getting sick of this . oh and i cant install mac osx back on it because both hard drive's or not showing up on it.

---

### Post by snafu006 on 2011-03-15
So when you put the CD in and hold option key and a list comes up you typed install right? and then you fallow the install of setting up your Username And Password.

 Then the partitions comes up and asks if you want you use the full harddrive you tell it yes and then install of ubuntu shound come up after the install the computer should restart.

 **So this is my question do you see yaboot come up? its the second black screen after the computer restarts**

---

### Post by yesfullfull man on 2011-03-15
well first off if i hold option, c, or the conrtrl alt delete it ejects it but if i put it back in before it boots up mac osx and hold one of them down it will boot up the cd. also it doesnt get to the install. it gets to the partitioning and the little loading bar gets to about 50% then brings up a weird screen with text and what i noticed is it starts under it and looks like its loading or installing when i havnt got there yet . its not like an error. then it says reboot in 180 second on the very bottom. and it reboots and i have to go through the cd ejecting again then when i get to the cd it starts all over again(and yes i did type in install).

---

### Post by snafu006 on 2011-03-15
> **yesfullfull man said:**
> well first off if i hold option, c, or the conrtrl alt delete it ejects it but if i put it back in before it boots up mac osx and hold one of them down it will boot up the cd. also it doesnt get to the install. it gets to the partitioning and the little loading bar gets to about 50% then brings up a weird screen with text and what i noticed is it starts under it and looks like its loading or installing when i havnt got there yet . its not like an error. then it says reboot in 180 second on the very bottom. and it reboots and i have to go through the cd ejecting again then when i get to the cd it starts all over again(and yes i did type in install).

Just hold the option key when the computer is loading then place the cd in and wait for it to pop up thats ezer. Now you are trying to install 10.04 PPC right. lets get the computer to boot the cd live this is where you don't install it but it will have a desktop where you can try ubuntu.


TYPE this in press tab after the cd starts type live-nosplash-powerpc video=ofonly to boot it will get you to the desk top and you can install from there.

---

### Post by wweeks on 2011-03-15
Did you make sure you have the PPC version and that the ISO's match the md5 checksums?

---

### Post by yesfullfull man on 2011-03-17
i do have the ppc version but what do you mean md5 checksums? (i have used ubuntu before but im still a little new at this) and ill try to type the stuff in and see how it goes ill tell you how it goes when i can.

---

### Post by yesfullfull man on 2011-03-17
ok i typed it in on the live cd an i got the same panic kernel eror thing heres what it says(also i got this before with the live cd.

[   122.563635] Kernel panic - not syncing attempted to kill unit! [122.564232] rebooting in 180 seconds

---

### Post by yesfullfull man on 2011-03-22
ok i have even downloaded 9.10  still isnt working  whats the checksums thing and what does that error mean? guys i realy need help im getting sick of this my mac is crap and all i want is ubuntu especially since my laptops charger craped out on me and the g5 i was hoping to get working probably wont happen this little computers my only hope at the moment:confused::confused::confused:.

---

### Post by snafu006 on 2011-03-22
hey if ubuntu is not working for you then try linux mint ppc [http://www.mintppc.org/](http://www.mintppc.org/) try it out its a very good os.

---

### Post by Snipeye on 2011-03-22
OK, simple instructions for installing:

Make sure you have the right version, you stated that you did.

Place the CD in the drive, close the drive, shut down the computer.

Turn on the computer, as soon as you hear the chime, press and hold down 'c' and do not let it go until you are at a black screen prompting you to enter text.

Press 'tab', it should come up with a list of things you can use.  If I recall correctly, you want powerpc-linux or something like that.

It continues booting (give it time) and eventually gives you on-screen instructions for installing.

The only way I was able to get it to work was by formatting my entire drive - I didn't partition and install ubuntu on another part, I nuked the whole thing and installed ubuntu over all of it.


Good luck!

---

### Post by yesfullfull man on 2011-03-22
ok ill try that when i gety home but i dont think itll work because of the weird error and i will try  linyx mint if i no for sure ubuntu wont work. ty!

---

### Post by snafu006 on 2011-03-22
and when you burn a cd burn it slow like 2x

---

### Post by yesfullfull man on 2011-03-22
well i did that with one disc and there was no difference same error and everything and i tried the powerpc-linux but it wasn't there i also tried 9.10 and nothings working but the speed of the disc was 4x not 2x also with 9.10 it just showed he symble screen went black and reboot after awhile alt install just got frozen ug if there's no good answer soon i'm going to tr the mint linux thing. i just want it to work. also does power pc linux still work with wine? sorry just a curious side note.

---

### Post by snafu006 on 2011-03-23
are you downloading from here [http://cdimage.ubuntu.com/ports/releases/lucid/release/](http://cdimage.ubuntu.com/ports/releases/lucid/release/) you need the PowerPC iso download the desktop ver. if you are trying from there web site ubuntu.com thos are for intel base computer i386 it well not work. 

Click This Download  [Mac (PowerPC) and IBM-PPC (POWER5) desktop CD]("http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-desktop-powerpc.iso")

---

### Post by yesfullfull man on 2011-03-23
thats what im doing  ug i think it might be my hard drives fault im not sure what if i put a hard drive in from another  old computer nd try that? or is it posably to install it on a usb disc for now and figure it out within ubuntu or something?

---

### Post by yesfullfull man on 2011-03-23
i mean thats my only guess so i dont cause it doesnt want to work when i get to that point.

---

### Post by yesfullfull man on 2011-03-24
ok hard drive didnt make a difference so i think im going to try linux mint where do i download the ppc one?

---

### Post by snafu006 on 2011-03-24
google linux-mint ppc

---

### Post by yesfullfull man on 2011-03-24
ok thanks ill give it a try

---

### Post by yesfullfull man on 2011-03-25
OK i looked and  well i only found out how to get it installed on the xbox 360 and a download for that and since that was an old ended project of mine i thought this one actually looks easy so ill do it but as far as mint ppc download its self i cant find the download. im ether blind or they hid it that or im looking in the wrong spot.

[http://mintppc.org](http://mintppc.org)

---

### Post by yesfullfull man on 2011-03-25
ok nvm i feel dumb i found it also i have another question do i have to burn ubuntu on a mac or does it not matter. also  im thinking about trying the usb one will it make a difference.

---

### Post by snafu006 on 2011-03-25
> **yesfullfull man said:**
> ok nvm i feel dumb i found it also i have another question do i have to burn ubuntu on a mac or does it not matter. also  im thinking about trying the usb one will it make a difference.

No its ok if you burn from windows use infra burn its on ubuntu.com 
and its really hard to make a bootable usb drive

---

### Post by yesfullfull man on 2011-03-26
i've been using daemon tool is there a difference or anything i did a few using a mac to and with the usb thing no difference. well i had a plan but before i do it i want to be sure. if i install it on a usb using another mac can i then move the usb to this mac and boot up ubuntu. also if this does work will it make the os for the other mac ubuntu or will it still be mac i don't want to mess that mac up its my grandmas so yea. see if this works then i can format the drives from ubuntu and finaly install it on there.

---

### Post by snafu006 on 2011-03-27
I dont think apples can boot from a usb stick because of the boot loader get on a windows computer download the ubuntu ppc and use infra to burn the cd.

---

### Post by yesfullfull man on 2011-03-30
i wont have acces to a pc for a wile would i still be able to try it or would it install ubuntu on her mac i need it to just install it on the usb so i can at least try  and then if it works im good if it doesnt then i can try the infra burn when i get to a pc.

---

### Post by linuxopjemac on 2011-03-30
snafu006: it is possble to boot PPC based Macs from USB....

---

### Post by yesfullfull man on 2011-03-30
you seem upset by that but i still need to no one thing if i load up the live cd on a different mac and install it onto a usb will that mac still have its current os or will it be replaced by ubuntu. then i can test this care free. ty

---

### Post by yesfullfull man on 2011-03-31
sorry guys if I'm being impatient but i need to no this now and im ether a bad researcher or something cause i couldnt find any info about  it.

---

### Post by linuxopjemac on 2011-03-31
If you just put Ubuntu on a USB on another Mac, OSX on that machine will not be replaced by Ubuntu.

---

### Post by yesfullfull man on 2011-03-31
sweet thank you!

---

### Post by yesfullfull man on 2011-04-01
ok im officially pissed off now i installed it on a usb but this mac is retarded and wont open that selection menu to choose a boot up device it'll only open what's on a cd. i went as far as to put the hard drive from the g3 into the g5 (which was annoying because the g5 takes the newer hard drive types so i had to put a peace from the g3 that can read pci not pci express i believe it is and powered the hard drive using the g3 and it worked  perfectly. it installed it directly to the hard drive.  so when it was done i finally put it in my g3. and when i booted it up it ejected the disc try like it usually does and  comes up with that screen with finder alternating with a question mark and finally opens up the ubuntu stage one thing  and i press l. it says starting stage 2 and shows that finder question thing again  blended with the ubuntu stage screen and restarts the stage thing (not the computer) so i click it again and repeat. so i think its my computer or something. idk what to do with it im getting sick of it!!!

---

### Post by snafu006 on 2011-04-01
> **yesfullfull man said:**
> ok im officially pissed off now i installed it on a usb but this mac is retarded and wont open that selection menu to choose a boot up device it'll only open what's on a cd. i went as far as to put the hard drive from the g3 into the g5 (which was annoying because the g5 takes the newer hard drive types so i had to put a peace from the g3 that can read pci not pci express i believe it is and powered the hard drive using the g3 and it worked  perfectly. it installed it directly to the hard drive.  so when it was done i finally put it in my g3. and when i booted it up it ejected the disc try like it usually does and  comes up with that screen with finder alternating with a question mark and finally opens up the ubuntu stage one thing  and i press l. it says starting stage 2 and shows that finder question thing again  blended with the ubuntu stage screen and restarts the stage thing (not the computer) so i click it again and repeat. so i think its my computer or something. idk what to do with it im getting sick of it!!! Are you saying you see a load screen that has 10.?? on it then down at the bottem a white text if it has that then just press I if it asks and C to skip then you should be booting up but the next Problem you are going to have is your xorf.conf file and it need to be updated press alt f1 and type su dpkg-reconfigure -phigh xserver-xorg

---

### Post by yesfullfull man on 2011-04-01
hers the screen i get the loads up onm my g3


First Sage Ubuntu Bootstrap

Press l for GNU/Linux
x for osx
c for CDROM

Syage 1 Boot: _



then it will do this if i wait or push l



First Sage Ubuntu Bootstrap

Press l for GNU/Linux
x for osx
c for CDROM

Syage 1 Boot: _
Loading second stage bootstrap..._


and then it will show a box inm the middle of the screen showing the finder simble  then swiching to a question mark  and the screen flashes black and goes back to  this again

First Sage Ubuntu Bootstrap

Press l for GNU/Linux
x for osx
c for CDROM

Syage 1 Boot: _

---

### Post by yesfullfull man on 2011-04-01
also i should point out  that when ever i start the computer  it ejects the cd tray also if i push option it just starts from cd (after ejecting it first) it doesn't bring up the menu to choose what to boot up like the g5 does idk if thats just cause they didn't implement that in the g3 but just thought id point that out. also i will be getting access to a pc so im going to try and burn an ubuntu disc using the one ubuntu recommends and see if that solves it. after that idk what els to try  im completly out of ideas.......

---

### Post by snafu006 on 2011-04-01
> **yesfullfull man said:**
> hers the screen i get the loads up onm my g3


First Sage Ubuntu Bootstrap

Press l for GNU/Linux
x for osx
c for CDROM

Syage 1 Boot: _



then it will do this if i wait or push l



First Sage Ubuntu Bootstrap

Press l for GNU/Linux
x for osx
c for CDROM

Syage 1 Boot: _
Loading second stage bootstrap..._


and then it will show a box inm the middle of the screen showing the finder simble  then swiching to a question mark  and the screen flashes black and goes back to  this again

First Sage Ubuntu Bootstrap

Press l for GNU/Linux
x for osx
c for CDROM

Syage 1 Boot: _


Dont press i ubuntu is install the next screen is yaboot

---

### Post by yesfullfull man on 2011-04-01
oh so i should o kept the hard drive in the g5 five and went through that screen  crap i just took it out after the instalation on the live cd thing. do i got that right?

---

### Post by snafu006 on 2011-04-01
This is what you did you took the HHD from the G3 and put it in the G5 then you installed ubuntu i the HHD right? and then you placed in back in the G3.

---

### Post by yesfullfull man on 2011-04-01
yes

---

### Post by yesfullfull man on 2011-04-01
ok i installed it and tried to run it on the g3 hdd  in the g5 and it wouldnt boot up it showd that finder thing on this to so is it the disc should i try the  burnering app that ubuntu recomends? and see if theres a diference

---

