---
title: "Upgrade to Gutsy, what to do first"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Hopworks on 2007-10-28
I can't say that I'm a complete noob at Ubuntu, with a few months under my belt, but I'm new enough to worry about upgrading to Gutsy.

Every time I update my Ubuntu Feisty 7.04 Server, I see that button to upgrade now to 7.10. I want to click it, but I think of it breaking my almost working MythTV, my LAMP config.

So my question is; is there a way to backup my 7.04 so I can easily go back to it if things go wrong? I don't know the vital stuff to backup and a full backup would take up more room than I have on my Linux box. I'm really anxious to upgrade to see if my remote/receiver/IR Blaster package I got with my unsupported 1600 will work with Gutsy. I want to know before I RMA it to Hauppauge for a supported replacement.

I've worked so hard, jumped through some serious flaming, razor-wire lined hoops to get my database server, my apache server, my webmin, MythTV, and desktop to where I want it. I don't know enough to recover from multiple issues that may arise, and a read a lot of threads about MythTV breaking.

I had a major problem once (can't remember the specifics) where I changed my video card, and had to use the live CD, and edit some config file with a ton of research just to get back to a GUI environment. As a matter of fact, I think that's how I reinstalled Feisty from Edgy early on with my exploration with Linux.

I'm hooked now, and Feisty Server 7.04 is a huge part of my life so I just want to make sure I cover all the bases prior to going into the abyss. :-({|=

Thank you for your time!

Hop

---

### Post by oilchangeguy on 2007-10-28
if it ain't broke, don't fix it.

---

### Post by Hopworks on 2007-10-28
> **oilchangeguy said:**
> if it ain't broke, don't fix it.
I LOVE that! I agree, and wouldn't even consider it if it weren't for this damn VISTA-ONLY MCE remote package I have and NEED to use. I searched, and sure enough, there was a thread that said after the user upgraded to Gutsy, his remote worked fine. It's really important since my recording of programs right now is limited to me making sure the channel is right on my cable box and then watching TV in Myth. It does well at that, but the level of control is mediocre at best.

EDIT: oilchangeguy; I hear ya, but judging by the amount of posts you threw up, maybe you can direct me to a guide or a good thread on what I can do to secure my current installation? I would appreciate it.

---

### Post by por100pre1 on 2007-10-28
Feisty will continue to be supported for a long time. Ignore the upgrade button and enjoy your Feisty installation. It is a good idea to use rsync to backup your files to an external hdd, even if you don't upgrade at this time.

---

### Post by Pumalite on 2007-10-28
Stick to a system that is working and you like.

---

### Post by oilchangeguy on 2007-10-28
> **Hopworks said:**
> I LOVE that! I agree, and wouldn't even consider it if it weren't for this damn VISTA-ONLY MCE remote package I have and NEED to use. I searched, and sure enough, there was a thread that said after the user upgraded to Gutsy, his remote worked fine. It's really important since my recording of programs right now is limited to me making sure the channel is right on my cable box and then watching TV in Myth. It does well at that, but the level of control is mediocre at best.

EDIT: oilchangeguy; I hear ya, but judging by the amount of posts you threw up, maybe you can direct me to a guide or a good thread on what I can do to secure my current installation? I would appreciate it.

please define, what do you mean by secure my current installation?

---

### Post by skompier on 2007-10-28
> **oilchangeguy said:**
> if it ain't broke, don't fix it.

+1

I learned the HARD way and went back to feisty. I didn't lose any data because I backup important files. I did spend a lot of time reconfiguring everything, but that's the price I paid...:)

---

### Post by Pumalite on 2007-10-28
Save /home (including 'Hidden Files') and data to CD's, DVD's or an exteral drive. You can use PartImage.

---

### Post by Hopworks on 2007-10-28
> **oilchangeguy said:**
> please define, what do you mean by secure my current installation?Good point, as securing might relate to keeping bad guys out.
I meant, making sure I have what I have NOW available later if it goes bad. To me, going back a few years, securing it meant not just get it working, but cover all the bases and make sure you have a valid backup. =)

---

### Post by Hopworks on 2007-10-28
> **skompier said:**
> +1

I learned the HARD way and went back to feisty. I didn't lose any data because I backup important files. I did spend a lot of time reconfiguring everything, but that's the price I paid...:)That's what I'm trying to avoid. The reason why is because I'm so busy researching the right processor for my new system (a friend just threw AMD into the mix, which complicated things), Real Life stuff, chores, and my real job.

I LOVE Googling answers to my nagging Linux problems, and fixing them, gaining knowledge that might help others, and the technical aspect of Ubuntu, but I don't want to waste time getting back to what I had because I made a bad decision.

I had a radical idea. Just install 7.10 on another drive. I have dozens of them on my tech rack just waiting to fail! lol. Seriously, there are 40gig, 80gig, even higher that I'm not using. If I'm not mistaken, I can just change the boot order in my bios to go from one to the other and not worry about dual boot.

I have a large PSU so I'm not worried about throwing another drive in the rack. Then again, I'd like to migrate my current settings and stuff to the new install. Great, another brick wall. ](*,)

---

### Post by Pumalite on 2007-10-28
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Mojosdad on 2007-10-28
> **oilchangeguy said:**
> if it ain't broke, don't fix it.

Can't help but agree. I've gone through all distros since Breezy, and Gutsy has provided me with the most disappointing experience so far. I've posted recently about broken DMA and video with the Gutsy kernels and whilst I have fixed it these, the solution brings its own problems.

IMHO at the moment Gutsy is not worth the upgrade; my Feisty install was rock solid, and I wish I hadn't taken the plunge quite so early!

---

### Post by borimrr on 2007-10-30
I tried to upgrade to feisty bu it just wouldn't let me through Update Manager because it would give me errors while trying to fetch some files :(. I downloaded the Live CD of Gutsy and resized the disk during the installation to use Feisty (mostly becuase of the wireless internet) and saw that Gutsy is extremely basic. The only good thing perhaps is the integrated Compiz and no need to got through the Xgl process. But anyway I got tired of not being able to get the wireless to work. Feisty works perfectly , and so far it beats Vista in every way so I really didn't see the reason to upgrade now with the next distro Hardy Heron coming in April 2008 (based on what has been said so far). So really, the next Windows verison is coming in 2009/2010 with "Vienna". A couple more months a new distro will be available, hopefully better than gutsy. I don't see much difference between feisty and gutsy except better organization, but less compatibility with some stuff. My video card is not ggod enough according to Gutsy to run Compiz, but in Feisty it runs flawleslly. Bottom line is? 
Stay with feisty for now while trying out, separately, the new versions. Besides, all the configuration I've had to make to get fesity to my liking was a headache and I wouldn't want to go through it again.

---

### Post by rockin_goliath on 2007-10-30
Don't be afraid to experiment! If you want to actually write the changes to your disk, use Partimage to backup your Ubuntu partition, so that way you can just throw your old partition back on if something goes wrong, and you'll be right back to where you started. Use Bubackup to make a copy of your installation to a loop mounted file system (basically, a virtual hard drive) and try it there. If something goes wrong, just boot into your original installation and delete the Bubackup. Finally, if you have Windows, use Wubi to make a clean install of Gutsy in a loop mounted file system (which will be located on your Windows partition) and try it out there. If something goes wrong, uninstall Wubi in Windows.

---

### Post by misfitpierce on 2007-10-30
I think if you are really worried about upgrading just keep feisty for another 2 months or so and get used to everything then by time you upgrade there should be no problems. Up to you. Upgrade worked fine for me and system is bug free from what I can see.

---

### Post by Hopworks on 2007-10-30
> **Pumalite said:**
> Save /home (including 'Hidden Files') and data to CD's, DVD's or an exteral drive. You can use PartImage.
Thanks for the info. I'll do that. I probably blew it when I started out with 7.04 as far as partitioning, so I didn't partition Feisty to isolate it from other stuff I put on that partition, so copying that partition would take up and cause a lot of wasted space. I might even consider reinstalling and putting that backed up /home folder in there, but then I have a lot of other stuff I set up, like Apache2, php, MySQL, HellaNZB. It might be more complicated than just the /home directory. 

I haven't looked at resizing partitions yet, so re installation might not be necessary to widdle down the size of my install partition.

---

### Post by Hopworks on 2007-10-30
> **rockin_goliath said:**
> Don't be afraid to experiment! If you want to actually write the changes to your disk, use Partimage to backup your Ubuntu partition, so that way you can just throw your old partition back on if something goes wrong, and you'll be right back to where you started. Use Bubackup to make a copy of your installation to a loop mounted file system (basically, a virtual hard drive) and try it there. If something goes wrong, just boot into your original installation and delete the Bubackup. Finally, if you have Windows, use Wubi to make a clean install of Gutsy in a loop mounted file system (which will be located on your Windows partition) and try it out there. If something goes wrong, uninstall Wubi in Windows.
Wow! That's a lot to get my head around! Thanks for the list of things for me to research and try this week! :)

---

### Post by Hopworks on 2007-10-30
> **misfitpierce said:**
> I think if you are really worried about upgrading just keep feisty for another 2 months or so and get used to everything then by time you upgrade there should be no problems. Up to you. Upgrade worked fine for me and system is bug free from what I can see.

There was a lot of good ideas posted for me in this thread, thank you! I'm still thinking INSIDE the Windows box, and not thinking of all the ways I can explore options without hosing my current installation. I do think it would be easier for me just to RMA my VISTA-ONLY MCE remote for a more compatible one, so I can use the IR Blaster at least, and upgrade or at least try out Gusty for more worthy reasons than just getting this proprietary hardware to work. I also decided, since the holiday family computer upgrades will bless me with some surplus hardware (P4 Prescott 3GHz, 2mb ram, ASUS MOBO), I can now build two Linux machines. One for PVR and fun, exploration, and the other as my LAMP server. =)

I might have to dust off my acoustic guitar and get a tin can, and play on my street corner for donations to help pay my power bill though. :shock:

---

### Post by amtnbiker16 on 2007-10-30
if something happens and you have to re-configure anyway, why not just go with a clean install?
or, as aforementioned, you dont really need to upgrade, all it really does is cooperate better with certain hardware and it has some extra features, but if you like visual effects, compiz fusion hasnt frozen up on me yet, which is more than i can say for beryl

if you actually need it for something, go with a clean install.  it's slightly less buggy and it took me less time to configure
of course it seems that you have a lot of things configured right now...way more that i do
eh whatever....

---

### Post by Hopworks on 2007-10-30
> **amtnbiker16 said:**
> if something happens and you have to re-configure anyway, why not just go with a clean install?
or, as aforementioned, you dont really need to upgrade, all it really does is cooperate better with certain hardware and it has some extra features, but if you like visual effects, compiz fusion hasnt frozen up on me yet, which is more than i can say for beryl

if you actually need it for something, go with a clean install.  it's slightly less buggy and it took me less time to configure
of course it seems that you have a lot of things configured right now...way more that i do
eh whatever....

I have to check out this compiz fusiion I guess. When my Linux machine becomes a P4 3GHz Prescott instead of my aging Athlon XP 2600+, I want to really stretch the desktop to unwindows-like limits. OH YEAH!

EDIT. I have a Radeon X1650 512mb agp card in my current windows system, and that will be used in my future Linux upgrade when I build my Core 2 Duo. I'm hoping that will give me enough power to enjoy some nice desktop candy in Ubuntu.

---

