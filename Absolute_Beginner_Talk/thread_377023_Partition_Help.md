---
title: "Partition Help"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Lucas the Guy on 2007-03-05
Hello, my name is Lucas. I currently own a Dell computer that I have had since June 2004. It is running Windows Home Edition with SP2. And I am becoming sick of Windows. I have been looking, seriously looking at almost every Linux build and I decided that I want to install Ubuntu. I have everything, the right disk to burn the .iso file to, a siable 180 gigabyte hardrive, 2.8 ghz of power, 512 RAM, etc. I even know about Wine, Dapper, etc.

Except I have one issue.

Partitioning.

Now, I am fairly certain the the file system Ubuntu uses is ext3. If I am not correct, please inform me. Except, I am a little short on cash, and I don't want to spend money on a partitioning program. Does anyone know of some open-source partition program/live CD/or whatever that is non-destructive? And, I also am wondering, if I am resizing a windows NTFS partition, will I lose data, even if the program is non-Destructive? Please answer my questions. Thank you! And I just started downloading  Ubuntu. I believe I have 3 hours left or so. :P

---

### Post by natman on 2007-03-05
If your partitoning a drive, the ubuntu live cd/dvd will do that fine for you. Just be weary i partitioned a vista system using gparted ( gnu partitoner ) and it screwed it up, i was able to recover. Anyway i dont know ( i never had ) any problems using the live partitioner on ubuntu.
Have Fun:

---

### Post by floke on 2007-03-05
Lucas. Relax.
You can do all the partitioning from the LiveCD.
System/Admin/Gparted - this is the utility you need.

First, back up all your data from Windows - I've done this more than a dozen times and have never had it go wrong, but there could always be a first time.

Then - very important - defragment your wndows hard drive and run a discscan for errors.

Then - when you know how much space to give to windows and ubuntu (and you have burned the iso). Put the disc in the CD drive and reboot.

The LiveCD should automatically load up - if not then change the boot order in the BIOS.

From the menu - select check disc - make sure it is ok - if there are 0 checksums failed then you're good to go - if not then try reburning the ISO at a slower speed. OK- reboot (select install or start from the menu to start up the LiveCD)

When into the Live CD - use Gparted to shrink the NTFS partition. Then simply double click on the install icon - follow the instructions and select the install to largest available free space option.

Give it about 20 mins.

All done.

Enjoy Ubuntu!

Welcome to the Community :)

---

### Post by Lucas the Guy on 2007-03-05
Wait, so the Ubuntu will non-destructively partition it for me? Just confirming this.

EDIT: Thanks Steve, I had not noticed your post. So I load up the GParted Live CD (I Googled it just now) and resize it, then eject it, and restart my computer and put the Ubuntu CD in and then choose the ext3 partitioned partition and I'm good?

---

### Post by floke on 2007-03-05
Yep.
But backup all your data first (just in case anything does go wrong).
And run a defrag and scandisc.

---

### Post by Lucas the Guy on 2007-03-05
Have you read my edited post yet? Thanks.

---

### Post by floke on 2007-03-05
No- forget the live Gparted CD - the Gparted utility is already on the Ubuntu Live CD .

From the top bar on the dekstop - select system/admin/GParted

---

### Post by Lucas the Guy on 2007-03-05
So, after GParted runs it's course, will Ubuntu install on my system, or, what will I have to do? Thanks.

EDIT: Install icon, got it. xD

---

### Post by floke on 2007-03-05
Good luck.

See you on the other side.:)

---

### Post by mikewhatever on 2007-03-05
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by Lucas the Guy on 2007-03-05
Ok, so I know that I should back up all my important data to discs (I only have about 5 gigs of important stuff, the rest is stuff that's easily downloadable. I love big HDDs. So after I defragment, I should run the windows check disk (chkdsk), then insert the live CD?

And how will I know if my wireless adapter will work? And what if there are problems with my chkdsk?

Sorry for all the questions.

---

### Post by floke on 2007-03-05
If you have errors on the disc then fix them with Windows.

You can see if your wireless will work by (a) using the LiveCD (that's what its there for!); (b) search the forum for details on your wireless card. Some cards will require the use of a thing called ndiswrapper (never used it myself) - though many will be automatically sorted.

---

### Post by mikewhatever on 2007-03-05
Your wireless adapter can be tested from the live cd. If it doesn't work you can come back here and ask more.
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)
If for some now unknown reason, there are unsolvable problems and there is no way for you to use Ubuntu, then don't use it. Try another distro instead. What if and what if not way would lead nowhere.

---

### Post by Lucas the Guy on 2007-03-05
Thanks Mike and Steve. Mike, yours was a nice visual. Thanks guys. 22% download. I am now going through my hard-drive checking for all the REALLY important files. And then I'll defragment, etc. Thanks guys!

---

### Post by visible on 2007-03-05
> **mikewhatever said:**
> [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")
That whole psychocats page is awsome and very helpful definitly read this part too.

---

### Post by floke on 2007-03-05
Lucas, I'm going to bed. When I check in the morning I expect to hear you effusing about how wonderful Ubuntu is, and how everything works for you fantastically!

Any problems then post back and we'll try to sort it out.

(But just not from me for the next 8 hours).

zzzzzzzzz.

---

### Post by Lucas the Guy on 2007-03-05
You must live in the Eastern Hemisphere or Europe or Asia or something. Because, yay me, it's only 5 PM here. And I have a general question, does the Ubuntu distribution come with the Adobe Flash plug-in and stuff?

And switching programs will be a cinch, I use OpenOffice, Firefox, etc. Except I'll need to run Wine (I'll need to read up on that, but I got the basic idea) to use iTunes and Photoshop. Or I could just open up Windows. But that'd by stupid? And yes, I used GIMP for 6 months, but I find Photoshop more intuitive.

Hmm, Psychocats should help me from here until I am done setting up Ubuntu. I'll be back tomorrow to post how awesome Ubuntu is, or later tonight. Yay.

---

### Post by floke on 2007-03-06
Europe - home of Linux!

Yes you can use Wine. Flash not installed by default - but its easy to put in (and I think is in the repos).

---

