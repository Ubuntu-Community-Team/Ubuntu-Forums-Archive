---
title: "Wine to access Windows partition?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by cbs2186 on 2008-03-01
Is it possible to use Wine to run programs that are currently installed on my Windows partition, or will I have to reinstall a new copy of each program in Wine's pseudo-windows file tree?

For example, I play Guild Wars.  Will I need to install it both on the Windows Partition and the Linux partition to allow me to play the game from either OS, or can I only have it on Windows and then let Wine access it from there?

---

### Post by Oldsoldier2003 on 2008-03-01
no you'll have to install

---

### Post by Anduu on 2008-03-02
As far as I know you need the files in Wine's directories.

It is however not always nescessary to install through wine.For instance I know for a fact with WoW all you need to do is copy your WoW folder over to wines "virtual" drive ie /home/<username>/.wine/drive_c/Program Files/ and it works fine.

---

### Post by Oldsoldier2003 on 2008-03-02
> **Anduu said:**
> As far as I know you need the files in Wine's directories.

It is however not always nescessary to install through wine.For instance I know for a fact with WoW all you need to do is copy your WoW folder over to wines "virtual" drive ie /home/<username>/.wine/drive_c/Program Files/ and it works fine.
this is true as long as the program doesn't need to install anything in your windows/system or system 32 directories and doesn't make any crazy registry entires. Some prgrams work fine copying them across and others are less friendly under wine.

---

### Post by cbs2186 on 2008-03-02
Is this true even if I have read/write access to my Windows D: (Data) Drive?

Sorry for sounding doubtful, I just really don't want to install these things twice if I don't have to.  3-5GB per program for 3-4 programs is a lot of space, especially doubled.

---

### Post by timbounceback on 2008-03-02
I don't see why not. I'm not a wine expert (I don't use it), but can't you just cd to where the windows partition is mounted and run the program?

---

### Post by Oldsoldier2003 on 2008-03-02
> **timbounceback said:**
> I don't see why not. I'm not a wine expert (I don't use it), but can't you just cd to where the windows partition is mounted and run the program?

No you can't. Wine runs out of a "fake" windows installation.

---

### Post by Delkster on 2008-03-02
> **Oldsoldier2003 said:**
> No you can't. Wine runs out of a "fake" windows installation.

Well, you could try configuring Wine to use the real Windows partition mount point as the "fake" Windows drive. That might or might not work. Some of the native dll files might confuse Wine although I don't know what the default Wine configuration nowadays is like with regard to using available native dlls.

---

### Post by Anduu on 2008-03-02
I have been using Wine for quite some time now.Sometimes successfully...sometimes not.

I'm pretty sure if you could run apps directly from your Windows partition I would have seen it mentioned and I have not.

I suggested the possibility of copying files from your Windows install(...if it works...depends on the app...) for the simple fact that it saves a ton of time having to configure/customize everything the way you are used to.I had been playing WoW for a long time before I decided to try it under Wine and copying it over saved soooooo much time what with all the addons and customizations I was using.

> Sorry for sounding doubtful, I just really don't want to install these things twice if I don't have to. 3-5GB per program for 3-4 programs is a lot of space, especially doubled.

Using this method also acts as a safety net.If you cant get it to work under Wine for whatever reason you still have it in Windows.Once you get it to run under Wine you can remove it from Windows so there is no space wasted.

---

### Post by regbsn on 2008-03-02
If you install a program in Wine's "fake windows partition", can it be accessed by XP an run under windows? That way I could check out modifications/addons in both environments.

---

### Post by Oldsoldier2003 on 2008-03-02
> **regbsn said:**
> If you install a program in Wine's "fake windows partition", can it be accessed by XP an run under windows? That way I could check out modifications/addons in both environments.
No windows won't be able to see your wine installation or run programs from it.

---

### Post by CesarHideyuki on 2008-03-02
Well I was able to run Warcraft 3 that i had installed in my windows partition through wine. In fact i tried and couldn't. Then i installed in my linux part. It didn't work. But then i discovered that that was a problem with the movies in the game. Since i never discovered where the hell wine installed my game so i could delete the movies directory i unistalled it and deleted the movies in my windows partition. Then i run the war3.exe (is that the name? xD) and it work. I already formated my pc since i did it but as far as i remember all i had to do was copy my windows directory to wine directory and import the dll information (really forgot the name now, later i'll come and edit this part :D)

---

### Post by Oldsoldier2003 on 2008-03-02
> **CesarHideyuki said:**
> Well I was able to run Warcraft 3 that i had installed in my windows partition through wine. In fact i tried and couldn't. Then i installed in my linux part. It didn't work. But then i discovered that that was a problem with the movies in the game. Since i never discovered where the hell wine installed my game so i could delete the movies directory i unistalled it and deleted the movies in my windows partition. Then i run the war3.exe (is that the name? xD) and it work. I already formated my pc since i did it but as far as i remember all i had to do was copy my windows directory to wine directory and import the dll information (really forgot the name now, later i'll come and edit this part :D)

So what you're saying is that you could copy a game from windows into wine and run it.
 Yes, you can do this as long as you get all the dlls and overrides set. 

However, what you cannot do is "wine /sda2/windows/program files/somegame/game.exe" wine doesn't execute things that are outside of its environment, and your real windows drive is "out of the sandbox"

---

### Post by CesarHideyuki on 2008-03-02
Well, what i did was open sda1 and look for the warcraft directory and double click the war3.exe and it opened the game. In fact i  played the game only once because in the following day i formated my pc. And i had some troubles with the mouse (sometimes i'd click and it was as if i didn't). I though this was what was asked here xD
Anyway, i'll try again later.

---

### Post by Oldsoldier2003 on 2008-03-02
> **CesarHideyuki said:**
> Well, what i did was open sda1 and look for the warcraft directory and double click the war3.exe and it opened the game. In fact i  played the game only once because in the following day i formated my pc. And i had some troubles with the mouse (sometimes i'd click and it was as if i didn't). I though this was what was asked here xD
Anyway, i'll try again later.
Just for the hell of it I tried what you said. I stand humbly corrected, even though all the wine docs would suggest that you can't do it i tried opening apps from my ntfs drive and about 50% of the ones I tired launched in one fashion or another. It could just be because i already had a wine session open. However I'm pretty certain that its not a good idea to do it or the wine wiki and docs would say just map your windows drive and go to town...

---

### Post by soapytheclown on 2008-03-02
ive always been able to run WOW sucessfully from my windows partition (before i got rid of windows!) so yes you can with some applications

---

### Post by Chriis on 2008-03-02
I confirm,..i can even run winrar from ntfs to decompress file from desktop of linux lolll 

try it it's amazing!


Chriis

---

### Post by Oldsoldier2003 on 2008-03-02
> **Chriis said:**
> I confirm,..i can even run winrar from ntfs to decompress file from desktop of linux lolll 

try it it's amazing!


Chriis
Paintshop pro 7.02 wont run from the windows partition though it runs under wine... i'm probably trashing my ntfs partitions as we speak but it is kinda fun...

---

### Post by regbsn on 2008-03-03
So are you saying that some windows programs on the XP partition will run from the XP partition when running Ubuntu? Does the XP partition need to be mounted? I am not sure if a really understand the term mount...I am still searching for that answer.

---

### Post by Oldsoldier2003 on 2008-03-03
> **regbsn said:**
> So are you saying that some windows programs on the XP partition will run from the XP partition when running Ubuntu? Does the XP partition need to be mounted? I am not sure if a really understand the term mount...I am still searching for that answer.

last night i ran some apps that are not installed in wine by clicking on  them in nautilus after mounting the windows partition. of course i had to clean up a mess after I found a ton of crap in my home directory that was put there by the programs- so its obviously not supported behavior of wine, just a little side effect that you can run apps outside of wines "sandbox"

---

### Post by zvacet on 2008-03-03
Maybe you will find [this](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition) helpfull.

---

### Post by regbsn on 2008-03-03
Would you get "a ton of crap in my home directory that was put there by the programs" (quote from Oldsoldier2003) if the program resided normally on a NTFS shared data partition?

Also, can I run Windows programs that I installed into Wine when running XP.

I just do not have the disc space to double store anything. This is why I haven't decided on my partitioning plan for my non XP partitions yet. As it is I have yet to determine if I need one or two copies of OpenOffice and, if one, where to put it. But wait...that will have to be another post.

---

### Post by grimdeath on 2008-03-04
I got filezilla working with this cross drive method. Havent seen any junk in my home folder yet. I have tried booting photoshop cs3 for fun and was met with a message that it was trying to launch a web browser or something like that, but needed gecko...so it's downloading gecko now...we'll see what happens after that :P it's downloading SOOO slow

ill edit and tell in a moment

*edit*
looked like it it slowed down to a halt, but here's what happened when I canceled it:
[http://img205.imageshack.us/img205/8818/screenshotxr1.png](http://img205.imageshack.us/img205/8818/screenshotxr1.png)

it's almost working :P

---

