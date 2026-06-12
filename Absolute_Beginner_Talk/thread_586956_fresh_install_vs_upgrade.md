---
title: "fresh install vs upgrade"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-10-22
I've been doing some reading in order to make a choice between installing Gutsy through a fresh install or an upgrade.
For what i understand, it's always better to do a fresh install. My question is how much can we backup of the present system, in order not to waste 1 month putting things the way you like again.

I'll give my example.

Lost some days:
 - trying to put my wirelless card working;
 - trying to change the visual of my desktop;
 - installing all the software i need and all the configuration
 - copying all the files i need
 - creating links
 - installing VirtualBox with XP
 - video and audio codecs

How much of this can i actually backup? Won't it conflict with the settings of a fresh install?

---

### Post by dhruva023 on 2007-10-22
i think you should just upgrade.

it will be easier then backup.

---

### Post by NewJack on 2007-10-22
Well here a question for you....  why do you want to upgrade?  Is it because you need the newest thing going (like myself)?  Is Gutsy going to be that different than the version you are running now that you need to upgrade?  Do you have a separate /home partition?

If you do have a separate /home partition, it will make it alot easier to do a clean install since most of your music, movies, etc won't be formatted (As long as you choose not to format /home).  

IMHO clean install is the way to go.  From what I have read from others here in the forums, upgrading tends to present a lot of problems and conflicts.

So far I am loving Gutsy.  Good luck, whatever your choice.

---

### Post by Pulka on 2007-10-22
Why i want Gutsy....well, newer software, newer apps, newer look, better funcionality (i guess).

I do have a /home partition. My question is if all of those things i listed are in the /home partition.

---

### Post by forestpixie on 2007-10-22
I haven't if I was completely honest noticed that much difference - some things appear a bit easier - but you've got those sorted already. I'm glad I did the change - but mostly from curiosity as to how a change/upgrade compared to the hours and hours ... for windows:)

I will change to Hardy when it moves along  a bit but then I'm gonna stick with the LTS version.

I don't bother with eye candy so mine looks exactly the same as Feisty did and I've installed exactly the same software.

I upgraded originally from tribe5 to the RC - but ended up with a clean install

Just my pennysworth :)

---

### Post by AndyCooll on 2007-10-22
Since I keep my /home partition on a separate drive I've got a re-install down to a fine art and always prefer this method. I basically just follow some notes I have and re-installing the extra apps doesn't add too much time.

In the past this has always worked well for me ...though strangely enough, I've had some major problems with my old laptops this time round that I haven't encountered with previous new installations.

:cool:

---

### Post by philinux on 2007-10-22
> **AndyCooll said:**
> Since I keep my /home partition on a separate drive I've got a re-install down to a fine art and always prefer this method. I basically just follow some notes I have and re-installing the extra apps doesn't add too much time. 
:cool:

Would you mind sharing your notes, I've got a /home partition, they could come in handy if I decide to do a fresh install.

---

### Post by chr on 2007-10-22
i have just upgraded and had no serious problems.

chr

---

### Post by RomeReactor on 2007-10-22
Hi. Regarding a fresh install:

> trying to put my wirelless card working;
Your wireless card's configuration is stored in **/etc/network/interfaces**; your actual drivers are elsewhere on the root partition also, so a fresh install will require you to install the drivers again.

> trying to change the visual of my desktop;
Most of your user-installed themes are stored in your home folder, so you're likely to keep those.

> installing all the software i need and all the configuration
No way around that; since this is not the same version of Ubuntu, the packages must be reinstalled also.

> copying all the files i need
Assuming you don't overwrite your home partition, your files will be there; as for system files, see previous answer. 

> creating links
Links not found on your home partition will need to be recreated (or maybe not; it depends on what those links were for).

> installing VirtualBox with XP
Haven't used VirtualBox, so I don't know if it stores everything on your home partition, though i don't think so. I would guess you'll need to install it again.

> video and audio codecs
You'll also need to install those again.

On an upgrade, your wireless card and overall configuration--and most probably links to system libraries--should remain, as well as VirtualBox with XP. New versions of codecs and system libraries **will** need to be downloaded and installed, though.

The difference here is a faster process from a fresh install, but you lose your system configuration; or upgrade and keep the configuration, but spend more time downloading packages. Using the Alternate CD as a repository can help you speed up the upgrade, but I haven't tried that. And there's also the possibility (your mileage may vary) that your system doesn't upgrade correctly. In any case, make sure you burn an image of Gutsy (whether Live or Alternate) before trying the upgrade. If it doesn't go well, you can at least do a fresh install of Gutsy instead of Feisty.

---

### Post by Pulka on 2007-10-23
think i'll try an upgrade. Thanks for all your help

---

