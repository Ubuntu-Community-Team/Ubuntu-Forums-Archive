---
title: "[SOLVED] K3b says, &amp;quot;Cd record has no permission to open device&amp;quot;"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Motorhead Kaze on 2008-01-24
I see another post with the same(?) problem I have, but perhaps that thread has gone cold, so I couldn't ask my own questions.

First, my DVD player stopped playing DVDs outright.  But would play and burn VCDs just fine.  K3b claimed it could not "Copy encrypted DVDs" when I tried to copy one.  (never an issue all year).  I reinstalled the Cyberlink driver and can watch DVDs again, but now, trying to burn a .cue file (one I made personally, and have burned before) I get this message from K3b: **"Cd record has no permission to open device"**

This week, K3b is no longer friends with my DVD player.

Someone on another thread said to go to the "Kcontrol/admin" menu, but I don't know of such a menu.  I'm in Gutsy, perhaps that is a Kubuntu menu?  But basically, I need some help with simple, noob instructions.

If you need me to create or look at a log in order to help me, please tell me where to find it.  

I would appreciate the help, I create and burn DVDs regularly, so need the K3b to "Respect my authoritaaa!"

---

### Post by y-lee on 2008-01-24
I'm not sure but you can try typing the command **groups** into the terminal

the output should look something like

```
username adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin
```

where **username** is your user account name

If you do not see cdrom in the list, you can add yourself to the group with the following:

```
 sudo -a -G cdrom username
```

PS: again **username** is your user account name

---

### Post by Motorhead Kaze on 2008-01-25
Thanks for that bit of code.  Although cdrom was on that list, and didn't fix anything, I will put it into my memory for the future.

Anyone else have an idea how I can fix this problem?

---

### Post by y-lee on 2008-01-26
I was hoping it was something easy :(

Type in a terminal

```
dmesg | grep -i cd | grep -i rom
```

this should identify your devices Now type


```
sudo chmod 777 /dev/scd0
```

- replacing "scd0" with your own device.

Ps if ya get a lot of errors with post output here.

---

### Post by Motorhead Kaze on 2008-01-26
[   31.584642] hdc: DVD DC DW1670, ATAPI CD/DVD-ROM drive
[   32.623641] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   32.623656] Uniform CD-ROM driver Revision: 3.20

Could you be more specific on what you mean by "- replacing 'scd0' with your own device" in the code below?  A name or number that I should be putting in place of scd0 I understand, but I don't know the name.
```
sudo chmod 777 /dev/scd0
```

---

### Post by y-lee on 2008-01-26
try hdc

---

### Post by Motorhead Kaze on 2008-01-26
Hello.

I was just trying some things, these didn't work.

kaze@kaze:~$ sudo chmod 777 /dev/scd0
[sudo] password for kaze:
chmod: cannot access `/dev/scd0': No such file or directory
kaze@kaze:~$ sudo chmod 777 /dev/CD-RW/DVD±RW Drive
chmod: cannot access `/dev/CD-RW/DVD±RW': No such file or directory
chmod: cannot access `Drive': No such file or directory
kaze@kaze:~$ sudo chmod 777 /dev/cdrom0
[sudo] password for kaze:
chmod: cannot access `/dev/cdrom0': No such file or directory
kaze@kaze:~$ sudo chmod 777 /dev/cdrom
kaze@kaze:~$ 
kaze@kaze:~$  sudo chmod 777 /dev/hdc
kaze@kaze:~$ 

The last 2, nothing happened as you can see.

But at very least, now I see where you got "hdc" from.  [ 31.584642] hdc: DVD DC DW1670, ATAPI CD/DVD-ROM drive

---

### Post by mc4man on 2008-01-26
> The last 2, nothing happened as you can see.
Most times when 'nothing' happens that means command was successful, ie. no errors.

---

### Post by y-lee on 2008-01-26
> **Motorhead Kaze said:**
> Hello.
I was just trying some things, these didn't work.



[SIZE="3"][COLOR="Red"]Do Not Randomly try Commands in the Terminal. You can Completely Trash your System doing this!!

This is especially dangerous using the **sudo** command[/COLOR][/SIZE]

> **Motorhead Kaze said:**
> 
The last 2, nothing happened as you can see.



mc4man is right : *Most times when 'nothing' happens that means command was successful, ie. no errors.*

Does K3b still give you the same errors?

---

### Post by Motorhead Kaze on 2008-01-26
Yes, same error message.  Before this I was having troubles even viewing DVD's for a short time.  DVD player just stopped playing them (could still view and burn vcds though).  Now it's just the burning of movies via .cue or .iso files.

And to be clear, I don't randomly try commands as such. The recommendation was to replace the end of the code with my own device.  This was not clear to me, so I attempted to do just that by looking up the name through "Computer" and "Media".  I'm not so foolish that I would just type "Sudo" and then some random "Stuff" after it.

---

### Post by y-lee on 2008-01-26
if K3b is not working.

Is K3b set up right? 

[LIST]
[*]Can you please start K3b, click **Settings ** and then  **K3b Setup**,
[*]Enter  your Password as it should ask you.
[*]Take a screen shot of this window or your desktop and attach it here.
[/LIST]

Also 
[LIST]
[*]Can you please start K3b, click **Settings ** and then  **Configure K3b ...**,
[*]In the **Options-K3b** Window click on Devices
[*]Is your DVD Drive listed there?
[/LIST]

---

### Post by Motorhead Kaze on 2008-01-26
Wow, you're in this overtime, thanks a bunch.

There is a possibility that K3b isn't set up correctly, but when I reformatted Gutsy this week, I got K3b from the repos the same as I did when I formatted my disk with Gutsy last fall.  I didn't do anything special to set it up then, and it worked very nicely.  In fact this DVD player issue only began last week.  This is why I reinstalled Gutsy, figuring something went cockeyed with my player. (Sometimes my machine has freaked out with Ubuntu and hardware just "disappeared" so I've reinstalled.  But all that aside, on to your help:

    * Can you please start K3b, click Settings  and then K3b Setup,
I'm sorry, but I have no option for this in my Settings menu.  I have "Hide menubar, toolbars, hide status bar, show directories, show contents, show document header and configure shortcuts, config. toolbar and config. k3b.  In that order.

    * Can you please start K3b, click Settings and then Configure K3b ...,
But this I do have, and it does appear that everything is fine with my device.

Still, it is 3:30am over here in Osaka, I may be blurry at this point.  I am sending the screenshot of the Configure K3b screen.

Thanks for hanging in there for me, but I'll have to respond in a couple hours!

---

### Post by y-lee on 2008-01-26
*"Im sorry, but I have no option for this in my Settings menu."*

I see you are most likely running a newer version of Kb3 than I am, probably because I'm a dapper user.  I found the below on [another forum:]("http://www.linuxforums.org/forum/linux-applications/39898-k3b-k3bsetup.html")

> i was just hoping to use k3b but i've recently upgraded it and noticed that k3bsetup has disappeared from the Settings menu. 

Do the steps I previously posted and click on Advanced and post a screen shot.  I don't have an advanced tab here but I suspect the info I'm hunting for is found there.

Sadly I just found the below on [Cdrecords official website]("http://cdrecord.berlios.de/private/linux-dist.html")

> [SIZE="2"]**Linux controversy**[/SIZE]
	In autumn 2005 and early spring 2006, a group of Debian maintainers started to attack the cdrtools project.

The attacks have been based on the fact that cdrtools was licensed under the GPL. As a result, on May 15th 2006 most projects from the cdrtools project bundle have been relicensed under CDDL (giving more freedom to users than the GPL does). At the same time, an important amount of additional code (DVD support code from Jörg Schilling and a Reed Solomon decoder from Heiko Eißfeldt) has been added to the freely published sources.

In summer 2006, the attacks from the group of Debian maintainers escalated and in September 2006, these people created something they call a fork from cdrtools. They soon added a lot of bugs and this way turned the "fork" into a questionable experiment. The last work on this "fork" has been done eight months later on May 6th 2007, then the leader of the attacks stopped his efforts.

Although there is no "project" activity on the "fork" anymore since more than 8 months (which is more than the speudo activity period), there are still people who spread incorrect claims on both the original project and the fork. Please help the free original project by correcting these incorrect claims.

[SIZE="2"]**Many Linux distributions now come with broken variants of cdrtools**[/SIZE]

	If you are on Debian, RedHat, SuSE and some other Linux distributions, you need to take extreme care as these distributions recently started to replace cdrtools by a fork that is based on an outdated version of cdrtools. This fork did not fix bugs but rather introduced new bugs that never have been in the original software.

For other Linux distributions, I suggest to have a look at /usr/bin/cdrecord and check whether this is a link to another program or whether there is an original program file. Also call "cdrecord -version" to check what version you are using. The affected distributions replaced all programs from cdrtools (cdrecord, cdda2wav, readcd, mkisofs, ...) by programs from the fork.
How do I find out whether I am running a recent original version of cdrtools?
	Call "cdrecord -version" and check the output. If you see something like:

```
Cdrecord-ProDVD-ProBD-Clone 2.01.01a32 (i386-pc-linux) Copyright (C) 1995-2007 Jörg Schilling
```



Ubuntu is based on Debian so we may have a problem. :( This problem has been [reported]("https://answers.launchpad.net/ubuntu/+source/k3b/+question/21117"). And by the way :

```
uname -a
```

Gives your kernel version.

**edit**

> In fact this DVD player issue only began last week


I did a kernel update about a week ago, and probably so did you. cdrecord and Kb3 still works for me but  I'm running dapper, have different hardware and have only cd r/w unlike you.  I am now suspecting the update is what broke your cdrecord and K3b :(

---

### Post by Motorhead Kaze on 2008-01-26
Ah, good afternoon.  A little sleep and I'm back.  Sorry to disappear.

kaze@kaze:~$ cdrecord -version
The program 'cdrecord' is currently not installed.  You can install it by typing:
sudo apt-get install cdrecord
bash: cdrecord: command not found

kaze@kaze:~$ uname -a
Linux kaze 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
kaze@kaze:~$ 

From here it LOOKS like I don't have that fork thing in my PC.  That is just downright nasty, to click on the update button and suddenly your programs that work stop working.  As I said before, suddenly, with no warning, I stopped being able to use video recording functions, so perhaps it was messed up by a rotten "Upgrade".

Hope this is the menu you wanted to look at.

---

### Post by TheDilettante on 2008-01-26
While not directly addressing your problem, I wanted to interject to say that Kcontrol, while a Kubuntu thing, is available through Synaptic, or apt-get.

---

### Post by Motorhead Kaze on 2008-01-26
Oh hey! Super cool.  Thanks!  Will try Kcontrol too.

Y-Lee:  Just to show I'm not totally lazy, I posted my question in K3b's launchpad too.  Although that avenue make take time.

Is THIS the problem here?

kaze@kaze:~$ cdrecord -version
The program 'cdrecord' is currently not installed. You can install it by typing:
sudo apt-get install cdrecord
bash: cdrecord: command not found

---

### Post by Motorhead Kaze on 2008-01-27
I am now a bit more confused.  I followed this link about Cdrtools and Linux Controversy 

 "...If you are running cdrtools frontends like k3b and others and do not like to replace these programs with original versions, you should remove files like /usr/bin/wodim, /usr/bin/genisoimage, /usr/bin/icedax, /usr/bin/readom and replace them by links to the original software..."

And doesn't clearly state how to do that...for noobs anyway.

My current cdrecord -version is 
Cdrecord-ProDVD-ProBD-Clone 2.01.01a32 (i386-pc-linux) Copyright (C) 1995-2007 Jörg Schilling
and it appears to be an acceptable version.  
K3b is still not working.

"Using Wodim 1.1.6 - Copywrite (c) 2006 Cdrkit suite contributors
starting SAO writing speed at 48x
Cd record has no permission to open device"


Just an update for anyone who is having head-trips with this issue.  I got some advice that didn't fix my problem, but might fix yours!
Go to:  [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
for Feisty and Gutsy users, you'll end up navigating to:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)  to grab the Medibuntu repository.  But heck, since I'm here typing, I'll just post it here:

For Gutsy
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Then, to add the GPG Key:
```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Then to get "libdvdcss2"
```
sudo apt-get install libdvdcss2
```

As for me...this didn't give me "Permission" so I'm just a poor, permission-less waif.  I did a check on my hardware though.  I was a creep and booted into XP, and burned a movie with Nero, just to see.  It worked.  So, why is my beloved K3b treating me this way?

---

### Post by disturbed1 on 2008-01-27
" My current cdrecord -version is 
Cdrecord-ProDVD-ProBD-Clone 2.01.01a32 (i386-pc-linux) Copyright (C) 1995-2007 Jörg Schilling
and it appears to be an acceptable version.  
K3b is still not working.

"Using Wodim 1.1.6 - Copywrite (c) 2006 Cdrkit suite contributors
starting SAO writing speed at 48x
Cd record has no permission to open device""

I hope you noticed that K3b does not use cdrecord, but wodim instead ;)

If you happen to have an iso image or bin/cue file can you try the below -

cdrdao write --device /dev/hdc file.iso

^^ /dev/hdc is the location of your Benq writer as was listed in your previous posts. You will have to change file.iso to the actual name of the iso file. Or if you have a cue sheet, pass that name instead.

Should cdrdao not be installed, go ahead and install it -
sudo apt-get install cdrdao


This is only for CD not DVDs though. If CDs burn fine, good news.

To burn a DVD try this -

cdrecord dev=/dev/hdc file.iso

---

### Post by Motorhead Kaze on 2008-01-27
Oh sh*t~!  No...I didn't notice.  I'm so spazzed out on this, I am not seeing clearly. 

I tried this.  I'm guessing that I need to put the .iso or the .cue file on the desktop first?  I have a .cue right here in fact!

kaze@kaze:~$ cdrecord dev=/dev/hdc Isetour.cue
cdrecord: No write mode specified.
cdrecord: Asuming -sao mode.
cdrecord: If your drive does not accept -sao, try -tao.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'BENQ    '
Identifikation : 'DVD DC DW1670   '
Revision       : '100 '
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
cdrecord: No such file or directory. Cannot open 'Isetour.cue'.

Hmmm...

kaze@kaze:~$ cdrdao write --device /dev/hdc Isetour.cue
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.
ERROR: Cannot open toc file 'Isetour.cue' for reading: No such file or directory

I don't really MEAN to be such a noob...these didn't produce any results.  What did I miss?

---

### Post by rkd on 2008-01-27
Well, the error messages in both cases say the file Isetour.cue doesn't exist.  Either you spelled that filename wrong or it isn't in the directory you were in when you typed the command. 

Remember that filenames are case-sensitive (apologies if you don't need that reminder). Do an ls command to see what filenames are in the directory. If your .cue file is there, note exactly how its name is displayed. Be careful of characters that can be confused with each other, such as capital I, small L, and the number 1.

If the .cue file isn't there, look in the subdirectories until you find where it is. Then either change to that subdirectory or type the complete path to the file.

---

### Post by Motorhead Kaze on 2008-01-27
Hi Rkd,
"Remember that filenames are case-sensitive"  Thanks for the reminder!  

"Do an 'ls command' to see what filenames are in the directory... look in the subdirectories." Ah! Sounds good. How do I do that?

Do you mean 
```
kaze@kaze:~$ Is
bash: Is: command not found

```

"Either you spelled that filename wrong or it isn't in the directory you were in when you typed the command."
I put the .cue file on the desktop. Was I supposed to add a path command to point to that file?  If so, please tell me, what it should be.

These are all new to me, please enlighten me.

---

### Post by y-lee on 2008-01-27
ls as in LIST. Use an l as lowercase "L" :)

Sorry I had to go to sleep earlier, :lolflag: and now I gotta read thru all this and see what I think.

EDIT: Also **man ls** will tell ya more about the ls command than ya probably ever want to know.

works with any command (in theory)

**man *command***

---

### Post by disturbed1 on 2008-01-27
In Linux, the cAsE iS sEnSitivE.  The following all mean 3 different things in Linux. Home != home != HOME. 

The command asked to pass was ls
```

ls
```It's a list command to get the directory listing.

For -
cdrecord dev=/dev/hdc Isetour.cue

You have to define the absolute path of Isetour.cue, or be in that directory. When you launch a terminal, it opens in the path of your home directory
```

/home/kaze
```If Isetour.cue is in a folder inside your home directory called images then you have to do one of the below.
```

cd /home/kaze/images

```The above will **c**hange **d**irectory to the directory images inside your home folder.

```

cdrecord dev=/dev/hdc /home/kaze/images/Isetour.cue
```The above gives the absolute path to the file Isetour.cue.

BE SURE TO CHANGE /home/kaze/images to the real path ;)





-------------------editt-------------------

cdrecord dev=/dev/hdc /home/kaze/Desktop/lsetour.cue

cdrdao write --device /dev/hdc /home/kaze/Desktop/lsetour.cue

---

### Post by Motorhead Kaze on 2008-01-27
Thanks disturbed1 and good morning Y-lee.

Big sigh over my silliness.  Sorry the fact that my file starts with and "I" and I saw that "ls" my brain's font manager saw "Is".  (smile)  Okay, so no, I didn't put the .cue file in a folder, it's just right there on the desktop.  So below, just for the future (any other noobs reading)
```
cdrecord dev=/dev/hdc Isetour.cue
```
```
cdrecord dev=/dev/hdc /home/kaze/Isetour.cue
```
```
cdrecord dev=/dev/hdc /home/kaze/Desktop/lsetour.cue
```
did not work but 
```
cdrecord dev=/dev/hdc /home/kaze/Desktop/Isetour.cue
```
 started the burn process.   Unfortunately, I got another error message:

kaze@kaze:~$ cdrecord dev=/dev/hdc /home/kaze/Desktop/Isetour.cue
cdrecord: No write mode specified.
cdrecord: Asuming -sao mode.
cdrecord: If your drive does not accept -sao, try -tao.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'BENQ    '
Identifikation : 'DVD DC DW1670   '
Revision       : '100 '
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Starting to write CD/DVD/BD at speed 48 in real SAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Turning BURN-Free off
cdrecord: WARNING: Drive returns wrong startsec (0) using -150
WARNING: padding up to secsize (by 1857 bytes).
Track 01: Total bytes read/written: 191/614400 (300 sectors).

I took out the disc, put it back in and now get:
Cannot mount volume.  Invalid mount option when attempting to mount the volume.

Damn. I thought I had it that time.

---

### Post by y-lee on 2008-01-27
Ok I'm a little confused here so let me catch up.

First

> **Motorhead Kaze said:**
> Ah, good afternoon.  A little sleep and I'm back.  Sorry to disappear.

kaze@kaze:~$ cdrecord -version
The program 'cdrecord' is currently not installed.  You can install it by typing:
sudo apt-get install cdrecord
bash: cdrecord: command not found

kaze@kaze:~$ uname -a
Linux kaze 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
kaze@kaze:~$ 



This makes me think cdrecord is not installed or not found in your path statement, but now you appear to be trying to use cdrecord to burn your file for you instead of Kb3, So did you install cdrecord and if so how and what version? 

I also see you installed [ libdvdcss]("http://en.wikipedia.org/wiki/Libdvdcss2")

> libdvdcss is a software library for accessing and unscrambling DVDs encrypted with the Content Scramble System (CSS). libdvdcss is part of the VideoLAN project and is used by VLC media player and other DVD player software such as Ogle, xine-based players and MPlayer.


I don't think it had anything to do with your problem but It will help you play encrypted DVDs always a good thing :)

> **Motorhead Kaze said:**
> I am now a bit more confused. I followed this link about Cdrtools and Linux Controversy

"...If you are running cdrtools frontends like k3b and others and do not like to replace these programs with original versions, you should remove files like /usr/bin/wodim, /usr/bin/genisoimage, /usr/bin/icedax, /usr/bin/readom and replace them by links to the original software..."

And doesn't clearly state how to do that...for noobs anyway.


I had problems with his instructions too.  I was able to compile his programs but it didn't change my current version of cdrecord. I was still linked to the other and I couldn't uninstall it without uninstalling the gnome-destop, K3b and a bunch of other stuff (using synaptic package manger). I was looking around to see if somehow I could change from the old cdrecord to the new just compiled version, maybe use a link or something and somehow KILLED my own K3b. It wouldn't record anymore.:confused:

 Ok now i fixed that one 20 minutes later:lolflag: Still don't know exactly what i did, i usually document what i do but I was tired and decided to rely on my memory. Dumb idea as tired as i was. 

Anyway i think to use the official cdrecord one has to compile it right and stuff. I read thru the read me files included and decided it was more complex than I  wanted to deal with. It is really a set of programs (cdrecord being one of them) designed for [Suns solaris  operating system]("http://en.wikipedia.org/wiki/Solaris_(operating_system)") and not Ubuntu.

regardless I  was thinking a kernel update killed cdrecord for ya and It appears I was wrong on that one :confused:

Ok one more question how did you install K3b. I installed the kde desktop and I think it was included. I really hadn't been using it much untill  I started working on this post. Now i like it:)

---

### Post by y-lee on 2008-01-27
> **Motorhead Kaze said:**
> 
```
cdrecord dev=/dev/hdc /home/kaze/Desktop/Isetour.cue
```
 started the burn process.   Unfortunately, I got another error message:
[CENTER]**. . .**[/CENTER]
I took out the disc, put it back in and now get:
Cannot mount volume.  Invalid mount option when attempting to mount the volume.

Damn. I thought I had it that time.

Ok could you try ```
sudo cdrecord dev=/dev/hdc /home/kaze/Desktop/Isetour.cue

```

based on what I [URL="http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=266009"] just read.
[/URL].

---

### Post by Motorhead Kaze on 2008-01-27
Hey there.  Yes, I spent another full day on this and followed leads, installed more "Stuff" than I really needed to but learned a lot more, despite not fixing the problem.  I installed Cdrecord through the terminal and got this version
```
Cdrecord-ProDVD-ProBD-Clone 2.01.01a32 (i386-pc-linux) Copyright (C) 1995-2007 Jörg Schilling
```
also installed the Medibuntu repo, key and libdvdcss2 as you noticed.  Installed cdrdao too.

I got K3b through synaptic.

The following yielded the same result as my last try:
```
sudo cdrecord dev=/dev/hdc /home/kaze/Desktop/Isetour.cue
```
[sudo] password for kaze:
cdrecord: No write mode specified.
cdrecord: Asuming -sao mode.
cdrecord: If your drive does not accept -sao, try -tao.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'BENQ    '
Identifikation : 'DVD DC DW1670   '
Revision       : '100 '
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Starting to write CD/DVD/BD at speed 48 in real SAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Turning BURN-Free off
cdrecord: WARNING: Drive returns wrong startsec (0) using -150

WARNING: padding up to secsize (by 1857 bytes).
Track 01: Total bytes read/written: 191/614400 (300 sectors).

"Something" is happening though.  Because now both cdrs that I've tried this with are "Unmountable" in Ubuntu and "Unreadable format" in Xp.  So, the discs are now unusable, but that means something started, but can't finish.

Thought I would try this again, since I used an "l" instead of an "I" last time...BUT.
```
cdrdao write --device /dev/hdc/home/kaze/Desktop/Isetour.cue
```

ERROR: Missing toc-file.

Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.


Usage: cdrdao write [options] toc-file
options:
  --device [proto:]{<x,y,z>|device} - sets SCSI device of CD-writer
                            (default: /dev/hdc/home/kaze/Desktop/Isetour.cue)
  --driver <id>           - force usage of specified driver
  --simulate              - just perform a write simulation
  --speed <writing-speed> - selects writing speed
  --multi                 - session will not be closed
  --buffer-under-run-protection #
                          - 0: disable buffer under run protection
                            1: enable buffer under run protection (default)
  --write-speed-control # - 0: disable writing speed control by the drive
                            1: enable writing speed control (default)
  --overburn              - allow to overburn a medium
  --full-burn             - force burning to the outer disk edge
                            with '--driver generic-mmc-raw'
  --capacity <minutes>    - sets disk capacity for '--full-burn'
                            you must specify this when using blanks bigger
                            than 80 min. (90,99,etc.)
                            because they seems like 80 min. blanks
  --eject                 - ejects cd after writing or simulation
  --swap                  - swap byte order of audio files
  --buffers #             - sets fifo buffer size (min. 10)
  --reload                - reload the disk if necessary for writing
  --force                 - force execution of operation
  --tmpdir <path>         - sets directory for temporary wav files
  --keep                  - keep generated temp wav files after exit
  -v #                    - sets verbose level
  -n                      - no pause before writing

...I just wish I knew WHICH TREE to bark up...

I read that bug report you linked to Y-lee.  You understood it, which is commendable.  Haha.  It seems that there is more than Cdrecord that isn't working right.  "I read thru the read me files included and decided it was more complex than I wanted to deal with."  (Amen)  Above, "Disturbed1" mentioned that K3b was using Wodim, but then why the K3b error message regarding Cdrecord?  Other little elusive and evil bits in our systems.

It would be cool if the bug was fixed and put into an update in the next couple days.  Hopefully between the bug reports sent in and the stuff I sent to Launchpad, a fix will be made...for all the evil bits.

I was suspicious of that broken Cdrecord, etc. issue being something that came through the update manager and into our systems, but my best friend just burned a movie with K3b yesterday, and he's using the same K3b with Gutsy that I am, downloading every update the same as me.  It would seem that if something broken came through, his K3b would have broken as well.

Perplexing crap.

---

### Post by y-lee on 2008-01-27
Hmmm it has me puzzled and I'm running our of advice. I'm also learning more about cdrecord than I ever really needed to know. That's a good thing I suppose as I may be able to help other users. I have found out a lot of people are having problems with cdrecord tho, alot of bug reports and forum posts.

It might not help but could you find the file **/etc/cdrecord/cdrecord **and post its contents here. Note** cdrecord** is the files name and **/etc/cdrecord/** is its location. It is a text file ( well a link to a script really) but you should be able to open it in gedit.

Hopefully someone might be able to help you sort this out. Gotta work tomorrow and it's almost my bedtime. I did find [Using cdrskin instead of cdrecord]("https://help.ubuntu.com/community/K3BHowto"), scroll down its near the bottom. Maybe using cdrskin would help. Also are you sure your DVD r/w is working correctly? I found a forum post with the same cdrecord error as yours above where a broken DVD r/w was the cause. :( If you dual boot does it work in windows? If not can any other program burn DVDs for you in Ubuntu?

---

### Post by Motorhead Kaze on 2008-01-27
I want to try one more thing.  Since this really started with me trying to use K3b.  (Although the idea of burning from terminal is pretty sweet).

If I go into Synaptic, delete K3b, and reinstall using
```
sudo apt-get K3b
```
will that do anything at all?  Is the source for the program the same?  Will the versions of Cdrecord (etc.) be the same as what is with the K3b in synaptic?

Also, for my knowledge base, when using sudo apt-get, how do I make sure that dependencies are solved?

---

### Post by y-lee on 2008-01-27
> **Motorhead Kaze said:**
> my best friend just burned a movie with K3b yesterday, and he's using the same K3b with Gutsy that I am, downloading every update the same as me. It would seem that if something broken came through, his K3b would have broken as well.

Perplexing crap.

Perplexing indeed. But your friend probably has different hardware on a different machine. A program can work fine on one machine and not at all on another.  It's a joke with programmers saying *but it works fine on my machine*. lol

> **Motorhead Kaze said:**
> ..BUT.
```
cdrdao write --device /dev/hdc/home/kaze/Desktop/Isetour.cue
```

ERROR: Missing toc-file.



Hmm 

> 
cdrdao command [options] toc-file

Write all content specified in description file toc-file to a CD-R disk drive in one step. This is called disk-at-once (DAO) mode, as opposed to the more commonly used track-at-once (TAO) mode. DAO mode allows you to change the length of gaps between tracks and define data to be written in these gaps (like hidden bonus tracks or track intros). The toc file can be created by hand or generated from an existing CD using cdrdao's read-toc command. A cue file, as generated by other audio programs, can be used instead of a toc file. The file format for toc files is discussed at length in the cdrdao manpage.


Apparently cdrdao needs a toc-file created before one can use it like that.

Try
```
man cdrdao
```

for all the dirty details :confused:

>  The toc-file describes what data is written to the CD-R and allows control over track/index positions, pre-gaps and sub-channel information. It is a simple text file, use your favorite text editor to create it.

ALSO

>  Cue  files  may  be used wherever a toc-file is expected. The corresponding bin file is not taken from the FILE statement of a cue file but constructed from the cue file name by replacing ".cue" by ".bin". The cue file must have exactly one FILE statement.


---

### Post by y-lee on 2008-01-27
> **Motorhead Kaze said:**
> I want to try one more thing.  Since this really started with me trying to use K3b.  (Although the idea of burning from terminal is pretty sweet).

If I go into Synaptic, delete K3b, and reinstall using
```
sudo apt-get K3b
```
will that do anything at all?  Is the source for the program the same?  Will the versions of Cdrecord (etc.) be the same as what is with the K3b in synaptic?

Also, for my knowledge base, when using sudo apt-get, how do I make sure that dependencies are solved?

Just go into synaptic and mark it for reinstall and then apply to reinstall it. see if it helps.

---

### Post by Motorhead Kaze on 2008-01-27
Y-lee, you've been very supportive,I'll read that link you sent. Mc4man, thedilettante, disturbed1, rkd thanks to you too.There was much learned here, I'm sure once this is figured out I will also be more help to others. 

In the meantime, cdrecord isn't found in etc.  So...?  I have it because cdrecord -version says I do.  And I see it in bin/cdrecord

Ah yes, I reinstalled K3b from synaptic before even starting this 3 day post marathon.

---

### Post by mc4man on 2008-01-27
It might not hurt to say what exactly  it is your trying to burn.  what was the original  source and how did you create what your trying to pass along to k3b or cdrecord

---

### Post by y-lee on 2008-01-27
> **Motorhead Kaze said:**
> In the meantime, cdrecord isn't found in etc.  So...?  I have it because cdrecord -version says I do.  And I see it in bin/cdrecord

Ah yes, I reinstalled K3b from synaptic before even starting this 3 day post marathon.

What is in bin is an executable (ie the actual program) probably. Your machine is set up differently than mine, probably because i use dapper. maybe because I compile a lot of apps. Anyway I'm out of ideas for now and off to bed. I'll think more and be back on after work tomorrow, assuming I work (depends on weather as I'm a mason)

> Y-lee, you've been very supportive

Ah, I'm here to help. I'm actually new to linux and ubuntu too. I learn by helping people and playing on my own machine. :)

---

### Post by Motorhead Kaze on 2008-01-28
As I mentioned above (albeit this is a 4 page discussion now) I was trying to burn at first an .iso file then a .cue file of home movies.  The .cue file was 200Mb.  The original source was .mp4s converted to .iso and .bin/cue by ... Kino if I recall correctly.  I had previously burned both (separate instances of course) using K3b.  And as part of this week's K3b problem, I used the other OS installed in this PC, Xp, to burn both the .cue file and the .iso successfully - just yesterday.

(In case anyone is going to ask, "Why do you care then, if XP does it for you?" it is because I no longer use XP for my computing.  It is there for instances like this, where I need to check out hardware in another OS, etc.)

---

### Post by mc4man on 2008-01-28
I've got a test box that has a fresh install and I'd thought I'd fool around with k3b, so it's good to know what you were working with. In this particular case you are trying to burn to a cd?

---

### Post by Motorhead Kaze on 2008-01-28
Yes, trying to burn a .cue file or an .iso file onto a CD.  But, if you noticed in this post, I made allusions to my 1st trouble which was that K3b would no longer copy DVDs for me.  Just stopped one day.

Test machine, meaning that Ubuntu isn't your main, or that you just have a separate Gutsy machine?

K3b was really awesome for nearly a year, on both Feisty and Gutsy.  A similar thing happened to Kdenlive.  It was working cool, but it hates Gutsy. So, really waddayagunna do?  I am not the type of person who enjoys using 2 OS's.  I prefer Ubuntu now, but sometimes the convenience of updates is too convenient and I don't look at them...not knowing what I'm looking at... and sometimes good programs just get messed up.

---

### Post by mc4man on 2008-01-28
My main pc is gutsy but rather than screw things up I test, compile, screw up,  ect. on an extra box. I don't mind setting it up to try to mimic or reproduce someones issues or too look at how apps work on a fresh install vs. the point me or someone else has gotten themselves into. Like y-lee it's getting late here, I'm creating what I hope is a similar type video now, will see what gives after work tommorrow

---

### Post by rkd on 2008-01-28
This might not help anything, but I'm pretty sure you made a typo in the command you showed in post #27.

The command you show is:
```
cdrdao write --device /dev/hdc/home/kaze/Desktop/Isetour.cue
```
and it looks like you ran together the device name and the .cue file name. I think it should be:
```
cdrdao write --device /dev/hdc  /home/kaze/Desktop/Isetour.cue
```
Running the two names together would make cdrdao think you had not specified the .cue file, which is what it might mean when it says in the error that the toc-file is missing. (toc-file may mean table of contents file, and I think the .cue file is something like a table of contents.) It would have taken the one long, run-together name as the device name.

And just to make your typing a little easier, when you open the terminal, you are in your home directory, so you can shorten the filename of the .cue file thus:
```
cdrdao write --device /dev/hdc Desktop/Isetour.cue
```
The two forms of the filename are equivalent, when you are in your home directory. The longer name is a little safer to use since it always works, no matter which directory you are in. It is up to you whether to use the shortcut or not.

I don't have any experience with these programs, so I can't help with them, specifically. I was just looking at the thread to see whether I could learn something about K3b.

---

### Post by Motorhead Kaze on 2008-01-28
Thank you for the typing lesson.  This is what makes *other* people hate the terminal.  In a gui, if you miss your "click" you can click again.  In terminal, you miss a space, or add one and boy... but I'm clear now.  Also it was mentioned that I hadn't put the .bin file on the desktop.  I hate posting when it was ME who forgot something...but gotta be honest.  

```
cdrdao write --device /dev/hdc Desktop/Isetour.cue
```
The Cd is spinning...something is happening...

Oh yeah!  There we are, riding our motorcycles through Ise Japan!  (The burn was a success!)

Disturbed1, sorry buddy for messing up the code you gave me.
Rkd, you done a good thing.  Walk over to the mirror and say, "I rule".
Like I said, my friend is using K3b just fine, so it might work on your machine too.  I've been using it all year and thought it was awesome.

So, this proves that my DVD player is just fine with Ubuntu too.  Something with Cdrecord (perhaps Wodim?) is not working.  I will include this with my report to the Launchpad.  (odd though, the vcd I just made won't play on my PC, but plays great on my Television. I'll figure that part out later.)  For now...

:KSOooowwww!!!!:KS

---

### Post by disturbed1 on 2008-01-28
Always, always use cdrdao for burning VCDs, SVCDs.

To play the VCD on the PC use VLC. Choose File -> Open Disc. On that screen, tick VCD, at the bottom make sure /dev/hdc is listed. So if it says vcdx:///dev/cdrom just replace cdrom with hdc.

There is no bug, you just didn't burn the image correctly ;) VCDs and SVCDs need to be written either in DAO or SAO mode. K3b should have the option to change write modes.

---

### Post by rkd on 2008-01-28
I'm glad to see that fixing the typo allowed you to get a video written.  I'm glad I could help.

Here is another tip that might help you sometime: You can avoid typos by copying a command someone gives you in a post (highlight the command with the mouse, right-click and select copy), then go put the mouse pointer into the terminal window and click the middle button (or the scroll wheel). That will paste the command into the terminal window. Push the Enter key to run the command. (I think there are variations on how to copy the text and paste it -- I'm just describing how I do it. Any other way of copying and pasting should accomplish the same thing.)

I did a little web searching with Google, and I came across the  same explanation of a controversy about cdrecord that y-lee quoted in post #13. From what I read there, I think there is a fairly good chance that we can get a working cdrecord installed on your system.  (There seem to be packages of the working cdrecord available for use with the package manager.) And I think that would allow us to get K3b to work again.  The details of what has to be done aren't completely clear to me, so I would have to experiment on my test system to work out the exact steps.  Are you still interested in getting cdrecord and K3b to work, or have you found some substitute for writing DVDs that you are happy with?

---

### Post by Motorhead Kaze on 2008-01-28
Hello,
Of course!  I find K3b to be very useful most times and don't want to give up on it.  Of course, I also really enjoy the process of getting things to work too.
So yeah, if you're up to it so am I!  I read the cdrecord homepage and saw a short list of things they thought I should delete, but didn't understand what they wanted me to put in their stead, or where.
Thanks again.

Disturbed1 (Awesome handle.  Though I feel that I should start with "Oh")  You are right, I should be able to chose my write mode in K3b.  I'll spend some time looking at it.  Thanks for the tip.  I like that I learned another option on burning today.  Guis are super handy, but knowing how to work the terminal is good too. (Old school Linux users must have code embedded in their brains.)

---

### Post by mc4man on 2008-01-28
@ Motorhead Kaze Glad to see your up and riding again. While it's been years since i made a vcd, k3b worked fine. (the first attempt from an iso was a utter failure - audio, no video). While my source was different (no camcorder, reauthored first half of death proof into new video_ts) possibly it's the same idea.I used avidemux to convert the video to vcd format. If I took that output and created an iso k3b would gladly burn it with results noted above. What worked very well was to open the converted avi in kb3 as a new video cd project, allow kb3 to create a bin/cue and then burn. The cd works fine on pc and on sony standalone. Did not have to install cdrecord, only vcdimager.
Personally I only use dvd's for video's, (imgburn in wine or built in cd/dvd creator) but the image quality of the cd was better than I expected

---

### Post by Motorhead Kaze on 2008-01-29
K3b will turn .avi into .bin/.cue files?!!  Damn!  Honestly, when I moved from Winders to Ubuntu, I gave up on .avis.  The circus of trying to get an .avi through DeVeDe (aka the busted-***--mencoder-drama) and into a file type I could burn with K3b was seriously annoying.

When I was in the Gates Box, I always used Nero, and had no idea it was converting vids before making movies.  I always thought DVDs were being created directly from my .avis.  Anyway, when I moved, I started focusing my sites on .bin/.cue or .iso to make movies.  To bore you some more, when I made motorcycle touring vids on .mp4, I put them into Kino, saved them as .dv and converted them to .bin/.cue with DeVeDe and burned em with K3b.  Still, far too many conversions and trouble for my taste.

It would be very cool if there were ONE program for all that, but it would cost a lot I reckon.

Sorry I got distracted.  So, to repeat the important question:  "K3b will turn .avi into .bin/.cue files?"  I will definitely look into that.  

P.S. Yes, I usually use DVDs for video too.  But for short home videos there really isn't much point in using a full DVD.

---

### Post by biocyberman on 2008-01-30
> **y-lee said:**
> I was hoping it was something easy :(

Type in a terminal

```
dmesg | grep -i cd | grep -i rom
```

this should identify your devices Now type


```
sudo chmod 777 /dev/scd0
```

- replacing "scd0" with your own device.

Ps if ya get a lot of errors with post output here.

Typing following command in terminal gave me nothing, what should I do?

```
dmesg | grep -i cd | grep -i rom
```

---

### Post by y-lee on 2008-01-30
biocyberman, What does

```
dmesg 
```

give you?

---

### Post by McDuff on 2008-01-30
i found a solution for one of the problems described in the op. with me, k3b refused to copy encrypted dvds. following this thread i found out that here it is set to use wodim instead of cdrecord as well. so i went to settings > configure k3b > programs > user parameters and set the path to cdrecord as parameter: ```
/usr/bin/cdrecord
```
now k3b is copying my dvd without complaining

---

### Post by Motorhead Kaze on 2008-01-31
McDuff...an extra serving of "Oh yeeeaah!" for you!  That did it for me!  I just successfully used K3b to burn a DVD from an .iso  and am copying a DVD now.  Got the warm and fuzzy feeling again.
Disturbed 1 also mentioned "K3b should have the option to change write modes" and you were both right.

Running cdrdao from the terminal is wicked for vcds though.  Disturbed1, why did you say "Always, always use cdrdao for burning VCDs"?  Or why is it your favorite should I say? 

ANYWAY! K3b works again!  Thanks to everyone who gave so many options and put time into working this problem.  Although it turned out to be as simple as typing /usr/bin/cdrecord into a BOX,  I learned a lot.

---

### Post by biocyberman on 2008-01-31
> **y-lee said:**
> biocyberman, What does

```
dmesg 
```

give you?

Sorry, I after rebooting I got this content: 

```
[   22.112514] Uniform CD-ROM driver Revision: 3.20
biocyberman@gusty:~$ dmesg | grep -i dvd | grep -i rom
[   21.574613] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
biocyberman@gusty:~$ sudo dmesg | grep -i cd| grep -i rom
[   21.574613] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[   22.112514] Uniform CD-ROM driver Revision: 3.20
[   22.112576] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   68.731121] cdrom: This disc doesn't have any tracks I recognize!

```

---

### Post by McDuff on 2008-01-31
> **Motorhead Kaze said:**
> McDuff...an extra serving of "Oh yeeeaah!"
well, i have to thank you! without this thread i wouldn't have found this solution. at least not that quickly.

---

### Post by disturbed1 on 2008-01-31
cdrecord doesn't always right in true DAO (disc at once) mode it will try SAO (session at once) or even TAO (track at once) which isn't exactly the best thing for (S)VCDs. CDRDAO will write the complete disc in one go. 

If you look at the cue sheet for a (S)VCD you'll notice it defines more than one track. I've had cdrecord flake out on me a few times by only writing one track then exiting because it attempted to do TAO.

When I started using linux there wasn't a burning GUI besides X-CD-Roast, and burning was not possible unless you were root. Cdrecord required a key to write DVDs larger than 1gig. So it just became easier to script together a few scripts for Rox-Filer or jump to xterm to burn a quick CD. For me, I can type in the commands faster than I can launch a GUI, wait for it load, choose the type of image I want to burn, browse to the files/image, set options, click burn.

Sometimes it's just better to do things in the command line, that way I have complete control, and can watch for any problems that might arise.

Like when I burn karaoke CDs -
cdrdao write --device /dev/sr0 --speed 24 --driver generic-mmc-raw --eject disc.toc

For karaoke you need to use raw mode to write the subchannel data.

---

### Post by Motorhead Kaze on 2008-02-03
Thanks for the lesson on nomenclature.  I am a little silly in that I was thinking "Tao" not T.A.O.  Well, I spend far more time on Eastern philosophy than on my computer so ...

Yes, there wouldn't be many guis back then would there?  You were using Linux when it really WASN'T noob friendly though.

Thanks once again to everyone.

---

### Post by Spike-X on 2008-03-17
> **McDuff said:**
> i found a solution for one of the problems described in the op. with me, k3b refused to copy encrypted dvds. following this thread i found out that here it is set to use wodim instead of cdrecord as well. so i went to settings > configure k3b > programs > user parameters and set the path to cdrecord as parameter: ```
/usr/bin/cdrecord
```
now k3b is copying my dvd without complaining
This solution worked for me (once I installed cdrecord) - I was getting the 'no permission to open device' error when trying to burn a CD from a .cue file. Thanks!

---

