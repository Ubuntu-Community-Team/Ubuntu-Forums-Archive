---
title: "Ubuntu Destroyed My Pc!!! Waaaaaaahhhhh!!!! T_t"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by AdonisV on 2006-02-12
I had a p4 1.6Ghz
256 ram
40gbseagate hd

Previous O.S. : Windows XP

I planned to make my e drive the ubuntu so that the files of my sisters will not be affected which are
C(NTFS): = Windows
D(NTFS): = Documents and Program Files of sisters
E(NTFS): = Documents of mine

I turned the E drive into an ubuntu drive (EXT3) with some in swap  and it's working now but the problem is the windows xp does not lad anymore. it will load to a certain portion then hang. I've been trying to fix it for weeks now and it does't run windows xp

I tried:
-Repairing windows xp on drive c:
-Reinstalling windows xp on drive c:
-free the e: partition coz I tought it might be due to unrecognized partition format then reinstall winxp on c:

My last resort was to format the whole 40 gb HD. and turn it into 1 ntfs drive. and reinstall the whole windows xp. the same thing results..

Windows will load only to the loading screen where the logo and loading bar can be seen. then it hangs or reboots automatically and when you install ubuntu or suse they works fine but never if windows xp..

When I tried to reformat again to repair winxp using the repair tool I got into the c: drive I got the chance to discver something shocking... having formated the whole drive c: into ntfs and removing linux and having a fresh reinstalled windows xp on this drive.. the usual msdox command cd.. ; dir/w or dir/h are not working. the linux commands dir -h ; cd .. works though :cry: what is going on?? 

I also tried removing the HD from the cpu and reformat and reinstall winxp on it and it will run on the other cpu but when I return the harddisk to the original cpu it will not load and say Boot load error:

is there something linux did to my system and banned win xp from ever being installed on it?:cry:

---

### Post by Jason_25 on 2006-02-12
I think you should boot to the recovery console on xp and do a fixmbr and then a fixboot.  Then install XP like normal.  Also you should remember, that at least right now, the only way software can change hardware is by flashing the bios/firmware.

---

### Post by Iowan on 2006-02-13
[QUOTE=AdonisV]I also tried removing the HD from the cpu and reformat and reinstall winxp on it and it will run on the other cpu but when I return the harddisk to the original cpu it will not load and say Boot load error:
[/QUOTE]I wonder if the BIOS got changed?  Some are smart enough to autodetect HD settings, but maybe not smart enough to put things back.  I have a Compaq (old 233) that mis-detects HD size unless I run the Setup program.

---

### Post by newuser111 on 2006-02-13
sounds like your windows drive got toasted, if it were an MBR issue, it would not boot into windows

Of course this could be a completely unrelated issue to the ubuntu install, ever heard of coincidence?  because if it were the ubuntu installers fault, ubuntu wouldnt work or your windows drive would be erased, neither of which is true.  Since you are installing to different drives I would suspect physical hardware failure

---

### Post by wrtpeeps on 2006-02-13
i recon your hard disk has gone to pot. After 2 formats you still cannot boot, which is pretty weird.

---

### Post by Iowan on 2006-02-13
I wouldn't be too anxious to toss out a drive that works in another computer (I presume that's what you meant by "run on the other cpu").   Will the original drive from "the other cpu" work in this machine?

---

### Post by wolfmaniac on 2006-02-13
juz do this -- if u are using xp with sp2 then remove it.
install xp with sp1 or without ne sp. then this will definately wrk as it worked for me sp2 might not supporting some of ur hardware


and it was not ubuntu dat destroyed ur pc it was the problem with XP(sucks)

---

### Post by lzfy on 2006-02-13
Linux taking over the World, starting from your PC :rolleyes: 

Heh seriously I don't think this has something to do with Ubuntu. Try resetting you're Bios, maybe that works.

---

### Post by r4ik on 2006-02-13
Did you do a  format c: /q ?
As far as i know thats the ultimate format command.

---

### Post by patrick295767 on 2006-02-13
[QUOTE=r4ik]Did you do a  format c: /q ?
As far as i know thats the ultimate format command.[/QUOTE]
   
Or format c: /u  ,no ? 
  
fdisk /MBR 
(to remove the grub from the MBR)
  
U may  / should maybe downlaod the bootable cdrom : ghost powerquest driveimage dos, from the P2P 
(16MB about)
That'll help you a lot. 
  
Dont forget to copy the ntdlr on one of ur partition to boot the Windoxs !

-Greetigns and Courage !

Pat'

---

### Post by r4ik on 2006-02-13
Or format c: /u ,no ? 

Thanks for the correction on that one.
My mistake.

---

### Post by Chappy on 2006-02-13
I'd bet my lil bippie that the problem is in your BIOS. I thought I'd done the same thing this past weekend. My PC was running well w/Xandros, so I decided to put Ubuntu on another HDD. In the process my Bios, where it tells your MB which HDD to run, changed from Auto to none. I was sure the HDD was dead. Nope, the W-XP that was on the HDD had reset the BIOS. Or a gremlin. Check your BIOS. Also, when you install again, install Ubuntu 1st. It will reformat and partition your HDD for you. Never throw out old PCs or old components. Mail them to me.

---

### Post by alfonz on 2006-02-13
All the symptoms point to a hardware problem not software problem. As Chappy sugested you should start with your bios first.

---

### Post by newuser111 on 2006-02-13
most computer in the past 10 years can autodectect harddrive settings, there is no real need to custom set drive settings

its an obvious case of hardware failure, harddrives do fail, people are quick to jump to blame ubuntu

---

### Post by eriqk on 2006-02-14
Maybe it's the Parted bug? 
I'm not sure if that's around anymore, but until a while ago this would plague dual-booters. IIRC it would garble the partition table, which to my knowledge doesn't affect Linux (so it can still boot- if anyone can correct me on this one, please do, cause I'm not sure anymore. It's been a while). Windows needs it however, so when you try to boot into Windows you'll get nothing (or maybe a line or two from Grub).

It's best to set you HDDs to LBA- auto doesn't seem to be a way out of this one (if it's the Parted bug, that is).
However, any attempt to rescue your windows installation may have b0rked it permanently. Let's hope this isn't the case.

Groet, Erik

---

### Post by AdonisV on 2006-02-14
Tnx for all the replies but I don't thinks it's a hardware problem. my pc is not old. it's a p4 bought 2-3yrs only I do't think it's that old. my bios als detects it well no problem with that.

I reinstalled the ubuntu on it temporarilly so that my sisters can use the pc while the widows is not working. the harddisk accepts loading the ubuntu. 

:-k  here's what's going on..
[Hard disk on the original pc]
-Hangs on loading screen when 100% reformated for windows ntfs and run with windows only
-Runs ok when reformated and run with ubuntu only

[Same hard disk dismounted from orig pc and used in the p3 500mhz p.c.]
-Runs windows xp

[returning the same harddisk fully formated with working xp to orig p.c.]
-harddisk error!

[Weird encounters]
-Having reformated the hard disk into 1 drive C: ntfs and installing windows, it does not run windows and hangs in the loadings screen. So I used the recovery console.. what happens is I cannot use the windows command as they were.. "dir/w" or "dir /h" or any of the old ways I access windows like cd.. does not work anymore.. to do them you use "dir -h" or "cd .." which i think are linux commands.. \\:D/ 

tnx guys, I'll try the "format /u" or "fdisk mbr" commands within the week. I'll post the results when it's running ok already. so does that mean dismounting the entire partition and recreating the 3 partitioned H.D. into 1 drive c: using the windows installer did not clear the mbr and grub is in there? is there a way for ubuntu and windows to coexist in 1 hd? and if so is it windows xp in ntfs or fat32? :-k

[Unrelated Tpic] have you guys watch the movie "firewall"? why are the computers used by the bank still in black and green? is that cobol? running in servers. programming tools I use are mstly in win like vb.net, asp.net vb6, jsp and oldies like cobol. I was wondering why banks use old programming tools like them but the servers machines look cool though.

---

