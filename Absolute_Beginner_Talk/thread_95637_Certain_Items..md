---
title: "Certain Items."
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by snoboy939 on 2005-11-27
Ok, i got fedup with windows screwing over my system. (It randomly partitioned my harddrive and wouldn't accept any cd drives)
I installed Ubuntu, and it looks awesome!
I just have some questions.

How would i utilize MSN correctly with Ubuntu?
I try to play mp3's i had on a cd, and it says 
"There were no decoders foudn to handle the stream, you might need to install the corresponding plugins."
same with video's also.
How would i play games also? (Counterstrike Source, WOW, Guild Wars)
thanks for any help :)

---

### Post by amohanty on 2005-11-27
How would i utilize MSN correctly with Ubuntu?

Look at Applications->Internet->Gaim Internet Messenger

I try to play mp3's i had on a cd, and it says
"There were no decoders foudn to handle the stream, you might need to install the corresponding plugins."
same with video's also.

You need to install w32codecs and libdvdcss2 
Add these to your repositories:

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

and install them through synaptic. Also look around the forums. There is tons of help in this matter.


How would i play games also? (Counterstrike Source, WOW, Guild Wars)

I have used Cedega successfully. Its Winex with some extras. Costs about 5 bucks a month to be a member and get updates. Available at transgaming.com.

HTH
AM

---

### Post by snoboy939 on 2005-11-27
[QUOTE=amohanty]How would i utilize MSN correctly with Ubuntu?

Look at Applications->Internet->Gaim Internet Messenger

I try to play mp3's i had on a cd, and it says
"There were no decoders foudn to handle the stream, you might need to install the corresponding plugins."
same with video's also.

You need to install w32codecs and libdvdcss2 
Add these to your repositories:

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

and install them through synaptic. Also look around the forums. There is tons of help in this matter.

HTH
AM[/QUOTE]
i have no internet under applications....
and
what do i do in those URL's? (what do i click on?)

---

### Post by amohanty on 2005-11-27
What version of Ubuntu are you running?
Are you running Kubuntu by any chance?

what do i do in those URL's? (what do i click on?)

You have fire up Synaptic (System->Administration->Synaptic Package Manager)
then goto Settings->Repositories->Add->Custom and paste the entire line:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
do it again for:
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

click on ok and it will update itself. and then click on search to look for the packages.

HTH
AM

---

### Post by snoboy939 on 2005-11-27
i search for them but a big list comes up, what do i do?
i believe im running Ubuntu 5.10 but i did update it fully.

---

### Post by amohanty on 2005-11-27
ok so when you searched for w32codecs there should only be one package shown. 
what are you getting?

Alternatively goto: Applications->Accessories->Terminal

type in :
sudo apt-get update

provide your password and press enter.

Then type in:
sudo apt-get install w32codecs
and do the same.

HTH
AM

---

### Post by snoboy939 on 2005-11-27
Okay, im kinda lost now.
i did the link thing.
and now i have the search thing up for the first time, what do i do
and what should i look for in the list

---

### Post by amohanty on 2005-11-27
So you did this:

1. Fire up Synaptic (System->Administration->Synaptic Package Manager)
2. Goto Settings->Repositories->Add->Custom and paste the entire line:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
do it again for:
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
3. Click on ok and it will update itself. 
4. Click on search to look for the packages.

Type in the pop up box:
w32codecs

The screen on the right should show a single line, with an empty check box 
Click on the check box, it should have check mark on it.

Thenk click on the Apply Changes button on the toolbar.

HTH
AM

---

### Post by snoboy939 on 2005-11-27
i searched for both
w32codecs
and just w32
and nothing appeared.

---

### Post by amohanty on 2005-11-27
try this then:

Alternatively goto: Applications->Accessories->Terminal

type in :
sudo apt-get update

provide your password and press enter.

Then type in:
sudo apt-get install w32codecs
and do the same.

---

### Post by snoboy939 on 2005-11-27
steve@Sheila:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Fetched 19.8kB in 1s (11.9kB/s)
Reading package lists... Done
steve@Sheila:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs
steve@Sheila:~$

my computer name is sheila by the way.

---

### Post by aysiu on 2005-11-27
To play MP3s, you don't need w32codecs.
According to [https://wiki.ubuntu.com/RestrictedFormats:](https://wiki.ubuntu.com/RestrictedFormats:)
> If you live in a country where it is legal to play MP3s and other non-free media formats without a license,  enable the universe and multiverse repositories, and install the support packages by typing in a terminal:
```

sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
``` 

That said, I did notice w32codecs in the plf repositories (see screenshot).
Please visit the Wiki link I mentioned before.

---

### Post by snoboy939 on 2005-11-27
steve@Sheila:~$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
steve@Sheila:~$

---

### Post by amohanty on 2005-11-27
Ok you have to enable the repositories that you just added.

In Synaptic:
Goto: Settings->Repositories
Click on the settings buttons

Check off Show Disabled Software Sources
Click OK


Now scroll to the bottom of the list and make sure the new links you added are checkde off, and do thw whoel search thing again.

If that doesnt work please post the contents of your  /etc/apt/sources.lst file here.

AM

---

### Post by aysiu on 2005-11-27
Okay, you've got to have the right repositories first before you can *sudo apt-get install* anything. Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by snoboy939 on 2005-11-27
steve@Sheila:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
steve@Sheila:~$

---

### Post by aysiu on 2005-11-27
Yup. You don't have Universe enabled.

Can you follow the instructions in the first link in my signature **exactly** as they're written?

This will do two things:
1. Make a backup copy of your original sources.list
2. Give you an updated sources.list with the extra repositories you'll need to enable MP3 support

Once you're done with that, then copy and paste these commands into a terminal: ```
sudo apt-get update
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
gst-register-0.8
```

---

### Post by amohanty on 2005-11-27
Uncomment these lines ie remove the preceding '#' charachter:

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

TO do so at the command prompt type:
sudo gedit /etc/apt/sources.lst

HTH
AM

---

### Post by snoboy939 on 2005-11-27
i did that and a window poped up with nothing in it called sources.lst

---

### Post by amohanty on 2005-11-27
I think you better follow aysiu's instructions as they are easier to follow than my sleep-muddled ones.

AM

---

### Post by snoboy939 on 2005-11-27
i..i..did.
godammit, ima loser.
i dont understand any of this at all.

---

### Post by aysiu on 2005-11-27
[QUOTE=snoboy939]i..i..did.
godammit, ima loser.
i dont understand any of this at all.[/QUOTE] There are basically three parts to the instructions, if you look at them closely.

The first part backs up your sources list and lets you edit it.
*cp* means *copy*
*gedit* means *open the following file with the text editor*

So, *sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup* means "Create a backup copy of my sources.list"
*sudo gedit /etc/apt/sources.list* means "Edit the sources.list"

The second part gives you a more up-to-date repository list, with extra repositories. You put that in your sources.list file. Then you update.

The last part is a workaround because some people were still experiencing problems. It involves backing up the newly created list, emptying out the old list, updating, and putting the new list back.

If you do steps #1 and #2, you're fine.
If you do step #3 as well, you have to follow it all the way to the end, including the part where you copy the new list back. I suspect you may have emptied out the list without restoring the newly created one.

Bottom line: if you've done everything correctly, you should be able to type ```
cat /etc/apt/sources.list
``` and have this come out: ```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
``` *cat* means "list what's in this file."

---

### Post by amohanty on 2005-11-27
cmon man dont beat yourself up. everybody here learned it the same way. and it was my mistake :

do the following:

sudo gedit /etc/apt/sources.list

as you can see I pointed you to the wrong file.
bad typo on my part. sorry about that.

AM

---

### Post by snoboy939 on 2005-11-27
i did the change the # things like you said. so it now appears like this
steve@Sheila:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
steve@Sheila:~$



now what am i doing.

---

### Post by amohanty on 2005-11-27
Now follow aysiu's instructions in post #17.

AM

---

