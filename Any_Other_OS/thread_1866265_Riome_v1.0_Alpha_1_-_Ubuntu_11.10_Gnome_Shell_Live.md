---
title: "Riome v1.0 Alpha 1 - Ubuntu 11.10 Gnome Shell Live CD"
date: 2011-10-21
forum: Any Other OS
---

### Post by ryanrio95 on 2011-10-21
[COLOR=Red]UPDATE![/color]

This post doesn't contain information about Riome anymore.
For extra information you could check our website.
[Official Riome Website](http://www.riome.org)

Download right now:
Release: V2.0 Bravo
[Rapidshare Download](https://rapidshare.com/files/2321801520/riome-bravo-desktop.iso)
[Dropbox Download](http://dl.dropbox.com/u/58809168/riome-bravo-desktop.iso)

Regards, Ryan.

Reason for Editing:
Information about Riome that was set here is outdated and was about Riome V1.0 Alfa. The Bravo version has been released already.

---

### Post by 23dornot23d on 2011-10-21
Just been looking through the list .....  ( aim for quality ..... ) 

Not keen on Docky ...... Cairo-Dock is more polished with a very professional look to it ..... and also
very customizable

The [[COLOR=Blue]_***Zukitwo Themes***_[/COLOR]]("http://lassekongo83.deviantart.com/art/Zukitwo-203936861") on Deviant Art looks good ..... (but at the moment is not changing much on my set up)

I am currently trying to get this working  ..... maybe needs a small script to ensure the needed 
packages in the Install file are met ......

> 
To use this theme you'll need the LATEST stable versions of the following software: 
 
- Gnome 2.32 or Gnome 3. 
- The Unico GTK3 engine. (Only needed if you are using GTK3 applications. Google it or search for it on launchpad.net.) 
- The Murrine GTK2 engine 0.98.1.1 or later. (Package name varies between distributions. This engine should be installed by default in Ubuntu.) 
- The Pixbuf GTK2 engine (Package name varies between distributions. This engine should be installed by default in Ubuntu.) 
- Nautilus-Elementary (Not needed. But it's recommended if you're using Gnome 2.32.) 
- gnome-tweak-tool (If you're using Gnome 3.) 
 
## INSTALLING THE GTK2 THEME ## 
 
Unzip the included folder(s) to 1 of the following locations: 
/usr/share/themes 
/home/your username/.themes 
 
Go to System -> Preferences -> Appearance and click on the Customize button. 
Select the theme(s) from the lists there.

> 
## INSTALLING THE GTK3 & GNOME-SHELL THEME ## 
 
Unzip the included folder(s) to 1 of the following locations: 
/usr/share/themes 
/home/your username/.themes 
 
Note: The /.themes folder is only for your user. If you for example use an application as root it will not be styled. 
 
Go to System -> Accessories -> Advanced Settings or search for gnome-tweak-tool.

Will keep an eye on this thread ........ as its a good project to do ..... :)

Will test the CD for you ..... once you get a beta out ......

---

### Post by ryanrio95 on 2011-10-21
Okay, i found out that the new Dock of Gnome Shell 3.2 is really nice compared to the Dock Extension of 3.0.
So i'am going to use that one :)
I will release the Alpha 1 today or tomorrow.
Zukitwo is the default gtk & metacity theme btw of Riome.

Greets.

Edit: I first need to know how to enable extensions via command line in Gnome 3.2 Shell.

---

### Post by 23dornot23d on 2011-10-21
[[COLOR=Blue]*_**Cairo-dock**_*[/COLOR]]("http://www.google.com/search?client=ubuntu&channel=fs&q=cairo-dock&ie=utf-8&oe=utf-8") is a separate dock to the Gnome-shell one but if you can get it to look like this then its ok ...

It autohides when not in use and it also autohides if a window covers it ..... but it can be brought back
to the front with a muse over .....

Clarity Icons ....[URL="http://gnome-look.org/content/show.php?content=135654"].***_ download here_***
[/URL] 
set to lux after following the instructions ....

go into cairo-dock configuration ..... appearance change icons ......

standard background ...... from OO

[IMG]http://img823.imageshack.us/img823/8251/57347642.jpg[/IMG]


Not sure how to enable the extensions from the command line ......

But if enabling the extensions from the command line is the first task - then I will research it ........ and see whats available to do it .....

Guess we will start here

[http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html](http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html)

> 
So how should you go about creating a GNOME Shell extension?  Let us  dive in an create a simple extension and explain the concepts and theory  as we go along.  We will use *gnome-shell-extension-tool* for  our first example.   This tool is available in Fedora 15 Alpha. I am not  sure whether it is available on other GNU/Linux distributions.  There  is no manpage for this tool but it is simple to use. Just answer a  couple of questions and all the necessary files are created for  you.[LEFT][COLOR=#000000]
Read more: [http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html#ixzz1bQLwJ3SZ](http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html#ixzz1bQLwJ3SZ)
[/COLOR][/LEFT]

Quote from it ..... above ..... seems we need a tool that is only available in Fedora at the moment ,,,,,

unless someone can port it across ...... not sure if it can be done with [[COLOR=Blue]**Alien**[/COLOR]]("http://www.howtoforge.com/converting_rpm_to_deb_with_alien") ,,,, or not .... or something else maybe

---

### Post by ryanrio95 on 2011-10-21
I made a script that runs for new users, it sets the favorite apps, enables alternative status menu en dock extensions and it sets that the date is shown in the top bar.
So that isn't the problem anymore, the filesystem is 100 MB smaller due the remove of docky.

Remember you can set everything else by yourself.

---

### Post by 23dornot23d on 2011-10-21
Ok 100 meg less is good ..... does the Gnome Shell Dock look ok now ......

It was always a pain to move it around before on the first screen ..... seemed to want to go into the top left corner no matter what I tried ...... in the script I think it allowed for right and left side only ....

[http://linuxo.com/content/gnome-shell-dock-and-alternative-status-menu-extensions-fixes-gnome-3-webupd8-ppa](http://linuxo.com/content/gnome-shell-dock-and-alternative-status-menu-extensions-fixes-gnome-3-webupd8-ppa)

[http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

---

### Post by cbowman57 on 2011-10-21
Good luck with the project.

---

### Post by ryanrio95 on 2011-10-22
> **23dornot23d said:**
> Ok 100 meg less is good ..... does the Gnome Shell Dock look ok now ......

It was always a pain to move it around before on the first screen ..... seemed to want to go into the top left corner no matter what I tried ...... in the script I think it allowed for right and left side only ....

[http://linuxo.com/content/gnome-shell-dock-and-alternative-status-menu-extensions-fixes-gnome-3-webupd8-ppa](http://linuxo.com/content/gnome-shell-dock-and-alternative-status-menu-extensions-fixes-gnome-3-webupd8-ppa)

[http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

Yeah, i'am using the Alt Status Menu and the Dock Extension of Webupd8.
I really like its improvements since the Gnome 3 releases of this extensions.
The upload takes 4 hours from now.

Greets

---

### Post by 23dornot23d on 2011-10-22
I just ran the command to see ....

> 
user@user-MS-7181:~$ gnome-shell-extension-tool --help
Usage: gnome-shell-extension-tool [options]

Options:
  -h, --help          show this help message and exit
  --create-extension  Create a new GNOME Shell extension
user@user-MS-7181:~$ 



It is already included .... in 3.2.0 ..... by the looks ..... so thats another problem gone.

---

### Post by ryanrio95 on 2011-10-22
Okay, i was with my girlfriend this day so i decided to not take any time for Riome.
But, i don't understand this, is that command the way to enable one extension?
If it is, i would really love to use that command line.

Regards,

Edit: I'am now working on building packages, so i can make an repo for all these packages and so users can stay up to date.
And don't have to install it every time over and over again.

---

### Post by ryanrio95 on 2011-10-22
The Download for Alpha 1 is available in the first post

---

### Post by cbowman57 on 2011-10-22
I'm downloading now, will take some time.

---

### Post by ryanrio95 on 2011-10-22
All right, could you tell me what you think about it?

---

### Post by cbowman57 on 2011-10-22
Sure, though I might not be able to get to it until tomorrow.

---

### Post by ryanrio95 on 2011-10-22
Well. I'am now building one package that is the only one for riome and that overwrites all the ubuntu files where it is needed and removes the ones that are not needed.
That deb package will be updated like once a week.
And will be build on, so you always will have the newest updates.
But i need to know how to set that that package is always on top of other packages?
That it has the highest priority.

Regards,

---

### Post by 23dornot23d on 2011-10-22
Will burn it to disc tomorrow too .... to test it .

[IMG]http://img803.imageshack.us/img803/1011/downloadti.jpg[/IMG]

---

### Post by cbowman57 on 2011-10-23
Just finished downloading & installing.  I use Nvidia video and in the live session it used the gallium experimental drivers & took me right to the shell, very nice.

Installation went without a hitch, using it now.  Other than the incomplete branding a person wouldn't know this was alpha/beta.

It needs by default, gnome-tweak-tool.

You can remove (purge) compiz* & unity-2d*.

If this were my distro I'd eliminate banshee, thunderbird & libreoffice (personal preference).

 A target iso size of 690Mb would be nice if it could be accomplished by eliminating unity-2d, compiz & libreoffice.

Really nice so far Ryan, I wouldn't hesitate to name Riome as the heir apparent to gNatty in it's current state.

Great work, it easily surpasses what I did with gNatty.  =D>

Added link to this thread to post #1 of the [gNatty thread.]("http://ubuntuforums.org/showthread.php?t=1754198").

---

### Post by Glenn nl on 2011-10-23
> **cbowman57 said:**
> Just finished downloading & installing.  I use Nvidia video and in the live session it used the gallium experimental drivers & took me right to the shell, very nice.

Installation went without a hitch, using it now.  Other than the incomplete branding a person wouldn't know this was alpha/beta.

It needs by default, gnome-tweak-tool.

You can remove (purge) compiz* & unity-2d*.

If this were my distro I'd eliminate banshee, thunderbird & libreoffice (personal preference).

 A target iso size of 690Mb would be nice if it could be accomplished by eliminating unity-2d, compiz & libreoffice.

Really nice so far Ryan, I wouldn't hesitate to name Riome as the heir apparent to gNatty in it's current state.

Great work, it easily surpasses what I did with gNatty.  =D>

Added link to this thread to post #1 of the [gNatty thread.]("http://ubuntuforums.org/showthread.php?t=1754198").

I agree, Rhythmbox, Evolution and Abiword/Gnumeric are better for a pure Gnome spin.
Tomboy replaced with Gnote and Firefox replaced with Epiphany would be nice too.

---

### Post by cbowman57 on 2011-10-23
I might be way off-base but I think the majority of users use web based email, making any email software unnecessary, those that do use one probably have a preference based on experience & can install it.

Banshee is resource intensive, Rhythmbox slightly less so.  My favorite is Clementine, it's feature rich but is much lighter.  (again personal preference)

Epiphany just isn't up to par with Firefox & most people migrating from Windows or other *buntu distros are already familiar with Firefox.

Abiword/Gnumeric probably meets the needs of majority, those that want more can install libreoffice.

Just my ramblings, YMMV. :)

---

### Post by 23dornot23d on 2011-10-23
> 
Tomboy replaced with Gnote
Yep thats the one I do ...... remove Mono ...... big chunk gone .....

(always reinstalls what it needs if a package is needed by a user too)

I also remove Ubuntuone ..... but for those that use it .......  it should reinstall ....

(also can be added back in later)

Just about to try now ...... ( did have a quick run on a virtual box ....... Qemu ) 



Will burn to DVD ..... ...... burnt and now installing ....

---

### Post by ryanrio95 on 2011-10-23
Thanks, everyone :)
I'am now building my own packages and will be releasing V1.0 about next week.
You will stay up to date through the packages.
But i also wanted to change to Evolution Mail, because it's integrated with the Calendar in Gnome Shell.
It is an good idea to remove all the unity packages, because it can't be used in Riome.

Greets, Ryan

---

### Post by 23dornot23d on 2011-10-23
Ok cheers ,

Mine is installing now ..... and runs great from the DVD ...... like it ... ;)

---

### Post by Ichtyandr on 2011-10-23
is this project related to [Ubuntu GNOME Shell Remix 11.10]("http://news.softpedia.com/news/Introducing-Ubuntu-11-10-Without-Unity-228425.shtml")? 
Or perhaps to the [Ubuntu Gnome Remix]("http://ugr.teampr0xy.net/") project?

---

### Post by ryanrio95 on 2011-10-23
> **Ichtyandr said:**
> is this project related to [Ubuntu GNOME Shell Remix 11.10]("http://news.softpedia.com/news/Introducing-Ubuntu-11-10-Without-Unity-228425.shtml")? 
Or perhaps to the [Ubuntu Gnome Remix]("http://ugr.teampr0xy.net/") project?

No. None of both projects, I didn't even know about the Ubuntu Gnome Shell Remix.
My idea was to create an Ubuntu based Distro with Gnome Shell.

Greets.

---

### Post by Ichtyandr on 2011-10-23
> **ryanrio95 said:**
> No. None of both projects, I didn't even know about the Ubuntu Gnome Shell Remix.
My idea was to create an Ubuntu based Distro with Gnome Shell.
Greets.
I admire and thank you and people like you for your effort (spending you time and energy for free). After oneiric came out internet is full of tutorials like [this]("http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html") on how to switch to pure gnome with or without shell.
Without prejudice to unity (which is great in its own right), gnome-shell is using a different technology and produced a simple and futuristic experience in line with its philosophy. It is great to have a gnome-shell pure gnome spin to accommodate users like me and perhaps many others.
I just wonder whether there is any chance that you people join efforts in extending the Ubuntu family to maintain a non-official spin like that.

---

### Post by ryanrio95 on 2011-10-23
I like that tutorial, i will use it for my project.
But not gonna switch over to gdm, because lightdm is a lot easier in use.

Greets.

---

### Post by cbowman57 on 2011-10-23
All the repos in Software Sources get deactivated every time I reboot.  Is anyone else having this problem?  Is it Riome or something in Ubuntu?

The installation I created with the minimal.iso doesn't share this bug.

---

### Post by ryanrio95 on 2011-10-23
yes. Thats only in this release.
Sorry. But i did it so ubuntu can't overwrite the file changes i made.
In the official release i will use both ubuntu and riome repo's

---

### Post by cbowman57 on 2011-10-23
Ok, just wondered. :)

What do I need to do to make it writable again?

Well, been playing around with it for a couple hours, this is how it's looking so far.

[ATTACH]205277[/ATTACH]

---

### Post by ryanrio95 on 2011-10-23
you will have to remove /etc/rc.local and /etc/cron.hourly/riomesources.sh 
In v1.0 it will be writable.
Because i have my own repository now.
Just need an good hosting.

Btw i love your desktop with ambiance blue

---

### Post by cbowman57 on 2011-10-23
> **ryanrio95 said:**
> you will have to remove /etc/rc.local and /etc/cron.hourly/riomesources.sh 
In v1.0 it will be writable.
Because i have my own repository now.
Just need an good hosting.

Btw i love your desktop with ambiance blue

Ok, edited or deleted necessary files, now my changes will stick.

I know, that ambiance blue with your default background give it a custom but still Ubuntu look that I find really pleasant, dark but not too dark :)

Well I just inadvertently updated with oneiric-proposed, no ill effects.

---

### Post by ryanrio95 on 2011-10-23
that is because of riome has scripts to remove the ubuntu wallapers, themes and sessions, it will be possible to install other DEs like kde and lxde in the v1.0 but not in the testings.

If i remove the unity packages, are the ubuntu sessions than also removed in ubuntu 11.10 (the official one)

---

### Post by cbowman57 on 2011-10-23
> **ryanrio95 said:**
> that is because of riome has scripts to remove the ubuntu wallapers, themes and sessions, it will be possible to install other DEs like kde and lxde in the v1.0 but not in the testings.

Ok.

> If i remove the unity packages, are the ubuntu sessions than also removed in ubuntu 11.10 (the official one)Pretty sure they are.

I just screwed up my Riome installation playing with the oneiric-proposed repository so I can't check that out. Doh! ](*,)

---

### Post by ryanrio95 on 2011-10-23
haha, i have a lot to do for the official release, so an question,
Should i use gdm or lightdm?
Which do you prefer?
I will have to remove thunderbird and install evolution
And many more

---

### Post by cbowman57 on 2011-10-23
I'm pretty impressed with the look of lightdm but whatever you find easiest to work with is fine with me.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
sounds like a nice project a lot of people will enjoy.  You might consider an xfce version for low-end older computers...

---

### Post by cbowman57 on 2011-10-23
> **TREESofRIGHTEOUSNESS said:**
> sounds like a nice project a lot of people will enjoy.  You might consider an xfce version for low-end older computers...

Doesn't xubuntu already have that covered?

---

### Post by ryanrio95 on 2011-10-24
Okay i'am now trying to fix the sources.list.
It will always check if the riome repos are inside, and if not than it will add the riome repo's

Greets

---

### Post by 23dornot23d on 2011-10-24
Ok I am up and running too ..... not altered anything yet ....

missing aptitude

and gimp

so far ............

How do I install them using your sources list ...... or do I start adding repos ..... ?

I am going to try - just using the things you  have available for the time being ...... shotwell is quite good ....

 posted screenshots 

facebook  ( this workedd ok )

and picasa really quickly ..... ( but this one did not work ..... ) 

would like imageshack on there too ....

Not sure if its possible .....

Cannot play Flash on you-tube yet ...... and it does not allow download .........  of the flashplayer yet

may have to start adding repos .... sevenmachines I use for flash.


But on the plus side it is extremely quick and well done ...... so far so good ....... ;)

---

### Post by cbowman57 on 2011-10-24
You can temporarily modify the sources.list, or edit /etc/rc.local to keep your changes from being overwritten & disable the scripts in /etc/cron.hourly.

---

### Post by 23dornot23d on 2011-10-24
What do you have in the sources list at the moment ...... please ......

as we all might as well use the same ....... 

I like minimalistic ...... but none are active in my install yet


will use these for the time being ....

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe


ook now got 

gimp
aptitude
streamtuner

Can live with this now .......

maybe just add the clarity icons ......

[http://img90.imageshack.us/img90/976/tron2o.jpg](http://img90.imageshack.us/img90/976/tron2o.jpg)

[IMG]http://img38.imageshack.us/img38/3064/updatesg.jpg[/IMG]


Ok added flash aid .... and flash is working too

[http://www.webgapps.org/add-ons/flash-aid](http://www.webgapps.org/add-ons/flash-aid)

---

### Post by cecilpierce on 2011-10-24
I didn't have a sources.list in /etc/apt, all that was there was one line of sources.save.
So I copied a list from another oneiric and did update, upgrade, and nuttin!
I did install aptitude and gnome-tweak and midnight commander with sudo apt-get install <package>.
This riome works really great though   :)

---

### Post by cecilpierce on 2011-10-24
@Keith

Did you have any luck putting those three into sources.list  ?

---

### Post by 23dornot23d on 2011-10-24
yeo I created a new file and all is working well ....

[IMG]http://img824.imageshack.us/img824/7756/tronai.jpg[/IMG]

gksudo gedit /etc/apt/sources.list

then added the lines

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe

and saved it ........ 

dont forget to do 

apt-get update

as it builds the lists it uses for downloading ..... the other things like aptitude and gimp ..... 

its fast this too ..... ;) :D

( may need to remove later if we are doing a proper test ...... or create another partition .... 
I might do that later as this Distro seems good enough - to warrant two .... partitions ...... )


Just going to post the original 11.10 sources.list here ....... as its handy if I need the odd line out of it ...
```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110919)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

---

### Post by cecilpierce on 2011-10-24
Thanks Keith, that did something, only 4 updates.
I lost track of the time, went outside to fix my TV ant to see if I could get and old channel that puts old Sherlock Holmes movies on late at night and started working on my truck camper, what a disaster, Im not going outside any more today  :confused:

Have you added any extensions to riome?
It has a couple.

---

### Post by ryanrio95 on 2011-10-24
okay people, i know the sources.list problem.
But this is fixed in the final release, i first have to get an hosting and then i will release it.
With the newest packages there are no problems with editing any file.
But this test release has no repos yet.
 
Greets,

---

### Post by cecilpierce on 2011-10-24
@ryanrio95

Thanks,

Can the Riome v1.0 Alpha be upgraded to the final ?

---

### Post by 23dornot23d on 2011-10-24
> 
Thanks Keith, that did something, only 4 updates.
I lost track of the time, went outside to fix my TV ant to see if I  could get and old channel that puts old Sherlock Holmes movies on late  at night and started working on my truck camper, what a disaster, Im not  going outside any more today  :confused:

I go outside forget what I went outside to do  ..... then come back in ..... then realize why I went outside ..... lols ....

Was raining today so not a lot of fun outside here anyways .....

I used to mess with the satellite stuff ..... finding them tiny satellites in the sky is a pain too .... bought a tiny receiver that goes between the dish and the receiver that flashes and bleeps at me now ...... lets me know if one is close to where I am aiming it .....

> 
Have you added any extensions to riome?
It has a couple.
Its got the ones on I use ...... but add the ppa for them ......


sudo add-apt-repository ppa:webupd8team/gnome3  
sudo apt-get update 
   sudo apt-get install gnome-shell-extensions-alternate-tab   
sudo apt-get  install gnome-shell-extensions-alternative-status-menu   
sudo apt-get  install gnome-shell-extensions-user-theme gnome-tweak-tool 
 sudo apt-get  install gnome-shell-extensions-workspace-indicator   
sudo apt-get  install gnome-shell-extensions-apps-menu   
sudo apt-get install  gnome-shell-extensions-drive-menu


LOG OUT and back in then run

gnome-tweak-tool

[IMG]http://img23.imageshack.us/img23/7945/extfix.jpg[/IMG]


Applications menu is the other I switch on - switched it on after the screenshot .... gives the classic like menus .....

[IMG]http://img192.imageshack.us/img192/9939/menusa.jpg[/IMG]

> 
okay people, i know the sources.list problem.
But this is fixed in the final release, i first have to get an hosting and then i will release it.
With the newest packages there are no problems with editing any file.
But this test release has no repos yet.
 
Greets,     
Ok keep up the great  work ...... do you have a copy of the script to create the DVD with  .....
we can use and then we can keep sending each other versions to alter and update  ....

---

### Post by ryanrio95 on 2011-10-24
sorry, but i will not share the build script with others.
The live cd is reducing in size :) with removing unity and the packages that are on the cd.

---

### Post by 23dornot23d on 2011-10-24
> 
sorry, but i will not share the build script with others.
The live cd is reducing in size :smile: with removing unity and the packages that are on the cd.


Ok no problems .......

---

### Post by ryanrio95 on 2011-10-26
Okay, i'am almost done with Riome v1.0 RC1.
Yes, it's going fast, but that's because i almost did everything.
PS in the partitionmanager on the live cd there is an Ubuntu icon shown.
Where is this icon located? Does anyone knows?

Greets, Ryan.

---

### Post by cbowman57 on 2011-10-26
Haven't a clue, I never bothered with trying to re-brand the installation process so I'm pretty impressed with how quick you accomplished what you did with the alpha. :)

---

### Post by cecilpierce on 2011-10-26
Looks like I'm gona have to get a bigger hard drive for all this stuff  :P

---

### Post by cbowman57 on 2011-10-26
> **cecilpierce said:**
> Looks like I'm gona have to get a bigger hard drive for all this stuff  :P

Not sure how much space you give these test partitions, mine are no bigger than 50Gb & use only about 10% of that, but I share all the large folders and keep them on their own partitions.  Just a thought. :)

---

### Post by ryanrio95 on 2011-10-26
The RC1 will be available today or tommorow.
This release will be everything that the V1.0 final is.
But then without packages :(
I haven't got my hosting yet.

Greets, ryan.

---

### Post by ryanrio95 on 2011-10-26
Hi guys, i'am now uploading the V1.0 RC1
The CD now contains 824 MB, i don't what it makes so big.
I removed Unity, Compiz, Appmenu & Ubuntu Scrollbars, like in the tutorial that was posted on page 3.
Thanks for that!
The Icon Theme Faenza is 50 MB :| but really really nice.
So i think it can't be tinier.
I have 3 things that i want to do before i release V1.0 final.
- Change the default Firefox homepage.
- Change the Ubuntu logo in Ubiquity.
- Host the repos
- Disable all slideshows except of one Riome page.
- Maybe some Ubiquity settings to change the background.

I will post an screenshot of the current release soon in the first post.

Greets, Ryan.

Edit: Made an overview of available packages in Riome v1.0 Final in first post

---

### Post by cecilpierce on 2011-10-27
Installed RC1 two times, theres no grub, no initrd.img

Any one get it to work ?

---

### Post by cbowman57 on 2011-10-27
He forgot something in RC1, keep an eye on post #1, RC2 will be out shortly.

---

### Post by cecilpierce on 2011-10-27
> **cbowman57 said:**
> He forgot something in RC1, keep an eye on post #1, RC2 will be out shortly.

Thanks Chuck, I thought I had a bad DL so I did it again a few mins ago, took an hour and a half  :(

---

### Post by cbowman57 on 2011-10-27
I'm no chroot guru but this might help you in getting RC1 to boot [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

---

### Post by cecilpierce on 2011-10-27
> **cbowman57 said:**
> I'm no chroot guru but this might help you in getting RC1 to boot [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

Thanks, printed it, gona try for the heck of it  :lolflag:

---

### Post by cbowman57 on 2011-10-27
Let me know how it goes, you should be able to install grub that way too.

---

### Post by cecilpierce on 2011-10-27
Its too messed up, had all kinds of errors, missing this and that, no sources.list, cant remember it all, just got tired of problems and its getting late, gota go to air boat club meeting later and to the store for some liquid stuff !!!
Maybe when I get back he will have the new and improved version out   :P

---

### Post by cbowman57 on 2011-10-27
> **cecilpierce said:**
> Its too messed up, had all kinds of errors, missing this and that, no sources.list, cant remember it all, just got tired of problems and its getting late, gota go to air boat club meeting later and to the store for some liquid stuff !!!
Maybe when I get back he will have the new and improved version out   :P

While he's getting that sorted out I've been running pre-12.04 minimal with Gnome only installed. It's on par with my 11.10 minimal install & my Arch install.

I've noticed a lot of problems in the forum are the result of people trying to add G-S to their live Ubuntu installation.  I definitely prefer a Gnome-only installation.

---

### Post by ryanrio95 on 2011-10-27
It is going unstable right now.
I will check all files/scripts tommorow.
And test everything a few times.
Sorry for the bad release.
There is a lot to do before i will release V1.0 Final.

Greets, Ryan.

**Maybe is Ubuntu Mini Remix an better base cd?**

---

### Post by cecilpierce on 2011-10-27
Yea, me to, I cant wait till my check comes in so I can get a bigger HD

---

### Post by cbowman57 on 2011-10-27
> **ryanrio95 said:**
> It is going unstable right now.
I will check all files/scripts tommorow.
And test everything a few times.
Sorry for the bad release.
There is a lot to do before i will release V1.0 Final.

Greets, Ryan.

**Maybe is Ubuntu Mini Remix an better base cd?**

I install with this [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) since you are using a script to build I would guess you could use one of these.  apt-get install lightdm gnome-shell & video drivers, plus whatever else you want on it.

Been thinking about the growing image size, is the iso including the downloaded .deb files?

---

### Post by ryanrio95 on 2011-10-27
No. It is now just copying the files in the system.
The packages are not used yet.
I'am now trying Ubuntu Mini Remix in Virtualbox, i installed, gnome shell, lightdm and xinit so far. Now i will test the system.

Edit: I know something important.
In my build script, i don't clean the packages that were downloaded temporary.
This will reduce the ISO size incredibly.

---

### Post by cbowman57 on 2011-10-27
> **ryanrio95 said:**
> 

Edit: I know something important.
In my build script, i don't clean the packages that were downloaded temporary.
This will reduce the ISO size incredibly.

:)

---

### Post by ryanrio95 on 2011-10-27
I'am uploading Riome v1.0 RC2 now. It is bugless. And the CD is about 790 MB big.
Their are only a few things that i have to change, see first post.
Anyone has solutions for the to do list?

Greets, Ryan.

Edit: Check first post for RC2

---

### Post by cecilpierce on 2011-10-28
D/L says temporary out of service ?
:confused:

---

### Post by cbowman57 on 2011-10-28
Appears to be working now, hopefully I'll have it downloaded within a few hours.

---

### Post by cecilpierce on 2011-10-28
Just got it  :P
Hour and fifteen minutes  :)
Hope it works  :KS

---

### Post by IanW on 2011-10-28
> **cecilpierce said:**
> Yea, me to, I cant wait till my check comes in so I can get a bigger HD

Bad news. HD prices have doubled in the last week due to the Thailand floods.
(A significant percentage of the world's HD & HD components come from there)

---

### Post by cbowman57 on 2011-10-28
> **cecilpierce said:**
> Just got it  :P
Hour and fifteen minutes  :)
Hope it works  :KS

Any luck getting RC2 to install?  I got a jockey-text error but it seems to be taking forever to complete "Saving installed packages.."

---

### Post by cecilpierce on 2011-10-28
> **cbowman57 said:**
> Any luck getting RC2 to install?  I got a jockey-text error but it seems to be taking forever to complete "Saving installed packages.."

Nope, tried twice, installer crashed, I thought he was going to test it first ?

---

### Post by cecilpierce on 2011-10-28
> **IanW said:**
> Bad news. HD prices have doubled in the last week due to the Thailand floods.
(A significant percentage of the world's HD & HD components come from there)

CompUSA or Tiger Direct here has a Seagate 500GB for $39.99 but by the time my check comes in on Monday the price will probably change, thats always my luck   :(

---

### Post by cecilpierce on 2011-10-28
@Chuck

I put mine on a flash drive, I wonder if I burned it to a dvd it would make any dif ???

---

### Post by cbowman57 on 2011-10-28
> **cecilpierce said:**
> @Chuck

I put mine on a flash drive, I wonder if I burned it to a dvd it would make any dif ???

Let me know what happens, I use flash drives too.

I'm having the same problem, installer keeps stopping with errors shortly after selecting time zone.

---

### Post by cecilpierce on 2011-10-28
> **cbowman57 said:**
> Let me know what happens, I use flash drives too.

I'm having the same problem, installer keeps stopping with errors shortly after selecting time zone.

Had to take my senior citizen nap  :) and I banged my head into the awning outside ](*,) 

Mine got all the way to choosing partition and copying files then crash !
I did notice up at the top left where it said ubiquity there was a red circle with a line through it like something was wrong  :confused:

Just looked to see how many dvd's I have so guess I'll give it a go, I have my doubts though  :(

---

### Post by cecilpierce on 2011-10-28
Well I tried brasero and got EDD: Error 1000 over and over, then I tried k3b and it boots live ok but same problem when it gets to installing files to the partition...CRASH!
I'm done, the last 6 dvd's went to the trash, bummer  :(

---

### Post by ryanrio95 on 2011-10-29
Guys, that's an repository problem :$
I recommend to only test the test releases in virtualbox. Or install them in Virtualbox.

Greets, Ryan.

---

### Post by ryanrio95 on 2011-10-30
Now making an script that adds your most used applications to favorites automatically

Ryan

---

### Post by cecilpierce on 2011-10-30
@Ryan

Have you tried to install RC2 ?
Chuck and I down loaded it and the installer (ubiquity) crashes half way through.

---

### Post by ryanrio95 on 2011-10-30
I only tested the live cd because the installer isn't working because of the Repository script for Riome is inside
But is has no repository yet :p

So, just wait for the final :$

Greets,

---

### Post by cecilpierce on 2011-10-30
> **ryanrio95 said:**
> I only tested the live cd because the installer isn't working because of the Repository script for Riome is inside
But is has no repository yet :p

So, just wait for the final :$

Greets,

OK thanks Ryan, any idea when the final will be out ?
Cecil

p.s. is that colon dollar sign  suppose to have a dash (-) in the middle to look like Shhh  :-$
just curious, you have 'So, just wait for the final :$'

---

### Post by ryanrio95 on 2011-10-30
It's an blushing emoticon.
There is a lot to do. And i want it to be bugless.
I'am also going to use PHPFusion for the website.
So we can discuss there in different topics, i can post news etc.

Greets, Ryan.

---

### Post by cecilpierce on 2011-10-30
OK Ryan thanks for the info  :D

---

### Post by ryanrio95 on 2011-11-02
i was busy with school for some time. 
but i will work further on riome soon.
and try to release it in 2 weeks.

greets ryan

---

### Post by ryanrio95 on 2011-11-04
I'am now busy with the website for Riome.
It will be available in no-time.

Greets, Ryan.

---

### Post by cecilpierce on 2011-11-04
Thank Ryan, cant wait to try it, Cecil  :P

---

### Post by ryanrio95 on 2011-11-05
Check out the website at [www.riome.org]("http://www.riome.org")

---

### Post by 23dornot23d on 2011-11-06
Looks good ..... you should make the screenshots as jpgs to load in quicker ..... will make the initial site pages
pop-up quicker .

[IMG]http://img51.imageshack.us/img51/2766/screenshotat20111106135.jpg[/IMG]

as they seem to be larger png's and are a little slow to load (even the thumbnails are slow to draw as they still need to
read in nearly 1 Meg of data ...... )

900 kb ...

change to jpgs in GIMP ... or other editor ..... (screenshot's of same size and quality)

130 kb

 .... but other than that on first looks

It is very professional ..... 

I will give links to it ... once tested and I know that its all working ok ....

---

### Post by ryanrio95 on 2011-11-06
In don't think of making an RC3 and going right to the Final. But their are a few to do's left.
Check out [www.riome.org](www.riome.org) on how you can help me with Riome.

Greets,

---

### Post by 23dornot23d on 2011-11-06
I will go for what appears to be the easiest problem or TODO you have first .....

I would have thought saving the settings in Firefox

Edit . Preferences . set homepage to your site or whatever .... 
and then create the distro ..... 

A clean firefox needs to be installed and set up .....

so that you have no other history in it ........

[IMG]http://img11.imageshack.us/img11/5779/firefoxqd.jpg[/IMG]

Hope this works ok ..... would think it would ..... as long as you retain the 

home/.mozilla 

directory when creating the ISO ...... or maybe running a script file to set it up first time around
unzip it from a archive ..... as each user will have a different home name once installed .... but a
script should be able to do that task.

---

### Post by ryanrio95 on 2011-11-06
I know, but when an user is created, the firefox settings are saved in /home/username/.mozilla/firefox/?????.default/
The ???? is different with each user, so that's the problem :(

---

### Post by 23dornot23d on 2011-11-06
If you save your own profile is it just not a pointer to the first setup ..... 

The profile file looks like this .....


[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=????????.default

_____________________________________________________________

Then in the Profile ...... can you name this to startup a startup.default and overwrite the one there ...... or and unpack your own version called startup.default

unpacking your own profile into this directory if you want should do it  ..... with a small script ..... it can then point to startup.default maybe .....
______________________________________________________________

I will try it as the Firefox team and Mint are always setting the start pages ..... even the search menus ...... must be able to customize there own and set it as the default.

( ok only problem with mine is that folder its 125 Meg .... not sure what size it starts at when clean ...... 
or zipped up - 56 Meg as a tar file ..... interesting though as it works - so I can easily move my profile and this directory
to another system ...... now thats handy ..... )

---

### Post by ryanrio95 on 2011-11-07
hi.
i already removed the ubufox extension that loads the ubuntu startpage.
now i will try to set [www.riome.org](www.riome.org) as the homepage.

greets ryan

---

### Post by proxy.qtz on 2011-11-07
Hey, Ryan. I'm one of the main developers for the UGR distro project. Would you be interested in collaborating?

---

### Post by ryanrio95 on 2011-11-08
> **proxy.qtz said:**
> Hey, Ryan. I'm one of the main developers for the UGR distro project. Would you be interested in collaborating?

no. i will work on my own distro.
first ubuntu based in v2.0 my very own.

greets ryan

---

### Post by ryanrio95 on 2011-11-09
I'am now building the V1.0 Final.

---

### Post by cecilpierce on 2011-11-09
> **ryanrio95 said:**
> I'am now building the V1.0 Final.

WOW! that was fast  :P

Will it be installable ?

I had a lot of trouble trying it with V-box.

---

### Post by ryanrio95 on 2011-11-09
yes. it is full stable now. and i removed a lot of unused applications like alacarte, desktop sharing etc.
evolution and contacts are now available.
i wil release it tommorow on my website only.
because it can count the downloads :p
i have my own repositories so i can resolve bugs now.
when they are inside :o

greets. ryan

---

### Post by cecilpierce on 2011-11-09
Thanks Ryan,
I will try later or tomorrow since you are 6 hours ahead of me  :)
Cecil

---

### Post by shuttleworthwannabe on 2011-11-09
Hi Ryan, I can't wait to give it a spin; when do you think (time wise) you will release the FINAL?

Also, I want to first try it out on a USB stick as Live User--I am using WIndows now, so I am familiar with how to do this from Windows (unetbootin, pendrive, LiLi, etc). Will I be able to do this, or should I only do this using Ubuntu's approach " dd "?

Great--I want a stable and reliable and hassle free Gnome Shell rendition ontop of Ubuntu; there were too many hoops to negotiate under gNatty.

I just hope you will be able to maintain this hard work for a little longer. Wish you and project all the best.

SwB

---

### Post by ryanrio95 on 2011-11-10
Thanks for your feedback.
It is just an Ubuntu Based Live CD so it will work with unetbootin.
I will work on my website from now on.
So i can build an community to work together on building Riome.
I will try to make this an really great project.

Greets, Ryan.

---

### Post by ryanrio95 on 2011-11-10
3 hours to go...

---

### Post by Megaptera on 2011-11-10
Looking forward to giving it a try!

---

### Post by ryanrio95 on 2011-11-10
I'am looking for people with experience on Linux Distro's
I want the V2.0 to be from scratch, so..

Greets, Ryan.

---

### Post by shuttleworthwannabe on 2011-11-10
> **ryanrio95 said:**
> I'am looking for people with experience on Linux Distro's
I want the V2.0 to be from scratch, so..

Greets, Ryan.

May I ask, naively, why [this]("http://ubuntuforums.org/showpost.php?p=11438689&postcount=100") offer will not be useful to your endeavors?

---

### Post by ryanrio95 on 2011-11-10
Because of, i don't know everything and would like to have just a few people that will check what i'am doing or that comes with ideas, so i can make the distro better.

Btw. Megaupload occured an error :(

---

### Post by ryanrio95 on 2011-11-11
Yeaahh!
It has been uploaded and you can download it through this link.
[http://fusion.riome.org/downloads.php](http://fusion.riome.org/downloads.php)

Greets, Ryan.

---

### Post by shuttleworthwannabe on 2011-11-11
Ryan--trying to download from megaupload--it is very slow to non existent. 

BTW--well done for achieving this milestone.:guitar:

---

### Post by cecilpierce on 2011-11-11
Hi Ryan, I D/L v1.0 and installed it but no initrd.img so it wont boot, any suggestions ?
Cec

---

### Post by shuttleworthwannabe on 2011-11-11
> **cecilpierce said:**
> Hi Ryan, I D/L v1.0 and installed it but no initrd.img so it wont boot, any suggestions ?
Cec
You are lucky--my download bombed out; so I did not install. I downloaded PinguyOS instead.

anyway, hope you come right.

---

### Post by cecilpierce on 2011-11-11
> **shuttleworthwannabe said:**
> You are lucky--my download bombed out; so I did not install. I downloaded PinguyOS instead.

anyway, hope you come right.

Yea I saw your post right after I DL it and was wondering why it didn't work for you, took an hour and 15 mins.
Maybe I got a bad DL, I wish he would put the md5sum up to check it.

---

### Post by Megaptera on 2011-11-12
> **ryanrio95 said:**
> Yeaahh!
It has been uploaded and you can download it through this link.
[http://fusion.riome.org/downloads.php](http://fusion.riome.org/downloads.php)

Greets, Ryan.

Downloaded in 8 mins And run the live CD ... I can see the apps that are installed and the riome logo, but what other tweaks or enhancements are included?
I'm not sure I want to install 'til I now if/what else has been tweaked or changed ... thanks!:P

---

### Post by ryanrio95 on 2011-11-13
date in top bar, appearance, extensions, you can see all changes here:

[http://fusion.riome.org/forum/viewthread.php?thread_id=4&pid=5#post_5](http://fusion.riome.org/forum/viewthread.php?thread_id=4&pid=5#post_5)

---

### Post by Megaptera on 2011-11-13
Many thanks!

---

### Post by ryanrio95 on 2011-11-16
who knows an ubuntu based livecd with nothing installed to it?
so i can build it from scratch?

---

### Post by wolfen69 on 2011-11-16
> **ryanrio95 said:**
> who knows an ubuntu based livecd with nothing installed to it?
so i can build it from scratch?

Do a minimal install, add or don't add what you want, then use remastersys to make an image/live cd.

---

### Post by cbowman57 on 2011-11-16
> **ryanrio95 said:**
> who knows an ubuntu based livecd with nothing installed to it?
so i can build it from scratch?

[http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)

---

### Post by Megaptera on 2011-11-17
If I wanted to sudo apt-get remove evolution   from Riome, would that break any dependencies?

---

### Post by ryanrio95 on 2011-11-17
No, it won't remove system applications.

Greets, Ryan.

---

### Post by ryanrio95 on 2011-11-17
> **cbowman57 said:**
> [http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)

Thanks Chuck, i will try to make something of it.
First off all i would check all the files in this Live CD for Ubuntu Brandings, after that, i will start to install packages and check that files also for ubuntu brandings, package for package.

Greets, Ryan

---

### Post by Megaptera on 2011-11-17
> **ryanrio95 said:**
> No, it won't remove system applications.

Greets, Ryan.

Thanks!

---

### Post by ryanrio95 on 2011-11-19
Should i use openoffice as default office program or libreoffice??

---

### Post by Megaptera on 2011-11-20
I usually remove either of those if pre-installed and put on Abiword & Gnumeric instead, just my 2 cents worth!

---

### Post by ryanrio95 on 2011-11-20
I have an minimalistic working system right now, but who knows what the package name is that loads the power off button and other buttons in lightdm?

---

### Post by cbowman57 on 2011-11-20
> **ryanrio95 said:**
> I have an minimalistic working system right now, but who knows what the package name is that loads the power off button and other buttons in lightdm?

Most likely it's unity-greeter, there's a lightdm-greeter-gtk that might also provide those functions but Ubuntu is already setup for unity-greeter, I'd stick with that.

---

### Post by ryanrio95 on 2011-11-20
no unity-greeter loads the background logo etc.
but the topbar needs other packages

greets, ryan

---

### Post by cbowman57 on 2011-11-20
Try this, open up synaptic, locate lightdm, r-click & see what recommends it points to.

Could also look at this & see what you don't have installed: [http://packages.ubuntu.com/ca/oneiric/lightdm](http://packages.ubuntu.com/ca/oneiric/lightdm)

---

### Post by ryanrio95 on 2011-11-22
I have an basic build ready that is based on Ubuntu Mini Remix, i have chosen to not install suggested packages, and i have selected about 50 packages to install with dependencies only, also not recommends.
It's is about 600 MB size and it's working really good :)

Greets, Ryan.

---

### Post by cbowman57 on 2011-11-22
Sounds good, the lighter the better IMO.

---

### Post by ryanrio95 on 2011-11-22
Yes. But there are a lot of things i don't install because of i don't know it has to.
For example, i firstly forgot the theme engines and xsg-user-dirs.
These packages are not really well known.
But they are recommended for an good system (A)

Greets

---

### Post by jimrew111 on 2011-11-22
why would you use shell? fallback is better.

---

### Post by ryanrio95 on 2011-11-23
i have both inside, and you can choose between them. ;)

grets

---

### Post by jimrew111 on 2011-11-23
what software do you use to make ubuntu respins?

---

### Post by ryanrio95 on 2011-11-23
i don't use software.
the v1.0 just adds packages to ubuntu and removes packages
now i have an directory on my own system that contains the files of an vasic debian system and i will build on that and create my own packages for riome v1.5

greets

---

### Post by jimrew111 on 2011-11-23
you lost me there.
how do you do it?

---

### Post by ryanrio95 on 2011-11-23
just create an directory. install debootstrap (basic debian system inside) and install the rest you want. plymouth, gnome shell, ubiquity, lightdm, xorg xserver etc.

---

### Post by ryanrio95 on 2011-11-25
v2.0 will be builded from scratch with ubuntu & riome repos.
and edited packages
i have plymouth-theme-riome, rightdm (riomes lightdm), runity-greeter (riomes unity greeter).
these packages are having the same dependencies etc. as the ubuntu versions but modified files.
in this way i can build riome easier with the ubuntu repos also inside.

greets, ryanrio95.

---

### Post by ryanrio95 on 2011-11-26
Logo Contest Announcement.
I'am looking for an logo for Riome.
I would like to see an Altum fish in it, and that it is round.
If you want to compete. Post your logo here:
[http://fusion.riome.org/forum/viewforum.php?forum_id=6](http://fusion.riome.org/forum/viewforum.php?forum_id=6)
And their will be a poll for choosing an logo.

Greets, Ryan.

---

### Post by ryanrio95 on 2011-11-30
Okay, the website is relaunched right now.
And will be like for a long time.
So join the community.

Their is a logo contest right now.

Please help!
Would love to see a nice logo.

Greets, Ryan.

[http://riome.org/index.php?p=forum#/categories/logo-contest](http://riome.org/index.php?p=forum#/categories/logo-contest)

---

### Post by ryanrio95 on 2011-12-09
I'am now busy with Riome v2.0 Bravo.
It will be build from scratch.
I looked at the packages that are used by Linux Mint and Ubuntu and made an selection.
I will run my first test soon.

Greets, Ryan.

---

### Post by ryanrio95 on 2011-12-14
i have watched the work of linuxmint 12.
i really love it.
and it made me see things different.
i know how to define default gconf2 settings and also how to make package priorities.
i will also produce an software manager based on the one in LM.
iam building my own gnome-session package.
i have learned a lot of good things viewing the source of LM and elementary.
but elementary is too much ubuntu based.
their will be a little applications assortiment so the iso keeps tiny. it's hard with gnome-shell.
i will release it around new years day.
Riome Bravo is coming for you.

---

### Post by shuttleworthwannabe on 2011-12-14
Have you considered registering your project with Distrowatch? I think your hard work should be noted.

PS: I know you are 'repackaging" and maybe "re-scripting" some installation routines, will you be doing some bug fixes too? if so it will be good to address the power hungry battery problem and CPU throttling issues for laptops, then you will have a killer distro imho.

I am watching this space. Thanks

---

### Post by ryanrio95 on 2011-12-15
hehe, the power things are just where i'am working on right now.
i will register Riome with DistroWatch when i release the Riome Bravo release.
I will add an poll on my website with software choices. So you can choose apps, i will use the most listed to fit the 700 MB of data space. I will try to not make more of it.
I'am also thinking of making an user experience package so i can see which packages are mostly used on your systems for future releases. But this will be hard to make.

Greets

---

### Post by ryanrio95 on 2011-12-19
i will use the mgse-menu, mgse-bottompanel, autohidetopbar,altstatusmenu and a few other extensions to improve the desktop usability :)

greets

---

### Post by ryanrio95 on 2011-12-29
Riome Bravo is almost here.
Just a few things to do.

---

### Post by shuttleworthwannabe on 2011-12-29
> **ryanrio95 said:**
> i will use the mgse-menu, mgse-bottompanel, autohidetopbar,altstatusmenu and a few other extensions to improve the desktop usability :)

greets

Why did you not go with the Gnome Shell WM? why the bottom panel approach--seems very Windows like imho.

---

### Post by vanlong441 on 2011-12-29
@ryanrio95,

I think many people here and I want to know your approach to this GNOME Shell spin rather than a given name and then be surprised that it's just a combination of gnome shell and some existing extensions.


Yes I know that you can do whatever you want with your time and money but my advice is to support the current projects by simply learning to make an extension, a Shell/GTK3 theme for GNOME Shell rather than putting things together and calling it an OS. We already have had several working spins. These are some of my contribution to Shell themes. If you are interested in making one yourself and want a walk-through, I think I can make one in a few days.

[http://vanlong441.deviantart.com/art/Gnome-shell-Gaiink-3-2-275881084](http://vanlong441.deviantart.com/art/Gnome-shell-Gaiink-3-2-275881084)
[http://vanlong441.deviantart.com/art/Gnome-shell-Christmas-Orta-3-2-274480827](http://vanlong441.deviantart.com/art/Gnome-shell-Christmas-Orta-3-2-274480827)
[http://vanlong441.deviantart.com/art/Gnome-shell-Gradieness-Large-273348868](http://vanlong441.deviantart.com/art/Gnome-shell-Gradieness-Large-273348868)

---

### Post by ryanrio95 on 2011-12-29
> **vanlong441 said:**
> @ryanrio95,

I think many people here and I want to know your approach to this GNOME Shell spin rather than a given name and then be surprised that it's just a combination of gnome shell and some existing extensions.


Yes I know that you can do whatever you want with your time and money but my advice is to support the current projects by simply learning to make an extension, a Shell/GTK3 theme for GNOME Shell rather than putting things together and calling it an OS. We already have had several working spins. These are some of my contribution to Shell themes. If you are interested in making one yourself and want a walk-through, I think I can make one in a few days.

[http://vanlong441.deviantart.com/art/Gnome-shell-Gaiink-3-2-275881084](http://vanlong441.deviantart.com/art/Gnome-shell-Gaiink-3-2-275881084)
[http://vanlong441.deviantart.com/art/Gnome-shell-Christmas-Orta-3-2-274480827](http://vanlong441.deviantart.com/art/Gnome-shell-Christmas-Orta-3-2-274480827)
[http://vanlong441.deviantart.com/art/Gnome-shell-Gradieness-Large-273348868](http://vanlong441.deviantart.com/art/Gnome-shell-Gradieness-Large-273348868)

i know what you mean.
but i'am working on a system that is ready to use the way i want it.
and i want to share it.
after this release i will try to fork gnome shell.
it is just learning to me.

greets

---

### Post by vanlong441 on 2011-12-29
> **ryanrio95 said:**
> i know what you mean.
but i'am working on a system that is ready to use the way i want it.
and i want to share it.
**after this release i will try to fork gnome shell.**
it is just learning to me.

greets

great! This was what I was looking for from a serious developer. If there is anything that makes you dislike gnome-shell, you can share it here and I believe people will help restore your confidence in making gnome shell a better DE.

---

### Post by ryanrio95 on 2011-12-29
yes, i wrote a few things in my notebook that i would like to do.
but, i will start with this after publishing Riome Bravo.

i just want to make an desktop that is easy to use to everyone.

i also made an script that loads your 10 most used applications into docky.

this is really helpful to myself now.

just want to share everything i like.

greets

---

### Post by vanlong441 on 2011-12-29
that looks a bit like what Zeitgeist journal does with recent items in Docky. Don't you think that your script will make startup process a bit heavier and longer for older machines? Because as far as I understand what you said about "loads your 10 most used applications into docky", after the logging in stage, the script will automatically launch 10 apps, am I right?

If it's so, I think it's better to give people the option whether to choose if they want that than releasing it as default setup.

---

### Post by ryanrio95 on 2011-12-29
hehe no.
gnome generates an file that stores your most used applications ~/.local/gnome-shell/application_state
from that file the script will read which application has the highest score, the script can be run in less than a second.

Greets

---

### Post by ryanrio95 on 2012-01-11
Riome Bravo will be the most user friendly operating system, i think.

---

### Post by auratux on 2012-01-21
Hi,

Just stumbled upon riome now and it looks good and I want to try it!

But as you know MU was taken down by the FBI and no more riome iso... :-\"

Can you put it somewhere else (rapidshare is fast and good) or in a torrent.


Also riome.org is very buggy and I have experience in websites I might be able to help fix it.

I'm looking forward to see what future riome will hold.

---

### Post by ryanrio95 on 2012-01-21
Thanks for your interest.
I'am working on the website, i will try contact the designer i knew a few years ago.
Riome Bravo will be released in 2 hours?
After that i will advertise for Riome, register it with distrowatch etc.
And look for people that could help building the community.

Regards, Ryan.

---

### Post by ryanrio95 on 2012-01-22
Riome Bravo has been released!

---

### Post by shuttleworthwannabe on 2012-01-22
Hi there--can you put a few video's on Youtube to see how Riome Bravo looks and feels. I am keen to give it a spin--just that I have now tweaked Ubuntu 11.10 Gnome Shell to my liking, it is running just perfectly. I will download your Bravo and try on my other desktop.

Congratulations for the hard work coming to fruition!

---

### Post by ryanrio95 on 2012-01-22
yeahh, i will make some video's in a while.
but first i will advertise a little, and i'am going to convert a wordpress theme for the website, build a community etc.

regards, ryan.

---

### Post by Megaptera on 2012-01-22
> **ryanrio95 said:**
> Riome Bravo has been released!

I may have missed it, but what's new in Riome Bravo please?  :p

---

### Post by ryanrio95 on 2012-01-22
it is build from scratch
the build script installs the packages i selected
the rest of the packages are selected by a script that looks at the filesystem.manifest files of ubuntu and some derivatives which are most used and installs these to fit 700 mb
riome has an customized mintinstall as software center.
new fedora charge based boot screen.
new wallpaper and the unity greeter version of riome is inside.
logical filesystem script is included.
script to load 6 most used applications in the dock.
lsb release and apt configuration files are handled better.
4 common used extensions.
the dock is not the official one.
power manager tweaked, it is actually set now.
i will add all packages that i edited/ made to the development section of the website tommorow?

greatest change is that before the default theme ect. were set with an command. now they are defined in gconf and glib files.

want to know more? just try it and check out the repos.

regards, ryan.

---

### Post by ernestj on 2012-01-22
Ryan,
This looks good. The good news is that it looks like Mint is going with Cinnamon and there is not a straight buntu Gnome 3. Keep up the good work. You can run in 11.10 but the shell needs some tweeks and a good theme, you have taken care of that.

---

### Post by ryanrio95 on 2012-01-22
thanks. i will do my best to keep riome like the users of it want it to be.

regards

---

### Post by shuttleworthwannabe on 2012-01-23
Anyway of installing this through USB pendrive?

---

### Post by ryanrio95 on 2012-01-23
> **shuttleworthwannabe said:**
> Anyway of installing this through USB pendrive?

That should be no problem.
Installing on a USB pendrive is just like with Ubuntu.

Let me know if it is possible.

Regards, Ryan.

---

### Post by shuttleworthwannabe on 2012-01-23
Yah--big problem here--your download site is not giving me any joy--it is with rapidshare, right? blocked by my ISP police here.

---

### Post by ryanrio95 on 2012-01-23
That's a big problem for sure.
I can't host it by myself.
Because of the repositories and the bandwith.
I will try to find another other upload site for a mirror where i can upload files that are 700 MB big.

Regards,

---

### Post by Megaptera on 2012-01-23
> **ryanrio95 said:**
> it is build from scratch
the build script installs the packages i selected
the rest of the packages are selected by a script that looks at the filesystem.manifest files of ubuntu and some derivatives which are most used and installs these to fit 700 mb
riome has an customized mintinstall as software center.
new fedora charge based boot screen.
new wallpaper and the unity greeter version of riome is inside.
logical filesystem script is included.
script to load 6 most used applications in the dock.
lsb release and apt configuration files are handled better.
4 common used extensions.
the dock is not the official one.
power manager tweaked, it is actually set now.
i will add all packages that i edited/ made to the development section of the website tommorow?

greatest change is that before the default theme ect. were set with an command. now they are defined in gconf and glib files.

want to know more? just try it and check out the repos.

regards, ryan.
Thanks, I've tried the earlier RC1 and was curious as to what's new ... the update appreciated! :D

---

### Post by ryanrio95 on 2012-01-24
Hehe, if you have problems (don't think so) or ideas.
Could you post it in the community on my website?
You can login there with your google account.

Greets.

---

### Post by ryanrio95 on 2012-01-24
Who can make an mirror?
I don't know any site except of megaupload (it's gone) or rapidshare.
And my bandwith is going down :(
Regards,

---

### Post by shuttleworthwannabe on 2012-01-24
Well Opera Unite may be possible option? or even Drop box--is the limit to this, size-wise?

---

### Post by ryanrio95 on 2012-01-24
i will check out dropbox first ;)

Edit: Whoot, i'am loving dropbox !

Edit2: It is uploading right now to my public folder :D

---

### Post by ryanrio95 on 2012-01-25
I'am looking for php software like launchpad?
Where we can share source etc.
And were i can make two project one Stable and one Testing/Unstable or something.
Just on my website.
Anyone can help?

Regards,

Edit: Riome Bravo is available via Dropbox now.
Check the site.

---

### Post by shuttleworthwannabe on 2012-01-26
Can you update your first post with the link to Dropbox?

Will download now.

---

### Post by ryanrio95 on 2012-01-26
Okay, i will do that right now.
I need feedback (A)

---

### Post by ryanrio95 on 2012-01-27
Their's a problem in the current release.
The Installer doesn't work.

I will release tonight/tommorow the stable release.

Regards, Ryan.

Edit: This is really bad of me, but you learn from mistakes.

---

### Post by ryanrio95 on 2012-02-17
Everything works fine, from installation to integration.
You can download Riome Bravo Desktop Stable from the website :D

Regards, Ryan.

---

### Post by ryanrio95 on 2012-02-25
Does someone has some feedback??

What do you like, and what don't you like?

Regards

---

