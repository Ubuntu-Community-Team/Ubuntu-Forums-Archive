---
title: "problems installing 7.04 on HP Pavillion a1640n"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Greglu on 2007-06-19
Hello all,
I am brand new to linux as of today - well almost anyway.

I downloaded the Ubuntu 7.04 release, created the cd, booted from it and got stalled with the following:

bin/sh: Can't access tty; job control turned off
(initramfs)

Can anybody shed some light on this state of affairs.

My machine currently runs WinXP Media Centre Edition.

Cheers
Greg

---

### Post by Alex&amp;Linux on 2007-06-19
Thats a tough one.
Perhaps you could try choosing a different option in the boot menu for the live CD? 
I read that removable storage like usb harddisk, floppy disks could cause this.
Also, it looks like a problem that several are running into with ubuntu/kubunt/xubuntu on some newish computers.
Im sure someone with more experience will come along and save the day!

---

### Post by Greglu on 2007-06-19
Hi all,
I decided to try the 6.06 release, and it worked just fine - so now is there a simple way to upgrade to 7.04?

Cheers
Greg

---

### Post by Alex&amp;Linux on 2007-06-19
Good move on trying 6.06!
Its usually recommended to clean install, according to several user experiences Ive stumbled across, however, upgrading through you existing version can work!

It will be necessary to upgrade to 6.10 (edgy eft) before 7.04.
Here is a great guide that helped one of my amigos earlier:

[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html)

Ill try to track down a solution to your previous issue, as it may not work perfectly using upgrade!

---

### Post by DBGOTD on 2007-06-19
Okay so I had the same problem and I had an ubuntu Edgy disc so I decided to install that and then upgrade to feisty fawn. Well, edgy loaded fine, the upgrade went fine, but then when I restarted it gets to the loading screen (with the ubuntu symbol) and then does nothing. I waited 5 minutes and it still wasn't loading so I booted in the live disc, mounted my hard drive and checked menu.lst for live=break, which it didn't contain anywhere. So now I'm really stuck!

Help?

---

### Post by Alex&amp;Linux on 2007-06-19
Thats odd!
Ive had a few little problems like this, and I believe that I just reinstalled!
did you try booting up in a recovery mode?

---

### Post by DBGOTD on 2007-06-19
Yea when I try to boot in recovery mode it does nothing as well. I don't understand it. I installed edgy, and it worked perfectly, then I upgrade to feisty and nothing works. UGH. It makes no sense.

---

### Post by DBGOTD on 2007-06-19
And another note, I used to have feisty on here but i reformatted my computer and now these are the problems I'm having.

---

### Post by Alex&amp;Linux on 2007-06-19
Regarding these problems following an upgrade, unfortunatly it looks like "they happen" some times!
Most commonly I hear of problems with packages etc.
It is recommended to clean install to desired version, or reinstall 6.10 and attempt the upgrade again!

Can you boot into text mode?

---

### Post by DBGOTD on 2007-06-19
nope, can't boot into text mode either...sigh. Thanks for the help. I think maybe i'll just install edgy and leave it at that for awhile. Thanks again.

---

### Post by molly_001 on 2007-06-19
Just wanted to chime in -- last week I wanted to install Ubuntu 7.04 Feisty Fawn
onto an HP Pavilion a1210n.  I've installed 7.04 on all my machines and overall
have installed Feisty (or in history, Dapper and Edgy) on about twenty five
occasions.

I always use the Alternate Install CD for much more fine-tuned control over
the installation and data partitions.

In all my experiences, this HP Pavilion Media Center was the first that I could
not get 7.04 to install.  (I did not attempt to install 6.06 - but thanks for the tip.)

Ironically, I get to try again on this same a1210n over the next weekend.
(The new hard drive that I had installed as the boot volume in this a1210n 
last week faulted and Seagate is sending me another.)
So I'll report back how it goes.  I plan to try to install Feisty again after
installing Windows.  If it fails, I'm going to take particular note of where or
how it does seem to fail.  And I will try 6.06 if 7.04 won't take.

By the way, these HP Pavilion Media Center machines are the weirdest
I have ever worked with.  It has something to do with how the controllers
for the hard drives on these boards work.  For instance, VirtualDrive 9
would not install in Windows XP on this a1210n.  Farstone (the maker of
the VirtualDrive series) had to send me a new version which specifically
will install on these HP Media Center machines.

---

### Post by jimrz on 2007-06-19
had a similar problem...found [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=474693&highlight=BusyBox+v1.1.1")... have not yey tried, but planning to this coming weeked

---

### Post by Alex&amp;Linux on 2007-06-20
No problem!
Though, dont give up, and certianly seek more knowledgable members for troubleshoots!
There is always a solution.....somewhere :)

---

### Post by Greglu on 2007-06-20
Thanks alot,
I am going try this, however 6.06 did not recognize my network adapter, it is a Intel(R) 82562V 10/100.  I found this really odd, how do I get it do that - the docs say to select the ADD button in the network window and then simply add Ethernet - problem is I do not have a ADD button in the Connections tab - hmmm.

Thanks for your help so far
Cheers
Greg

---

### Post by molly_001 on 2007-06-20
> **Greglu said:**
> Greglu -- 

 6.06 did not recognize my network adapter, it is a Intel(R) 82562V 10/100.  I found this really odd, how do I get it do that - 





At this moment in time are you 100% certain that the drivers for the adapter chipset (network adapter you mentioned by name) are loaded into the linux driver system?

---

### Post by Greglu on 2007-06-20
No, I am not 100% certain.  I have to confess that I assumed with such a generic card that the chipset would be supported, coupled with all the incredible things I was hearing about Ubuntu's Linux - I thought these types of issues would not exist.  I expected others - but not out-of-the-box type of problems.  Having said that, I agree with your comments on the Pavillion Media Centre machines - they have really quirky personalities.

Cheers
Greg

---

### Post by molly_001 on 2007-06-20
I agree with you, it is likely that the chipset drivers were loaded at install.
However what is your result when you do command iwconfig  (in terminal) ?

---

### Post by Greglu on 2007-06-20
Hello Molly,
when I run iwconfig I get a message saying that no wireless networks found???

In your considered opinion, if I were to buy a machine just for Linux what would you recommend?  I don't think I can afford the productivity hit to diagnose and fix all these little/big things - I need to be up and running quickly.

Cheers
Greg

---

### Post by molly_001 on 2007-06-20
Get any lower-end Dell desktop with Ubuntu installed, not more than $450.
 
You're surely not the first person to have trouble getting the 562V chipset to work properly, and I'll bet a thread exists for a quick solution, too.
 
It's generally a matter of getting the right driver package.  Do a google on
intel wireless 82562V ubuntu
or leave off the 'V'
seewhat comes up.

---

### Post by jimrz on 2007-06-20
> **Greglu said:**
> Thanks alot,
I am going try this, however 6.06 did not recognize my network adapter, it is a Intel(R) 82562V 10/100.  I found this really odd, how do I get it do that - the docs say to select the ADD button in the network window and then simply add Ethernet - problem is I do not have a ADD button in the Connections tab - hmmm.

Thanks for your help so far
Cheers
Greg

one of my boxes has the intel 82566DC 10/100/1000 ethernet and it's drivers were not included in the kernel until edgy (6.10). your's may be the same situation as the model #'s are pretty close.

---

