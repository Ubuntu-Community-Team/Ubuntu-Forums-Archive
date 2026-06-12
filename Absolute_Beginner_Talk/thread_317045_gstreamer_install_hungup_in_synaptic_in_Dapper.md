---
title: "gstreamer install hungup in synaptic in Dapper"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Lost Traveler on 2006-12-11
My computer was a game box and has ample resources. No problem there.  Dapper Drake installed from Ubuntu CD.  I have been using book, UBUNTU LINUX FOR NON GEEKS, by Rickford Grant.  On page 241 of the book I used Synaptic search for 'gstreamer' which Synaptic found.  I attempted to do an install.  The install failed.
An Error Box appeared:
   The following problems were found on your system:
     E:Type 'gstreamer0.10-plugins' is not known on line 34 in
     source/etc/apt/source.list
     E:The list of sources could not be read.  Go to the repository dialog to correct the problem.

When I tried to use Add/Remove in the Applications list it showed:   Error Dialog box:
  Failed to check for installed and available applications.  
This is a major failure of your software management system.  Check the file permissions and correctness of the file, '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

This is more than I know how to do.  Can I somehow delete or remove this 'gstreamer' software and go on with my computer life?  If no one answers this post I will understand.  I could do a complete reinstall of Ubuntu to fix the problem, but that seems a tad drastic.  Thanks for any advice.

---

### Post by Ecthelion on 2006-12-12
> An Error Box appeared:
The following problems were found on your system:
E:Type 'gstreamer0.10-plugins' is not known on line 34 in
source/etc/apt/source.list
E:The list of sources could not be read. Go to the repository dialog to correct the problem.

> This is a major failure of your software management system. Check the file permissions and correctness of the file, '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

Did you tried to do 'sudo apt-get update' ?

Also, it might be usefull if you posted your /etc/apt/sources.list on the forum.

Just do
```
gedit /etc/apt/sources.list
```
in a terminal and copy-paste the text you get...

---

### Post by Lost Traveler on 2006-12-12
Thanks for the advice.  I will see what I can find and I will paste it here.

---

### Post by Lost Traveler on 2006-12-12
First I tried 'sudo apt-get update' but I do not think I entered it correctly as the prompt reset.  More luck with 'gedit /etc/apt/sources.list'.  Here is what sources.list returned:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

gstreamer0.10-plugins

Now do I still need to 'sudo apt-get update and if so, how do I do this?  Did I not insert a necessary space in this command?  I am not sure.  Anyway, Thanks for your help.

---

### Post by Lost Traveler on 2006-12-12
Here is what I got when I entered 'sudo apt-get update' in the Terminal.


srdouglas@srdouglas-desktop:~$ sudo apt-get update
Password:
E: Type 'gstreamer0.10-plugins' is not known on line 34 in source list /etc/apt/sources.list
srdouglas@srdouglas-desktop:~$

---

### Post by Ecthelion on 2006-12-13
Hey,

I'm really wondering what that line 
gstreamer0.10-plugins
is doing in your sources.lst

Could you remove or comment out that line?

To be able to modify your sources.lst you have to use sudo in your command:
```
sudo gedit /etc/apt/sources.list
```
uncomment (with ##) the line and save.

Then try
```
sudo apt-get update
```
again.

If you get no error, try again to install your gstreamer via Synaptic.

---

### Post by Lost Traveler on 2006-12-13
No doubt 'gstreamer0.10-plugins' got into the sources.list because I done something very stupid....that is all I can imagine.  You are talking to someone who is very newbie and using the Ubuntu Linux For Non Geeks book to get around. I will try to be more careful of what I am looking at before doing an action that could mess things up.  I will try to follow your advice without doing more damage.  Thanks for your advice.  I will report back on how well I did.

---

### Post by Lost Traveler on 2006-12-13
Many Thanks Ecthelion,
   Your advice won the day with this newbie.  Everything is back to normal with the Linux box.  Now, I will study carefully my next move with 'gstreamer' or anything like it before committing an action. Can you close this posting or do I do it?
Anyway, Thanks!
Lost Traveler

---

### Post by Lost Traveler on 2006-12-13
I might add that using the commands you offered I was able to comment out the 'gstreamer' line from the sources.list.  Everything worked as advertised with no errors during the update.
Many thanks.
Lost Traveler

---

### Post by Ecthelion on 2006-12-14
> Many Thanks Ecthelion,

Your welcome

> Can you close this posting or do I do it?

You can put this thread as "solved"
To do that, click to edit your first post,
click on "go advanced" and check the button wich says "thread resolved"

---

