---
title: "new hd has messed things up..."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-23
Im in my first"real"trouble since installing ubunto recently.
As my xp is on main40g hd and ubunto is only on small 3.2g slave i took some advice and got a new(well..old)20g drive off a friend.

Anyway,just to do an initial "check" i plugged the new hd into the spare connector on the dvd-rom cable.At first it showed up in both ubunto and xp.
So i tried to use gparted to do it`s thing till i realised i might need the cd version(gave ubunto live to friend).

Anyway to get to the point i unplugged the cable from the dvd-rom so as to make more room and put the hd in properly then i went and got the gparted iso and after putting the cables and hd back in i suddenly started getting problems at the bios flash boot up screen......

So i go back into the bios and none of my hd`s are listed and if i reset them to auto still nothing.It`s just keeps comming back "NOT INSTALLED"

Ive been booting xp/ubunto fine till now (bar my setup probs).

IVe payed about with the IDE HDD AUTO DETECTION and even the boot order is no longer allowing me to set anything...all"disabled"

This sort off stuff is a wee bit beyond me.....any ideas please anybody??

---

### Post by TFX360 on 2006-08-23
Get a live-cd and see what gparted says via the live-cd.


Kind regards,


TFX

---

### Post by xpod on 2006-08-23
ive got it here but i cant even get the pc to boot from anything...let alone the cd...all BIOS FEATURES SETUP are

   BIOS Flash protection   :auto
   1st boot device         :disabled
   2nd boot device         :disabled
   3rd boot device         :disabled
   Floppy drive seek       :disabled

The top ones the only thing i can change now......I know the gparted cd works cause i had a quick look before all went awol...

I`ll go switch it off n on and see what happens with the cd in this time.

Thanks for the help

edit:cant even get it to open cd now.....restarting just takes it to bios flash screen that goes through the very slow motions of NOT DETECTING my usual hd`s and dvd-rom???????????   I can change anything in the bios apart from the IDE HDD AUTO DETECTION and the BIOS FEATURES SETUP.

OH dear

---

### Post by TFX360 on 2006-08-23
Let us know what happens! This looks very wierd. Didn't try that with the machine powered on did you?

Kind regards,


TFX

---

### Post by xpod on 2006-08-23
lol.....i might be a bit of a dozy git at times but no i never did that.

if i restart it the normal bios "flach" screen just holds there with each of the ususal steps NOT DETECTED.

THe only thing i got slightly confused about was exactly what way round i had the ide cable ..I.E on the end or on the middle plug?
But since removimg the new hd altogether ive tried it both ways but i just cant adjust no settings in the mentioned bios options.

Ive been in my bios many times before and have never encountered a problem.....ALL i did was plug an hd in,see if it showed up.....Unplugged it all again to tidy it up and when i turned back on nothing was there?

It`s sitting there staring at me smuggly...:rolleyes:

---

### Post by TFX360 on 2006-08-23
Well, the red line on the IDE cable should be pointing TOWARD the white power (connector) thing what ever that is in English. Check that also on the motherboard if you removed them. A thighening push on them can be an help sometimes. Double check allllll you cables. Remove and plug them in all again. Remove the power cord for ten minutes. All that kind of stuff!

Good luck Xpod,


TFX

---

### Post by xpod on 2006-08-23
now when its finished NOT detecting any devices it comes up with this..

searching for boot record from SCSI...not found

Boot failure
reboot and select proper boot device
pressa ny ket when ready

---

### Post by nickpaton on 2006-08-23
Sound's like a hair-pulling-out problem to me; my sympathies.

Can I suggest doing a complete BIOS reset by removing the CMOS battery and moving the CMOS link on your mobo to clear the CMOS settings.

Handle the battery with a cloth like a hankerchief to stop getting finger prints on it.

Put the link back to normal position, and the battery back again.

It also does point to a wire problem.  You must have another PC so as to post stuff etc, so check which way round the IDE leads go - just to make 100% certain in your own mind.

& whilst you are there make 100% certain you have the master / slave links correct.

& temporarily remove the new HDD and get everything working as it was at first.

Check you have the power leads correcty inserted.  I would also say to make sure you have the +5v & +12v present, but you cannot do that without a test meter.  
It's these things which should lead you to the solution.

---

### Post by xpod on 2006-08-23
well...i seem to have made some progress by leaving it off for 5...
now when i boot the flash screen lists the main hd then the slve one with ubunto is next BUT it`s listed as a load of jibberish......loads of mad charcters.
I can boot in to xp ok it seems but ubunto sticks on the "waiting for root file system stage....

"loading essential drivers is ok but thats it..........

---

### Post by TFX360 on 2006-08-23
Can you check the partition table in Gparted?

---

### Post by xpod on 2006-08-23
is it the same principle with the gparted live cd as it is with the gui version on ubunto......
Got back into xp ok but ubunto seems to having issues still...

will go do that now
First thing it say`s is

uncompressing linux...ok,booting the kernal
hdb:INVALID GEOETRY:175.....missed the rest

mow the bbot options has come up on gparted and the text at the bottom says

mount: /dev/hdd is write-protected,mounting read only
hdd:timeout waiting for dma
hdd: drive not ready for command


and it aint doing much more...??????

What could i have done.?????i never touched any of my other hdd`s and only connected another then disconnected it

---

### Post by xpod on 2006-08-23
after trying again to reboot it still does the listing /dev/hda ok but then it lists jibberish for ubunto`s slave hd and asks me to press f1 to continue.....so then grub loads and gives me the numerous ubunto options and the xp one.
so xp`s ok but if i try ubunto it stalls where i mentioned previously for 4 minutes then lists this

ALERT /dev/hdb1 does not exist.Dropping to a shell


Theres quite a bit of other stuff before and after that but none of it is off much sense
/bin/sh:can`t access tty; job control turned off

is the only othere real line of any sense.....sorry i cant be more specific

---

### Post by Stew2 on 2006-08-23
Sorry if I missed something here but is the new hard drive still hooked up or did you take it out again? Also did you set the new drives jumper to slave or leave it as master when you hooked it to the CD-Rom cable? 

Regards,
Stew2

---

### Post by xpod on 2006-08-24
Sorry i never got back to this last night..zzzzzzzzzzzzzzzzzzzzzzzzzzz

I managed to get it back to how it was before....
The hd in question has the jumper instructions on the side and recommended no 
jumpers for using as slave.......
The only free IDE plug i had was on the same one as my dvd-rom which itself is set as the master on that lead.
When i just plugged it in to check it  and rebooted i got a error message on the bios screen about actpi(?) not being compatable.
Which was THEN that i began playing with the leads......I had to unplug them to tidy up the wiring a bit and when i put it back in i must have put the dvd on the middle when it was on the end...OR vice versa?Thats when it started detecting NOTHING(lesson learnt)

I think the differences between the middle and the end ide cable plugs is what got me.....But i still dont understand WHY it went the mad way it did with NOTHING being detected..Surely only that cable`s devices would have not been detected???...

I had it showing up in both xp and ubunto at one point but gparted would`nt allow me to set "disclabels" or something like that..

Just a "short" post to let you know i got it sorted BUT am away to most likely break it all again........love it...:rolleyes: ](*,) :grin: 

SO regardless of wether a hd etc is set to master or slave it also has to be on the correct plug(middle or end) on the cable i gather now.

 Well i`ll give it another go today.......i suppose i could just completely replace the  tiny ubunto slave hd with this bigger one(20g) but i was wanting to just keep my setup as is and mabey just move my /home over to the new one or put home on the little one and move the rest of ubunto to the bigger one

---

### Post by TFX360 on 2006-08-24
Reinstall with /home backuped is the way to go :!

---

### Post by xpod on 2006-08-24
Yeah i was thinking about that........there aint really much in /home im bothered about(i can do it all again) but regardless of backups will i have much trouble with my dualboot if i just replace the hd its on with the bigger one then install on THAT?

I tried just getting the new hd on to the ide cable the dvd-roms on again but no matter how i try it i get a problems which then mess up the rest of my ide settings in the bios...
Ive done this before but not with 3 hds in there.....i hoped i could just plug in and it would work..It did at one point but gparted could`nt set "disclabels" so i got the live cd version(believe that was right idea?)then thats when i started having the trouble with the bios all messing up.

It seems like just getting rid of the little hd ubunto is presently on and just replacing it rather than fiddling with 3 of the things in there is the best bet....As long as it wont be too much hassle with the grub and xp boot.

---

