---
title: "INTERESTING OS: I CAN'T watch DVD's, I can't run my WEBCAM"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Jah Jah Binks on 2006-06-04
Can I at least convert AVI's to DVD format with a program like WINAVI?

---

### Post by carlosqueso on 2006-06-04
[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restrictedformats%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restrictedformats%29)

will both explain why and help you be able to.

---

### Post by MetalMusicAddict on 2006-06-04
[QUOTE=Jah Jah Binks]INTERESTING OS: I CAN'T watch DVD's, I can't run my WEBCAM[/QUOTE]
Is this scarcasim? Condecention? _Ask for help_ and _read_. Your webcam might not work in linux. Just the way it is.

---

### Post by Jah Jah Binks on 2006-06-04
I have read it's just that the solutions never work. My webcam supposedly works but the tutorial always fails for some obscure reason. You have to admit this is not the most user friencly OS.

---

### Post by halitech on 2006-06-04
well Jah Jah, I've made the complete switch from windows to Ubuntu with very few difficulties. Sorry to hear you are having trouble but I'm sure if you provide a few more details like the brand of webcam, what format the mvies are in that someone here wil lbe able to help you out. off the top of my head, I'd suggest trying the info here: [http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux") if  you feel confident enough to try the CLI, if not, rty grabbing a copy of DeVeDee or Tovid to convert your movies.

hth

---

### Post by dvarsam on 2006-06-04
To play DVD's with the Totem player, install the package named "totem-xine-firefox-plugin".
Then, you should be all set!

---

### Post by MetalMusicAddict on 2006-06-04
[QUOTE=Jah Jah Binks]I have read it's just that the solutions never work.[/QUOTE]
*Sometimes* its user error. ;) Youll get out of it what you put into it. I replied to the thread where you were getting help for you webcam.

---

### Post by Jah Jah Binks on 2006-06-04
[QUOTE=MetalMusicAddict]*Sometimes* its user error. ;) Youll get out of it what you put into it. I replied to the thread where you were getting help for you webcam.[/QUOTE]
I followed the tutorial and what you said but continually get errors:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package easycam

That's the last error i got.

---

### Post by Jah Jah Binks on 2006-06-04
Oh yeah here is the TUTORIAL i'm using: [https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

Pretty straightforward and I've followed the steps exactly and still get the error.

---

### Post by MetalMusicAddict on 2006-06-04
[QUOTE=Jah Jah Binks]I followed the tutorial and what you said but continually get errors:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package easycam

That's the last error i got.[/QUOTE]
User error. You didnt follow the WIKI instructions that you referenced.
[QUOTE=Jah Jah Binks]Alrighty then could someone walk me through this then?

[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)[/QUOTE]

From the WIKI:
------------------------------------------------------------------------------
_Installation_

Add the following line to your /etc/apt/sources.list

**deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main**

Then you need to update the packages and install easycam

```
sudo apt-get update
sudo apt-get install easycam2
```
------------------------------------------------------------------------------

This assumes you have a certin level of knowlege. If you dont have that knowlege, ask or better yet, read to get it.

---

### Post by Perfect Storm on 2006-06-04
Did you ran:
```

sudo apt-get update

```

afterwards you added deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main to your repo?

---

### Post by dvarsam on 2006-06-04
[QUOTE=Jah Jah Binks]
E: Couldn't find package "easycam"[/QUOTE]

To be able to install the package "easycam2", add these lines to your "/etc/apt/sources.list" file:

> ## This is required if you would like to install a Webcam.
## The Repo below, helps you locate & install the required package 
## named "easycam2".

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

To edit your "/etc/apt/sources.list" file:

1. Just launch a Terminal window & type:

> nano /etc/apt/sources.list

2. Then add the lines (I provided above)

3. When finished press "Ctrl+X" & then "Y" (to save changes).

Then, launch your "Synaptic Package Manager" & click on the "reload" button (same as "apt-get update" from the Terminal)...

Then perform a search for the package "easycam2" (from Synaptic)

Install it & you are all set!

Good Luck!

P.S.> DO NOT MAKE ANY TYPOS!!!!!!!

---

### Post by Jah Jah Binks on 2006-06-04
You see now I'm lost. Where did all this extra stuff come form?

---

### Post by halitech on 2006-06-04
here are the steps I followed:

1. sudo gedit /etc/apt/sources.list

2. added 

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

to the list

3. sudo apt-get update

4. sudo apt-get install easycam2

5. started easy cam 2 by going to system -> administration -> easycam2

seems the new version even has support for my old 3com lite :)

---

### Post by MetalMusicAddict on 2006-06-04
Ill through you 1 bone. Please learn from it.

Reading through the forums you will see **sources.list** referenced _alot_. Its a very important file you will need to edit from time to time. In Ubuntu you dont have write access to it. To get write access to it open a terminal window and paste in this command _exactly_.
```
sudo gedit /etc/apt/sources.list
```
[LIST]
[*]**sudo** gives you root access
[*]**gedit** is a text editor
[*]**/etc/apt/sources.list** is the path to the file
[/LIST]

It will open up the file and add this line to that file. At the bottom, it doesnt matter.

**deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main**

Save the file and the issue these 2 commands.

```
sudo apt-get update
sudo apt-get install easycam2
```

[QUOTE=Jah Jah Binks]You see now I'm lost. Where did all this extra stuff come form?[/QUOTE]
There are many ways to do things.

---

### Post by Jah Jah Binks on 2006-06-04
Another error. When I open Synaptic Manager:

E: Type 'o' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by dvarsam on 2006-06-04
...And my approach was a little differect compared to the one suggested by the rest of the people here...

For example:

> **sudo** gives you root access
**gedit** is a text editor
**/etc/apt/sources.list** is the path to the file

Instead of using the > **gedit** text editor

I suggested to you to use the:

> **nano** text editor

It is up to you, which Editor you prefer...

The rest remains the same, even though, instead of suggesting typing the "apt-get update", I suggested you "update" from the Menu, by launching the "Synaptic Package Manager" (from the Menu, you can select "System/Administration/Synaptic Package Manager")...

The process is the same, it is up to you which way you want/prefer to go...

Good Luck!

P.S. 1> Hey man, you have learned to do it in 2 ways...

P.S. 2> I wish I had _ALL_ these folks reply to me so fast (with loads of info), back in February, when I started off... :) Not that I did NOT, but the SPEED is so much faster now...!!!

---

### Post by Jah Jah Binks on 2006-06-04
I appreciate everyones help. I haven't slept in 2 days so forgive me if I'm wound a little tight. Any help with this error:

E: Type 'o' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by dvarsam on 2006-06-04
[QUOTE=Jah Jah Binks]Another error. When I open Synaptic Manager:

E: Type 'o' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/QUOTE]

You have probably made a "typo" error in your "/etc/apt/sources.list"

OR:

You added an "o" letter by mistake, somewhere where you shouldn't have!

Anyway, just copy&paste all your "/etc/apt/sources.list" file in here & maybe we can see what you have typed wrong...

Bring it in!

---

### Post by Jah Jah Binks on 2006-06-04
[QUOTE=dvarsam]You have probably made a "typo" error in your "/etc/apt/sources.list"

OR:

You added an "o" letter by mistake, somewhere where you shouldn't have!

Anyway, just copy&paste all your "/etc/apt/sources.list" file in here & maybe we can see what you have typed wrong...

Bring it in![/QUOTE]

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
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

#created by arniedappersecond

---

### Post by dvarsam on 2006-06-04
The only error I got from using your "sources.list" file (when on the standard toolbar I click on the "reload" button), is the following:

> W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)


You might have the same line twice in your "sources.list" file...

I am NOT going to bother to fix your "sources.list" file...

I am just going to give you mine:

> # For Ubuntu v6.06 - Dapper Drake:
# -------------------------------

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper universe


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


## This was added (as  asked)
## Multiverse

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse


## This is required if you would like to install a Webcam.
## The Repo below, helps you locate & install the required package 
## named "easycam2".

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

## Backports:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

So, just delete _ALL_ the contents of your "/etc/apt/sources.list" file & replace with the above I supplied!

Save & Exit your Editor.

On Synaptic Package Manager perform a "reload"...

On Synaptic's Standard Toolbar, click on the button named "Search"

And type the name of the package you are looking for (e.g. easycam2)...

Select it, mark it for Installation, Click on the button named "Apply" & wait until the package gets installed...

Then from the Menu, click on "System/Administration/Easycam2"...

You will end-up running the program!

Good Luck!

---

### Post by Jah Jah Binks on 2006-06-04
All good until I got to here:

[QUOTE=dvarsam]
Then from the Menu, click on "System/Administration/Easycam2"...

You will end-up running the program!

Good Luck![/QUOTE]

Gave me error message:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ln: creating symbolic link `/lib/modules/2.6.15-23-386/build' to `/usr/src/linux-headers-2.6.15-23-386': File exists
ERROR: Module uvcvideo does not exist in /proc/modules
mkdir: cannot create directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media-back': File exists
cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/ov511'
cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/podxtpro'
cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/pwc'cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/quickcam'
cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/spca5xx'
mknod: `/dev/video0': File exists
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
rm -f *.o *.ko .*.cmd .*.flags *.mod.c
rm -rf .tmp_versions
Installing USB Video Class driver...
/bin/sh: line 0: cd: /lib/modules/2.6.15-23-386/build: No such file or directorymake: *** [install] Error 1

---

### Post by dvarsam on 2006-06-04
Sorry man, but I have no clue regarding your specific error!

Hopefully somebody more expert than me could help you with this!

Good Luck!

P.S.> By the way: Did you connect your Webcam, before running the program (from the Menu)?

---

### Post by Jah Jah Binks on 2006-06-04
[QUOTE=dvarsam]Sorry man, but I have no clue regarding your specific error!

Hopefully somebody more expert than me could help you with this!

Good Luck!

P.S.> By the way: Did you connect your Webcam, before running the program (from the Menu)?[/QUOTE]

Yes I did thanks anyway it looks like it's back to Windows for me.

---

### Post by shamrock_uk on 2006-06-04
[QUOTE=Jah Jah Binks]All good until I got to here:



Gave me error message:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ln: creating symbolic link `/lib/modules/2.6.15-23-386/build' to `/usr/src/linux-headers-2.6.15-23-386': File exists
ERROR: Module uvcvideo does not exist in /proc/modules
mkdir: cannot create directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media-back': File exists
cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/ov511'
cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/podxtpro'
cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/pwc'cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/quickcam'
cp: omitting directory `/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/spca5xx'
mknod: `/dev/video0': File exists
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
rm -f *.o *.ko .*.cmd .*.flags *.mod.c
rm -rf .tmp_versions
Installing USB Video Class driver...
/bin/sh: line 0: cd: /lib/modules/2.6.15-23-386/build: No such file or directorymake: *** [install] Error 1[/QUOTE]

Just a thought, but what happens when you run that command as root? The first couple of lines seem to show a lack of access to the package list.

---

### Post by MetalMusicAddict on 2006-06-04
Too bad. Bye.

---

### Post by Jah Jah Binks on 2006-06-04
I'm sure you're sorry to see me go Metal Addict. Just a little tip for you: when someone posts in a forum titled ABSOLUTE BEGINNER TALK maybe you should try showing a little more patience. Bye.

---

### Post by Nikusan on 2006-06-05
[QUOTE=Jah Jah Binks]I'm sure you're sorry to see me go Metal Addict. Just a little tip for you: when someone posts in a forum titled ABSOLUTE BEGINNER TALK maybe you should try showing a little more patience. Bye.[/QUOTE]

When you post in a forum where people VOLUNTEER THEIR TIME TO HELP YOU maybe you should try showing a little more politeness. Bye.

---

### Post by nalmeth on 2006-06-05
Wow

Chill out people.

This crap doesn't solve the OP's issue and it doesn't make it worth anyone's time to spend lecturing a new guy, even if he's a little demanding. 
@ Jah Jah
The title of your thread is a little sarcastic/condescending. The people helping you here did not build this OS. We don't represent Canonical, we wander through here on our free time to help people out. Don't confuse us for the developer's.

You've come this far Jah Jah, let's not give up right now.

All that error sounds like permission errors (shamrok uk called that first_)_. Did you run it from the menu (following dvarsam's advice) or from the terminal? If you ran it from the menu, were you prompted for your password?

Possibly as a regular user you don't have permission's to this device yet, so let's try running easycam2 with admin priviledges, as shown previously when editing the sources.list file.

(For future reference, if you'd prefer a User Interface over a terminal for adding repositories, [read this thread]("http://ubuntuforums.org/showpost.php?p=993129&postcount=1"))

OK, so you know where the terminal is
```
sudo easycam2
``` will launch the app with admin priviledges.

Alternatively, you can do this graphically

hit ALT-F2
type this command:
```
gksudo easycam2
``` 
gksudo is essentially 'graphical sudo' a box will appear prompting you for the password.

Post back with the outcome of this, if you're still there..

BTW ubuntu doesn't come with all the patent encumbered codecs you probably use with your media (I know I do unfortunately, it's what most everyone uses). The Restricted Codec's link you were given explain's how to get them manually, but there are automated scripts that can do all the work for you. Click Almighty Automatix in my signature for one such script.

---

### Post by richbarna on 2006-06-05
> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I have seen this message when "Synaptic" or "Adept" is left open/connected while trying to apt-get.

I can't beleive that someone would choose Windows over Ubuntu for a webcam !?

---

### Post by Valavien on 2006-06-05
I still call myself a noob and having been using Ubuntu as my primary OS for over a year now this release has put me a few more steps closer to not having to uss windows at all.  

I used to boot to windows to use:

itunes,
burn dvd's from avi files
copy dvd's
sync my XDA II
(got wireless working in breezy usind ndiswrapper)

well with this release the only thing left is my XDA II so I am absolutely thrilled.  I really struggle going back to windows now as I really notice the difference.  XP is just so flakey once you install a few things.  I do suspect Vista will be very different though.  

I also installed Neverwinter Nights on my windows install and it barely ran and was hopeless and it should as I hvae a much more powerful computer than when I first got the game.  I installed it in Ubuntu and it works sweetly!

So stick with it,  Dapper is great and it just gets better and better.

---

### Post by lapsey on 2006-06-05
I dunno, I did a fresh install and all I needed to do to get everything working was to run automatix, install some drivers and add the extra repositories - all of which information was found already on these forums. 

I can see how certain items of hardware can be a problem - chances are the manufacturer only had windows in mind - but when there aren't people trying hard to get the generic devices supported in linux there is nearly always a fix you can find yourself. Sure, that takes a bit of work. But you can't blame the OS for that. :-\"

I can recall having just as much "fun" with Windows and certain hardware, even the 5th time I installed it.

---

