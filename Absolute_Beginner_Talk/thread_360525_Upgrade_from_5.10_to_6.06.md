---
title: "Upgrade from 5.10 to 6.06"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by marianlibrarian on 2007-02-13
I have searched this forum on how to upgrade from 5.10 to 6.06 and it seems there are not many who have had to do this. I installed with no problems the CD that came with my book. The version is Ubuntu 5.10. I want to upgrade to 6.06 Dapper. I have access to the internet and would prefer that option if possible. I have to do this for 9 computers (Public Library). They are brand new computers and will only have Ubuntu - nothing else!! Yippee. I am using one of my machines that I set up yesterday to post this. I am thrilled that this is working for me and my library. 

Anyway, I do want to upgrade to 6.06. I can download the CD info and copy it. I have bittorrent on my xp machine, but I used a bunch of bandwidth yesterday downloading all the updates for 5.10 (there were 219) and it took over 4 hours. 

What is the advice? Can I simply "upgrade" without a full install to 6.06? Or do I need to "upgrade" from a CD?  Or do I need to just start from scratch again and "install" 6.06 from a CD?

thanks in advance 

PS. I want to use automatix and there is not a version that works with 5.10

---

### Post by taurus on 2007-02-13
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and replace the word **breezy** with **dapper**.  Save it and run

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by marianlibrarian on 2007-02-13
When I typed in the first command in the terminal, I get the following statement:
> (gedit:10040): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Then the source list window opens but it is empty.

---

### Post by taurus on 2007-02-13
Is it really empty?

What's the output of this command from a terminal then?

```
ls -la /etc/apt/sources.list
```
Otherwise, use a text editor like nano.

```
sudo nano -Bw /etc/apt/sources.list
```
And when you are done editing, hold <Ctrl> while pressing x to exit.  Then Y and Return.

---

### Post by marianlibrarian on 2007-02-13
This is what I get with your first command in the last post:
> -rw-r--r--  1 root root 1868 2007-02-12 06:54 /etc/apt/sources.list

This is what I get with the nano command:
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main $

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted univ$# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted $
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

              [ line 1/37 (2%), col 1/90 (1%), char 0/1868 (0%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell


---

### Post by marianlibrarian on 2007-02-13
This is what I changed using the nano command:
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



The very first line, I wasn't sure about changing, so I left it alone. Any reply before I save this will be welcome. :)

---

### Post by taurus on 2007-02-13
1.  Put a # in front of the first line to comment out the CD-ROM for breezy.

2.  Remove the **us.** from all the lines.

3.  Remove the # in front of all the lines with deb (except the first one where you just commented it out).

4.  Replace the word breezy with dapper for all of them.

Save it with <Ctrl>x.  Then answer the question with Y and Return.

Now, you your upgrade with

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by pay on 2007-02-13
You should be able to upgrade the way Taurus mentioned or you could try this way```
gksu "update-manager -c"
```

---

### Post by taurus on 2007-02-13
> **pay said:**
> ```
gksu "update-manager -c"
```

I thought that method is if you go from Dapper to Edgy.  I believe you can do the old fashion way, modifying /etc/apt/sources.list, if you go from Breezy to Dapper.

---

### Post by confused57 on 2007-02-13
I had no problems upgrading from Breezy to Dapper, using the method taurus suggested.

I followed aysiu's guide:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

It's been awhile since I did the upgrade, but if I remember correctly, approximately 600 mb or so was downloaded to do the upgrade...I could be wrong, though.

---

### Post by marianlibrarian on 2007-02-13
Well, that did it. Thank you. For anyone else who needs to do this: Get the CD and do a clean install. Why? Because the last command is going to take about 6 hours to complete. This may be a mess for me right now because we are under a tornado warning and if the power goes out during all of this.... Well, I will need my 6.06 Install CD to start from scratch! oh well.

Thank you for responding to me so quickly. I love this place!

---

### Post by taurus on 2007-02-13
> **marianlibrarian said:**
> we are under a tornado warning and if the power goes out during all of this.... 

Be safe and I think all that stuff is heading this way later this afternoon.

---

### Post by pay on 2007-02-13
> **taurus said:**
> I thought that method is if you go from Dapper to Edgy.  I believe you can do the old fashion way, modifying /etc/apt/sources.list, if you go from Breezy to Dapper.You're probably right. I just assumed that all version had that update manager.

---

### Post by Entity` on 2007-02-13
> **confused57 said:**
> It's been awhile since I did the upgrade, but if I remember correctly, approximately 600 mb or so was downloaded to do the upgrade...I could be wrong, though.

The 600 MB thing is EXACTLY why I want to upgrade using the CD.  For me it would take all, day all night, plus another day; all without turning my PC off, which I can not do.  Sure I downloaded the CD using Bittorent, but I can turn my pc off and on when I want when I do that.  And Ive been searching everywhere on how to do it.

---

### Post by bartendercorey on 2007-02-14
Marianlibrarian this is a little off the subject, but I'm the IT Tech for the Clay County Public Libraries near Jacksonville, FL.  I was just wondering how Ubuntu is working for you at your library?  I'm in the process of starting a project of switching all of our public and catalog computers over to Ubuntu.  I'd say I have about 100 Dell Optiplex gx280s and 170Ls at five different branches.  I will be installing 6.06lts on the systems.  Just wondering if you've had any hiccups besides the upgrade you just did?

---

### Post by IronMac on 2007-02-14
> **confused57 said:**
> I had no problems upgrading from Breezy to Dapper, using the method taurus suggested.

I followed aysiu's guide:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

It's been awhile since I did the upgrade, but if I remember correctly, approximately 600 mb or so was downloaded to do the upgrade...I could be wrong, though.

Great thread! I think I also have the same book that MarianLibrarian has (Beginning Ubuntu Linux) and I'll be upgrading soon too!  :)

---

### Post by confused57 on 2007-02-14
> **IronMac said:**
> Great thread! I think I also have the same book that MarianLibrarian has (Beginning Ubuntu Linux) and I'll be upgrading soon too!  :)

You can also download the Official Ubuntu Book:
[http://www.ubuntuforums.org/showthread.php?t=339531&highlight=ubuntu+book](http://www.ubuntuforums.org/showthread.php?t=339531&highlight=ubuntu+book)

---

### Post by tommynz1975 on 2007-02-14
Can you please tell me if the instructions given is to use  the desktop 6.06 CD or the alternative install CD?

Many Many Thanks.

---

### Post by marianlibrarian on 2007-02-15
Hi bartendercorey:

I have just completed one machine for public access. This means that it now has Dapper Drake, I used automatix to install adobe reader, flash reader, and real audio and a few other things. Then since these machines were purchased with federal grant money, I have to have filters in place. I used dansguardian. I had several stumbles during the whole process. The first being the CD that came with the book was Breezy not Dapper. I downloaded the Dapper at home and put it on a CD. Then I had a few stumbles with getting the dansguardian, tinyproxy and firehol to work but all has been resolved.

If you will give me a few days, I will have a much better idea regarding process and procedure for a full installation. I still have 8 more machines to go plus a server. When I am finished I will try to post a something here on how to set these up in a public library environment.

---

### Post by marianlibrarian on 2007-02-15
When I try to use gksu "update manager -c" I am asked for password which I type in then I am asked for ??? keyring password ???  what is that??

---

