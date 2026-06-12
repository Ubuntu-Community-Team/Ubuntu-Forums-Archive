---
title: "NTFS,Samba,Workgroup"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by DeadEnd on 2006-01-10
HI
I have installed latest Ubuntu on one of my PC and I wish to use it as a 24/7 always on, file server to the rest of my network.
I use WIFI,WPA PSK throughout the house and all other boxes are XP pro running in workgroup configuration, I use a wrt54g(flashed with DD WRT firmware) router to connect them all VIA WIFI, and 1 XP box is hard wired to that (rj45).
All the boxs can see each other and show up in network places, in the correct workgroup.
I have followed some info in the forums and wiki and can share from a folder called public to xp and when I try a folder called homes I am prompted for a password.I can see and access all my XP shares.

I am new to linux,esterday actually and so am a little confused about a cpl of things.

I have an external USB 2.0 hard drive Caddy which houses a 200GB IDE hard drive, This dive is formatted NTFS and contains a folder with 150GB of music and video.
I want my Ubuntu box to share this on the network but I get error cannot find,it may have been moved deleted.  es this mean I cannot share NTFS from Ubuntu or the problem lies in the fact it is an external USB drive.
Could I create a Public folder on the extnal drive and drop my music into that?

---

### Post by DeadEnd on 2006-01-10
sorry my Q seemed slightly confusing 

Basically can I share a  USB 2.0 external hard drive contents which are  formatted as NTFS from a Ubuntu PC using Samba to a windows workgroup, if not why,and what solutions are open to me? other than buy a new had drive, I have no way of backing up 150GB if I were to reformat nor enough room to dedicate a ext3 partiton.

---

### Post by DeadEnd on 2006-01-10
Could someone just confirm what I am trying to do is possible?

---

### Post by DeadEnd on 2006-01-10
:(

---

### Post by tabinin on 2006-01-10
File systems are transparent across the network, however, NTFS read/write is not ready for prime time in the linux world (which your server would need, as local file systems are not).  If you can convert NTFS to FAT32 (I *think* this can be done with a 3rd party tool), then you are in business.

---

### Post by DeadEnd on 2006-01-10
ok thnx for info, I can stop bashing my head against a brick wall now.
Strange how it can read my files on that disc but not share them esp since I presume samba is based on windows technology,and yet Ubuntu quite happiy see my NTFS file on the window machine .
looks lke my only option then is to purchase a new drive because I beleive its not possible to convert NTFS to fat without losing info.

---

### Post by tabinin on 2006-01-10
If you only want to read from the drive, you should be able to set it up.  If you want to write (save) that is were you might have problems.  

You only need to back up the data while you reformat your drive.  Maybe someone you know has a few extra gigs of space to lend?

---

### Post by DeadEnd on 2006-01-10
"*If you only want to read from the drive, you should be able to set it up."*
Yes that would be fine but for some eason when I set the share on my music folder , from Ubuntu on the drive which is attached to this machine, I go to server connect \ mshome \ music the folder is there but when I click to open it gives me a pop up box saying the folder does not exist or has been deleated.

---

### Post by tabinin on 2006-01-11
Hmmm....  I just checked my USB drive attached to my server which I almost never use via samba and it is giving me the same problem.  A while back, I didn't have this problem.  I will look into it after work more, but my suspicion is a pmount upgrade may be causing this.  

How do you mount your usb drive?

---

### Post by DeadEnd on 2006-01-11
[QUOTE=tabinin]  

How do you mount your usb drive?[/QUOTE]
Hmm Basically i just plugged it in, I assumed its automatically mounted as it appears on the dektop or is this not case?
I have been delving through the forums and qiute possibly this is the problem I assumed if it enabled me to share the folder in admin/shares then it was mounted, but cannot actually find any reference to mounting external drives and share NTFS to use as template to correctly set this up (total noob  day 3 of my adventures in linux ) I was hoping there is a GUI appplication I could download from the repositries to help me, would I be correct in saying swat is the best for this purpose? 

And thnx for replying I read so many issues and ways to achieve this but I cannot see the wood for trees at the moment.

---

### Post by tabinin on 2006-01-11
When you have Gnome running, plugging in a USB drive causes a program called pmount (see man pages) to mount the drive and then Gnome puts an icon on your desktop.  I normally do not automatically start X/Gnome on my server since I run it headless.  I found out tonight that when I do start Gnome, I can see my USB drive via Samba on my other computer.  When I do a manual pmount remotely (ssh), I don't get this.

Anyway, back to your issue. Post your smb.conf and lets take a look at it.  

```
sudo gedit /etc/smb.conf
```

---

### Post by hwliang on 2006-01-12
You know, when I share my NTFS formatted External HD with my Ubuntu laptop, I don't have problems accessing it on a WinXP Machine. I don't recall doing anything special.

A potential problem is the way you're sharing it. Maybe you didn't check "Allow browsing folder" when you shared it? If that's the case, then the External HD is actually being shared, but you don't see the folder when you access your Ubuntu machine (you'd have to manually type in the address at the location bar).

I hope that was helpful (I'm also a newbie, so I don't really know more than that).

---

### Post by DeadEnd on 2006-01-12
Hi
Thanks for info and help guys alls working fine now,

I didn’t want to keep coming back with all the problems I was having so thought sort them first, little did I know it would take me 16 hrs solid . 

Unfortunately I ran into some other problems which forced me to reinstall Ubuntu, I decided to try konquoror, but for some reason after installing it just would not load, any other packages I tried got error ,(sorry haven’t got the exact error message but) went something along the lines of ) " no newline in a package kfind.." browsing around it seems I had to add an extra break space somewhere in that file or package for the fix but no idea how to edit it,I did to try to open the package but I got error "archive not supported" unfortunately the "no newline" thing stopped me from removing or installing any other packages so decided to reinstall anyway as quick fix.

Which then lead me on to another problem. 

When I reinstalled,  on the second boot I kept getting (again sorry not exact message)  "intel boot loader error blah blah psx " again goggling seemed to suggest a problem with BIOS attempting to boot off a NIC and fix was to change the boot order,I have no idea why the Boot order had changed
in BIOS my boot order was CD/HD/bootable diskette/network  which was correct , so no idea why I got the psx error.

I had not installed any new hardware nor settings in BIOS but then I remembered

I have my Wlan card and a basic LAN card in my box,?   I could not disable network as an option in BIOS but I did remember when I first installed Ubuntu I only had my Wlan card in the PC, I read before installing my card was supported and so was surprised when Ubuntu informed me "no network card found” but there is a firewire device that could be used” well I knew for sure I had no firewire device maybe it was referring to my Wlan card but to be on the safe side I added a LAN card to my box restarted and everything else went ok from there.
My wireless card worked fine, I never configured the Lan card.

As the HD in the Pc was old 6.GB and may be to blame for all the problems, and to cut a long problem short, I have took the Lan card out, the floppy as well (there was some mention this also could cause the psx), connected a new CD drive (again just to be sure)   archived all my data on the 200.GB drive to DVD and spare storage on other PCs and formatted the 200GB to use as internal drive on the Ubuntu box and took out the old  6.GB one,
And started again formatted drive as
1 ext3 = 40GB
1 swap 350MB
! Home =50 GB  
1 Fat 32 100 GB 
The rest I formatted as NTFS so I could at least get what I was originally planning to do to work.
Ok it all seemed to go well I ignored the offer to use firewire as my network device and chose configure manually but part way through I got yet another problem, 

“Debootstrap exited with an error (return value 1)"   again after a search it suggested there was a problem with the way I formatted the drives so went back looked more carefully at some of option and found I could mount the fat32 partition as /window from there so I chose that it seemed relevent, sorted my partitions correctly this time tried the installation, and from then on the installation finally ran through and got me to the point where I take the CD out  and the PC reboots, which it did but then I got the message from BIOS  “no operating system found”.
.
Ok so I decided to keep it even simpler this time and wipe drive completely and keep default settings for partition one big drive with swap only.
Again after taking CD out and rebooting message “no operating system found……………..

So at this juncture I can only presume the BIOS does not correctly identify the size of the 200GB HD yet whereas when the Ubuntu CD takes over it can, unfortunately when it comes to booting of the HD after CD is removed the BIOS must throw a wobbly, so I guessed I must need to get the fix from drive maker to overcome BIOS limit to get this drive working.

So I decided to put the 6.GB drive back, install Ubuntu on that again and use the 200GB as full fat23 storage in the USB caddy.
Ok so this time all install went well, I installed gparted from the repository and got some warning about “Warning unauthenticated package” at this stage I did not care just wanted to get this thing done now, so I updated synapsis downloaded / installed gparted ignored the warning and ran the program,plugged in my external drive selected fat 32 and formatted it,,2 hrs later the bar was still churning but no way would it have took that long,I could not click on anything ,no kboard strokes were responding, just the graphic bar kept moving in gparted so switched off PC in frustration.
Ok rebooted back to login desktop and there was a little red box in right hand side saying updates available,,,hmm maybe there was a fix in there I had been missing all this time, so pressed update
It started up then gave me error “download interrupted” but helpfully gave me a command to run in terminal to fix it, which I did (if it knew what to do why didn’t it just do it) any way ran update again this time I got an error unable to flush something or other mail then duly dropped all the GUI leaving me only with cursor, again I pulled the plug.

Now this was getting beyond a joke,, so I could only put all this down to one thing, I had  pondered on earlier, I ripped another spare drive from another box formatted it, installed Ubuntu and finally everything so far is working as it should.
it was A BAD HARD DRIVE!  to blame for all my woes

I could have screamed, the original hard drive had ran win 2003 for months without any trouble, no idea why it gave up the ghost when I installed Ubuntu but it must have?
Anyways I am just happy now I have at least a fully functional OS that is sharing successfully, to my home network. 
The only things I am left to ponder is

•	Why did windows run and not Ubuntu on that drive
•	Why do packages say “not authenticated” and should I install them or will they cause harm.
•	Why is my Wlan being detected as Firewire device, if I selected to use it would it have worked?
And  my idea the BIOS not identifying the 200GB drive size correctly, but Ubuntu does so hence it throws a wobbly when being booted from after installation.

I am sure I will find the answer to all these over time in the forum and web and tinkering, just wanted to let you know how it all went..any why I took so long in replying,,
I must have had a years worth of problems and this is only my 4th day using any flavour of linux,:))

Now I neeed Sleeeeeep and looking forward to taking Ubuntu out for a test drive tomorrow seeing whats it got  and finding some window equivelent apps for linux I like to use daily, and getting some of those excellent apps that only linux seems to have. 
Hmm I dont feel so tired all of sudden :))

---

