---
title: "Dual Boot with XP, few questions before i do."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by nintennuendo on 2007-03-10
I want to dual-boot with XP, just so I can make sure my wireless card and connection eveyrthing will work.  I think I have some good instructions, but can someone look over them?

[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)

After that, I just install Ubuntu, right?  I was thinking about 15gb free on this hard drive for it.  and, if everything works and I can connect, can I just. wipe out the XP and add that to Ubuntu, or do I have to format everything and do it again?

---

### Post by oilchangeguy on 2007-03-10
to find out if everything will work with your computer simply load and run the live cd. no changes will be made unless you select install from the desktop. if you decide to delete xp you can use gparted from the live cd to acomplish this.

---

### Post by nintennuendo on 2007-03-10
and this one is not really a big deal, but would the bookmarks.html file from Firefox keep all my bookmarks?  like, in the toolbar, in the bookmark folder itself in file, edit etc, and my RSS feeds?

---

### Post by mikewhatever on 2007-03-10
Do not wipe Windows even if everything works beautifully. It takes at least several month to learn and get fluent with any new OS.
The link you posted does not work.

---

### Post by Crooksey on 2007-03-10
If you put the ubuntu CD into your disc drive...

Let it boot, then ...

Click the applications menu, then accessories then terminal, now type "iwconfig" if you get an output something like...

```

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Your wifi card is/has been detected.

---

### Post by carusoswi on 2007-03-10
So, I am interested.  Downloading Ubuntu, the disc burner, and that other thing Win5 or whatever.  My XP system has important data on it.  Will resizing partitions per instructions in the link given in this thread trash the data on my drive?

Is installation really as simple as it appears in the instructions?

I am getting excited (and also a bit nervous).

Caruso

---

### Post by oilchangeguy on 2007-03-10
yep, it's that simple, drop in the live cd and select install from the desk top. let ubuntu set it's own partitions. for example if you've got an 80gb hard drive it'll split it in half. 40gb for windows and 40gb for ubuntu.

---

### Post by Kevf on 2007-03-10
Without reading your link: partitioning your hd can allways damage your data. Most of the time it works (done mine with partition magic) but there's still a chance.

---

### Post by nintennuendo on 2007-03-10
Wait, I do not need any other program to partition?  I can just run the live cd, and ubuntu can split my hard drive for me to dual-boot?  I just want to give ubuntu 12 or so gigs to start with, can I choose that?

---

### Post by oilchangeguy on 2007-03-10
yes you can do a manual partition with the live cd. it's just easier to let it auto partition.

---

### Post by Mr. Svinlesha on 2007-03-10
Hej, **carusoswi** and **nintennuendo**:

I did this myself for the first time about a week ago.  Do be sure to backup all important data just in case something goes wrong.

Which version of ubuntu are you planning to install?  The instructions you linked to show a slightly different version of gparted than the one I used.  How simple the process actually is depends to a great extent on how computer literate you are; for some people it's a snap -- I needed some help, because I didn't know how to make partitions and so on.  I did manually partition my disk for the install, which is probably the best option, but also the most difficult/confusing.

Even so, it wasn't all that difficult.  Just take your time and you should be able to figure out the steps.  I posted questions during the install as well, here, just to make sure I was doing everything correctly, and got great help.

Good luck, and welcome to Ubuntu!

---

### Post by vavroom on 2007-03-10
Also speaking from a newbie's point of view here.  If you use PartitionMagick, do it *before* you install Ubuntu, unless you're feeling confident about going in to the command line straight away to fix a few issues.

I installed Ubuntu, no worries, went like a charm.  Then I decided to reinstall my windows (I had done a dual-boot thing) because... well, because it needed it ;), which also went well, except that the WIndows install did nasty things to Grub...  I fixed the grub stuff (thanks to numerous posts and tutorials here and on the wiki).  Then I used partitionmagick to resize my windows partition.

Which of course changed the references of the Ubuntu partition (went from hd0,5 to hd0,6).  And I coudln't get Ubuntu to boot.  Had to go to the LiveCD, command line, etc.

Moral of the story, it *is* ultra simple to install Ubuntu and have it work in dual boot mode, if you do it in the right order.  However, if you decide to do a few things out of "sync", you'll likely have to fiddle :)

My 2 cents

---

### Post by soul814 on 2007-03-10
I finally had time to install ubuntu on my notebook today, I'm installing updates. My advice is defrag your hard drive before you resize Ubuntu and make sure everything is at the front of your drive. After that resize it and it should be fine. I'm dual booting XP and Ubuntu and left a little space for Vista if I ever wanted to try it out.

---

### Post by rusty4r on 2007-03-10
yes your guide is either wrong or outdated.

Ubuntu has gparted, which is freesource partition editor, included on the live cd and it will, contrary to your guide, partition a ntfs drive for you.

I did it about two months ago. Just remember to defrag windows before you start, I've even seen some advise to do it twice.

I would think that 12 gigs would be fine for you to experiment with. As mikewhatever said I'd keep windows for a while until you learn Linux

---

