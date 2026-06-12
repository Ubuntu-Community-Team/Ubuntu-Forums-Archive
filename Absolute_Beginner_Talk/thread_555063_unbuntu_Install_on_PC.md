---
title: "unbuntu Install on PC"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by viplayday on 2007-09-19
We'll I am trying to install Ubuntu on a computer that has a windows OS on it now. When I put the CD in it acts like it is installing the OS. But when I reboot it boots windows. I would like to get rid of windows all together and just have Ubuntu. right now i waited long to turn the PC off and on the desk top of Ubuntu it has an Icon that says install. I click on it just now but everything seemed to be moving very slow very very slow. I have 256 ram on the machine. Please tell what I maybe doing wrong. I how can I reformat the drive if that is what I need to do? I hope to get a reply from someone smart and knowledgeable. :)

---

### Post by Pumalite on 2007-09-19
Make sure you have CD first in boot order in BIOS.
256 MB RAM>Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
You can boot Live CD making 1 GB swap partition ahead of time, but would run slow in your system.

---

### Post by madmatrixz3000 on 2007-09-19
If you can deal with not hibernating, and this is your first try at Linux I suggest using Wubi.  It installs and sets up most everything up for you and creates the boot menu and everything.  I hear that depending on your harddrive it can be a bit slower but I do not know as I only use Wubi installs.

---

### Post by Duck2006 on 2007-09-19
When you boot from the live CD and click the install icon, when it comes to the partitioning part, tell it to use the hole drive.

---

### Post by viplayday on 2007-09-19
So I have the OS open via the live CD I have not the desk top the install file. i clicked on that and after 20 mins. A window appeared label install it asked me fr the language. I have clicked on forward about 10 mins. ago. nothing is happening. this is not a slow computer. the mouse is constantly frozen. This sucks!

---

### Post by cappii on 2007-09-19
I have to agree with Pumalite.  At only 256 MB of Ram, I would strongly suggest the alternate install CD.  It works just as well, and is very easy to do.  As mentioned, though, when it comes to the partition editor, ensure that you are using the entire hard drive.

---

### Post by Pumalite on 2007-09-19
Don't forget the swap partition if you want to boot Live CD.

---

### Post by Duck2006 on 2007-09-19
May be the ISO you downloaded had bad blocks. 
Did you burn the cd at x4

---

### Post by viplayday on 2007-09-19
Ok so whats this Pumalite and wubi stuff? What is the difference between it and the  .ISO of Ubuntu that I am trying to install. Can I just get rid off Windows reformat the drive and install the damn thing? Yeah this thing is not going anywhere. at the install menu I clicked forward after choosing the language nothing is happen 20 min now just sitting there and mouse is frozen most of the time.

---

### Post by Duck2006 on 2007-09-19
What is the system that your trying to install ubuntu to?

---

### Post by lisati on 2007-09-19
I had similar problems on my laptop - nothing seeming to happen for HOURS after clicking on something on the Live CD, other than a rather busy CD/DVD drive. I eventually gave up and burnt a copy of the "alternate" CD to a DVD (yes, it can be done) and installing from that. From what I've read elsewhere, part of the problem could be that Ubuntu likes to have a "SWAP" partition available, and, depending on your system, not having one can sometimes slow things down horribly.

---

### Post by viplayday on 2007-09-19
Sorry to say this but it really sucks that I have to become a damn computer guru or programmer/ builder to get away from the monopoly of f*#king Microsoft!!!! I have to be honest yes i don't jack about these programs and partitioning a drive. Are all linux based OS a puzzle and a half? i have tried CentOS too and I had to pay someone just to get the drivers for my netwrok card and wireless. Now I have a dell pc with most of my hardware all intigrated onto the mother board. I feel I am F*#ked. I am going to have to jump through hoops to make my sound, wireless, network, camera, and external drives work. right?  Damn Microsoft making us all stupid and lazy sorry I should just say capitalists!!!!!! Capitalizing off of the stupid people that they created. what a great idea!! 
:)

---

### Post by madmatrixz3000 on 2007-09-19
This is your first install, go right now to google and look up Wubi.  Within windows on the computer you want linux on.  Download this and then double click on it.  The link will bring up the setup options then will begin to install Ubuntu or Kubuntu depending on what you choose.

Basically this creates Ubuntu within a virtual partition.  Then once setup you can deinstall windows based on the many posts and instructions made by the creators of Wubi.

In layman's terms Wubi will install Ubuntu within Windows so that you can boot Ubuntu without the hassle of worrying about the install.  Then when you start your computer, Ubuntu starts like normal with only a difference here or there

---

### Post by madmatrixz3000 on 2007-09-19
I felt similar and almost spent 24 true working hours trying to get my laptop working.  Trust me I wanted a true boot and install, but in truth just use Wubi, you won't be able to tell the difference

---

### Post by SteveHoffmanUK on 2007-09-19
My advice is:

1. Calm down, cool it, take it easy. You can get rid of Windows if you really want to. You will need to be a bit patient but no need to become a programmer.
2. I have 256 Mb on my 4-year-old Dell laptop, and it runs Ubuntu Feisty without any problems.
3. Download free Killdisk  [http://www.killdisk.com/downloadfree.htm]("http://www.killdisk.com/downloadfree.htm")
Unzip it and write it onto a floppy. Put it in your floppy drive, boot up and follow its instructions. It will wipe your hard disk.
4. Download and burn at your slowest speed (4x) the Alternate CD [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
(Check the box at the bottom of the page for the alternate CD) 
5. Put it in your CD drive and install Ubuntu.
6. Come back here with further problems. People are willing to help if you are nice to them:)

**ON EDIT:** See later post. Please do 4 before you do 3; otherwise you will wipe out your disk and won't be able to download anything!

---

### Post by madmatrixz3000 on 2007-09-19
I'm running 256 fine on my laptop.  Its faster than in windows, but it is on the lower end of the spectrum when it comes to hardware.  I run 1.5Gb on my studio computer and it still is not enough so you might want to look at Xubuntu which will probably run better and it takes up less space.  But you sacrifice alot of features to do so.

---

### Post by madmatrixz3000 on 2007-09-19
Steve I think for his first install he should use Wubi, then he does almost nothing and he can switch back if he wants, or use both like I do

---

### Post by viplayday on 2007-09-19
thank you, thank you, thank you. I appreciate everyones help I will try something and get back with my results. i just ate something...Now I don't think I am going to throw my PC out the window. Ok I will get back in a little bit.

---

### Post by SteveHoffmanUK on 2007-09-20
Madmatrix: Thanks for the heads-up about Wubi - I'd not heard about it before. Sounds like an interesting concept, though I'm still trying to get my head around it! I'm slightly wary because it's still a beta, but I guess you have found it reliable?

viplayday: Oops! If you're going to follow my advice, you need to do 4 before you do 3; otherwise you will have wiped out your disk and won't be able to download the alternative CD. :redface:

BTW, most of us have felt as you do when we first started to use Linux. It **can be** irritating and a bit tecchie at times, but it's well worth a bit of effort. Always try to find your own answers first, either by searching these forums or by doing a Google search. If that doesn't work, then come onto the forum and ask your question - there are a lot of very helpful people here.

---

