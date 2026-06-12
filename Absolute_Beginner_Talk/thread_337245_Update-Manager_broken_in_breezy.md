---
title: "Update-Manager broken in breezy"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2007-01-12
Hi,

I'm pretty sure my Update Manager is broken in Breezy.

I have Edgy on my laptop with no problems.

I wanted to install Ubuntu on my son's laptop but only had a 5.10 Breezy iso. I don't have a burner on my laptop to download the Edgy or Dapper iso.

Breezy has been installed with no problems everything works fine.

However, the CD iso I used is ages old, and yet update manager is saying my system is up to date, which surely must be wrong, as there have been tonnes of updates.

This means I can't get Dapper. Last time Breezy upgraded to Dapper easily: Update manager told me there was a new distro available. No such thing now. If I refresh it tells me my system is upto date.

I've tried: gksu “update-manager -d”

But I get the same message that my system is up to date.

Any idea how to get it working, or more importantly, how to upgrade to Dapper. I've read the Dapper upgrade guide, but just get my system is upto date.

I've checked my network. I am online.

Thanks.

---

### Post by bscbrit on 2007-01-12
In a terminal, try

sudo apt-get update

It should update all of your repos but, if not, you will get a helpful message telling you why it can't. :-)

---

### Post by NeoLithium on 2007-01-12
In your /etc/apt/sources.list change your instances of breezy to dapper, then sudo aptitude update and then sudo aptitude dist-upgrade; should bring you up to a nicely upgrade dapper version.  Just be aware this can take quite a while depending on your connection speed.

---

### Post by DougieFresh4U on 2007-01-12
You could try other ways, such as edit sources list-all instances of breezy change to dapper then update and upgrade then dist-upgrade. Just a suggestion although not the "official" way, good luck!! **gksudo gedit /etc/apt/sources.list**

---

### Post by obsidion on 2007-01-12
> **Tweedicus said:**
> Hi,

I'm pretty sure my Update Manager is broken in Breezy.

I have Edgy on my laptop with no problems.

I wanted to install Ubuntu on my son's laptop but only had a 5.10 Breezy iso. I don't have a burner on my laptop to download the Edgy or Dapper iso.

Breezy has been installed with no problems everything works fine.

However, the CD iso I used is ages old, and yet update manager is saying my system is up to date, which surely must be wrong, as there have been tonnes of updates.

This means I can't get Dapper. Last time Breezy upgraded to Dapper easily: Update manager told me there was a new distro available. No such thing now. If I refresh it tells me my system is upto date.

I've tried: gksu “update-manager -d”

But I get the same message that my system is up to date.

Any idea how to get it working, or more importantly, how to upgrade to Dapper. I've read the Dapper upgrade guide, but just get my system is upto date.

I've checked my network. I am online.

Thanks.

  Check the /etc/apt/sources.list

Make sure it isn't just pointing to the cd. If it is and if you are not sure about making a new one then this link
may help 
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
Then from a terminal run sudo apt-get update
and sudo apt-get dist-upgrade

---

### Post by Tweedicus on 2007-01-12
For sudo apt-get update

I get:

$ sudo apt-get update
Password:
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages
Fetched 1B in 2s (0B/s)
Reading package lists... Done

For: gksudo gedit /etc/apt/sources.list

It's a blank. There's not a single word in my sources list.

---

### Post by Tweedicus on 2007-01-12
Then I get for sudo apt-get dist-upgrade:

~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by bscbrit on 2007-01-12
Search these threads for an example of a typical sources.list.  Copy it and update using apt-get or synaptic. :-)

---

### Post by DougieFresh4U on 2007-01-12
you could copy and paste this into that blank sources list of yours(save) and do update and upgrade::                         ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by NeoLithium on 2007-01-12
Here's a copy of mine just in case, nothing fancy, just my basics:
```

neo@linux-notebook:~$ cat /etc/apt/sources.list

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://ca.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://ca.archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://ca.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://ca.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```

---

### Post by Tweedicus on 2007-01-12
I copy and pasted but it won't let me save the source list

---

### Post by NeoLithium on 2007-01-12
You have to use root access, open it from a terminal with this:
```

gksudo gedit /etc/apt/sources.list

```

Then copy, paste and save.

---

### Post by Tweedicus on 2007-01-12
That's what I thought and that's what I did. But I get the reply after copying and pasting:

Could not save the file "/home/mikailweir/'/etc/apt/sources.list'"

---

### Post by NeoLithium on 2007-01-12
Are you sure that you specifically used the command above? The way it looks is that it's trying to save it within your own /etc inside your home folder, which, isn't right; try this:
```

cd /etc/apt

gksudo gedit sources.list

```

---

### Post by DougieFresh4U on 2007-01-12
I'm not sure of the code, maybe one of the gurus can give for the 'nano' command and try that route

---

### Post by NeoLithium on 2007-01-12
The nano route would be 
```

sudo nano -w /etc/apt/sources.list

```

---

### Post by DougieFresh4U on 2007-01-12
> **NeoLithium said:**
> The nano route would be 
```

sudo nano -w /etc/apt/sources.list

```

Thanks!!

---

### Post by Tweedicus on 2007-01-12
OK. I used those two commands, then copied and pasted the source list on page one of this thread to my source.list.

This time it saved.

Then I did the following and got the following from terminal:

mikailweir@ubuntu:~$ sudo apt-get update
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages
Fetched 1B in 0s (2B/s)
Reading package lists... Done
mikailweir@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mikailweir@ubuntu:~$


Hold on. I just went back to my source.list so I could post that as well now it's copied and pasted, and it's empty again, even though I saved.

---

### Post by NeoLithium on 2007-01-12
No problemo. Hope it all works out for ya.

---

### Post by Tweedicus on 2007-01-12
Erm. I'm not sure if I gave you the wrong impression. But nothing's changed. It still isn't working, and won't upgrade

---

### Post by DougieFresh4U on 2007-01-12
Gone out of my league, sorry do not know how to help any more :(

---

### Post by Tweedicus on 2007-01-12
Thanks anyway

---

### Post by NeoLithium on 2007-01-12
I noticed when you posted your output from your update, it had breezy sources on there; try to copy and paste the dapper ones that were given to you; run a sudo aptitude update and try the dist-upgrade again...

---

### Post by Tweedicus on 2007-01-12
I did copy  the dapper lists. Here's my sources.list:

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


However, when I type from terminal

mikailweir@ubuntu:~$ gksudo gedit /etc/apt/sources.list

It's blank. 

Only when I do:

cd /etc/apt

gksudo gedit sources.list

Do I get the Dapper Sources listed above.

Don't know if this what is making the difference.


with my

---

### Post by NeoLithium on 2007-01-12
Hm, run a search for sources.list and see if you have a doppleganger of it somewhere, that's the only thing I can think of that would be giving you those weird results.

---

### Post by Tweedicus on 2007-01-12
When you say run a search, I presume you mean from Places -- Search for Files.

---

### Post by NeoLithium on 2007-01-12
Yes; make sure you also select "file system" in the LOOK IN area when you do as well, so you don't only search through your user folder.

---

### Post by Tweedicus on 2007-01-12
Ok. I searched for sources.list in File System and it spewed out a load of results. What am I looking for? I was going to post a screen shot but there are too many results.

---

### Post by NeoLithium on 2007-01-12
a load of results? I have 9 at best, which I have in the screenshot; make sure that in /etc/apt/ you only have 1 sources.list; it really just seems like for some reason, aptitude is looking at a blank version when it shouldn't be.

Another think you can try, is deleting the sources.list in that directory, and making a whole new one; but that would be a very last resort...

---

### Post by Tweedicus on 2007-01-12
Well I have 133 results for sources.list (this was a clean install of Breezy done only two hours ago)

And none of them are in a folder resembling /etc/apt.

In fact  etc is not mentioned in any of the locations for the 133 files. And I've attached a shot of the first few results.

---

### Post by Tweedicus on 2007-01-12
Sorry, Did a search for text contains sources.list.

Here's the results for file name sources.list.

---

### Post by NeoLithium on 2007-01-12
Ok that looks a little better. Just to make sure, copy and paste the output of this:
```

cat /etc/apt/sources.list

```

---

### Post by Tweedicus on 2007-01-12
mikailweir@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
mikailweir@ubuntu:~$

---

### Post by obsidion on 2007-01-12
Ok open a terminal, don't use the gksu etc that you have been using and we may get to the bottom of things. Once the terminal is open cd /etc/apt

Once there type ls or dir 

there should be a sources.list

If there isn't then we could create one, either 
sudo pico sources.list and then paste one of those given to you or use the atomatic creator that I pointed you to earlier, the beauty of using that is that you customise it for your own country and the type of repos you want.

Once all that is done sudo apt-get update
and ten sudo apt-get dist-upgrade

Forget about aptitude for the moment, it seems to be playing up a bit on your system anyway

---

### Post by Tweedicus on 2007-01-12
Here's the outcome:

mikailweir@ubuntu:~$ cd /etc/apt
mikailweir@ubuntu:/etc/apt$ dir
apt.conf.d   'sources.list'  sources.list.save  trusted.gpg
secring.gpg  sources.list    trustdb.gpg        trusted.gpg~
mikailweir@ubuntu:/etc/apt$

---

### Post by Tweedicus on 2007-01-12
Then for sudo pico sources.list 

I get:

 GNU nano 1.3.8             File: sources.list

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main $

## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted multive$              [ line 1/37 (2%), col 1/90 (1%), char 0/1963 (0%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

---

### Post by obsidion on 2007-01-12
> **Tweedicus said:**
> mikailweir@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
mikailweir@ubuntu:~$

   Use sudo pico from a terminal, I like it better than nano, F2 will close and prompt for a save rather than the ctrl keypresses needed in nano.

Un # the updates and security repos for a start. Since that is there you must not have been typing the commands you said you had earlier. Either that or gedit is just not doing its job properly, use the command line method I suggested you will hopefully have more luck. You could go straight to dapper here by replacing the work breezy with dapper

---

### Post by Tweedicus on 2007-01-12
> **Tweedicus said:**
> Then for sudo pico sources.list 

I get:

 GNU nano 1.3.8             File: sources.list

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main $

## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted multive$              [ line 1/37 (2%), col 1/90 (1%), char 0/1963 (0%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

In the output above I changed everything to Dapper. From terminal it's now downloading 484 mb of an upgrade. And Update Manager has suddenly kicked in and has started working. It seems to have done the trick and started working. Thank you very much, both of you. I did enter the text in the previous posts, but it seems there was a problem with gedit, even though it said it was saving, and I was in as root. Thanks once again

Scrolling through the other threads, it seems as if a number of users have had a problem upgrading from Breezy to Dapper SINCE Edgy was released. I upgraded from Breezy to Dapper on this computer once before, before Edgy was released and there were no problems. It seems that the update manager in Breezy now points to Edgy as the distro upgrade, though of course you can't upgrade straight to Edgy, and Dapper has been missed out.

---

