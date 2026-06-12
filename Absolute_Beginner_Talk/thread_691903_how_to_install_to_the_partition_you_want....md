---
title: "how to install to the partition you want..."
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by shtewe on 2008-02-09
ok i have an asus laptop with 2 partitions on it and the 30 gig is used for xp and the other is blank.  i wanted to install ubuntu on the blank 20 gig hard drive but when i try to install it using the live cd, it wants to install it on the primary partition which is my xp!   

how do i make want to install into the blank 20 gig partition?

thanks

---

### Post by overdrank on 2008-02-09
> **shtewe said:**
> ok i have an asus laptop with 2 partitions on it and the 30 gig is used for xp and the other is blank.  i wanted to install ubuntu on the blank 20 gig hard drive but when i try to install it using the live cd, it wants to install it on the primary partition which is my xp!   

how do i make want to install into the blank 20 gig partition?

thanks

HI and you would select manual partition, this link has some screen shots that may help. 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by shtewe on 2008-02-09
ok thanks, i looked at that alternative but it just confused the hell out of me

---

### Post by overdrank on 2008-02-09
> **shtewe said:**
> ok thanks, i looked at that alternative but it just confused the hell out of me

HI and I understand I was confused when I first started. If you have two existing partitions on the drive then you would select the second partition to install on. If you would like you could always format the second partition from within windows and you  could format it like a fat32 and then when you go to install Ubuntu just selected the fat file system for Ubuntu to format and install. This is if your windows partition is ntfs there will be no confusion in which partition to install Ubuntu on.

---

### Post by shtewe on 2008-02-09
sorry but i am still confused, the guide doesn't show u step by step to fo through with manually installing the OS

soo confused

---

### Post by overdrank on 2008-02-09
> **shtewe said:**
> sorry but i am still confused, the guide doesn't show u step by step to fo through with manually installing the OS

soo confused

The fourth screen shot in dealing with partitions section is manual partitions
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Then the next screen shot is showing that you will need to set it as a root mounting point. If you do not feel comfortable with it then please wait until you do. And back up all your data.

---

### Post by shtewe on 2008-02-09
sorry to be a noob but it says u need a swap partition and a home partition.  i made a new partition and i thought it would be in the 20 gig partiton but its not.

i am just wrecking everything up.  i made the new partition 9 gig for the /home but obviously that won't work.

SILLY ME!

---

### Post by overdrank on 2008-02-09
> **shtewe said:**
> sorry to be a noob but it says u need a swap partition and a home partition.  i made a new partition and i thought it would be in the 20 gig partiton but its not.

i am just wrecking everything up.  i made the new partition 9 gig for the /home but obviously that won't work.

SILLY ME!

Ok you will need to do some more investigating on that link I gave. Where did the new partition show up that you created? If it is not where you wanted it the click "undo changes to partitions".

---

### Post by shtewe on 2008-02-09
well i rezized /dev/sda5 to 10 gig and the rest of it renamed itself free spac and it goes straight at the bottom with no / at the start of it.  

when i try to click undo changes to partitions, the end result is the same, nothing happens.

hmmm.  why can't there be a guided installation of to select this partition.  soo much easier

---

### Post by overdrank on 2008-02-09
> **shtewe said:**
> well i rezized /dev/sda5 to 10 gig and the rest of it renamed itself free spac and it goes straight at the bottom with no / at the start of it.  

when i try to click undo changes to partitions, the end result is the same, nothing happens.

hmmm.  why can't there be a guided installation of to select this partition.  soo much easier

HI and if you are installing Gutsy 7.10 there should have been a option to do just that. Something like use continuous or largest free space. Could you post a screen shot of the manual partition page. Screen shot is located under applications, accessories.

---

### Post by shtewe on 2008-02-09
i have tried looking for videos on youtube to help me with this problem but all the installation vidoes just use a guided installation form.  i can't see why anyone would get stuck using guided.

if a person could upload a video of them selves using the manual way of installing ubuntu (using partition editor) that would be awesome and it would help alot of other noobs like me that like watching videos then just screen shots..

just a suggestion

---

### Post by shtewe on 2008-02-09
[http://i255.photobucket.com/albums/hh150/shtewe/Screenshot-Install.png](http://i255.photobucket.com/albums/hh150/shtewe/Screenshot-Install.png)

thats the screenshot of it


weird.  it never came up with the option to install with the largest free space.

thanks for helping me out

---

### Post by overdrank on 2008-02-09
> **shtewe said:**
> [http://i255.photobucket.com/albums/hh150/shtewe/Screenshot-Install.png](http://i255.photobucket.com/albums/hh150/shtewe/Screenshot-Install.png)

thats the screenshot of it


weird.  it never came up with the option to install with the largest free space.

thanks for helping me out

Ok there is a video of manual partitioning
[http://www.youtube.com/watch?v=XcvmNpWI8Cg](http://www.youtube.com/watch?v=XcvmNpWI8Cg)
On your screen shot you have 3 fat32 partitions and I am assuming that sa2 is your windows partition? You stated that sda5 is the partition you just created, correct? If so then you can delete it.
Have you booted into windows since you have been trying to install Ubuntu?

---

### Post by shtewe on 2008-02-09
ok the SD5 thing was already there but i changed it to 10 gig.  and the rest of the space went to the free space thing.

i have not booted up windows yet, should i?

---

### Post by Paqman on 2008-02-09
Hmm, the fact you've got three FAT32 partitions will make things trickier. You can only have four normal partitions on a drive, and you normally need at least two for Ubuntu.

You can get around this by creating an extended partition using all your free space. You can then create the Ubuntu partitions inside the extended partition to get around the four partition limit.

---

### Post by shtewe on 2008-02-09
asus have made the 3rd one which is only 2 gig for the drivers and crap needed for reinstallation of xp.

without that, i will need to aquire a windows xp cd.

it is annoying with that extra partition.

my sis uses the laptop the most and she wants xp becuase its "easy" so that is why i want to dual boot it.

---

### Post by overdrank on 2008-02-09
> **Paqman said:**
> Hmm, the fact you've got three FAT32 partitions will make things trickier. You can only have four normal partitions on a drive, and you normally need at least two for Ubuntu.

You can get around this by creating an extended partition using all your free space. You can then create the Ubuntu partitions inside the extended partition to get around the four partition limit.

Paqman is correct and I did not point that out as I thought the op was confused enough. shtewe yes I would suggest booting to windows just to make sure that the changes you have made have not damaged windows. :(

---

### Post by mikewhatever on 2008-02-09
Why not simply use the free space you have. Right click on it to create partitions, or use 'New partition' button. You need to create at least two partitions for Ubutnu, root and swap. (One partition in not enough.) A separate home partition is also an option, but that is up to you. Do not create any more primary partitions because of 4 primary partitions limit per HDD.

---

### Post by shtewe on 2008-02-09
my xp is fine but now my local disk (D) is 10 gig instead of 20. silly me

hmmm wat should i do?

i can't wait until i get my own pc.  i can do watever i want to it.

i just start my computer systems course last week so i will learn about linux and stuff.

woop woop

---

### Post by Paqman on 2008-02-09
> **overdrank said:**
> Paqman is correct and I did not point that out as I thought the op was confused enough. 

Agreed, this is shaping up to be a very complicated install for a first-timer.

Is it possible to get rid of one of those FAT32 partitions? One is a reinstall partition, one is Windows, what's the other one? Data?

---

### Post by shtewe on 2008-02-09
the other one is nothing.  just a blank partition

---

### Post by shtewe on 2008-02-09
don't worry.  i will reinstall windows on the laptop and choose to only have 1 partition instead of 2.

then i will install ubuntu the guided way of resizing that partition.

easy

thanks for your help.  this is why i love ubuntu, because of the community

---

### Post by overdrank on 2008-02-09
> **shtewe said:**
> don't worry.  i will reinstall windows on the laptop and choose to only have 1 partition instead of 2.

then i will install ubuntu the guided way of resizing that partition.

easy

thanks for your help.  this is why i love ubuntu, because of the community

HI and wait there is no need to do that. you stated 
my xp is fine but now my local disk (D) is 10 gig instead of 20. silly me
If there is no data on that partition then just delete it and then create a extended partition then you will be able to install ubuntu on the partition. You will need a extended partition as stated be the reasons previously.

---

### Post by Paqman on 2008-02-09
> **shtewe said:**
> don't worry.  i will reinstall windows on the laptop and choose to only have 1 partition instead of 2.


I don't think you'll need to go that far. If it's an empty partition you can just delete it. If it's adjacent to some free space then you're in business. Otherwise you might want to move the other paritions to make one big area of free space. Moving a partition takes a while, and i'd HIGHLY recommend backing up the data on it before starting.

---

### Post by vyco10 on 2008-03-08
Hello all. This is my first post on this forum. I'd just like to say how awesome this forum is, how awesome Ubuntu is, and how awesome Linux is in general.

Moving right along... the reason I am posting in this particular thread is because I am having similar questions regarding the installation of Ubuntu on a separate hard drive. The hard drive to have Ubuntu installed on is a 2.5 hard drive that is connected to my desktop PC via USB. I have two hard drives in the desktop PC.

My question is this: If, when going through the install with Ubiquity, I choose the Guided - use entire disk option:

[INDENT]"SCSI5 (0, 0, 0) (sdc) - 20.0 GB "technical_name_of_hard_drive_here"[/INDENT]

Will my two internal hard drives in the desktop not be touched? Basically, I'm confused by the differences between the Guided options and the manual options. I've read where the Guided options are good for those who want to create a dual boot hard drive, but that isn't what I want. But I just want to make sure that if I choose the Guided option that i don't mess up my other two drives.

By the way, here is a screenshot of the install window:

[IMG]http://i247.photobucket.com/albums/gg122/vyco10/Screenshot-Install.png[/IMG]

Thanks all.

---

