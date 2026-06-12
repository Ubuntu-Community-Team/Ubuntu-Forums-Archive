---
title: "Please help rescue installs"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-26
Im starting a new thread on this as ive now got my live cd back and the problems has become MORE than it started out as so sorry for a new thread on continuing probs but i need elp..

Basically i installed a third hd(hdc) two days ago and turned on both xp and ubunto to see the new hd was detected ok and everything seemed ok.
ALL i did with the new hd was then go to it in Ubunto "discs" and used the format option there to change the new hd to ext3 then i  mounted it at
/mnt....I assumed this would only stay mounted  UNTIL i made the correct adjustments to my fstab etc which i was going to do after i`d put the pc back together and rebooted..

SO i reboot and get a GRUB LOADING STAGE1.5 ERROR

I assume i must have just messed up the grub menu or something and getting the live cd would fix this.
SO ive got the live cd back and when i go look at things in gparted i get the below calamity......AM I SCREWED.......

I NEVER touched ANYTHING at any time that could have wiped discs clean in this manner but i dont know if it`s just a problem with not being ABLE to see the xp data(fat32) AND the linux ext3(ubunto install).as gparted mentions "read"problems...

[ATTACH]14876[/ATTACH]             [ATTACH]14877[/ATTACH]


I have since removed this new HD(AGAIN) and all my bios settings are exactly as they were but i just dont know if i NEED to reinstall or if things are just needing fixed.
I dont have a bootable xpcd,just the 1386 directory on a cd with the xp setup files on it so it would be a real hassle for me:-({|= as i woud`nt know where to begin.

Ive been getting help from "catlett" as i first thought it was just an mbr/grub problem and he has a great fix for it BUT i think im missing more than just an mbr now..

I apoligise to the mods for starting a new thread on a similar issue but it has escalated and the other thread was`nt helping.
I go back to work on monday so could really do with this back up and running again FROM its old setup

EDIT:XP.O.D for good this time is it?.....ouch....lol

---

### Post by xpod on 2006-08-26
Can anyone advise????
HAS my xp/Ubunto just vanished or is it in here somewhere????..pleeeeease

Also my @discs@ lists 4 discs but i only have two
[ATTACH]14882[/ATTACH]

Is that the separate swap partitions or something.It dosent give ANY info about them.I really done know what to do next

---

### Post by confused57 on 2006-08-26
I see you're still having some major problems...I wonder if just reinstalling Ubuntu to your hdb would write a new grub to your Windows hda mbr & enable you to boot Windows, since you don't have the WinXP install CD.  Your hdb being so small, it may have reached capacity & corrupted the filesystem somehow.

or

Can you get someone to make you a Windows 98SE OEM boot floppy, as described here?:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

This would enable you to possibly repair Windows with "fdisk /mbr"...I don't really know.  Good luck with it.

---

### Post by xpod on 2006-08-26
Right firstly thanks for replying.I really dont want to make things worse than i already seem to have done.
The little Ubunto HD still had 700ish mb of space left but it was still working fine up until i stuck the 3rd drive in.This was going to be for ubunto as i knew thw small one it`s on was going to run out eventually.

SO can my partitions data (xp & ubu) still possibly BE THERE even though it aint showing up in gparted...
When i start gparted i see some message about not being able to "read" /dev/hdd.

I already have numerous startdisks.....the xp 6 packs first floppy returns some form of error as does a plain single 98/m.e startup disc..

I already tried the fdisk/mbr with one but i could`nt get that to work either......I just cant see where they could be.IF i knew windows was actually still on it`s drive i would go ahead and reinstall BUT thats what im not sure about....IS it or IS`NT it?????

I have had all my usual new user issues but i know enough to know i did`nt physically do anything that would go wipe discs clean in this manner.
All the jumpers had been right with master slave etc and the new hd was there and detected and even mounted temporarily via "discs".

If i can find out xp is definetely gone i would just reformat and share the main drive with ubunto and any hopeful(?)reinstall of xp BUT it would be so much easier if XP is still there and ok.

:confused: :oops:

---

### Post by xpod on 2006-08-26
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4673    37535584    c  W95 FAT32 (LBA)
Disk /dev/hdb: 3243 MB, 3243663360 bytes
255 heads, 63 sectors/track, 394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         373     2996091   83  Linux
/dev/hdb2             374         394      168682+   5  Extended/dev/hdb5             374         394      168651   82  Linux swap / Solarisubuntu@ubuntu:~$



I dont know if this is of any use but i cant figure it all out:rolleyes:

---

### Post by zappafrank on 2006-08-26
Try mounting the devices in the live cd and see if you can access them. 

mount -t ext3 /dev/hdb1 /some/empty/directory
mount -t vfat /dev/hda1 /another/empty/directory

---

### Post by jrjr on 2006-08-26
If I remember correctly, you have an ME machine there right?

---

### Post by xpod on 2006-08-26
Not sure if this is right?

ubuntu@ubuntu:~$ sudo mount /dev/hda1 /media/windows/ -t vfat -o umask=000
mount: special device /dev/hda1 does not exist
ubuntu@ubuntu:~$

HI jrjr......yup i got it sitting right next to me as i had trouble with our kubunto(no cdr) so swapped machines to give me some sort of poxy windows machine to get poxy windows stuff with.

I did`nt have my ubunto live cd for the last couple of days so was trying to access the xp cd(non bootable)i have with the start disks but even that was`nt happening.I thought it must just be a grub problem till i looked at the partitions with the gparted cd last night and noticed the distinct LACK of yellow....

Anything you or anyone else can help me do is much appreciated as im not much help to myself yet again

---

### Post by jrjr on 2006-08-26
I take it that the major goal here is to get XP working again. It sounds like grub got messed somehow. 
One way around this is to change the XP boot to boot just XP
Normally when you install Ubuntu it changes the XP boot and tells it to send things to grub and then the grub menu pops up at boot time
So, you can set the XP mbr (master boot record) back to its original state so it boots windows with no other options.
Ok, got that?

Then if that works and windows boots then work on getting grub fixed. At least you will have windows back

I think that unless you told it to format the wrong drive that all your windows and Ubuntu stuff is still there, it just cant find it

Of course I may be in left field too....

So.... look up above if this is what you wanna do. This link was posted and it seems like a reasonable one to follow. You can either make a boot floppy from your me machine or download it from this link:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

See what you think

Edit:
that was confused57 that posted the link for you :D

---

### Post by xpod on 2006-08-26
Cheers but thats the fdisk/mbr your talking about i already tried that and even from any Start disks in getting error reading c or something like that.

I`ll go away and follow that link again but im sure it`s something ive alreday tried.
Reinstalling ubunto aint a prob if it`s gone but xp is a more serious matter with just the 1386 cd i have(again the startdisks cant get access to then access the cd)
The wifes would pretty much like xp back but`s THATS just to annoy me as she dont really use it too much BUT will take pleasure in saying

"SEE...i told you to leave it alone"..........I cant have THAT now can i

---

### Post by jrjr on 2006-08-26
.

---

### Post by xpod on 2006-08-26
with a 98/me startup disk i get 
      General failure writing drive c...

Ive got an XP startup disk(think it was made from xp)
I get to the A: prompt but  when i type fdisk/mbr it says "bad command or file name

Ive got the 6 pack of xp bootdiscs too but it give some other error when i try and start it.Even with the xp files on that cd

IT`s looking grim down south is it not........lol

EDIT:Even loading the ubunto live cd to it now has this after the second "OK" as it loads

Uncompreesing Linux...OK,booting the kernal.
[4294862.832000]hdd:timeout waiting for DMA
[4294862.832000]hdd:drive not ready for command

And this goes on for quite a few lines with the numbers changing as it goes before it eventually loads

EDIT2:sorry....but 6 lines further down it changes to 

[4295167.164000] Buffer I/O error on device hdd,logical block 357298.

THIS goes on for a further few lines before it loads ok

---

### Post by jrjr on 2006-08-26
.

---

### Post by xpod on 2006-08-26
Everythings fine in the bios.Ive now resorted to trying to install ubunto again on the small drive.Ive tried everything else.
If i dont get any joy im just going to stick ubunto on the main drive and i`ll keep 10g or so in case i manage to figure out installing xp from that cd-rom.

Thats the mad thing,everything is fine everywhere..i.e bios,fstab discs(usually only 2 show up but i assume it`s the live cd seeing the 1 fat32 plus 3 linux).
The only place things look worrying is in gparted and obviously

Im going to go install this again and see what happens(try)I dont know why just loading the live cd now gives all those errors..6 of the 1st and 8 of the 3nd with redard to hdd....

Here goes nothing

---

### Post by PriceChild on 2006-08-26
> **xpod said:**
> then i  mounted it at
/mnt....

In the future, i really don't think you should mount drives at this point (/mnt).

Personally i mount my fixed drives at /media/namehere However you can put yours wherever you want, just create a folder there and mount it to there.

As a general rule, don't mount at points already there, instead create a new folder.

---

### Post by jrjr on 2006-08-26
> **xpod said:**
> Everythings fine in the bios.Ive now resorted to trying to install ubunto again on the small drive.Ive tried everything else.
If i dont get any joy im just going to stick ubunto on the main drive and i`ll keep 10g or so in case i manage to figure out installing xp from that cd-rom.

Thats the mad thing,everything is fine everywhere..i.e bios,fstab discs(usually only 2 show up but i assume it`s the live cd seeing the 1 fat32 plus 3 linux).
The only place things look worrying is in gparted and obviously

Im going to go install this again and see what happens(try)I dont know why just loading the live cd now gives all those errors..6 of the 1st and 8 of the 3nd with redard to hdd....

Here goes nothing

Best of luck to ya!

---

### Post by xpod on 2006-08-26
Well i reinstalled ubunto back  to its little hd and the install went fine and i noticed the last stage with the grub"looking for other operating systems" and finding hda.It finished the set uo without fault it seemed....

Then i rebooted to once again be presented with 
    GRUB LOADING STAGE 1.5 ERROR.

I can load the cd again and look at gparted

[ATTACH]14905[/ATTACH]             [ATTACH]14906[/ATTACH]


At least one of the hds is showing a bit of "yellow" data now......
I reckon XP must be there but somethings messed uo somewhere.
Something dont want to let me on any of the 2 of them no matter what.

---

### Post by jrjr on 2006-08-26
Well I sure wish you the best my friend and I hope it works out for you. For me, I am outta here. I'm not welcome here any longer and I dont feel like putting up with the crap of some of these jerks around here. See you in another distro somewhere, someday!
Cheers!

---

### Post by confused57 on 2006-08-26
> **jrjr said:**
> Well I sure wish you the best my friend and I hope it works out for you. For me, I am outta here. I'm not welcome here any longer and I dont feel like putting up with the crap of some of these jerks around here. See you in another distro somewhere, someday!
Cheers!

Sorry to see you go...you've been an asset to the forums with your knowledge and willingness to help others.  I have no idea what happened and probably don't want to know, but hope you'll reconsider...most of the people using the forums are pretty nice.  I sometimes get a little "perturbed" when someone contradicts what I've suggested when trying to help someone, but I try to keep things in perspective...it's just an OS, not life-or-death.  I still "attempt" to help others with my limited knowledge, experience, and abilites when I can.  Hope to see you around.

---

### Post by xpod on 2006-08-27
Well unlike JrJr it looks like im STUCK here cause i ainy any further WITH OR WITHOUT the forums help.

I aint fussed about losing XP JUST curious as to how it happened AND where yhe bloody hell it went

Having reinstalled ubunto it looks like im going to have to do something with XP`s drive as i cant get past the STAGE 1.5 ERROR
AND i reckon i`ll just go give ubunto the main drive after all and XP can stay OD`D.

All it means is the missus wont have access to her stupid bingo sites via XP and will have to go use our M.E

AND "MOI".....well,i`ll be able to go add to the "HAVE YOU MOVED AWAY FROM XP COMPLETELY AND WHY THREAD"

OFF TO FORMAT XP`s HD:twisted: .

---

### Post by xpod on 2006-08-27
Well i dont even know if anyones interested BUT i have now wiped both drives and reinstalled Ubunto onto main drive BUT still i get
this GRUB LOADING STAGE 1.5 ERROR

I`m OK about killing XP off for good BUT i aint going to do much with ubunto if i cant get it to load now no matter where i put it

DOES ANYBODY HAVE ANY IDEAS......????

Im currently loading live cd onto it AGAIN so would love some pointers on whats wrong........This is the same prob i had away back at the start when i tried the 3rd hd

---

### Post by xpod on 2006-08-27
So this is the end is it....Try Ubunto,Kill Ubunto,Kill XP.....
Reinstall ubunto.......STILL NO UNUNTO other than seeing my install via a live cd.....IS`nt there ANYone who knows about this stuff who could help me out seeing as the other lad has gone and LEFT Ubunto for good?

I`ve googled and searched and still im none the wiser........
Ive chose to opt for Ubunto RATHER than put XP back on but it aint going to happen unless someone a bit wiser than me knows what to do.
I dont know if it`s a grub problem or an hd problem or just a "user" problem but ive done everything according to tutuorials and still end up with a messed up PC.........

I go back to work tommorow so if i aint got it fixed by then it`ll be impossible to give it any time then.....ANYBODY

EDIT:This forum and it`s members have been great with all the usuall setup probs a new user has BUT just as i was getting to grips with it all and begining to comprehend it all a bit more THIS happened and as i said in my previous posts I DID`NT do nothing that would have caused the initial probs so it must have just been one of those moments we are all advised to "backup" against.
This is`nt a "REAL" problem,merely a messed up computer so i aint fussed either way(plenty more computers out there)BUT i would be a shame i had to give up because im mabey not doing smoething simple i mabey need to do.I dont know WHAT after doing a complete fresh install and it STILL doing the same as it had done away back at the start.

---

### Post by toasted on 2006-08-27
Maybe this will help, sounds like it couldnt hurt :) 

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by nickpaton on 2006-08-27
Hi Xpod - I feel for you M8 - nought but problems recently but I admire your persistence!!

As I get if from your last post, you want to nuke the PC and install just Ubuntu.

With this in mind it's time to take a step back.  lets simplify this down.

Since you want to only install Ubuntu, forget about having 2 discs fitted, simply fit one disc, physically set it to Master using the link (ie NOT cable select), and place it at the end of the IDE cable.

Bear in mind that if you do install Ubuntu first, then putting XP on afterwards is difficult (search for numerous other posts on this). 

Now reformat that disc using fdisk via the FDD, removing all partitions and ending up with a clean disk.

Next it's back to setting the partitions, Ext3, Swap (2 x memory) and a 3rd FAT 32 to store stuff - make it a couple of Gb.

Then try loading on Ubuntu, and hopefully the formatting will have cleared out the problems.

Good luck!

---

### Post by xpod on 2006-08-27
hey hey....ceers for the advice folks.
If i take ant more "steps back" im gonna fall of the edge.
Me thinks the both drives were "nuked" 2 days...lol
Anyway....heres what i done now(prior to your replys)
I used gparted on the live cd to wipe both hd`s then i just re-installed as normal putting Ubunto on the 40g drive this time and i never put nothing on the smaller(unallocated).

It`s installed ok it seems but even if were to go do it all again and use a floppy to fdisk im most likely just gonna have the same problems with using them(floppys) as i did the other day.

So..Floppy disc(without cd-rom support) and "fdisk" at the a:.....IS THAT RIGHT?..THEN install again...mmmmm:-\" 

I had only been using windows for months so forgive the COMPLETE ignorance.....right here i go again:rolleyes:

---

### Post by xpod on 2006-08-27
Ok the floppy disk at least seems to work...4 choices
1. Create DOS partition or Logical DOS DRIVE
2. Set active partiton
3. Delete parttiton or Logical DOS drive
4. Display partition info

Then if i choose 3 i get a load more choices about deleting prmary,extended,logical and non-dos partitions..

:confused:

---

### Post by toasted on 2006-08-27
If it were me and I had those mbr toubles, I would low-level format the drive before doing anything else. What brand drive is it, Western Digital? (I hope)

---

### Post by nickpaton on 2006-08-27
Right - remove that smaller disc if you are not using it at the moment - KISS (Keep It Simple Stupid LOL!!!) principle!

If you have used QTparted already, then that should have formatted the disc back to squeeky clean.  Also make 100% sure that you are initially removing ALL partitions & that there is not a small one hiding away somewhere.

With all your troubles, it's possible there's something lurking there.

The reason why I'm suggesting fdisk via a floppy is that I'v used it loads rather than QTparted (100% good program BTW!).

So go here to get fdisk:

[http://radified.com/Files/]("http://radified.com/Files/")

File is in the RH column BTW

Having created the floppy, you will need to fire up the PC and into the BIOS and change the boot order so that the FDD is the first boot device.

What you could then do is to simply use Fdisk to remove ALL partitions (make sure that there is not a small one hiding away somewhere) and then just format the whole disk.

Then reboot & set BIOS to boot the CD first, remove the Fl Disk and reboot into the live CD.

Use this to create the 3 partitions:
Linux Ext3 as Root /
Swap as 2x your memory capacity
The FAT32 partition for extra storage etc.
 
Then carry on from there.

HOPEFULLY....this will work for you (hopefully LOL!)

---

### Post by xpod on 2006-08-27
right i think i done that right(?)but upon loading the live cd again i still get to the 2nd ok(mounting root)then it goes to a black screen with all those "hdd: timeout waiting for DMA
                             hdd: drive not ready for command

I get 6 of them, then the Buffer I/O error on device hdd,logical block errors and i get 8 of them before the cd continues to load ok.

Theres obviously some error somewhere with the disc but i dont know why the cd cares as it uses the ram does it not.Plus im still managing to do the install but......grub  stage 1.5 error.

Anyway,the cd has loaded again so i`ll look at my partitions(or lack of) with gparted first and see what it`s saying before i try install again

---

### Post by nickpaton on 2006-08-27
It does not seem to be seeing the HDD.

If the PC starts up and you go into the BIOS, can you see the Hdd there?

Can you open up the case, make 100% sure that you have removed the IDE ribbon cable and power cable from your little drive.

Make sure that on the HDD you are using, you have set the little link jumpers  so that it is Master.  DO NOT leave it in the 'Cable Select' position.

Connect the IDE cable using the end connector, and make sure it's the right way round.
Make sure the other end of the IDE cable is properly pushed into the mobo, and you have the power cable plugged into the HDD (yes I once forgot!)

Now try again.  Anything you are unsure about please post for further information & I'm happy to try and explain.

---

### Post by toasted on 2006-08-27
I think your mbr section is corrupt. Best way (maybe only way) to fix is low-level format. You need the program from manufacturer. It will restore disk to factory newness.... write 0's to drive

---

### Post by xpod on 2006-08-27
[ATTACH]14951[/ATTACH]

Typical....When i dont want things getting wiped it happens BUT when i try and wipe them i cant even do that right...

](*,) :???: :confused: :-k :twisted: .....

I cant use the fresh install thats ON the disc and i cant uninstall to reinstall....NOT with "fdisk" it seems.....

I did what you said and unconnected the little drive but i obviously got the "fdisk" part wrong....SURELY theres some way of just usuing the clean install thats on here(im jumping between pc`s......on ubu cd now)

---

### Post by nickpaton on 2006-08-27
Xpod I've just PM'd you.  Can you read and get back to me.
Nick

---

### Post by xpod on 2006-08-27
Just to say "thank YOU" publically to nickpaton who is going to help this poor beast rise from the ashes once again.......

And IF he cant........WEll not to worry cause i got plenty issues i could find with our kubunto SO you`se wont get rid of me back to windows that easily im afraid.......Thanks again nick=D> =D> 

GOOD MAN.....

---

### Post by nickpaton on 2006-08-27
Thanks.....but lets fix it first!!!

---

### Post by xpod on 2006-08-27
I did say "IF" nick my friend........I was just letting the rest of these guys know they were`nt getting rid of me that easy...lol

---

### Post by toasted on 2006-08-28
I hope you will post the results...  I would like to know how you fixed it :mrgreen:

---

### Post by nickpaton on 2006-08-28
Yes the HDD does need a good ol' reformat and I agree about the low level stuff etc, 

BUT....

From PM's etc, it's almost pointing to a BIOS or other problem on the mobo.

We'll get there but it's going to take some days & we will post the results.

---

### Post by xpod on 2006-08-28
Right folks im still not 100% clear on how or why my harddrives were both seemingly wiped by merely plugging a third hd in but i can tell you`se a little of the soloution thats got me back up and running.

My  install of XP "used" to take up most of the main drive with a small 2g of unalloacated space on the end of it.
Even once nick run me through the Fdisk to completely wipe the disk it still left this space unallocated on the end after doing a complete format of the disk.

All my attempts at reinstalling just ubunto to the main drive failed no matter how i partitioned the disk UNTILL i did it so there was still that little unallocated space on the end of the drive.

I also made sure that the main ext3 linux partition was not to large as this was producing error 18 if i gave "/" any more than what i have.

So i now have 10g ext3,1g swap then a fat32 that uses the rest BAR the little 2g UN-allocated on the end.

As some may recall i had many issues with that little 2g when XP used to be on this drive and i could not touch it without messing xp up untill i UN-allocated it again.Nothings changed it seems.
Why it still has to exist on the end for ubunto i`ll never know but there you go......It does on this.

Many thanks to all who helped again especially nickpaton who went above the call of duty.
NOW i am completely free of the space problem..... AND of course the xp problem...lol

I takes me all my time to understand what happens so forgive my lack of knowlage in explaining what apparently happened...(I happened!!:rolleyes: )

---

### Post by toasted on 2006-08-28
At least its working... thats good!
I take it you did not do a low level format then?

---

### Post by xpod on 2006-08-28
I could`nt tell you what "level" format is what but i did it with a startup disk and fdisk to completely wipe it(that still left the little unallocated bit on end when i then "looked" via gparted)....I was flying by the seat of my pants as usual so i`d say it was pretty much "low level" stuff...lol

Anyway,then i tried to install by just pointing it towards the main drive which was by NOW the only drive.It installed fine but when i went to use it i got the GRUB LOADING STAGE1.5.(i had tried reinstalling on its own original 3.2g slave but i got same stage 1.5 with grub) 

So i redone it by splitting it in half with a swap in the middle but still no good THEN i made sure ubunto`s "/" ext3 was only 10g but still no joy THEN i done it the same way but left a couple of "g" on the end UNallocated as it always had been with xp and after that format.AND IT WORKED

I can understand it refusing to work without that space when it was xp but not now its ubunto.

The mad thing is this time my flash sound works without all the further codes i had to do first time round but now my printer wants some stcolor driver to work when IT worked out the box last time round.My old epson was`nt ON when i insatalled and updated so thats mabey why.

At least im sitting down to a fresh new os this time WITH a wee bit more savvy to get things done....IT`S ALL GOOD.........i`ll probably STILL be back needing my printer fixed next week though...lol...cheers.

The MORE i break it the more i learn on how to "make it" again:rolleyes:

---

### Post by toasted on 2006-08-28
break it make it.. its a viscious circle LOL
Well, if you have to start over again think about the low level thing
It just may get rid of the 2 gig nightmare partition 

Now go have fun!!    :mrgreen:

---

### Post by xpod on 2006-08-28
I imagine it is a REAL "vicious circle" for some when it`s all a bit more serious stuff they do but this is just a load of old junk i use to play about with so theres never no "real harm" done but i do sympathise with all the poor folks that have similar issues with serious stuff on their pc`s.

Mind you people with serious stuff on their pc`s SHOULD`NT be messing around with them in this way but just like the poor vicars church assistant who was here recently ....they always will.

Good luck people....and have "fun":twisted:

---

### Post by toasted on 2006-08-28
Well ya know.. some people have serious stuff on old 'junk' and can use the input at times on how to keep it purrin' like a kitten. Anything worth doing is worth doing well so they say.

---

