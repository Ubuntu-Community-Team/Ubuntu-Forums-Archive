---
title: "[SOLVED] busybox V.1.3"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by tadcan on 2007-11-04
I am using 7.10

I put in the CD I get the busybox V.1.3 message. I've done searches on the forum and am seeing very differen't answers. Can anybody who has solved this problem tell me how?

I have two DVD drives, both give me the same result. I put the CD into another PC and I was able to run 7.10 with the liveCD. It looks great, I really really want to use ubuntu. :(


Athlon x2400+ 2.01Ghz 1GB ram, 80 GB HD runing XP SP2

---

### Post by hockey97 on 2007-11-05
I have the same problem but a little different, I have ubuntu installed on my computer and was following a tutorial for mail servers and ended up downloading and installing busybox.

I now only have busybox loading and now my ubuntu.

to me it lookes like we have no solution, to it, I asked around and they told me I have to reinstall it.

Tell me if you found out the solution.

---

### Post by tadcan on 2007-11-09
Since I had the same issue with 7.04  and started a thread for that I should have kept to it. I think someone posted on that and said try burning the CD at a slower speed. So I burned it at 1x speed with the same result. 

I remember one sugesstion I read a few months back was to remove one of the CD drives. Which seems to be simialar to the story of having one CD try open when you turn on the machine. 

Anyway Still hoping that someone has an answer. Otherwise I'll try again when I get a new machine in maybe four months time.

---

### Post by tadcan on 2007-11-15
ok, I uplugged the cables for the first dvd drive and put them into the second. Checked the Gusty CD worked in XP. The cd didn't run but opened into its componants. I found the wubi icon, clicked on that and reboot. Still got the same busybox message. The only differance was that the PC  now thought ubuntu was installed and asked me to choose an OS. 

I 'uninstalled' ubuntu with wubi afterward!

---

### Post by dwhitney67 on 2007-11-15
Just so you know, Busybox is a multi-binary that emulates many of the common utilities found on Linux distros.  It is not an error message, but a tool.  IMO, the original developer should have chosen a better name for their product.

Anyhow, Busybox will provide these and other commands:

[LIST]
[*]ls
[*]more
[*]find
[*]chmod
[*]chgrp
[*]mount
[*]umount
[*]etc, etc.
[/LIST]

P.S.  In the "old" days, burning a CD at slower speed was necessary, but nowadays with buffering of data, the likelihood that a CD is bad due to burning at a high-speed is remote.  Since I have not observed first hand the issue all of you have reported (i.e. the Busybox problem), I cannot comment further.  However, I doubt it is your CD.  I use Busybox for my installation CD, and like I said earlier, it is just a tool... a tool that takes up less space on a CD than the traditional tools.

---

### Post by tadcan on 2007-11-19
So why is this tool activated on my PC and not on the other one I tried it on. Is there a command line I can enter to by pass this?

---

### Post by jaybombalous on 2007-11-19
If the cd does not boot to a live desktop then the cd isn't loading. When u get the busybox login thing its because something went drastically wrong. I wouldn't even try to install ubuntu on that computer and on the same hd as xp until u figure out your hardware setup.

When I have problems booting, I start right at the beginning. Meaning, u unplug everything u don't need to run a pc and then try the CD again. If it works u start plugging **** back in till it stops working again. 


I would also try the **alternate desktop CD ISO** if the liveCD does not work.

---

### Post by JBAlaska on 2007-11-19
I just had this problem on a HP pavilion, it has to do with the IDE chipset (jmicron I think). After much searching and whining I found that adding ```
all_generic_ide
``` to the end of the boot string (F6 I think on the install menu) will allow you to complete the install.

Then you have to add ```
all_generic_ide
``` to the boot string in grub to let Ubuntu boot normally after the install.

---

### Post by tadcan on 2007-11-19
I pressed F6 and got the below, which I added the code to

Boot options t=casper initrd=/casper/initrd.gz quiet splash - - all_generic_ide 

Then the bar came up to load the linux kernal, the ubuntu screen came up and then I was back in the busybox page. So after some failed tries I got 

/bin/sh:all_generic_ide not found

I'll try again later. Did I do it correctly?

---

### Post by tadcan on 2007-11-23
Ok I've tried again. As well as the previous message I also get this 

(initramfs) [    186.095620] atal.01: exception Emask 0xO SAxt SErr 0x0 action 0x2 frozen
                                             atal.01:    
the code then keeps changing with different number sequences in the brackets, with the numbers incressing.  ?

The line always ends in Buffer I/O error on device sda, logical block 0

Not sure if that makes sense/ is enough info?

Oh and that time I tried to install with wubi

---

### Post by dwhitney67 on 2007-11-23
Originally I only got involved in this thread to explain what BusyBox was about.

Unfortunately, it would seem that you have not progressed very far.  I sparingly use Ubuntu, so I cannot comment much on it.  I would, though, recommend that you try downloading the Ubuntu ISO, verify that it has the correct SHA1SUM, and then burn it to a CD-R.  Or, and this is just me, I would dump Ubuntu and get a different distro... for example, Fedora.

---

### Post by tadcan on 2007-11-23
I was thinking of trying another linux. 

Does the problem exists with Sata HDDs?

---

### Post by tadcan on 2007-11-27
I was thinking about the problem and came up with the following theory. 

If I new which type of HDD didn't cause Ubuntu to divert to busybox I could buy that copy my current HDD over to it. Then install Ubuntu. 

If I don't end up buying a new machine in a few months I might give it a go.

The question is has anyone investigated which type of HDD cause the problem?

---

### Post by tadcan on 2007-11-30
I am downloading the alternate CD. I know its more advanced, but could be a way of by-passing busybox.

Is this possible or am I clutching at straws?

---

### Post by dcclabough on 2007-12-02
I am having a similar problem.  I successfully installed Gutsy from the live cd, but I keep booting into busybox.  This was a clean install of i386 7.10, but I was running x64 7.10 for weeks/months and never encountered busybox once.  Prior to that, I was running Edgy for over a year (i386) with no relevant issues.  I am going to attempt to reinstall from the alternate cd, but I think it might have something to do with i386 Gutsy and not my hardware.  

I have an AMD XP 3800+, a 250 gb SATA (1 ntfs partition for XP, a swap, 1 ext3 for file system, and a large fat32 for shared linux/windows file storage), 1gb gskill ddr2, and a pny geforce 8500gt on an Asus m2n4 x16 sli mobo.  

I do have 2 screens connected to my machine, which I suspect could be the source of the problem, but when it booted the live CD both screens worked.  (cloned display - I didn't do anything to make it work... just booted that way)

Will post an update after I try the alternate CD

---

### Post by tadcan on 2007-12-02
Please do post the result. My internet connection is broken. It will say the file is downloaded even though I only have a portion of it. I have started using Deluge to get files via Bit Torrent, but it takes a few days.

I have had the same problem with Gos and Mint linux which are all from Debian. The busybox mentions Debian in brackets in the first line.

Knoppix works, except they dont have wireless out of the box yet. I found a 20 step plan to get it working. Someone else posted the same issue on there forum. The (paraphrased) response was, post 1) Here is the how to, post 2) Knoppix is not for noobs, post 3) Get Ubuntu......

I got opensuse10.3 which got some good reviews in the other OS talk. If that works I'll probably dual boot to that instead.

---

### Post by dingclancy on 2007-12-16
yep me too and i do not want to try another distro..

I had ubuntu for a month... then had a RAMDISK error (Kernel Panic) - formatted the HDD and tried to reinstall from the livecd... boom! BusyBox.

I mean it does not make sense. I formatted the HDD so the LiveCD should just have walk through it.

I think that is one myth debunked for me - Ubuntu does need a reinstall just like XP.

Anyway, I am downloading another iso hoping that it is just a CD problem. 

Help!

---

### Post by dingclancy on 2007-12-16
yep me too and i do not want to try another distro..

I had ubuntu for a month... then had a RAMDISK error (Kernel Panic) - formatted the HDD and tried to reinstall from the livecd... boom! BusyBox.

I mean it does not make sense. I formatted the HDD so the LiveCD should just have walk through it. I think this has something to do with the X window interface having an error

Anyway, I am downloading another iso hoping that it is just a CD problem. 

Help!

---

### Post by tadcan on 2007-12-19
Opensuse 10.3  just hung as the live CD was setting up. I know its supposed to be slow but 30 plus minutes is a bit long.

I will put on Fedora 8 as soon a s I get my PC to see my new hard drive... One problem after another. 

Since we both have AMD processors, maybe that's where the problem lies?

---

### Post by Calash on 2007-12-19
I have seen this on PPC based systems, where it seems to have issues connecting the drive.

I am not sure if this will help for this issue, but it is worth a try :)

When you get to the busybox prompt, type 
```

modprobe ide_core

```

it should come back to the prompt.  Then type 

```

exit 

```

and see if it continues to boot.  You can go to the PPC forum to look up the details on the commands, but as I understand them it loads the ide_core module so it can use that chipset, then exits.  If this helps your problem then this may be a related issue.  If not...well...good luck ;)

---

### Post by tadcan on 2007-12-20
I typed in modprobe ide_core

Got (iniframfs) /bin/sh: modprobe not found

---

### Post by Calash on 2007-12-21
I think I got my dash wrong.  Try

```

modprobe ide-core

```

From this page
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Like I said I have no idea if this will help, but it is worth a try.

---

### Post by tadcan on 2008-01-26
Opps I didn't check for an update.

I tried out the code in that page. I did typed 'modpobe ide-core' then 'exit' which resulted in a new line without (iniramfs) so I wasn't able to tpye anything in. The cursor just flashed. 

I tried the ' break=top' and 'live break=top', which didn't help either.

I checked the other Known issues on the wiki, nothing else mentioned the issue.

---

### Post by tadcan on 2008-01-28
> **tadcan said:**
> I was thinking about the problem and came up with the following theory. 

If I new which type of HDD didn't cause Ubuntu to divert to busybox I could buy that copy my current HDD over to it. Then install Ubuntu. 

I just installed fedora 8 on a new  hard drive, then remembered my above question. I put in the live CD, lo and behold it worked. It didn't see mynetgear WG 311  ethernet despite it being supported. 

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

However I suspect when I put the old hard drive back in the same problem will happen. 

The new hard drive is a seagate.

---

### Post by rennu on 2008-02-28
> **tadcan said:**
> I pressed F6 and got the below, which I added the code to

Boot options t=casper initrd=/casper/initrd.gz quiet splash - - all_generic_ide 

Then the bar came up to load the linux kernal, the ubuntu screen came up and then I was back in the busybox page. So after some failed tries I got 

/bin/sh:all_generic_ide not found

I'll try again later. Did I do it correctly?

You'll need to move all_generic_ide _BEFORE_ --

So the correct line would be:

**Boot options t=casper initrd=/casper/initrd.gz quiet splash all_generic_ide -- **

At least this worked for me.

---

### Post by coggz on 2008-03-10
WOW! 
Thanks so much, that boot line works perfectly on my old machine!
> Boot Options: boot=casper initrd=/casper/initrd.gz quiet splash all_generic_ide --
Thanks, 
Luke

---

### Post by tadcan on 2008-03-10
Glad my thread helped somebody. 

Bit late for me now since I have a new machine that I can install Ububtu on. Wow its been a year since I tried to install. Still giving it a try.

---

