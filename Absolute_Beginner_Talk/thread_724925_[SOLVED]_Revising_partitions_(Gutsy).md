---
title: "[SOLVED] Revising partitions (Gutsy)"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Mylorharbour on 2008-03-15
I recently changed the HD in my old Pentium 111  machine. Following the help on here I set up 4 partitions.....

WinXP - 10Gb
Swap - 1Gb
/home - 10Gb
/ - 20Gb

I installed XP into the fist partition then used the liveCD to install Gutsy and setup dual boot - works a treat. I then allowed Ubuntu to download it's updates and installed a whole host of packages I fancied trying. My problem is that, being an absolute beginner, I set the partions as primaries, all 4 of them so now I can't access the spare 240Gb on the HD. Now as there's nothing I need to keep I could wipe it all and spend another 2-3 hours re-installing but I'm wondering whether/how I could back up what I have, re-jig the Linux partitons to extended/logical and restore.

Could something like PartedMagic do the job or is it best done another way? Command line stuff's come as a bit of a shock after years of GUI so If there's a GUI method that'd be nice.

---

### Post by forestpixie on 2008-03-15
From a quick search I think it's possible with some utilities - but I'd be a bit worried myself.

If I was trying to do it I'd be inclined to change the /home and not / - also just as an aside 20Gb for / is very big - I've only used 4of 8.

Why don't you just resize your /home using gparted either as a livecd or the version on the buntu cd. 
If that's not possible for you and you haven't got a problem reinstalling I would do this -

1 - install aptoncd - you can get it from synaptic or do it cli with sudo apt-get install aptoncd. Use that to copy your downloaded debs - then when you reinstall - get aptoncd again and restore them.

2 - delete the /  and /home then make your extended partition and create the logical  / and /home inside  ( I wouldn't have 20Gb for / though :) )

I'd certainly favour going for the resize of /home if that's possible.

---

### Post by Herman on 2008-03-15
:) Hello Mylorharbour,
I don't know anything about PartedMagic yet, but I imagine it would be okay. I use GParted.
GParted is also called Gnome Partition Editor, and it's in your Ubuntu Gutsy Gibbon LiveCD. Go 'System'-->'Administration'-->'Partition Editor'. 
Any good 'Parted based partitioner will do.

I would probably start by deleting the swap area first, and resize the Windows XP to occupy the extra space left behind after you delete the swap area.
Then you will have three primary partitions.
You should be able to create an extended partition after the 20.0 GB/ (root), and make it fill the rest of your hard disk.
Then inside the extended partition, make a new swap area, (logical).

You would need to edit /etc/fstab to register the new swap area.
```
gksudo gedit /etc/fstab
```Find out the new swap area's file system UUID number with '[COLOR=#000000][FONT=Bitstream Vera Sans Mono]ls /dev/disk/by-uuid/ -alh'
[/FONT][/COLOR]```
ls /dev/disk/by-uuid/ -alh
``` And paste the new UUID number over the old UUID number in /etc/fstab to overwrite it and update /etc/fstab.

After that you should be able to create as many logical partitions as you like and utilize the remaining 239 GB of your hard drive.

---

### Post by Herman on 2008-03-15
I agree with forestpixie, 20 GB is more than you should need for / (root), and you could probably use more space in /home.
If you did re-install you could place your /home after your / (root), so you can resize it larger if you ever want to.

Actually, I don't like having a separate /home partition at all myself, I prefer installs with everything in the single / (root) partition because that way we never need to worry about whether there's too much or not enough space in one partition or the other. Directories are able to expand and contract instantly, and so are always the perfect size for their contents.

Regards, Herman :)

---

### Post by forestpixie on 2008-03-15
Herman - do you know if it is possible to change a partition from primary to extended-  just in the interest of extending my knowledge? Also do you have a permanent 'partition or grub' search set up , really ought to learn to leave them alone - I'd imagine you've a post in all of them :)

I tend to try and keep my /home seperate - because as much as I make everone I know sick telling them to make sure they have backups - I'm not very good at it :D

I managed to lose all my data following a hairy time when I reinstalled without making sure I'd got up to date backups. So now I have a seperate /home - and clear out all the hidden folders I've accumulated before I start reinstalling. 

:smily of me slapping myself round the face:

---

### Post by Herman on 2008-03-15
> do you know if it is possible to change a partition from primary to extended We can use GParted to copy a primary partition and paste it into an extended partition, that would turn it into a logical partition.
> do you have a permanent 'partition or grub' search set upNo, I just browse around the forums for something that interests me or that I think I can help with, sometimes I use the 'find unanswered posts', sometimes I search for 'grub' or 'fsck' or whatever subject happens to seem like a good idea. If I'm updating a web page article about a subject I'm more likely to be attracted to threads on it, but very often it's the other way around,  I learn something from a thread and then decide to update a web page. :)

It's okay to have a separate /home, but it's okay not to. 
You just got me thinking, I need to make a new backup too and I think I'll try making myself a new backup script and run it from crontab and see what I can come up with. There are some nice backup programs we can install in Ubuntu now too. Maybe tomorrow. (Yawn).

Regards, Herman  Zzzz

---

### Post by Mylorharbour on 2008-03-15
> **forestpixie said:**
> ..........If I was trying to do it I'd be inclined to change the /home and not / - also just as an aside 20Gb for / is very big - I've only used 4of 8.
 I did read that 10Gb would be big enough but as I didn't know the size of the debs nor where they were installed at the time I played safe. As it happens Ubuntu and the debs in / (root) only seem to take up 3.5Gb anyway.

> **forestpixie said:**
> Why don't you just resize your /home using gparted either as a livecd or the version on the buntu cd.  The order on the disk is WinXP, swap, /home, / (root) so /home is jammed between swap and /.

> **forestpixie said:**
> 
If that's not possible for you and you haven't got a problem reinstalling I would do this -

1 - install aptoncd - you can get it from synaptic or do it cli with sudo apt-get install aptoncd. Use that to copy your downloaded debs - then when you reinstall - get aptoncd again and restore them.

2 - delete the /  and /home then make your extended partition and create the logical  / and /home inside  ( I wouldn't have 20Gb for / though :) )

I'd certainly favour going for the resize of /home if that's possible.This seems my best bet as I can then re-arrange their positions. Shame there seems to be so much help to install Ubuntu but this sort of thing doesn't get a mention.

> **Herman said:**
> :) Hello Mylorharbour,
GParted is also called Gnome Partition Editor, and it's in your Ubuntu Gutsy Gibbon LiveCD. Go 'System'-->'Administration'-->'Partition Editor'. 
 Yep, I used that from the LiveCD to partition the disk prior to installing Ubuntu

> **Herman said:**
> 
I would probably start by deleting the swap area first, and resize the Windows XP to occupy the extra space left behind after you delete the swap area.
Then you will have three primary partitions.
You should be able to create an extended partition after the 20.0 GB/ (root), and make it fill the rest of your hard disk.
Then inside the extended partition, make a new swap area, (logical).

You would need to edit /etc/fstab to register the new swap area.
```
gksudo gedit /etc/fstab
```Find out the new swap area's file system UUID number with '[COLOR=#000000][FONT=Bitstream Vera Sans Mono]ls /dev/disk/by-uuid/ -alh'
[/FONT][/COLOR]```
ls /dev/disk/by-uuid/ -alh
``` And paste the new UUID number over the old UUID number o /etc/fstab to overwrite it and update /etc/fstab.

After that you should be able to create as many logical partitions as you like and utilize the remaining 239 GB of your hard drive. Sounds quite logical but forestpixies route looks a little easier for a newbie. I did use one of your commands to see what the current UUID number was but as the output didn't make any reference to UUID I thought I'd shelve your option for now. 

Thanks very much for replying both. I'll let you know how I get on.

---

### Post by Mylorharbour on 2008-03-15
Guys,
Before I commit myself, what would happen to my dual boot setup if I shifted the partitions around?

---

### Post by forestpixie on 2008-03-15
> 
Shame there seems to be so much help to install Ubuntu but this sort of thing doesn't get a mention. not sure what you're getting at there, anyway - 

Your boot menu will be wrong but that can be edited from within the livecd environment, if the order at the moment is like so assuming that you're discs are referenced as sda* and for grub the reference is in ()
WinXP - sda1 - (hd0,0)
swap, - sda2 - (hd0,1)
/home - sda3 - (hd0,2)
/ (root) - sda4 - (hd0,3)

to get a definitive answer to the references

```
sudo fdisk -l
```

_But _if you delete the buntu partitions then grub will be rewritten during the install.

If that's what you're going to do I would - 
delete the partitions and then create these

10Gb - for / - as a primary, format to ext3
create an extended

all of the rest - 1Gb - as a logical, format to ext3

1Gb format as swap - as a logical

That SHOULD then make them (believing that partitions within an extended number from 5) like this in gparted, 

sda1 - ntfs - existing XP
sda2 - ext3
sda5 - ext3
sda6 - swap

Now start the install - when you  get to the partition part - go manual

pick sda2 (check numbers here) - edit partition - pick a mountpoint of /
pick sda3 - edit partition - pick a mountpoint of /home
swap should be uneditable - it knows what it's going to do here.

Obviously if you're wanting to check anything post here -I'll keep half an eye on it.

Good luck.

---

### Post by Herman on 2008-03-15
[LEFT]> Shame there seems to be so much help to install Ubuntu but this sort of thing doesn't get a mention. Sorry about that, you have a point there, but where should we put the information so people will find it? 
Did you just install Ubuntu your own way, or did you follow someone's installation guide?
I have an installation guide, but it's mainly for the 'Alternate' installation CD, and I doubt if very many people find my [Help on Partitioning]("http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning") in the [Pre-install Page]("http://www.users.bigpond.net.au/hermanzone/p17.htm").

There are lots of different installation guides out there, I don't know how anyone would ever find and choose the 'right' one. 
One of the best is aysiu's, [Install Desktop CD Ubuntu]("http://www.psychocats.net/ubuntu/installing"). Aysiu also has another web page that explains [Plan Partitions]("http://www.psychocats.net/ubuntu/partitioning").

If you found the [Ubuntu Community Docs]("https://help.ubuntu.com/community/") and went to the [installation page]("https://help.ubuntu.com/community/Installation") there you would have found lots more guides for installing Ubuntu.  
If you followed  [GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall") there you probably would have been okay, or [WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot"). Neither of those explain much about partitioning but they would have resulted in a nice with a Ubuntu / (root) in a primary partition and swap in a logical partition, so you would easily be able to resize and do whatever you wanted from there, and you wouldn't be stuck at all.

Right now the best I can do about it is update my [Help on Partitioning]("http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning"), I can see some room for improvement there, but I wonder if anyone ever looks at it? Probably I'm just wasting my time. :lolflag:

Regards, Herman :)
                                [/LEFT]

---

### Post by forestpixie on 2008-03-15
> I doubt if very many people find my Help on Partitioning

I did - in fact I found it before in the dim and dark windows days :) so don't feel to despondent.

It seems to be a fact that most people have no real idea about partitioning or any of the other things you learn by making your own pc. I get really funny jokes about jumpers still :rolleyes:

---

### Post by Forrest Gumpp on 2008-03-15
No, Herman, you are not wasting your time and people do read your guides.

Even more people are referred to them in threads where it seems that a more general understanding of installation matters would be of benefit to the OP (at least in many of my bean-gathering posts!:)), or where they serve to clarify the discussion generally.

I don't know what others think, but I find that your extensive explanations in human-readable text are just what is needed in a forum help environment that does tend toward extensive presumption of prior learning about these matters.  Given that the subjects of partitioning and installation **of necessity lie at the forefront of most new users' experience** of Linux in general and Ubuntu in particular, and that about the only thing most new users know beforehand is that "[COLOR="Red"]**partitioning is dangerous**[/COLOR]!", full explanations are doubly, yea, trebly, important in this context.

Your Illustrated Dual Boot Site homepage sits permanently in a tab in Firefox on my computer, as does aysiu's Ubuntu Linux Resources in another tab.  Your whole site is saved to HDD in another installation of Ubuntu 7.10 that I did just for practice, against those times when my Fraudband service may be running at peak performance.

Your 'TestDisk' page allows me to live in hope that, when once I have digested it and become experienced enough, the presently lost contents of a HDD containing years of work in another field will eventually be recoverable.

Many thanks Herman.

---

### Post by Mylorharbour on 2008-03-15
Herman,

I hope this will be useful to you. It's a few jottings regarding how I stumbled across information as I tried to come to grips with Ubuntu Gutsy. I will have a good look through your links over the next few days though. Thanks for your help. All's ok now. I am now the proud owner of a 256Gb /home partition.:)

I think, like many, I started off searching for Ubuntu in Google, came across the LiveCD pages then hunted for dual boot help. I came across this [https://help.ubuntu.com/community/WindowsDualBoot#head-c55a4224ebb4fe343620aedbe01de401057fc624](https://help.ubuntu.com/community/WindowsDualBoot#head-c55a4224ebb4fe343620aedbe01de401057fc624)  and some other forum messages which basically stated that the LiveCD install would sort it automatically. It didn't. Ubuntu installed ok using the first auto install option but I lost Windows 2000. Not a major inconvenience as it happened. I just reformatted and loaded XP, looked around for some guidance and eventually stumbled across posts recommending I use the manual option AFTER partitioning (GParted). This made much more sense as I was then free to screw the partitions up as you now know.

I did have to look long and hard before I found out how large the / and swap partitions should be but I never found much out about sizing /home nor primary/logical nor how best to arrange things on a large HD like the one I have now.

At one point though I did decide to leave XP on the old 20Gb drive and put Ubuntu on the new drive but the install couldn't get its head round the dual boot setup and left me with Grub loader Error 17's. So I fetched XP across to the new drive and it was happy again.

I actually started my new Ubuntu life here [http://www.ubuntu.com/](http://www.ubuntu.com/)
then here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
then downloaded from here [http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fmirror.ox.ac.uk%2Fsites%2Freleases.ubuntu.com%2Freleases%2F&debug=&download-button=](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fmirror.ox.ac.uk%2Fsites%2Freleases.ubuntu.com%2Freleases%2F&debug=&download-button=)
that led me to here to burn the cd [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
But that was the end of that thread as there are no links from these pages to what was needed next, a description of the LiveCD, how to use it and how best to install from it for a standard or dual boot system. I suspect that's where newbies go off in different directions and end up on the forums as there's no 'official' way forward from that point.
I eventually stumbled across a LiveCD page here [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD) but that doesn't say much about how to use it nor how to install from it. There is another page here [https://help.ubuntu.com/7.10/](https://help.ubuntu.com/7.10/) which I presume is the official documentation page but it only covers ready installed systems, not the LiveCD nor the issues surrounding installation.

Then I came across the definitive Gutsy guide here [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy) but that also only makes a single passing reference to a LiveCD and that's buried in a terminal command.

Other pages I found:
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows) - not much use really.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html)
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020) - post installation stuff
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) - ditto

---

### Post by Mylorharbour on 2008-03-15
Forestpixie...............You are a STAR!!!
Excellent explanation. I did all that and all's now well. Have one on me, Thanks again.

---

### Post by Herman on 2008-03-16
Thanks for your support there, forestpixie and Forrest Gumpp, I'm happy now, so at least some people do find the info I put out there, that's good. Thanks again.
I have revised that 'help on partitioning' and updated it but maybe there's still some more I should add to it like how much space roughly to allow for different kinds of partitions. 

Thanks for your input Mylorharbour, that's just the sort of thing I was interested to find out. When I looked I couldn't find very much information about partitioning in the Ubuntu Community Documentation either.
I went ahead and edited this page, [/forum/installation/Partitioning]("https://help.ubuntu.com/community/forum/installation/Partitioning?highlight=%28partitioning%29"). The silly thing is, I couldn't find any links from the installation pages to the partitioning page. I'm not very good at editing Wiki's either, so it's not a very good job, I'll have to keep on working on it, unless someone will clean it up for me.

I'm glad your installation is all sorted out now. Good luck with it and happy Ubuntuing! :)

Regards, Herman :)

---

### Post by forestpixie on 2008-03-16
> I'm happy now- good, glad to hear it
> 
maybe there's still some more I should add to it like how much space roughly to allow for different kinds of partitions - that could be quite helpful I would think - as you've seen on this thread - 20Gb is probably too much - but if you don't know then you guess

I think there should be a simple guide for those who've never done it before, but the problem lies in disseminating the ideas before it's too late.

I tend to point people at aysiu's page - mostly because the pictures are the same as installers are seeing on their monitors. But you're pages are ones I constantly use myself - especially the GRUB pages - that is how I found out about Supergrub - which has been more than useful at times.

But of course - this is always without fail after the horse has bolted, perhaps there should be a 'I'm just about to install but...' sub forum in Absolute Beginners. There doesn't seem to be many people asking for pre installation advice which is a shame because it'd help many of them.

Mylorharbour:

you're welcome - next time I take the drive down to Kernow - I'll pm you before I leave and take you up on that :) 

Can you mark thread solved now that it is.

Edit - Herman when I opened this thread - the one directly underneath it had this reference in it  - [http://ubuntuforums.org/showpost.php?p=4524900&postcount=5](http://ubuntuforums.org/showpost.php?p=4524900&postcount=5)
 - see - stop worrying :D

---

### Post by Herman on 2008-04-06
:) Update: I'm starting a new website which shows how to install with the 'Desktop' Live CD's installer and it shows the actual partitioning process.

I plan to put more information in there about partitioning, it's still under construction right now, (April 7, 2008.)

Here are the links, 
[Hardy Heron Beta / Gutsy Gibbon Graphical Installation]("http://www.herman.linuxmaniac.net/p22.html") A

[Hardy Heron Beta / Gutsy Gibbon Graphical Installation B]("http://www.herman.linuxmaniac.net/p23.html")

There's a third page that I'm making which uses 'Guided' partitioning which is easier and so a smaller page than the other two.

Regards, Herman :)

---

