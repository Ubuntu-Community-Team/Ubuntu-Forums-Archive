---
title: "Help.."
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by mourad on 2007-01-08
I installed ubuntu and was excited with having linux as I was fed up with windows, but after a while from using ubuntu, I found the market is making it so hard for a linux user, there are so much restrictions ... 
So sadly I will go back to windows, but I need help on **how to uninstall or remove ubuntu from my system???** I guess it is worth of mentioning that I am not able to enter ubuntu anymore, every time I choose ubuntu from the boot screen, it tries to login but it gives me error, and I can't login any more using ubuntu.

Any help is appreciated, and I am going to miss all ubuntu community...
Thanks

---

### Post by oracle5 on 2007-01-08
I really can't see how you think linux is restricted.

---

### Post by aysiu on 2007-01-08
This HowTo should help:
[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

---

### Post by ardvark71 on 2007-01-08
> **mourad said:**
> I installed ubuntu and was excited with having linux as I was fed up with windows, but after a while from using ubuntu, I found the market is making it so hard for a linux user, there are so much restrictions ... 
So sadly I will go back to windows, but I need help on **how to uninstall or remove ubuntu from my system???** I guess it is worth of mentioning that I am not able to enter ubuntu anymore, every time I choose ubuntu from the boot screen, it tries to login but it gives me error, and I can't login any more using ubuntu.

Any help is appreciated, and I am going to miss all ubuntu community...
Thanks

Out of curiosity, what restrictions do you face? With multimedia?

Best Regards...

---

### Post by oracle5 on 2007-01-08
> **aysiu said:**
> This HowTo should help:
[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

I like the part that says "Additionally, Linux recognizes more than 40 different partition types..." Its nice to hear something positive about linux on the MS website even if its not intentional.

---

### Post by c-ron on 2007-01-09
It's too bad ubuntu isn't working out for you. You may just want to try to re-install to give it another chance. I'm loving kubuntu edgy 6.10! If you really don't want to see the grub menu at all and boot straight into Windows XP, you can boot your PC off of the Windows XP install CD, select recovery mode, select the command line, and type FIXMBR. Upon reboot, WinXP should load automatically. You can use a windows based tool like Partition Magic to repartition and get your harddrive space back.

---

### Post by yurimxpxman on 2007-01-09
> **mourad said:**
> I installed ubuntu and was excited with having linux as I was fed up with windows, but after a while from using ubuntu, I found the market is making it so hard for a linux user, there are so much restrictions ... 
So sadly I will go back to windows, but I need help on **how to uninstall or remove ubuntu from my system???** I guess it is worth of mentioning that I am not able to enter ubuntu anymore, every time I choose ubuntu from the boot screen, it tries to login but it gives me error, and I can't login any more using ubuntu.

Any help is appreciated, and I am going to miss all ubuntu community...
Thanks

First of all, I must let you know that there are open-source alternatives to everything. For instance, MP3 codecs can be installed from the package manager. Judging by what you've said, I assume that you do not yet know much about using Linux. (But that's alright.. it wasn't too long ago I was in your seat.)

If you're going to go through with putting Windows back on your computer, here's my advice. Use the XP disk to re-partition your hard drive and install Windows. Then use the Ubuntu CD to dual-boot Linux *and* Windows. That way, you have the best of both worlds.

---

### Post by oracle5 on 2007-01-09
Dual booting would not be too bad of an idea at all. I do it because I have some cad programs I have to use for my engineering classes that don't have linux versions and don't work in wine. I use linux for everything else.

oracle5

---

### Post by mourad on 2007-01-09
Sorry that I did not make it clearer in the first time, I do have a dual boot for windows and ubuntu, but I want to remove ubuntu/linux and make use of hard disk space, also I want to remove ubuntu from the grub menu (**the boot screen**), **in short, To Remove ubuntu totally from my computer without affecting my current windows !!!!!**

Some of you was curious about the restrictions I faced, well here are some, all websites that use macromedia flash 7 don't work, as there is no flash 7 for linux yet. All the internet phone companies doesn't have there version for linux, except for skype and yahoo, all the prepaid online phone compaines doesn't have for linux, I use Evoiz, and it doesn't work with wine. Adobe professional to create pdf files doesn't have a version for linux and doesn't work with wine. And finally my medical programs are designed for windows and they don't work with wine. It is so hard to keep shuffling between windows and linux when you don't have much time, it is hard to do somethings on windows, and then go to linux to do the rest of things, one needs one operating system that you do everything on. So sorry that microsoft is playing a monopoly.

**Any further help would be appreciated, I still need to remove ubuntu without affecting my current windows version ???**

**Thanks**

---

### Post by aysiu on 2007-01-09
Yes, and I've linked to how to do that. You use the Windows CD and the *fixmbr* command to give the Master Boot Record back to Windows. Once that happens, you can delete the Ubuntu partition from within Windows using the administrative tool called Disk Management.

Please read the link.

One correction, though: the lastest official release of Flash for Linux *is* 7. 9 hasn't been officially released (it's in beta) but is pretty stable and a lot of people use it.

---

### Post by yurimxpxman on 2007-01-09
> **mourad said:**
> Sorry that I did not make it clearer in the first time, I do have a dual boot for windows and ubuntu, but I want to remove ubuntu/linux and make use of hard disk space, also I want to remove ubuntu from the grub menu (**the boot screen**), **in short, To Remove ubuntu totally from my computer without affecting my current windows !!!!!**

Some of you was curious about the restrictions I faced, well here are some, all websites that use macromedia flash 7 don't work, as there is no flash 7 for linux yet. All the internet phone companies doesn't have there version for linux, except for skype and yahoo, all the prepaid online phone compaines doesn't have for linux, I use Evoiz, and it doesn't work with wine. Adobe professional to create pdf files doesn't have a version for linux and doesn't work with wine. And finally my medical programs are designed for windows and they don't work with wine. It is so hard to keep shuffling between windows and linux when you don't have much time, it is hard to do somethings on windows, and then go to linux to do the rest of things, one needs one operating system that you do everything on. So sorry that microsoft is playing a monopoly.

**Any further help would be appreciated, I still need to remove ubuntu without affecting my current windows version ???**

**Thanks**

Well, in that case, it's going to take a little more doing. You'll need to use your Ubuntu CD to enter LiveCD mode and resize your NTFS partition again, but this time you want to stretch it to 100%.

Once this is done, instead of installing Ubuntu, you'll want to exit the LiveCD and boot your Windows disk. Press R for the repair console. Type "logon", "fixboot", and "fixmbr".

---

### Post by Modernity on 2007-01-09
I am sorry Linux is not working out for you, but with that said, you have to give and take just alittle if you plan to use an alternative OS to Microsoft. If you are worried about the restrictions, then get your XP system back up and running like you want to, then build an economy system to learn linux on. This way you can use your Xp box for everyday use, but gives you a learning center to learn Linux. I know this may sound like alot to keep up with, but can be very rewarding in the end, just ask the other Linux users if they regret learning Linux.

---

### Post by oracle5 on 2007-01-09
> **Modernity said:**
> I am sorry Linux is not working out for you, but with that said, you have to give and take just alittle if you plan to use an alternative OS to Microsoft. If you are worried about the restrictions, then get your XP system back up and running like you want to, then build an economy system to learn linux on. This way you can use your Xp box for everyday use, but gives you a learning center to learn Linux. I know this may sound like alot to keep up with, but can be very rewarding in the end, just ask the other Linux users if they regret learning Linux.

That how I started out by running linux on an old machine and then after about 3 months I felt like I knew enough to dual boot my main computer. No regrets that's for sure.

oracle5

---

### Post by ardvark71 on 2007-01-09
> **mourad said:**
> Sorry that I did not make it clearer in the first time, I do have a dual boot for windows and ubuntu, but I want to remove ubuntu/linux and make use of hard disk space, also I want to remove ubuntu from the grub menu (**the boot screen**), **in short, To Remove ubuntu totally from my computer without affecting my current windows !!!!!**

Some of you was curious about the restrictions I faced, well here are some, all websites that use macromedia flash 7 don't work, as there is no flash 7 for linux yet. All the internet phone companies doesn't have there version for linux, except for skype and yahoo, all the prepaid online phone compaines doesn't have for linux, I use Evoiz, and it doesn't work with wine. Adobe professional to create pdf files doesn't have a version for linux and doesn't work with wine. And finally my medical programs are designed for windows and they don't work with wine. It is so hard to keep shuffling between windows and linux when you don't have much time, it is hard to do somethings on windows, and then go to linux to do the rest of things, one needs one operating system that you do everything on. So sorry that microsoft is playing a monopoly.

**Any further help would be appreciated, I still need to remove ubuntu without affecting my current windows version ???**

**Thanks**

Yes, I'm afraid all that would impact my decision too. I look forward to the day when there will be no need for people to have to dual boot because Linux will be far more desirable and just as workable (to an average user's point of view.) However, Linux is making strides and I'm sure it will eventually get there.

Best Regards...

---

