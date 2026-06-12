---
title: "Zorin: shortcuts on desktop"
date: 2013-02-22
forum: Any Other OS
---

### Post by whs37 on 2013-02-22
[SIZE=2]In Zorin, I can create a desktop shortcut like this - with any program:[/SIZE]
 
[[IMG]http://img651.imageshack.us/img651/3941/201302220009.png[/IMG]]("http://imageshack.us/photo/my-images/651/201302220009.png/")
 
[SIZE=2]But if I want to do anything with it, I get this:[/SIZE]
 
[[IMG]http://img35.imageshack.us/img35/7228/201302220010.png[/IMG]]("http://imageshack.us/photo/my-images/35/201302220010.png/")
 
[SIZE=2]What could be the problem.[/SIZE]

---

### Post by QIII on 2013-02-22
Moved to Other OS/Distro Talk.

Zorin is Ubuntu-based, but is a separate distro.

---

### Post by whs37 on 2013-02-22
See, that's what is too confusing for a newbie like me.

---

### Post by MadmanRB on 2013-02-22
I can understand your frustration.
Anyway I have had this issue and the best way to get around it is to right click on the app and hit "properties"
And in the permissions tab make sure the checkbox that says "allow executing file as program" is checked.
I have had nautilus (the file manager in most Gnome based linuxes) give me crap like this once or twice.
Now I am unsure where the issue lays in this case, perhaps its gnomenu (the menu for zorin) to blame here.

*to clairify:
Zorin is based off Ubuntu and it uses nautilus as its file manager (its kind of like windows explorer in well... windows)
Nautilus is not just the file manger for it but also provides your desktop interactivity (such as changing wallpapers and such)
All shortcuts are provided by nautilus but sometimes it goofs for one reason or another.
I am suspecting its gnomenu as I am not facing this issue on my setup (currently using Ubuntu 12.04 LTS)
And its possible the issue is caused by that.
I am unsure, I could test this out myself if this is an issue with it or not.*

*
Issue confirmed indeed, a virtualbox session of zorin tells the tale.
Its not actually an issue with Zorin itself, but the default windows like menu it has does seem to have this issue.
Probably a derp on how its translated as a desktop icon
In any case at least now you have a workaround.

---

### Post by whs37 on 2013-02-22
Thanks buddy. The Properties trick worked. And thank you very much for giving me the extra background info. Every bit helps for an old Windows hand that knows nothing about Linux.
 
I like this Zorin and I do not understand why it does not get a lot more attention. For a Windows guy, that's the easiest to get into tune - a lot easier than vanilla Ubuntu or Mint or any of the other dozen I have tried.
 
Have a look at my little Demo expressing my excitement - and that takes a lot for a 75 year old man.
 
[http://www.sevenforums.com/chillout-room/276418-having-fun-zorin.html#post2275421](http://www.sevenforums.com/chillout-room/276418-having-fun-zorin.html#post2275421)

---

### Post by MadmanRB on 2013-02-22
Zorin is more or less a very tiny distro, it does not have the backing that Ubuntu or Linux mint have.
Ubuntu vanilla might be harder for a windows user because of its approach to things but in reality windows in its pure form is just as hard on the end user as Ubuntu.
And I am not lying, if you dont have some professional handle things Windows is actually harder to set up then Ubuntu could ever hope to be and the only reason why people think its easy as its so wide used and more computers come with it preinsalled with some bells and whistles added in by the manufacturer.
But install a barebones Windows OS from one of the non OEM vendors and issues will crop up all over the place.
Windows by default doesnt offer codecs out of the box and would have to be installed separately.
As would drivers and believe it or not, Linux is actually kind of better in detecting hardware sometimes.
Of course this is not all the time but it does happen from this users perspective.
Ubuntu only looks hard to the windows user because the windows user is not used to installing things like codecs.
Ubuntu has its reasoning for not handling codecs and by the same laws neither windows can come with codecs pre packaged.

Also I am a little surprised that you said Mint is hard to use (well not in a direct way)
After all Linux mint does offer a UI that is very much like the old XP, the layout is virtually identical.

---

### Post by whs37 on 2013-02-25
Hi, Sorry I did not get back earlier. But the answers do not show up in my User CP on this forum. Only after I looked at my posting history could I find your answer.
 
Anyhow, the last 2 days I was busy with Mint Cinnamon and Mint Mate. Both were very frustrating because I was unable to install the VMware Player Tools. I tried many different versions on both systems with no luck. Even got some help from nice people at the Linux Forum. But all was in vain. And without the tools, it is inconvenient to run a system as a guest.
 
I had none of those problems with Zorin and Ubuntu. The tools installed on the first attempt.
 
Zorin is a well established system for me now and I use it quite a bit because it is so fast. Ubuntu is another matter. What a mess with this Unity UI. I can't even find Preferences or Administration and the Terminal I only get with CTL+ALT+T. One of the members here said that Ubuntu is for masochists and recommended Xubuntu. I tend to believe him.

---

### Post by MadmanRB on 2013-02-26
Personally I dont find unity that hard to use, its just different from windows.
I mean I understand its frustrating to use something that doesnt look andc feel like windows but all things have a learning curve including windows.
I am sure if you remember when the first time you used windows it was a bit rough around the edges.
Preferences in Unity could easily be found in the cog menu.
As for administration what kind of administration are we talking about here?
Package management?
root nautilus?
Huh?

As for VMware yeah its a bit rough to set up if you dont know what you are doing.

---

### Post by whs37 on 2013-02-26
It's not because it is different. I have been an operating system developer for 35 years and have no trouble adapting to different systems. Never had real problems with the old Ubuntu. But I think that this Unity is a mess.
 
No problems with VMware either. I even wrote tutorials about it.
 
[http://www.sevenforums.com/tutorials/278957-vmware-player-install-setup-zorin.html](http://www.sevenforums.com/tutorials/278957-vmware-player-install-setup-zorin.html)
 
[http://www.eightforums.com/tutorials/19657-vmware-player-share-partitions-between-host-guest.html](http://www.eightforums.com/tutorials/19657-vmware-player-share-partitions-between-host-guest.html)

---

### Post by Redalien0304 on 2013-02-26
nice posting on Zorin OS trying get my brother on Ubuntu. he has tried Kbuntu, Ubuntu, but Ultimately has problems, not Intuitive enough. he is so used to windows OS. has a hard time learning new stuff (memory problems) but he wants to run Linux/Ubuntu. so i have slowly been steering towards him Zorin Os cause of it is windows familiarity. he also wants Netflix native to Linux but thats another whole issue. besides he has Roku Device & Nexus 7 Tablet.

---

### Post by whs37 on 2013-02-26
I think your brother might do well with Zorin. I do not like the new Ubuntu Unity UI. I would not use it.

---

### Post by Redalien0304 on 2013-02-27
yep. for myself i use Ubuntu 12.04 Cinnamon Desktop. Dont like the Unity thing either.

---

