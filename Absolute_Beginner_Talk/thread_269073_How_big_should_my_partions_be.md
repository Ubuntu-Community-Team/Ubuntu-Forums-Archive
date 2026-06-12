---
title: "How big should my partions be?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by boogyman on 2006-10-01
Hey guys I'm about to install ubuntu for the first time on my laptop. It has a 100GB 7200RPM Hard Drive. I currently have XP installed and want to be able to duel boot so I can use both.
At the moment I have 52.2GB out of my 88.6GB Hard Drive space left and just downloaded unbuntu for intel. I wanted to know while I;m installing it how should the drives be partioned? I do play games every now and then so should I have a partion for for the OSs to share with games and documents and such or should I have a partion for them each? I also want to minimize the chance of viris's and spyware. Thanks all info will be appriciated
Bartman

---

### Post by bigken on 2006-10-01
I have 20 gig for windows 
10 gig fat 32 
10 gig for ubuntu /
10 gig home 
and 2 gig swap (twice the size of installed ram)

---

### Post by petri on 2006-10-01
First you have to do defrag until your hdd is "clean".

Second you have to leave space on your ntfs partition, minimum 20% empty.

Third there is no need to share games between these OS? Linx don't play them? 

Fourth, I would use about 10-15GB for the **root** (linux installation) and the rest to **/home** partition. Swap will be installed automaticly and it is about twice your RAM. In that way you always have your files safe when you do an upgrade or reinstallation or Ubuntu.

Here you can find how to plan and howto make partitions:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by boogyman on 2006-10-01
Well the games I want to play are 'Guild Wars' and 'Dawn of War' so your saying just leave them on my NTFS for XP?
So should I just Defrag once? I'm doing that at the moment.
So once I have defraged it I just run the installation and have 2GB for swap 20GB for Windows, 15GB for ububtu and the rest for /home?
That means /home will be about 50GB big. Or should I make XP's bit bigger if thats where I will be installing games. (I'm confused if I install a game on XP can I choose to install it in the XP drive or the /home drive?)
Sorry this is getting a little big confused with all this but I really wan to have it up and running. Thanks
Bartman

---

### Post by bigken on 2006-10-01
make your windows the bigger partion for your games 
make root 10 gig
home 20 gig 
swap twice your ram

download and burn this [gparted ]("http://gparted.sourceforge.net/livecd.php")liveCD and you can try the partion editor it quite easy

---

### Post by geezerone on 2006-10-01
Don't forget that you could create an extended partition to hold logical partitions for NTFS (data - games for instance) and another logical partition for your /home (ext3) partition.

You need to assess what you will store in your Ubuntu /home directory - e.g. dvds, iso files etc and plan storage accordingly.

Best wishes and hope it goes well! :)

---

### Post by petri on 2006-10-01
Defrag until you don't have any fragments left. That is the best.

If you decide to let ntfs have 20GB partition then your windos is now less than 16GB? If you plan to install and you probably will it is better to make ntfs partition bigger. I would have at least 35-40GB.

I have to confess I don't know about the games if they work in Linux but I think you will have to install the games for Linux separately from windows games.

/home is big, just getting bigger... mine is at 250GB which in reality is only 232,89GB. Vendors sell hdd with GB (gigabyte) but in reality it is Gb (gigabit) :rolleyes:

What ever  the size of ntfs(XP) is now double it when downsizing it's partition. If you have 16GB then have at least 32GB for it. And do make a backup of your important files.

P.S. When you have LiveCD and session going on you can actually download and install gparted with your Synaptic. No need to download the others and burn them ;)

---

### Post by boogyman on 2006-10-01
Ok I understand the GB and Gb but thats about it lol.
So my HDD is currently using 35GB of space with XP plus all my games, videos and music on it. I would want the music and movies on the sared partion so both OSs can use them so thats in the FAT32 partion. My games and XP will be on NTFS and how big should that be? And I'm not sure what I will install on the EXT3 partion apart from ubuntu I think I'll put it all in the FAT32 partion. So EXT3 wont need to be very big. And the Swap will be 2GB because my RAM is 1GB. and with that program linked before should I used that or the partioner incorporated with the installer?
Sorry if I dont make sence but this is all new for me.

---

### Post by SirShaggy on 2006-10-01
I too am fairly new at Linux. I have found on two of my systems that 10GB for root barely cut it. I now try to have 12 to 15GB for root. For some reason, my /usr and /var folders get kinda big?!?
So, as mentioned before, I double my ram size as a /swap partition, make a 12+ GB /root and the rest is my home.
SirShaggy

EDIT:
Here is what my desktop has:
100GB hard drive
30GB NTFS for XP
20GB FAT32 for my music that it shared between XP and Ubuntu
then the rst of the hard drive is an extended partition containing:
2GB /linux swap
12GB ext3 / 
and the rest is my /home ext3 also

---

### Post by petri on 2006-10-01
You can read the ntfs files from Ubuntu but you can't write.

If you don't need the write rights then you don't need a shared FAT32 partition. If you only want to view movies and listen music you don't need writerights. You can copy files from ntfs to ext3 but not viceversa. There is program that makes it possible but it is a kind of beta :rolleyes: 

Making partitions leads to that they  get too small with time passing by and then you have to resize them. That is not fun.

---

### Post by boogyman on 2006-10-01
Ok I understand then with my 100GB Hard Drive what should I do with it? Just have 2GB for swap, 15GB root (This is where ubuntu is installed is it not?) and the rest for NTFS (games, music and movies) Does this sound right?

---

### Post by bigken on 2006-10-01
no make a home partion also for linux

Sample 

50gig ntfs windows 
15gig /root
2gig swap
the rest /home

---

### Post by boogyman on 2006-10-01
Is the above what you suggest I do?
Thank you for your patience

---

### Post by petri on 2006-10-01
> Ok I understand then with my 100GB Hard Drive what should I do with it? Just have 2GB for swap, 15GB root (This is where ubuntu is installed is it not?) and the rest for NTFS (games, music and movies) Does this sound right?

No. :rolleyes: 

If you have 2 for swap 15 for root where's the /home?

Let XP have 60GB and the rest for automatic partitioning for Ubuntu. Then it makes one partition to root and /home and one for swap. You are going to upgrade soon anyway when Edgy comes and then you know how big /home you want/need. (You are going to ditch XP :cool:  )

I don't like reading manuals, they too boring. I like reading howtos and guides with pictures and examples which makes them easy (and fast) to understand. Here's two good ones for you, BTW for all of you:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by SirShaggy on 2006-10-01
we can only give you a rough estimate from what you have said.....
I'd say keep windows at 30 to 35 gig, then make a 10 to 20 gig fat32 partition to share music/photos/other files btween XP and Linux. Then 2 gig swap, 12 gig root and the rest your home partition.

Just a guess though. I don't know how much music or other files you will want to share. Hope that helps.
SirShaggy

---

### Post by bigken on 2006-10-01
there are many ways but for you 1st go make it easy and dont forget to defrag your windows 1st the reason for a home partion is if you ever need to install ubuntu again all your settings and files ect stay on the sperate 
partion ;)

---

### Post by boogyman on 2006-10-01
Well I don't use more then 15GB for videos and music combined and games between 4GB and 10GBs depending on what I'm playing. Most of my time on this computer is used on MSN, surfing the net and listening to music and a games every now and then. One thing I do like to do is have a cool looking toolbar, mouse pointer, wallpaper lol I know it sounds bad but hell I'm 15 lol. At the moment I'm using couserXP and windowsblinds so can I do things like that on unbuntu?

---

### Post by petri on 2006-10-01
I don't know.

Can you do this in XP?
[http://www.youtube.com/watch?v=V1iet8MWJr8](http://www.youtube.com/watch?v=V1iet8MWJr8)


EDIT: A better video at [http://www.ubuntuvideo.com/xgl_and_compiz_reviewed](http://www.ubuntuvideo.com/xgl_and_compiz_reviewed)

---

### Post by boogyman on 2006-10-01
Okay I'm impressed :D

---

### Post by Imsati on 2006-10-01
"Fourth, I would use about 10-15GB for the root (linux installation) and the rest to /home partition. Swap will be installed automaticly and it is about twice your RAM. In that way you always have your files safe when you do an upgrade or reinstallation or Ubuntu."


I went one step further than this and did the same for my Windows disk as well. C: I use solely for the XP OS; D: is for added software (Office, games, etc.) and the third are all my files.

---

### Post by SirShaggy on 2006-10-01
I must have looked at 25 different threads. All of them were different in how they installed their OS. I am sure there are some wrong ways, but basically it's a matter of preference. I'd say just be sure that your /home, /root and /swap all exist and that you get them big enough. It really is a huge pain to try to increase the size of a partition, I KNOW!!!](*,) 
Once you set it up, don't worry about it, just enjoy it! Ubuntu is a great place. No, it's not just an OS. I have been to several places that were just an OS. The Ubuntu community is a great place. Many people around willing to help and give you answers and explanations. I hope your visit is as great as mine has been. I'll never look back now, I'm hooked.
SirShaggy

---

### Post by boogyman on 2006-10-02
Ok what format should /root, /home and/swap be?
That all I should need to know now thanks.
Bartman

---

### Post by bigken on 2006-10-02
/root ext3
home ext3
swap

---

