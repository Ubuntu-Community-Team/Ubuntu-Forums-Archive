---
title: "Reinstall UBUNTU"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by harakiri on 2006-07-13
hi all,
i hav been using ubuntu frm almost 6 months widout a single crash or a problem.. 
now i want to reinstall ubuntu as i feel my comp boot time has increased drastically. so to remove all prog that i installed and are now un-necessaary. i hav very imp files in my home directory.. i donot want to go thru the pain of taking a bak-up. so is thr a way to install ubuntu widout harming any home directory files?
 :-k 
thx in advance.. 
ubuntu roxs..
harakiri
p.s. i hav only ubuntu and not windows.. i mean its not a dual boot system.

---

### Post by Tweek84 on 2006-07-13
I know there is the option when installing ubuntu to leave the exsisting filesystem in tact. I presume that wouldn't touch your home folders then.

However as an aside if the files are important it sounds like you may be setting yourself up for a pretty common folly. I'd go through the 'trouble' of backing that data up to an optical medium so you have it if something bad happens.

---

### Post by uzi09 on 2006-07-13
well, if you installed ubuntu so that you have a seperate partition for home, you could pretty much just wipe out the root partition and re-install in it and have all your data still there.

you may also want to look through the 'How-To's Tips and Tricks' section of these forums. there have been numerous threads that show you how to speed up your system.

---

### Post by aysiu on 2006-07-13
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by harakiri on 2006-07-14
thx a lot all.. now ill try the seperate home creation but aiysu... i didnot understand wat the following meant 
> This guide is for creating a separate /home partition if you already installed Ubuntu without a /home partition (i.e., /home is just a folder inside your / partition)
how can an installation not have /home.. linux creates /home automatically.
can u clear this for me?

---

### Post by Arisna on 2006-07-14
> **harakiri said:**
> thx a lot all.. now ill try the seperate home creation but aiysu... i didnot understand wat the following meant 

how can an installation not have /home.. linux creates /home automatically.
can u clear this for me?

What that part of the guide means is that you would use it if /home is not on its own partition.  If you followed the default Ubuntu installation, you currently have /home on the same "piece" of your harddrive as the rest of your stuff.  Following that guide will allow you to put /home on a different section (partition) of your harddrive that is controlled independently of the main (root) filesystem, which means you can reinstall Ubuntu without touching /home.

---

### Post by SigmaX on 2006-07-14
Personally I don't like putting /home itself on a different partition, as sometimes it causes problems with the custom user configurations (in ~/.kde, for example), particularly if I'm switching distros or operatings sytems all together (Like to FreeBSD).  Do it how you wish, but I stick to using a ~/documents folder for my user files partition(s), which is handy on a system without multiple users.

Just my two cents.

SigmaX

---

### Post by aysiu on 2006-07-14
I wrote that guide because requests for a separate /home partition are popular.

I, too, use a separate /documents partition instead of a /home partition.

---

### Post by harakiri on 2006-07-19
Hi Ayisu,
> I, too, use a separate /documents partition instead of a /home partition.

what is this /documents partition? how is it different from /home.. can you elaborate or gimme a link to this?

---

### Post by -deadcats on 2006-07-20
I do something a bit different. I use my 2nd HDD solely for linux documents, videos, mp3s--all that stuff I might normally have in my /home directory--and keep them in a "Documents" directory on that 2nd HDD. It's formatted ReiserFS and I mount it as "/data".

But to make things easier, I create a link to the "Documents" directory on that 2nd HDD and put it in my /home/username directory. It functions better than assigning my /home to that HDD, and I never have to clear out any of the crap if I choose to use a different flavor of Linux. :)

regards,
-dc

---

### Post by aysiu on 2006-07-20
> **harakiri said:**
> Hi Ayisu,


what is this /documents partition? how is it different from /home.. can you elaborate or gimme a link to this?
/home has all your settings and personal configuration files.

/documents (or deadcats' /data) is just a folder that has... documents in it, or data. It isn't a special folder. It just has stuff that's important to you.

/home, however, is a special folder--if there's no /home folder, there's no functioning Ubuntu. Any new user will have configuration files in /home/username.

/documents has no special processing. If it exists, great--you can put stuff there. If it doesn't exist, Ubuntu couldn't care less.

---

### Post by harakiri on 2006-07-20
can i seperately back-up all configuration files like .emacs, .bashrc etc etc which are in my /home by some single command or will i hav to select and remember not to forget any of theses files manually(](*,) ).
:-k

---

### Post by aysiu on 2006-07-20
Look at this tutorial for details:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

If you follow that, all the hidden configuration files will be copied.

---

### Post by harakiri on 2006-07-25
thx aysiu

---

### Post by Blondie on 2006-07-25
> **-deadcats said:**
> I do something a bit different. I use my 2nd HDD solely for linux documents, videos, mp3s--all that stuff I might normally have in my /home directory--and keep them in a "Documents" directory on that 2nd HDD. It's formatted ReiserFS and I mount it as "/data".

But to make things easier, I create a link to the "Documents" directory on that 2nd HDD and put it in my /home/username directory. It functions better than assigning my /home to that HDD, and I never have to clear out any of the crap if I choose to use a different flavor of Linux. :)

regards,
-dc

At the moment I have two 40 GB HDDs that I've set ubuntu up to amalgamate together and recognise as a single 80 GB volume by striping the data across both drives. I set this up using the RAID 0 option in the partitioner of the dapper set up program (alternative and DVD set-up discs only I think). Then I've partitioned that single 80 GB virtual disc into swap, home and root partitions in the sizes of my choosing, all three of which span across both discs. I did it because I wanted maximum flexibility in choosing the sizes of my partitions, but it is also supposed to give a speed boost since you can have two drive heads reading or writing data at the same time.

Ubuntu can do this kind of RAID without having to buy extra hardware - because of the server background of Linux most of the software to do it is in the Linux kernal AIUI.

---

### Post by SigmaX on 2006-07-27
That's just... sweet.  Imagine the clueless look a sheltered Windowite would give you after hearing that description...

SigmaX

---

