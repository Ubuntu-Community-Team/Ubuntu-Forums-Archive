---
title: "reinstalling deb files from dvd rather then online"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by skew on 2006-08-29
I installed ubuntu without any problems(knock wood). I then updated 200 megs of updates on a dial-up account(56k), it took over 12 hours. I then somehow screwed up my ubuntu install by dicking around in a root account. My fault for sure, I accept full blame.  lesson learned, I decided to reinstall ubuntu . Before doing this I saved all the deb files from my cache to a dvd so that I would not have to spend so long reupdating my system over a dialup account when that time came. Well it's now that time and I have over 100+ files to be reinstalled from that dvd.  

  Simple queastion: How do I do that without having to click on each .deb file at time while it complains about dependencies,etc. ](*,)  Is there a way I can get the installer to look for each files dependancies on that dvd first before complaining and then install them?  I tried adding the dvd to synaptic but that didn't seem to work.

thanks,
jester

---

### Post by PriceChild on 2006-08-29
Can't you just copy them all back to the cache?

When updating, it should realise they're all already downloaded and just install them.

Hopefully :)

Pricey

---

### Post by catlett on 2006-08-29
I never did it but you cab use a cd rom (or dvd rom) with synaptic package manager. Put the cd in your drive. Then open up synaptic package manager. Select "settings" and then "repositories". When that window opens, select "add cdrom". I never did it so I do not know the entire process. But it should search the cd and add it to your synaptic cache. If it doesn't automatically hit "reload". After it does that you should be able to select "mark all upgrades". Then synaptic will take care of the debs and dependencies.

---

### Post by skew on 2006-08-29
I tried that and it didn't work. It wouldnt accept my dvd as an added cdrom (god knows why) and when i added it custom as /media/cdrom0/archives/ binary/ it still wouldn't work.:(

---

### Post by skew on 2006-08-29
Nobody else? Jezz can it really be this difficult?!!:???:

---

### Post by catlett on 2006-08-29
That stinks. I never tried it  but I know the feature. I wonder if it is only for Ubuntu install cds? I do not know what will happen  if you try to copy the debs to the apt cache. My debs are held in an archive inside the apt cache. I do not know if their being in the archive will trigger synaptic to notice them as upgrades. In /var/apt/cache I have 2 files with the cache info from the repositories. Those are the files that tell synaptic what debs are in that repo. Synaptic then checks them against your system to see if there are any packages available for upgrade.  During an update, the debs are not downloaded, only info about what the repo is holding. When you select to upgrade, then it downloads and installs the debs. Once they are installed, the deb goes into the archive. That is why I do not know if synaptic pays atttention to a "new" deb in the archive. I'll try and see if there is something I am missing about adding a dvd rom.

P.S/ I just checked the ubuntu add repository wiki [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) It doesn't say you need an ubuntu cd. It appears any cd can be used. It does say you need to enter the "description of cd". Does you dvd have a title. Sometimes the program that made it comes up as the title. YOu might want to open totem media player and select "movie". It will then say play disc "descrition of disc". Try using that description when adding to synaptic. I posted the link so you can check the wording yourself. That appears to be the only thing I can see that is different from what you are doing.

---

### Post by skew on 2006-08-29
Thanks My-Man.  I hope you can find the answer.

 I just seems to me to be a real problem that this isn't an easier fix.  I'm not the only linex user on dial-up and to have to spend up-teen hours online downloading the same programs that are already archived on a dvd seems well...frankly nuts!   

  If Linex is ever to compete against MS (my mouth to big G's ears) then these little quirks have to be fixed(imho) so newbies like myself aren't always yanking out our collective hair because of some many dicky littly problems.

---

### Post by catlett on 2006-08-29
> **skew said:**
> Thanks My-Man.  I hope you can find the answer.

 I just seems to me to be a real problem that this isn't an easier fix.  I'm not the only linex user on dial-up and to have to spend up-teen hours online downloading the same programs that are already archived on a dvd seems well...frankly nuts!   

  If Linex is ever to compete against MS (my mouth to big G's ears) then these little quirks have to be fixed(imho) so newbies like myself aren't always yanking out our collective hair because of some many dicky littly problems.

This should be p[ossible because they have repository dvds out there. I do not know why it isn't workinmg for you. [http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=1113&zenid=7afmkrsvtgfugshugbocoigj15](http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=1113&zenid=7afmkrsvtgfugshugbocoigj15)
That is a pay for packages dvd but it is doing the same thing you are.
[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en) That one is about doing what you just did. Actually I am going to browse that one for their instructions on using tha add cdrom feature.

---

### Post by skew on 2006-08-29
Thanks again, i'll look over your links. 
I'm off now for tonight i'll check this thread again in the morning. 

Here's hoping for a sure-fire solution!:-D  

Cheers!

---

### Post by Toxicity999 on 2006-08-29
You need to turn it into a repository much like the default install disks pre dapper. Might want to just read up on that, it isn't very difficult. If you didn't want to do that so much just type sudo dpkg -i then drag a few of the updates at a time to the terminal window... only problem there is when you hit the piece by piece dependancies if you have the time install them one by one along with what it calls for from your disk... but if you have broadband no complaining! Haha dialup here my friend.

---

### Post by timmahhny on 2007-03-05
I am currently attempting the same thing; tried to update to edgy, screwed it up, reinstalled Dapper on the second hard drive; made a DVD of the packages, because I am on a bandwidth limit here, small one. I have attempted to try to add the DVD but it won't do it.
 I will try to just copy the packages into the archives on the new install, but need to change the permission before it can be done. 

 I too will look at how to use a DVD as I know it is done, because of the DVD's you can buy to install and upgrade Ubuntu. 

 If I find something that works I will post it.

Timmahhny

---

