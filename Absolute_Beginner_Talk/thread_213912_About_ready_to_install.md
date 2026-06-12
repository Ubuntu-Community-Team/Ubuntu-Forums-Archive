---
title: "About ready to install"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Talisker on 2006-07-11
Hi
I'm about ready to install Dapper on my Laptop.

I spent the last couple of days browsing the forum and I think I got most info I was looking for.

Still, a few questions remain:

[COLOR="Red"]1)[/COLOR] I have a 60 Gig HD in my Laptop. I made 2 partitions one for windows 40Gig (NTFS) the other one is still RAW (should be 20 Gig, Windows shows it as 16 Gig?).
I assume the Dapper installer will recognize thr RAW partition and format it to Ext3?

[COLOR="Red"]2.[/COLOR] I plan on 3 partitions, a Home/shared files, Ubuntu and Swap. I would like to avoid the Fat32 partition and use FS-Drive instead.

I think SWAP should be twice the size of the memory? In my Case 1 gig memory -> 2 Gig Swap?

How much space do I have to allocate to Ubuntu? I assume all applications are installed in that partition?

3. The last question (for now ;) )
Installing Dapper after WindowsXP should add the GRUB to it? So, Dual boot should be installed automaticly?

I appreciate your help, thanks

---

### Post by Rule on 2006-07-11
1.ubuntu will install on the free space that you made for it.
2. imo 2gigs would be a lil much 1 or 1.5 gigs should do
3.yep it will dual boot 

:mrgreen:

---

### Post by user1397 on 2006-07-11
> **Rule said:**
> 2. imo 2gigs would be a lil much 1 or 1.5 gigs should doeven 1 or 1.5 Gigs is excessive in my opinion, unless you plan to run some crazy xgl or ram-intensive program, 512 MB or even 256 MB of swap would do fine.  (i have 1 GB of ram and only have 256 MB of swap, and it barely gets used ever.)
[quote=Rule]3.yep it will dual boot [/quote]well, you would have to add a menu entry for windows in your /boot/grub/menu.lst file, you can find plenty of guides on that here in the forums.

---

### Post by Talisker on 2006-07-11
ok, lets say 1.5 gig for SWAP. That would leave me with about 16 Gig for the Ubuntu partition and the Home/Shared Files partition.
Should I just split the remaining space between them?

---

### Post by molly_001 on 2006-07-11
> **Talisker said:**
>   [COLOR=Red]1)[/COLOR] I have a 60 Gig HD in my Laptop. I made 2 partitions one for windows 40Gig (NTFS) the other one is still RAW (should be 20 Gig, Windows shows it as 16 Gig?).
I assume the Dapper installer will recognize thr RAW partition and format it to Ext3?

Assuming that you are using the desktop LiveCD version: yes, it will install into that empty unpartitioned place for you.  As you probably know, if you want the /home separate, it is best to use the text installer on the Alternate Install CD.  The text installer of the Alternate CD will give you much more control over the creation of your ext3, your separate /home, and your swap.

> **Talisker said:**
>  2) How much space do I have to allocate to Ubuntu? I assume all applications are installed in that partition?

3GB is the minimum, but of course you want more.  After Ubuntu install and updates, you will probably want to go for automatix to round out a beautiful desktop package.  Therefore, I would suggest at least 5GB.

> **Talisker said:**
>  3. Installing Dapper after WindowsXP should add the GRUB to it? So, Dual boot should be installed automaticly?

Using either the liveCD or alternate install CD, it should configure itself automatically for a dual boot.  Even if it did not do so, you could fix it in GRUB menu.lst easily.

Of course, before doing anything, ANYTHING, at all from here, you will make a 100% backup of all data.  This is essential.  The install process for Ubuntu can still be iffy.

---

### Post by Qrk on 2006-07-11
If you don't plan on trying out a lot of applications, / should only need to be 5 GB. But if you want to try KDE or another desktop, maybe Xgl and some other neat stuff, you'll want a little more. I usually use 10 GB for ubuntu / and the rest for home.

---

### Post by Talisker on 2006-07-12
Wow, great info.

I guess I download the Alternate CD as well and give it a shot.

Guess I'll make following partitions:
512 for SWAP
12 Gig for Dapper
the Rest for Home
I assume that should give me room to play with the applications.

BTW, is the Desktop-CD and the LIVE-CD the same when downloading  Dapper? I think the older version had 2 separate CD's.:-k

---

### Post by -deadcats on 2006-07-12
Good advice all-round so far. Remember that your 60-gig drive isn't really 60 gigs. The way hardware manufacturers figure it, a gigabyte is 1000-cubed bytes. But a gigabyte is really 1024-cubed. So what the drive manufacturer CLAIMS as 60 GB, is actually substantially smaller. (55.8 GB)

Interesting Factoid: 
Did you know Bill Gates missed this Computer Bowl question (around 1994, if I remember right); "How many bytes is one megabyte?" He answered 1,000,000 bytes. But he was wrong and he lost, because one kilobyte is 1,024 bytes, and one megabyte is 1,024 x 1,024 or 1,048,576 bytes.

---

### Post by user1397 on 2006-07-12
> **-deadcats said:**
> Good advice all-round so far. Remember that your 60-gig drive isn't really 60 gigs. The way hardware manufacturers figure it, a gigabyte is 1000-cubed bytes. But a gigabyte is really 1024-cubed. So what the drive manufacturer CLAIMS as 60 GB, is actually substantially smaller.

Interesting Factoid: 
Did you know Bill Gates missed this Computer Bowl question (around 1994, if I remember right); "How many bytes is one megabyte?" He answered 1,000,000 bytes. But he was wrong and he lost, because one kB (kilobyte) is 1,024 bytes, and one mB is 1,024 x 1,024 or 1,048,576 bytes.i just wish they could make bytes based off of 10 and not 8 or w/e they use

---

### Post by user1397 on 2006-07-12
> **Talisker said:**
>  BTW, is the Desktop-CD and the LIVE-CD the same when downloading  Dapper? yes

---

### Post by Talisker on 2006-07-12
Alright, thanks for the help everybody! :D

---

### Post by Rule on 2006-07-12
> **erik1397 said:**
> even 1 or 1.5 Gigs is excessive in my opinion, unless you plan to run some crazy xgl or ram-intensive program, 512 MB or even 256 MB of swap would do fine.  (i have 1 GB of ram and only have 256 MB of swap, and it barely gets used ever.)
well, you would have to add a menu entry for windows in your /boot/grub/menu.lst file, you can find plenty of guides on that here in the forums.

I didnt have to edit my menu.list when I dual booted my laptop with XP I never have had to actually weatehr it was SuSE, Red Hat or Mandriva.

---

### Post by user1397 on 2006-07-12
> **Rule said:**
> I didnt have to edit my menu.list when I dual booted my laptop with XP I never have had to actually weatehr it was SuSE, Red Hat or Mandriva.well then you are very lucky, because some people do have to do that extra step.

btw, your sig is from that movie bulletproof monk, right?

---

