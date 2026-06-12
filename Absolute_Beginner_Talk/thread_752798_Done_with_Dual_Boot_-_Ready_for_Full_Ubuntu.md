---
title: "Done with Dual Boot - Ready for Full Ubuntu"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Nodestar on 2008-04-12
I've been dual booting XP and Ubuntu 7.10 for a couple weeks now and I'm ready to go all Ubuntu. I've got a couple questions.

First I don't know how to do this. Or the best method of doing this if there is more than one way to do it. Also I don't mind losing all of my Current Ubuntu settings.

I'm also not fully aware of how the Ubuntu filing system works yet. (But I am learning and reading as many tuturials as I can find. ) So I don't know what will happen to my none Windows files when I make the switch.. like most of the applications in Program Files such as MS Office and Games and Codecs and what not. I would like all these things to disapear since I won't be useing most of these applications on Ubuntu anyway. 

I'm just afraid of going full ubuntu and having all these left over XP based applications hanging around. 

Any help would be great. Or if this has already been discussed in detail please post a link. I could not find anything.

---

### Post by Gulyan on 2008-04-12
There shouldn't be much difference between instaling ubuntu alone and dual booting.
Did you install ubuntu from xp (with wubi)?

If so, to install ubuntu alone just boot from the live cd and you'll see an icon there "install". Double click it and follow the instructions. :popcorn:

---

### Post by Master Yami on 2008-04-12
If you truly aren't afraid of losing anything, or have stuff copied to an external drive, just re-run the install and pick the option to use the entire disk. You will lose your configuration, heck, you will lose absolutely everything on your computer, but you will have only Ubuntu as a result.

I hope you have a Windows install disc if you ever want it again, because there is no other way to recover it afterward.

There is a way to do it without re-installing Ubuntu, but its much more complicated.

---

### Post by thisiam on 2008-04-12
if you save your home folder you can just replace it with the one that you get with the new install and it will be like you never left.

---

### Post by Nodestar on 2008-04-12
OK. Maybee my initial ideas of what Ubuntu did during installs was a little off. You said "you will lose absolutely everything on your computer".

I didn't know Ubuntu did a full format. I thought it only replaced windows. Does this mean that by installing ubuntu to the entire disk that I will lose Dell Drivers, ATI, etc. If so does it even matter?

---

### Post by thisiam on 2008-04-12
I would back them up and keep them for a rainy day and if you don't want to do a full format you could use gparted and delete the ntfs partition and add it to the ext3 partition and edit grub to delete windoze.
couldn't tell you exactly what you would have to edit in grub but i'm sure its here somewhere.

---

### Post by jcwmoore on 2008-04-12
> **Master Yami said:**
> I hope you have a Windows install disc if you ever want it again, because there is no other way to recover it afterward.

agree, in fact if you don't have a windows disk then i would recommend you not kill windows.  I managed to get a windows disk, so i only run ubuntu.  I use a windows VM on virtual box, the ubuntu + windows VM is perfect for me.  I have found that there are just some things in life you will need windows for:(

---

### Post by Master Yami on 2008-04-12
> **Nodestar said:**
> OK. Maybee my initial ideas of what Ubuntu did during installs was a little off. You said "you will lose absolutely everything on your computer".

I didn't know Ubuntu did a full format. I thought it only replaced windows. Does this mean that by installing ubuntu to the entire disk that I will lose Dell Drivers, ATI, etc. If so does it even matter?

Windows drivers don't work in Linux. Linux uses its own drivers to do things. When you ran Linux, the Windows drivers don't do anything but run devices in Windows. Linux used its own. So don't worry - everything should still work fine. You lose the Windows drivers, but that does not matter.

I assume that everything simply worked for you in Linux then. Otherwise you would have noticed something not working. Means switching makes even more sense.

Plus the guy 2 posts above mentioned the more complicated method I was talking about. If you want to do that it would avoid a reinstall, but pretty much have the same effect windows-wise.

---

### Post by Master Yami on 2008-04-12
> **jcwmoore said:**
> I have found that there are just some things in life you will need windows for:(

True, my main comp runs windows, but I hardly use it now. Even though its my best computer. Gaming keeps Windows alive for me.

EDIT: Why did I make a second post for that? Stupid...

---

### Post by mrgnash on 2008-04-12
I'm sorta in the same position. I know how to use gparted to delete the NTFS partition, but how does one then add the free space to say, my ext3 /home partition?

---

### Post by Nodestar on 2008-04-12
Thanks for the help guys that clears up alot.

My main problem now is this. I'm running off of a 20 gig hardrive from my Latitude D600 Dell Laptop. I would'nt mind keeping windows around with the duel boot but I'm running out of space. Also I am not my computers original owner so their are random things and files on this machine that are above my techinical knowledge. Alot of buisness programs that are not easly reconizeable or that are lost deep in files I don't understand. That just can't be uninstalled. 

I don't have a Windows disc. Thats why formatting with Ubuntu looks like a great idea. Should I try and get a copy of Windows? Or will I need a Dell Reboot disc. (not sure the name) 

Should my solution be to get a disc. Format and reinstal a clean(er) Windows. Then dual boot with Ubuntu?

It almost doesn't seem like it's worth the trouble. Although I do agree that I'll probly we needing Windows for somthing in a month or two.

---

### Post by Master Yami on 2008-04-12
> **mrgnash said:**
> I'm sorta in the same position. I know how to use gparted to delete the NTFS partition, but how does one then add the free space to say, my ext3 /home partition?

Right-click on the partition to extend, and extend it to the free space you made.

I don't know how extend to free space that isn't directly preceding or following though. Is it possible?

---

### Post by Master Yami on 2008-04-12
> **Nodestar said:**
> Thanks for the help guys that clears up alot.

My main problem now is this. I'm running off of a 20 gig hardrive from my Latitude D600 Dell Laptop. I would'nt mind keeping windows around with the duel boot but I'm running out of space. Also I am not my computers original owner so their are random things and files on this machine that are above my techinical knowledge. Alot of buisness programs that are not easly reconizeable or that are lost deep in files I don't understand. That just can't be uninstalled. 

I don't have a Windows disc. Thats why formatting with Ubuntu looks like a great idea. Should I try and get a copy of Windows? Or will I need a Dell Reboot disc. (not sure the name) 

Should my solution be to get a disc. Format and reinstal a clean(er) Windows. Then dual boot with Ubuntu?

It almost doesn't seem like it's worth the trouble. Although I do agree that I'll probly we needing Windows for somthing in a month or two.

If you will be needing Windows but don't have an install disc then I'd keep windows and continue to dual boot. If you insist on removing it you could use Wine to run the Windows app or find an open-source implementation of it. I wouldn't buy Windows, or remove Windows simply to clear the apps (the prior owner should have done this - tsk, tsk, prior owner - he should have given it Windows disc too, I think all Dells come with one)

Why can't you un-install those Windows apps, anyway? They should have un-installers somewhere. But if you need windows (why, though? Tell me.), removing it without being able to re-install sounds like a bad idea.

---

### Post by Nodestar on 2008-04-12
I've got apps just randomly everywhere on my PC. And I've got random files as well. For instance directly on the C drive I have a DELL folder and Dell(2) folder an OEMSETTINGS Folder a MSIR20 Folder and a 1386 Folder that has tons of stuff in it. Also directly on the C drive are random files like CTX.DAT , DELL.SDR. The list goes on and on. I'm sure some of these files are suppose to be there. But alot are just random. And there are even more just stuck in weird spots like this. 

I don't know that I need windows. As of right now I don't need it at all. But it will probly come up in the future. As of right now I've found every program I use now for Linux. Minus games of course. Which is not a big deal to me.

---

### Post by Tews on 2008-04-12
> **Nodestar said:**
> I've been dual booting XP and Ubuntu 7.10 for a couple weeks now and I'm ready to go all Ubuntu. I've got a couple questions.

First I don't know how to do this. Or the best method of doing this if there is more than one way to do it. Also I don't mind losing all of my Current Ubuntu settings.



There's no reason to lose **any** of your current Ubuntu settings or files!  There is a now a program that will backup and restore your current system called Quick-Start.  This little app was developed with Ubuntu in mind.  Your situation is exactly why Quick-Start was created.


[IMG]http://www.libertymanor.org/menu.png[/IMG]

As you can see you have a lot of options.  

Check it out here ==>>  [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by Master Yami on 2008-04-12
> **Nodestar said:**
> I've got apps just randomly everywhere on my PC. And I've got random files as well. For instance directly on the C drive I have a DELL folder and Dell(2) folder an OEMSETTINGS Folder a MSIR20 Folder and a 1386 Folder that has tons of stuff in it. Also directly on the C drive are random files like CTX.DAT , DELL.SDR. The list goes on and on. I'm sure some of these files are suppose to be there. But alot are just random. And there are even more just stuck in weird spots like this. 

I don't know that I need windows. As of right now I don't need it at all. But it will probly come up in the future. As of right now I've found every program I use now for Linux. Minus games of course. Which is not a big deal to me.

Those apps and files you specifically mentioned are just bundled crap, which unfortunately, aren't random and should be left alone if you keep Windows(I'm sure some can go, but sadly theres no way for me to figure that out). So the prior owner is innocent after all. If you go Linux however the are expendable.

Games can be run in Wine half the time, so that's no issue.

So I guess you might be able to take the plunge if you are sure you won't be needing Windows. But it looks like you aren't. I honestly don't see why you would be needing Windows, however. Think of what it is you might be needing it for. If you can't honestly think of anything, I doubt anything will come up.

> **Tews said:**
> There's no reason to lose **any** of your current Ubuntu settings or files! There is a now a program that will backup and restore your current system called Quick-Start. This little app was developed with Ubuntu in mind. Your situation is exactly why Quick-Start was created.

Damn I wish I'd known about that a while ago. Would've been handy for me!

---

### Post by Nodestar on 2008-04-12
Where it says Clone your MS Windows Installation. What does that mean exactly?

I'm reading about Quick-Start now. But basically it will allow me to back up windows and then erase it with full Ubuntu with the option to bring it back later?? Not sure If I'm really grasping the full purpose of this program. Please explain more if you can.

---

### Post by Tews on 2008-04-12
> **Nodestar said:**
> Where it says Clone your MS Windows Installation. What does that mean exactly?

I'm reading about Quick-Start now. But basically it will allow me to back up windows and then erase it with full Ubuntu with the option to bring it back later?? Not sure If I'm really grasping the full purpose of this program. Please explain more if you can.

Quick=Start will make an "image" of your Windows <spit> partition and save it to any folder that you specify.  Its purpose is for dual booters so you wouldn't want to erase your Windows <spit> partition, cause you couldn't restore it without the NTFS partition.

---

