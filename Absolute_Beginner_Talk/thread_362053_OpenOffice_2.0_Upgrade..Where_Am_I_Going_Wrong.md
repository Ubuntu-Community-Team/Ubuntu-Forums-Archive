---
title: "OpenOffice 2.0 Upgrade..Where Am I Going Wrong?"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by IronMac on 2007-02-15
HI all,

I'm following these instructions to upgrade to OO 2.0 from 1.9.129:

In SPM:

Click Settings > Repositories, and then click the Add button
Click the Custom button. In the APT line box of the dialog box, enter the following:

[http://people.ubuntu.com/~doko/00o2](http://people.ubuntu.com/~doko/00o2) ./

Click the Add Repository button
Click Ok in the Software Preferences dialog box. Then click the Yes button to reload the package list.
Close the SPM

My biggest problem is that there is no "Yes" button from that second to last line. Thanks!

P.S. This is for 5.10.

---

### Post by louis_nichols on 2007-02-15
Hm... I think there have been some small changes in the GUI of synaptic since 5.10, so I'm not really sure, but if you manage adding the repository, you should then just be able to click a button "reload" on the main interface of Synaptic. Or, you can use

$ sudo apt-get update

in a terminal. One thing to check, when using the ***add repository ***option in synaptic or the option ***software sources*** in the system menu is that entries there, afaik, should also have *deb* in front. So your entry should be:

deb [http://people.ubuntu.com/~doko/00o2](http://people.ubuntu.com/~doko/00o2) ./

There is another way to all this. You can add the repository manually to sources.list like this:

[LIST=1]
[*]$ gksudo gedit /etc/apt/sources.list

[*]add the line *deb [http://people.ubuntu.com/~doko/00o2](http://people.ubuntu.com/~doko/00o2) ./* at the end of the file
[*] use *sudo apt-get update* in terminal
[*] use whatever means to perform the actual upgrade of the packages
[/LIST]

---

### Post by IronMac on 2007-02-15
> **louis_nichols said:**
> Hm... I think there have been some small changes in the GUI of synaptic since 5.10, so I'm not really sure, but if you manage adding the repository, you should then just be able to click a button "reload" on the main interface of Synaptic. Or, you can use

$ sudo apt-get update

in a terminal. One thing to check, when using the ***add repository ***option in synaptic or the option ***software sources*** in the system menu is that entries there, afaik, should also have *deb* in front. So your entry should be:

deb [http://people.ubuntu.com/~doko/00o2](http://people.ubuntu.com/~doko/00o2) ./

There is another way to all this. You can add the repository manually to sources.list like this:

[LIST=1]
[*]$ gksudo gedit /etc/apt/sources.list

[*]add the line *deb [http://people.ubuntu.com/~doko/00o2](http://people.ubuntu.com/~doko/00o2) ./* at the end of the file
[*] use *sudo apt-get update* in terminal
[*] use whatever means to perform the actual upgrade of the packages
[/LIST]

Thanks. I tried the "deb" option in SPM and it doesn't work. I get an error saying that the repository couldn't be found. I was hoping for a simple say of doing this since I'm a total n00b at all of this.

---

### Post by louis_nichols on 2007-02-15
But it IS simple. OK, so the deb in SPM doesn't work. But the command line way should. If nothing else, just copy/paste this in terminal:

sudo echo -e "##Openoffice 2.x\n deb [http://people.ubuntu.com/~doko/00o2](http://people.ubuntu.com/~doko/00o2) ./" >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get upgrade

It will ask for your password and then for a couple of confirmations and voila.

---

### Post by IronMac on 2007-02-15
Ok, I tried the Terminal route and it didn't work. I am getting the following error (both in SPM and in Terminal):

Failed to fetch [http://people.ubunto.com/~doko/OOo2/](http://people.ubunto.com/~doko/OOo2/) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat  (2 No such file or directory)

---

### Post by louis_nichols on 2007-02-15
True. That's a typo. The repository is in the domain ubuntu.com, but your command reads ubunto.com.

This raises the small problem of correcting the wrong repository and trying again. here are the steps to do it:

[LIST=1]
[*]in terminal, type:
```
gksudo gedit /etc/apt/sources.list
```
[*]go to the end of the file and correct this address, then save and close the file
[*]in terminal, type
```
sudo apt-get update && sudo apt-get upgrade
```
[/LIST]

Then you should be alright.

---

### Post by IronMac on 2007-02-15
Ok...I typed in the first command in the Terminal and I am getting the following:

(gedit: 7315): GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

In post #5, I may have typed in the "ubunto" by mistake since I could not figure out how to copy and paste from Terminal.

---

### Post by louis_nichols on 2007-02-15
The error you get isn't very relevant and can be safely ignored. Gedit will still open the file and let you edit and save it, then follow the next steps.

---

### Post by IronMac on 2007-02-15
Ok, I'm sorry but I am now looking at a box with the title on top:

*sources.list' (/home/ironmac/'/etc/apt) - gedit

Not sure how to go on from there and follow the rest of the instructions "open the file and let you edit and save it, then follow the next steps."?

---

### Post by louis_nichols on 2007-02-15
that's a typo in the console again. copy/pasting in terminal is as easy as selecting the text in firefox and then making a middle-click in the terminal window. Sorry for not mentioning this earlier.

you can safely close this window and then typing the correct command in terminal.

---

### Post by IronMac on 2007-02-15
Ok, I've figured out how to copy and paste (boy, do I feel stupid in that sense!).

I've closed that gedit window:

> *sources.list' (/home/ironmac/'/etc/apt) - gedit

I then tried the following command:

> sudo echo -e "##Openoffice 2.x\n deb [http://people.ubuntu.com/~doko/00o2](http://people.ubuntu.com/~doko/00o2) ./" >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get upgrade

That gives me:

> bash: /etc/apt/sources.list: Permission denied

I think I am missing a step here...  :(

---

### Post by louis_nichols on 2007-02-15
Hm... That's my mistake over there. I thought it should work.

The thing is that a regular user can't modify the file /etc/apt/sources.list. One needs to be root for this. Ok. I'll give you the not ellegant solution to this, because I'm not at my machine right now and can't figure out the right way.

So.. do this: in console type

sudo su

then press enter. It will ask you for your password and then you will be root. After this, copy/paste the command I wrote above and should be ok.

---

### Post by IronMac on 2007-02-15
@#$%

Did that and got a whole bunch of "Failed" messages.  :confused:

---

### Post by SunnyRabbiera on 2007-02-15
try sudo apt-get update
that sometimes fixes the repo's

---

### Post by IronMac on 2007-02-15
Nope, that didn't work. Here are the messages:

> Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg                                    sGet:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [191B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Err [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Err [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Fetched 3B in 0s (3B/s)
Failed to fetch [http://people.ubuntu.com/~doko/00o2/./Packages.gz](http://people.ubuntu.com/~doko/00o2/./Packages.gz)  404 Not FoundFailed to fetch [http://people.ubuntu.com/~doko/00o2/./Packages.gz](http://people.ubuntu.com/~doko/00o2/./Packages.gz)  404 Not FoundReading package lists... Done
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_00o2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_00o2_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by louis_nichols on 2007-02-15
OK! These typos are killing us! :)
the reason it doesn't work is there is a space missing between 
[http://people.ubuntu.com/~doko/00o2/](http://people.ubuntu.com/~doko/00o2/)
and
./
in sources.list

so now we really are back to editing /etc/apt/sources.list to correct the problem and then run

sudo apt-get update && sudo apt-get upgrade

again.

And, PLEASE, be very attentive to typos!!

EDIT: some of the problems there are not related to the problem we are discussing. For some reason, you have another invalid entry in sources.list, which is a line with  [http://people.ubuntu.com](http://people.ubuntu.com). when you edit the file, make sure to remove that line, too.

---

### Post by IronMac on 2007-02-15
Ok, I am now absolutely confused here. I am back in root but I have no clue as to how to edit the /etc/apt/sources.list file you're talking about.  :confused: 


> **louis_nichols said:**
> OK! These typos are killing us! :)
the reason it doesn't work is there is a space missing between 
[http://people.ubuntu.com/~doko/00o2/](http://people.ubuntu.com/~doko/00o2/)
and
./
in sources.list

so now we really are back to editing /etc/apt/sources.list to correct the problem and then run

sudo apt-get update && sudo apt-get upgrade

again.

And, PLEASE, be very attentive to typos!!

EDIT: some of the problems there are not related to the problem we are discussing. For some reason, you have another invalid entry in sources.list, which is a line with  [http://people.ubuntu.com](http://people.ubuntu.com). when you edit the file, make sure to remove that line, too.

---

### Post by IronMac on 2007-02-15
Ok, never mind. I don't know what I did but it looks like I may have gotten SPM to update OpenOffice...bbl to give everyone an update.

I think that the main typo was in the line where it was supposed to be [http://people.ubuntu.com/~doko/00o2/](http://people.ubuntu.com/~doko/00o2/), I had put in 00 rather than OO or OO rather than 00. Numbers versus alphabet. SPM is now downloading 16 updates.

---

### Post by IronMac on 2007-02-15
Success!!!!!!!!!!

Whew!!! Those typos were really killing us!!! :mad: 

OO 2.0 has been installed successfully!!! Thanks to everyone, especially louis_nichols who's not even at his machine, for the assist!  :popcorn:

---

### Post by louis_nichols on 2007-02-15
phew! that's a relief! :) \\:D/ 

thanks for the popcorn! ;)

Just out of curiosity: why don't you upgrade your whole system? If I remember well, 5.10 is not even supported anymore. All other versions of Ubuntu have OpenOffice 2.x by default and many other improvements (I can tell: I started with breezy and now I'm using edgy).

The upgrade might not be a very lean process, but at least you do it once and then are worry-free for quite a while.

---

### Post by IronMac on 2007-02-15
> **louis_nichols said:**
> Just out of curiosity: why don't you upgrade your whole system? If I remember well, 5.10 is not even supported anymore. All other versions of Ubuntu have OpenOffice 2.x by default and many other improvements (I can tell: I started with breezy and now I'm using edgy).

The upgrade might not be a very lean process, but at least you do it once and then are worry-free for quite a while.

I have 5.10 only because the CD that came with the book (Beginning Ubuntu Linux) comes with Breezy Badger. I was reading through the OO part and decided to upgrade on the spot instead of waiting for a later version of the distro.

I'm pretty sure that I will be back here eventually.  :lolflag:

---

### Post by Slokar on 2007-02-15
Hi!

I'm new to this community, but I like it very much so far. I chose Ubuntu as my primary OS and I'm still learning, but so far it's pretty cool. I was just wondering why there is no "ubuntu update for OpenOffice". The one listed in ubuntu is still 2.0.4 but 2.1 is out already for a very long time. I'm trying to pick up all the tar,gz stuff, but so far the easiest way to do anything was with deb or synaptic package manager. Anyway, I just wanted to ask why there is still no update on that aspect and didn't want to open a new topic just for that.....

Slokar

---

### Post by Maestro23 on 2007-02-15
> **Slokar said:**
> Hi!

I'm new to this community, but I like it very much so far. I chose Ubuntu as my primary OS and I'm still learning, but so far it's pretty cool. I was just wondering why there is no "ubuntu update for OpenOffice". The one listed in ubuntu is still 2.0.4 but 2.1 is out already for a very long time. I'm trying to pick up all the tar,gz stuff, but so far the easiest way to do anything was with deb or synaptic package manager. Anyway, I just wanted to ask why there is still no update on that aspect and didn't want to open a new topic just for that.....

Slokar

I installed OO 2.1 last night from source using the thread below.  Installed with no problems at all.  If you want the newest office, give it a try.  Look for the directions by [COLOR="Red"]sgla1.[/COLOR]

[http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=Install+OpenOffice](http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=Install+OpenOffice)

It's not hard, just follow the directions.  You can even cut/past the terminal commands if you want.

Good luck.

---

### Post by Slokar on 2007-02-15
Works perfectly. 

THANK YOU!!!

Slokar

---

