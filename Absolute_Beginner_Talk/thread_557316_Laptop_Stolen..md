---
title: "Laptop Stolen."
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Judgegeo on 2007-09-22
So, i woke up this morning to find my windows laptop was stolen. Sure it had a password on my account but that was it.

When/if insurance pays out I will be becoming purely linux. But, if my laptop got stolen again what kind of protection could i use that would drive the person insane and stop them from selling it on?

Also, can someone reccomend a good make of external HDD's?

Thanks.

---

### Post by CaptainInsaneO on 2007-09-22
That's terrible to hear, so sorry for your loss. :( I think if I actually HAD a laptop and it got stolen I'd be ready to kill.

I'm not really sure what you mean by "protection to drive a person crazy". But I can say two things: 1) Ubuntu requires a password for login and 2) you can look into [LoJack for Laptops]("http://www.lojackforlaptops.com/"). It probably won't work in Ubuntu, so you could maybe keep a small windows partition for it. This could also work as a honeypot because most people (especially stupid-*** crooks) will see Ubuntu and not be able to crack the password and switch to (what they know) Windows. If they surf the internet and you've reported your laptop stolen, LoJack will report back to the master server and say "I'm here!" and you can tell that thief to have a fun go at prison. :guitar:

As for external hdd's, I don't really know because I build mine, but I've heard a lot of BAD things about Maxtor externals.

---

### Post by 22bsti on 2007-09-22
If im not mistaken there is companies that provide insurance on laptops and such, but im not so knowledgable about such things, however as for the external harddrive question that depends, are you looking for cheap, fast or something in between.  Personally i usually buy the enclosure and hd seperately this way i can get a quiet drive.  I personally have had good luck with samsung drives.  I have built about 40 computers and have only had one hd failure and that was when a cheapo psu died and killed the mobo and hd and cd rom.  As for the enclosure i have had good luck with AMS venus enclosures i have used 4 of them so far no failures (they have been used for about 2 years for incremental backup every saturday so they have been well used), and they provide good ventilation and are still quiet.  Are you planning on connecting using usb, firewire, esata? and are you planning on using an ide hd or sata one?

if you'd prefer a prebuilt one, a few of my friends swear by western digital hd enclosures.

---

### Post by Pumalite on 2007-09-22
I've had 2 Maxtor externals for 5 years, but I prefer Wester Digital.

---

### Post by JNowka on 2007-09-22
When it comes to external HDD's I recently bought a Western Digital 120GB Passport.  It weighs about the same as my mouse, and works off the power provided by the usb plug in.  I have not had any problems with it personally.  No messy electrical cords.

---

### Post by JNowka on 2007-09-22
[quote=CaptainInsaneO]2) you can look into [LoJack for Laptops]("http://www.lojackforlaptops.com/"). It probably won't work in Ubuntu, so you could maybe keep a small windows partition for it.[/quote]

What every you do, do not install LoJack for Laptops when you have a Linux Partition.  Everytime you boot up into windows, the MBR is written to preventing you from booting into anything the next time.

---

### Post by kevinatkins on 2007-09-22
I'd suggest the following -

1) Alter boot order so that CD is disabled as first boot device;
2) Password-protect the BIOS so that the thief cannot reset, nor do anything else;
3) Pick a strong password for your Ubuntu account;
4) Remove 'recovery mode' from the Grub boot menu.

Hopefully this should be enough to deter the average crook - they basically won't be able to do anything with the machine at all.... hopefully ....

---

### Post by CaptainInsaneO on 2007-09-22
Ooooh didn't know that. Thanks for correcting me. :)

---

### Post by JNowka on 2007-09-22
I have first hand experience with LoJack.  It sucked.  Putting in the cd and reinstalling grub to the MBR was just to much.  BTW I no longer have a Windows Partition.  ;)

---

### Post by thesunscreen on 2007-09-23
The problem with that is it wouldn't deter a theif. The thief has your laptop, but I would agree with the post about the bios password. Granted you can still change the bios chip and reinstall the OS but it would piss them off. There are devices to reflash the bios without the system being on, but they are specific to the laptop. Also there are other lojak type programs and I'm unsure but I think they all write to the MBR. There is always the long shot of registering your serial number on sites that hardly anyone checks.

---

### Post by Judgegeo on 2007-09-24
Well, the house insurance coveres it. So if all goes well i'll be looking at £549 to buy a new laptop. 

They probably took it apart and sold as parts. But thats just my opinion.

---

### Post by wieman01 on 2007-09-24
Truecrypt for personal data. Or encrypt your entire harddisk using LUKS. Encryption is the best protection for your personal data.

---

### Post by hyper_ch on 2007-09-24
I'd encrypt the drive and also make backups at a regular interval externally.

Have a read here:

[http://www.c3l.de/linux/howto-completly-encrypted-harddisk-including-suspend-to-encrypted-disk-with-ubuntu-6.10-edgy-eft.html](http://www.c3l.de/linux/howto-completly-encrypted-harddisk-including-suspend-to-encrypted-disk-with-ubuntu-6.10-edgy-eft.html)

That will encrypt the whole drive... so even if your notebook gets stolen it can be used (by reinstalling a new OS but the data you have on it cannot be retrieved (except you use a weak password).

Preventing the the notebook to be used is not possible. Even if you set as bios password that normally can be resetted by removing the battery from it...

---

### Post by lebabyg on 2007-09-24
> **wieman01 said:**
> Truecrypt for personal data. Or encrypt your entire harddisk using LUKS. Encryption is the best protection for your personal data.

I agree with Wieman.  A bios password does nothing.  All a smart thief needs to do is remove the lithium cell that powers the bios and it will reset the password.  My work laptop used to have something called Safeboot, but it was on Windows [http://www.safeboot.com/](http://www.safeboot.com/).  Basically without entering the Safeboot password nobody could access that data on the drive.  Don't know if LUKS does something similar but i was assured by one of the ethical hacking guys at work that you'd have a hard time accessing the data with Safeboot....

---

### Post by hyper_ch on 2007-09-24
that link above will encrypt everything on your system except for the /boot partition... that one cannot be encrypted... but root, home, swap, etc. will all be encrypted. Without password upon booting the data can't be accessed at all.

---

### Post by High Roller on 2007-09-26
I've been told that the new alternative install CD for Gutsy will have the option to encrypt your entire drive.  Everything but /boot.

There's a large group of Ubuntu/laptop users that have been begging for this to be implemented in an easier fashion since Debian was capable of such a task at install time.  Now it looks like we have it!

I'm proud to be a Ubuntu user.  Go Gutsy!  :)

---

### Post by Supergoo on 2007-09-26
Wow that just blows, I am sorry to hear about your laptop being taken ! But when you get another one do a few things, make sure all the parts work with Linux and get a Chain to protect it j/k :)    I hope it works out for you !

---

### Post by wieman01 on 2007-09-26
Can anybody else confirm that Gutsy will have an option for hard disk encryption?

---

### Post by yuku-aki on 2007-09-26
I once received a pc from a mortgage company, and I wrote over it with Mandrake Linux, a bit before the '05 version came out.  Hopefully you have the serial #; at least then they can't sell it to a pawn shop or something.

---

### Post by justleen on 2007-09-26
Good to hear your getting your insurance money!


And thnx for the thread! I installed linux on my work laptop, but im required to protect it with safeguard (thats for windows only, so i need an alter.) and wasnt able to find any thing.. this thread turns out to be the gold nugget i needed!

LUKS and Truecrypt! Cheers Wieman!

---

### Post by MenZa on 2007-09-26
I'm sorry to hear about your loss---if I lost this laptop, I'd be in trouble.

When it comes to the make of external harddrives, I've---like CaptainInsaneO---always built mine myself.

However, I know that Seagate disks are generally a great purchase, and I've also been told that WD MyBooks and LaCie disks are good disks. (And LaCie will give you up to 2TB storage...)

---

### Post by High Roller on 2007-09-26
> **wieman01 said:**
> Can anybody else confirm that Gutsy will have an option for hard disk encryption?

It's still in testing apparently.  I'm downloading the alternative installer right now from : [https://iso.qa.stgraber.org/](https://iso.qa.stgraber.org/)

Just make sure you use the alternative installer.  Report bugs and help make it happen!  :)

---

### Post by Paulmd on 2007-09-26
> **lebabyg said:**
> I agree with Wieman.  A bios password does nothing.  All a smart thief needs to do is remove the lithium cell that powers the bios and it will reset the password.  My work laptop used to have something called Safeboot, but it was on Windows [http://www.safeboot.com/](http://www.safeboot.com/).  Basically without entering the Safeboot password nobody could access that data on the drive.  Don't know if LUKS does something similar but i was assured by one of the ethical hacking guys at work that you'd have a hard time accessing the data with Safeboot....


Yes and No. With virtually all desktops, bypassing the bios password is easy.(pull battery, wait a few minutes) With many models of laptop, the bios password simply cannot be cleared unless you know it.  (there's a couple dozen different hacks for various... mostly very old... laptops, and some of them require special skills and/or equipment).

I won't be discussing exactly how. :)

---

### Post by weedeatr on 2007-09-26
> **kevinatkins said:**
> I'd suggest the following -

1) Alter boot order so that CD is disabled as first boot device;
2) Password-protect the BIOS so that the thief cannot reset, nor do anything else;
3) Pick a strong password for your Ubuntu account;
4) Remove 'recovery mode' from the Grub boot menu.

Hopefully this should be enough to deter the average crook - they basically won't be able to do anything with the machine at all.... hopefully ....

my dad did that to me in exams :( lol
i think that wil hold him out...

---

### Post by weedeatr on 2007-09-26
> **High Roller said:**
> It's still in testing apparently.  I'm downloading the alternative installer right now from : [https://iso.qa.stgraber.org/](https://iso.qa.stgraber.org/)

Just make sure you use the alternative installer.  Report bugs and help make it happen!  :)
is there a mini.iso file for gutsy gibbon??

---

### Post by High Roller on 2007-09-26
> **weedeatr said:**
> is there a mini.iso file for gutsy gibbon??

I'm not sure.  But please keep in mind that this is all still Alpha/testing only.  Don't use it for a production environment.

But testing on that spare computer never hurt anyone!  :)

---

### Post by weedeatr on 2007-09-26
ok thanks i will see if i get one and let u know...:)

---

### Post by DapperMe17 on 2007-09-26
Adding to the great post above...

When you're in the BIOS, laptops usually have a "drivelock" setting that you can password protect....this way your covered by a password from wherever you boot from, so that you shouldn't have to update your boot order.

---

### Post by weedeatr on 2007-09-26
is this only in windows or in ubuntu??

---

### Post by wieman01 on 2007-09-26
> **weedeatr said:**
> is this only in windows or in ubuntu??
If you are referring to the BIOS thing, that's nothing to do with the OS. It is possible on any platform.

---

### Post by Desiree on 2008-01-23
My laptop was also recently stolen, from my hotel room.  From reading the posts, there is a lot of talk about the BIOS password.  Does this mean that the standard Ubuntu login screen is able to be passed without the person knowing the password, if they had the right knowledge?  And how likely is it that someone can find out how to do this, if applicable?  Just wondering if I can expect the person may have access to my files, even though there is not much that I think would be any use to someone else.

I do not have a Windows partion.

Any suggestions on things I should do after having a laptop stolen, other than buying a new one?  I'm hoping the house insurance will cover the replacement, but I'm really pissed off at the Hilton for the cleaning folks leaving my door unsecured on two occasions (As confirmed by security the first time when our room was raided, the second by me knowing when the lady left and no one else going in in those few minutes).

Thanks for any advice.

---

### Post by wieman01 on 2008-01-23
> **Desiree said:**
> My laptop was also recently stolen, from my hotel room.  From reading the posts, there is a lot of talk about the BIOS password.  Does this mean that the standard Ubuntu login screen is able to be passed without the person knowing the password, if they had the right knowledge?  And how likely is it that someone can find out how to do this, if applicable?  Just wondering if I can expect the person may have access to my files, even though there is not much that I think would be any use to someone else.
A BIOS password offers no protection at all. All one has to do is remove the hard disk and connect it to another PC. There you go.

The Ubuntu login password is no protection either. Again you can connect the HD to another device and mount it from there, then make a copy of all your precious data. It's as simple as that.

I wouldn't even have to think about it twice if I was a thief. So unfortunately your data are totally unprotected, only HD enryption could have saved you and your data.

I generally recommend **Truecrypt **for encryption of personal/sensitive data.

---

### Post by Joeb454 on 2008-01-23
Not every thief would be clever enough to think of that though, plus I think most of them wouldn't have a clue how to use Linux as well, which helps a little

---

### Post by hyper_ch on 2008-01-23
Don't underestimate thieves...

Truecrypt is nice but it has its drawbacks... to be sure I'd use total harddisk encryption... the only unencrypted part would be a /boot partition.

---

### Post by wieman01 on 2008-01-23
> **Joeb454 said:**
> Not every thief would be clever enough to think of that though, plus I think most of them wouldn't have a clue how to use Linux as well, which helps a little
Yes, something you can hope for, but there is no guarantee at all. If that intruder is really interested in your data, then she/he will find a way of retrieving it with little effort. Let's hope for the best then.

---

### Post by wieman01 on 2008-01-23
> **hyper_ch said:**
> Don't underestimate thieves...

Truecrypt is nice but it has its drawbacks... to be sure I'd use total harddisk encryption... the only unencrypted part would be a /boot partition.
'Total hardware' encryption is too much for beginners though, it's for advanced users. That's why I would rather not recommend it. Encryption of personal file should normally do. But you never know, so I understand where you are coming from.

---

### Post by hyper_ch on 2008-01-23
> **wieman01 said:**
> 'Total hardware' encryption is too much for beginners though, it's for advanced users. That's why I would rather not recommend it. Encryption of personal file should normally do. But you never know, so I understand where you are coming from.

Why is it for advanced users?

Upon installation with the alternate CD you can directly chose to encrypt it all ;)

The problem is, there are parts where also personal files are stored that you wouldn't suspect... e.g. your swap, temp folder, ... so either find you konw where it all is or you just fully encrypt your system.

---

### Post by wieman01 on 2008-01-23
> **hyper_ch said:**
> Why is it for advanced users?

Upon installation with the alternate CD you can directly chose to encrypt it all ;)

The problem is, there are parts where also personal files are stored that you wouldn't suspect... e.g. your swap, temp folder, ... so either find you konw where it all is or you just fully encrypt your system.
That is all true, but did the advent of Gutsy really make it as simple as you describe it? I am asking because I know little about it, but before Gutsy the only option was LUKE which is.. cumbersome to say the least.

Is the installation process through Alternative CD simple enough even for beginners? How much manual tweeking is involved if you go for full HD encryption?

if you convince me, I'll go for it right away, no doubt. :-)

---

### Post by hyper_ch on 2008-01-23
Installation through alternate cd is not more difficult than through the Desktop one...

You can either choose to fully encrypt your system, to fully encrypt lvm or to manual partitioning (and encrypting)... it's not difficult actually.

---

### Post by wieman01 on 2008-01-23
> **hyper_ch said:**
> Installation through alternate cd is not more difficult than through the Desktop one...

You can either choose to fully encrypt your system, to fully encrypt lvm or to manual partitioning (and encrypting)... it's not difficult actually.
Alright then. It is as simple if you decide to use up to 5 different partitions (e.g. root, home, swap, data, etc.)? And when are you asked to enter the password?

Thanks for sharing your thoughts with us. This sounds great despite the sad topic of this thread.

---

### Post by hyper_ch on 2008-01-23
swap is the only thing that's more difficult form manual partitioning to set it up encrypted... the rest is simple... however for every encrypted partition you need also to enter the password

---

### Post by wieman01 on 2008-01-23
> **hyper_ch said:**
> swap is the only thing that's more difficult form manual partitioning to set it up encrypted... the rest is simple... however for every encrypted partition you need also to enter the password
Ah, OK, I was afraid so. So the installation is not the issue, but the actual handling in that particular case. So I'll stick to what I have right now... an encrypted data partitions. Thanks anyway, this was very helpful.

---

### Post by Desiree on 2008-01-23
Thanks.  I guess all they would have to do is read this thread!
Okie dokie, perhaps they will enjoy my random music... Out of spite, I hope they don't have the same music taste as me!

There should be someway that the owner of a computer can "communicate" with their own laptop and tell it to self distruct.  That would be comforting, assuming only the owner could initiate it and not cause any harm other than to the computer! 

:icon_frown:

---

### Post by wieman01 on 2008-01-24
> **Desiree said:**
> Thanks.  I guess all they would have to do is read this thread!
Okie dokie, perhaps they will enjoy my random music... Out of spite, I hope they don't have the same music taste as me!

There should be someway that the owner of a computer can "communicate" with their own laptop and tell it to self distruct.  That would be comforting, assuming only the owner could initiate it and not cause any harm other than to the computer! 

:icon_frown:
Like we have discussed, encryption is the only effective safeguard against further damages. So following that recommendation will give you some comfort in future, however, replacing your laptop will still be necessary I guess. :-)

If you need further help or advice, let us know.

---

### Post by hyper_ch on 2008-01-24
> **wieman01 said:**
> Ah, OK, I was afraid so. So the installation is not the issue, but the actual handling in that particular case. So I'll stick to what I have right now... an encrypted data partitions. Thanks anyway, this was very helpful.

The handling is not difficult.. during the boot process you will be asked to enter each encrypted partition's password... after that you can use it like you normally do...

---

### Post by wieman01 on 2008-01-24
> **hyper_ch said:**
> The handling is not difficult.. during the boot process you will be asked to enter each encrypted partition's password... after that you can use it like you normally do...
That's what I am referring to. I want to enter the password once, not four times. But I'll think about it, perhaps merging /root & /home will make sense. Thanks for that piece of advice, it did help a lot.

---

### Post by Oppewall on 2008-01-30
> **wieman01 said:**
> That's what I am referring to. I want to enter the password once, not four times. But I'll think about it, perhaps merging /root & /home will make sense. Thanks for that piece of advice, it did help a lot.

It is not true that you need to enter the password for every partition. I made the full disk encryption and when i boot i need to enter a password for accessing the logical partition (where swap and /root is placed). When that is done you will be asked for no more password and the system is completely transparent.

I have not tried it myself, but I think it would be possible to make more partitions inside the logical area, such as /home and still access them all with a single password at boot.

---

### Post by wieman01 on 2008-01-30
> **Oppewall said:**
> It is not true that you need to enter the password for every partition. I made the full disk encryption and when i boot i need to enter a password for accessing the logical partition (where swap and /root is placed). When that is done you will be asked for no more password and the system is completely transparent.

I have not tried it myself, but I think it would be possible to make more partitions inside the logical area, such as /home and still access them all with a single password at boot.
So you basically create multiple partition inside a logical one? Sounds quite simple in fact. Are you sure that's the way it works? Are all of your files encrypted when the PC is turned off?

---

### Post by hyper_ch on 2008-01-30
well, you could use LVM across multiple partitions.... you can select that also during install (lvm encryption) but the way Oppewall described... I don't see how that should work.

---

### Post by Biochem on 2008-01-30
> **hyper_ch said:**
> The handling is not difficult.. during the boot process you will be asked to enter each encrypted partition's password... after that you can use it like you normally do...

Actually once multiple encryted partition are setup you can use keyfile with LUKS so you wont have to enter each passphrase. Technically the key-file is not encrypted, but since it's located on an encrypted partiton it should be safe. However make sure that /etc/crypttab is not readable, because anyone who can read it will know how to find the key and use it.

At this point, it is more a question of security vs usability. But, for those who worry about  thiefs accessing their credit card number, it should be more than enought.

---

### Post by hyper_ch on 2008-01-31
good point about the keyfile there :)

---

### Post by Madmoose on 2008-02-27
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=697841&amp;highlight=Lojack+for+laptops](http://ubuntuforums.org/showthread.php?t=697841&amp;highlight=Lojack+for+laptops) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **CaptainInsaneO said:**
> That's terrible to hear, so sorry for your loss. :( I think if I actually HAD a laptop and it got stolen I'd be ready to kill.

I'm not really sure what you mean by "protection to drive a person crazy". But I can say two things: 1) Ubuntu requires a password for login and 2) you can look into [LoJack for Laptops]("http://www.lojackforlaptops.com/"). It probably won't work in Ubuntu, so you could maybe keep a small windows partition for it. This could also work as a honeypot because most people (especially stupid-*** crooks) will see Ubuntu and not be able to crack the password and switch to (what they know) Windows. If they surf the internet and you've reported your laptop stolen, LoJack will report back to the master server and say "I'm here!" and you can tell that thief to have a fun go at prison. :guitar:

As for external hdd's, I don't really know because I build mine, but I've heard a lot of BAD things about Maxtor externals.

Lojack is good, but it doesn't work with ubuntu, It will only let you have one partition. If your try and duel boot it keeps yanking out the GRUB MBR, I'm trying to get them to support Ubuntu.

---

### Post by wieman01 on 2008-03-05
Something I wanted to share with everyone:

[http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")
[http://citp.princeton.edu/memory/media/]("http://citp.princeton.edu/memory/media/")

**Morale:** Turn your computer off while you don't use it.

---

