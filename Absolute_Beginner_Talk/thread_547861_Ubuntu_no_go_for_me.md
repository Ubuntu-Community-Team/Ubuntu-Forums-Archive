---
title: "Ubuntu no go for me"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by kfctombraider@hotmail.com on 2007-09-10
About to give up folks, cannot get it installed.  I have an AMD Athlon 1600, Maxtor 40 gb hard drive formatted to NTFS clean, Nvidia GeForce 5200 PCI video card brand new, 512mb ram, standard keyboard mouse, DVD-RW drive, floppy, that's it.  Have tried Live CD, goes to main menu, hit install it goes to blinking cursor and stays that way (left it overnite still there). Have tried it with safe vga mode, same thing.  Have tried the alternate CD, same thing.  Have tried with noacpi, nolacpi, acpi=no, vga=733, still sits there with blinking light.  CD doesn't even seem to being accessed to read the disk it seems, no lights, nothing.  I'm about to give up, please don't make me pay Bill, my 7 yr old just needs Webkinz.com, nothing more, nothing less.

Mark

---

### Post by nikef on 2007-09-10
Hi and welcome
sorry i can not help
but
please do not give up
there will be some1 along shortly who is experienced,this site is great
they know every thing,so just hang on in there,till some1 gets to you  :)
its worth  the wait

---

### Post by kellemes on 2007-09-10
Sorry for not helping.. :popcorn: but there are a lot more distro's out there.. 350+ atm.
PClinuxOS, Mepis, Mint, Fedora, openSUSE, Mandriva to name a few.. all with comfort in mind.
I highly recomend PClinuxOS. Get the livecd, burn and see if it works.. you'll know soon enough.

---

### Post by shae on 2007-09-10
Have you tried using a different CD?  Sometimes CDs will have defects that prevent them from working correctly.  If you burned the CD, what speed did you burn it at?

If you have tried the things you say you have, my first guess would be some type of problem with the DVD drive.  I first suggest that you check the connections of the DVD drive to the motherboard.

Another thing to consider is what version you are trying to install.  Are you trying to install Feisty or Dapper?  Sometimes, the install CD may have a problem with certain chipset configurations.

It is very important we know the exact moment this problem occurs.  Is it right after the initial menu?  Is there any messages before the blinking cursor?

---

### Post by rsambuca on 2007-09-10
Just a quick try.  Add "ide=nodma" as a boot option prior at the main menu screen.

---

### Post by CaptainInsaneO on 2007-09-10
When you go to boot the livecd there's an option that says "Check CD for defects". Run that, if there's errors burn a new disc at the slowest burn rate your burner can achieve. It minimizes errors.

I say this because when I first tried Ubuntu I had the exact same problem as you, the culprit was a bad disc.

---

### Post by kfctombraider@hotmail.com on 2007-09-10
Wow!!! Super fast help everyone, try to answer your questions.  I burned the cds at 1x with the free burner linked from here.  If I hit Check CD and hit enter it also goes immediately to the blinking cursor.  If I hit enter for any of the menu items it goes directly to the blinking cursor.  Do I add the "ide=nodma" after the two dashs -- or before in the command line?  I have the DVD setup to be the secondary master, orginally had it as primary slave and it doesn't seem to make a difference.  It reads the disc because it pulls up the menus on both the live cd and the alternate, just selecting any option but memtest goes right to the blinking cursor.  I'm installing the 7.0.4 version I think that's Feisty.  There are no messages before the blinking cursor that I can see, unless they're too fast to see.  Tks again for the fast help!

Mark

---

### Post by rsambuca on 2007-09-10
> **kfctombraider@hotmail.com said:**
>  Do I add the "ide=nodma" after the two dashs -- or before in the command line?  
Mark

Before, and leave a space before the dashes as well (and without the quotation marks)

---

### Post by southernman on 2007-09-10
Try again by downloading the Alternate CD and use it.

When you go to Ubuntu to download the CD, be sure to tick the box below the "start download" button... or you'll wind up with the same Desktop (Livecd) you have now.

---

### Post by kfctombraider@hotmail.com on 2007-09-10
I'll try that extra command when I get back home shortly, what does that do?  The board does support ultradma I remember from the specs.  I'm pretty sure I have the alternate cd because the menu options are different on it vs. the live cd.  Are there any video issues to be aware of for that card, it's brand new from CCty.

---

### Post by hsweet on 2007-09-10
Burn the iso slowwwwwwwwwwly.  I have had trouble anytime I didn't and it has always worked when i did (disclaimer... past performance is no guarantee of future return)   

but great good luck

---

### Post by kfctombraider@hotmail.com on 2007-09-10
Won't disabling the dma really slow the system down if I use the command? Or does this just disable it for the installation only?

---

### Post by rsambuca on 2007-09-10
Just for boot-up.  If you can get it to boot up, then you definitely want to turn dma back on.  I had to do this to load Dapper, but Feisty works without it.  I thought it might be worth the few seconds it takes for you to try it, though.

---

### Post by lncoll on 2007-09-10
Hi:
  Have you tried the memtest option at boot?, this one does a full memory test and many times you get surprised. 
  If this does not solve the problem...
  Try another O.S. (Freedos or similar), if it works...
  Try a lighter Linux dist, DSL is the best for this, if this works.... get all the hardware info in DSL to start Ubuntu, if doesn't, cry a little and ask again.:confused:

Good Luck, you'll need it.

---

### Post by Jimmyfj on 2007-09-10
One thing you could try is to enter your BIOS and tell it to load the BIOS Default Settings. 

From what I understand you don't even get to the point of the pending bar while loading the Live CD. The alternate CD has never failed for me. My 7.10 install is made from that CD type. It could be, as already mentioned that you have a DMA conflict of some kind. Resetting the BIOS should show if that's the case. If it isn't a DMA conflict then you need to check all the connectors to your CD-ROM, hdd, floppy. Even try to take out your graphics card and clean both the card and the slot it sits in.

---

### Post by kh1116 on 2007-09-10
you could try installing xubuntu or kubuntu, then download the ubuntu packages from synaptic if you still cant get ubuntu to install and one of those install properly.

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Tried the ide=nodma switch and still didn't work.  Tried it with alternate and live cd's, same thing blinking cursor.  Will try the default bios settings after work, but that's going to be the last effort.  I've already spent over 20hrs just trying to get it installed, if that's what a Linux installation typically takes even before making the peripherals work then that's just not worth it.  Bill wins again, at least I can get his stuff to instal the first time.

---

### Post by Calash on 2007-09-11
Your experience is not the typical experience.  Just like Windows most Ubuntu installs go very smooth.

What ISO did you download?  Meaning did you get the 32 or 64 bit version, CD or DVD image, etc. I can see that causing problems if you accidently got the wrong one.

Are you overclocking at all?  As suggested above you may want to bring your BIOS to default to see if something is not working right there.

I do hope you can get the issues worked out.  Ubuntu is a very good Operating System IMHO.

---

### Post by kfctombraider@hotmail.com on 2007-09-11
I think I got the right versions from the main site here.  I didn't know there was a seperte cd and dvd version, but i'm pretty sure I got the 32bit version, but that's a good place to start.  The cd's read just fine on my home pc so I just assumed they were okay, I'll try and run the live one when I get home.

---

### Post by hyper_ch on 2007-09-11
for installation I would recommend the alternate version and not the desktop cd.

---

### Post by overdrank on 2007-09-11
> **kfctombraider@hotmail.com said:**
> I think I got the right versions from the main site here.  I didn't know there was a seperte cd and dvd version, but i'm pretty sure I got the 32bit version, but that's a good place to start.  The cd's read just fine on my home pc so I just assumed they were okay, I'll try and run the live one when I get home.

Hi the only other thing I can add would be to remove the quiet splash from the command line where you added the command ide=nodma. And see if any errors and search from there.

---

### Post by asmoore82 on 2007-09-11
Do you have a "LG" Brand super-multi DVD-RAM drive??

---

### Post by sawjew on 2007-09-11
Just a thought, did you burn the image to the cd as an image or as a data disc.  You need to burn the image not just copy the image to the cd.  I don't know how experienced you are with iso images but it's a common mistake.

---

### Post by CaptainInsaneO on 2007-09-11
I actually didn't even think of that, sawjew but that's very good advice.

And it IS a common mistake, definitely not something to be embarrassed about because everyone does it at least once their life. :)

---

### Post by rsambuca on 2007-09-11
> **sawjew said:**
> Just a thought, did you burn the image to the cd as an image or as a data disc.  You need to burn the image not just copy the image to the cd.  I don't know how experienced you are with iso images but it's a common mistake.

That can't be the problem here since he gets to the menu screen.  There is obviously a hardware issue.

---

### Post by frrobert on 2007-09-11
I've seen this before on Windows XP.  You would get the initial screen then the system would choke.  The problem was the CD ROM Drive itself.

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Thanks again everyone for the advice.  I did try deleting the nosplash and quiet out of the string no help.  I actually do have an LG super-multi DVD/RW drive by coincidence I'm pretty sure (at work now), are there issues with that drive maybe?  Should I download and create the dvd version and try it as well?  I did burn the ISO file with the free burner (burn image) and I did see several files on the cd and a directory or so as well so I think that's good.  Now I feel we're getting somewhere, perhaps the drive is the culprit.

---

### Post by steve.horsley on 2007-09-11
asmoore82 must have had a reason to name that particular make of drive - pity he didn't say more. Still, it would be well worth trying a different CD drive if you have one lying around.

---

### Post by Brightbelt on 2007-09-11
This is a long shot, but it's sometimes worth trying a different BRAND of CDs. For example, if you're using Sony CDs try Verbatim or Memorex etc. 

If it doesn't help, at least you know you have gotten that possible factor out of the way.

Frank B.

---

### Post by jpsimm on 2007-09-11
> **kfctombraider@hotmail.com said:**
> About to give up folks, cannot get it installed.  I have an AMD Athlon 1600, Maxtor 40 gb hard drive formatted to NTFS clean, Nvidia GeForce 5200 PCI video card brand new, 512mb ram, standard keyboard mouse, DVD-RW drive, floppy, that's it.  Have tried Live CD, goes to main menu, hit install it goes to blinking cursor and stays that way (left it overnite still there). Have tried it with safe vga mode, same thing.  Have tried the alternate CD, same thing.  Have tried with noacpi, nolacpi, acpi=no, vga=733, still sits there with blinking light.  CD doesn't even seem to being accessed to read the disk it seems, no lights, nothing.  I'm about to give up, please don't make me pay Bill, my 7 yr old just needs Webkinz.com, nothing more, nothing less.

Mark




Is your BIOS OK?

---

### Post by scalawag on 2007-09-11
Ubuntu is great, wonderful system - I've still got a few quirks, little things with simple workarounds which I will get worked out soon, I'm sure, but a great operating system, user and newbie friendly all around.  I tried the PCLinux OS referenced a ways back in this thread and it gave me a similar outcome to what you're witnessing with Ubuntu.  Point being, don't give up on Linux just because Ubuntu didn't work for you.  I'm a HUGE fan of Ubuntu, never used a distro this nice, simple (to use, not too look at, very flashy, very nice), and easy to install and use - and this is on newer hardware right down to the widescreen, flat panel display I'm using, but if it won't work for your situation, it won't work.  Try another distro.  Just 'google' Linux Live CD - You'll find one almost as nice (and perhaps even nicer for your cause.)  Give a good swing at linux before you give up - It's a great OS and a great community.

---

### Post by asmoore82 on 2007-09-11
> **kfctombraider@hotmail.com said:**
> Thanks again everyone for the advice.  I did try deleting the nosplash and quiet out of the string no help.  I actually do have an LG super-multi DVD/RW drive by coincidence I'm pretty sure (at work now), are there issues with that drive maybe?  Should I download and create the dvd version and try it as well?  I did burn the ISO file with the free burner (burn image) and I did see several files on the cd and a directory or so as well so I think that's good.  Now I feel we're getting somewhere, perhaps the drive is the culprit.

Gentoo GNU/Linux 2004.2 universal install cd will freeze everytime at the stage
"Mounting CD-ROM"  only on LG super-multi DVD-RAM drives.

never found an explanation/solution for that one way back in 2004...

the drive was brand new OEM, so it may have had something to do
with the ambiguous state of the DVD Region firmware.
EDIT: I'm not sure, but I think the problem still existed even after the drive was
used to play commercial DVDs in windoze(my dad's); so that theory is out.

---

### Post by pooper on 2007-09-11
have you done memtest?? 

i had windows xp working but gave that the boot for ubuntu. i kept having trouble installing ubuntu, it kept going so far then just stopping. But windows worked !?

so

I ran memtest and it gave me like over a million errors. So i had a fiddle about with my sticks of ram (3 in total) and tried to figure if one had failed. Turns out after trial and error 2 sticks were actually faulty, but as i had 3 i used the one working and got ubuntu installed.

So try that and basically try and single out faulty ram.

---

### Post by ElTimo on 2007-09-11
just a thought, but do you have the right architecture for your CPU? It sounds a stupid question even to me as I type it, but it's always good to make sure. Did you download the i386 version or the 64-bit version?

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Back at home now.  I set the bios to defaults and tried the ide=nodma, noacpi, irqpoll, still blinking cursor.  I selected the memory test, I see a green box on a blue background and it says Memtest86 (red + blinking) v1.65.  At the far left of the green box is a red underscore blinking also.  What is it supposed to be doing/displaying?  Does it take long to run?

---

### Post by kfctombraider@hotmail.com on 2007-09-11
this is the iso that I downloaded does it look right ubuntu-7.04-alternate-i386.iso.  Put in an old plain cd-r drive 52x non LG now, same thing happening, nothing but blinking cursor.  I think I'm cursed.

---

### Post by pooper on 2007-09-11
it should look something like

[IMG]http://i4memory.com/reviewimages/motherboards/intel/975XBX_rev304/installed/html/photos/975XBX_065.JPG[/IMG]

and below the system details it should have errors highlighted in red, if any. (not shown in that pic)

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Here's where I'm at.  I have the alternate cd in.  Menu is open.  First line is Install in text mode, there are f1 thru f6 available.  I select f6, it says:
Boot Options d/ubuntu.seed initrd=/install/initrd.gz quiet --|

I edit it to say:
Boot Options d/ubuntu.seed initrd=/install/initrd.gz ide=dmaoff noacpi irqpoll --|

I hit enter, goes to the blinking cursor.  Is this typed in right?

---

### Post by pooper on 2007-09-11
correction my mistake disk is fine if your get menu etc

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Tks Pooper, mine is just blank, with just that green box showing, a blinking red underscore at the far left of the green box, and a blinking red + sign beside the number 6.  How long does it take to get to data to show up on the screen?

---

### Post by pooper on 2007-09-11
well for me it was straight away. :confused:

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Okay, I've put in four different ram sticks, running the memtest on one at a time, get the same green box with blinking + sign and underscore.  The cd drive is not being accessed at this time, it only seems to read when starting up the memtest.

---

### Post by kfctombraider@hotmail.com on 2007-09-11
It's got to be a bad iso burn or image, can someone give me a link to one of the alternate or live that they know is a good iso image and I'll try and reburn.

---

### Post by pooper on 2007-09-11
then i guess its not a ram problem like i had. but neither memtest or ubuntu are loading correctly :confused:

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Nope, neither one is working, I hope it's a bad or wrong image I chose.  i'm going to try and download a different one this time and reburn it.  Don't know what else to try.

---

### Post by pooper on 2007-09-11
so your running windows atm? if so download the iso again (or if you still have it) then go to  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
scroll down to the windows bit, install the program check the iso is correct, then burn iso image to disk and a low speed and if you can, have the burn software verify data after its written too. (nero does this im sure others will)

---

### Post by danny joe ritchie on 2007-09-11
I'm thinking that you are probably right about the image being screwed up somehow!  I've had problems with this myself.
 
After wasting a bunch of cds I finally got Nero and it worked for me !

---

### Post by scalawag on 2007-09-11
I got mine right from ubuntu.com's download page - selected Desktop edition - selected "Ubuntu 7.04 - Supported to 2008" - and selected my architecture (amd64) - X86 in your case from what I've read, then downloaded, burned as ISO (not even sure what I used to burn it, forgot Winblows that fast :) ) and been happier then a pig in chit since.

---

### Post by southernman on 2007-09-11
> **kfctombraider@hotmail.com said:**
> It's got to be a bad iso burn or image, can someone give me a link to one of the alternate or live that they know is a good iso image and I'll try and reburn.
[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso]("http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso")

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Tks guys very helpful for me in my time of frustration.  I went and got the bit torrent for both the desktop live and alternate and am going to burn them both.  I used that freebie that's recommended to burn and selected burn image, I have Nero and Easy cd creator, hell i'll try anything at this point.  Seems to point to bad image I think, maybe still some hope.

---

### Post by Michael Allison on 2007-09-11
You're installing Ubuntu for a 7 year old's use only?

Honestly, I would use something simpler. Ubuntu is simple for Linux, but it's still Linux.

Edubuntu (I believe that's what it's called) might be a better idea?

But where did you get the installation CD? My suggestion is to ask someone you know with a CD burner to burn the ISO onto a DVD-RW, and let you borrow it... If you got the disk somewhere else but the official shop, it's likely there's something wrong with it anyway...

---

### Post by rsambuca on 2007-09-11
EDIT:  Ooops, I see from your first post that you have the AMD 1600+.  You want the i386 version.

---

### Post by Caffeine_Junky on 2007-09-11
[**_Here is the place I got mine from_**]("http://www.ubuntu.com/getubuntu/download"), Ubuntu 7.04 Desktop X86 ..had no prob's with it.  I used nero-6 to burn it to disk in Windows (I think the option was  'Make Bootable CD')  ..burned it at somthing like 2x speed with "Verify after burn" enabled.   worked like a charm!

best of luck this time mate :)

---

### Post by Tyke91 on 2007-09-11
> 
Quote:
Originally Posted by [email]kfctombraider@hotmail.com[/email] View Post
Thanks again everyone for the advice. I did try deleting the nosplash and quiet out of the string no help. I actually do have an LG super-multi DVD/RW drive by coincidence I'm pretty sure (at work now), are there issues with that drive maybe? Should I download and create the dvd version and try it as well? I did burn the ISO file with the free burner (burn image) and I did see several files on the cd and a directory or so as well so I think that's good. Now I feel we're getting somewhere, perhaps the drive is the culprit.
Gentoo GNU/Linux 2004.2 universal install cd will freeze everytime at the stage
"Mounting CD-ROM" only on LG super-multi DVD-RAM drives.

never found an explanation/solution for that one way back in 2004...

the drive was brand new OEM, so it may have had something to do
with the ambiguous state of the DVD Region firmware.
EDIT: I'm not sure, but I think the problem still existed even after the drive was
used to play commercial DVDs in windoze(my dad's); so that theory is out.

i think asmoore has provided the answer here... have you tried getting an external cd drive? (i installed my ubuntu from an external iomega CR-RW 52x
[http://www.cdw.com/shop/products/default.aspx?edc=578046&cm_ven=RKG&cm_cat=adwords&cm_pla=Data+Storage&cm_ite=iomega_52x32x52_cd_rw](http://www.cdw.com/shop/products/default.aspx?edc=578046&cm_ven=RKG&cm_cat=adwords&cm_pla=Data+Storage&cm_ite=iomega_52x32x52_cd_rw)

---

### Post by southernman on 2007-09-11
> **rsambuca said:**
> EDIT:  Ooops, I see from your first post that you have the AMD 1600+.  You want the i386 version.Because I've always had best success with the alternate cd, and in light of OP's massive headaches...

dang your fast rsambuca... :p  :lolflag:

You zigged while I was zagging! I linked him this time to the 64bit alternate disk!

---

### Post by kfctombraider@hotmail.com on 2007-09-11
I do have an external dvd drive usb 2.0 will that load from there?

---

### Post by kfctombraider@hotmail.com on 2007-09-11
burned the new iso with nero, no difference at all.  Now burning with Roxio, this is it people.

---

### Post by southernman on 2007-09-11
Before throwing your hands up... Did you try it also with your external drive?

---

### Post by kfctombraider@hotmail.com on 2007-09-11
No  option to boot from usb so i'm shut out.  Might the other buntus, maybe they'll load. can i install the edubuntu and load firefox for browsing and the office stuff?

---

### Post by rsambuca on 2007-09-11
All the *buntus are the same under the hood.  Unfortunately I doubt that switching will help.  You might be better off trying a different linux distribution altogether.  Perhaps PCLinuxOS if you want to keep it simple.

---

### Post by kfctombraider@hotmail.com on 2007-09-11
OH MY GOD@!!! I turned off almost everything in the bios and lo and behold the alternate install came up!!!! but oh crap, i don't know what I turned off!!!! Cross your fingers everyone, it's friggin askin me questions!!

---

### Post by kfctombraider@hotmail.com on 2007-09-11
holy crap batman it's loading stuff from the cd too!!

---

### Post by southernman on 2007-09-11
> **kfctombraider@hotmail.com said:**
> OH MY GOD@!!! I turned off almost everything in the bios and lo and behold the alternate install came up!!!! but oh crap, i don't know what I turned off!!!! Cross your fingers everyone, it's friggin askin me questions!!
Excuse me for a moment but I need to... ROFLMFAO

w00t!
:popcorn:

---

### Post by kfctombraider@hotmail.com on 2007-09-11
laugh all you want my brother, i'm rockin.  Question, asking me to partition disk, do i do entire disk with or without LVM??

---

### Post by danny joe ritchie on 2007-09-11
:lolflag:

---

### Post by danny joe ritchie on 2007-09-11
I'd go for without lvm, no big deal either way!

---

### Post by kfctombraider@hotmail.com on 2007-09-11
didn't recognize the network with dhcp to my wireless router, hope that's not hard to fix.

---

### Post by wheredidrealitygo on 2007-09-11
wireless in gnome is pretty easy now (in feisty), are you using WEP or WPA (or better) encryption?

---

### Post by kfctombraider@hotmail.com on 2007-09-11
actually I'm using a netgear plug in the wall device that uses your wiring for the network wiring.  I've used it on several pcs before and a mac so it should work for this too I hope.

---

### Post by southernman on 2007-09-11
> **danny joe ritchie said:**
> I'd go for without lvm, no big deal either way!

+1

btw... I was laughing with you. I know you were (probably still are) grinning form ear to ear. AND... if truth be known, you probably got out of your chair and did a little diddy around the room too! :p

---

### Post by danny joe ritchie on 2007-09-11
Yes, I did!

---

### Post by Paul133 on 2007-09-11
So it's working? You installed Ubuntu? If so, mark the thread as solved. Go to thread tolls -> mark thread as solved.

---

### Post by danny joe ritchie on 2007-09-11
Hang on a minute, the mans working!

---

### Post by kfctombraider@hotmail.com on 2007-09-11
we ain't finished installing yet and booted, at 65% and still installing.

---

### Post by Maestro23 on 2007-09-11
> **kfctombraider@hotmail.com said:**
> we ain't finished installing yet and booted, at 65% and still installing.

I've been watching this thread, hope everything works out for ya man. :guitar:

---

### Post by danny joe ritchie on 2007-09-11
Shhhh! Quiet everybody!

---

### Post by kfctombraider@hotmail.com on 2007-09-11
YEAH BABY YEAH!!!! WE HAVE DESKTOP!!! Now installing 118 updates.  I'm going to write down my bios settings for everyone tomorrow so we can have my saga on record for others.  Should I go back and set the bios for the optimal settings or let ubuntu manage all of that stuff?  are the updates coming from the web or cd?

---

### Post by wheredidrealitygo on 2007-09-11
**munches popcorn, gripping blanket in suspense**

This is better than a movie!

All joking aside, I think you're really going to be happy with it. Do you have any questions about what general apps replace specific Windows ones or anything along those lines?

Updates come from web usually if connection is up.

---

### Post by danny joe ritchie on 2007-09-11
O.K. now you can mark it solved!:lolflag:

good luck!

---

### Post by rsambuca on 2007-09-11
And to think I recommended PCLinux!

---

### Post by southernman on 2007-09-11
> **kfctombraider@hotmail.com said:**
> YEAH BABY YEAH!!!! WE HAVE DESKTOP!!! Now installing 118 updates.  I'm going to write down my bios settings for everyone tomorrow so we can have my saga on record for others.  Should I go back and set the bios for the optimal settings or let ubuntu manage all of that stuff?  are the updates coming from the web or cd?

If your running updates, they are coming from Ubuntu repos directly. w00t again!

Unless you find something not working as it should, I wouldn't touch the bios until that time. Just keep track of what changes you make from this point so if it flugs up immediately, then you can go right back and change it!

VERY NICE JOB!

Persistence paid off, and you'll see soon the beauty of what you've done tonight.

Congrats... My hats off to you! And everyone that helped you.

---

### Post by rsambuca on 2007-09-11
I too am impressed.  If my initial foray into linuxland was like yours, I would be still using XP exclusively.

Seeing how it looks like you have a bunch of extra discs now, you may as well give them out to people you think might actually try it out.

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Guess what, I"m posting from my new install!! However.....already have a booboo with the update manager.  Got this error when trying to run the updates:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

help!

---

### Post by southernman on 2007-09-11
> **rsambuca said:**
> I too am impressed.  If my initial foray into linuxland was like yours, I would be still using XP exclusively.

Seeing how it looks like you have a bunch of extra discs now, you may as well give them out to people you think might actually try it out.

lol!

Chuck says "Spread the love, or your gonna catch a round house kick!"

---

### Post by southernman on 2007-09-11
Open a terminal (Menu->Accessories->Terminal).
Type the following command and press the Enter key:

sudo dpkg --configure -a && sudo apt-get -f install

This should correct the problem and restart the install.

---

### Post by rsambuca on 2007-09-11
Open a terminal from the top menu bar.  "Applications -> Accessories -> Terminal".

Enter the following command in the terminal:```
sudo dpkg --configure -a
```

EDIT:  Chuck is fast.  So fast.  Too fast.  Need my numchucks.

---

### Post by kfctombraider@hotmail.com on 2007-09-11
Tks again guys, ran sudo dpkg --configure -a && sudo apt-get -f install and got this error: 

Errors were encountered while processing:
 metacity-common
mark@rachelpc:~$ 

a bunch of stuff installed it looks like. I've got so much to learn.

---

### Post by southernman on 2007-09-11
try first...

sudo aptitude install metacity-common

if that don't work try

sudo aptitude -f install metacity-common

Don't fret it pal... things like this teach you more than you realize. You've got the gumption, we know this!

---

### Post by kfctombraider@hotmail.com on 2007-09-11
tks again bud, that did it.  got my sound working, turned it on in the bios and unbuntu recognized it, although not very loud.  got flash installed terminal paths and directories take a little while to get used to, similiar to dos.  gonna go for acrobat, some other stuff tomorrow.  tks again for everyone's help, i'm sure gonna return the favor.

---

### Post by southernman on 2007-09-11
No problem friend.

---

