---
title: "iMac - PowerMac 4.2 - PowerPC G4 (2.1)"
date: 2012-02-24
forum: Apple Hardware Users
---

### Post by danix803 on 2012-02-24
I have an iMac, that has lost it's way. It comes up with the apple and the little circling icon :confused:. 
It won't go any farther. I don't have the original discs. I have d/l'd a few variations, via torrents. I can't even get them to load in VBox.:confused: 
I've got Tiger 10.4 (The DVD & the spanned CD set of 4 - with number 1 cd labeled as bootable). However, they won't boot. I believe that this because the discs need to be in HFS or HFS+ format. This is the part I don't know how to do. 
I have Kubuntu 11.1 with K3B. It gives many wonderful options for putting these iso files on cds and dvds. But, none of them have worked 4 me. 

I will appreciate any constructive help that anyone can offer me on this issue, besides telling me to buy an official OSX cd or dvd. I'm not going to pay twice for the same OS. That's ridiculous. Furthermore, everybody wants an insane amount of money for those cds/dvds. I'm in a tough spot:(. I appreciate your help Ubuntu community:P.

---

### Post by svtguy88 on 2012-02-27
Frankly, I surprised this thread didn't get locked immediately.  The Ubuntu community will NOT help you pirate OS X.  We can help you install Ubuntu and get it working properly on your system.

If your OS X install is still present on the hard drive, it's possible it could be saved with some fdisk magic, but I'm not too familiar with rescuing a broken HFS+ partition.


If you absolutely must have OS X, just go on eBay and buy yourself some 10.4 discs - they've got to be dirt cheap by now.

---

### Post by danix803 on 2012-02-27
> **pkmgarf said:**
> Frankly, I surprised this thread didn't get locked immediately.  The Ubuntu community will NOT help you pirate OS X.  We can help you install Ubuntu and get it working properly on your system.

If your OS X install is still present on the hard drive, it's possible it could be saved with some fdisk magic, but I'm not too familiar with rescuing a broken HFS+ partition.


If you absolutely must have OS X, just go on eBay and buy yourself some 10.4 discs - they've got to be dirt cheap by now.
  
Thanks 4 jumpin' on me so quick... lovely forum U have here... I'm just amazed that U don't have so many users... 

I can tell right away that UR not very legal minded at all. Let me educate U. Pirating is a for stealing. Making a copy of your own os is legal. Using someone else's' copy to restore your system is also legal. I don't have the time or the room to go into how many things that U apparently do not comprehend are actually legal. That would probably require a few books, since UR probably 12. 

It is not very polite to call someone a pirate who is simply doing the best that they can with a incredibly limited resources. I do feel very offended and I definitely, like I'm certain many others have already done, seek genuine assistance elsewhere. Thank U again for your bad manners and insolence. :mad:

First, no one said anything about pirating SW of any kind... The SW is over 10 years old... That would be like trying to pirate Windows 3.1 or DOS 5... I'm certain that UR aware that not all copies of media are faithful (that is, some are not made properly and therefore do not work). Apple simply doesn't make or care about making them anymore. Like I said in my post, people like me who bought and paid for this system and the associate, highly, proprietary sw are pretty toast at this point. Others who have copies of it are selling it, but it is not dirt cheap. For some reason, they want an insane amount of money for the discs.

---

### Post by Double.J on 2012-02-27
Hi Danix803,

As previously stated I can't comment on anything that infringes on Apple's End User License Agreement. (This is part of the ubuntu forums terms of use - it's nothing personal, but these forums are provided directly by ubuntu, which works very hard to put out an open source operating system cost free, so as you can imagine they don't want negative attention brought to them by users helping people circumvent these agreements.)

As for what's happened, and what you can do, the most likely reasons to get stuck at the beach ball of doom in old Macs are changes in the system - kernels, kexts, etc and hard drive issues - these are becoming more and more common as these machines age.

Because of this risk of hard drive failure, I'd say the first thing to do is attempt to get any data off of the hard drive. If you happen to have another mac anf a firewire cable lying around you could start the damaged one in target mode to get access to the hdd, but I suspect that this is a pretty specific situation!

Failing that, you would be able to use an ubuntu Live CD to access the drive, but you'd need a ppc version and you'd have to make sure that you added the hfsutils and hfsplus packages to be able to copy off the drive, so it may all just be easier to remove the hdd and connect it to another computer to attempt data recovery - remember it will have an IDE not SATA connector. (live USB is another route, but the USB 1.1 will make things very slow)

Once you've got your data safe, you can start trying to get the OS working again, of course you will need a disk to do this - how you achieve that will be up to you, just remember that it doesn't have to be tiger - jaguar was also a very good OS and will run well (and is now equally outdated) you are also able to run Leopard on G4's, so if you're buying a disk, I'd say get the best it can run as I also found Iwork 9 ran better on 10.5 than .4

All the best, hope it helps!

---

### Post by svtguy88 on 2012-02-28
> **danix803 said:**
> 
Let me educate U.

I'm not much for Internet wars, but I find it humorous that you are planning to educate someone while referring to them with the wonderful Internet slang "u."

Twelve I am not, and I was just stating that, like it or not, the "old proprietary software" that "no one cares about" is still just that - **proprietary**. 

Let me add that I once went down your path.  I was given an old Apple machine with a flashing Finder icon.  I immediately went to online forums for help burning a disc image of Tiger, Leopard or whatever flavor OS X, and was I was met with equally harsh comments.  The fact is:  it's illegal (not impossible) to download and burn - plain and simple.

That said, if you wish to rescue your system,  a Lubuntu Live CD may be your best bet (if there is indeed an OS X install on the drive still).  I'm not sure if Lubuntu includes the necessary HFS utilities, but it's the distribution that I find to have the best PowerPC support, so you might get lucky and the utilities will be there.

---

### Post by svtguy88 on 2012-02-28
> **danix803 said:**
> lovely forum U have here... I'm just amazed that U don't have so many users... 

 

This happens to be the largest collection of PowerPC Linux users (at least Mac-specific) that I know of.  If you know of a larger community, please share.

---

### Post by MisterGaribaldi on 2012-02-29
Apple may well still have or have the ability to make and ship you discs appropriate for your system.

Failing that, you can still get a copy of Leopard, which supports both PPC and Intel architectures, and from there you should be good to go.

That being said, please be more respectful of those who are trying to help you. Message boards such as UF are populated by people who do, in fact, know what is legal and what isn't, based on copyright law and as applies to proprietary software. Communities such as this one are champions of F/OSS in part precisely because of the legal restrictions traditionally imposed on proprietary software.

Thank you.

---

