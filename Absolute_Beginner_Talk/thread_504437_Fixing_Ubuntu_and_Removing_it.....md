---
title: "Fixing Ubuntu and Removing it...."
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Millha on 2007-07-19
Hello....
I installed Ubuntu for 5-6 days ago and was a happy camper til I f*@ked it up...
I have encountered alot of problems that easy was fixed but I'm stuck now.
I was updating Ubuntu and it frooz, and I restarted and waited it too boot up like normal.
But it didn't :(  It came with a console and there was a file that was defect...

Too the point! I want too know if there is a console command that makes my laptop boot up the CD.
Ubuntu does not boot the CD like it would in XP and I can't start Ubuntu... Plz help... My laptop is useless in this state... 

I doent have a floppy on my laptop, so that aint a option...

Thanks the kind soul that helps me.... [-o<

---

### Post by Spike-X on 2007-07-19
Can't you boot from CD? How did you install Ubuntu from the CD in the first place?

---

### Post by ubuntu.daemon on 2007-07-19
post ur dmesg

---

### Post by Millha on 2007-07-19
Just to clear things.

1. I hade XP when I installed Ubuntu... After installing ubuntu it would not boot up the CD. PS: there is only Ubuntu on the hard drive... I removed XP...

2. I do not know much or lett say anything about linux ... like I said, I have only used it 5-6 days...

INFO: I have Ubuntu feisty or somthing like that... Begins with an "F" at least...
Don't know **** more.... Ohh... I have the newest update and the second one installed but I have removed the newest since that would not start....

Whats a Dmesg? DamegMesseg?

---

### Post by narumi on 2007-07-19
Ubuntu is bootable CD so you should not have any problem to boot it if your computer configured correctly to boot the cd.

dmesg is a one of the linux command. you said that your ubuntu right know only boot into console. you can type  dmesg in that to see the result

---

### Post by Flashgordon20 on 2007-07-19
I'm not sure if this will help your boot to the CD issue, but my Dell has an option where I can choose where to boot from if I hit F12 before the grub screen comes up. I then see a list of boot options. Select your CD/DVD drive and you should be in good shape. Make sure the disc is in before you reboot and do this. This may be an option on all computers but this is my 1st laptop and it happens to be a Dell. I'm very new to Ubuntu and  the forums so sorry if this advice is not relevant to your situation.:)

---

### Post by Millha on 2007-07-19
There was a option at the start of my laptop but they dont work any more after I installed Ubuntu...
There is logo that tells me tatt I can do two things: 1.Choose what to boot 2. settings.... both are useless now after installing Ubuntu....

About that commands: is there no console command that can make it boot the CD just like windows?

PS: ALL booting options that I had where gone after ubuntu was installed....

---

### Post by Millha on 2007-07-19
I tried typing dmesg.... and there came a mess of text.... what part do I need to post...
There is soo much I cant post it all.

---

### Post by Millha on 2007-07-19
I ask again... is there a command too boot the CD?

I cant see any other way to fix this other than fixing the error in Ubuntu and taking the booting from there.... But I doent know how..

In the recovery mode, is there a command to check or fix problems...
Like use the Ubuntu Install CD or somthing.... 
Anything that you can come with, just tell me....

---

### Post by LaRoza on 2007-07-19
0. Turn on computer.
1. Put in Ubuntu CD
2. Turn off computer
3. Turn on computer

What happens?

(To answer your question from before, booting takes place during the BIOS routines, before any OS is loaded.)

---

### Post by ihristov on 2007-07-19
What is the make and model of your laptop?

There isn't a "command" to boot from the CD. There is no such thing. When you power on a computer it is the BIOS that determines how to boot.

Furthermore installing Ubuntu cannot change your computer configuration in such a way that it stops booting from the CD-ROM drive. This is simply impossible. Your problem is either:

a) you cannot boot from the CD-ROM because your BIOS is configured to not attempt to boot from the CD, only from the hard disk

b) your computer hardware has broken. Return it for repair

As mentioned previously by others you have to make your computer boot from the CD. This is done by changing the boot order list in your BIOS or on some laptops you can invoke a menu to make a one-time selection of the boot device. How to invoke this is different for different manufacturers/models. 

On the manufacturer's web site there should be instructions on how to make the computer boot from a CD-ROM. If you can't find them, call their technical support and ask them how to do it.

On my HP system it happens to be the ESC key, however this does not work all the time. I mean that you have to strictly follow the sequence and you have a small window of time in which pressing the hot key would actually bring the boot menu. 

If you have an HP try the following:

1. Turn it on. Open the CD-ROM tray. Insert the Ubuntu CD.
2. Turn it off, making sure it is completely off (hold down the Power key for about 10 seconds and all the lights on the buttons on the laptop will turn off.
3. Now turn it back on and press the ESC key several times. Hopefully you will see a menu with usually 3 options: "boot from hard disk", "boot from CD-ROM", "boot from USB hard disk"

At some point here you should see some text from the BIOS displaying some stuff, sometimes it counts memory, etc. Do you see anything like this?

You might also try to ask a friend which has a little bit more knowledge about computers to help you.
You might also try to contact your local LUG (Linux User Group) for help.

and finally, since your computer is only a week old you can always return it or send it for repair.

---

### Post by regomodo on 2007-07-19
An OS will not damage your BIOS. It is completely seperate.

Either the CD you are using is shagged or you are doing something wrong. Chances of hardware failure (DVD drive) will be slim

---

### Post by Millha on 2007-07-19
When I put a boot CD any CD like Ubuntu it starts grub and then Ubuntu... 
Ubuntu works on starting but stops and starts checking a sector or part of (I think harddrive) /dev/sda1 or somthing.... then it fail too do soo and pops the command line up....

Can I change Grub too boot the CD rom befor Ubuntu?

---

### Post by LaRoza on 2007-07-19
> **Millha said:**
> Can I change Grub too boot the CD rom befor Ubuntu?

No, you can change the bios though, when the computer starts up, there will be a screen (that differs computer to computer) that will have the instructions for entering the setup, most of the time you will have to press esc, delete, or F1, the computer will say. You can manually select the boot device, or change the settings to look for a cd first.

---

### Post by Millha on 2007-07-19
I dont get this.... I have no way of starting Bios setup , and the boot menu I got befor when using windows does not come up....

---

### Post by VoiceOvGod on 2007-07-19
GRUB loads up after the BIOS.

What kind of computer do you have?

You will want to adjust your boot priority to boot in the following order:

1. BIOS
2. CD/DVD-Rom
3. Hard Driave

---

### Post by Millha on 2007-07-19
Grub..... anything I can do inn it too boot CD befor Ubuntu?

---

### Post by fastpakr on 2007-07-19
Editing GRUB is not the solution to your problem.

What you need to do is edit the BIOS config.  Post the type of laptop and somebody can look up the instructions for you.  Again, the problem here is simply what is configured in BIOS as the boot order.  Before GRUB starts, BIOS runs its POST sequence and then goes into the boot order.  You just need to get in and change the order.

How did you install Ubuntu in the first place?

---

### Post by LaRoza on 2007-07-19
> **Millha said:**
> I dont get this.... I have no way of starting Bios setup , and the boot menu I got befor when using windows does not come up....

Ok, I'll clarify. (I know it can be confusing)

When you first turn on the computer, a screen with the company logo will probably come up (probably, sometimes it is just the POST screen), then the boot loader comes up, in this case, grub, then the OS loads. The first screen, with the company logo will have, at the bottom of the screen, a message telling you which key to press to enter the CMOS. Press that key. A new screen will come that severely lacks visually appeal. Now here is were I can not be explicit. The setup utility will allow you to change the boot order or select the boot device, exactly how I cannot say, all the BIOS manufactorers are different.

---

### Post by Millha on 2007-07-19
I know every thing about the bios and booting order but I cant get inn too bios becouse after Ubuntu the only thing I can get inn to is grub and the ubuntu command line.... Why would Ubuntu change my BOOT order!?

Sooo... cut the noob stuff and get me som real stuff I can try....

---

### Post by Tomosaur on 2007-07-19
When you FIRST turn your machine on, you should see a line of text somewhere where it says 'hit <F2> to run Setup' or something of that nature. The button may be different. If you can see the grub menu (where it asks which Ubuntu you want to load), then you've missed it, and you need to restart your machine. You have to be fairly quick. If you can't see any line of text such as this, then restart your machine, and keep hitting any of the following (not all together, just try one)

F2
Del
Esc

The key you need to press is usually one of those. If none of those works (you should try each one, just keep hitting it as your machine boots. If it fails, reboot and try a different key), then you'll need to find the documentation which came with your laptop. If successful, you will be taken to your BIOS setup screen. From there you should be able to change the boot order of your hardware. Set it so that the CD drive is the first piece of hardware to boot, stick the Ubuntu CD in the drive, then save your settings and exit.

You shouldn't be having this problem though - you will have needed to boot from the CD to install Ubuntu in the first place. Are you sure you have the right CD in the drive?

And quit with telling us about Ubuntu changing your boot order. It didn't, it can't, and it wouldn't. There is nothing about Ubuntu which could make it do what you're saying it does. The problem is either with your CD, the CD drive, or your BIOS, and is completely unrelated to you having installed Ubuntu.

---

### Post by Millha on 2007-07-19
Sorry for that... I'm just getting irretated... stuped laptop....
The laptop is no brand, it's a shell with custom parts... But things like bios and booting and so on work befor but dissaperd? How come... 
Be passiant with me :P

---

### Post by LaRoza on 2007-07-19
> **Millha said:**
> Sorry for that... I'm just getting irretated... stuped laptop....
The laptop is no brand, it's a shell with custom parts... But things like bios and booting and so on work befor but dissaperd? How come... 
Be passiant with me :P

How did you install Ubuntu before?

---

### Post by fastpakr on 2007-07-19
> **Millha said:**
> I know every thing about the bios and booting order but I cant get inn too bios becouse after Ubuntu the only thing I can get inn to is grub and the ubuntu command line.... Why would Ubuntu change my BOOT order!?

Sooo... cut the noob stuff and get me som real stuff I can try....

You can develop an attitude and assume you know what's going on, or you can listen to people who understand what they're talking about and providing the information you need to help.  BIOS comes BEFORE Ubuntu - you can get into it and configure it regardless of what OS is on the machine or what GRUB does.  Ubuntu does NOT change your boot order.

Post the model of laptop and somebody can help you out.

---

### Post by VoiceOvGod on 2007-07-19
In order for us to be able to help you, we need you to provide us some answers.

Have you tried pressing the Escape key right as you turn on the computer?

What kind of computer do you have?

---

### Post by Tomosaur on 2007-07-19
> **Millha said:**
> Sorry for that... I'm just getting irretated... stuped laptop....
The laptop is no brand, it's a shell with custom parts... But things like bios and booting and so on work befor but dissaperd? How come... 
Be passiant with me :P

We've told you what to do. There is no possible way your machine would even get to the grub screen if the BIOS didn't load first. You need to restart and look very closely. Have you tried reading the documentation for your motherboard? That will probably tell you which key to press.

---

### Post by LaRoza on 2007-07-19
> **Millha said:**
> Sorry for that... I'm just getting irretated... stuped lapto shell with custom parts... But things like bios and booting and so on work befor but dissaperd? How come... 
Be passiant with me :P

What brand is the bios? (All of this is actually dependant on BIOS, not the computer brand.) If Bios was broken, the computer wouldn't boot anything, so it must work. 

Did you change any settings? Did you flash the bios recently or at all? 

You can reset the CMOS settings, exactly how it depended on the motherboard.

---

### Post by Millha on 2007-07-19
I'm not saying that this is becouse Ubuntu, but I'm saying that this is as it is after I installed Ubuntu....
The CD is 100% correct.... used it too install... And the keys too start bios and soo on does not work... why? I dont know and I dont care... I have not changed these settings my self... then why would they be wrong? I was rigth when I installed, soo the thing I have too work with are getting kinda thin don't you think....

But YAY for Ubuntu.... Very nice OS.... I will installet after fixing this and learn more... But before that I have too get some one that know of anything smart too help.... 

but thank for the effort... but no more bios talk, just if it's nessasery...

(sorry for my bad english):)

---

### Post by Millha on 2007-07-19
Like pulling out the Bios battery!?

---

### Post by tgm4883 on 2007-07-19
> **LaRoza said:**
> What brand is the bios? (All of this is actually dependant on BIOS, not the computer brand.) If Bios was broken, the computer wouldn't boot anything, so it must work. 

Did you change any settings? Did you flash the bios recently or at all? 

You can reset the CMOS settings, exactly how it depended on the motherboard.

While this is true, since it is a laptop it should have the same bios for all models of this brand.  Since the OP doesn't seem to think the BIOS exists anymore (and thinks he knows more than everyone trying to help him), I seriously doubt he is going know which BIOS it is.  I see us getting the type of laptop it is much easier than the BIOS

---

### Post by fastpakr on 2007-07-19
BIOS talk is EXACTLY what you need.  That's where you need to go to fix this.  What type of motherboard is it?

---

### Post by tgm4883 on 2007-07-19
> **Millha said:**
> I'm not saying that this is becouse Ubuntu, but I'm saying that this is as it is after I installed Ubuntu....
The CD is 100% correct.... used it too install... And the keys too start bios and soo on does not work... why? I dont know and I dont care... I have not changed these settings my self... then why would they be wrong? I was rigth when I installed, soo the thing I have too work with are getting kinda thin don't you think....

But YAY for Ubuntu.... Very nice OS.... I will installet after fixing this and learn more... But before that I have too get some one that know of anything smart too help.... 

but thank for the effort... but no more bios talk, just if it's nessasery...

(sorry for my bad english):)

Fine, no more BIOS talk.  You have 1 of 2 problems (maybe both).  
1.  Your CD drive is trashed
2.  Your CD is trashed.

Options to repair. 
1.  Buy a new CD drive
2.  Get a new CD

---

### Post by LaRoza on 2007-07-19
> **Millha said:**
> 

but thank for the effort... but no more bios talk, just if it's nessasery...

(sorry for my bad english):)

Since I am not there, I can't really say more. 

Here is one last solution (sort of):

Try removing the hardrive and then boot, it should find the cd then. You will not be able to install it, however, because the harddrive is out of the computer, but it will give you a clue as to what is wrong. If it doesn't boot the cd, it may be the cd player.

---

### Post by tgm4883 on 2007-07-19
> **fastpakr said:**
> BIOS talk is EXACTLY what you need.  That's where you need to go to fix this.  What type of motherboard is it?

Actually im doubting the problem is in the BIOS

---

### Post by tgm4883 on 2007-07-19
> **LaRoza said:**
> Since I am not there, I can't really say more. 

Here is one last solution (sort of):

Try removing the hardrive and then boot, it should find the cd then. You will not be able to install it, however, because the harddrive is out of the computer, but it will give you a clue as to what is wrong. If it doesn't boot the cd, it may be the cd player.

What he means to say is, power down the computer, unplug it, take the batter out, then remove the hard drive

---

### Post by fastpakr on 2007-07-19
> **tgm4883 said:**
> Actually im doubting the problem is in the BIOS

Could very well be the disc/drive, but we should be able to talk him into checking the boot order regardless, don't you think?

---

### Post by LaRoza on 2007-07-19
> **Millha said:**
> Like pulling out the Bios battery!?

CMOS battery, yes. Be careful, notebooks are sensitive to ESD, if you break something I doubt it will be under warrenty.

I suspect the cd or cd drive. (I also doubt that BIOS is inaccessable, just the ability to access it)

---

### Post by LaRoza on 2007-07-19
> **fastpakr said:**
> Could very well be the disc/drive, but we should be able to talk him into checking the boot order regardless, don't you think?

We tried...

---

### Post by VoiceOvGod on 2007-07-19
What I did when I didn't see the "Press Fx to enter BIOS" was try each key.

Usually its F2, or F8, or F12.

You may have to actually try them all until you get it.

Yes, that will likely result in your needing to restart several times.

---

### Post by tgm4883 on 2007-07-19
> **fastpakr said:**
> Could very well be the disc/drive, but we should be able to talk him into checking the boot order regardless, don't you think?

Not if it's this much work.  Lets look at the situation.  He had windows, popped in a CD of Ubuntu and installed Ubuntu.  That requires that the CD be booted first (although the HD test will verify this).  Since he didn't change any BIOS settings since, it must be concluded that the BIOS is not at fault.  Also, since it seems that he has built this computer from bare bones, it would seem he knows at least a little about computer.  And last, since the computer was a bare bones computer and had windows on it, I must assume that it is an older computer.  Combining this info with the above info I conclude that the problem is either in the CD or the CD drive.

---

### Post by LaRoza on 2007-07-19
> **VoiceOvGod said:**
> What I did when I didn't see the "Press Fx to enter BIOS" was try each key.

Usually its F2, or F8, or F12.

You may have to actually try them all until you get it.

Yes, that will likely result in your needing to restart several times.

Also F1 and F10.

---

### Post by tgm4883 on 2007-07-19
> **LaRoza said:**
> Also F1 and F10.

Dont forget delete

---

### Post by VoiceOvGod on 2007-07-19
Is the CD drive even being acknowledged?

Try this:

```

cd /media/


```

Then, list the drives showing by doing this:

```


ls -l


```

Let us know what you see.

---

### Post by Millha on 2007-07-19
Are you here too help or not...
I lay it down as best I can....
My computer is and SL-DL75
The main bord is (or at least the pic inn the start says) INSYDE and the pc all INTEL comps....

I try everything that is told... but I can't change that it is as it is!!!
Just give me options and I will try it...

---

### Post by tgm4883 on 2007-07-19
> **Millha said:**
> Are you here too help or not...
I lay it down as best I can....
My computer is and SL-DL75
The main bord is (or at least the pic inn the start says) INSYDE and the pc all INTEL comps....

I try everything that is told... but I can't change that it is as it is!!!
Just give me options and I will try it...

Remove the hard drive then try booting the cd, tell us what happens.

---

### Post by Millha on 2007-07-19
I'll try it all... but I need some time.... I'll be back later.....

---

### Post by LaRoza on 2007-07-19
> **Millha said:**
> Are you here too help or not...

I try everything that is told... but I can't change that it is as it is!!!
Just give me options and I will try it...

Yes, but we can only do so much.

What happend when the hard drive was removed? Did you get a message from BIOS saying it couldn't find a boot device? (That would point to the cd drive as being the culprit)

---

### Post by Millha on 2007-07-19
Removed the HD....

Boot order is...
1. CD
2. HD
3. Ethernet (LAN)

Still could not get into Bios but the CD booted up, and worked fine....
But why not when the HD is in? 

I found the 100% bios name Insyde MobilPRO 4.20.10
Getting anything out of this?

---

### Post by tgm4883 on 2007-07-19
> **Millha said:**
> Removed the HD....

Boot order is...
1. CD
2. HD
3. Ethernet (LAN)

Still could not get into Bios but the CD booted up, and worked fine....
But why not when the HD is in? 

I found the 100% bios name Insyde MobilPRO 4.20.10
Getting anything out of this?

How did you find that boot order?  If the CD booted up, then that isn't your BIOS boot order.

---

### Post by LaRoza on 2007-07-19
Am I correct in typing that the cd worked when the harddrive was removed, but doesn't boot when the harddrive is present?

If so, it is BIOS. Are you sure about the boot order?

---

### Post by VoiceOvGod on 2007-07-19
Hrm, may need to flash the BIOS then....

But at least we confirmed that it is NOT the CD drive.

---

### Post by Millha on 2007-07-19
Mr.TGM
I removed my harddrive...
When doing this there comes a check list of what my laptop tries too boot up... 

Like I said.... 
1.CD-ROM
2.HD
3.ETHERNET

But putting you aside and asking could my RAM have anything with it too do?
I checked the RAM with the memtest that is in grub, and there where a bad sector.....
Hade bad RAM once before and simular tings happend....

---

### Post by LaRoza on 2007-07-19
I don't know about the RAM, but swapping it with known good RAM wouldn't hurt.

If something happened like this before, why didn't you tell us?

---

### Post by Millha on 2007-07-19
I'm have been on this all day... I'll check the forum tomorrow... tnx everyone...

And good luck with your PMS tgm4883 :P

---

### Post by tgm4883 on 2007-07-19
> **Millha said:**
> I'm have been on this all day... I'll check the forum tomorrow... tnx everyone...

And good luck with your PMS tgm4883 :P

WTF?

---

### Post by LaRoza on 2007-07-19
> **Millha said:**
> I'm have been on this all day... I'll check the forum tomorrow... tnx everyone...

And good luck with your PMS tgm4883 :P

????

We must be too nice...

---

### Post by tgm4883 on 2007-07-19
> **LaRoza said:**
> ????

We must be too nice...

This may be the last time I waste my time on people like this.  Next time we are trying to help someone and they think they know it all, better watch out.

---

### Post by VoiceOvGod on 2007-07-19
Meh.

It's a turn-the-cheek thing.

I'm just in it to contribute to the community.

---

### Post by LaRoza on 2007-07-19
> **tgm4883 said:**
> This may be the last time I waste my time on people like this.  Next time we are trying to help someone and they think they know it all, better watch out.

I wonder why you were targeted?

Maybe you could PM and find out.

---

### Post by fastpakr on 2007-07-19
> **Millha said:**
> Mr.TGM
I removed my harddrive...
When doing this there comes a check list of what my laptop tries too boot up... 

Like I said.... 
1.CD-ROM
2.HD
3.ETHERNET

But putting you aside and asking could my RAM have anything with it too do?
I checked the RAM with the memtest that is in grub, and there where a bad sector.....
Hade bad RAM once before and simular tings happend....

This sounds like a menu of what you can choose from to TRY to boot, not the order it uses in BIOS. Your problem is STILL in the BIOS config.

---

### Post by tgm4883 on 2007-07-19
> **LaRoza said:**
> I wonder why you were targeted?

Maybe you could PM and find out.

I dont care about it that much.  Sometimes though I get my fill.  Just tires me out dealing with some of these people all the time, the ones that know it all or have 20 years of Windows experience and think that matters somehow.  Whats funny is that I think I found his laptop on the internet and I think I have a solution to his problem, but do I really feel like helping him anymore?

And to answer a future question, yes, I can be petty like that.

---

### Post by LaRoza on 2007-07-19
> **tgm4883 said:**
> I dont care about it that much.  Sometimes though I get my fill.  Just tires me out dealing with some of these people all the time, the ones that know it all or have 20 years of Windows experience and think that matters somehow.  Whats funny is that I think I found his laptop on the internet and I think I have a solution to his problem, but do I really feel like helping him anymore?

And to answer a future question, yes, I can be petty like that.

It is not petty, you are not obligated to do anything. In fact, it is amazing that you tried. 

(20 years of Windows? I feel sorry for them.)

---

### Post by twiceasworn on 2007-07-19
Sigh, for all the amazing people in this community, it angers me when people try to help and get completely **** on.

The whole time I was reading this thread I kept wondering why this guy didn't even attempt to figure the issue out on his own.  Then I realized he is like a lot of the people that come here for help and has absolutely no interest in helping himself.

Sad.

tgm4883:  You were nothing but a nice to the guy, I say let him sit there with a jacked up laptop.

---

### Post by VoiceOvGod on 2007-07-19
20 years of Windows experience....

*THAT* is why I see a therapist.... 

that, and because of the Safety Dance...

But anyway, I'm thinking the BIOS is just hiding.

---

### Post by LaRoza on 2007-07-19
> **VoiceOvGod said:**
> 20 years of Windows experience....

*THAT* is why I see a therapist.... 

that, and because of the Safety Dance...

But anyway, I'm thinking the BIOS is just hiding.

I feel bad for the therapist...

I think the OP is not reading the BIOS correctly.(the device order is not always  the same as the boot order)

---

### Post by VoiceOvGod on 2007-07-19
We've made leaps and bounds dealing with the Safety Dance... Not so much with the Windows thing.

I was experiencing a similar problem with my laptop, however, in my case, the OS boots up into KDE no problem, but it will not acknowledge the DVD-rom drive. 

It's a Sony VAIO....

---

### Post by VoiceOvGod on 2007-07-20
Did this problem ever get resolved?

---

