---
title: "Installing Ubuntu/Kubuntu"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by hayz on 2006-12-31
Hello There,
 A friend of mine just introduced me to the Ubuntu OS.
I av tried the live Cd and i love the Interface and everything About it.
Now d Problem is I want to install it on my pc that has Windows Media Center on it.
So i dont want anything to affect my Windows cos i heard i can install the Ubuntu on a Partition on my Hard Disk.
I av Tried installing it Several times but when i get to the Partition section I get some kind of Error message(I cant even remember the Error Message I got)
So I will be very Glad to hear frm u people in the house who can take me thru steps of Installing the OS on my Laptop(Hp Pavilion dv5215us Entertainment Notebook Pc)

Expecting ur Replies, So that i can join the Ubuntu Family..

                                                                     Thanks


You can holla me on YahooIm: hayznet

---

### Post by smoker on 2006-12-31
do you have enough free space on your hard drive?

check this link for good information on installation, and read down to the relevant bits:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by meng on 2006-12-31
If Windows is already on there, you may wish to boot to Windows and defrag ... maybe even more than once. Windows has a nasty habit of creating lots of immovable data, and if it's at the end of the partition, that makes it rather difficult to resize.

---

### Post by hayz on 2007-01-01
> If Windows is already on there, you may wish to boot to Windows and defrag
-I dont get You there
Pls be more explanatory cos i am new in all this:confused: 


> do you have enough free space on your hard drive?
-Yes I do! Infact, my Hard Disk is a 80Gb One but atleast i still gat up to 25Gb left free.

---

### Post by meng on 2007-01-01
What I mean is you should try defragmenting the drive in Windows, sometimes this gets cluttered with data scattered all over the drive and it's then difficult to resize the partition because there's very little contiguous space. Windows has a disk defragmenter tool that you should use.

---

### Post by adewale on 2007-01-01
ahmed for u to defragment just go to my computer and right click and pick properties click the tool tab and click on defragment

---

### Post by hayz on 2007-01-01
@meng: So when am true doing that what Do u think is the next thing?

-I will go for the Defragment now. hope it wont av a problem doing dat?

---

### Post by hayz on 2007-01-01
Hello Fellas,
 I'm Thru with the Defragment -Whats Next?
 Shuld I go On install nd how?

---

### Post by adewale on 2007-01-01
u have to partition before u install. hope u have back up

---

### Post by hayz on 2007-01-01
Partition? How?
-Is it via the Ubuntu Cd? -Pls put me thru:confused: 
Or do u think its advisable to first Partition my HDD via Windows using one of these partitioning tools?](*,)

---

### Post by adewale on 2007-01-01
u can do it on windows through partition magic and u can also do it through the live cd. but make backup of your entire hard disk on a dvd or sum place other than your hard disk. i wish someone would explain how to partition the disk for you

---

### Post by smoker on 2007-01-01
hi, hayz,

> check this link for good information on installation, and read down to the relevant bits:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

did you read through the above link?

this is a link from the above:

[https://help.ubuntu.com/community/forum/installation/Partitioning](https://help.ubuntu.com/community/forum/installation/Partitioning)

if you read through this information, and post if you have any further questions.

hope this helps

---

### Post by hayz on 2007-01-01
@All Thanks Very much support!

@Adewale I av been advised earlier to use Partition Magic For the Partitioning.
But the Problem is dat i will like anyone who's used it b4 to Guide me thru.
-Anyone Of u used it nd worked well? Holla.:D 


@Smoker thanks for the link.. I did browse thru them but its like they r not solving my problems](*,)
Can u put me thru A step by step guide?:-k ;)

---

### Post by hoagie on 2007-01-01
Well as long as I remember I partitioned thorugh the partition editor during the ubuntu installation and everything went fine. 
So I believe you will have to boot to the live cd start the installer and follow the steps.

---

### Post by hayz on 2007-01-01
Hey hoagie: I av once gotten to the partitioning stage in the Ubuntu installer but it gave me an error message. But I dont know why?](*,)
-How do u intend helping me pal?;)

---

### Post by benerivo on 2007-01-01
Can you remember what the error message said and at what point it happened during the installation?

---

### Post by adewale on 2007-01-01
i was with him we both tried installing it but as we ran the installation all went well until it reached the time for partitioning and it gave an error like failed un start partition something i can't remember. i think what we need is how to partition manually

---

### Post by Bartender on 2007-01-01
Download [GPLCD]("http://gparted.sourceforge.net/livecd.php").  Burn it to a good quality CD just like you would a Linux distro. 
Boot from the GPLCD. 
You should see an NTFS partition at the front (to the left in the map across the top of the page) of the HDD.  That partition will be a primary partition, labeled hda1.  
Do you see any other partitions?  If so, what are they?
Take a look at this guy's blog.  Scroll past the PCLOS guide to the partitioning guide.  Although it was written for an all-Linux HDD it'll still give you an idea of what you're after and how to do it.  With pictures!!

[http://www.sroyc.blogspot.com/](http://www.sroyc.blogspot.com/)

I don't know why, but the stand-alone GPLCD just seems to work better than the partitioner in the Ubuntu install CD.  Even though they're the same thing.  

Check out [aysiu's]("http://www.psychocats.net/ubuntu/index.php") site for all sorts of graphical guides.  Definitely read thru his "Just Beginning" guides.

If you get your Linux partitions built, then choose "manually partition" on the Ubuntu install CD and mount / to the primary ext3 partition (probably hda2 but that will depend on how you build it) and mount swap to the "linuxswap" partition you made (probably hda5 but again it's up to you).

I just read back thru this...I tried to speak in plain English but can see how all the terminology could make you dizzy.  Take a look at those links, see if any of it makes sense, post back with questions

---

### Post by hayz on 2007-01-01
> Download GPLCD. Burn it to a good quality CD just like you would a Linux distro.
Boot from the GPLCD.
You should see an NTFS partition at the front (to the left in the map across the top of the page) of the HDD.
-@Bartender thanx for the info but cant i use partition magic?
Cos wot u mentioned is just similar to what i saw on Partition magic when try to resize my HDD so that i can allocated an free/unused partition.. -Take a look @ the Screenshot...

-The aysiu's site is a good example of what one shuld see when Installing Thanks It was Very helpful

> If you get your Linux partitions built, then choose "manually partition" on the Ubuntu install CD and mount / to the primary ext3 partition (probably hda2 but that will depend on how you build it) and mount swap to the "linuxswap" partition you made (probably hda5 but again it's up to you)

-I think i culd be able to do that now, only if u can help me wit using the Partition magic..

---

### Post by hayz on 2007-01-01
**Where r my fellas?**:-k ](*,) ;)

---

### Post by adewale on 2007-01-02
@bartender the gpl cd maybe big for him to download cause he uses gprs just like me. so the only choice he has is to use partition magic

---

### Post by Bartender on 2007-01-02
Hey, I'm sorry -
I didn't ask about your bandwidth.  I usually do ask cause I'm on dial-up at home and can't do a #$*& thing.

I'm no expert, but too many people have said that Partition Magic gave them troubles.  Apparently it appears to work, but then they can't install Ubuntu because the install CD doesn't recognize the partitions.  Or something like that.

Besides, I can see from your screenshot that PM talks to you in Windows-speak (C drive, D drive) whereas GPLCD refers to everything in Linux-speak (/dev/hda1, /dev/hda5, etc.)  It's very important to write down or take a screenshot of the final GPLCD partition map because you want to be absolutely sure about your partitions when you've fired up the Ubuntu installCD.  It'd be too easy for me to make a mistake interpreting the PM partition labels.  

I'd be going, "Um, F drive is - er - is that hda3 or hda6 or....???"

But if PM is what you've got, then that's what you've got.  I don't know anything about maneuvering in PM.  I didn't know anything about GPLCD a few months ago!  If there's any way to practice on something other than your Windows HDD, I'd sure try that!

EDIT:  I imagine it'd be pointless to offer to mail you a few copies?

---

### Post by hayz on 2007-01-02
Ok Bartender no probs I get U.

I decided i should use the inbuilt partitioner(On the Ubuntu Cd)
Here are some Shots i took on another visit to d Ubuntu Installation.
-Hope dis helps..;) 

-Some Pls tell m if am on the right path:confused:

---

### Post by hayz on 2007-01-03
Hey Guys Where did yah all go?
I'm Still stuck O! - I am not true with d ubuntu installation problem.
Anyone take a look at the shots i posted?
Who's gon fire-up my anticipation to Use Linux?

---

### Post by Bartender on 2007-01-03
Sorry, hayz -
Everyone vanished on you, eh?  OK, those lameass extra partitions that the manufacturer put in there are boxing you in.  The Gnome partitioner sees three primaries and is going to balk at making a fourth one.  I'm not sure you can even force it to do so.  I was never able to.  

See in your second screenshot?  All three of the existing partitions are primary.

Fortunately, Linux isn't as fussy as Windows.  It can run from an extended partition.

I see in your third shot that you were preparing to resize hda1, where the Windows OS is installed.  But in your fourth shot it doesn't look like hda1 was resized.  Is that the case?

Without knowing the answer, I'll just plow ahead.  Resize hda1.  Do like you showed in your third attachment and click "resize".  Make sure it did the deed.

Now you should see a large chunk of disc that's "unallocated" in between hda1 and hda2.

Here's what I'd do next.  Check out this [thread]("http://www.ubuntuforums.org/showthread.php?t=329474").  Harrison resized his Windows partition (using a different method but same results) then just let Ubuntu install to the largest free space instead of manually partitioning.  

If you like that idea, then after you've seen the partitioner resize hda1 click "Cancel" and "Quit" to abort the install, then start over again. When you get to the first window you attached (Select a Disk) click on /dev/hda1, then click on "Use the largest continuous free space".  

Or, just click "Back" once or twice til you get back to that "Select a Disk" window and click the two settings I just described.  Either way, you have to be sure that hda1 was resized or you'll probly get an error message because the installer won't be able to find enuf free space.  

You're using an Ubuntu Dapper CD, right?  I'm running an Edgy install CD on my test PC as I type this.  It doesn't have the "Use largest continuous free space" option.  I don't know why they took that out of Edgy  :-?  

I believe that for your situation we're better off to let the installer make the decisions, just like Harrison did in that other thread.  Read post #5.

If the installer does the same thing as it did for Harrison, you'll end up with an extended partition in that free space and an operating Ubuntu install.  It'll install GRUB at the very front of the HDD, where the Windows MBR is now.  Next time you boot up after the installation, you'll get a GRUB window asking which OS you want to start.  Linux will be the default.  If you want Windows the default, it's not hard to change.  

But let's see if we can get you going with Linux first.

---

### Post by hayz on 2007-01-03
> I see in your third shot that you were preparing to resize hda1, where the Windows OS is installed.
-Yeah, I was making a demonstration if it was the right thing to do.

But in your fourth shot it doesn't look like hda1 was resized. Is that the case? -Yes, It was resized (in that shot i was thinkin if i made the resize in the 3rd shot i wuld jst go ahead and do the swap,ext3 etc in there)- u get it?

> Without knowing the answer, I'll just plow ahead. Resize hda1. Do like you showed in your third attachment and click "resize". Make sure it did the deed.
-Ok, i get that(i think i am getting somewhere) Take a look @ the 3rd shot, Should i allocate d size i want to remove frm hda1 in the "free Space following"?

> Now you should see a large chunk of disc that's "unallocated" in between hda1 and hda2. -I will get u a shot of that when its done.;) 

> Here's what I'd do next. Check out this thread. Harrison resized his Windows partition (using a different method but same results) then just let Ubuntu install to the largest free space instead of manually partitioning.

Yeah I like his Idea, but then I will like to Create A data partition[So i can keep my files]
-Therefore, I think I shuld Get a DVD disc(As much as i need to 1st copy my files{music,pictures,documents etc onto) and thn delete my entire "copied data off the Drive" to know the space i really av on the hda1 when i visit the ubuntu partitioner once more. -Hope u get me:-# 

Dont forget, I mentioned a data Partition. Hw do i create one? Can it be done thru the ubuntu installer? how? 

> Or, just click "Back" once or twice til you get back to that "Select a Disk" window and click the two settings I just described. Either way, you have to be sure that hda1 was resized or you'll probly get an error message because the installer won't be able to find enuf free space.
-I will make sure of that[No mistakes;) ]

> You're using an Ubuntu Dapper CD, right? -Yes(Version 6.06 LTS For 64bit Pc)

> I believe that for your situation we're better off to let the installer make the decisions, just like Harrison did in that other thread. Read post #5.

- I read and understood his simple analysis.

> If the installer does the same thing as it did for Harrison, you'll end up with an extended partition in that free space and an operating Ubuntu install. It'll install GRUB at the very front of the HDD, where the Windows MBR is now. Next time you boot up after the installation, you'll get a GRUB window asking which OS you want to start. Linux will be the default. If you want Windows the default, it's not hard to change.
-I didnt Get this last sentence very well..
----Ok Let Me Break It Down------

-Does an "Extended Partition" mean the Partition where everything linux needed(like swap etc) is enclosed?
-> It'll install GRUB at the very front of the HDD What's GRUB? nd y shuld it stay in front of Windows.

> where the Windows ** MBR** is now Dont know That Neither...

> Linux will be the default. -Is That A Good Thing to Do?

> If you want Windows the default, it's not hard to change Ok, thats Good to Hear:mrgreen: 




                 *Pls dont be Bored by my Questions if they r too much,
                   Its jst me I ask Questions to be In the know;)

---

### Post by hayz on 2007-01-04
Where r u guys?
Bartender, U r still needed here;)

---

### Post by adewale on 2007-01-04
hayz grub is just like a thing that tells your computer what os to boot and it use mbr don't bother about this. ok so have u backed ur system to a disc? and ur uncle finally surfaced and am really mad at him and going to run a live cd on his laptop and tell him i've installed ubuntu. thats should scare him a little.

---

### Post by Bartender on 2007-01-04
Hi, hayz - 
When you're ready to do some Linux work, I'm getting ready for bed.  When you're sleeping, I'm looking at your posts.
I work a rotating shift, so unfortunately for me I was up in the middle of the night a few nights ago, hangin' out at the forums while on break.

I'm thinking there are two ways (probly more but you know what I mean) to make a data partition.  

First off, think of the extended partition as a box.  Once you've built the box, you can build several "logical" partitions inside the box.  Both Windows and Linux can access logical partitions for data, but the Windows OS can't boot from within the box, so it has to be in a primary partition.  If I had a Dell or HP PC to tear into I'd experiment with trying to take the data from the two extra primary partitions and move that data inside the extended box, but I'm not sure how (or if) that could be done.

Anyway, if we wanted to stick with letting the Ubuntu partitioner install to the largest free space, then I'd do that.  See if we can get Ubuntu running.  Then I'd go back in with the LiveCD, resize the main Ubuntu partition, referred to as "/".  (I know that seems a little weird but that's what it is!)  After resizing it, you'll have created an unallocated space.  Right-click on the unallocated space (if right-clicking on the map itself doesn't work, go down to the text part and right-click on the "unallocated" line) and click "New", then format it as vfat if you want to create a partition that both Windows and Linux can access. 

For some extra help on how to click on the correct buttons, look at this blog 
[http://www.sroyc.blogspot.com/](http://www.sroyc.blogspot.com/) 
scroll past the "PCLOS" dual-boot guide to the partitioning guide.  I wrote it for use with a GParted LiveCD, so using the version on the Ubuntu CD is a little different, but I think it'll help you get an idea.

The other way to get your data partition would be to manually partition the whole thing instead of letting the Ubuntu partitioner do it.  You'd resize hda1, then create the extended partition, then create an "ext3" partition for /, a "linuxswap" partition for swap, and a "vfat" (FAT32) partition for shared data.  All of this within the extended "box".

OK, I'm getting pretty far out on a limb here.  I've never done all this, but it makes sense to me based on the partitioning that I have done, and from what I've picked up on the forums recently regarding working around the existing partitions already crammed in there by the manufacturers.

I'm sorry, i kinda sped thru the GRUB part.  My wife was wanting me to stop hanging out with my geek community and spend some time with her.  

GRUB is the bootloader for Ubuntu.  There's at least one other bootloader for Linux, LILO, but let's not get off the subject.  GRUB's job is to get your Linux OS booted.  It comes into play after you've turned on your PC and before the Linux OS starts to boot.

This is another area where the Linux solution is so much more elegant than Windows.  GRUB is very customizable, and can even be detached from the OS in order to guide the PC back to the OS.  For the majority of people dual-booting Windows and Ubuntu, we just let GRUB install itself (well, part of itself but again let's not get off-subject) to Windows' MBR.  MBR is what starts Windows.

Before you install Linux, the Windows MBR shares the hard drive with no one.  It's MBR points the PC to the OS, and you see Windows start.  After you've installed Linux, you'll see a DOS-looking screen come up asking which OS you want to start.

What I meant by "default" was that if you don't touch the keyboard, Linux will boot after - um - 10 seconds, I think, not Windows.  That's all.  Windows will be in the list, but if you're getting a cup of coffee when GRUB comes up your PC will be at the Ubuntu username screen when you get back.  You have to be there to tap down to Windows, then hit Enter.

Once you have Ubuntu running, you can edit GRUB's menu.lst to make Windows the default OS instead of Linux (although why anyone would want to do this is beyond me ;) ) and you can edit the menu.lst so that it waits longer before proceeding to the default OS.

Both of those tweaks are really simple to do.  The first time you do it it won't seem that way, but it is.  

Well, I've gotta get ready to go to work now.  Dayshift, not niteshift.  Will be back to check up on your progress.  I see Harrison posted a screenshot over on that other thread.  Those extra partitions sure do make things messy.  I'm attaching a screenshot of my dual-boot.  This is from my home-built PC, using a genuine Windows CD.  No extra partitions to get in the way.  Notice the "vfat" partition for sharing data.

EDIT:  Hey, that larger vfat partition of yours - is that your "recovery" partition?  Do you have a separate recoveryCD or is it all on the HDD?  I'm just checking cause I want to make sure you've got a way to rebuild Windows if you have to.  Have you saved copies of any important data on this HDD?

---

### Post by hayz on 2007-01-04
> EDIT: Hey, that larger vfat partition of yours - is that your "recovery" partition? Do you have a separate recoveryCD or is it all on the HDD? I'm just checking cause I want to make sure you've got a way to rebuild Windows if you have to. Have you saved copies of any important data on this HDD?

-Yes It is.

I shuld go into the live Cd once again to see what i can do.
Will Post You something;)

---

### Post by tchoklat on 2007-01-05
UBUNTU LiveCD will partition your HDD for you and leave your XP untouched. At boot up you will have the option of booting into XP or into Ubuntu. Choose auto paruition it is quite safe. You can always adjust the size of the partitions with GPartEd after which you can download with Ubuntu's Synaptic package manager


tchoklat

---

### Post by hayz on 2007-01-06
Hello Yah All,
           Am sorry i avnt posted my result after another visit to Ubuntu installation...
Here, It is...
                    Once again i inserted my ubuntu LiveCd into my cd Drive it Loads up and got into the ubuntu interface. Not wasting much time i headed for the Installation[Partitioning Aspect] Tried Resizing the Ntfs Windows Partition, allocated 20GB to the unallocated and it said it was carrying out the action.
    I thought every thing was kool not until for about 5mins my system was stuk[hung]. I chilld thinking it was performing the task but in another 10mins it was still the Same Hanged Screen i was seeing. To the Extent that i didnt know when i dozzed Off, waking up about 20mins Later I met A blank Screen I went OOOOOO thats It! I av done wot i didnt want.
     So i decided to put it off wit the Emergency Turn Of[Holing down the Power button for some seconds] And i turned it on Again.

       THANK GD IT BOOTED TO WINDOWS.:mrgreen: 
                                                                   -Guys What UP?:-k ;)

---

### Post by Bartender on 2007-01-06
Damn, hayz, the hairs were standing up on the back of my neck while reading that last post.  I was going, Oh, please, don't tell me his Windows partition is wrecked...

OK, nothing like a little close call to scare everyone back to reality.  Before we go any further with this, have you copied your recovery partition?  Maybe even copied it twice?  Have you copied your important personal data?

The times I've tried to partition with either an Ubuntu install CD or with GPartED everything went just like it should.  As soon as somebody's goes sideways I'm out of my league.  

Sometimes certain hardware configurations or chipsets on the motherboard or what have you don't behave so well for God knows what reasons.  

All I can suggest at this point is to play this very conservatively.  

I know we talked about broadband before...is it completely unavailable?  Because Edgy offers the option of resizing the main partition on it's "Select a Disk" page (same page as your first attachment in post #23), which is different from Dapper's choices.  The Edgy installer might work.  You drag the little bar back to whatever size you want and it'll try to resize the partition.

Of course, if you can get access to some broadband, I'd say download [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) at the same time!

Are you sure you've got the Windows data shoved over to the left by defragging several times?

At this point I'm just guessing  :-k

EDIT:  Do you think it made the partition, or gave up?  Go into Disk Management in XP and see if you can tell

---

### Post by hayz on 2007-01-07
> Damn, hayz, the hairs were standing up on the back of my neck while reading that last post.
-It Shuld Cos in my case it was my head Standing Up..

> I was going, Oh, please, don't tell me his Windows partition is wrecked...

-Me too, I was going thats Good U ve done it.

> OK, nothing like a little close call to scare everyone back to reality
-Welcome Back to reality.

> have you copied your recovery partition?
-I av tried copyin that several times but it keeps telling me some sort of error When @ 55%,
But recently i was able to get to copy 2 of the 4 disk needed for partition but it gave error on the disk no 3&4. I am just not going to waste anymore disc on that...:mad: 

> Have you copied your important personal data?
-Yeah,I do that regularly.

> I know we talked about broadband before...is it completely unavailable?
-It is available in Cyber cafes but isnt those Os in GBs{to download a GB in a cafe culd take days even a week}

> Of course, if you can get access to some broadband, I'd say download [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) at the same time!

-I can access some broadband but not in those cafes we av got here[ Imagine me making the download and am told by the attendant that the Server is Down](*,) ]

> Are you sure you've got the Windows data shoved over to the left by defragging several times?

What???:-k 
> 
Do you think it made the partition, or gave up? Go into Disk Management in XP and see if you can tell
Where is that? Will check.. thanks;)




                     -So what Other Options Av I got?:-k

---

### Post by psycosmyth on 2007-01-07
crap......slow pst

---

