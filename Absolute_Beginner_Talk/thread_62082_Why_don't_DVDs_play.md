---
title: "Why don't DVDs play?"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by Vulpus on 2005-09-03
I have been using Ubuntu for about three months and I am generally very pleased with it.  My previous experience of Linux was with Mandrake.  Arguably that has the advantage that everything (?) works 'out of the box'.  Whereas with Ubuntu I have had to you have add certain things manually (e.g. MP3 play).  Personally I do not mind that too much as I like tinkering with software and PCs.  However, the one I have NEVER got to work is DVD playback.  That has not been a big issue but it has slowly been nagging at me as it SHOULD work.

I have tried various DVD players and the closest I have got to working is Xine.  Others (VLC etc) usually either hang up or close down.  I have followed the instructions in the Ubuntuguide to install and configure Xine and it at least TRYS to play the DVD.

When I insert a DVD it is detected correctly, Xine tries to play it and then I get the following error message:

[I]The source cannot be read
Maybe you do not have enough rights for this or source doesn't contain data (e.g. not disc in drive). (Error reading from DVD) [/I]

The last line of the log viewer is:

*snd_pcm_open() failed:-16:Device or resource busy*

Anyone got any ideas or can recommend an alternative DVD player?

---

### Post by bored2k on 2005-09-03
1. [http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)
2. VLC or MPlayer

---

### Post by nic2 on 2005-09-03
The following Howto might just do the trick for you:

[http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646)

---

### Post by bored2k on 2005-09-03
[QUOTE=nic2]The following Howto might just do the trick for you:

[http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646)[/QUOTE]
 I disagree. Just do the steps I said and you should be fact. The above link is an automated script that installs a gazillion things you may or may not want, and its DVD section is just what I told Vulpus to do.

---

### Post by Vulpus on 2005-09-03
[QUOTE=bored2k]1. [http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)
2. VLC or MPlayer[/QUOTE]

I have tried all the steps in point 1. except 'sudo apt-get install libdvdcss2'.  Apparently that file is not available.

I have also tried VLC (it opens and then closes imediately) and MPlayer which gives an error messagewhich i forget.  The player that seems to get the closest to working is Xine.

The error I get when trying to install libdvdcss2 is:

[I]Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate[/I]

---

### Post by bored2k on 2005-09-03
[QUOTE=Vulpus]I have tried all the steps in point 1. except 'sudo apt-get install libdvdcss2'.  Apparently that file is not available.

I have also tried VLC (it opens and then closes imediately) and MPlayer which gives an error messagewhich i forget.  The player that seems to get the closest to working is Xine.

The error I get when trying to install libdvdcss2 is:

[I]Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate[/I][/QUOTE]
 1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install libdvdcss2

Retry

---

### Post by Vulpus on 2005-09-03
Nope!  Still get:

[I]dt@ubuntu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
dt@ubuntu:~$[/I]

---

### Post by aysiu on 2005-09-03
Did you *sudo apt-get update* after changing your /etc/apt/sources.list?
If not, do it.
If so, post your sources.list file, so we can see what's missing.

---

### Post by Vulpus on 2005-09-03
Erm?  I did a gedit on sources.list and there is nothing there!  Have I got the right one?

/etc/apt/sources.list

---

### Post by cedarbarn on 2005-09-03
HI, another newb here.  I did everything above, and have successfully used xine to play DVD.

---

### Post by poofyhairguy on 2005-09-03
[QUOTE=Vulpus]Erm?  I did a gedit on sources.list and there is nothing there!  Have I got the right one?

/etc/apt/sources.list[/QUOTE]


Add this:
> 
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by Vulpus on 2005-09-04
I did  'sudo gedit etc/apt/sources.list' pasted in the quoted text but it won't let me save the file!  ](*,)

---

### Post by Vulpus on 2005-09-04
[QUOTE=cedarbarn]HI, another newb here.  I did everything above, and have successfully used xine to play DVD.[/QUOTE]

Thank you!

---

### Post by vruum on 2005-09-04
> I did 'sudo gedit etc/apt/sources.list' pasted in the quoted text but it won't let me save the file!   
Don't know if it's just a typo but that should be 

'sudo gedit /etc/apt/sources.list' 
the "/" before etc was missing

---

### Post by Vulpus on 2005-09-04
[QUOTE=vruum]Don't know if it's just a typo but that should be 

'sudo gedit /etc/apt/sources.list' 
the "/" before etc was missing[/QUOTE]

DOH!!!!  ](*,)   That explains the empty file!  The contents of my sources.list is actually:

[I]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

[/I]

---

### Post by thundertoad on 2005-09-04
Hi,
so did you actually get it to work or what?

I also have a combo drive (CD / DVD writer/reader) and I have ubuntu for AMD64 installed and I cant for the life of me get the DVD to play dvd movies... its driving me nuts... its the only issue I have with my ubuntu system... if that gets fixed i'd be in ubuntu heaven... 

anyhoo... I had the same issue with it telling me that there is no media and that I might not have the right privilages.

but mostly that there is no media in the drive...

thanks
ThunderToad

---

### Post by Vulpus on 2005-09-04
No, it still isnt working!  In fact it seems worse than ever.  Now the Xine control panel doesn't load! 

I rarely actually NEED to play DVDs on my PC so I could do it in windows.  But it galls me that Windows can do something that Ubuntu cannot!

---

### Post by vruum on 2005-09-04
just in case you haven't given up yet, a few things that might help,
first, did you add the extra repositories to your sources.list ? I think the backports were missing.

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


also, xine looks for the dvd in /dev/dvd, which should be a symlink to your dvd drive, try doing:

ls -l /dev/dvd

to see what it points to. About the xine control panel, do you mean the player controls? try, when xine is focused pressing "g", 
it should be doable to play dvd's

---

### Post by thundertoad on 2005-09-04
Man I feel for ya,

Although xine is working fine... I just get nothing when I put a dvd in the drive. and it doesnt see it... it sees CDs fine though.

I would uninstall xine and reinstall it if I was you... no win dlls thank God.

But I know what you mean with the whole windoze playing the DVD. And to top it off in the Ubuntuguide.org site the libdvdcss2 file or whatever isnt applicable for an AMD64 install so I had to go to tamir's ripository (i think its in the AMD64 support section of this forum) and add those and then download from him the libdvdcss2 (am I spelling this right?) files and install them.... AND YET I STILL CANT GET THE FRIKKIN DVD TO WORK....

AAAARRRRRGGGGGGHHHHH    HULK MAD..
er... I feel much better now... really.

ThunderToad

---

### Post by rah on 2005-09-04
I can't play DVDs either.  This is what I've done so far:

1.  I added the multiverse and backports repositories as described in the unofficial guide.  libdvdcss isn't there, as far as I can see.

2.  I tried adding Tamir's unofficial AMD64 repositories -- I'm running AMD64 -- but I couldn't find libdvdcss there either.

3.  I tried adding the Marillat repositories; at last, I found libdvdcss, but Totem-xine still gives this message about how the medium is encrypted and can't be read.

4.  I have a RPM for libdvdcss, built for AMD64, so I used alien to convert it to a deb package and installed that.  The message from Totem-xine hasn't changed.

On top of all this, I can't seem to get all my speakers working -- I've got a 5.1 set, but I only get 2.1 sound (front right left, and subwoofer).  That's another story though.

I like Ubuntu so far, but the no DVD thing is killing me -- I don't have a real DVD player or television.  If I can get that sorted, along with my 5.1 surround sound and get playing some old games on MAME, I'll be happy.

---

### Post by thundertoad on 2005-09-04
OK so what I did was try that command you posted for the dvd... the ls -l /dev/dvd command and what it displays is this:

me@funkymachinename:~$ ls -l /dev/dvd
lrwxrwxrwx  1 root root 3 2005-09-05 02:56 /dev/dvd -> hda

so... uh... what does that mean... hey rah... I was actually able to get the libdvdcss files off tamir's ripository... you might want to try again

---

### Post by vruum on 2005-09-04
> OK so what I did was try that command you posted for the dvd... the ls -l /dev/dvd command and what it displays is this:

me@funkymachinename:~$ ls -l /dev/dvd
lrwxrwxrwx 1 root root 3 2005-09-05 02:56 /dev/dvd -> hda

so... uh... what does that mean... hey rah... I was actually able to get the libdvdcss files off tamir's ripository... you might want to try again 

the output means that /dev/dvd, which should be a symbolic link to your dvd drive, and is, by default the one xine tries to read from, points to /dev/hda, which seems a bit off, since /dev/hda is your primary master ide drive. /dev/hdb is the primary slave, hdc is secondary master etc. f you already know the name of the dvd drive,  delete the old /dev/dvd, and make a new one.

sudo ln -s /dev/[name of dvd drive] /dev/dvd
if you don't know the name, in the xine settings media tab try changing the dvd settings from /dev/dvd to /dev/hdb or /dev/hdc /dev/hdd see if any of them work

---

### Post by thundertoad on 2005-09-04
[QUOTE=vruum]the output means that /dev/dvd, which should be a symbolic link to your dvd drive, and is, by default the one xine tries to read from, points to /dev/hda, which seems a bit off, since /dev/hda is your primary master ide drive. /dev/hdb is the primary slave, hdc is secondary master etc. f you already know the name of the dvd drive,  delete the old /dev/dvd, and make a new one.

sudo ln -s /dev/[name of dvd drive] /dev/dvd
if you don't know the name, in the xine settings media tab try changing the dvd settings from /dev/dvd to /dev/hdb or /dev/hdc /dev/hdd see if any of them work[/QUOTE]
 Very cool, Thanks
I think one of the reasons why it says hda... is because I dont have any hd drives... both my drives are serial ata drives so they are listed as sda sdb etc
... I hope this works... 
... I'll keep you informed with what happens

---

### Post by thundertoad on 2005-09-04
Ok this is sorta embaressing but ... I cant help be tell the truth on this...
it seems that the dvd I was using to test whether my ubuntu was playing dvds at all was messed up... Having said that I apologize for bothering you folk with the posts. All I did was put in a different dvd movie and xine recognized it immediatly.

Vulpus ... I apologize for hoggin the post and ending up with... well with having a simple enough solution for the problem.

Rah... I'm sorry ma brotha... I shudder to even suggest this... but have you tried a different dvd... I mean hey I look like a total n00bified b00b .. but I figure i'll avoid hiding this from you folks so as not to confuse those who do have a more serious problem.

Vruum.. thank you for your input and I apologize for the inconvenience.

I will go and wallow in my wretchedness ... and not watch any DVDs in solidarity with Rah.. ... the moment you get your DVD running... I'll break my DVD fast.

anyway... I better go and let you guys figure out what it is thats messin up with Rah's system... incidently Rah which athlon processor do you have? ... whats your configuration?

Just plain toad

---

### Post by invisage01 on 2005-09-04
with that dvdcss2 thinga.. i had the same problem with the package not being available.. but do a quick search using synaptec for "dvd" and a similar looking package came up.. i just installed that and it seemed to work fine for me after that.. im at work now so i can't tell you exactly what the package name is.. but just do a search in there and see if it turns up.. 

Iain.

---

### Post by rah on 2005-09-04
I tried Tamir's repository and this is what I get:

W: Failed to fetch [http://tamir.nooms.de/ubuntu/dists/hoary/universe/binary-amd64/libdvdcss2_1.2.9-1ubuntu1_amd64.deb](http://tamir.nooms.de/ubuntu/dists/hoary/universe/binary-amd64/libdvdcss2_1.2.9-1ubuntu1_amd64.deb)
  404 Not Found

I was using Synaptic -- that shouldn't matter should it?

invisage - Thanks for your suggestion, but I can't figure out which file you're talking about.  There's libdvdread3, but I have that already, and I was pretty sure that decryption was impossible without libdvdcss specifically.

thundertoad - Go ahead and watch 'em if you got 'em; don't deprive yourself on my account.  I'm just glad it's working for you.  I know my DVD is okay because it was working a couple of days ago on my SUSE 9.3 system, before I somehow broke that too.  Getting DVDs to play on my P4 SUSE 9.1 system a few months ago was so much easier...  (This is a new machine I'm playing with, AMD64 3700+.)

EDIT:  It seems that libdvdcss2 was removed sometime yesterday.  I don't yet know why... :neutral:

EDIT #2: Apparently it was removed because of legal concerns. :mad:

---

### Post by thundertoad on 2005-09-05
[QUOTE=rah]I tried Tamir's repository and this is what I get:

W: Failed to fetch [http://tamir.nooms.de/ubuntu/dists/hoary/universe/binary-amd64/libdvdcss2_1.2.9-1ubuntu1_amd64.deb](http://tamir.nooms.de/ubuntu/dists/hoary/universe/binary-amd64/libdvdcss2_1.2.9-1ubuntu1_amd64.deb)
  404 Not Found

I was using Synaptic -- that shouldn't matter should it?

invisage - Thanks for your suggestion, but I can't figure out which file you're talking about.  There's libdvdread3, but I have that already, and I was pretty sure that decryption was impossible without libdvdcss specifically.

thundertoad - Go ahead and watch 'em if you got 'em; don't deprive yourself on my account.  I'm just glad it's working for you.  I know my DVD is okay because it was working a couple of days ago on my SUSE 9.3 system, before I somehow broke that too.  Getting DVDs to play on my P4 SUSE 9.1 system a few months ago was so much easier...  (This is a new machine I'm playing with, AMD64 3700+.)

EDIT:  It seems that libdvdcss2 was removed sometime yesterday.  I don't yet know why... :neutral:

EDIT #2: Apparently it was removed because of legal concerns. :mad:[/QUOTE]
 Well isnt that just a kick in the java beans. I thought libdvdcss2 was GNU.
hmm.. so technically speaking... when someone downloads that file... doesnt it get cached on their system?
where does it get catched? anybody know?
maybe someone can send you their cached file... and you can run that!

oh hey I had found this other post somewhere where the guy told you to install fakeroot and run this script to get the dvd working. Google that... dvd+fakeroot+install or something... I am just the worst reference since I dunno if the stupid dvd was always working ... or one of my 60 different remedies got it working.. And now I gotta go get me a new frikkin dvd to replace the one that got fragged up.

Galactica anyone?

---

### Post by ssck on 2005-09-05
i feel all of you guys who are having problems with dvd playback

i have been trying to get it to work but to no avail.it's not like it doesn't play.it just plays for about 10 minutes or so, and then it freezes.i have tried with dma on, tried with different players, .....  ](*,) 

frustration ...... anyone has any ideas ?

---

### Post by thundertoad on 2005-09-05
[QUOTE=ssck]i feel all of you guys who are having problems with dvd playback

i have been trying to get it to work but to no avail.it's not like it doesn't play.it just plays for about 10 minutes or so, and then it freezes.i have tried with dma on, tried with different players, .....  ](*,) 

frustration ...... anyone has any ideas ?[/QUOTE]
 Hey guys, 

Been doing a little bit of digging... least I could do after that last debacle... so here are a few links to other forums that had the same issue:

[http://www.linuxquestions.org/questions/archive/63/2005/07/1/338908](http://www.linuxquestions.org/questions/archive/63/2005/07/1/338908)

[http://www.linuxquestions.org/questions/showthread.php?s=&postid=1823269#post1823269](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1823269#post1823269)

[http://www.linuxquestions.org/questions/history/349791](http://www.linuxquestions.org/questions/history/349791)

hope this helps.

Thundertoad

---

### Post by Steve1961 on 2005-09-05
I also had a problem with not be able to play DVDs in Ubuntu 64 until I ran the script in /usr/share/doc/libdvdread3/examples following advice I received from a forum member.  Just 

cd /usr/share/doc/libdvdread3/examples
sudo ./install-css.sh

It worked for me!

---

### Post by thundertoad on 2005-09-05
[QUOTE=Steve1961]I also had a problem with not be able to play DVDs in Ubuntu 64 until I ran the script in /usr/share/doc/libdvdread3/examples following advice I received from a forum member.  Just 

cd /usr/share/doc/libdvdread3/examples
sudo ./install-css.sh

It worked for me![/QUOTE]
 Yup I ran that too... one of the many many many (police academy anyone) many remedies that I tried.. .but it said that it was experimental... so give that a try too... hell I did.

I think you need fakeroot for it though... steve do you remember the forum you got it from? I think there were a bit more things you had to do and some libs you needed to get it to run properly.

Thunder... Thunder... Thundertoad.... hoooooooooooooooooo (what the hell did he say... and who is he calling h0!?)

---

### Post by Steve1961 on 2005-09-05
It was a private message but you're right, I did have to install some extras.  They were build-essential, fakeroot, the linux headers for my version, and debhelper.  I think I was missing fakeroot when I first tried to run the script, but when you run it it starts out by listing everything you need and gives you the option of terminating by pressing control c (I think) before you proceed.  I did this and just double checked in Synaptic that I had everything, and then ran it again.

You tend to need these packages anyway when you're compiling source code so probably a good idea to install them anyway.  

From what I can gather the script downloads the source for libdvdcss2 from the web and compiles it on your system.  It takes a while, with lots of entries flashing past in the terminal, but once it had finished I put a DVD in the drive and Xine launched straight away and started playing it.

---

### Post by Vulpus on 2005-09-05
I have to say I am very dissapointed by this debacle!  DVDs are not exactly new technology and it seems a major failing of Ubuntu not be able to play them.  Yes I know some people can play them without problems but that is not good enough.  This is not going to stop me using Ubuntu but it will make me consider some alternatives, especially iv Breazy doesnt solve the problem.  :-|

---

### Post by Steve1961 on 2005-09-05
I know it can be frustrating but Ubuntu is a free distribution and its committed to supplying free software.  From what I can gather they would be on legally dodgy (or at least gray) ground if proprietary codecs were supplied on the CD.  Stick with it my friend.  After a few weeks, once you have your system configured the way you want it, you'll really start to see what a great distro it is.

---

### Post by thundertoad on 2005-09-05
oh hey ... I just found this posting where the guy was saying that his dvd drive make was the cause of his dvd not working... tell you what... so as to exhaust the crap out of this thing.. how about you ask a friend of yours to bring over their dvd player and see if its something like that... like its some hardware conflict or something... As for me... I went and found myself yet another ubuntu amd64 problem... Frikkin FLASH... no flash plugins work for this distro... what the frik was the point of this processor... its brought me grief.... grief I tell ya.

(and the oscar goes to.... )
moi

---

