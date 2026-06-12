---
title: "'The folder contents could not be displayed'"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by rojodojo on 2007-10-26
Hello,
I recently installed gutsy a week ago, and I seem to have run into a problem. I am not connected to any network; however, after a few hours of use, I get the message: "The folder contents could not be displayed" when I try to access ANY folder whether it be the home folder, desktop folder, etc. Still, I am able to access the files if I open them via a program(eg.movie maker to open a movie file in the home folder). Also, my desktop icons completely disappear and the log off/switch user/power down icon gets delayed. After a reboot, everything is fine again.

Is there a cause or cure to this problem?

---

### Post by MegaJim on 2007-10-26
I sometimes get this sort of behaviour, it happens when gnome is stuck trying to access a non-existent network.

rather than rebooting you can save your work and restart the X server using Ctrl+Alt+Backspace and login again.

---

### Post by allengroove on 2007-10-29
I get this problem daily since i've installed gusty, and i'm sorry to say but i'm a little dissapointed about gusty because this is not the only bug i've encountered. The 'log on' screen doesn't match the screen resolution, the search function of nautilus doesn't work anymore, and the most annoying thing is this problem with 'the folder content can not be displayed' wich i get daily after half hour of functioning, all icons dissapear and i can not acces any folder until i restart x. I also had some problems with compiz at the begining (beryl worked much better, and was much better pre-configured, compiz still seems like beta version compared to beryl, but that is just my opinion). When i first had installed Tribe 3, i really liked how gusty was working, after that i've installed back feisty and i was absolutely happy with it while i was waiting for gusty, but when it came out the first impression was that feisty seemed to be more stable and bug free. Again, i'm really sorry that i had to bring all this up, cause in the last 5 months i've become a real ubuntu fan and i'm using it full time and i'd really like it to work and i'm also tired of daily Ctrl+Alt+Backspace. :-x Also, sorry if my english is not allways verry good! :(

---

### Post by h3_ on 2007-11-11
Have the same problem here, I ran Gutsy development version for a while and I never had this problem until the last update.

Now it happens on a regular basis, I couldn't pin point anything special that could trigger it. I don't have network shares, I have only one computer on this network.

Oh, in fact I just recall that most of the time it happens when I copy||cut/paste a mp3 file from a folder to another.  I get a first error that says "cannot copy file, to many files opened", then I close nautilus and reopen one, then I get the "The folder contents could not be displayed" error.

I agree that I have often MANY files/folder opened at the same time, but I honestly think that it should take a bit more to bring a 64bit dual core with 2gb of ram tom his knees.

Will try to find a way to reproduce it..

---

### Post by growingneeds on 2007-11-16
I too face this problem. I recall having none of these issues in Feisty. But ever since the upgrade to Gutsy, I've had many problems:
[LIST=1]
[*]Linksys Wireless-G USB Network Adapter ver. 4 malfunctioned
[*]Unclear instructions to Compiz-Fusion setup (ATI graphics card)
[*]Latest OpenOffice is horrendously slow (debian install of 2.3 is faster; both JRE disabled)
[*]Latest Firefox update unacceptably slow. (It's not an IPv6 issue, trust me.)
[*]Nautilus refuses to open folders and mp3s after use and organizing for a couple of minutes (my local HDD).
[/LIST]
I've managed to solve issues 1 & 2. Partially solved 3 cause the debian install of OOo 2.3 sped things up slightly (slow compared to OOo 2.3 on WinXP). I'm losing patience on 4 and 5. I was really happy with Feisty and recall telling everyone I know about the upcoming release (Gutsy). But now, I have my hands full trying to troubleshoot these issues. I have the urge to fall back on Feisty. But, eventually I might unknowingly install an update and  these problems would return. It's really vexing. Is anyone using Gutsy on a Pentium motherboard and having these problems too? I suspect it is some sort of a memory leak (RAM) but I haven't a clue how to solve this. Perhaps I should give other distros a try. Fedora Core? Shudder.

Believe me. When Firefox churns out my typing slower than a snail, there is no longer any joy in typing. It's arduous. (Feels like Sandisk's new product Sansa View. That's another story to tell. I'm going with iPod for now.) I am returning to my Windows XP. At least, it functions as expected.

---

### Post by bumanie on 2007-11-16
> **growingneeds said:**
> I too face this problem. I recall having none of these issues in Feisty. But ever since the upgrade to Gutsy, I've had many problems:
[LIST=1]
[*]Linksys Wireless-G USB Network Adapter ver. 4 malfunctioned
[*]Unclear instructions to Compiz-Fusion setup (ATI graphics card)
[*]Latest OpenOffice is horrendously slow (debian install of 2.3 is faster; both JRE disabled)
[*]Latest Firefox update unacceptably slow. (It's not an IPv6 issue, trust me.)
[*]Nautilus refuses to open folders and mp3s after use and organizing for a couple of minutes (my local HDD).
[/LIST]
I've managed to solve issues 1 & 2. Partially solved 3 cause the debian install of OOo 2.3 sped things up slightly (slow compared to OOo 2.3 on WinXP). I'm losing patience on 4 and 5. I was really happy with Feisty and recall telling everyone I know about the upcoming release (Gutsy). But now, I have my hands full trying to troubleshoot these issues. I have the urge to fall back on Feisty. But, eventually I might unknowingly install an update and  these problems would return. It's really vexing. Is anyone using Gutsy on a Pentium motherboard and having these problems too? I suspect it is some sort of a memory leak (RAM) but I haven't a clue how to solve this. Perhaps I should give other distros a try. Fedora Core? Shudder.

Believe me. When Firefox churns out my typing slower than a snail, there is no longer any joy in typing. It's arduous. (Feels like Sandisk's new product Sansa View. That's another story to tell. I'm going with iPod for now.) I am returning to my Windows XP. At least, it functions as expected.
 If feisty did all you need, why don't you return to that, instead of lining Bill's pockets???

---

### Post by growingneeds on 2007-11-17
So true, mate. I guess I have no choice but to format away Gutsy. This time, I'll install Feisty and instruct the update manager to ignore all updates, except those pertaining to security. I just learnt how to install OOo 2.3 via the native debian package. I guess this skill is rather vital. Nonetheless, I hope Ubuntu can get better. Sigh. Now to back up all my files again. Not sure if I can take such hard knocks. Was reading about Damn Small Linux last night. Wondering if I should give that a go, since it's Debian and customizable and all. Just got my copy of Fedora 7 from the school library. But, I know nuts about rpm. *ponder ponder*

Please, Mr Shuttleworth, if you see this... Something has to be done about the stability of the distro. I love Ubuntu, I really do.

---

### Post by allengroove on 2007-11-18
Since my last post i've reinstalled Gutsy but the problem it's still there. The only thing i've managed to find out is that the problem is indeed related to manipulating media files like wav's and mp3's. As a music producer i work a lot with media files like wav's and mp3's and every time i do i get this problem. After a few minutes of opening media files i get the same message: 'folder content could not be displayed'. Also, after this new install of gutsy a new problem appeared - sometimes when i start ubuntu the screen resolution is changed. Before reinstalling Gutsy only the log on screen had a different resolution, and this made me to allow automatic login for my user but now from time to time even the workspace resolution is not the one i've chossen. May all this problems be somehow related to video drivers or x?

---

### Post by philinux on 2007-11-18
In nautilus preference change from list view to icon view.

---

### Post by MegaJim on 2007-11-18
> **philinux said:**
> In nautilus preference change from list view to icon view.

Is this a confirmed bug/rumour/superstition ?

---

### Post by Anthony M on 2007-11-18
When you get the problem, in a terminal type:

```
killall nautilus
```

This will restart nautilus and will allow you to access your files without having to log off and everything.

---

### Post by philinux on 2007-11-18
> **MegaJim said:**
> Is this a confirmed bug/rumour/superstition ?


I've seen posts where a folder is full of mp3 files,i.e. lots, with list view locking up nautilus. Icon view apparently has no problems

---

### Post by bribri124 on 2007-11-19
> **philinux said:**
> I've seen posts where a folder is full of mp3 files,i.e. lots, with list view locking up nautilus. Icon view apparently has no problems

I have many folders with mp3's, all of which are in icon view, and I have been having this problem since Gutsy came out.  I don't think the view has anything to do with this issue.

---

### Post by growingneeds on 2007-11-20
Yes, agreed. My nautilus freezes up in icon view. The way in which the files are viewed isn't an issue here. It freezes up after some time: More often when music files are renamed or relocated. Restarting the X system or Nautilus itself helps. But that doesn't solve the problem. Does anyone else experience an incredibly slow firefox and OpenOffice.org in Gutsy?

---

### Post by hellonull on 2007-11-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/163095](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/163095) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Anthony M said:**
> When you get the problem, in a terminal type:

```
killall nautilus
```

This will restart nautilus and will allow you to access your files without having to log off and everything.

I just experienced this issue and came across this thread after a quick Google search. I too was manipulating/tagging MP3 files (using foobar2000 under Wine) when I encountered the problem. Also had Amarok open and playing some MP3s. Though it is not a permanent fix, the above solution is the one that works for me since I don't encounter this problem on a regular basis.

---

### Post by proalan on 2007-11-27
Such a strange problem, i also seem to encounter this problem when transferring music from and to my mp3 player.

Its starting to occur so frequently I've switched to KDE for the time being.

---

### Post by pdadad on 2007-11-29
> **growingneeds said:**
> ...
[*]Latest OpenOffice is horrendously slow (debian install of 2.3 is faster; both JRE disabled)
...

*********************

OOo works well for me when I set the following: 
Tools -> Options -> Memory -> In the 5 boxes use the values 30, 128, 20.0, 00:10, and 20. Check the box for "Enable systray quick starter".

---

### Post by vanadium on 2007-12-02
Strange indeed that what seems to be mayor bugs continue to exist in an application that is already around for quite some time. I also experience this issue. What I tried was turning off the "Sound preview" option  (Edit - Preferences - Preview tab). In fact, I was searching now for another quirk: the Search function that does not seem to wrok at all.

---

### Post by growingneeds on 2007-12-08
I am happy to report that my system is back online. OOo, Firefox are running at top speed. I even had the JRE enabled in OOo. The Linksys wireless adapter works without much configuration! (I just had to disable roaming, and key in my SSID i and password manually. Worked like a charm.) Nautilus seems fine for now, though I wouldn't be too surprised if it tried to hang on me whilst dealing with mp3s again. But, I'll take my chances. And here's what I did:

1. I used the Windows XP installation CD and deleted my Ubuntu partitions, including the swap. (All non-NTFS partitions)
2. Did a reinstallationof Ubuntu Feisty Fawn.
3. Instructed Synaptic Update Manager to download only the Security Updates. This prevented the system from upgrading to Gutsy. But I could theoretically still keep my system security up to date.

I ran into an issue, though. The index repository for Fesity Security wouldn't update itself. Not from the Main Server, not from the Singapore Server (I'm from Singapore.) Not even from the best server that Ubuntu picked itself (It ran a series of pings across its entire list of mirrors). Finally I got it to update selecting the Australian server : "http://ftp.iinet.net.au/pub/ubuntu". There were nearly 200 updates, amounting to 180+MB worth of data.

It was worth the wait as the system downloaded the security updates. I had to reboot as the updates involved a kernel change. I shall have to reinstall my codecs, VLC, aMSN and gtkpod. I love Ubuntu. But my love remains with Feisty. Ha.

---

### Post by gilf on 2007-12-18
I'm going to make a totally unsubstantiated suggestion:

The problem seems to affect large files after manipulation. I'm wondering if it's a disk fragmentation problem with large files locating all over the disk. If the system is timing out when trying to display folder contents. Symptons would be exaggerated in a drive with smaller amounts of free space which had a lot of use. Problem would be least apparent on re-installation where the files were newly laid down and relatively unfragmented. The problem might be more apparent in certain filesystems than others (vfat,ntfs,ext3,reiserfs, etc).

If some focus could be put on what the details of the partition are (age, system type, etc) there might be a correlation with some of these factors.

Just a thought.

---

### Post by vanadium on 2007-12-18
I confirm that the problem is related to the sound preview function. The problem disappears when you disable sound preview: in a nautilus window: turning of "Preview sounds" in Edit - Preferences - Preview tab: set "Preview sound files" to "Never".

---

### Post by gilf on 2007-12-18
Makes sense. Good work!

---

### Post by growingneeds on 2007-12-24
I'd like to report that in Feisty Fawn, after manipulating with sound files, the icon of the files changes sporadically in the way Nautilus does in Gutsy. But after the brief change, it reverts back to the original sound icon. I can still play the file after the revert. If what "vanadium" claims is true, that would imply the sound preview function is broken in Gutsy, but more resilient in Feisty.

---

### Post by Dekadence on 2007-12-25
> **vanadium said:**
> I confirm that the problem is related to the sound preview function. The problem disappears when you disable sound preview: in a nautilus window: turning of "Preview sounds" in Edit - Preferences - Preview tab: set "Preview sound files" to "Never".

Thanks alot mate! I've been searching for a solution like that for a long time :)

---

### Post by vanadium on 2007-12-27
It is not a solution. It is a workaround.

---

### Post by spaceboy909 on 2007-12-28
This problem has started showing up on me recently, averaging about once per day.  It is usually when I'm accessing A/V folder/files.

Normally, nautilus will shut itself down after a few tries and restart, but this last time it just died.

I tried the killall nautilus solution posted earlier and that worked good.  I also turned off the sound preview.  I'll post back in about a week and report on that.

---

### Post by armymil on 2008-01-01
> **Anthony M said:**
> When you get the problem, in a terminal type:

```
killall nautilus
```

This will restart nautilus and will allow you to access your files without having to log off and everything.

This worked for me. I will reread over the thread to find if there were any more fixes. Thanks a bunch guy!

---

### Post by yabbadabbadont on 2008-01-31
This must be an upstream bug as the same thing happens to me on Gentoo.  In my case, I have all previews disabled except for image thumbnails.  I have a very large wallpaper collection and while browsing through it I noticed that my system had started using swap.  (swap is on a different drive and I could hear it when it started being used)  I discovered that nautilus was eating up memory every time it had to generate new thumbnail images.  It doesn't seem to do it when it loads existing thumbnails, just when it is first generating them.

EDIT: I spoke too soon.  It allocates memory for displaying the existing thumbnails and never releases it until nautilus is killed.  I've worked around this by changing the gconf settings so that nautilus is not used to draw the desktop, nor to display the wallpaper.  It still eats up memory while I'm browsing images, but I get it back when I close nautilus now.  By the way, there is an open, unconfirmed, bug on this at the gnome bugzilla from quite a while ago.

---

### Post by crazypiglady on 2008-02-15
I use amarok to listen to music (ogg and mp3) at home. I rarely need to view these files and rarely add them although I occasionally back them up to an external drive. I've recently been getting this problem (possibly since my last backup) using gutsy. amarok can not see all of these files (“local file does not exist”) but strangely sees some of them - the number of files it can see varies. A restart does work but, after some time (time rather than usage – it eventually happens even if I don't use the computer), the problem returns. when this problem happens, I instinctively look around my music drive to see if it actually is there and usually find I'm locked out. it is only at this point that I use nautilus and actively view files (although amarok presumably does). my point here is that it is not specifically a “viewing in nautilus” problem. If I kill nautilus then it works but I have to rescan my entire music collection in amarok which takes a while and re-orders them. yes, its a 'workaround'. Is there a fix? This thread went quiet. did i miss something?

---

### Post by yabbadabbadont on 2008-02-15
It's an upstream bug.  Someone needs to light a fire under the Gnome devs.  :D

---

### Post by crazypiglady on 2008-03-02
Actually my problem got worse and so I looked around to investigate. my hard drive was crumbling. bit by bit. the symptoms were as above but I seem to have been suffering from a different problem to other posters. I've changed my drive and .. hmm well. it seems to be ok for now. hope it all works out. maybe its possible that this is the problem of someone else who stumbles upon this thread. thanks for the help. its all educational even if not directly related. cheers.

---

