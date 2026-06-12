---
title: "Re-install questions..."
date: 2006-12-07
forum: Apple PPC Users
---

### Post by three-cushion on 2006-12-07
Experience to date:
6.06 LTS runs OK FIREFOX, MAIL, Synpatic etc..... BUT:
1) Software Properties will not open... Quick message re :API unstable? then window disappears.
2) Clamav will not install ... Needs libclamav1 but will NOT install it .. libgmp3 missing?
3) None of the suggestions re: sharing OS X; read OR write...work.

Looks to me I MUST re-install (others suggested that).:( 
So a few how-tos are in order , I guess:

1) To re-install, I am going back to LiveCD....
a) Can I ZERO-out the Ubuntu partitions with iPartition /OR
Disk Utility? Then tell LTS to re-format during Install?
b) Are there ANY pre-install options to set with LiveCD?
c) When I assign an Ubuntu Username, should I use my OS one
(eg, '501'). Then I *might* be able to Share folders with
OS X?

After re-install (and updates finish) I will try;
1) Uncomment 'universal' repos in /etc/apt/sources.list; then run: <sudo apt-get update>
2) I read in the forum about using 'volatile debian' for universal app installs.. true?

Any other hints for me before my re-install?](*,) 

Cheers, Jim B
PS What does 'Bean Count' mean?:confused:

---

### Post by Gen2ly on 2006-12-07
3:

It's been from my lessons that most of problems and errors can be fixed.  I've known people that have boxes running for years.  Reinstalling seems desparate!  Lost are all your application configurations, added programs, bookmarks, downloads.  When I installed Ubuntu I had bad issues: no sound, menu locking problems, no idea home to mount a Macintosh disk, but through the plentiful information in these forums, and the patient people who too the questions thoughtfully, my system runs great now.

If you are dead on about reinstalling everything, I'll let you know you don't need to repartition everything.  If you choose the option to edit your partitions manually you can tell the installer which one you want to use as root, swap, etc. and the installer will tell you that doing so will erase any data.

---

### Post by three-cushion on 2006-12-08
Dirk: Thanks for the thoughtful advice. I am interested in Linux for additional OS knowledge. My main OS is/will be Mac OS X, Leopard & beyond.
 
I also use Windows, but only for working at home  for income, not pleasure. In fact, recently I found a way to use Safari's updated JAVA system to run what has been for several years, an APP that would ONLY run on IE 6 and MSFT's VM bastardization of a JAVA engine (see the above remark on income :p ).

My background is from UNIX (started in 1978 on a PDP-11). I chose OS X b/c of its FreeBsd foundation and the Mac GUI.  My next system will be an Intel Mac running Parallels. And, besides a Windows OS I want to widen my OS know-how to use Linux too.  Later I'll even try Vista under Parallels.

So, my decision to re-install will not destroy anything that I haven't yet obtained. You are right that this forum of knowledgeable users is priceless. You can see by my 'NOT Working' list that I have been using the forum frequently. And, I again thank you for your reply.

I'll post any problems I have in this re-install thread.

Cheers, Jim B

---

### Post by stream303 on 2006-12-09
Welcome aboard Jim.

If you are already satisfied with your existing Ubuntu partition layout and just need to reinstall, you won't need to zero out anything - just let the installer find and use the old partitions.

That said, you *could* use iPartition I suppose to wipe out your existing Ubuntu partitions and change the size of your HFS+ partition.  If you use disk-utility, you are looking at destructive partitioning and will be loading OSX again as well.  Works - many do it this way to just put OSX on half the drive, etc.

An alternative to iPartition is parted if you don't mind only being able to shrink your hfs partition and not grow it:

[http://www.ubuntuforums.org/showthread.php?t=89960&highlight=hfs+partition](http://www.ubuntuforums.org/showthread.php?t=89960&highlight=hfs+partition)

Sure wish I had known about unix since 78.  A bit off-topic, but that's one thing I express to my friends wanting to learn the command line - it's not likely to change in the next 30 years either, so what you learn is a valuable skill.  Ubuntu might be long gone, but VI will still be around. :)

---

### Post by Gen2ly on 2006-12-11
tell us how it goes.

---

### Post by three-cushion on 2006-12-12
First The re-install work fine (More on Partitioner later).
The *massive* update that foloowed (221MB) work OK EXCEPT:
     3-failures; gnome-terminal-data; gnome-terminal; and
                 Ubuntu-desktop ALL had dependency errors. 
                 All 3 said: "Not configured yet"
      So, is there an easy way to fix these? 
      Is it necessary to fix them?

Next, I verified that all the Accessories worked OK. Set up to update for Universal, Security, as well as Ubuntu apps. Then set up Mail & checked to see if Synpatic listed the supported apps as well as the Universal. All OK.
-------------------------------------------

Second: This partitioner in Ubuntu... its not very user friendly. I left the 3 partitions used before in the 1st install, expecting the Installer to overwrite them. 
I could NOT force the installer to use the 3; OK for ext3 & swap; but it did not recognize the previously created small Apple_boot partition at all. Rather it tried to take the rest of the HD space for itself. No way was I about to allow that (What, 38GB for a 1MB boot volume???) 

So, I went back to iPartition on OS X; deleted all 3 Ubuntu volumes, and created a DUMMY OS X volume to take up all the Largest unused space EXCEPT for about 10GB left for Ubuntu to use.

Went to install again (from LiveCD), told installer to use the largest unused space on one of my internal HDs.

Then, the Install proceeded and ended OK.

iPartition will create Linux volumes... ext3, swap, boot, etc, but I have not tried to complete an entire install cycle with them., primarily b/c the "manual create" doesn't seem to work as one would like. (Take this volume and USE it).

Now I will try to install some apps that I want, clamav being the first, followed by acroread.... 
More as I progress.

Cheers, Jim B
PS BTW, after choosing the additional Universal and Security properties, the /etc/apt/sources.list was changed automatically (eg, uncomment the correct lines, etc)!. I did nothing to the file.

---

