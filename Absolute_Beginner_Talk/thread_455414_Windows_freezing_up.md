---
title: "Windows freezing up"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Dennis56 on 2007-05-26
Every time I click on System>Administrator>Network or System>Administrator>Users after I click a button it freezes and when I try to open the window again it freezes up withought me pressing anything It doesn't even show the content. I have 7.04. Did I install it wrong? What can I do to fix this?

Thanks in advance,
Dennis

---

### Post by Dennis56 on 2007-05-26
Someone, please?

---

### Post by starcraft.man on 2007-05-26
> **Dennis56 said:**
> Someone, please?

I have never heard of this problem. Can't offer any advice. What is your hardware specs? Do you have a minimum of 256 ram? I can't think of any reason why it would freeze on those two menus in the GUI. If you do have at least 256/512 ram, then I guess reinstall. I don't know what else to say... unless Aysiu poinces in and knows. :)

---

### Post by Dennis56 on 2007-05-26
I have 1 gig of RAM and it's the only window open.

---

### Post by starcraft.man on 2007-05-26
> **Dennis56 said:**
> I have 1 gig of RAM and it's the only window open.

Thats more than enough, something must have gone bad with your install. I'd reinstall it manually. The quickest way to solve unknown and new issues. If it appears after you reinstall, I am perplexed >.>.

---

### Post by Dennis56 on 2007-05-26
> **starcraft.man said:**
> Thats more than enough, something must have gone bad with your install. I'd reinstall it manually. The quickest way to solve unknown and new issues. If it appears after you reinstall, I am perplexed >.>.

Thanks for the help I appreciate it.

I'm in the process of burning it onto a cd and hopefully the install will work this time.

---

### Post by djchandler on 2007-05-26
**[SIZE="5"]DISASTER WARNING![/SIZE]**

Do not try to duplicate this problem. I'm hoping one or both of us just did something goofy, and it's not an OS bug.

I read Dennis56's leading post in this thread and managed to exactly duplicate the problem. My network settings and users/groups carried through as I progressed from Dapper, where I had originally installed Ubuntu as the ONLY OS on this system. Configurations to network and users/group had not been accessed after upgrading to Edgy and Feisty. What Dennis56 described happened to me as well, just after I had entered my sudo password. I am running on spare hardware, a P3 with 512 mb ram and Nvidia TNT2 with 32 mb. We may have found a bug. I hope not.

I'm a tinkerer by nature, and, against all advice, had set up a root account and password so I could fool around with fonts easier. I work in graphic design and have quite a collection of high quality fonts I wanted available, and do not care whether or not I have non-Latin fonts available. I know better than to set up a root account now in Ubuntu, and will not do it again. What finally happened is when I tried to log-in as root, things went wonky. My root password was accepted, and the system got to the point just before the Ubuntu banner comes up just before drawing the desktop. It hung there for over an hour, so I pushed the hardware reset button. **DISASTER WARNING!** Boot up now freezes before getting to log-in screen. I get to where my monitor goes to default resolution, (I have a very informative monitor, it puts up a quick message every time I switch graphics modes, resolutions, or inputs) but stays black with the busy icon spinning until infinity if I let it. So my system will not boot and I have had no success running repair from the alternate CD.That's what I get for being such a wise guy. I'm going to re-install from scratch. I've been thinking of going to Xubuntu anyway on this underpowered box. I'm happy with Gnome 2.18, but I'm going to do something different just because I can. I'm going to lose a little bit of stuff, but nothing truly important. It's just going to be a while before I get that P3 running again. It's a good thing we are on a holiday weekend in the USA.:redface:

---

### Post by Dennis56 on 2007-05-27
I haven't done anything like you have I've been using Ubuntu for 1 day. I guess we really have found a bug, the problem is I cannot access the User/Group admin menu and change the root password to a password I know so I can access SU via terminal.

---

### Post by djchandler on 2007-05-27
> **Dennis56 said:**
> I haven't done anything like you have I've been using Ubuntu for 1 day. I guess we really have found a bug, the problem is I cannot access the User/Group admin menu and change the root password to a password I know so I can access SU via terminal.

Dennis,

I'm back up with Xubuntu. Whatever you do, don't activate the root account. You should be able to access sudo just by entering the password for the first account you set up while installing Ubuntu. I don't know what either of us did, but I'm going to edit my *.conf files using text editor- better than getting an un-bootable box. I was able to save all pertinent data because the Xubuntu installer was aware it was there, and didn't want to use the part of the hd that was already occupied. I was able to get root on the install cd environment, and copied the data to a spare hd I had laying around. Since I'd already backed up my data elsewhere, I had to power down and re-boot with DBAN to wipe the hd I wanted to install to so it would use the whole thing. The Xubuntu installer is very smart; a good thing if you want to dual-boot.

I don't know what to tell you at this point but to edit those .conf files by hand until someone else figures this out. I was able to salvage my old .conf files for samba and x11, but didn't worry about the users/groups because I'm the only one using this thing, and I'm not sure what I want to do about Samba yet. Maybe we'll have an answer soon. In the meantime, I guess I'll do the bugzilla thing or what ever it takes.

All the best,
djc

---

### Post by Albi on 2007-05-27
It's very possible that you have a bad installation.  Do an MD5sum of the CD you used to install and check CD for defects.

I had a similar problem with Knoppix a while back, it would freeze whenever I opened a menu and this was the problem.

---

### Post by djchandler on 2007-05-27
I updated to Feisty using update-manager. You can bet I used MD5 when I dowloaded the Xubuntu Feisty install cd today. I'm up now with Xubuntu Feisty. I think the originator of this thread, Dennis56, says he installed from scratch on CD. Sounds like a bug to me. Just tried to report at Launchpad and got timed out.

Regards,
DJChandler

---

### Post by djchandler on 2007-05-28
> **Albi said:**
> It's very possible that you have a bad installation.  Do an MD5sum of the CD you used to install and check CD for defects.

I had a similar problem with Knoppix a while back, it would freeze whenever I opened a menu and this was the problem.

Well, I've got to say XFCE just does not measure up. So I ran MD5 on the regular Feisty Ubuntu install CD and did a clean install. I am back to Gnome 2.18 and Metacity. But I'm still not going to try to do what Dennis56 and I did before to make those screens freeze. Hand editing is the way to go for .conf files for the time being. I tried to file a bug report at Launchpad, but I just don't understand how they are handling things. I had no idea how to fill in the "package" and "project" fields. I hate cross-posting, but I'm going to look for a thread in the Forums here to see if I can figure this out. I finally gave up using the form and sent an email to [email]feedback@launchpad.net[/email]. It could very well be I am just not thinking clearly. I have been using pain medication, i.e., narcotics for a complex medical situation. Let it suffice to say that it could just be me. Anybody else want to try to report this bug?

---

### Post by djchandler on 2007-05-28
There seems to be a limit on how many administrative tasks you can perform before you run into the frozen window syndrome. I can't figure it out, nor can I say how many such tasks it takes. One thing I have found out for sure. If you get a message in a dialog that the system needs re-booting, pay attention, and click that button that says "restart." Ignoring it will cause an immediate crash in Feisty. I'm beginning to think that Canonical went to such extremes to make sure Feisty ran on the Dells, that it is costing some of us the stability we had in previous versions. If the new Dells are behaving like my computer is, Canonical is in trouble.

My advice is that if you are not running a computer less than a year or so old in terms of ANY of its hardware, avoid using some of the new bells and whistles. It is too bad XFCE looks so bad in Xubuntu compared to Gnome 2.18 in Ubuntu. I would have liked to reduce the load on this old cpu, but XFCE was just too hard on my eyes. Fonts looked terrible, there was ghosting due to inadequate screen redraws. I should probably put this little rant in another thread.

So caution to you new Ubuntu users trying to make use of older hardware. Stay away from unnecessary power management, and stick with the graphics drivers that load during installation. Don't tweak too much. Plain vanilla in a cup is better than a bananna split on the ground.

If you really want to use Ubuntu and make a commitment, go buy a Dell. Something tells me they are solid performers. The only caveat I can see is that you should spend the extra bucks for the base model that includes the NVidia PCIe 7300 chip set graphics card, and upgrade the ram, graphics card, and storage if you can afford it.

---

