---
title: "From Linux to Windows"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by FoL)Heero( on 2008-02-16
Greetings everyone,

Since short I've been using Linux : Ubuntu.

At the start it was very nice to use it,
but after a period of time I found out it was very hard for me, a gamer to use.

I cannot turn on music while gaming, I cannot alt tab, I cannot turn on so many program at once, etc... (even some games are not running!)

Now.

I tryed to return upon windows ( xp and vista ), which on I failed.
When I try to install windows xp / vista : something is wrong with the partition, or it cannot find a partition meanwhile I used the Gpart many to format a FAT32 or NFTS.
I can't reinstall windows for a reason somehow.
I even went to the shop where I bought my computer and they didn't know it either and told me to buy a cd in order to restore everything back ... ( I hope there is another way).

I would appreciate any help from here, or any links.
I've been searching for days and nights upon a solution which I did not found.

I hope you guys can help me. If you need more information just ask.

Thanks in advance,
Heero.

---

### Post by Linux_Man on 2008-02-16
Which install disk are you using? The OEM install disk or a purchased one?

---

### Post by Shippou on 2008-02-16
Maybe you should try what the store owner have said: buy a new CD (Windows CD).

But then first be sure to back up your files.

What do you really want to do in the first place: reformat or dual boot?

Just confused with your question...

---

### Post by shadowmaster79 on 2008-02-16
boot with windows xp cd and initiate recovery console.

you should type fixmbr and fixboot and restart now probe to install

Remove and add partitions with windows installer....

Bay:guitar:

---

### Post by kwacka on 2008-02-16
You might try one Microsoft support  - you've paid for it.

Alternatively, ask on one of the Windows forums - clearly you will find many more experienced Windows users than you will on a Linux forum. 

  ;)

---

### Post by FoL)Heero( on 2008-02-16
> Which install disk are you using? The OEM install disk or a purchased on

*erhms* , What do you mean by 'OEM'? I might sound nooblike, but actually I have no idea what it is.

> Maybe you should try what the store owner have said: buy a new CD (Windows CD).
What do you really want to do in the first place: reformat or dual boot?

Well, buying a new windows cd would be stupid (IMO) -> I already have some cds of them (legal ofcourse). 
+ I am not planning to spend another 50 € on a stupid 'recovery cd' (if I may call it like that).
> 
boot with windows xp cd and initiate recovery console.
you should type fixmbr and fixboot and restart now probe to install
Remove and add partitions with windows installer....

I'll experimentate more, thanks.

> 
You might try one Microsoft support - you've paid for it.

Alternatively, ask on one of the Windows forums - clearly you will find many more experienced Windows users than you will on a Linux forum.

Arg, Windows doesn't has that much forums.
And almost everywhere they've been asking for money, the dogs.

Well, 
Already thanks for your supporting.
I hope that I will find out the solution soon..

- Heero

---

### Post by forrestcupp on 2008-02-16
It sounds like you are using a manufacturer's 'restore disk' and not an actual Windows installation disk.  So you've already used GParted to create *and* format an NTFS partition, and it still didn't work?

Try using the [Super Grub Disk](http://supergrub.forjamari.linex.org/) to fix the Windows boot loader.

If you need a good Windows support forum, check out [Tech Forums](http://www.tech-forums.net/pc/f9/).  It's a great place.

---

### Post by jcitguy78 on 2008-02-16
Are you trying to dual boot or just run a single OS (Linux or Windows)? Just remember that anytime you try to use non-Bill Gates software with "free" software Bill doesn't like that because he didn't make any money off you. 


Stay Free!!!

---

### Post by uaharryh on 2008-02-17
I'm just in the process of doing this.  I wanted a bual boot with XP and Ubuntu, which was already on the PC.  When Win XP started to install it reported No Disk, this is because it couldn't detect the SCSI disk (No native driver).  I changes the BIOS setting from AHCI to IDE support for the HDD and then restarted the install.  I checked that my Ubuntu was OK before starting and it was.  I booted back to the XP install CD and started, it now found the Partition that I set up with GParted and started the install.  

While this all sounds good, the install didn't finish, it's taking ages for the last step.  I was expecting problems as the machine is newish and I need to put on a bunch of Driver.  Hoping that it finishes soon, so I can get on with doing the driver task and then fixing the boot was I can get back into Ubuntu.

Hope this helps.


Cheers,

Harry

---

### Post by ugm6hr on 2008-02-17
> **FoL)Heero( said:**
> I even went to the shop where I bought my computer and they didn't know it either and told me to buy a cd in order to restore everything back ... ( I hope there is another way).

You say you already have a Windows CD.  Did it come with your current computer?  If so - just take the computer and the CD to the shop and ask them to install for you.

If it did not come with this computer, did you buy it separately?  Or did it come with a previous computer?

If the former - it should work, as long as Windows has the correct drivers.

If the latter, it will not work.  And I believe it would be in contravention of the license.  Go buy a new Windows CD.

---

### Post by Bartender on 2008-02-17
> **FoL)Heero( said:**
> Well, buying a new windows cd would be stupid (IMO) -> I already have some cds of them (legal ofcourse). 
- Heero

I don't know what anyone else thinks, but when someone says they have several Windows CD's (legal of course!) but don't know how to use them it just sounds a little suspicious to me.

If these are legal, genuine, Windows install CD's, not recovery CD's with Windows embedded in them along with drivers and all the other crapware, then you should have absolutely no problems re-installing.   You would almost surely need to download/install drivers for the motherboard, video, audio, etc. afterward but Windows should install.

You could format the drive to NTFS first with GParted, but even that shouldn't be necessary.  The Windows installer should recognize existing partitions and ask if you want to format.

If you have pirated Windows CD's, or recovery CD's from a different model of computer than yours, then there's nothing more to be said.

---

### Post by FoL)Heero( on 2008-02-17
First of all :

I have no illegal windows cd's / downloads whateverso.

I do have : windows 98, xp & vista. 
I have a micro windows 98 'boot floppy disk', but yeh.
floppy disk -> I can not use floppy disks :/.
Although, we have 4 computers here.

I am still searching and trying out some steps which you people said.

Already thanks for the support,
I appreciate it.

Edit :
What about using windows as virtual machine,
and burning inside the virtual an image ?

---

