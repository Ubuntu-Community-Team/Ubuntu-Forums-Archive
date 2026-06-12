---
title: "building your own computer"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2007-09-05
well, id like to save up and either buy or build a new computer soon, and im wondering which would be cheaper to meet my needs. 

-i need a laptop, 
-preferably compact but doesnt have to be super-expensively-tiny, 
-id like to have it able to dual-run windows of some sort and linux...
-and so that means i need, is it an FAT or...the other one? lol
-and uh, is partitioning a disk hard?
-basic graphics and sound cards, whatever a dell inspiron is usually preloaded with (thats what i have now and its fine as far as graphics and sound goes)

basically, id like an updated version of my inspirion as far as hardware goes, that will dual run the above OS's. 

any suggestions?

---

### Post by Steve1961 on 2007-09-05
If you're interested in building your own PC, start with a desktop and use cheap parts to keep the cost down.  That said, there's a lot of really good deals around at the moment so it isn't always cheaper to build your own - although I personally like the satisfaction of building exactly what I want.  But if its a laptop you're after, and you have no experience of building a PC at all, I'd recommend just buying one.  If you like your Dell, just get an upgraded model.  They can all be setup to dual boot.

---

### Post by Nythain on 2007-09-05
Just about anything will really meet your requirements... I would recommend definately buying a laptop, its still not to terribly easy to build one from scratch yet like it is a desktop.
Craigslist usually has some great deals... possible ebay if you arent looking for anyting new

Other than that, best buy, wal mart, wherever really.

I would highly recomend one with a nvidia graphics card over ati... a decent sized hard drive (100+ gigs) (for enough room to dual boot well).
The wireless will probably be a little tricky to get installed right but there are tons of threads on here to help out with that.

Partitioning is pretty easy, dont know why so many are affraid of the idea... make sure you install windows BEFORE ubuntu when setting up your dual boot system... and presto you will be good to go

---

### Post by bodhi.zazen on 2007-09-05
> **Steve1961 said:**
> If you're interested in building your own PC, start with a desktop and use cheap parts to keep the cost down.  That said, there's a lot of really good deals around at the moment so it isn't always cheaper to build your own - although I personally like the satisfaction of building exactly what I want.  But if its a laptop you're after, and you have no experience of building a PC at all, I'd recommend just buying one.  If you like your Dell, just get an upgraded model.  They can all be setup to dual boot.

+1 on that advice.

---

### Post by Dr Small on 2007-09-05
I personally hate laptops, as I love big desktop's and towers, since I just built my own tower not to long ago. But if you rebuild an old machine, it is a whole lot more cost efficient than buying a brand new one.

Dr Small

---

### Post by BobCFC on 2007-09-05
You cannot build your own laptop they come pre-built although on some you can add extra ram or replace the hard disk.

I always build my own desktop although it takes months of study to choose the right bits and get them at the price/time so that you get the best bang for the buck.  If you get the latest stuff you will pay an unnecessary premium which will be half the price in a few months.

As said before if you are getting some sort of 3D graphics.. choose nvidia over ati 100%.. they have better linux drivers.  If you are just getting simple onboard graphics I think the Intel chips are best supported,


The easiest windows partitions to use are FAT32 because the support is built in.. but most machines with windows on come setup as NTFS these days.  You can get drivers called ntfs-3g to write to NTFS partitions but some people complain that they are slower.  

You wont have much space on a laptop anyway... somewhere around 100GB which is small compared to a desktop. If you want to download and share lots of movies between linux and windows it might be easier to get an external USB2 hard disk for storage... I got a Western Digital 500GB MyBook Pro for a good price.   This was FAT32 anyway so I just plug it in and use it on ubuntu or xp.


Partitioning is easy if you are confident.  The default Ubuntu install will squash the free space from your windows drive and make an ubuntu partition for you.   You could also do this before hand from the liveCD and make a FAT32 partition to share data.   The only trouble you might find is that many big laptop companies make a secret 5GB recovery partition at the end of the disk which has a backup of your windows on it.. As long as you don't delete the recovery partition it will be fine.

---

### Post by expatCM on 2007-09-05
Not sure that I agree with all the comments .....  building a desktop machine .. yes, by all means.   But not to save on cost (in absolute terms), rather more buy quality parts and to put together a machine to your own personal need - be picky with the configuration.

I have seen that cheaper deals on hardware typically have a warranty of say a year or less and when a year and a day passes there is often something that fails.  Better quality parts often give a longer warranty but that is only nice to have since the parts do not fail....  they keep on going.

A machine that will run trouble free for the extra two or three years may cost more at the outset but since its life is longer it really is a cheaper option.

From my perspective too many people want to buy the fastest chip and the fastest FSB and I really do wonder why, it simply is of no value to the average user who only wants browsing and email.

---

### Post by Nythain on 2007-09-05
> **BobCFC said:**
> You cannot build your own laptop they come pre-built although on some you can add extra ram or replace the hard disk.
actually with the right looking around and knowing what you are doing you CAN build your own laptop... its not an easy feat but i have friends who do it
> The easiest windows partitions to use are FAT32 because the support is built in.. but most machines with windows on come setup as NTFS these days.  You can get drivers called ntfs-3g to write to NTFS partitions but some people complain that they are slower.
i generally believe oposite this... i think you should stick with an extra partition in the native format of the os you plan on using most... if Windows then NTFS, if Linux then ext3... then just install the appropriate drivers for the other os... xp has a drive that allows read/write mount of ext2/3 and linux has the ntfs-3g wich allows read/write mount of ntfs... the reason i DONT suggest fat, ESPECIALLY if sharing files like movies or iso's is fat's limited filesize capabilities... it sounds great untill you download an 8 or 9 gig dvd iso and try to copy it over to teh fat partition, only to find out you cant, because its over 4 gigs

---

### Post by the.phantom on 2007-09-05
i might suggest finding a "real computer store" the small ones not part of a chain and local (mom and pop stores)

talk to them and they can give advice and usually they do sell a "bare bones" model

you can pick the hard drive and memory and cd/dvd's you want and install them yourself !

i have a small store about 20 miles from me and i love that place !

i can get help if needed and good support and good ideas of what to do !, and then i can take the info home and check prices and see what people think of the parts ( he has been right so far) 
mom and pop stores are disappearing so i would suggest you support the local one while they are still in business, and they have a wealth of knowledge !

---

### Post by BobCFC on 2007-09-05
> **Nythain said:**
> actually with the right looking around and knowing what you are doing you CAN build your own laptop... its not an easy feat but i have friends who do it


Your kidding?   And you think this is the right path for someone unsure about the difference between fat32 and ntfs?  You can build your own cars too.  Jesus.


 > **Nythain said:**
> linux has the ntfs-3g wich allows read/write mount of ntfs..


I said this.  I also said that is has limitations.  There is a reason why this is not enabled by default in Ubuntu.

Also the ext3 partitions are accessed in windows using an ext2 compatibility layer so you loose journalling.


How many 9gb DVDs is he going to keep on a ~100gb laptop with two OSs on it?  If you must download that then burn it to disk from the linux side.

---

### Post by SpiritIsReality on 2007-09-05
howdy

good thread, thanks all

trails

---

### Post by Nythain on 2007-09-05
> **BobCFC said:**
> Your kidding?   And you think this is the right path for someone unsure about the difference between fat32 and ntfs?  You can build your own cars too.  Jesus.
nowhere did i recommend doin so, i was just countering your use of definatives, note the cannot  in "You cannot build your own laptop".
> 
I said this.  I also said that is has limitations.  There is a reason why this is not enabled by default in Ubuntu.
you're right, it does have supposedly some limitations, though i havent encountered any problems, and neither have a whole lot of people. I assumed it wasnt included out of the box for numerous reasons, the main probably being the fact that its still beta technology... but you realize we are in linux land where almost everything is technichally still in beta... do you use beryl/compiz... its been beta forever... how about wine... more beta... other possible reasons i assumed were liscensing reasons... similar to why mp3 support isnt installed out of the box, but that doesnt stop everyone from making it one of the first things they install when they get ubuntu up and running.
> 
Also the ext3 partitions are accessed in windows using an ext2 compatibility layer so you loose journalling.

ill give you that one, but still, its there and its an option, wich is all i was trying to provide... its personally the method i use and havent had any problems yet (well except windows created a Recycled folder in root, and linux didnt so much like that)
> 
How many 9gb DVDs is he going to keep on a ~100gb laptop with two OSs on it?  If you must download that then burn it to disk from the linux side.
Well if they follow suit with your suggestion of buying an external hdd they arent limited to that 100gig are they... i just dont understand a 500gig fat32. I had a fat32 partition till the first video game dvd i tried to download. Thats when i reliazed the fat32 limitations... luckily it wasnt when trying to move over a raw video file (wow, those are huge)... thats really about it... i was just providing my view on things and giving alternatives (oh and correcting the use of definatives, sort of a pet peeve of mine, to many people think to many things are set in stone in this world)

---

### Post by BobCFC on 2007-09-05
Ok mate I don't want a flame war I'm just trying to think about the easiest way from his view.


EDIT:  [here]("https://help.ubuntu.com/community/MountingWindowsPartitions") is the guide to installing ntfs-3g in Ubuntu

---

### Post by cotcot on 2007-09-05
I have rebuild an old desktop myself because I wanted to select the components on best linux compatibility. Saved me a little money too.

---

### Post by notwen on 2007-09-05
> **Steve1961 said:**
> If you're interested in building your own PC, start with a desktop and use cheap parts to keep the cost down.  That said, there's a lot of really good deals around at the moment so it isn't always cheaper to build your own - although I personally like the satisfaction of building exactly what I want.  But if its a laptop you're after, and you have no experience of building a PC at all, I'd recommend just buying one.  If you like your Dell, just get an upgraded model.  They can all be setup to dual boot.

I've recently purchased one of the pre-loaded Ubuntu Linux Inspiron 1420n laptops nd I'm very satisfied.  I'm also currently in the process of dual-booting Ubuntu w/ WinXP.  Here is Dell's [site]("http://dell.com/open") for Ubuntu PCs.  And here is the [thread]("http://ubuntuforums.org/showthread.php?t=540397") regarding some of the people who have started dual-booting their pre-loaded 1420n w/ Windows.  Hope some of this info helps.  =]

---

### Post by LowSky on 2007-09-05
i suggest you buy a dell or gatway or hp... from where ever

---

### Post by mramsey on 2007-09-05
I have purchased a couple on ebay fro an ebay store called TechRenew. They typically have alot of Dells from the corporate world that have been cleaned and have no OS.  The last one I purchased was a Dell Optiplex GX260. Worked great and only $120.00. A Great place to start. BTW I have installed Ubuntu on 4  Dells in the GX series and had no issues.

---

### Post by m9ke on 2007-09-05
I bought a bunch of upgrades for an old PC recently.  A couple of observations that are as valid for buying components for building your own PC:

1.  Make 100% sure that a component is compatible with your box before you buy it.  You can do that on this forum, or maybe even better on a good vendor's website.  Newegg has a forum called "Eggspert" that helped me figure out that I couldn't easily use a newer SATA drive in my old box and that I needed an older IDE drive.  

2.  Read the reviews (often right on vendor website ie Newegg)  for anything you are thinking about buying.  Look for components with a high number of reviews, and a generally high rating.  For example, I would be more likely to buy a product with  5000 reviews totaling up to an overall score of 4.5 on a 5-scale than a product with 10 reviews totaling up to 5 on a 5-scale.

3.  Think about Linux-compatibility before you buy.  Look for the proposed product on this forum, and look in the reviews on the vendor's site for comments like "works with Linux" or even better "works with Ubuntu".  As long as you are going to buy a component, you have a choice and can select Linux compatible products.

Disclaimer:  even though I mention Newegg in this post, I have nothing to do with that company except I am a satisfied customer.

---

### Post by tech9 on 2007-09-05
I recommend NewEgg.com - I build all my own computers from newegg

---

### Post by Panganat on 2007-09-05
ACER is not a bad choice, economically, for a laptop. Think they just bought out Gateway.  Tigerdirect is a good source if you want to build your own box.  i find you will never get everything you want in an over the counter box. my $0.02. :):):)

---

