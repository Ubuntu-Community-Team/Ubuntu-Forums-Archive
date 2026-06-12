---
title: "How can I speed up ubuntu with 128mb ram?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Zigon on 2006-09-14
Right now it's running hella slow, atleast blazing fast compared to trying to run live CD. Is there anything I can do to kind of speed things up withought installing more ram, non of the newer ram I have fits in the computer with ubuntu on it, I think that's about it.

---

### Post by Kilz on 2006-09-14
> **Zigon said:**
> Right now it's running hella slow, atleast blazing fast compared to trying to run live CD. Is there anything I can do to kind of speed things up withought installing more ram, non of the newer ram I have fits in the computer with ubuntu on it, I think that's about it.

Install fluxbox, icewm or the xubuntu desktop and use them instead of gnome.

---

### Post by Zigon on 2006-09-14
I've installed it already using the alternate CD.

---

### Post by bodhi.zazen on 2006-09-14
Use the alternate CD, do a server install (type server at the prompt after booting).

This will give you a CLI interface.

Install X and fluxbox or icewm. Install any additional apps you need.

Better run fluxbuntu

[fluxbuntu](http://fluxbuntu.org/)

---

### Post by DJiNN on 2006-09-16
> **bodhi.zazen said:**
> Use the alternate CD, do a server install (type server at the prompt after booting).

This will give you a CLI interface.

Install X and fluxbox or icewm. Install any additional apps you need.

Better run fluxbuntu

[fluxbuntu]("http://fluxbuntu.org/")

Damn!! You beat me to it! :lol:   Fluxbuntu is a surefire way to make an older computer run really well,,,,,  Working fine here! :)

---

### Post by louieb on 2006-09-16
I guess i need to try fluxbunta. I have a p1 200 mmx w/ 128 mb ram. Ubuntu is slow. It dual boots to DSL linux (Runs much faster) . DSL uses fluxbox. The only problem I've had with it is the numlock key and the enter key on the far right hand side of the keyboard don't work in fluxbox. The strange thing is when I cntl-alt-bkspce to the command line both keys work. Go figure.

---

### Post by Kilz on 2006-09-16
[Ubuntu lite]("http://www.ubuntulite.org/drupal/?q=node/1") is another option, it uses icewm instead of fluxbox.

---

### Post by bodhi.zazen on 2006-09-16
> **louieb said:**
> I guess i need to try fluxbunta. I have a p1 200 mmx w/ 128 mb ram. Ubuntu is slow. It dual boots to DSL linux (Runs much faster) . DSL uses fluxbox. The only problem I've had with it is the numlock key and the enter key on the far right hand side of the keyboard don't work in fluxbox. The strange thing is when I cntl-alt-bkspce to the command line both keys work. Go figure.

Try numlockx. Works fine in Fluxbox.

---

### Post by Zigon on 2006-09-17
Alright I'm doing a server install right now, I have no idea how much longer it will take to finish. After it's done am I given an option to install fluxbox or what.

Alright im at the command prompt now and I've tried typing 
> 
apt-get install xorg-server
and
> apt-get install fluxbox
and it gives me
> E: COuld not open lock file /var/lib/dpkg/lock -open (permission denied)
E: UNable to lock the administration direcroty (var/lib/dpkg). are you root?

---

### Post by Zigon on 2006-09-17
> sudo apt-get install fluxbox
gives me reading package lists, it finish's that then build dependency tree then I get:
> E: Couldn't find package fluxbox

---

### Post by xpod on 2006-09-17
> How can I speed up ubuntu with 128mb ram?

PUSH IT DOON A HILL:-\"

EDIT:sorry..it slipped oot

---

### Post by Najand on 2006-09-17
> **Zigon said:**
> 
```
sudo apt-get install fluxbox
```
gives me reading package lists, it finish's that then build dependency tree then I get:
> E: Couldn't find package fluxbox

Add "Universe" and "multiverse" to your "sources.list" by clicking:
System -> Administration -> Software Properties
And check all the unchecked options. Then try to use your favorite package manager; i.e. Synaptic, apt-get, aptitude (recommendation: aptitude):
```

sudo aptitude install fluxbox

```

---

### Post by comppsyco on 2006-09-17
but it sounds like he has a server install, so he doesn't have a GUI.
Try ```
sudo nano /etc/apt/sources.list
```
(I'm assuming that you know how to use nano, if not, just use google and find out.)
and add the line 
```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```
That should work.

---

### Post by Kilz on 2006-09-17
> **xpod said:**
> PUSH IT DOON A HILL:-\"

EDIT:sorry..it slipped oot

Im glad I didnt have a mouthfull of coffee when I read that. :D 
But you do know some of these older computers can make gread firewalls and file servers. They need some more ram than that, but ram is relitivly cheap.

---

### Post by Najand on 2006-09-17
> **comppsyco said:**
> but it sounds like he has a server install, so he doesn't have a GUI.
Try ```
sudo nano /etc/apt/sources.list
```
(I'm assuming that you know how to use nano, if not, just use google and find out.)
and add the line 
```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```
That should work.

Well, I see... Thanks for reminding that...
But first of all, he might not be in canada so he is not supposed to use canadian mirrors, so let us help people with the official server.

Secondly, main and restricted are added by default, so if he adds one he will get duplicate source error. And if he has a server adding source packages is also recommended.

So a good choise to add in sources.list would be:
> 
# Ubuntu community supported packages
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

And finally, for using nano, open it by using "nano" command, after editing use "Ctrl+X" then "Y" to save and "Enter" again to accept the file name.
Then use:
```
sudo aptitude update 
```
to update the package database. Everyone knows how to use google these days... So let us just answer people completely.

---

### Post by comppsyco on 2006-09-17
Thanks for correcting me, I don't really know what I'm doing.
I just used the line that easyubuntu adds to the top of your sources.list. Is that a bad line to have in there? My sources.list (after easyubuntu) looks like this: 
```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
#deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
## xgl repos
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

```

EDIT: Oh, and I forgot, the xgl/compiz stuff is in there after a few failed attempts to install that

---

### Post by Najand on 2006-09-17
Well, it is not bad... But not very good organized; If you make it tidy a little it is easier and faster to see what is there when neccessory. I edited it for you using your own repositories...


> 
# Ubuntu supported packages 
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages 
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages 
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages 
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## EasyUbuntu Repositories
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main



If some repositories don't work use # before the line with the name of those repositories to change them to comments.

---

### Post by comppsyco on 2006-09-17
I just realized that the reason that they're all the canadian repos is because I selected Vancouver BC during the install because it's in my time zone. (I'm actually in Seattle) Can I just change all of those to "archive.ubuntu.com"

---

### Post by Najand on 2006-09-17
Sure... just remove all "ca."s.
It would be like:
> # Ubuntu supported packages
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## EasyUbuntu Repositories
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main


Anyway, how does it feel when living beside Microsoft and using linux?

---

### Post by comppsyco on 2006-09-17
Thanks!
I have gotten slapped in the face a couple of times for promoting linux to someone who I later realized was a microsft employee. Other than that, not too bad.

---

### Post by Najand on 2006-09-17
Wow, must have a very brave heart... Hahaha

---

### Post by kerry_s on 2006-09-17
Here's how i do my server+flubox install.

do the server install
login
sudo su  <makes you root
nano etc/apt/sources.list
comment(#) out the cdrom and uncomment all the repos
ctrl and x and y and enter to save
apt-get update
apt-get install x-window-system-core gdm xterm fluxbox synaptic
reboot
now you get a gui to login, select fluxbox in session and login. You should have the base now. You can go straight to synaptic and start selecting what you want to use or uninstall things that you don't need like the extra drivers then install what you want.
I usally select light weight things like rox-filer(filemanger), leafpad(editor),gaim,dillo,xpdf,abiword,xarchiver(to unpack),xfburn(cd burner)....I like to install as i go when i need it, instead of trying to install everything up front.

---

### Post by Zigon on 2006-09-18
> **kerry_s said:**
> Here's how i do my server+flubox install.

do the server install
login
sudo su  <makes you root
nano etc/apt/sources.list
comment(#) out the cdrom and uncomment all the repos
ctrl and x and y and enter to save
apt-get update
apt-get install x-window-system-core gdm xterm fluxbox synaptic
reboot
now you get a gui to login, select fluxbox in session and login. You should have the base now. You can go straight to synaptic and start selecting what you want to use or uninstall things that you don't need like the extra drivers then install what you want.
I usally select light weight things like rox-filer(filemanger), leafpad(editor),gaim,dillo,xpdf,abiword,xarchiver(to unpack),xfburn(cd burner)....I like to install as i go when i need it, instead of trying to install everything up front.

Alright I'm lost at the "comment(#) out the cdrom and uncomment all the repos" part

---

### Post by Najand on 2006-09-18
Delete all # signs at the begining of the lines starting with "deb", "deb-src", and put a # sign before the line starting with "deb cdrom".

---

### Post by Zigon on 2006-09-18
=D!! Awsome thanks for everyones help, wow it looks nothing like the live cd.

---

### Post by Najand on 2006-09-18
well then you are just fine.... Even with having Live CD... The apt will give the priority to the Internet packages. So there won't be any problems.

---

### Post by kerry_s on 2006-09-18
Once you've done it a few times and get use to the sever install. You can try other WM's like wmaker, icewm, gnome-core, kdebase, You just use the same install but change the "fluxbox" to the window manager you want. Right now i'm playing with wmaker(aka: windowmaker). You can look what other mini distro's use for applications and try some of those to keep the size down and the speed up. :)  don't be afraid to experiment till you find your sweet spot for your computer. Here's a pic of wmaker that i'm playing with and learning to use->

---

### Post by DJiNN on 2006-09-18
I'm using Dapper (With Gnome) on a 2.4ghz P4 with a Gig of Ram, and this machine is NOT much faster than the P3 that i have (700Mhz with 256mb Ram) runnig Zenwalk. 

It's strange but sometimes Dapper feels fairly snappy(ish), and then i go use something like "Thunderbird" & it's sooooo slow! :)  So it's hard to know whether it's just the general bloat of the system (Gnome et al) or just one or two particular apps.

I've also got Fluxbox running on Zenwalk (Thanks bhodi) & it's really snappy. Just about to give it a try here on Dapper & see what difference it makes, although because i've installed as a package on an already bloated system, maybe it won't perform anywhere near as well as it would on a fresh server install?  

As for running on a 128mb of ram, i've done that with both Zenwalk & Fluxbuntu (& also Xubuntu) & they all ran really well, given the limitations.  Also, what about "Puppy" or "DSL"? Worth a shot...?

---

### Post by bodhi.zazen on 2006-09-18
Puppy and DSL are both very nice and are "Ultra lights". Biggest problems with both is small size or repositories and occasionally hardware detection. I could not compile on either OS.

You may also like SLAX, especially if you like Zenwalk.

Ubuntu is much faster if you do a server install and add only what you need as Zigon, kerry_s, or anyone who does a server install and adds X will attest.

Slowness of Ubuntu is more pervasive then a single application or window manager. For example you can install Gnome in Zenwalk with just 6 additional packages over the base install and it also is quite fast. See the Fluxbuntu site for some discussion of the issue, although Fluxbuntu is in the "alpha" stages. As an alpha it runs well and hardware detection was quite good.

Disadvantage of moving away from Ubuntu is these distros become less user friendly. Sure you can boot and use the default applications, not rocket science there. What about ssh, samba, adding applications, sys admin, etc.

None of these have a colorful forum like Ubuntu either :)

You may find yourself moving towards one of these distro's to boost performance once you have "cut your teeth" on Ubuntu.

---

### Post by xpod on 2006-09-18
> Wow, must have a very brave heart... Hahaha

Good stuff Zigon..Welcome to THE machine..
Hope you ..like me have many hours of endless fun.
Just popped home for lunch so im away back to work to break some rocks.](*,) 

I get "withdrawal symptoms" cause i really want to be HERE breaking THIS!!.

==D> See ye around=D> =

ps (i dont really break rocks...Well:-\" ,I restore them!)

If ONLY a few more bravehearts would take the plunge eh!!:biggrin:

---

