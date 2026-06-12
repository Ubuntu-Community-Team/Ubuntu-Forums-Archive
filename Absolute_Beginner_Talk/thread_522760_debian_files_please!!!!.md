---
title: "debian files please!!!!"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by tictactoe on 2007-08-11
hello.this is my first thread in ubuntu forums actually :) .well,i am a newbie to linux or ubuntu ,in particular.i previously used ubuntu 6.06 dapper drake ( for 2 weeks :( )before,and found it OK!!!.see,i dunno whether all newbies face this problem or not,but i do not have a permanent internet connection (i am speaking from my friends place):(.but that does not stop me from being an open source lover!!!!the problem i find is that many codecs or players or new compiler versions are available only through synaptic package manager or automatix(correct me if i am wrong).well,people who do not have internet connection,just get confused ,seeing those apt-get commands,including me at one time.
                                                                                    well,here is what i thought.well,all debian files are managed through synaptic right???then why cant they just post links to the debian files for non - internet users.I have seen some add - on CDs doing that work,but they are not upto date,i guess.can u guys please post links where can i get all the required debian files.


Thank You.:)

---

### Post by 5-HT on 2007-08-11
Here's the entire Ubuntu Archive for you: packages.ubuntu.com :) For non-official packages and third-party repositories you'll need to search around for the specific package/repository.
cheers,

---

### Post by tictactoe on 2007-08-11
i am sorry,but i already know that sight.most of them are in .tar format.
i need direct debian file links.

---

### Post by splintercellguy on 2007-08-11
I'm pretty sure there's plenty of debs on there, but try getdebs.net?

---

### Post by 5-HT on 2007-08-11
> **tictactoe said:**
> i am sorry,but i already know that sight.most of them are in .tar format.
i need direct debian file links.
Those are all the .debs in Ubuntu's archives. When you click on one of the Architectures in the Download section of each package's page, you are presented a page to select your mirror, and it gives you the direct link to the .deb

---

### Post by bwtranch on 2007-08-11
Geez.guy you are the man!. OK , let's backup our system and burn a copy of Gutsy! Come on, you know you want to:(

Come on you pussies, I have not been able to crash this thing and I need some help! If you can crash this thing, please let me know. I have been trying to put this thing in the dirt, with no luck. Please help!!!

I cannot get this thing to not stop working!!! It is so frustrating my email works, my broadband internet works, my printer works, webcam and all the rest. What can I do? Please help!!!

If all this continues to work, what will I do? Have to find a job or something?:guitar:

---

### Post by Caffeine_Junky on 2007-08-11
...Hey ..duno if this is any help to ya, ..check it out :guitar:

                                debian.org/distrib/packages

cheers mate...

---

### Post by ugm6hr on 2007-08-11
@tictactoe:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/) is **definitely** the place where the .debs are stored.

If you are looking for specific packages, you can either search there, or use Synaptic Package Manager.  I know this sounds unbelievable without internet - but bear with me.  If you want to read the full discussion - read this: [http://ubuntuforums.org/showthread.php?t=512364](http://ubuntuforums.org/showthread.php?t=512364) (specifically posts 5, 6, 10 and 13).

In simple terms:
1. You can update your package lists manually or with wget (/var/lib/apt/lists) - **optional step**.
2. You can search for packages and dependencies with Synaptic Package Manager
3. You can Generate Package download script with Synaptic (File menu), which creates a file with a list of **all** the necessary .deb files, and their locations (url's) with wget script
4. Having downloaded them, you can then either just copy them to /var/cache/apt/archives/ and re-select in Synaptic and install, or try using the "Add downloaded packages" option in Synaptic.

Hope that helps.

---

### Post by tictactoe on 2007-08-11
i will definetely try them guys.thanks for the replies!!!:)

---

### Post by az on 2007-08-11
You can make a cd:
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

also, as far as downloading from the debian repo, you must avoid using debian packages in Ubuntu.  Debian and Ubuntu are similar, but they are not binary-compatible.

---

### Post by Caffeine_Junky on 2007-08-12
> **az said:**
> You can make a cd:
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

also, as far as downloading from the debian repo, you must avoid using debian packages in Ubuntu.  Debian and Ubuntu are similar, but they are not binary-compatible.
*****
Ahh... thanks az ..i was wondering about the compatability between the two.

Cheers

---

### Post by Caffeine_Junky on 2007-08-12
..here is a howto I just came across,  thought it might be of interest...

[http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

Cheers

---

### Post by tictactoe on 2007-08-12
guys,before,i used dapper drake ,and my friend gave me a link for an ADD - ON CD,and after downloading it and after using the public key and alll.................i saw that all the files in the cd were .DEB :) .i mean whoever created that cd image,must be knowing where to get all the debian files(just my imagination).so can u guys give me the link for an add - on CD for feisty please???

---

### Post by az on 2007-08-13
> **az said:**
> You can make a cd:
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)


> **tictactoe said:**
> guys,before,i used dapper drake ,and my friend gave me a link for an ADD - ON CD,and after downloading it and after using the public key and alll.................i saw that all the files in the cd were .DEB :) .i mean whoever created that cd image,must be knowing where to get all the debian files(just my imagination).so can u guys give me the link for an add - on CD for feisty please???

See the above link or look at aptoncd ([http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)).

---

