---
title: "Installation into second dual boot HD"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by allochthonous on 2007-03-04
I am trying to set up a triple boot system. HDD 1 (20 gb) is on the primary master, HDD 2 (13.6 gb) is on the primary slave. HDD 1 contains WinXP, HDD 2 contains Win98. I do not use a boot menu, but rather select which HD boots in my BIOS. 

I want to leave HDD 1 completely alone, but create a dual boot on HDD 2, leaving 5 gb for Win98 and using the other 7 gb for Linux (in this case, Ubuntu)

I used GParted and created an unassigned partition in the 7 gb, then proceeded with the Ubuntu installation into that partition. But when it said where it was putting the GRUB loader, it indicated hd0, which looked to me like it may have been HDD 1.  Everywhere else it referred to the hard drives as hda and hdb, so I changed the hd0 to hdb, but the installation failed. 

I opened the case and plugged the HDD 2 into the primary master so it would be the only HD visible, and reformatted the partition into unassigned. I again installed Ubuntu into this partition, using the default settings.  Afterwards, I replugged in both drives and booted to the HDD 2. The GRUB loader works, but Ubuntu fails to load. Win98 loads fine.

What should I do now? If i install Ubuntu with both drives installed, how do I designate that I want GRUB on HDD 2? My gut says that I would need to change hd0 to hd1.

Thanks

Paul

---

### Post by bulldog on 2007-03-04
If you can put the output of```
sudo fdisk -l (l as in like)
``` to the forum,and a copy of your menu.lst```
cat /boot/grub/menu.lst
``` we can have a look what's wrong.

I think it points to the wrong device because you connected a disk afterwards again.
A simple solution would be,connect the ubuntu disk as the primary boot device like you did when you installed ubuntu.
Connect the former primary as the secundary and you're ready to go with ubuntu.
Windows XP will not boot however,but that's a minor thing and can be solved easily.

---

### Post by allochthonous on 2007-03-04
I don't mind reintalling Ubuntu (and removing GRUB if i have to, as long as someone tells me how) but what hd do i indicate for the installation of GRUB?

I can try to get those outputs, but how do i get the outputs to a file to move to another system?

PK

---

### Post by louieb on 2007-03-04
Look like you about have it figured out.
You confused GRUB or Linux when you switched the drives around after installing Ubuntu. I'm kinda surprised  that Win98 worked. 
There are more that a couple of ways to get Ubuntu to boot.
One is to tweak the files [COLOR=Magenta]/boot/grub/menu.lst [/COLOR] and [COLOR=Magenta]/etc/fstab[/COLOR] this would be the fastest if you know what your doing. But its the hardest (lots of learning) if your new to Linux.

If it were mine I would leave the Linux/Win98 drive as master. I am assuming that Linux and Win98 boot when its installed that way.
Then plug in the  XP drive in as slave.  Now to get GRUB to boot XP and at the same time trick XP into thinking its on the master drive.   You edit /boot/grub/menu.lst.
Boot to Ubuntu.
Press Alt+F2 and enter ```
gksudo gedit /boot/grub/menu.lst
```Press run and enter your password.
Add the follow to the very bottom of the file.
```
title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1
      boot
```
That is how my P2 is set up and it works.
Hello Bulldog I see your back have not seen much of your work lately.

---

### Post by allochthonous on 2007-03-04
I really did not want to involve the XP drive in Grub. I want to leave the XP drive as it is and select to boot to it via the BIOS. Now, I have not tried plugging it as slave and the Win98/Linux HD as master and see if everything boots the way I want it.

Why is the HD referred to in the Ubuntu setup for where to put Grub "hd0" - what drive is this?  How would I refer to the slave (Win98) drive?  

Can I clean the slate and start over and get it to do what I want to do?

PK

---

### Post by louieb on 2007-03-04
Never tried set up Dual boot the way you want it. The method in my previous post works and your XP drive except for maybe the jumper is untouched. 

When GRUB is installed it ask BIOS what is the the first boot drive and calls it hd0. So if you have both plugged in: XP drive as master and Win98 as slave. GRUB would  call the Win98   drive hd1. 

GRUB is a complex program, to the point that its almost an operating system itself. You may want to check out the Dual Boot link in my signature, lots of good stuff there.

Good luck, have fun.
louie

---

### Post by allochthonous on 2007-03-04
OK, so if I change "hd0" to "hd1" in the Grub setup during installation, that should do it?

I know how to remove Ubuntu (just delete that partition, right??) but how do I get rid of Grub?

PK

---

### Post by louieb on 2007-03-04
You don't get rid of GRUB you replace it with something else (Do you have your win install disks).  The GRUB code in the MBR is just a pointer to the grub program in your linux install. SO IF YOU REMOVE Ubuntu and don't replace GRUB your up the creek without a paddle.

---

### Post by allochthonous on 2007-03-04
Yes, I have my install disks. From what I can gather from your Dual Boot link in your profile, I can create a boot floppy and use the fdisk/mbr command. Can I use a Windows created boot floppy, or does it have to be the special downloaded one?

Once the MBR points back to Windows, then I can delete the partitions?

Then I can try reinstalling Ubuntu, but change the grub location to hd1.

Right?


pk

---

### Post by louieb on 2007-03-05
That he way I understand it.
 In truth all you need to do is reinstall Ubuntu  Just format the Ubuntu partition as a part of the installation,
When you change hd0 to hd1 don't forget to include   the [COLOR=Magenta]parenthesis[/COLOR] around [COLOR=Magenta](hd1)[/COLOR] . 

But its good you have the install disk just in case. You should see the panic of those that don't and something goes wrong. But your past that point. Usually if something goes wrong its during the partition resize part of the install 
Good luck.

---

### Post by allochthonous on 2007-03-06
OK, that did not work.

I plugged in the 13.6 drive into the master (leaving the 20 unhooked) and booted to the floppy. I used the fdisk/mbr command to get rid of Grub on the 13.6. I rebooted to make sure that Win98 came up, which it did.

Then I put the 20 back as master and the 13.6 as slave and booted to the Ubuntu CD. I reclaimed the previous Ubuntu installation and then reran the install process, designating (hd1) as the location for Grub.

When I selected the 13.6 as the boot HDD in the BIOS, the Grub loader menu came up, which was what I wanted, however, XP showed up in the list, which kinda surprised me.

When I selected XP from the menu, 98 booted. When I selected 98, XP booted. When I tried to boot Ubuntu, it said that it the partition did not exist.

Ack!!!

I want the 20 (XP) to be untouched and isolated and the 13.6 to have the boot menu to choose either 98 or Ubuntu.  I want to be able to select which drive to boot from the BIOS. 

I suppose that if i can get Grub to be the overall boot menu, rather than use the BIOS, then that would be OK too.  Should I let Grub install on the (hd0) - XP drive then leave that HDD as the boot drive in the BIOS?  

Where do I go from here?  Repeat the steps that I took above to reset the MBR?

I really don't want to flip the 98/Linux HDD to the master, as the cable will not reach in that configuration and I really do not want to move the drives.

PK

PK

---

### Post by confused57 on 2007-03-06
You can try this:
Select your slave drive with Ubuntu to boot first in bios, in the grub menu at bootup, highlight your Ubuntu entry, press "e" to edit, then change your root to (hd0,1), then press "b" to boot.

(hd0,1) is the 2nd partition on the disk, (hd0,2) would be the 3rd partition...depends on where your Ubuntu root partition is.

Post back if this works, then you can set your system up "permanently" this way.

---

### Post by louieb on 2007-03-07
Well you got Ubuntu installed or GRUB would not have come up.
Your  XP drive is untouched. or XP would not have booted when you selected that drive in BIOS. 

Your and oddball :)in more that one way. Never seen GRUB do XP or Win98 right and screw Linux up. It usually the other way around. :confused:Try confused57 suggestion but I don't think it will work because of the your BIOS is reporting  a different drive setup from when you did the install. I believe you have 1 or 2 more files to tweak. 

But the fact that you insist on using  BIOS to determine what operating system to boot means  you got to do some extra work to get it the way you want it. 

Now  you need to  edit your /boot/grub/menu.lst file to get XP out of the menu 
and  fix the Ubuntu entry.
You also may need to edit /etc/fstab and /boot/grub/device.map. 

Since I'm to lazy to explain how to mount a Linux partition  read /write using the Ubuntu Live CD. Do me a favor and get and burn the Puppy Linux Live CD. 

Once you get Puppy up and running and connected to the net. Click on the Drive Icon then click on the mount button for you Linux partition. This opens the file manager. And post the content of the following 3 files.[LIST]
[*]/boot/grub/menu.lst
[*]/boot/grub/device.map
[*]/etc/fstab[/LIST]And for good measure open a terminal window in Puppy and post the output of fdsk -l that an lowercase l as in little.

Now rock on brother and get that stuff and we will get you set up .:guitar:

---

### Post by allochthonous on 2007-03-07
Technically it didn't do either right, since selecting XP booted 98 and vice versa.

OK, if it would be easier, I am willing to concede to leaving the 20 gb XP HDD as the master boot drive and leaving the 13.6 98 drive as the slave, with one partition as 98 and one as Ubuntu, and installing Grub on the XP drive so that when I boot, i can select the OS from there.

Is that possible??

Should I start over and when I install Ubuntu again, let it install Grub on (hd0)?

I don't think that confused57's idea will work either, because Ubuntu is not installed on hd0, it is on hd1.


PK

---

### Post by louieb on 2007-03-07
> **allochthonous said:**
> Technically it didn't do either right, since selecting XP booted 98 and vice versa.
Hey windows is windows, right? 
> I am willing to concede to leaving the 20 gb XP HDD as the master boot drive and leaving the 13.6 98 drive as the slave, with one partition as 98 and one as Ubuntu, and installing Grub on the XP drive so that when I boot, i can select the OS from there.

Thats probably the most common way to set up a computer to dual boot Linux and windows on a computer w/2 hard drives. The installer should not have any problem configuring GRUB so that all  three to boot. It might even label XP and Win98 right this time.

---

### Post by confused57 on 2007-03-07
> **allochthonous said:**
> Technically it didn't do either right, since selecting XP booted 98 and vice versa.

OK, if it would be easier, I am willing to concede to leaving the 20 gb XP HDD as the master boot drive and leaving the 13.6 98 drive as the slave, with one partition as 98 and one as Ubuntu, and installing Grub on the XP drive so that when I boot, i can select the OS from there.

Is that possible??

Should I start over and when I install Ubuntu again, let it install Grub on (hd0)?

I don't think that confused57's idea will work either, because Ubuntu is not installed on hd0, it is on hd1.


PK
Why don't you try my idea?  I honestly believe it will work, I can explain why your Windows entries are reversed also(Least I think I could last night?).
When you select your current hdb (hd1) to boot first in bios, it automatically is recognized as hd0 in grub and hda is recognized as hd1...that's why your Windows entries are reversed(must admit, I've never seen this before) when you boot first to your hdb and that is why you need to change your root in Ubuntu to (hd0,1)...I've helped enough people with this problem to know it works.  I thought this would be your easiest solution, rather than reinstall...it's your choice.

Added:  Then again, I may be completely wrong for you system...just basing my suggestion on experiences I've seen from other posters.

---

### Post by louieb on 2007-03-07
> **confused57 said:**
> Why don't you try my idea?  I honestly believe it will work, I can explain why your Windows entries are reversed also(Least I think I could last night?).
He is learning. But I also think he probably needs to check the root= in the kernel line to make sure it matches up with the root (hd?,?) line. That why I asked for the other stuff. Maybe he will. Your method is a fast and easy way to see if fixing his menu.lst will fix the whole problem. But even at that we need the other stuff to give him any more than a guess?

The louieb warranty: :twisted:  If it breaks, you get to keep both pieces.

---

### Post by confused57 on 2007-03-07
> **louieb said:**
> He is learning. But I also think he probably needs to check the root= in the kernel line to make sure it matches up with the root (hd?,?) line. That why I asked for the other stuff. Maybe he will. Your method is a fast and easy way to see if fixing his menu.lst will fix the whole problem. But even at that we need the other stuff to give him any more than a guess?

The louieb warranty: :twisted:  If it breaks, you get to keep both pieces.
Yes, that was my intention...my suggestion would be a fast & easy method to see if he could get his system to boot.  The root in the kernel line is based on which controller the hard drive is connected to, therefore this shouldn't need to be changed.  I don't offer any guarantees, either expressed or implied...especially since helping in the forum is voluntary, unless the check's in the mail.
It's a pretty steep learning curve, and your suggestions are quite accurate & clearly explained and will help in his Linux "education".

Added:  Guess all he'd need to do for his Window's entries is to change the title.  I'm not sure about my original hypothesis about the entries being reversed.  I'll have to ponder it and do a little more ciphering.

---

### Post by louieb on 2007-03-07
**allochthonous ** has been clear about what his setup is,  what he did and what happened. Kinda nice to see that even if he is a bit bullheaded.
I've been fat fingering in another thread [http://ubuntuforums.org/showthread.php?p=2259829](http://ubuntuforums.org/showthread.php?p=2259829) and a guy name Gutti  came up with this [http://fedorajim.googlepages.com/dualbootlinux%26xpthesafeway...](http://fedorajim.googlepages.com/dualbootlinux%26xpthesafeway...) It seems like a pretty sane way to duel boot with 2 hard drives.

---

### Post by confused57 on 2007-03-07
> **louieb said:**
> **allochthonous ** has been clear about what his setup is,  what he did and what happened. Kinda nice to see that even if he is a bit bullheaded.
I've been fat fingering in another thread [http://ubuntuforums.org/showthread.php?p=2259829](http://ubuntuforums.org/showthread.php?p=2259829) and a guy name Gutti  came up with this [http://fedorajim.googlepages.com/dualbootlinux%26xpthesafeway...](http://fedorajim.googlepages.com/dualbootlinux%26xpthesafeway...) It seems like a pretty sane way to duel boot with 2 hard drives.
Looks pretty similar to this "howto":
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

allochthonous described his setup very well, that's why I was able to make a suggestion...it's wise to weigh all options, before blindly following someone's advice, mine included.

---

### Post by allochthonous on 2007-03-07
Bullheaded???  Why....the nerve!! (most of my friends call it "anal retentive") :) 

I do indeed like to get several opinions before I plunge into something.

But, you know what, I AM learning, and this is my "learning" system. There really isn't much I can mess up. I am pretty much just using the system to backup my pictures from my main system, so if I lose XP (and have to reinstall) its not a huge deal, just time.  It's an old Dell XPS T450 that I upgraded to an 800, 384 MB of RAM, tossed in a second HDD, 64 MB Radeon 7000 that I got for $2....I thought it would be perfect to use to mess around (and learn about) Linux as a real install rather than a Live CD.

I had a dual boot Win98/Linux (PCLinuxOS) AMD K6-2 550. But it ran like crap so I didn't mess with it much.

As I think about it, I guess it would be nice to be able to just leave the BIOS as is and select the OS from the XP drive (master).  I just originally thought it would be cool to have two completely independent OS/HDD's (three with Linux)  - like having two computers in one.

So.....guide me oh wise ones.  

What should I do to acheive this goal?

If you want, I can still try the things that you suggested, if for anything, just out of curiosity.

PK

---

### Post by confused57 on 2007-03-07
> **allochthonous said:**
> Bullheaded???  Why....the nerve!! (most of my friends call it "anal retentive") :) 

I do indeed like to get several opinions before I plunge into something.

But, you know what, I AM learning, and this is my "learning" system. There really isn't much I can mess up. I am pretty much just using the system to backup my pictures from my main system, so if I lose XP (and have to reinstall) its not a huge deal, just time.  It's an old Dell XPS T450 that I upgraded to an 800, 384 MB of RAM, tossed in a second HDD, 64 MB Radeon 7000 that I got for $2....I thought it would be perfect to use to mess around (and learn about) Linux as a real install rather than a Live CD.

I had a dual boot Win98/Linux (PCLinuxOS) AMD K6-2 550. But it ran like crap so I didn't mess with it much.

As I think about it, I guess it would be nice to be able to just leave the BIOS as is and select the OS from the XP drive (master).  I just originally thought it would be cool to have two completely independent OS/HDD's (three with Linux)  - like having two computers in one.

So.....guide me oh wise ones.  

What should I do to acheive this goal?

If you want, I can still try the things that you suggested, if for anything, just out of curiosity.

PK

Ok, Mr. bullheaded "anal retentive"(haven't heard that in a long time), I've consulted the oracles, and they say for you to give what I suggested a try...to satisfy your curiosity and mine, if it'll actually work.
   The changes I suggested are only temporary, so they won't affect your system, but you'll know if it works...if it works, then you can make it permanent.

---

### Post by louieb on 2007-03-07
> **allochthonous said:**
> 
So.....guide me oh wise ones.  
I bet your motto is: If its not broke tweak it till it is.  I'm good at breaking stuff.  Ok go ahead and install the stuff the way you originally had it.  Then in XP install [fs-driver]("http://www.fs-driver.org/") so you can modify Ubuntu's configuration files as needed. It may be as easy as confused57 thinks and its just a matter of tweaking the menu.lst file. 
I'll check back from time to time and I bet you'll get it working the way you originally wanted.:lolflag:

---

### Post by allochthonous on 2007-03-07
Actually, louieb, I am just the opposite.  I always want to make sure that everything is as "safe and sound" as possible...almost to the point of obsessive compulsive.

I didn't mean "So.....guide me oh wise ones" to be sarcastic.  I really am seeking your advice as someone who knows a whole heck of a lot more about Linux and bootloaders than me.

Bottom line...what do you guys think would be the best configuration given my setup?

PK

---

### Post by confused57 on 2007-03-07
> **allochthonous said:**
> Actually, louieb, I am just the opposite.  I always want to make sure that everything is as "safe and sound" as possible...almost to the point of obsessive compulsive.

I didn't mean "So.....guide me oh wise ones" to be sarcastic.  I really am seeking your advice as someone who knows a whole heck of a lot more about Linux and bootloaders than me.

Bottom line...what do you guys think would be the best configuration given my setup?

PK
I'm also the sort of person who likes to "play it safe", that's why I set my initial dualboot up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

louieb's suggestion in reply #4 is a great way to have your system setup, but you had mentioned your cable wouldn't reach set up this way...that's why I suggested the "temporary" way I mentioned to get your system booting with 98/Ubuntu on the slave drive.
I personally think it would be a good idea to leave your XP drive "untouched", booting it with grub from your 98/Ubuntu drive.

I probably shouldn't have intruded, louieb had everything under control, but thought I'd give you an option to get your system working the way you had it set up(XP master, 98/Ubuntu slave)...if you don't want to try what I suggested earlier:
set bios to boot first to your 98/Ubuntu drive
boot your computer
highlight your Ubuntu entry
press "e" to edit
change root (hd1,1) to root (hd0,1)
press "b" to boot

You're able to boot XP & 98 booting first to your slave drive, so you're 66.7% of the way to getting your system working.  If the above works, you can make it permanent in your /boot/grub/menu.lst & leave your system set up this way.

If you want to reinstall Ubuntu, hopefully without installing grub to your XP mbr...set your slave drive in bios to boot before your Windows drive, before installing Ubuntu, this should make your slave drive recognized as hd0 by grub...you can always specify /dev/hdb as the drive to install grub to the mbr.

See the first link in my signature for some great info about grub, Super Grub Disk, GAG, mounting different filesystems, etc.

---

### Post by louieb on 2007-03-08
> **confused57 said:**
> I probably shouldn't have intruded, louieb had everything under control,
Two heads are better that one. You have added valuable input. Liked your how to Dual Boot. (post 20)  I've put it in my bookmarks. It will save me a lot of typing. 

Lets see 3 squared is 9. Factor in two hard drives. Anyway that come to a bunch of different ways you can set up a triple boot system. I can see the point of being able to use BIOS to choose which disk to boot first. If there is a problem with one of the hard drives then just boot the other one. 
At times I don't alway play safe. I'll try something just to see if it works. Don't ask me about how much I had to pay a pro to fix my pickup's A/C   after I decided I could do it myself.

---

### Post by confused57 on 2007-03-08
> **louieb said:**
> Two heads are better that one. You have added valuable input. Liked your how to Dual Boot. (post 20)  I've put it in my bookmarks. It will save me a lot of typing. 

Lets see 3 squared is 9. Factor in two hard drives. Anyway that come to a bunch of different ways you can set up a triple boot system. I can see the point of being able to use BIOS to choose which disk to boot first. If there is a problem with one of the hard drives then just boot the other one. 
At times I don't alway play safe. I'll try something just to see if it works. Don't ask me about how much I had to pay a pro to fix my pickup's A/C   after I decided I could do it myself.

Thanks, I'd didn't want to feel like a 5th wheel(or is it 3rd) here...you're right, there are numerous ways to set up a triple boot, especially with 2 hard drives & bios is an excellent way to do so for the reason you mentioned.  It's good to put some thought into how a person wants to set their system up, but there comes a time to actually implement the plan...doesn't work try something else...as long as any important data is backed up.

I've had instances of assisting someone, where I've thought...someone, please give me a little help here...although, I don't think you needed any in this thread.

Years ago, I used to try to do minor "fixes" to my vehicles, replace brakes pads, shoes, radiators, tuneup, distributor replacement, etc...changing the oil is about it now...cheaper in the long run to take it a garage...but I see your point.

allochthonous, hope you don't mind a couple of old(er) f**ts trying to enlighten you with our profound introspections.

---

### Post by allochthonous on 2007-03-09
Of course I don't mind.  

I will reread this thread this evening and will attempt some of the suggestions either tonight or tomorrow. 

I have been a little preoccupied with a build (my first) that did not go so smoothly and a 10 month old daughter (and work, and housework, and errands, and....)

So the concensus is that I should stick with XP as master, 98/Linux as slave, leave Grub on the slave, boot regularly to the slave via the BIOS, and select the OS from there, whether it be XP, 98, or Linux?  If I want to avoid the Grub and go straight to XP, I can select via the BIOS.

Is that right?


PK

---

### Post by confused57 on 2007-03-09
> **allochthonous said:**
> Of course I don't mind.  

I will reread this thread this evening and will attempt some of the suggestions either tonight or tomorrow. 

I have been a little preoccupied with a build (my first) that did not go so smoothly and a 10 month old daughter (and work, and housework, and errands, and....)

So the concensus is that I should stick with XP as master, 98/Linux as slave, leave Grub on the slave, boot regularly to the slave via the BIOS, and select the OS from there, whether it be XP, 98, or Linux?  If I want to avoid the Grub and go straight to XP, I can select via the BIOS.

Is that right?


PK
Sounds like you're pretty busy, don't know how you find time for Ubuntu...your system "should" work OK set up this way.  Try the "trick" I described earlier, it's only temporary so it won't affect your current setup, but it'll let you know if your system will boot this way:

> set bios to boot first to your 98/Ubuntu drive
boot your computer
highlight your Ubuntu entry
press "e" to edit
change root (hd1,1) to root (hd0,1)
press "b" to boot

---

### Post by allochthonous on 2007-03-09
OK, you were right.  That change did indeed boot Ubuntu.

So now what should I do to make the changes permanent?  Do I need to follow the instructions in post #13? I already have a Puppy CD.

I would like to keep both versions of Windows in the boot menu, if possible.



PK

---

### Post by louieb on 2007-03-09
Its simple to make the changes permanent now that you can boot Ubuntu.
While in Ubuntu Press Alt+F2 and enter:
```
gksudo gedit  /boot/grub/menu.lst
```Press run and enter your password.
Down near the bottom you will find a few (probably 2 or 4) menu entries for Ubuntu 
change root (hd1,1) to root (hd0,1) 
and while your there might as well fix the title lines for XP and win98. You can make the title whatever you want displayed in the grub menu.
Save the file and exit. That should work. 
One bit of warning there is a chance you will have to fix you menu after a kernel update. Make sure you have a backup copy of your menu.lst before you press that orange update square at the top of the screen.
Have fun, 
Good lord a 10 month daughter :KS been a while since I had a little one around. My youngest graduates from college this spring..:lolflag:

---

### Post by allochthonous on 2007-03-09
How do I back up that file? And how do i restore it if it gets messed up after the update?

PK

---

### Post by louieb on 2007-03-09
You can back it up just like in windows. When in the editor Just do a file>save as ... and name it something like menu.lst.bak1. Or in gedit  edit>preferences there is a box you can check to get gedit to make a copy.

To restore you use the confused57 method of booting Ubuntu. The do the same edit I described in post #31. The backup is there for you to look and see what you did before. (gedit has tabbed editing just like Firefox has tabbed browsing).     

There is a way to make the updater do it automatically. believe it has something with the groot line in the auto-magic section of the file. But I never had a reason to do it so I'm not sure how. Perhaps confused57 know something about it.

Want a fish swimming around the screen? 
press Alt+F2 and enter ```
free the fish
```go that one from this thread [http://ubuntuforums.org/showthread.php?t=380500](http://ubuntuforums.org/showthread.php?t=380500)

---

### Post by allochthonous on 2007-03-09
OK.

Confused57, is there an easier way to restore the file?

I was able to successfully (and accurately) boot to all three OS's... YAY!!

Now, is there a way to make the XP entry the default that is highlighted and boots if nothing is done?

Will there be any adverse effects if i just leave the system to boot from the slave all the time or should I switch in the BIOS if i want to consistently boot to XP and only occasionally boot to Linux/98?

pk

---

### Post by confused57 on 2007-03-09
> **allochthonous said:**
> OK.

Confused57, is there an easier way to restore the file?

I was able to successfully (and accurately) boot to all three OS's... YAY!!

Now, is there a way to make the XP entry the default that is highlighted and boots if nothing is done?

Will there be any adverse effects if i just leave the system to boot from the slave all the time or should I switch in the BIOS if i want to consistently boot to XP and only occasionally boot to Linux/98?

pk
You can make a backup of your menu.lst by:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
if you need to restore from your backup:
```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
```

No, there's no harm in leaving your system set up this way.

Here's how to change the default OS you want booted:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

louieb is right about needing to change the groot line:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
when you have a kernel update, update-grub is run, which looks at this line & uses it to assign your root partition to the kernel entries in your menu.lst.

You might want to bookmark Herman's( a forum member) site:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
most of what I know about grub & bootloaders I learned from his site.

Glad it worked, sometimes I'm right...if I can just convince my wife of that.

---

### Post by allochthonous on 2007-03-11
I have booted to XP and Ubuntu several times, and everything seems to be working great!  

I ran the update and did have to go in and edit the (hd1,1) again. So editing that groot line will prevent me from needing to do that after the next kernel update?

Thanks a ton for your time and patience.  I have found that Linux communities are the best - always friendly and willing to help. I wish I had the time to really dive into Linux and learn how it ticks so I could help spread the word.   I (like many others) would love to see it catch on and be used to make computers more accessible to everyone across the world.  I do like Windows too, but it can be so cost prohibitive, especially when you are trying to resurrect an old machine that would be good enough for a poor kid or elderly person, but not worth paying $100 for an OS.  Know what I mean??


PK

---

