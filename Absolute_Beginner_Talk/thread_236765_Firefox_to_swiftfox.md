---
title: "Firefox to swiftfox???"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-15
Another simple question folks...thanks

Was having a lot of speed related problems yesterday which i eventually resolved but i still ended up installing Swiftfox from automatix along with the required plugins.

Not really too sure if it`s making much of a difference but what i want to know is.....Is it ok now to uninstall FIREfox.

The reason i ask is space.....I dont have much.

My Ubunto is on a tiny 3.2g slave with XP(fat32) on 40g master.(dont mention resizing) and theres 20g of that xp space free

as you could imagine whats left of the slave space is vanishing rapidly.

My XP IS mounted and i made an Ubunto folder on the / of it BUT thats ok if i need to manually store something there BUT what will happen when the little bit of space on the slave is gone...WILL Ubunto KNOW to use it.(the space on xp hd that is)

The removing of firefox obviously only matters if i  WILL need the space

Im going to buy some fancy mega gig hd at sosme point but im quite happy learning what i am with what ive got for the moment.

---

### Post by d4rk on 2006-08-15
I've read that some programs needs firefox to run correctly.
Azureus is an exapmle, I think.

---

### Post by Jagot on 2006-08-15
Yep, definitely not good to remove Firefox.

---

### Post by xpod on 2006-08-15
Hi...Ive not come across that app yet but im begining to wonder if this here "Swiftfox" was worth the bother.......

Dont see much real difference with normal use...

I`d quite happily keep firefox(aint they the same underneath)if i knew the score with regard to what Ubunto will do ONCE the 500mb it has left runs out.

If anyone could tell me WHAT will happen when that last mb is used up...

...CAN and WILL Ubunto utilise the 20g of space available on XP`s fat32 hd.

If it can ..Would i need to direct Ubunto to any desired folder?,Will it KNOW where to go and put things......

I know a lot of people will say"just resize xp etc etc" but it`s not an option......It gets all BSOD and tempromental if i even try use the 2g of UN allocated space it has on the end of it.....

I dont have an xp cd so i cant take those risks........I aint bothered about XP...I`d quite happily reformat and GIVE ubunto the master and stick DSL or something on the little hd...BUT the missus and kids still want me to keep it so KEEP IT i must

---

### Post by xpod on 2006-08-15
Sorry for asking again...BUT does anybody know what will happen with regard to the above post?

And is anybody else having the timeout problems on this site that i am??

I.E  threads hanging or returning server timeouts constantly..

It`s taking me a couple of minutes just waiting to see if it will connect.

THATS obviously something out of my hands and i will be making a donation to contribute my wee bit to the bandwith problem in due course(when she leaves me some of my wages)

But i really need to know whats going to happen in 497mb`s time when the space on this itty bitty little hd finally run`s out with all the updates etc etc........

Theres loads of stuff out there but i aint found nothing specific to my soon to be problem....(other than reformatting or resizing)

As always im extremely grateful to all those who listen to my constant queries.......:confused: ](*,) :-k :p

---

### Post by steve.horsley on 2006-08-15
Things get really nasty when Linux runs out of disk space. The best thing is to boot into recovery mode and delete stuff it that happens (if you can). Failing that, a live CD where you can mount the hard disk and then make space by deleting stuff.

Yes, the Ubuntu servers seem to have been quite bad recently. I like to think it's more users that's the cause. In fact, I think the population has doubled since last time I lookes at the number of current online users (1000->2000).

---

### Post by xpod on 2006-08-15
Hi steve, So is there no way it can be made to utilise the 20g of free xp fat32 space thats available on the master hd.
The only real stuff that gets downloaded are the updates(and a couple of apps..FF) so i would`nt know what to remove anyway.

You`d think that if I can access my main hd and if I can read and write to it
ok THEN this would be able to access it itself if and when required.

It can do all that stuff BUT wont do it itself if it needs to....

Surely theres a way round this   NO??

OR is that just asking a bit tooo much  lol

---

### Post by David Corrales on 2006-08-15
Just a couple of tips...
[LIST]
[*]Try running **sudo apt-get clean** to remove all the downloaded packages, that saves HD space vs bandwidth in case you need to download them again
[*]Try removing stuff you don't use via Synaptic
[*]You could also mount your home partition on a directory in the FAT32 partition so everything you do inside of it gets saved on the other hard drive. This could also apply to some directories like the apt-get cache for example.
[/LIST]

---

### Post by jimmygoon on 2006-08-15
Azureus use **the** mozilla browser (not firefox!)

---

### Post by xpod on 2006-08-15
Hi david....Cheers for the input.
Right im getting a bit confused here(nothing new)...Surely the last thing i want is to get get rid of ALL downloaded packages??

Are`nt a lot of them to do with security and system workings??

Im also not sure what you mean by "saves hd space vs bandwidth"

I know cleaning out EVERYTHING would obviously make space but whats that to do with bandwith???(something else new to learn??)

All i really need is to be able to use the 20g of xp space and if you reckon i can make my home in the xp hd then surely thats my problem solved??

I only got Ubunto last week and other than ALL the "informed of" updates i dont really download a lot...

Tell me if im wrong then....Would i just create a folder called Ubunto home and then mount it`s full path and put it in the fstab ....

AM i even close.........If its just the same as mounting any other filesystem then that i can mabey manage ..I just was`nt sure it would be the same for what it is i need to do

---

### Post by David Corrales on 2006-08-15
**IMPORTANT**
Due to the fixed file permissions in FAT32 partitions (root/devplug), this solution will NOT work. Use a symlink instead or create a new ext3 partition and mount through fstab
**IMPORTANT**


I have to agree that my redaction was confusing, sorry :(

What I meant about bandwidth is that if you downloaded any packages (updates or new programs using apt-get/synaptic) and you delete those packages in the cache, you'll have to redownload them should you need them.
On the other side, one almost never needs to redownload stuff they already downloaded with apt-get/synaptic so I think that given your situation it's best to delete those files and get the extra space back (which can be quite a bit after some time).

About the home folder on the FAT32 partition, actually you won't have to "mount" it in another partition but rather use a soft link (which is easier). I'll elaborate now :)

One really cool thing about linux is that you can create links to other files or directories -similar to a shortcut in windows- BUT they are a lot more powerful than their microsoft counterparts. Say, you can have a link in your Ubuntu partition pointing to a directory in the FAT32 partition and it's transparent to applications when they save files or manipulate them. On windows, links aren't as "persistant" as linux ones. Sometimes they're treated as regular files.

Enough blabber :), the basic idea is to have a symlink in the /home directory pointing to a directory in the FAT32 partition. That way, whatever you do in your home directory, gets saved in the 20GB drive so you can work freely! Here we go:

For this example I'll use **xpod** as your username :) and the FAT32 partition is mounted at /media/fat32. Of course adjust these values to your actual settings.
[LIST]
[*]First, start creating a folder with your Ubuntu username in the FAT32 partition. So it's /media/fat32/xpod on the 20GB HD.
[*]Copy all your home files from Ubuntu. Go into *Places->Home Folder* and press **crtl+h** to see all files. You should see a lot more directories with a "." before their name besides your commonly visible files.
[*]Select all files pressing **ctrl+a**, and copy them to /media/fat32/xpod in the FAT32 partition. You have two copies of the information at this point, in the Ubuntu partition and the 20GB hard drive.
[*]Now you need to delete all the files in the Ubuntu partition and set up the soft link.
The safest way to do it is to reboot, go into recovery mode and remove the directory from there since it guarantees no application will be writing to the home directory.
Personally if the data is not -that- vital I'd just close every regular application and do it from the GUI then reboot. Your choice :)
[*]Safe way: 
[LIST]
[*]Reboot and choose "Recovery mode".
[*]Delete the folder from the Ubuntu partition: **rm -rf /home/xpod**
[*]Set up the soft link: **ln -s /media/fat32/xpod /home/xpod**
[*]Make sure the owner of the link is correct: **chown xpod:xpo d/home/xpod**
[*]Make sure the permissions for the link are correct: **chmod 755 /home/xpod**
[*]Reboot
[/LIST]
[*]Lazy way: 
[LIST]
[*]Close all applications running
[*]Delete the folder from the Ubuntu partition: **rm -rf /home/xpod**
[*]Set up the soft link: **ln -s /media/fat32/xpo /home/xpod**
[*]Make sure the owner of the link is correct: **chown xpod:xpod /home/xpod**
[*]Make sure the permissions for the link are correct: **chmod 755 /home/xpod**
[*]Reboot
[/LIST]
[/LIST]

---

### Post by xpod on 2006-08-15
WOW.....now that has got to be the most comprehensive reply ive had to date.
I aint even read it properly yet BUT am going to go do so right now...

Ive been wrestling with an UNallocated 2g on the end of the xp hd this last week and tried everything to format & mount that wee bit space for Ubunto(ext3) BUT no matter what or how i did it my XP would then just BSOD when i tried to boot it,which i could only remedy by undoing what i`d done(deleting back to UNallocated again).Then doing "last good config"in xp.

Being one of those lucky people who have a 1386(with xp setup) directory instead of an actual XP cd im not in a position to take too many risks.
Unfortunately i never did master the slipstreaming of THAT copy with the SP2 files(purely acedemic now)to make the "bootable"cd...lol

ANYWAY ive had a quick read over it and THATS exactly what i need....

Im still a little confused about the first paragraph though regarding removing packages ive downloaded with apt-get......The ONLY stuff i got with it is the regular updates...Then i began using "aptitude"to get them after i learned the pro`s and con`s of both...BUT i aint going to now go and remove what have basically been mostly updates i was notified to get..

..AM I????mabey i could get rid of a LOT of those things as half of it i see flash by on the terminal lools like stuff i`d never use anyway..

STILL........none of that will matter once i utilise the xp space so who cares if ive got some russian language files i`1l never need eh...lol

I`ll get round to purging the whole thing of anything i and it dont need eventually but im happy for now......

NOT going to give it all a go now as im knackered but im ON IT first thing in the morning my man so i`ll get back on here and give you a hopeful "thumbs up in the morning"....GOODNIGHT for now(morning)zzzzzzzzzz[-(

---

### Post by David Corrales on 2006-08-15
I'll explain a bit the whole apt cache issue. When you download a new program or updates using Synaptic/Aptitude/apt-get, the file (.deb) is first downloaded to a local folder (/var/cache/apt/archives) and then used to update or install the program.

Once the program or update is installed the file remains in cache, should you need it later on then you don't have to redownload it. After a while this directory becomes filled with all the installion .deb's for updates and programs.

What the command **sudo apt-get clean** does is clear that folder automatically for you, giving you that valuable space back. The tradeoff is, you'll have to download the .deb if you need it later on (kinda rare).

So basically what you're deleting are the -installer- files, not the actual updates to the system or programs. Think of it like deleting the installer files for any windows program you already set up.

Good luck on the home folder move :)

---

### Post by xpod on 2006-08-15
GOTCHA NOW.....good man.goodnight for now.ZZZZZZzzzzzz

---

### Post by mdsmedia on 2006-08-15
> **David Corrales said:**
> 
[*]First, start creating a folder with your Ubuntu username in the FAT32 partition. So it's /media/fat32/xpod on the 20GB HD.
[*]Copy all your home files from Ubuntu. Go into *Places->Home Folder* and press **crtl+h** to see all files. You should see a lot more directories with a "." before their name besides your commonly visible files.
[*]Select all files pressing **ctrl+a**, and copy them to /media/fat32/xpo in the FAT32 partition. You have two copies of the information at this point, in the Ubuntu partition and the 20GB hard drive.
[*]Now you need to delete all the files in the Ubuntu partition and set up the soft link.
The safest way to do it is to reboot, go into recovery mode and remove the directory from there since it guarantees no application will be writing to the home directory.
Personally if the data is not -that- vital I'd just close every regular application and do it from the GUI then reboot. Your choice :)
[*]Safe way: 
[LIST]
[*]Reboot and choose "Recovery mode".
[*]Delete the folder from the Ubuntu partition: **rm -rf /home/xpo**
[*]Set up the soft link: **ln -s /media/fat32/xpo /home/xpo**
[*]Make sure the owner of the link is correct: **chown xpo:xpo /home/xpo**
[*]Make sure the permissions for the link are correct: **chmod 755 /home/xpo**
[*]Reboot
[/LIST]
[*]Lazy way: 
[LIST]
[*]Close all applications running
[*]Delete the folder from the Ubuntu partition: **rm -rf /home/xpo**
[*]Set up the soft link: **ln -s /media/fat32/xpo /home/xpo**
[*]Make sure the owner of the link is correct: **chown xpo:xpo /home/xpo**
[*]Make sure the permissions for the link are correct: **chmod 755 /home/xpo**
[*]Reboot
[/LIST]
[/LIST]Just a point of clarification for xpod when he wakes and jumps in here (hopefully). Throughout those commands you used the name xpo. It should be xpod in all cases I think

---

### Post by David Corrales on 2006-08-16
> **mdsmedia said:**
> Just a point of clarification for xpod when he wakes and jumps in here (hopefully). Throughout those commands you used the name xpo. It should be xpod in all cases I think

Edited, thanks :)

---

### Post by xpod on 2006-08-16
Well GOOD MORNING people....

It looks like in falling at the first hurdle here as when i try and create the folder /media/windows/dad on my xp hd i get told that it cannot use the / character.....

Conflicts????

I`ll keep trying but i dont want to do anything until im SURE

Also...dont know if it`s relevant but as well as having /media/windows...which is obviously my xp i ALSO have a folder at /windows
which was already there....this is`nt a problem is it(theres nothing in it)

EDIT:...wait,let me guess....i NEED to go INTO xp to create this folder as apose to doing it from Ubunto....DUH!!!!!PAY ATTENTION GRAHAM

2nd EDIT:nope ..going into xp still would`nt allow me to use / in any folder name..?????????????????????????????

---

### Post by David Corrales on 2006-08-16
Morning xpod, actually you can create the folder from either Ubuntu or Windows. What's important is that the letter case remains the same (dad, Dad and DaD are all different to linux while equal to Windows).

Now that we know your account is called **dad** and the FAT32 partition is mounted at */media/windows* we can make this more especific.
To create the folder, just navigate in nautilus to */media/windows* (where you should see all the regular folders like Program Files, etc), right click on the window and create a new folder called **dad**.
You should now be able to continue the step by step instructions of the previous post :)

---

### Post by xpod on 2006-08-16
morning mate....Well i know i can be a bit slow on the uptake at times but im doing EVERYTHING right i believe....I always use lowercase and thats what everything is but still
The name "/media/windows/dad" is not valid because it contains the character "/". Please use a different name.

EDIT:And it dont matter what way i do it....from here or there?

Sorry...I can make a folder called "dad" okay but not as per your main post with a / in it

Alright ive got the folder called "dad" on the/ of my xp and ive got all the hidden (ctr-h)files from my home selected (ctr-a) but when i try and paste them over ctr-v....i aint having much luck....doing that wrong too no doubt.

---

### Post by xpod on 2006-08-16
Eventually managed to use the mouse to try and copy them over but It dont want me copying that home folder

ERROR "OPERATION NOT PERMITTED" WHILE COPYING "/home/dad/..iscopy.pyo

Whatever that means??....Im sure ive done exactly as told but it aint having it

EDIT:Tried again(and again) but i can select all the home files and when i attempt to copy them over i get some form of error message in most of them but 5 or 6 did find their way over...just empty app folders.

I keep trying but only get the same ones to copy successfully....
I`ll try some of them seprately just out of curiosity....

EDIT2:Nope,even trying them separately is no good as most of them Will not copy....no matter how i do it...c&p OR d&d....Stumped im afraid

---

### Post by sailor2001 on 2006-08-16
that 2gig unallocated file in XP is a swap file... When something overloads your ram it virtually spills over to there. don't remove it.

---

### Post by jrjr on 2006-08-16
.

---

### Post by xpod on 2006-08-16
Hi...thought this had been forgotten.
i stopped trying to use that 2g on the end of xp after a couple of days as i kinda figured it was still being used by xp after all.
I was just lucky the thing still worked.

Anyway YOU would`nt know why i cant copy any of those home folders as advised would you...I `d really like to DO as the other chap was helping me do but i cant copy that "home" like he says.???

STUMPED.....thanks for that on the little space though(it had still been bugging me even though i`d gave up on it)

---

### Post by jrjr on 2006-08-16
.

---

### Post by David Corrales on 2006-08-16
I just came back home and read all your posts. Let's do this, let me do it all on a virtual machine and I'll upload pictures of what to do in each step and in the process see if it actually works :) ok?

---

### Post by David Corrales on 2006-08-17
I just learned using the virtual machine that there's a problem with FAT32 partitions. There's no way you can change the user to another than root/plugdev... so the solution won't work :(
I'd suggest resizing the 20gb drive to make an ext3 partition and THEN using that partition to mount the home files.

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
AH HA.....Good day to you all again..I had gave up trying to copy that "home" to the fat32(xp) as it just ws`nt having it.
I was`nt sure if it was ME or THIS...:rolleyes: .

Anyway,the only reason i am here now trying to use the xp partition is that I spent a whole week Tip-Toeing around the XP hd and im sorry to say i always chickened out at the last minute.
The only reason i used such a small hd for Ubunto was my fears over resizing  master drive PLUS it was good to learn how to salvage old pc parts and reuse them.
As i had said elsewhere,I did do the defragging a couple of times when last in there BUT still it left a rather large(relatively)block of blue data towards the end of the partition which it never used to do.(murphy strikes)

I know the resizing would most likely move that ok BUT..As i am one of the "lucky" people who have a 1386 directory(xp setup) instead of an XP CD and as i never quite mastered slipstreaming THAT copy of XP with the SP2 files.Well im not in a position to REinstall if anything was to go wrong.

It`s SO frustrating knowing that XP`s there taking ALL the decent space up and knowing i dont even want it BUT have to keep it just in case.
Xp having BSOd`s just with me touching that 2g  has me thinking it would be worse if i even tried resizing for some reason.

I dont know if just trying to copy that "home" directory did anything but now my online sound has gone from stuff like you tube and google video.
It still works on rhythmbox radio and logon but just not online.

The more problems  i try and overcome and the more i try and learn semms to just leave me with all the MORE to figure out.:confused: 
I started a new thread about the sound but i`ll take answers from ANYWHERE i can get them.

EDIT:> Well I just looked the thread over again and in the first page it says your xp is on fat 32 so you should be able to write to it with no trouble. Its odd that you cannot partition it.

Just noticed this...I tried partitioning the 2g Unallocated on the end of xp to ext3 then i tried fat32 BUT both left me with BSOD``s on booting XP.
I havent actually attempted to re-partition the main 38g xp one.

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
I actually dont even use the xp defragger...(pain in a**)
I use a wee program called simply"Scandefrag" which worked really well for me and does all the disk checking,cleaning and defragging in a lot less time than xp `s did....I think it killed all the running process or something prior to starting.But yup all that sort of stuff became a bit of an obsession along with the constant De-hyjacking nonsense that was the extent of my few months in windows.
I became an expert at all that stuff.But not much more...:-({|=

---

### Post by jrjr on 2006-08-17
.

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
Sorry for confusing you with MY OWN confusion.
I have already navigated to my c drive VIA /media/windows and THEN once on my / in xp i created a folder called "dad" and THEN attepted to copy my home diractory from here over to there.
I tried the copy and paste way AND i tried dragging and dropping them in but most of them produce an error message whenever i try.

I even tried moving them over seprately but even that produced the same error messages on each separate attempt.
Sorry for ANY confusion.......Purely MY doing

---

### Post by jrjr on 2006-08-17
.

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
Just to verify...:) 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1   /media/windows   vfat     iocharset=utf8,umask=0000   0 0


The mad thing is...as i said "most" wont copy,BUT some(about 6 empty app folders)DO copy .The ones that dont just produce a little window with the copy error messages i mentioned previously.

I sure appreciate you using your time on me mate.This is a bit more than the typical line or two of code im getting.I was fumming with myself yesterday cause i even had to go use XP to edit my tux as that gimp was a bit too hard so you see why i need to keep XP for now

EDIT:It would`nt be to do with "permissions" would it?.I dont know what the score would be with permission to move certain "home" floders.Another thing ive yet to run into problems with so dont know much about.

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
No problem mate....What about my online sound?do you know much about this?As i said i aint been able to hear anything online.I could yesterday okay and can still hear the rhythmbox radio ok BUT the sounds gone if i visit you tube and google video etc.

Ive got all the relevant plugins etc and it worked fine till i booted this banger up today..As i said,i just seem to create MORE probs as i go along.

I DO actually have a couple of small hd`s lying around btw but just was`nt sure what the score would be with putting a third one in with regards to the bootloader etc....Would it all be recognised and setup without causing me any boot probs?......The plot thickens!!..lol

EDIT:missed yours too..lol
Done the command you just gave to open nautilus and got
dad@dad-desktop:~$ gksudo nautilus
(nautilus:15268): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

But it still opened nautilus although there is not as many folders in it this way even when i hit ctrl-h.....I suppose theres a reason for that(not required)

---

### Post by jrjr on 2006-08-17
.

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
Right...THIS is getting real crazy now...I just went back to the home folder in the "root file browser" (with it`s less files) and i done the "ctrl-a" thing to highlight them all THEN i navigated to /media/windows then i opened the file called "dad" to try again AND THEY NOW LOOK TO ALREADY BE THERE??

Ive still not hit "paste" or tried to unload the files i highlighted.
Im not 100% sure exactly what one are all in there but it looks like the ones i seen in root mode and not the many more there were in normal mode..

Does ANY of that make sense???give me 5 mins to see whats what:confused: :rolleyes:

---

### Post by jrjr on 2006-08-17
.

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
Right....here we go again.THIS TIME i went to my own home with the root filebrowser and tried to copy and paste them ALL over but this time i got about 10 plus of THESE sort of errors
     INVALID PARAMETERS
   2fdcim.xml
   2f%2f.xml
   ris 1503741
   ing 150374
    cn-za.soe
I hit "skip" at each one just to see
There was mabey a few more too.BUT it looks like most if not all of the files "seemed" to copy but i`ll need to scrutinise them to be sure.

Still...All those invalid parameters cant be good ...can they?...OR was that just some formal protest ...lol


EDIT:SORRY.....just noticed all this in the terminal too

** Message: Hit unexpected error "Invalid parameters" while doing a file operati on.
** Message: Hit unexpected error "Invalid parameters" while doing a file operati on.
** Message: Hit unexpected error "Invalid parameters" while doing a file operati on.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
** Message: Hit unexpected error "Operation not permitted" while doing a file op eration.
dad@dad-desktop:~$
dad@dad-desktop:

---

### Post by jrjr on 2006-08-17
.

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
A "seagate" or something like that i think.

After now closing all windows and going back into the "dad" folder on the xp there is 8 of them now(there was a lot more when i left it.. in root mode
ALL 8 of them have aquired the little padlock next to them.

Im begining to think that although it sounded like a good move at the time it is NOW becomming apparent that even though the XP hd is readable and writable
It is still not willing to play "home" for this here Ubunto.....

Wether it`s the XP being tempramental OR the Ubunto protesting im not sure but UNLESS we`re missing something here i reckon it`s looking like a NO GO?

The MORE i go on like this the MORE i feel like just letting gparted loose on it.....THAT would solve the issue eh...haha.....

Well..as long as i know ive "listened and tried" thats good enough for me.
Thats NOT to say it wont "niggle away" at me....The poxy 2g is STILL doing it so this aint going to be any easier to let go off eh......lol

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
HAHA......I spent practically my last month of my 4 on XP trying to make that slipstreamed cd....ALL of the stuff out there involved first copying your xp
setup files FROM your xp cd THEN getting your SP2 files and slipstreaming them both together.
Quite a few of these guides mentioned little bits about having THAT sort of copy of XP already on your disc or emergancy partiton and apparently there could be problems with "some" forms of it.

I must be one of "those" lucky people" as i never managed to master it.
I DID manage to re-direct the SFC /SCANNOW function to replace missing and corrupt DLL`s from that copy of xp (instead of requesting cd-rom)but sadly thats as far as i ever got.

That XP is still dangling it`s unsolved mysteries under my nose to annoy me is`nt it....lol

---

### Post by jrjr on 2006-08-17
.

---

### Post by jrjr on 2006-08-17
.

---

### Post by xpod on 2006-08-17
Cheers again......Unfortunately this old thing was the mother in laws and i only got it cause the M.E we had was dead too at the time.She had dumped it in a cellar due to severe infestation and BSOD.(she got new one).
I somehow got it into a decent state but the fact that it`s a "TIME" box should tell you that calling uo aint an option.

Although i did hear their making a comeback somewhere i doubt they`ll have a CD for anyone let alone me...Thanks again

---

### Post by David Corrales on 2006-08-17
Hey xpod, just wanted to add some extra info as to why the move to FAT32 isn't going to work.
When I created the virtual machine with xp/ubuntu I got the same file copy problems. There's a real problem with file permissions in FAT32 partitions, they always stay root/devplug no matter what so it's not going to work in the way I expected.
You can write freely to the partition, for example, make a symbolic link from your regular home folder and save everything there. That's what I do and it works fine, but moving your whole folder won't work.
I'm going to edit the solution post and add a note that it won't work.

---

### Post by WADemosthenes on 2006-08-17
Use the "fasterfox" extention instead of swiftfox.

---

### Post by xpod on 2006-08-17
Hi again well at least you know what i meant now eh...lol
Funny you mention these symbolic links but im sure it was something like that i had to create to get the sound working again.
I could be wrong im not sure what half those lines of code i read even do but one of them seemed to work after messing around with alsa and oss stuff.

Well at least i got something sorted.
So i can go back to your solution and create this link WHICH will do what exactly..........Save any future stuff  saved to "home" there???

It`s going to get pretty silly if i end up having to costantly manually move stuff i CAN move just to keep making way for possible important updates etc etc.Does that make sense?

Im not going to bother messing about with any of those other old hd`s i mentioned.I had a look and their even smaller than the one Ubunto`s on just now.Out of a win98 pc.......so not worth bother.Kid`s are all wanting laptops soon no doubt so any hardware i could do with will have to wait.
Im quite happy messing about with this lot for now until im a bit more proficient in the art of it all.

---

### Post by jrjr on 2006-08-17
.

---

### Post by David Corrales on 2006-08-18
> **jrjr said:**
> Greets!

David, the way I understand this, xpod has not created a virtual machine. He is trying to do just basic copy and paste to his fat32 partition and it is not working for him for some reason.

Hehe yeah, thing is I created a virtual machine with his same environment to try my solution out. That's when I found out you can't use a FAT32 partition as a home directly, but rather as a folder inside your current home.

---

### Post by xpod on 2006-08-18
Good morning people....Firstly ive been using "faster fox" sinse i started out with firefox which was about 2 weeks after i sat down at a pc for the first time those few months ago.....(did`nt take me long to get away from I.E then WINDOWS full stop)

I only tried the "swiftfox" cause i was having major problems with the amount of time FF was taking(WITH FasterF)...But after a while i soon realised it was nothing to do with Firefox.......It was this bloody site that must be so busy at certain times of the day that just "opening a thread reply" was taking ages OR usually just "hanging" with "server time outs"

I might even relegate "swiftfox" back to synaptic cause it certainly AINT much better that i can see.

Anyway..it`s good to see my trivial little -little hd problems  and Ubunto space requirements are of interest .....Thanks as always:-k 

If anybody has got any any FURTHER ideas im ALL EARS..........(yes yes buy a new hd ..i know).....THATS not the same fun though is it!!!.

FOR anyone not wanting to read the whole thread........I NEED TO HAVE UBUNTO AUTOMATICALLY USE THE FAT32(xp) HD AS THIS ONES RUNNING OUT OF SPACE 
AND RESIZING THE FAT32 IS NOT AN OPTION.......MOVING "HOME" OVER TO IT NEVER WORKED...

---

### Post by jrjr on 2006-08-18
.

---

### Post by xpod on 2006-08-18
HAHA....It had began as M.E XP O.D`d......But i settled for the XPOD.
Was`nt sure it`s actual meaning was even being realised.

It`s fine NOW though just in case you were mabey wondering if it`s a messed up xp that was the cause of any the recent failures we had .

Both the XP on this and the M.E pc upstairs used to have numerous probs but i`d always manage to fix one with the help of the other.

Their both probably in better "working" order now than what they were when they left the shop......AS hard as THAT might be to believe judging by some of my still obvious ignorance of  a lot of stuff.

Without meaning ANY less of davids help i was just jumping AT the possibility it was actually doable..I`ll try anything.
It`s not something im even bothered about just something i like to get my head around.
Upon till recently we were intent on buying a new pc once "that" new one was out and ready for us normal people to use.We only bought a second hand complete M.E off a pal in febuary just to get the kids(and moi) a little bit knowlageable but that died so i salvaged the XP from mum in law and a couple of months later HERE i am.With NO intention now of "buying" that new system when it comes out now but instead will eventually just buy the bit`s and pieces of new "hardware" .And obviously IT`S operating system is already sitting here on any number of live cd`s.....Sorry bill;)

---

### Post by jrjr on 2006-08-18
.

---

### Post by xpod on 2006-08-18
LOL......Not at all mate.....I was intending to wait and get the Whole lot as this pc itself is a few years old and we want something a bit more presentable  for in here but HEY.....at that price i reckon i`ll  sort one later.Theres nothing wrong with this OR any of the other two but she wants all the fancy flat screens and cool looking box`s n printers n stuff.
We were going to buy new originally buy my missus being my missus COULD`nt refuse the leather recliner and unit she got with it off her pal for the price she got it.Im glad NOW though as we`d have bought something we probably would`nt have wanted eh...

That one looks the same as the 40g one thats already in here.Im sure theres similar i bit closer to home too...

---

### Post by jrjr on 2006-08-18
.

---

### Post by jrjr on 2006-08-18
.

---

### Post by xpod on 2006-08-18
HaHA......Show off.Dont worry about being OFF topic as ive spent the last 20 minutes just trying to get ON the site again(timeouts) SO at least one of us is back where we started...;) 

We`ve got a load off "sickly cream machines"....
I used to be like that with the ultra cool sound systems in a past life.
That was before kids started comming along and i could "afford" to have hifi`s that cost more than my cars.
We really dont need nothing new for what we actually use them for BUT.....
....She wants cool looks now and i want extra ram and bigger processors,graphics cards `N` hd`s..........Not for ANY "real" reason you understand but just cause i "want".....I`ll figure out WHY once ive got them.

That make sense???????.........I know what i mean....:rolleyes:


PS....tell the truth.....your using some old commodore 64 with bits of your microwave added to get it going

---

### Post by jrjr on 2006-08-18
.

---

### Post by xpod on 2006-08-18
HEY HEY......i was only winding you up mate....I DID believe you;) 
You`ve obviously been AT THIS for many years my friend where as the last time I used a computer up untill a couple of months ago WAS indeed the commodore 64 my mother bought for my 14 birthday a couple or so decades ago.

I used to have to load a cassette tape to then batter the poor joystck just to get my decathlon man to run a 100 yards at a decent rate of knots.

That "corner" you have does look a bit like MY corner though with all the pc junk(just a "term";) )Except ours is all beige....I`ll try figure my camers out at some point and give you a laugh.....
Well i got the photo but cant suss out getting it on here.........
Im sure you`ll tell me if your curious enough......:D

---

### Post by xpod on 2006-08-18
[ATTACH]14493[/ATTACH]


I think this is right.......Apart from yours being a nicer hue and the fact that you got more hamsters running round little wheels than moi....haha

EDIT:obviously not "right" then.......Cant even get an attatchment right me.

EDIT:...tch tch......

OH...not be outdone...I got a comfier chair than you  haha

[ATTACH]14494[/ATTACH]

---

### Post by jrjr on 2006-08-18
.

---

### Post by jrjr on 2006-08-18
.

---

### Post by xpod on 2006-08-18
Unfortunately with 5 kids and only 5 bedrooms there aint no spare rooms to stick it all.The kid`s use the m.e in the dinning room but we`re going start moving the pc`s into their rooms now their getting the hang of them.
Ive had them doing the basics on the Kubunto you see at the side there so as long as i buy a decent tower with some decent inners for Myself then ive practically got the makings of one for each of their rooms.
THATS so much easier than the "alternative".......(WAR)

YEAH....a bit messy to say the least.

Ps ..i was only joking about the chair,I got a black one like you:cool:

---

