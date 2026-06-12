---
title: "FolderShare for ubuntu?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by BradDet on 2007-06-04
Hello,

Today is Day 3 of my migration from my HP Windows Media Center PC to Ubuntu. I have been very impressed by it, I have succesfully migrated all of my media tools over to ubuntu, including MythTV which seems to be working very well using my TV as a secondary display.

On XP I used a program called "FolderShare", which I believe orginally had a linux flavor, but since M$ bought the company I can no longer find it.

I used FolderShare to share my pics with my familiy (They have the client). I would like to use it under ubuntu? Any ideas on how this could be done?

If you have recommendatinos for a similar program, please post them too, though I would like to avoid having to get my family to change to a different client program.

Tks.

Brad D. :-)

---

### Post by slumcat05 on 2007-06-04
Just off the top of my head, you could use a couple gigs of your hard drive space to install a virtual Windows environment using VirtualBox (you can create a dynamically sized virtual hard drive with just a little more than the minimum size required for the OS install, it will resize itself as you add more files and such). 

In the Vbox user manual there is a section on how to share a folder between Linux and the virtual Windows, so you could share your media folder to Windows, then use the FolderShare program in Windows to share the shared folder (sounds crazy, huh?) with your family. 

The only thing is, if you would need the folder shared continuously, you would have to have the virtual OS always running in Ubuntu, which would take a hit on your RAM. You could minimize this by only dedicating the minimum required RAM to the virtual OS (as it sounds like this program is probably not memory intensive), but it may still affect your system performance in Ubuntu. Also, it would probably be better to install something older like Windows 2000 rather than XP, as it would probably require less memory (not sure though?). 

Anyway, kind of a hack solution, but it's all I got. Good luck.

---

### Post by lazyart on 2007-06-04
Use Hamachi, create a virtual network (they would have to install the client as well) but it is a Lin-Win solution.  Share a folder out and they can see it by browsing the network from their Windows machines.  As long as your machine is running they would be able to access it.

This lends itself to other possibilities--  FTP, remote desktop/VNC and even remote printing.

---

### Post by slumcat05 on 2007-06-04
**EDIT: Apparently you need to install the Guest Additions in the virtual OS to do this, see the user manual linked below.**

Here's how to share a folder between Ubuntu and VBox, in case you're interested. In Ubuntu, the command is like:

```
VBoxManage sharedfolder add "VM name" -name "sharename" -hostpath "/path/sharefolder"
```

Then in the virtual Windows, you do (in the command prompt):

```
net use x: \\vboxsvr\sharename
```

where you can replace x: with whatever you want the folder to be mapped as.

Thus if you want to share "/home/john/Media", your virtual OS is named "WinXP" in VirtualBox, you want the folder to be called "Media" in Windows, and you want it mapped as g:, you would do:

```
VBoxManage sharedfolder add "WinXP" -name "Media" -hostpath "/home/john/Media"
```

Then boot up your virtual Windows, open the command prompt, and do:

```
net use g: \\vboxsvr\Media
```

That's it. Then in My Computer, there will be a new network folder called g: that will contain all the files in your Media folder (you should then be able to share this folder using your program). I like to make a shortcut to it and put it on my Desktop or in the My Music folder, or whatever, but it's there and you can add or remove anything you want from it.

If you want to see the entire manual (many useful things for VBox in there) you can download the PDF from here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by rich.bradshaw on 2007-06-04
Can't you just use a webserver or ftp server to share files over the internet?

---

### Post by BradDet on 2007-06-04
Thanks for the suggestions.

On of the things I like about FolderShare (over other solutions), Is that it is sort of 'P2P', in the sense that once one or more people get their shared copy, I can then turn my machine off. If someone else wants a copy they can get it from any machine that has my shared folder.

Sort of like 'Kazaa' but with security so only my friends can see my shared files.

---

### Post by lazyart on 2007-06-04
Maybe something like fileden which is an online service.  Upload your stuff there and you can invite others to view.

---

### Post by rabideau on 2007-06-17
On my version of feisty there were a couple of additional items I needed to do before Virtual Box file sharing worked.  Before these were done I kept getting an Error 53 on the windoze XP pro client.

Before the **use net X: \\vbboxsvr\share** will work be certain to complete the following steps:[LIST=1]
[*]Start your Windoze client
[*]On the window in which windoze is running at the top is a menu bar, select ***Devices>>Install Guest Share*** (this may be all you need to do if the function works-- I needed more) If the Install Guest shares works you should get a message saying it completed. From that same window bar item you can verify the success by selecting ***Devices>> Shared Folders ***(if you see yours there you are ready to use go into windoze and execute **use net X: \\vboxsvr\share**
[*]**If it didn't work, **like it didn't for me, **do not despair! **Go back to that little handy Devices menu and select ***Devices>>Mount CD/DVD ***and select the CD/DVD ROM image on your windoze desktop (or maybe it was Control Panel...) you should find Guest Shares install CD (iso).  Run that and everything should work fine! You have manually installed the Guest Additions.  From here your **use net X: \\vboxsvr\share **should work. Remeber to look for the shares at the bottom portion of your Control Panel.[/LIST]I hope this helps... it sure frustrated me finding all these little parts. ;)

---

### Post by maxito on 2007-09-22
hi,

I have the same problem, I now got a stable feisty running, but I haven't found such a smooth, easy to use file sync like foldershare yet.
I also crawled google, wasn't there a linux version on the foldershare website?? can't just anyone who downloaded it give it back to the community, it might still work ;-)

but I've also found another possibility: [http://www.powerfolder.com/](http://www.powerfolder.com/) I haven't tried it yet, but it seems to be a good solution.
Anyone used [http://www.powerfolder.com/???](http://www.powerfolder.com/???)

all the best,
max

---

### Post by rabideau on 2007-09-23
Hi

With folder sharing there is nothing to synch.  The same files are used in both Windoze and Linux.  You only would need to synch two separate directories and so far as I can see there's no reason to use twice as much space when a single image will do.:KS

---

### Post by maxito on 2007-09-25
hi,

don't get me wrong, i don't weant to share files on a single computer, i want to share them between different computers and operating systems.

all the best,
max

---

### Post by Tmantiko on 2007-09-26
Hi,

Th exact same sentiments here - installed ubuntu 3 days ago and truly love the experience. I do however sourly miss foldershare: secure p2p folder sharing over PCs. 
I use it mainly as means to keep folders synced between my home and work PCs (the latter is behind a firewall).

---

### Post by rabideau on 2007-09-26
Try looking at unison... I think it's from the Univ. of Pennsylvania.  That will synch almost anything imaginable.:KS

---

### Post by Tmantiko on 2007-10-12
Thx for the tip, but as unison works in client server mode it's less suitable to me, as both my PCs (work and home) cannot operate as servers open to the world.
The great benefit of foldershare is the fact the once installed on both PCs, they communicate via peer to peer architecture.

---

### Post by hyper_ch on 2007-10-12
Well, I'd say either go for SSH/SCP by creating additional users and jail them to the share folder and allow SCP only

or you could setup an rsync server and they could then sync with you... however in Windows they would need Cygwin to get rsync.

Or you could setup a VPN

---

### Post by jacw on 2008-01-05
I have used Foldershare succesfully to share family photos with family members as well as keep multiple personal computers in sync in different locations (work, vaca house, offline laptop and home) where home network sharing would not work ("My Documents" and "Favorites" in Windows for example) so all files remain local. I tried Powerfolder because I am using Ubuntu much more recently and it is nowhere near as good. It seems to get confused easily whereas Foldershare is more robust and syncs more efficiently. For example on PowerfolderI have had one fresh new machine move files into the Powerfolder recycle bin that it downloaded in the first place in favour of the same file from a different machine that had the same files but happened to be offline when initial sync started. Powerfolder is OK but Foldershare has worked far better for me.

Why did Foldermatch announce a Linux release in 2005 (the press release is still on their website) but not deliver?

---

### Post by Shagratz on 2008-05-02
I am also looking to get foldershare working.. I managed to run and OLD version under wine for a few weeks, but M$ have now stopped it working again with a new update... grrrr....

btw my 1st post :) I love Ubuntu so far :) just need to fine tune it more :)


Shagratz

---

