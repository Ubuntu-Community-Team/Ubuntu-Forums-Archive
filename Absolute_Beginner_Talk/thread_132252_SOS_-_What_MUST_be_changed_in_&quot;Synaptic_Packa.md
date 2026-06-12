---
title: "SOS - What MUST be changed in &quot;Synaptic Package Manager&quot;"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-17
Hello ALL !!!

Since I have become an "Ubuntu-holic", I feel that it is time to suggest what MUST be changed in the way the "Synaptic Package Manager" works.

What I am going to suggest, requires very little transformation on "Synaptic Package Manager", BUT (I believe that) it is CRUCIAL & REQUIRED by the Users.

Note:
I really HOPE that the Ubuntu programmers VISIT our pages (the "Absolute Beginner Talk"), cause then this post (and my effort involved in writting this) is going to be useless (& with no meaning at all).

However, I feel that it is important to suggest NEW changes, since we are ALL going to benefit from them.

At the same time, I feel that the changes we suggest MUST be written with "Having in Mind" the Programmers & their effort involved to provide to us a BETTER OS.
I think that we should ONLY request from them, the Minimum possible work involved (& that means writting code) for OUR NEEDS to be satisfied.


**Chapter 1:**
SO, let me first talk about OUR NEEDS:

We want to be ABLE to BACKUP a Program & its Dependencies, EASILY !!!

In the Computer World there could always be Problems, Crashes (see Windows) & other Critical situations involved.

I have (& YOU all have) read, _even_ here in this Forum, of Situations where Users (people) have lost their Files, or can NOT Boot, etc, etc.

Now, if in ANY case (which I hope it NEVER happens to anybody), we have to Re-Format our Hard Drives, & Re-install the Ubuntu OS, if we have NOT Backed up our Programs & their Dependencies Programs or Files, we would have to Download AGAIN the same stuff !!!

AND WE HATE DOING THIS REPEATEDLY !!!


**Chapter 2:**
The "dependencies"...
You see, In Windows, when I downloaded programs, each Program was usually 1 File, which I saved in case I ever had to format my Hard Drive (& that was TOO often).

In Linux, you have this "Synaptic Package Manager" or "Automatix" that perform the Installs by
themselves.
_But_ the fact that WE can NOT BACKUP the downloaded programs & their dependencies, means that in case we have to Format, we would have to download the programs AGAIN.
Now the programmers of the Linux community should do something about this...

Come on Programmers, do NOT tell us to Use the CD to backup ..... stuffed files deep in the Hard Drive's repositories, from some folder with "zillions" of files (we do not have a clue what they are for), packed like "sardines in a can", & b*llsh*t...

Note:
There is an article posted in this Forum about how to Backup on a CD, but I find it Useless,
cause you will end up, burning zillions of CD's & in the end you won't be able to track which
programs are Backed Up, what is their latest version, etc., etc.


**Chapter 3:**
What do I have to Propose:
When the "Synaptic Package Manager" downloads a program we want to install (& the
appropriate files, dependencies, etc. that come with it), it should download it to a Folder lying on the Desktop.
If such a Folder does NOT exist, "Synaptic" should create one.

When the Download of the Program & its Dependency Files (or Programs) is done,  then we are ready and can Go & perform our Backup to that folder & it's required Dependencies.
So, Up to this moment, NO installation is performed.
The "Synaptic Package Manager" should NOT auto-install AFTER the Download.
It just pops up a window asking us if we want to install.
If we say NO (which we will, to perform a BACKUP), it will dissapear - close.

After Backup, we are ready to install.
We then go & LAUNCH the "Synaptic Package Manager", and instead of Downloading the files AGAIN, WE tell "Synaptic Package Manager" where to look for the program & its dependencies to install (right on our Desktop's Folder).
So, basically, EVERY TIME we want to Install a program, "Synaptic" should pop up a window, asking us if we want "Synaptic" to search the Internet for the Program or if WE will specify where the program is, to install it. 

In the case that WE specify to "Synaptic" to install the program (& its dependencies) from a designated Folder inside our Computer, there might be the case that we are trying to install an OLDER version of that program (OR an older Dependency file).

So, before the "Synaptic" performs the install (from our designated folder), it can go & search the Internet to Verify that the latest version of the program (& the latest dependencies) have NOT changed.

Now, if (in any case) our program is an OLDER version (OR some dependencies are mission OR are older too), "Synaptic Package Manager" will ask US to download ALL for us or NOT.

After WE decide:
a. it will either install what we have, OR
b. will download the NEW version OR NEW dependencies, save ALL inside our Folder on our 
     Desktop & ASK us if "Synaptic" can get rid of the OLD (versions) of program OR 
     dependencies we might have inside the Folder (that are NOT needed anymore).

Here, the "Synaptic Package Manager" AGAIN, should NOT auto-install AFTER the Download.
It SHOULD pop up a window asking us if WE want to install.

If we would like to make a Backup, we will say NO, and the Synaptic window will close.

Now, WE could Go & Backup the MOST Recent Version of our program - with ALL the
latest Dependency files (or programs).

Then AGAIN, WE go & launch "Synaptic Package Manager" & THIS TIME we tell AGAIN
Synaptic NOT to download, BUT to look for the program (& its dependencies to install),
right from our Desktop Folder.

So, before the "Synaptic" performs the install (from our designated folder), it can go AGAIN & search the Internet to Verify that the latest version of the program (& the latest dependencies) have NOT changed.

ONLY this time: ALL is "top notch" (perfect & we have the latest versions), & Synaptic installs OUR requested program's.

It is NOT hard, is it?

**Conclusion:**
EVERYBODY is HAPPY:

1. We can MAKE BACKUPS to programs & dependencies (before we install),

2. The Programmers will have to change ONLY a little piece of code which has to do with the way 
     "Synaptic Package Manager" Program works.
      But the BASIC CONCEPT of "Synaptic Package Manager" does NOT change.

3. We do NOT get rid of Synaptic. We use it ALWAYS to perform ALL our installations & program 
     related needs.

     _Note_:
     And this is EASIER than the ".deb" or ".tar.gz" st*p*d "MANUALLY PERFORMED" installation 
     procedures that ONLY end up in NON-installing situations & endless problem encounters - 
      with NO viewable solutions in the "nearest" HORIZON...).
      _And you know what_:
      If I can NOT backup with "Synaptic", I then prefer to search for a ".deb" or ".tar.gz" file, Back it
      up & then try to Install it by myself.
      But then:
      I am HAPPY to have a BACKUP, I' ve spent "zillions" of hours trying to find the right way to 
      install the program, and "Synaptic" ends up as "useless" for ME !!! 

4. We do NOT use the silly (if not worse) CD suggested way, to end up Backing Up AGAIN & 
     AGAIN, unknown files from inside our Hard Drive's Repositories, and at the same time 
     waisting our CD's repeatedly.


Hope I helped & YOU guys liked my idea.

.... and MOST of all:  I HOPE the PROGRAMMERS READ THIS !!!


Please Tell Me what YOU think about this...


Take care, 

Dimitris.

---

### Post by BoyOfDestiny on 2006-02-17
Don't like it.
If you want your own repos, either order a cd/dvd or back up your current debs (/var/cache/apt/archives/) to a cd/dvd. Better yet just put /usr and /var on different partitions, then your current apps won't be overridden during a re-install.
As for a folder on the desktop... No. Look at the program description. If you download it and don't want it, just remove it. It makes no difference if it's installed.
In synaptic you can right click the file and see where it goes.
All user interactive apps should make an icon in the menu (that is something needed)

---

### Post by TheIdiotThatIsMe on 2006-02-17
Unfortunately, I couldn't read all of your post due to the constant capitalizing of so many words. May I suggest to not put so many words in all caps? ;) It really ruins the flow of trying to read such a long post. Just a friendly suggestion :KS

---

### Post by stalefries on 2006-02-17
This may solve some of your problem; when you are selecting programs to install through Synaptic, you can tell it to just download them, and not install them. There is a checkbox on one of the windows that pops up that specifies this. You can then manually install these, by using "sudo dpkg -i /where/the/file/is.deb" from a terminal. Of course, change that location to where the file actually is.

---

### Post by Qrk on 2006-02-18
Are you sure you just aren't thinking of 


/var/cache/apt/archives ???

In synaptic settings--> preferences you can tell it to save all the downloaded packages into a cache. If that isn't a good backup, I don't know what is.

---

### Post by najevi on 2006-02-18
[quote=BoyOfDestiny]... Better yet just put /usr and /var on different partitions, then your current apps won't be overridden during a re-install.[/quote] 
That was a path I started down but stopped partly because I am new to partitioning in linux and don't have enough experience with the partition table editor that runs during install.

/var was too much data to place on a separate partition. 

I tried to set the mount point of a separate partition to 
/var/cache/apt 
but that was not succesfull. (Mind you I may have done something else wrong because I was also learning about LVM, PV, VG and LV at the time! FYI: [http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux")) )


In the end I settled for just a separate partition for /home and sized that large enough to make a tarball archive of the entire filesystem. Overkill to be sure; but it solved my immediate problem.

Now all I do is selectively tar directories of interest:

/var/cache/apt
/usr/local
/usr/share
/var/mail
/var/tmp

and several files from
/etc

Eventually this will become a shell script and scheduled using cron but for now I do it manually because I am still re-learning the joys of shell commands.

** dvarsam**,

There is one more point within Synaptic you will want to pay attention to. 

*Settings -> Repositories *
in this window which lists the repo's check whether there is a *Settings *button or not. If not then don't worry. If it is there then open that Settings window and look to the last three radio buttons ufder the heading: *Temporary Files*.

**They configure how the local cache of package files are to be periodically purged/trimmed. **

For what you are describing all three should be unchecked. 

I can relate well to what you are asking for - you may care to monitor any response to a related post at  [http://www.ubuntuforums.org/showthread.php?t=132281&highlight=synaptic]("http://www.ubuntuforums.org/showthread.php?t=132281&highlight=synaptic")

---

