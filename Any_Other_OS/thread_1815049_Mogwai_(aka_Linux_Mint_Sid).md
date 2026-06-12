---
title: "Mogwai (aka Linux Mint Sid)"
date: 2011-07-30
forum: Any Other OS
---

### Post by cbowman57 on 2011-07-30
**What is Mogwai?**  

To put it simply, it's a discussion/project/recipe for upgrading(?) Linux Mint Debian Edition (LMDE) to unstable and installing Gnome 3.0 shell in it. If there is interest shown there might even be a custom iso available in the near future.

[[COLOR=SeaGreen]Click here for the latest recipe for Mogwai[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11109751&postcount=68")

**How the name Mogwai was chosen**: (Revised) 

A few months ago I went searching for a name for another project.  What I discovered was that in African culture gnome=gremlin, went searching for what they were called and came back with Mogwai.  The name was used in the movie "Gremlins" & is probably Chinese in origin.  For some reason I had it in my head the name was African but when it was checked recently no African link was found.  Anyway, it's a cute name & we'll keep it.  Trying to install Gnome 3.0 shell on Debian does unleash the gremlins, so the name fits it pretty well. :)

[ATTACH]198873[/ATTACH]

**What is the best way to use the information in this thread?**

If you're looking for info on how to install Gnome 3.0 shell on a Debian distro (including LMDE), start at the last post & work your way backwards.  The ongoing chatter is the result of experimentation in attempt to streamline & simplify the process.

_[COLOR=RoyalBlue]Helpful links:[/COLOR]_

[COLOR=SeaGreen]**[Download Linux Mint Debian]("http://www.linuxmint.com/download_lmde.php")**[/COLOR]
[B]
[How to install GNOME 3 on Debian testing aka wheezy]("http://raphaelhertzog.com/2011/06/16/installing-gnome-3-on-debian-6-0-squeeze-no-sorry/")[/B]

**[Gnome3 for the experienced (FUN Stuff!!!)]("http://forums.linuxmint.com/viewtopic.php?f=141&t=65745#p379338")**

                                                                   [B][URL="http://forums.linuxmint.com/viewtopic.php?f=141&t=63392&start=20#p417263"]Fix: Cannot install Remastersys on LMDE
[/URL][/B]



Commands to get Debian tweaker script smxi:
(You need to use sudo or be in root terminal)

```
cd /usr/local/bin && wget -Nc smxi.org/smxi.zip && unzip smxi.zip && smxi
```* I expanded the scope of my experimentation, quickest & easiest method (for me) was to start with a Debian net install.

[ATTACH]199240[/ATTACH]

[ATTACH]199241[/ATTACH]

---

### Post by Naiki Muliaina on 2011-07-30
Looks like a fancy way of saying '***FIRST!***'..... Heee ^^

---

### Post by cbowman57 on 2011-07-30
First?  Don't know about that but I've been playing with LMDE for a couple weeks & it started a discussion that probably didn't belong in the other thread. :)

Have you been tinkering Naiki?

---

### Post by Naiki Muliaina on 2011-07-30
No links or anything in your first post when I replied just 1 line of text ^^

Haven't tinkered, been a while scince I had a go at Mint, been put off by the Debian direction a bit ^^

---

### Post by cbowman57 on 2011-07-30
Ok, some lessons learned.

1. Easier to start with LMDE the Xfce spin.
2. Local repository, I found I was doing a lot of reinstallations and have a slow connection.  If you have space create a local repository for your deb files.  After you add/delete, make changes copy or move the packages from /var/cache/apt/archives to your repo.  When you do your safe & dist-upgrades later you can transfer those .debs to that directory (/var/cache/apt/archives) & save a lot of downloading. (This also might apply to those of you testing Oneiric)

---

### Post by cbowman57 on 2011-07-30
> **Naiki Muliaina said:**
> No links or anything in your first post when I replied just 1 line of text ^^

Haven't tinkered, been a while scince I had a go at Mint, been put off by the Debian direction a bit ^^

Yeah, I just needed an url to link to the other thread.

I've used Mint before, and toyed with Debian some but this is new ground for me so I'm making plenty of mistakes.

Now post #1 has a little more content that makes some sense. :)

---

### Post by mips on 2011-07-30
Love the name, Mogwai, obviously from the Gremlins movie :D

---

### Post by el_koraco on 2011-07-30
So it's coming to life. You never know, you might end up as a Linux Mint developer by the end of this.

---

### Post by cbowman57 on 2011-07-30
> **mips said:**
> Love the name, Mogwai, obviously from the Gremlins movie :D

Actually the influence from the movie was secondary, though creating a distro with version naming conventions like Spike & Gizmo definitely have their appeal.

Actually it was taken from the culture in your part of the world & it sounds cool, add that to the movie recognition that is unavoidable and it seemed like a good name.

@el_koraco; That sounds like work but I hope a couple of us have some fun sorting this mess out. :)

@all; Updated post #1

---

### Post by 23dornot23d on 2011-07-30
Looking good ...... and glad we have a thread for it .... played a little last night 
then got it working today ...... for 32 bit and used remastersys on the 32 bit
seems to have worked .... this ones based on MINT 11 + Oneiric though .... and a tad of debian ...

[IMG]http://img705.imageshack.us/img705/2667/screenshotat20110730210.jpg[/IMG]

All good fun ...... ;)

and the beauty is it sits nicely ontop of KDE too .... [COLOR=Blue]_***[SCREENSHOT]("http://img850.imageshack.us/img850/2830/screenshotat20110730180.jpg")***_[/COLOR] .... likeing this a lot now ....

---

### Post by cbowman57 on 2011-07-30
@Keith; Can you retrace your steps & post your method?  I've got a feeling I'm trying to do it the hard way.

I'm still feeling my way along, trying to get more familiar with Debian, LMDE gives it some familiarity & contains a lot of the non-free packages by default, but it's still a little alien to me. Especially the difference in package management in comparision to Ubuntu & it's ppa's.

The one I built on LMDE Xfce last night is running real well for me too, but I did a lot of installation using synaptic.  There has to be an easier way. :)

---

### Post by 23dornot23d on 2011-07-30
Lols .....

I actually made a mistake last night ..... and thought I had got the debian version

So added the debian SID repository to it and started updating it ,,,,, no sweat as it only added about 4 packages ,,,, 
which I can see and remove in synaptic ..... if I want to ....

as you know disableing repositories is no big deal neither ...... so have done that ....
(once I realised what had happened .....)

So then just updated as I would with the noral Natty to ONeiric ....
using a link to set the repositories to Oneiric ....

Then dist upgraded it .......

and all the usual happened that I have already been through before .....

Just a case of retracing my log that I keep in my mail in Ubuntu ...... and doing it all again

Last night though ...... no this morning 6:30 AM ..... when I rebooted ..... it was just a blank blue screen

Woke at 2:30 after a bit of shut eye ...... and continued with it ..... and things started to come together,



Now it all works well ..... but its the 3.0.0-7 kernel .... the latest Nvidia driver    
and its based on the mint 11 distro 32 bit ..... so the next step now is to do it all again
with the 64 bit one ...... only trouble is my desktop test machines are 32 bit ....
so ..... 
( I have created a remastersys of this though and it seemed to go well - not burnt it to Dvd yet to check though )

Do I continue with this ..... which is basically MINT oneiric with the Debian Repository added
or start again ...... :confused:

and risk it on my main laptop ..... which is the 64 bit one and my Production machine  ..... ?

---

### Post by cbowman57 on 2011-07-30
Well it's up to you how you want to continue but I'm going to base mine on LMDE :)

Starting with LMDE is a completely different animal than using Ubuntu or Mint.

---

### Post by 23dornot23d on 2011-07-30
Ok I am ready to go


Got the Debain one in and it works on the desktop machine ...... its MINT 10 though ,,,,, is there a Debian 11

kernel 2.6.32-5-amd64 .....


Give me a link to the one your using if its different and we will both start on the same page so to speak ..:D

---

### Post by cbowman57 on 2011-07-30
**[Download Linux Mint Debian]("http://www.linuxmint.com/download_lmde.php")** (added to post #1)

Yeah, the LMDE doesn't use versions, just incorporates the date the iso was made.  I've used both, the Gnome & Xfce editions, and I think the Xfce edition is a better starting point.

---

### Post by 23dornot23d on 2011-07-30
Ok I need to download and burn the XFCE one .... 64 bit or 32 bit ?

I have the 64 bit Debian v10 - may save this for another time though ....

[COLOR=Red](while the other is downloading will install this too though)
[/COLOR] 
_______________________________

So will use [xfce 32 bit ]("http://www.linuxmint.com/edition.php?id=79").....  ok its downloading now ...... 1.0 meg per second ... so it should not be long ....

Am downloading it now ...... will post again when its burnt and installed

I will catch up to you .... sometime tonight this is going to be a long session .....

and will try to install both on the USB drive ..... and gives me two chances of screwing up then lols ;)

---

### Post by cbowman57 on 2011-07-30
Cool, I need to find that post that told how to get Remastersys working under LMDE.  From my experiment yesterday I managed to get it to work but to install I had to downgrade to gdm 2.32 and used the Remastersys Installation app.

Found the link for a fix, added to post #1.

---

### Post by 23dornot23d on 2011-07-30
Ok we can get Gnome-Shell working as gnome v2.32 ..... and then burn a remastersys disk ,,,,

then upgrade  later .....
 
to 3.1.3 or whatever Debian have and try another one ..... see how far we get ...

at least this way we can document it all and keep check on what we are doing ,,,,,,


See what works and what works ..... if anything ..... ;)

Ok slightly different installer for Debian ,,,,, first problem it hung .... on the empty partition did not format it ....
( and the installer would not format it for some reason )

so used gparted and formated and set it up myself as / root ....

now its going quite happily ... quite fast too .....

meanwhile the xfce is being burned to another DVD ...... just where to put it .....  ?

Will see how the 64 bit Debian installs and works first ..... if its no good will just overwrite it ....
otherwise might have been better splitting the partition in two ..... oh well .....

no problem the 64 bit just gave up 3/4 of way through at ttynaame3.gz ..... so it gets wiped and the 32 bit xfce is going on there now ....

---

### Post by cbowman57 on 2011-07-30
I just got Remastersys working, burning the resulting iso to flash now.

---

### Post by 23dornot23d on 2011-07-30
Nice one ..... I am 1/4 the way through installing XFCE and it runs fast from the DVD too

nice .....:D

I just hate the screensavers while installing why dont they disable them by default ....

 .... with 512 Meg memory ... they can kill a installation ... ( sure thats what happened on the 64 bit one a minute ago )

Nope same has happened again 3/4 of way through ..... just stopped dead .... 

One more go and going to alter this partion size .... just in case there is a problem on the hard drive.....

will skip the first gig .... and leave it as empty space ....

Moved the installation on a GIg and also reformated both the swap and the 14 Gig root for it ....

hopefully this time it will go on ....

---

### Post by cbowman57 on 2011-07-30
Yeah, Xfce in Debian flies. :)

---

### Post by 23dornot23d on 2011-07-30
Ok well its looking better now upto localazing thunderbird and Firefox

Installing bootloader

configuring bootloader

ok reboot time .... all done for install

wow ..... nice bootloader too ...

fast boot .... and a gdm login ... screen too

Ok first thing what do we do load up the Nvidia-Current drivers ?

as this is bizarre the screen keeps flashing on and off ..... on for 5 sconds off for 1 second




The version here already has build dependancy problems .....  as soon as I try adding Nvidia-xconfig
its asking me to fix dependancy problems .......... will sort them out


ok - not sure if this is the right way to go but am sorting out the dependancy problem with
a dist-upgrade ..... see where it takes me ...

its early enough on to re-install if it does not work out ok ,,,,,,.

---

### Post by cbowman57 on 2011-07-30
> **23dornot23d said:**
> 

Ok first thing what do we do load up the Nvidia-Current drivers ?

as this is bizarre the screen keeps flashing on and off ..... on for 5 sconds off for 1 second

You can use the smxi script to install the drivers, if you select the beta you'll get 280.11 today.

Not sure about the flashing screen, that's when you logon to the desktop?

---

### Post by 23dornot23d on 2011-07-30
> 
You can use the smxi script to install the drivers, if you select the beta you'll get 280.11 today.
( its doing the flashing constantly ..... on the desktop screen .... never seen anything like it before )

Where is the script ......  ? 

if you can supply a link I have 2 computers going and can quickly transfer from one to the other

I am already in the process of distribution upgrade .... but could stop it if needs be ..... 45% at moment

what do you think .... ?

---

### Post by cbowman57 on 2011-07-30
Go ahead & do the dist-upgrade.

---

### Post by 23dornot23d on 2011-07-30
Ok doing that ...... 3 mins to go to download the lot .....

well the desktop and the speed it works is good ..... but the flashing screen is weird ....

 ,,,, this is the Nvidia 6300 ...

ok pre configuring packages ...... now a long wait unpacking and installing them


Processing them now ..... all the graphics drivers seem to have loaded in and its going well

but will need to make a decision whether to risk rebooting ,,,,,,, or do as much as possible while
we have a desktop  ......

as 891 Meg of updates is no small task .... but it will be totally up to date ,,
and hope fully will be free of problems ,,,, ;)

ok kernel its loaded in is 2.6.39-2-686-pae ///

need headers and the nvidia drivers ..... loading before reboot ....

[IMG]http://img200.imageshack.us/img200/1853/screenshot310711032017s.jpg[/IMG]


Oh yes looking good now ..... no flashing after reboot - looking good 48 mins to install 890 Meg of compressed data
pretty good for a single processor ...

The thing is are there any dependency problems now .... ?

[IMG]http://img263.imageshack.us/img263/4976/screenshot310711033335s.jpg[/IMG]


Now we can work .... its totally uptodat and clean .... and is this smooth and fast too ..... love it ...

So to the Instructions .....[ thread 1 ]("http://ubuntuforums.org/showpost.php?p=11102434&postcount=1").....

[COLOR=Red][B][I]but before this ..... make sure your Graphics Divers are up to date  .... 1360 x 768 .... ( for me my resolution on the desktop ).
so what do we need 
Nvidia latest[/I][/B][/COLOR] ............ 

Synaptic add ..... this .... it pulls in all the Nvidia requirements too ......
nvidia-xconfig

also add
nvidia-settings

The graphics drivers may be best set up before we go into testing ..... ( but I did my upgrade in testing )
add the headers too .... 

from root terminal run .....

**nvidia-xconfig**

and then reboot .... see what we have !!! 

[IMG]http://img638.imageshack.us/img638/7863/screenshot310711041535s.jpg[/IMG]



Ok now to alter the /etc/apt/sources.list ....... from stable to testing

[I]sudo sed -i 's/stable/testing/g' /etc/apt/sources.list



deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) debian main upstream import
deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) testing main contrib non-free
deb [http://security.debian.org/](http://security.debian.org/) testing/updates main contrib non-free
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing main non-free



ok then add the following ......

[/I]**How to install GNOME 3 on Debian testing aka wheezy** ([ [COLOR=Red]link to original [/COLOR]]("http://raphaelhertzog.com/2011/06/16/installing-gnome-3-on-debian-6-0-squeeze-no-sorry/"))

 If you want to try GNOME 3 before it has landed in testing, you&#8217;ll have to add unstable and experimental to your sources.list:
 deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) unstable main contrib non-free 
deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) experimental main contrib non-free



ok this is where I decided not to follow the instructions ....

I Just added Gnome-shell and its dependencies ...... so if it all goes wrong for me here ..... follow the original link above .... in red

[IMG]http://img846.imageshack.us/img846/8002/screenshot310711044252s.jpg[/IMG]

ok this is running from a terminal still  ....... so now the final test ......
reboot ...... and run by itself !!!


[IMG]http://img62.imageshack.us/img62/679/screenshot0731201105020.jpg[/IMG]


We are in business ..... just needs customizing now ...... but it is smooth ,,,

[IMG]http://img577.imageshack.us/img577/7783/screenshot0731201105165.jpg[/IMG]

ok 5:19 am time to sleep ..... ;)

---

### Post by 23dornot23d on 2011-07-31
[IMG]http://img225.imageshack.us/img225/7591/screenshot0731201106253.jpg[/IMG]

Just the extensions to add now ..... will do that later on ...

---

### Post by cbowman57 on 2011-07-31
You made that look quick & easy. :)

Mine looks & runs great but even with gdm 2.20 installed I can't get the dist.iso to load the desktop, though it does boot and gives a working terminal.   It's an error loading Xserver, going to take a break from it for a while.

---

### Post by 23dornot23d on 2011-07-31
Ok what are the exact errors it was giving you ... ?

don't forget to disable the testing ppa's before loading in remastersys ,,,

as remastersys seems to do a lot of things before it actually starts ...... like upgrading parts
of the system and removing old files etc .....

I might have been lucky in the way mine installed ...... Debian Mint V10 .... for the  upgrade to the
latest SID release ..... Gnome 3.0.2 .......... which is behind Ubuntu ...... Gnome 3.1.4
it was reporing on one System Monitor ....

The two problems I did have were not show stoppers .....

1 ...... The flashing screen ...... which luckily stayed on long enough for me to work
          ( was like 5 to 10 seconds on .......... then one second off / black )


2 ...... My system originally locking after going 3/4 of the way through ...... this I put down   to either a bad Dvd or part of my Old 80 Gig hard drive being worn out ......


But its running gdm3 ..... now ...... guess later on today sometime I will try remastersys
and see if I get the same errrors as you do .....

if you have the exact error post it ..... please ......

For anybody else reading about this error we are discussing here - it has nothing to do with
Mint debian not working ( as Mint Debian runs very well indeed ) ....... but its to do with creating a brand new disk ......
Using remastersys to create it ...

Ok do I download remastersys and try it out ...... guess the answer to that has to be yes
will just see what the Debian version of [[COLOR=Red]_***remastersys is upto***_[/COLOR]]("http://sourceforge.net/projects/remastersys/files/remastersys-debian-squeeze/") ...... ok there are a few versions of it ..... guessing the newest are at the top ...... 

Time to wake up and smell the coffee again ..... now thats an idea coffee or a energy drink
neither being very good for the body .......

Heat wave here again by the way .......

ok have a good day .... Sunday is a day of rest .... also monday is in France .... so I will
take a day off tomorrow and go for a bike ride ..... :D

Looks like you are online now chuck ..... what version of remastersys do you want me to try .... ?

If we both use the same we should be able to work out if the errors are consistent ....

The other thing I always do is ensure the squashfs tools are loaded up too .....

---

### Post by mips on 2011-07-31
> **cbowman57 said:**
> 
**Actually it was taken from the culture in your part of the world** & it sounds cool, add that to the movie recognition that is unavoidable and it seemed like a good name.


You lost me there, please elaborate?

---

### Post by cbowman57 on 2011-07-31
The remastersys problem involves conflicting initramfs pkgs, I posted a link to a workaround in post #1.  I just created an iso and installed it, but I had to use the failsafe option to do it and it ran grub but didn't seem to install it correctly in the mbr, but other grub can see it. (Maybe I accidently selected the install to partition option).

Had to downgrade gdm3 to gdm, must use the Remastersys installer app

---

### Post by cbowman57 on 2011-07-31
> **mips said:**
> You lost me there, please elaborate?

Your location info puts you in South Africa.  The name Mogwai is from African culture. :)

---

### Post by 23dornot23d on 2011-07-31
> 
The remastersys problem involves conflicting initramfs pkgs, I posted a link to a workaround in post #1


Ok thanks for that ..... will check it out ..... I have just downloaded remastersys_2.0.20-1_all.deb

will be running it shortly ..ty

---

### Post by cbowman57 on 2011-07-31
I used 2.0.23-1, have no idea where I found it.  Had to run it from the command line.

---

### Post by mips on 2011-07-31
> **cbowman57 said:**
> Your location info puts you in South Africa.  The name Mogwai is from African culture. :)

Never heard of it in a african context and Google does not find anything either. Only reference to Mogwai in culture I could fine is in Chinese culture [http://en.wikipedia.org/wiki/Mogwai_(Chinese_culture](http://en.wikipedia.org/wiki/Mogwai_(Chinese_culture)) but that's on a different continent.

We've got Tokoloshes down here ;)

---

### Post by cbowman57 on 2011-07-31
> **mips said:**
> Never heard of it in a african context and Google does not find anything either. Only reference to Mogwai in culture I could fine is in Chinese culture [http://en.wikipedia.org/wiki/Mogwai_(Chinese_culture]("http://en.wikipedia.org/wiki/Mogwai_%28Chinese_culture")) but that's on a different continent.

We've got Tokoloshes down here ;)

That's the oddest thing.  I looked it up a couple months ago and that's what came up.

Very strange. :lol:

There was also the name & link to the movie Gremlins.  Oh well, still like the name, might as well stick with it.

---

### Post by 23dornot23d on 2011-07-31
ok thanks for the version number .....

I will try with the -20 first and see what happens as its installed and running now

using the fix from the [[COLOR=Blue]_**LINK**_[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=141&t=63392&start=20#p417263") that you posted ty

ok its running quite happily at the moment .... the speed this goes it will be ready well
after my sunday lunch is cooked .......  ..... ;)

Ok finished now .... 1.4 Gig .... reasonable size ..... now to see if it works .... ?

ok loaded k3b up and that has gone in ok .... loading lots of other packages too as its
kde based ..... but the disk is burning ..... will reboot as soon as it finishes to see if we have 
a working Dvd


Goes all the way through to the point where it should load the desktop up ..... but .....
Failed on the live boot ..... re FAIL comes up alongside it .... orange warnings also against squashfs ?

 
Ok tried it on another laptop
and it goes in ,,,, but only in safe mode ...... which is to be expected as I set it for Nvidia
and this is a S3 graphics card ..... but itts running from the CD .....

will try it on my main system now .....

ok no go ...... * if I was to try this again .......

Use the 32 bit debian 10
distribution upgrade .... 810 Meg 
load in the graphic drivers for Nvidia
set the repositories as outlined in this thread

remastersys ..... -20 works ..... and boots into safe mode ok ,,, problem graphics card on my laptop
bizarre .... but obviously its because it was not the Nvidia but a S3 that it worked and fell into
fallback mode .....

so just double check the transitional package thats the fix to the rematersys problem first ..... is it ok ?

Then do a version where we remove the xorg.conf ........ to force it to work in low graphics mode
first ......

I can try this now actually ..... just by 

mv xorg.conf xorg.confold

then after move it back again 

mv xorg.confold xorg.conf
( message to me put this back again before re-booting )

May give this one more go ....



need a treat now - _**[creme brulee]("http://en.wikipedia.org/wiki/Cr%C3%A8me_br%C3%BBl%C3%A9e")**_ .... yummmmm ;)

ok that was nice ,,,,,

Back to it ..... the Dvd with low resolution i.e no xorg.conf is burning now ..... lets see if it throws a error up
the xorg.conf can be added after a install - thats if this will install of course .... as I have not tried that yet.

But we have got a up to date Debian with all the files and repositories on now that are needed for Gnome-Shell

Interesting failing on the desktop ..... not enough memory 512 Meg ....

But the other Acer Aspire 1355 LC laptop ,,,,, it runs but as expected and drops into fallback gnome ,,,,


ok next problem the debian installer does not run ..... but

I have noticed there is a remastersys installer ..... now I have never seen this before .....
 
So first thing ..... will do [COLOR=Blue]_***[some research]("http://www.remastersys.com/forums/index.php?topic=1509.0")***_[/COLOR] ..... see what _***[screenshots there are of it functioning first ]("http://www.geekconnection.org/remastersys/debian.html")***_,,,

The thing I cannot see is where it is going to put the MBR and the GRUB ...... ?

I am re-sizing a partition for it now .... will see what happens ... as it could save me a lot of downloading of updates etc.

The partitioner is ok if you have set your system up for it - it makes it easy ...

It does ask where you would like the MBR ..... two options were given for me .....


Ok we have a success ...... it can be done this way

I now have a successful install and no errors ..... ;)

---

### Post by Winelord on 2011-07-31
> **mips said:**
> Only reference to Mogwai in culture I could fine is in Chinese culture

They're a great post-rock Scottish band, too.:D

---

### Post by cbowman57 on 2011-07-31
@Keith; Yeah, you end up having to use the Remastersys installer.

@Winelord; yeah, I saw that. :)

---

### Post by cbowman57 on 2011-07-31
> **mips said:**
> Never heard of it in a african context and Google does not find anything either. Only reference to Mogwai in culture I could fine is in Chinese culture [http://en.wikipedia.org/wiki/Mogwai_(Chinese_culture]("http://en.wikipedia.org/wiki/Mogwai_%28Chinese_culture")) but that's on a different continent.

We've got Tokoloshes down here ;)

Ok, I revised & corrected the origin of the name in post #1.  Don't know how I made that error when I was going through the search engines, too many open tabs maybe.

---

### Post by 23dornot23d on 2011-07-31
Ok Screenshot of installed version .... [[COLOR=Red]_***LINK***_[/COLOR]]("http://img10.imageshack.us/img10/8724/screenshot0731201108401.jpg")

so it took almost a full day ,,,,, but I could do it quicker next time .... lols .... ;)

Just by sticking the backup disk in .... now

At least you sorted a good routine out ,,,, and no doubt some time in the future we will have
a ISO to distribute ..... 

The one I have here is including all my logins and everything on it ..... although does bleachbit 
work ok on this ( whatever - I would still want to do it clean next time )

Maybe even the 64 bit .... if I ever get a laptop with a monitor on it .... this one runs
off my TV as the main screen on it does not work ......

So I boot up by braille ..... lols ... ( not seen a boot up screen or anything till the gdm comes up
for about 6 months now ..... since the monitor on the laptop died ..... makes life interesting.

cannot afford any mistakes otherwise once the laptop stops booting up ..... a new laptop would be needed

---

### Post by cbowman57 on 2011-07-31
> **23dornot23d said:**
> Ok Screenshot of installed version .... [[COLOR=Red]_***LINK***_[/COLOR]]("http://img10.imageshack.us/img10/8724/screenshot0731201108401.jpg")

so it took almost a full day ,,,,, but I could do it quicker next time .... lols .... ;)

I know what you mean, use my suggestion to maintain a local folder for all your .debs that you can copy into /var/cache/apt/archives & it goes real fast.

Looks good, what do you think of the performance compared to other distros?

---

### Post by 23dornot23d on 2011-07-31
Performance wise its almost twice as fast ,,,, or seems that way to my Ubuntu installs ....

Especially booting in to it there is a big difference ..... very quick ...  and it runs on my 512 Meg machines too

I like that I can see what is happening too ..... as it boots ...

I run Gimp quite a bit ..... doing the screenshots and things last night and its really responsive ..

( and 3D apps like blender and Wings 3d ....... not tested them yet )

but for firefox etc it flies ...... really good I would say ..... definitely one to keep ... and it may even become my main Distro ,,,,

Need another one of these 500 Gig USB drives .... may invest again ... as its safer writing the boot
to one of those then transferring it to my main laptop :D

Need another project now ......

---

### Post by cbowman57 on 2011-07-31
Yeah, it's pretty snappy.  Make sure you try the **export CLUTTER_VBLANK=none** in **~/.profile** kludge.

It's a little funny, Linux Mint was my gateway to Ubuntu & now they're doing it again with Debian.  Making the transition to Debian this way is a lot easier (for me) than trying to get comfortable with Suse or Fedora.

Oh, for the gnome-shell-extensions (common) & gnome-shell-user-theme you can use the natty .debs.

---

### Post by 23dornot23d on 2011-07-31
Same here ,,,, I have rpm based distros ..... but not too keen  although Fedora is so similar now in the way it operates to debian it might well have been the one I swapped to ...

But Mint is now covering two bases ..... for me .....

and

Now Gnome-Shell is on it ..... I am happy ..... :)

Nice to have choices .....

Just loaded Blender and Wings3d in ..... both are the latest releases so again thats good ...

> 
Yeah, it's pretty snappy.  Make sure you try the **export CLUTTER_VBLANK=none** in **~/.profile** kludge.
What will this do ?
[http://www.google.com/search?client=ubuntu&channel=fs&q=export+CLUTTER_VBLANK%3Dnone&ie=utf-8&oe=utf-8]("http://www.google.com/search?client=ubuntu&channel=fs&q=export+CLUTTER_VBLANK%3Dnone&ie=utf-8&oe=utf-8")


ok home/.profile kludge

might give it a try .....

---

### Post by cbowman57 on 2011-07-31
For some cards it's a workaround to fix sluggishness but it feels like it makes my system snappier.

---

### Post by 23dornot23d on 2011-07-31
Next job is to get conky running on it .... see if the transparency is there ....

Blender and wings3d work quite well in it too ...... just had a quick play ..... but I doubt
there will be that much difference in applications ...... running

But the system is definately very responsive .... on my older computers .... 
I need to get it on my main machine to test it properly though .....

If I set the MBR of the USB with it as the first operating system to boot its easy just to swap across
onto the laptop ..... but its almost time for my games of scrabble now ....  so its a job for another time.

[IMG]http://img851.imageshack.us/img851/2149/screenshot0801201112361.jpg[/IMG]

But not bad going learned a lot more today too .....

Ok its my main system now ...

---

### Post by cbowman57 on 2011-07-31
Yeah, bleachbit works great on it.

---

### Post by 23dornot23d on 2011-07-31
Ok cheers for that ...... and I have just nicely got conky going of a sorts .....

[[COLOR=Blue]_***Screenshot***_[/COLOR]]("http://img153.imageshack.us/img153/2558/screenshot0801201101280.jpg")

Look at that though ,,,,, only using 243 Meg ...... its always been around 400 before .... in Ubuntu ,,,

its only 322Mb with Firefox running too

Temps abot the same at 57^

so the system runs well ....

ok will add bleachbit now too .... ok done that ...

next the extensions - no themes or anything yet

---

### Post by cbowman57 on 2011-07-31
That's a really light footprint, especially with the nvidia drivers loaded.

---

### Post by 23dornot23d on 2011-07-31
Yep even now as I am working on it is stable at 366 Mb with Firefox open ..... and 10 tabs

Fan is hardly cutting in either and the temps are stable too at 57  ,,,,

going into the top left is so quick and smooth too ,,,, definately better than before ....

Still loading things in too

Inkscape - Ktoon - Xaos - Blender - Wings3d - Dia  ......

All there too ....easy as ....

---

### Post by cbowman57 on 2011-07-31
My opinion so far is that Debian benefits from the longer development cycles.  Even the experimental & unstable repos seem to rival the Ubuntu release versions.

---

### Post by 23dornot23d on 2011-07-31
I must admit this testing one is sound ..... 

I have disabled the experimental while I get things set as I like ....

Then I will try breaking it ..... :confused:

Just doing another safe-upgrade 256 Meg ..... see where this takes us .
hopefully better ..... ;) if I do not return you will know what has happened ...

---

### Post by cbowman57 on 2011-07-31
:lol: I'm still trying to simplify the installation process, though I'm getting an error about linuxmint InRelease expired something or another.

Not making much progress today, starting from scratch on a development installation.

---

### Post by 23dornot23d on 2011-07-31
[http://www.google.com/cse?cx=002683415331144861350%3Atsq8didf9x0&q=linuxmint+InRelease+expired+&ie=utf-8&sa=Search]("http://www.google.com/cse?cx=002683415331144861350%3Atsq8didf9x0&q=linuxmint+InRelease+expired+&ie=utf-8&sa=Search")

seems someone solved your problem using synaptic .... here ...

[http://forums.linuxmint.com/viewtopic.php?f=110&p=404552](http://forums.linuxmint.com/viewtopic.php?f=110&p=404552)

Ok similar here ...... got it all nicely setup .....

then unticked experimental ..... reloaded the repositories

did a safe upgrade .... and its taken the kernel to 3.0.0.1 

thing is it seems to have missed dkms also seems it does not see my USB drive
as I would like it to ..... we will see later .....

What does the Nvidia script file do you mentioned earlier .... 

what does Nvidia msi 
do Systems manager interface ...... looking for a easy way here to resolve it before I log off ...

as I have tried re-installing the headers and the nvidia driver files..... as we had the same problem in Oneiric 
new Kernel means re-install the Nvidia -drivers twice for some reason otherwise they do not pick up
or at least the module they use does not .....


nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-1-686-pae/updates/dkms//

depmod....

DKMS: install Completed.
Setting up nvidia-glx (275.21-1) ...
No diversion 'diversion of /usr/lib/xorg/modules/extensions/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx', none removed.
No diversion 'diversion of /usr/lib/xorg/modules/extensions/libGLcore.a to /usr/lib/nvidia/libGLcore.a.xlibmesa by nvidia-glx', none removed.
No diversion 'diversion of /usr/lib/xorg/modules/extensions/libglx.a to /usr/lib/nvidia/libglx.a.xlibmesa by nvidia-glx', none removed.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-1-686-pae
live-boot: core filesystems devices utils:memdisk udev wget blockdev.
ldconfig: /lib/libuuid.so.1 is not a symbolic link


I hope that is ok now ..... no second chances on my setup ..... one day I will get a brand new laptop ....
and all the fun will go away struggling like this lols .... ;)

it looks a little better now .... not sure what that symbolic link problem is though > ?

Oh well time to try a reboot ....

and its good [_***kernel 3.0.0.1 - 686-pae***_]("http://img827.imageshack.us/img827/9379/screenshot1fz.jpg")

[IMG]http://img641.imageshack.us/img641/6848/screenshot0801201104530.jpg[/IMG]

[IMG]http://img854.imageshack.us/img854/8011/screenshotmint3s.jpg[/IMG]

---

### Post by cbowman57 on 2011-07-31
I think there are some module support problems with the 3.0 kernel.  I'm running it right now, with errors, but it doesn't break anything on my system.

I got that error to go away, don't know how, it just cleared itself up, or maybe I got my time corrected, not certain.

You're just going to have to play with that smxi script, it does much more than install video drivers and there are pages & pages on the internet trying to explain it.  Much more involved than what would fit in this thread. :)

---

### Post by 23dornot23d on 2011-08-01
It is all running ok .....

I just need to get the latest gnome-shell now .... this one is still 3.0.2

tried adding the ricotz ppa to get 3.1.3 ...... idea was to get it and its dependencies

then untick the pps ..... and see if it would carry on ..... but the other packages
are too out of date and trying it this way just wants to drop it back to 2.32
if you try to fix the dependancies .....

Well its good at 3.0.2 ..... so will just have to wait until they get the repositories in
debian upto the latest ...... version of Gnome-shell

[[COLOR=Red]_***Screenshot***_[/COLOR]]("http://img155.imageshack.us/img155/7625/screenshot5qb.jpg")

do I or dont I
first a remastersys backup

Ok I have a backup .... so should be able to restore back to this point ....

the safe-upgrade wants to remove tdb-tools ...... which relate to samba
[http://www.google.com/cse?cx=002683415331144861350%3Atsq8didf9x0&q=tdb-tools&ie=utf-8&sa=Search]("http://www.google.com/cse?cx=002683415331144861350%3Atsq8didf9x0&q=tdb-tools&ie=utf-8&sa=Search")

O k got a few things to do ..... so will be back later on .....

The resume freature works pefectly too ....

Ok tried installing the [COLOR=Blue]_[**Clarity icons**]("http://gnome-look.org/content/show.php/Clarity?content=135654")_[/COLOR] ..... all went well no errors ...... but no icons yet .... maybe on reboot !!!

ok quick recap

last things to install 

kernel 3.0.0.1
conky - with transparency
icons

Things still to do .... sound was set up for my other computer and is now built into the kernel ...
so how do I change this now > ?

sudo aptitude install alsa-utils
alsamixer

what does it show me ....

[COLOR=Blue][B][Screenshot]("http://img269.imageshack.us/img269/4816/alsamixer.jpg")

ok switch the soundcard F6

[Screenshot]("http://img233.imageshack.us/img233/4027/screenshot4rr.jpg")

No sound but at least the card switched over and is recognised ...

[COLOR=Red]so now to alter the alsa settings ....

[COLOR=Black]there was a file and some instructions I made a long time ago for debian
when I was using E17 ,,, wonder if they will still work .....
have to find them first but the principal is probably the same ..... 

Was Elive 2009 ..... Well I never .... [LINK to sorting Elive sound problems on 7730ZG]("https://sites.google.com/site/keithaerospace92/elive")

so lets go through it again ..... see whats changed

so lets find as much information as we can before we syart doing anything yet ...

```

[COLOR=Blue]keith@debianmint[/COLOR] ~ $ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: LSI ID 1040
Codec: Nvidia MCP77/78 HDMI

[COLOR=Blue]keith@debianmint[/COLOR] ~ $ dmesg | grep Linux
[    0.000000] Linux version 3.0.0-1-686-pae (Debian 3.0.0-1) (ben@decadent.org.uk) (gcc version 4.5.3 (Debian 4.5.3-3) ) #1 SMP Sun Jul 24 14:27:32 UTC 2011
[    0.004395] SELinux:  Disabled at boot.
[    0.161583] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.584369] Linux agpgart interface v0.103
[    2.756616] usb usb1: Manufacturer: Linux 3.0.0-1-686-pae ehci_hcd
[    2.776395] usb usb2: Manufacturer: Linux 3.0.0-1-686-pae ehci_hcd
[    2.780626] usb usb3: Manufacturer: Linux 3.0.0-1-686-pae uhci_hcd
[    2.781825] usb usb4: Manufacturer: Linux 3.0.0-1-686-pae uhci_hcd
[    2.783034] usb usb5: Manufacturer: Linux 3.0.0-1-686-pae uhci_hcd
[    2.791123] usb usb6: Manufacturer: Linux 3.0.0-1-686-pae uhci_hcd
[    2.792319] usb usb7: Manufacturer: Linux 3.0.0-1-686-pae uhci_hcd
[    2.793466] usb usb8: Manufacturer: Linux 3.0.0-1-686-pae uhci_hcd
[   12.780702] Linux media interface: v0.10
[   12.813944] Linux video capture interface: v2.00
keith@debianmint ~ $ 

[COLOR=Blue]keith@debianmint[/COLOR] ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[COLOR=Blue]debianmint keith #[/COLOR] lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

[COLOR=Blue]debianmint keith #[/COLOR] cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0500000 irq 46

(this always bothers me ...... used to work so much better on irq 22 for some reason)


[COLOR=Blue]debianmint keith #[/COLOR] cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.

[COLOR=Blue]debianmint keith #[/COLOR] lsmod | grep snd
snd_hda_codec_hdmi     26009  1 
snd_hda_codec_realtek   206339  1 
snd_hda_intel          21691  2 
snd_hda_codec          58364  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              12936  1 snd_hda_codec
snd_pcm_oss            36377  0 
snd_mixer_oss          17713  1 snd_pcm_oss
snd_pcm                53315  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi           12744  0 
snd_rawmidi            22621  1 snd_seq_midi
snd_seq_midi_event     13124  1 snd_seq_midi
snd_seq                39539  2 snd_seq_midi,snd_seq_midi_event
snd_timer              22027  2 snd_pcm,snd_seq
snd_seq_device         12985  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    38562  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12992  1 snd
snd_page_alloc         12899  2 snd_hda_intel,snd_pcm


debianmint keith # grep ^Codec /proc/asound/card?/codec*
/proc/asound/card0/codec#0:Codec: Realtek ALC888
/proc/asound/card0/codec#1:Codec: LSI ID 1040
/proc/asound/card0/codec#3:Codec: Nvidia MCP77/78 HDMI



```ok thats the  reconnaissance done
and most things seem to the same again ..... yet no sound .... always did get me how to set sound up
even before when I posted on the forums everyone told me its working
you must have something muted .....

but it was just a .conf file that wanted altering ...... now what was it ? is in my notes ..... somewhere.

Other thing is compile it again ..... but its already at latest version ....

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

ok so do we download and compile .... as that solved it once before ?

or has everything moved to pulseaudio now .... 
( even so I prefer ALSA if I can get my surround souind working again as it used to ..... )
as since ubuntu all I have had is stereo ...... 

maybe debian and ALSA can get me the full thing back again



What was that .conf file ... ? search on soundcard problems and 23dornot23d ,,,,

got it ...... [COLOR=Blue][U][I][LINK]("http://ubuntuforums.org/showthread.php?t=1515200")

and the solution was to add one line to a file

[/I][/U][/COLOR][/COLOR][/COLOR][/B][/COLOR]gksudo gedit /etc/modprobe.d/alsa-base.conf

[B]options snd-hda-intel model=auto

__________________________________________________________

So I have now done this on debian will it work ?

YEP :) :) :)

another success .....

[COLOR=SeaGreen][_*SCREENSHOT*_]("http://img855.imageshack.us/img855/6086/screenshotsn.jpg")[/COLOR][/B][B]  plus the Clarity Themed icons too ,,,

No longer a RED line through the sound symbol on the right and my startupo sound is back

Time for some ice-cream now ..... caramel flavoured ..... another hot day here ..... no global warming

somebody just left there cooker on ......... ;)

[/B]

---

### Post by cecilpierce on 2011-08-01
You guys lost me :confused: I DL the wrong one I think "OEM" version 32bit 664megs and its a piece of crud so far.
I also DL the DVD and gona install it, I hope.
:P
be back soon I hope ! ! ! ! !

---

### Post by 23dornot23d on 2011-08-01
Ok yep its the Debian Dvd Xfce one From thread               #[**16**]("http://ubuntuforums.org/showpost.php?p=11103075&postcount=16")

We seem to be going fast again at creating another mega thread ....

> 
So will use **[COLOR=Red][xfce 32 bit ]("http://www.linuxmint.com/edition.php?id=79").[/COLOR]**....  ok its downloading now ...... 1.0 meg per second ... so it should not be long ....

Am downloading it now ...... will post again when its burnt and installed

I will catch up to you .... sometime tonight this is going to be a long session .....

and will try to install both on the USB drive ..... and gives me two chances of screwing up then lols :wink:

I am considering using bleachbit on this and seeing if its possible to make a torrent ....
but the only way I know how is to do a backup ...... ( but it might give someone a quick start )
If only I can remember what to do again .... the remastersys backup is ok

Its making the torrent again .... will have to download transmission and the likes - qbittorent
might be something to do for this afternoon .....

Ok going to use bleachbit and any other tools to tidy this up ..... computer janitor if there is one ....
then see if it will creat another working ISO .....

---

### Post by cecilpierce on 2011-08-01
Keith, does it matter, I think I DL the gnome one instead of xfce ???

---

### Post by cbowman57 on 2011-08-01
> **cecilpierce said:**
> Keith, does it matter, I think I DL the gnome one instead of xfce ???

Doesn't really matter, can be done with either but it was recommended on the LM forum.  I've used both.

@Keith; you've made some quick progress.  I did 3 (maybe 4) installs yesterday, all were successful, but I used some different approaches each time, still looking for a brain dead simple method.  Haven't found one yet.  Oh, better to stick with 3.0.2 & avoid adding ppa's, it can be done but it begs for trouble. :) 

Don't worry about incorporating all the bling, just open a terminal & ```
sudo remastersys dist

``` when you think it's stable. If you want to offer the extras I rather liked the way gNatty v3 was packaged. I'll keep tinkering with the 64-bit version.

Pretty sure you'll have to downgrade to gdm, use the failsafe menu entry and to install use the Remastersys installer.

---

### Post by 23dornot23d on 2011-08-01
Ok well just done a bakup cleaned with bleachbit ..... will put it safe ....


 Then .... will just try a Dist one .... and see how it goes ,,,

do you remove the xorg.conf ...... ( I might just mv to a xorg.conf2monitor one )

[COLOR=Red]**[COLOR=Black]mv xorg.conf xorg.twinscreen[/COLOR]**[/COLOR]

[COLOR=Red][B]ok reminder to myself ..... mv the xorg.conf back after doing this ,,,, 
otherwise you wont have a screen to look at anymore .....
and paste this back in after ....

[COLOR=Black]mv xorg.twinscreen [/COLOR][/B][/COLOR][COLOR=Red]**[COLOR=Black] xorg.conf[/COLOR]**[/COLOR][COLOR=Red][/COLOR]

---

### Post by cbowman57 on 2011-08-01
Anyone visiting this thread should also keep an eye on this [one]("http://forums.linuxmint.com/viewtopic.php?f=141&t=65745&sid=b3bf2ab542523b09669c8710ad7a5a19&p=455995#p455995") in the [COLOR=Lime]Linux Mint[/COLOR] forum.

The last install I did I tweaked apt preferences & the gnome pinning file, that's primarily how I'm trying to go about it.  I'd like to find a simple recipe that anyone can copy but so far it includes cherry picking quite a few files.

Another quick note, you don't have to dist-upgrade to sid if you don't want to.  You can keep it 'testing' and do the same process, there is more info available for simply addng gnome-shell to Debian on the web.

---

### Post by cbowman57 on 2011-08-01
> **23dornot23d said:**
> Ok well just done a bakup cleaned with bleachbit ..... will put it safe ....


 Then .... will just try a Dist one .... and see how it goes ,,,

do you remove the xorg.conf ...... ( I might just mv to a xorg.conf2monitor one )

You might also want to clean bash history for root, otherwise it will end up in the dist iso.  Didn't try removing xorg.conf, that might be a goog idea. With **remastersys** you can create a **distfs** first, explore the temporary file system, manipulate it some, then do a **distiso** to ceate the iso.

---

### Post by 23dornot23d on 2011-08-01
Cheers for the information on the bash already done the root clean .... and bash
thanks for the warning though ....

_____________________________________

Ok I see the problem with gdm

its because in /etc/

its folder has been renamed to gdm3

--------------------------------------------------------------------------------

```

debianmint X11 # remastersys dist
 
Distribution Mode Selected
Checking if the /home/remastersys/remastersys folder has been created
Copying /var and /etc to temp area and excluding extra files
/usr/bin/remastersys: line 230: /home/remastersys/remastersys/dummysys/etc/gdm/gdm.conf-custom: No such file or directory
find: `/home/remastersys/remastersys/dummysys/var/crash': No such file or directory
Setting up live options for dist mode
update-initramfs: Generating /boot/initrd.img-3.0.0-1-686-pae
live-boot: core filesystems devices utils:memdisk udev wget blockdev.
ldconfig: /lib/libuuid.so.1 is not a symbolic link

Copying your kernel and initrd for the livecd
Creating filesystem.squashfs   ... this will take a while so be patient
Adding stage 1 files/folders that the livecd requires.
Parallel mksquashfs: Using 2 processors
Creating 4.0 filesystem on /home/remastersys/remastersys/ISOTMP/live/filesystem.squashfs, block size 1048576.
[===========================================================|] 10852/10852 100%
Exportable Squashfs 4.0 filesystem, gzip compressed, data block size 1048576
    compressed data, compressed metadata, compressed fragments, compresse

```--------------------------------------------------------------------------------

So lets try to trick it ...... and copy the gdm3 to gdm ...... what harm can it to ,,,, :confused:

two to choose from  is better than none ..... at least it does not error now ....

Its run through with no errors ...... but just incase ,,,, lets check it in a virtual world 
first

Qemu ...... can I use this to test it rather than waisting a disk ,,,,,,, if so how ....
I have done this before but the iso was on CD ...... will search for a solution ....

)starting in my home directory ....... these are the commands I used to start a virtual
iso from the remastersys directory using the remastersys custon disk .....

Will kee it here for future reference ....

[COLOR=Blue][B]keith@debianmint ~ $ ls
alsa-utils-1.0.24.2  Desktop    Downloads  Pictures  scripts    Videos
Clarity              Documents  Music      Public    Templates
-----------------------------------------------------
[COLOR=Black]This line creates a place for it to work in make sure your disk is big enough ie has enough free space for it  8 Gig ..[/COLOR].

keith@debianmint ~ $[COLOR=Red] qemu-img create mintdebian-test 8G

[COLOR=Black]Formatting 'mintdebian-test', fmt=raw size=8589934592[/COLOR]
[/COLOR] 
keith@debianmint ~ $ [COLOR=Red]qemu -hda mintdebian-test -cdrom /home/remastersys/remastersys/customdist.iso -m 192 -boot d

[/COLOR][COLOR=Black]Running the image[/COLOR][/B][B][COLOR=Red]
[/COLOR] -----------------------------------------------------

[COLOR=Black]so this then gives this .... [COLOR=SeaGreen][U][I][SCREENSHOT.]("http://img841.imageshack.us/img841/4144/screenshot3fz.jpg")

ok well it runs .... and it sets the screen up and the mouse .... but stops at that ....
no gdm3 ..... sort of expected it ...... so another way !!!

[[COLOR=Black]This is  A SREENSHOT as it was booting for those interested ...[/COLOR]]("http://img199.imageshack.us/img199/3029/screenshot4lb.jpg")

and this was as far as it got .... 
( heatwave here today and that temp is the highest its been 75^ not good )

[[COLOR=Black]SCREENSHOT[/COLOR]]("http://img220.imageshack.us/img220/390/screenshot6bky.jpg")

after stopping .... the QEMU ... ( firefox was running too - might have been best killing that for the testing ..... as that was taking a chunk too at times ..... )
dropped back to 65 now ...


[COLOR=Black]OK what I can do now is try the others that I created as I know my backup works
just to check that QEMU is functioning fully .....

[IMG]http://img52.imageshack.us/img52/6650/screenshot11s.jpg[/IMG]

Works fine ....
One more go with the other Distro .... as this takes a while to load in a emulation mode

Ok my backup as I know works fine because I installed my new system from it ......

keith@debianmint ~ $ qemu -hda mintdebian-test -cdrom debmint/custombackup.iso -m 192 -boot d


The clean distribution on the other hand will not load gdm3 .... as it is not set up in 
Remastersys to cater for it ....... unless the newer version has it .... ?

[/COLOR][/I][/U][/COLOR][/COLOR][/B][COLOR=Black][COLOR=SeaGreen][COLOR=Black]Ok ....... so do I put out my version with my settings ....... like last time .....
Bulldog got it working last time ..... wonder if he is still around ..... to
test another one out ....... as he must have a similar setup to me .....

Ok just thoughts ..... wher next ...... gdms ...... is it just something in a script needs altering
how does remastersys work is it scripts ..... or C++ or something else ....

I can deal with scripts ..... or Python to some extent ...

Ok what next ...... ?

recap ....

[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Blue][COLOR=Black][COLOR=SeaGreen][COLOR=Black][COLOR=Red]fail [/COLOR]............ No Clean Distro .... with no settings in it .... 
[/COLOR][/COLOR][/COLOR][/COLOR]
[COLOR=Blue][COLOR=Black][COLOR=SeaGreen][COLOR=Black]success ..... Qemu works

success ..... My ISO backup works and it can be used to install from


so do we upload it ...... one more thing to do ..... as last time create other users
as we have choices again .....

Kde
Gnome-Shell
Gnome Fallback
[/COLOR][/COLOR][/COLOR][/COLOR]Xfce 
[COLOR=Blue][COLOR=Black][COLOR=SeaGreen][COLOR=Black] 
To ensure they all work do some tests first ......


[/COLOR][/COLOR][/COLOR][B][COLOR=Black][COLOR=SeaGreen][U][I][COLOR=Black]
[/COLOR] [/I][/U][/COLOR][/COLOR] [/B][/COLOR]

---

### Post by cbowman57 on 2011-08-01
I'll be watching your progress.  I just test by burning to a flash drive, haven't messed with emulators in years.  If you don't have any luck with gdm3 you can always downgrade, gdm 2 looks & acts nice.

I was in Germany in the mid-80's when they had a hotter than normal summer, it was a hot one so I know what you're going through. :)

---

### Post by 23dornot23d on 2011-08-01
Yep crazy temps here at moment ..... am almost cooked ..... ;)

I live in a attic and it catches all the sun too .... one small velux window ,,,,, :D

ok back to work ,,,,,,

This is getting interesting again ..... and I am sure there is a easy solution to the gdm3

maybe a dynamic link between two directories if its possible ,,,,

who knows ..... 

I just like working problems out ..... maybe if anybody that programs or knows about remastersys
is looking in on this .....

How do we get the system to either see gdm as gdm3

or make the system think that gdm3 is the correct one to use ....
as I think my idea of fooling it ...... by having /etc/gdm (a copy of this) dir  /etc/gdm3 
in the iso disk may have worked as long as the system still looks for gdm3 once its all installed ..

as it is there on the disk ..... too .....

___________________________________________

Its just gdm been renamed - directory in the /etc/ to gdm3

as far as I can tell ..... and its causing bother .... :confused:

I maybe need to investigate again .... on the remastersys forum ...... 

but scrabble time coming up ;).
one thing is flash and facebook work ok ,,,,, so what else really matters ,,,, !!!!


[Looked on the Mint forum]("http://img855.imageshack.us/img855/2925/screenshot20vg.jpg") ..... problem Gimp and Eclipse .... not a problem ...

[IMG]http://img51.imageshack.us/img51/300/screenshot20so.jpg[/IMG]

Need a way forward ...

as said .... don't use Experimental once its installed ..... aslso gdm3 is not the problem
Remastersys needs altering to cope with it ...... ( our problem for the time being )

So what alternatives are there ...... still produces a backup and it will install from that too
using remastersy install .... so I really see no problem ....

other than first it needs installing to work properly ..... and mine installed clean too

Set some default users ,,,,, the user then creates their own once its running ....
or changes the ones set as defaults .... ( just different - but its an option )

Will still aim for a proper one .... that works with gdm 2.32 maybe !!!

Need to keep going forward though as it will soon be old hat ,,,,

Just got the themes going again too .... [_***LINK***_]("http://img143.imageshack.us/img143/8112/screenshot22ee.jpg")

Need these though .... the older themes  debs ,,,, plus themeselector out of the gnatty pack ...

> 
**THEMES**

Found a fix for adding the theme selector in this thread ......
 Step 1
 Get these 2 debian files and install them using gdebi in a terminal ..... 

[Link1]("https://sites.google.com/site/000menu/home/gnome---3/gnome---shell/gnome-shell-files/gnome-shell-extensions-common_3.0.1-2_all.deb?attredirects=0")

[Link2]("https://sites.google.com/site/000menu/home/gnome---3/gnome---shell/gnome-shell-files/gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb?attredirects=0")
as you have to run as root and answer yes to the question ......
 C Bowman made the debs available here ......  from Fedora ....

[LINK 3]("https://sites.google.com/site/000menu/home/gnome---3/gnome---shell/gnome-shell-files/themeselector%40fpmurphy.com.tar.gz?attredirects=0&d=1") - themeselector for this version 3.0.2

to get this working extract this into the 
(home)/.local/share/gnome-shell/extensions(folder)

we also need to do two more things ........ themes are kept in

(home)/.themes
but at least one them needs to go into
(home)/.local/share/gnome-shell/themes(folder)

for it all to work properly ...... ( well thats what worked for me )


Dark Glass seems to suit Mint better ,,,, than the tron theme ....

[IMG]http://img231.imageshack.us/img231/8917/screenshot24sh.jpg[/IMG]


_________________________________

Try Number 002 ....... to get the gdm3 working ..... ( as it already works for a normal backup = done that one )

I have a feeling the gdm3 problem is ok the problem was the xorg.conf

it loops ..... trying to find the correct screen if no xorg.conf is there ,,,, I believe this is what happened

when I ran Qemu ...... will try again .......



remove the xorg.conf ...... and replace with single monitor one for other people with Nvidia ...

**cd /etc/X11/**

[COLOR=Red][B][COLOR=Black]mv xorg.conf xorg.twinscreen

mv xorg.confdesk xorg.conf
[/COLOR][/B][/COLOR] 
[COLOR=Red][B]ok reminder to myself ..... mv the xorg.conf back after doing this ,,,, 
otherwise you wont have a screen to look at anymore .....
and paste this back in after ....

[COLOR=Black]mv xorg.twinscreen [/COLOR][/B][/COLOR][COLOR=Red][B][COLOR=Black] xorg.conf

ok its already ....

so 
bleachbit root
bleachbit (user)

open a root terminal to copy gdm in there ,,, use thunar quick and simple

cd /home/remastersys
remastersys clean
remastersys dist
copy gdm in as remastersys creates the copy etc directory

Then use the emulator to see if it works ok ,,,, 

[/COLOR][/B][/COLOR][COLOR=Blue][B]keith@debianmint ~ $[COLOR=Red] qemu-img create mintdebian-test 8G
[/COLOR][/B][/COLOR][COLOR=Blue]**keith@debianmint ~ $ [COLOR=Red]qemu -hda mintdebian-test -cdrom /home/remastersys/remastersys/customdist.iso -m 192 -boot d[/COLOR]**[/COLOR]
[COLOR=Red][B][COLOR=Black] 
I made it bigger and increased the size to 8 gig ..... for the emulator ,,,, as it was a 2 Gig distro ....
just hope it was enough ..... it should be as the other ran quite happy - from my backup  in 6 Gig
and that was a 1.7 gig backup iso ,,,,,,

So I can only thin its not an xorg problem ,,,,, as my backup worked ok .... and the only real difference
being ..... that was gdm ........ this new one igdm3 .......

So options ..... ? mine will hopefully keep stable now as I am not using experimental or any other repository
that could harm it ....

I can drop it back to gdm ..... with aptitude ..... ( risk in downgrade here ,,,, may break it ,,, )


 or ..... change the 
window manager to kdm ( kdm is quite big but remastersys does cater for it )

or another smaller lighter one ..... !!!

Will carry on with it just as a backup ... and clean it out ..... with  one 

___________________________________________________________________

extra user .... debianmint     ...... password ..... debianmint

[/COLOR][/B][/COLOR][COLOR=Red][B][COLOR=Black]done that ..... 

So now create a backup distro ..... using that user .... or mine .....
while in testing mine .... * but have given the debianmint administrator priveliges 
[/COLOR][/B][/COLOR]

---

### Post by cbowman57 on 2011-08-01
Ok, I think I've got it somewhat figured out.


[LIST=1]
[*]Install LMDE (Xfce version recommended)
[*]Run mintupdate, it will update itself & restart.  Run it again, install everything it suggests.
[*]Purge evince* [**sudo apt-get purge evince***] You can install it after you are finished (It provides support for reading pdf files).
[*]Shutdown/Restart
[*]**gksu thunar** & navigate to **/etc/apt**, rename your sources.list just to be prudent, then create a new **sources.list** that contains this data: ```
deb http://mirror.csclub.uwaterloo.ca/linuxmint-packages/ debian main upstream import backport romeo
deb http://debian.linuxmint.com/incoming testing main contrib non-free
# deb http://debian.linuxmint.com/latest testing main contrib non-free
deb http://security.debian.org/ testing/updates main contrib non-free
deb http://www.debian-multimedia.org testing main non-free
deb http://ftp.us.debian.org/debian stable main contrib non-free
deb http://ftp.us.debian.org/debian testing main contrib non-free
deb http://ftp.us.debian.org/debian unstable main contrib non-free
deb http://ftp.us.debian.org/debian experimental main contrib non-free

## Liquorix sources added by smxi ##
# deb http://liquorix.net/debian/ sid main
```
[*]Now navigate to **/etc/apt/apt.conf.d **create a file called **local**, insert this data into it: ```
APT::Default-Release "sid";
APT::Install-Recommends; 
```
[*]Go to **/etc/apt/preferences.d** create a file called **gnome**, insert this data into it & save it. ```
Package: *gnome* libglib2.0* *vte* *pulse* *peas* libgtk* *gjs* *gconf* *gstreamer* alacarte *brasero* cheese ekiga empathy* gdm3 gcalctool baobab *gucharmap* gvfs* hamster-applet *nautilus* seahorse* sound-juicer *totem* remmina vino gksu xdg-user-dirs-gtk dmz-cursor-theme eog epiphany* evince* *evolution* file-roller gedit* metacity *mutter* yelp* rhythmbox* banshee* system-config-printer transmission-* tomboy network-manager* libnm-* update-notifier shotwell liferea *software-properties* libunique-3.0-0 libseed-gtk3-0 libnotify* libpanel-applet-4-0 libgdata11 libcamel* libcanberra* libchamplain* libebackend* libebook* libecal* libedata* libegroupwise* libevent* gir1.2-* libxklavier16 python-gmenu libgdict-1.0-6 libgdu-gtk0 gnome-shell gconf2 gir1.2-gconf-2.0 gir1.2-gkbd-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomekbd-3.0 gir1.2-mutter-2.91 gir1.2-networkmanager-1.0 gjs gnome-bluetooth gnome-control-center gnome-icon-theme-symbolic gnome-settings-daemon libcanberra0 libdbus-1-3 libebook1.2-10 libecal1.2-8 libedataserver1.2-14 libedataserverui-3.0-0 libgconf2-4 libgjs0b libgl1-mesa-glx libgl1 libglib2.0-0 libgnome-desktop-3-0 libgnome-menu2 libmutter0 libpulse-mainloop-glib0 libpulse0 mutter python zlib1g gnome-control-center xserver-xephyr gnome-3.0 gir1.2-atk-1.0 gir1.2-clutter-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gsettings-desktop-schemas libatk1.0-0 libc0.1 libc6 libcairo-gobject2 libcairo2 libcamel1.2-19 libclutter-1.0-0 libcroco3 libdbus-glib-1-2 libdconf0 libdrm2 libffi5 libfontconfig1 libfreetype6 libgcc1 libgdk-pixbuf2.0-0 libgirepository-1.0-1 libgstreamer0.10-0 libgtk-3-0 libgtk2.0-0 libical0 libjson-glib-1.0-0 libmozjs2d libmozjs5d libnspr4-0d libnss3-1d libpango1.0-0 libpolkit-agent-1-0 libpolkit-gobject-1-0 libsoup2.4-1 libsqlite3-0 libstartup-notification0 libtelepathy-glib0 libtelepathy-logger2 libx11-6 libxcomposite1 libxdamage1 libxext6 libxfixes3 libxi6 libxml2 mesa-utils pkg-config libgnutls26
Pin: release experimental
Pin-Priority: 990

Package: *gnome* libglib2.0* *vte* *pulse* *peas* libgtk* *gjs* *gconf* *gstreamer* alacarte *brasero* cheese ekiga empathy* gdm3 gcalctool baobab *gucharmap* gvfs* hamster-applet *nautilus* seahorse* sound-juicer *totem* remmina vino gksu xdg-user-dirs-gtk dmz-cursor-theme eog epiphany* evince* *evolution* file-roller gedit* metacity *mutter* yelp* rhythmbox* banshee* system-config-printer transmission-* tomboy network-manager* libnm-* update-notifier shotwell liferea *software-properties* libunique-3.0-0 libseed-gtk3-0 libnotify* libpanel-applet-4-0 libgdata11 libcamel* libcanberra* libchamplain* libebackend* libebook* libecal* libedata* libegroupwise* libevent* gir1.2-* libxklavier16 python-gmenu libgdict-1.0-6 libgdu-gtk0 gnome-shell gconf2 gir1.2-gconf-2.0 gir1.2-gkbd-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomekbd-3.0 gir1.2-mutter-2.91 gir1.2-networkmanager-1.0 gjs gnome-bluetooth gnome-control-center gnome-icon-theme-symbolic libcanberra0 libdbus-1-3 libebook1.2-10 libecal1.2-8 libedataserver1.2-14 libedataserverui-3.0-0 libgconf2-4 libgjs0b libgl1-mesa-glx libgl1 libglib2.0-0 libgnome-desktop-3-0 libgnome-menu2 libmutter0 libpulse-mainloop-glib0 libpulse0 mutter python zlib1g gnome-control-center xserver-xephyr gnome-3.0 gir1.2-atk-1.0 gir1.2-clutter-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gsettings-desktop-schemas libatk1.0-0 libc0.1 libc6 libcairo-gobject2 libcairo2 libcamel1.2-19 libclutter-1.0-0 libcroco3 libdbus-glib-1-2 libdconf0 libdrm2 libffi5 libfontconfig1 libfreetype6 libgcc1 libgdk-pixbuf2.0-0 libgirepository-1.0-1 libgstreamer0.10-0 libgtk-3-0 libgtk2.0-0 libical0 libjson-glib-1.0-0 libmozjs2d libmozjs5d libnspr4-0d libnss3-1d libpango1.0-0 libpolkit-agent-1-0 libpolkit-gobject-1-0 libsoup2.4-1 libsqlite3-0 libstartup-notification0 libtelepathy-glib0 libtelepathy-logger2 libx11-6 libxcomposite1 libxdamage1 libxext6 libxfixes3 libxi6 libxml2 mesa-utils pkg-config
Pin: release unstable
Pin-Priority: 950

# gnome-settings-daemon

Package: *
Pin: release experimental
Pin-Priority: 150 
```
[*]Open terminal & **sudo apt-get update**.
[*]Purge gstreamer0.10-plugins-bad [**sudo apt-get purge gstreamer0.10-plugins-bad**], it also removes other files but you can reinstall when done.
[*]Do a dist-upgrade, **sudo apt-get dist-upgrade**.  It will add, remove & upgrade quite a few files.
[*]Shutdown/Restart
[*]**sudo apt-get update** & **sudo apt-get upgrade**
[*]Run update manager & update suggested files.
[*]Install gnome-shell [**sudo apt-get install gnome-shell**] Hopefully all dependencies are met, if not you might have to do some research.
[*][LEFT]Install gnome-tweak-tool [**sudo apt-get install gnome-tweak-tool**].[/LEFT]
[*]Install gnome-themes-standard [**sudo apt-get install gnome-themes-standard**].
[/LIST]
That should get you an installation of Gnome 3.0 shell & fallback installed on Linux Mint Debian Edition upgraded to Sid, otherwise known as Mogwai. :)

Installing user theme & extension support will be another post, but the simple way is to add the natty .debs from launchpad, make sure you install the ones for gnome-shell 3.0.2.

You will likely only have gnome-session-fallback when you log on from the gdm (don't forget to select your DE).  You can install your video drivers via synaptic or use the smxi script (link in post #1).

I'm sure there are some errors, and shortcuts I didn't try, but overall I think this is a good start.

---

### Post by cbowman57 on 2011-08-01
@Keith; you might want to see if SLIM is supported by Remastersys, it's small & doesn't carry much in the way of dependencies.  Might even install side-by-side with gdm3, in which case it would just be a simple matter of dpkg --reconfigure gdm3 (or whatever the comand was).

---

### Post by 23dornot23d on 2011-08-01
Nice that looks pretty thorough - 

I just got the custom Iso made -tested and working too ,,,,,  [URL="http://img804.imageshack.us/img804/8123/screenshotuo.jpg"][COLOR=Blue][U][I]**Fullsize screenshot  :D**
[/I][/U][/COLOR][/URL]
[IMG]http://img546.imageshack.us/img546/4581/screenshotsy.jpg[/IMG]


Its just a case of putting it on a torrent now ...... 

I think we have done ok with this little challenge ... was good fun ....

> 
@Keith; you might want to see if SLIM is supported by Remastersys, it's  small & doesn't carry much in the way of dependencies.  Might even  install side-by-side with gdm3, in which case it would just be a simple  matter of dpkg --reconfigure gdm3 (or whatever the comand was).


Will have a look and see what it does ...... ( just worried about breaking this now ...... my booting of this is superb )
and the suspend and everything works ....... might use the ISO to transfer it back onto my desktop test machine.

Then I will have a proper backup to work on that does not really matter if it gets broke ......

Ok been a good few days ...... 3 solid .... and completed in 7 pages .... well almost ... 

Tasks still need doing ...... 

1 ..... Conky needs some more work on it ..... as its not displaying as it should yet
2 ..... A new Desktop manager SLIM ... or An other ...
3 ..... A proper Distro .... to give a clean install .... 32 bit and 64 bit .....

Then we are done I guess ..... till something else comes along .....

---

### Post by cbowman57 on 2011-08-01
Man, could you just imagine what could be done IF Debian wanted to put out a distro like this? :)

So Keith, did you end up using kdm?

---

### Post by 23dornot23d on 2011-08-01
No its just a clean backup ..... with everything included ...... 



I have used this method before to transfer distros machine to machine ...... and it works .....

anybody using it would set up a new user .... and keep debianmint as administrator

Will be trying it on my desktop once I have transferred it ...... 

Then will test  >>> to use slim or kdm . ;)

---

### Post by cbowman57 on 2011-08-01
> **23dornot23d said:**
> No its just a clean backup ..... with everything included ...... 



I have used this method before to transfer distros machine to machine ...... and it works .....

anybody using it would set up a new user .... and keep debianmint as administrator

Will be trying it on my desktop once I have transferred it ...... 

Then will test  >>> to use slim or kdm . ;)

Ok, I thought it was a working dist iso made with Remastersys.  It is a backup made that way though?

This what I've got on this development installation, no plans to install video drivers in case I decide to create a distro from it, I think that just muddies the water.

[ATTACH]199053[/ATTACH]

---

### Post by 23dornot23d on 2011-08-01
Yep mines a remastersys backup ....... 

Looks like we have two version now ...... 32 bit and 64 bit ...... looking good .....

I like your thinking ... about setting it up so the graphics is not so much of a problem.

Everything is time phased with this type of work ...... a few days out and the repos can change
and lead to problems .....

I need to sort this out on my desktop machine as I cannot risk my production machine going AWOL

So ,,, what to do ..... its for another day now ...... its 5:15 am here ,,,, and I am about bushed ....

Ok been good though and that 64 bit looks ever so good ...... cannot wait to try it out. ;)

think I am going to call it a night now ..... or early morning lols .... breakfast time already 

ok you have fun and will catch you sometime tomorrow ........ night for now .....

---

### Post by cbowman57 on 2011-08-01
Yeah, get some rest.

Well I think it's pretty well established that video drivers in Debian can be difficult but I think this project might lend itself to people either familiar with using Debian or willing to give it a spin.

I've installed the basic support for user themes & extensions so far but of course haven't been able to test them since I can't load the shell. :)

Hope you saved your deb cache, when you get time I'd like it if you could test the recipe on a 32-bit installation.

If anybody else is reading this thread I would appreciate feedback on whether or not the recipe works for you.  Particularly if you found a simpler way to do it, or have a better knowledge of working with pinning files, or even the skills & ambition to make this one a real distro.

:guitar:

---

### Post by cbowman57 on 2011-08-02
[LEFT]Ok, got a working 64-bit dist iso.
[/LEFT]
 
[B]Bugs:

[/B]
[LIST=1]
[*]Had to install using Remastersys installer.
[*]Had to reinstall mintupdate-debian.
[*]Installer didn't install grub to mbr.  I booted from another installation and did an update-grub which found it so I could boot into it.  Then booted from Rescatux to install the grub to mbr, that took care of it.
[/LIST]
**Good stuff:**


[LIST=1]
[*]Booted straight to the Gnome fallback desktop.
[*]Runs well, just like a standard installation of LMDE Sid with G-S on it. :)
[*]Even with the installation & grub bugs it was hours quicker to install than building it from a bare LMDE installation.
[/LIST]
I think we'd really have something here if we could get somebody with real skills involved.

---

### Post by 23dornot23d on 2011-08-02
[B]Bugs: ( not really bugs - minor inconvenniances )

[/B]Had to install using Remastersys installer.

**( not a bug just a new way to do something - it works )**

Had to reinstall mintupdate-debian.
[B]
( not sure what you mean ,,,, I aslways try safe-upgrade first )

[/B]Installer didn't install grub to mbr.  I booted from another  installation and did an update-grub which found it so I could boot into  it.  Then booted from Rescatux to install the grub to mbr, that took  care of it.

**( I choose to always insall to a partition for working on things like this .... safest way usually .... but MBR is good if one OS )**


I think we'd really have something here if we could get somebody with real skills involved.           


Well the only thing thats stopped the full creation of this ..... is the [COLOR=Red]_*** /etc/gdm3***_[/COLOR] directory changing.

1 ..... get Debian Developers to change it back .....

2 .... get Remastersys to work using this .... picking up gdm3 directory for Debian instead of gdm ...... don't forget its not a released OS we are sorking on .......

So I doubt they even realise yet that Remastersys will not work on it .....


Not sure what you mean here ...... ours aren't real skills ....... :confused:

well we haven't done so bad for part time employees ...... and all for free ,,,,

---

### Post by cbowman57 on 2011-08-02
> **23dornot23d said:**
> [B]Bugs: ( not really bugs - minor inconvenniances )

[/B]Had to install using Remastersys installer.

**( not a bug just a new way to do something - it works )**

True, works, just not pretty.
> 

Had to reinstall mintupdate-debian.
[B]
( not sure what you mean ,,,, I aslways try safe-upgrade first )[/B]Somewhere in the installation process, or iso creation, the update manager breaks. (the little shield icon)
> Installer didn't install grub to mbr.  I booted from another  installation and did an update-grub which found it so I could boot into  it.  Then booted from Rescatux to install the grub to mbr, that took  care of it.

**( I choose to always insall to a partition for working on things )**
I do that sometimes too, but most people would expect it to be installed to mbr if they select mbr. :)  I was able to retrieve it because I had other working partitions, if I hadn't the only choice would have been Rescatux or some other method of installing grub to mbr.

> 
Well the only thing thats stopped the full creation of this ..... is gdm3 directory changing.

1 ..... get Debian Developers to change it back .....

2 .... get Remastersys to work using this .... picking up gdm3 directory for Debian instead of gdm ...... don't forget its not a released OS we are sorking on .......

So I doubt they even realise yet that Remastersys will not work on it .....Forgot to mention, it was using gdm3, booted straight to the desktop from the iso. I kind of liked that.  The developer of Remastersys does realize that LMDE uses a different installer, if it could use the Debian installer it would be fine.


> Not sure what you mean here ...... ours aren't real skills ....... :confused:

well we haven't done so bad for part time employees ...... and all for free ,,,,I think we've done quite well actually, but somebody that knows about distro creation could really polish it up.

You're right, how many other employees will work 20 hour days for nothing? :lol:

---

### Post by 23dornot23d on 2011-08-02
> 
I do that sometimes too, but most people would expect it to be installed to mbr if they select mbr. :smile:   I was able to retrieve it because I had other working partitions, if I  hadn't the only choice would have been Rescatux or some other method of  installing grub to mbr.
I just use the last system I loaded up that I allowed to alter the MBR ..... and do a 

update-grub ..... 

Then adds the latest install into my main menu ....... 

* Confusers
 ( otherwise know as a computer that makes you think harder - than what it does )

[COLOR=Red]*[**Running Debian - Mint - inside of Fedora**]("http://img232.imageshack.us/img232/6466/screenshot4tn.jpg")*[/COLOR] 15 Gnome Shell

---

### Post by 23dornot23d on 2011-08-02
> **cbowman57 said:**
> Ok, I think I've got it somewhat figured out.


[LIST=1]
[*]Install LMDE (Xfce version recommended)
[*]Run mintupdate, it will update itself & restart.  Run it again, install everything it suggests.
[*]Purge evince* [**sudo apt-get purge evince***] You can install it after you are finished (It provides support for reading pdf files).
[*]Shutdown/Restart
[*]**gksu thunar** & navigate to **/etc/apt**, rename your sources.list just to be prudent, then create a new **sources.list** that contains this data: ```
deb http://mirror.csclub.uwaterloo.ca/linuxmint-packages/ debian main upstream import backport romeo
deb http://debian.linuxmint.com/incoming testing main contrib non-free
# deb http://debian.linuxmint.com/latest testing main contrib non-free
deb http://security.debian.org/ testing/updates main contrib non-free
deb http://www.debian-multimedia.org testing main non-free
deb http://ftp.us.debian.org/debian stable main contrib non-free
deb http://ftp.us.debian.org/debian testing main contrib non-free
deb http://ftp.us.debian.org/debian unstable main contrib non-free
deb http://ftp.us.debian.org/debian experimental main contrib non-free

## Liquorix sources added by smxi ##
# deb http://liquorix.net/debian/ sid main
```
[*]Now navigate to **/etc/apt/apt.conf.d **create a file called **local**, insert this data into it: ```
APT::Default-Release "sid";
APT::Install-Recommends; 
```
[*]Go to **/etc/apt/preferences.d** create a file called **gnome**, insert this data into it & save it. ```
Package: *gnome* libglib2.0* *vte* *pulse* *peas* libgtk* *gjs* *gconf* *gstreamer* alacarte *brasero* cheese ekiga empathy* gdm3 gcalctool baobab *gucharmap* gvfs* hamster-applet *nautilus* seahorse* sound-juicer *totem* remmina vino gksu xdg-user-dirs-gtk dmz-cursor-theme eog epiphany* evince* *evolution* file-roller gedit* metacity *mutter* yelp* rhythmbox* banshee* system-config-printer transmission-* tomboy network-manager* libnm-* update-notifier shotwell liferea *software-properties* libunique-3.0-0 libseed-gtk3-0 libnotify* libpanel-applet-4-0 libgdata11 libcamel* libcanberra* libchamplain* libebackend* libebook* libecal* libedata* libegroupwise* libevent* gir1.2-* libxklavier16 python-gmenu libgdict-1.0-6 libgdu-gtk0 gnome-shell gconf2 gir1.2-gconf-2.0 gir1.2-gkbd-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomekbd-3.0 gir1.2-mutter-2.91 gir1.2-networkmanager-1.0 gjs gnome-bluetooth gnome-control-center gnome-icon-theme-symbolic gnome-settings-daemon libcanberra0 libdbus-1-3 libebook1.2-10 libecal1.2-8 libedataserver1.2-14 libedataserverui-3.0-0 libgconf2-4 libgjs0b libgl1-mesa-glx libgl1 libglib2.0-0 libgnome-desktop-3-0 libgnome-menu2 libmutter0 libpulse-mainloop-glib0 libpulse0 mutter python zlib1g gnome-control-center xserver-xephyr gnome-3.0 gir1.2-atk-1.0 gir1.2-clutter-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gsettings-desktop-schemas libatk1.0-0 libc0.1 libc6 libcairo-gobject2 libcairo2 libcamel1.2-19 libclutter-1.0-0 libcroco3 libdbus-glib-1-2 libdconf0 libdrm2 libffi5 libfontconfig1 libfreetype6 libgcc1 libgdk-pixbuf2.0-0 libgirepository-1.0-1 libgstreamer0.10-0 libgtk-3-0 libgtk2.0-0 libical0 libjson-glib-1.0-0 libmozjs2d libmozjs5d libnspr4-0d libnss3-1d libpango1.0-0 libpolkit-agent-1-0 libpolkit-gobject-1-0 libsoup2.4-1 libsqlite3-0 libstartup-notification0 libtelepathy-glib0 libtelepathy-logger2 libx11-6 libxcomposite1 libxdamage1 libxext6 libxfixes3 libxi6 libxml2 mesa-utils pkg-config libgnutls26
Pin: release experimental
Pin-Priority: 990

Package: *gnome* libglib2.0* *vte* *pulse* *peas* libgtk* *gjs* *gconf* *gstreamer* alacarte *brasero* cheese ekiga empathy* gdm3 gcalctool baobab *gucharmap* gvfs* hamster-applet *nautilus* seahorse* sound-juicer *totem* remmina vino gksu xdg-user-dirs-gtk dmz-cursor-theme eog epiphany* evince* *evolution* file-roller gedit* metacity *mutter* yelp* rhythmbox* banshee* system-config-printer transmission-* tomboy network-manager* libnm-* update-notifier shotwell liferea *software-properties* libunique-3.0-0 libseed-gtk3-0 libnotify* libpanel-applet-4-0 libgdata11 libcamel* libcanberra* libchamplain* libebackend* libebook* libecal* libedata* libegroupwise* libevent* gir1.2-* libxklavier16 python-gmenu libgdict-1.0-6 libgdu-gtk0 gnome-shell gconf2 gir1.2-gconf-2.0 gir1.2-gkbd-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomekbd-3.0 gir1.2-mutter-2.91 gir1.2-networkmanager-1.0 gjs gnome-bluetooth gnome-control-center gnome-icon-theme-symbolic libcanberra0 libdbus-1-3 libebook1.2-10 libecal1.2-8 libedataserver1.2-14 libedataserverui-3.0-0 libgconf2-4 libgjs0b libgl1-mesa-glx libgl1 libglib2.0-0 libgnome-desktop-3-0 libgnome-menu2 libmutter0 libpulse-mainloop-glib0 libpulse0 mutter python zlib1g gnome-control-center xserver-xephyr gnome-3.0 gir1.2-atk-1.0 gir1.2-clutter-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gsettings-desktop-schemas libatk1.0-0 libc0.1 libc6 libcairo-gobject2 libcairo2 libcamel1.2-19 libclutter-1.0-0 libcroco3 libdbus-glib-1-2 libdconf0 libdrm2 libffi5 libfontconfig1 libfreetype6 libgcc1 libgdk-pixbuf2.0-0 libgirepository-1.0-1 libgstreamer0.10-0 libgtk-3-0 libgtk2.0-0 libical0 libjson-glib-1.0-0 libmozjs2d libmozjs5d libnspr4-0d libnss3-1d libpango1.0-0 libpolkit-agent-1-0 libpolkit-gobject-1-0 libsoup2.4-1 libsqlite3-0 libstartup-notification0 libtelepathy-glib0 libtelepathy-logger2 libx11-6 libxcomposite1 libxdamage1 libxext6 libxfixes3 libxi6 libxml2 mesa-utils pkg-config
Pin: release unstable
Pin-Priority: 950

# gnome-settings-daemon

Package: *
Pin: release experimental
Pin-Priority: 150 
```
[*]Open terminal & **sudo apt-get update**.
[*]Purge gstreamer0.10-plugins-bad [**sudo apt-get purge gstreamer0.10-plugins-bad**], it also removes other files but you can reinstall when done.
[*]Do a dist-upgrade, **sudo apt-get dist-upgrade**.  It will add, remove & upgrade quite a few files.
[*]Shutdown/Restart
[*]**sudo apt-get update** & **sudo apt-get upgrade**
[*]Run update manager & update suggested files.
[*]Install gnome-shell [**sudo apt-get install gnome-shell**] Hopefully all dependencies are met, if not you might have to do some research.
[*][LEFT]Install gnome-tweak-tool [**sudo apt-get install gnome-tweak-tool**].[/LEFT]
[*]Install gnome-themes-standard [**sudo apt-get install gnome-themes-standard**].
[/LIST]
That should get you an installation of Gnome 3.0 shell & fallback installed on Linux Mint Debian Edition upgraded to Sid, otherwise known as Mogwai. :)

Installing user theme & extension support will be another post, but the simple way is to add the natty .debs from launchpad, make sure you install the ones for gnome-shell 3.0.2.

You will likely only have gnome-session-fallback when you log on from the gdm (don't forget to select your DE).  You can install your video drivers via synaptic or use the smxi script (link in post #1).

I'm sure there are some errors, and shortcuts I didn't try, but overall I think this is a good start.


Ok going through this again  ..... step by step ..the way I did it ......will take a while
just so there are two options - if one fails try the other ,,,,,,,,

.

[LIST=1]
[*]Install LMDE (Xfce version recommended)
[*]aptitude dist-upgrade  (do not choose the first thing it gives you .....wait till libtar ..is the only thing it cannot resolve....)
[/LIST]
I am upto here again .......... with a 43 minute wait while it does this ...... same as last time ......same
flashing screen too ..... 10 seconds on one second off

will then have a look at evince and mintupdate ...... to see if there are any problems

      3.   add the repositories and reload using synaptic ......
      4.   choose gnome-shell - install ......
5. in synaptic .... untick the experimental repos ......

( if you have a  (ATI card however) ..Nvidia the nvidia-xconfig plus the drivers and kernel headers and kernel image needs setting up before reboot )

---

### Post by cbowman57 on 2011-08-02
aptitude dist-upgrade (might give much different results than apt-get, not sure)

If you saved your old cache it should go pretty fast, well as fast as your computer can go. :)

---

### Post by 23dornot23d on 2011-08-02
Nope no old saved cache ...... just wanted to see if I could get another one going .. from scratch .....

I like having fall back systems ...... 

I usually create 3 if I think they are any good  ...... 
( gives me 3 chances sometimes more if I can recover from any problems that I encounter )
always good to find the pitfalls - then not repeat them a second time .....


The last one I do will be the 64 bit one ........... but that has to go on my main machine .....
and I do not like risking anything on that ,,,,, ( as I said before it does not show me a grub or it booting
even though I have a monitor on VGA and the TV on DVI ....... it still does not display the grub or boot
sequence .......

The computer is slow and fragile ..... but it gets there .....

I was looking today for a new computer ........ but I wondered if it would make me less careful with how I approach things ....... 
so its still in the shop ..... would love one with better graphics .....

But would stick with Nvidia ..... what is it the [COLOR=Blue]_***[Nvidia  GTX 580]("http://www.google.com/search?client=ubuntu&channel=fs&q=Nvidia++GTX+580&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=c44&channel=fs&source=hp&q=Nvidia++GTX+580+laptop&pbx=1&oq=Nvidia++GTX+580+laptop&aq=f&aqi=g1g-b1&aql=&gs_sm=e&gs_upl=13251l15417l0l15807l7l6l0l0l0l0l315l1194l0.4.1.1l6l0&bav=on.2,or.r_gc.r_pw.&fp=92a46c51efbcab27&biw=1157&bih=534")***_[/COLOR]M ..... fastest on a laptop
would love that ....

Not sure they are ready for it yet with drivers though on Linux .....

Although I may be wrong ...... [[COLOR=Blue]**Thread on drivers for Nvidia GTX 580**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1620020")


[http://www.engadget.com/2011/06/28/nvidia-announces-geforce-gtx-580m-and-570m-availability-in-the/](http://www.engadget.com/2011/06/28/nvidia-announces-geforce-gtx-580m-and-570m-availability-in-the/)
_____________________________________________________________________

ok so the steps so far ..... to get here .....

Ok going through this again  ..... step by step ..the way I did it ......will take a while
just so there are two options - if one fails try the other ,,,,,,,,

.

[LIST=1]
[*]Install LMDE (Xfce version recommended)
[*]aptitude dist-upgrade  (do not choose the first thing it gives you  .....wait till libtar ..is the only thing it cannot resolve....)
[/LIST]
I am upto here again .......... with a 43 minute wait while it does this ...... same as last time ......same
flashing screen too ..... 10 seconds on one second off

Ok its upgraded and I have rebooted ....... 

[IMG]http://img708.imageshack.us/img708/7443/screenshotmintdebianloa.jpg[/IMG]


will then have a look at evince and mintupdate ...... to see if there are any problems

Evince looks ok ..... no dependency problems ...

[COLOR=Red]But mintupdate ..... does have dependency problems ....... ( !!!!! ) .

[COLOR=Black]But its not a problem ...... as the Mintupdate-debian is surely the one we need    !!!!! which is installed already and working[/COLOR]
[/COLOR] 
[IMG]http://img696.imageshack.us/img696/5595/mintupdate.jpg[/IMG]
 
       as the question it is asking - is do I want to remove mintupdate-debian to replace it with mintupdate ...... ( not sure I do ? )

Does it run ok

[IMG]http://img834.imageshack.us/img834/3559/mintupdaterunning.jpg[/IMG]

[COLOR=Blue]so moving along ..... ( before I do anything else ...... I will download remastersys ..... and save a iso here .... ) saves me 40 mins
if I ever need to do this again ......
[/COLOR]
3.   add the repositories and reload using synaptic ......
       4.   choose gnome-shell - install ......
 5. in synaptic .... untick the experimental repos ......
 
 ( if you have a  (ATI card however) ..Nvidia the nvidia-xconfig plus the  drivers and kernel headers and kernel image needs setting up before  reboot )

---

### Post by cbowman57 on 2011-08-02
You can't follow instructions any better than I can. :lol:

---

### Post by 23dornot23d on 2011-08-02
Lols ..... I play it by ear ..... :D

never failed me yet ..... lols .... :confused:  so a small diversion in the road here ........

__________________________________________________

I am wondering whether or not to use a [different remastersys]("http://sourceforge.net/projects/remastersys/files/remastersys-debian-squeeze/")

I used   [remastersys_2.0.20-1_all.deb]("http://sourceforge.net/projects/remastersys/files/remastersys-debian-squeeze/remastersys_2.0.20-1_all.deb/download")  .... last time ..... there is a 21-1 and a 22-1 there 
> 
its the gdm3 it looks for /etc/gdm
and the only directory created by gdm3 is /etc/gdm3
and I know you managed to find a later one .....

I will jump to the 22-1 I think ....... and see if it works any better .......

So this time using ..... this ..... [remastersys_2.0.22-1_all.deb]("http://sourceforge.net/projects/remastersys/files/remastersys-debian-squeeze/remastersys_2.0.22-1_all.deb/download")

so if it fails to create a use able backup .... we will know 20-1 is better ...........

[COLOR=Red][U][I][B]TRIED BOTH of these versions here and they FAIL  ..... they are trying to overwrite something ..... 

will give a screenshot ...... ( so this is not the time to install remastersys  .......

[IMG]http://img534.imageshack.us/img534/7306/error1rematersys.jpg[/IMG]
[/B][/I][/U][/COLOR]

---

### Post by cbowman57 on 2011-08-02
I haven't really experimented with the different versions of Remastersys, an earlier one might actually be better.

I know you can get G-S running on most anything.  What I was really curious about was if anybody could follow the recipe verbatim and get it running, but I'm like you, I always have to try it just a little bit different.

I had it confirmed in the LM forum thread so you really don't need to waste any time with it unless you just feel like it.

Let me know what Remastersys version you find is best though.

---

### Post by 23dornot23d on 2011-08-02
If we do not need a backup then I will continue ...... as Remastersys was installed later
on when I initially did this ......

The only reason we need remastersys though is to creat another Distro ..... 
so any body following this can skip it with no worries - as I was just trying to save 
myself another job, if I ever want to run it like this again as it is ideal here
for my desktop machine with 512 Meg ...... its very responsive ....

ok one more diversion ...... 

aptitude update
aptitude safe-upgrade

here .... I get a warning ...... not sure how critical it is ....... I run from USB drives all the time
and I did the upgrade as it updated asking to use the uuid's ........ so why this is here .....

[COLOR=Red]**ldconfig: /lib/libuuid.so.1 is not a symbolic link**[/COLOR]

I do not like errors ...... but it may just be a warning ...... that the file actually exists as a proper file
rather than a symbolic link .... to one ......


ok done it again and everything is as I like it clean and totally upto date

[IMG]http://img692.imageshack.us/img692/9376/cleanmeqd.jpg[/IMG]


Smooth ...... now for the repos .....

sudo sed -i 's/stable/testing/g' /etc/apt/sources.list

done

sudo gedit /etc/apt/sources.list



[I]ok then add the following ......

[/I]**How to install GNOME 3 on Debian testing aka wheezy** ([ [COLOR=Red]link to original [/COLOR]]("http://raphaelhertzog.com/2011/06/16/installing-gnome-3-on-debian-6-0-squeeze-no-sorry/"))

 If you want to try GNOME 3 before it has landed in testing, you&#8217;ll have to add unstable and experimental to your sources.list:
 deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) unstable main contrib non-free 
deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) experimental main contrib non-free



then
aptitude update

and added Gnome-shell and its dependencies in synaptic 


now the Nvidia drivers for the current kernel ....

Synaptic reload and add ..... ( it pulls in all the Nvidia requirements too ......)
nvidia-xconfig

also add
nvidia-settings

The graphics drivers




------------------------------------------------------

[COLOR=Red][U][I][B]Condensed its basically this ...........


[/B] [/I][/U][/COLOR]  
[LIST=1]
[*][COLOR=Red]_***Install LMDE (Xfce version recommended)***_[/COLOR]
[*][COLOR=Red]_***aptitude dist-upgrade  (do not choose the first thing it gives you  .....wait till libtar ..is the only thing it cannot resolve....***_[/COLOR]
[*][COLOR=Red]_***add the repositories and reload using synaptic ......***_[/COLOR]
[*][COLOR=Red]_***choose gnome-shell - install ......***_[/COLOR]
[*][COLOR=Red]_***in synaptic .... untick the experimental repos ......***_[/COLOR]
[/LIST]
[COLOR=Red][U][I] [B]
( if you have a  (ATI card however) or ..Nvidia Cards )

then [/B][B]

nvidia-xconfig plus the  drivers and kernel headers and kernel image needs setting up before  reboot [/B] [/I][/U][/COLOR]  
Ends up like this to start with .... then customize to suit ......

[IMG]http://img825.imageshack.us/img825/1761/screenshot0803201104495.png[/IMG]
__________________


It took me a couple of hours to do ..... but when you do it you will not be uploading screeenshots and trying
to show any errors that may come up ...... also the single core processor I am using celeron 3100 took
45 minutes to load the first set of updates (810 Meg) and upgrade the machine .....

[IMG]http://img42.imageshack.us/img42/7274/back10.png[/IMG]


[[COLOR=Blue]_***Fullsize Screenshot Fully uptodate***_[/COLOR]]("http://img198.imageshack.us/img198/847/fullyupdated.jpg")

---

### Post by 23dornot23d on 2011-08-03
> **cbowman57 said:**
> Ok, I think I've got it somewhat figured out.


[LIST=1]
[*]Install LMDE (Xfce version recommended)
[*]Run mintupdate, it will update itself & restart.  Run it again, install everything it suggests.
[*]Purge evince* [**sudo apt-get purge evince***] You can install it after you are finished (It provides support for reading pdf files).
[*]Shutdown/Restart
[*]**gksu thunar** & navigate to **/etc/apt**, rename your sources.list just to be prudent, then create a new **sources.list** that contains this data: ```
deb http://mirror.csclub.uwaterloo.ca/linuxmint-packages/ debian main upstream import backport romeo
deb http://debian.linuxmint.com/incoming testing main contrib non-free
# deb http://debian.linuxmint.com/latest testing main contrib non-free
deb http://security.debian.org/ testing/updates main contrib non-free
deb http://www.debian-multimedia.org testing main non-free
deb http://ftp.us.debian.org/debian stable main contrib non-free
deb http://ftp.us.debian.org/debian testing main contrib non-free
deb http://ftp.us.debian.org/debian unstable main contrib non-free
deb http://ftp.us.debian.org/debian experimental main contrib non-free

## Liquorix sources added by smxi ##
# deb http://liquorix.net/debian/ sid main
```
[*]Now navigate to **/etc/apt/apt.conf.d **create a file called **local**, insert this data into it: ```
APT::Default-Release "sid";
APT::Install-Recommends; 
```
[*]Go to **/etc/apt/preferences.d** create a file called **gnome**, insert this data into it & save it. ```
Package: *gnome* libglib2.0* *vte* *pulse* *peas* libgtk* *gjs* *gconf* *gstreamer* alacarte *brasero* cheese ekiga empathy* gdm3 gcalctool baobab *gucharmap* gvfs* hamster-applet *nautilus* seahorse* sound-juicer *totem* remmina vino gksu xdg-user-dirs-gtk dmz-cursor-theme eog epiphany* evince* *evolution* file-roller gedit* metacity *mutter* yelp* rhythmbox* banshee* system-config-printer transmission-* tomboy network-manager* libnm-* update-notifier shotwell liferea *software-properties* libunique-3.0-0 libseed-gtk3-0 libnotify* libpanel-applet-4-0 libgdata11 libcamel* libcanberra* libchamplain* libebackend* libebook* libecal* libedata* libegroupwise* libevent* gir1.2-* libxklavier16 python-gmenu libgdict-1.0-6 libgdu-gtk0 gnome-shell gconf2 gir1.2-gconf-2.0 gir1.2-gkbd-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomekbd-3.0 gir1.2-mutter-2.91 gir1.2-networkmanager-1.0 gjs gnome-bluetooth gnome-control-center gnome-icon-theme-symbolic gnome-settings-daemon libcanberra0 libdbus-1-3 libebook1.2-10 libecal1.2-8 libedataserver1.2-14 libedataserverui-3.0-0 libgconf2-4 libgjs0b libgl1-mesa-glx libgl1 libglib2.0-0 libgnome-desktop-3-0 libgnome-menu2 libmutter0 libpulse-mainloop-glib0 libpulse0 mutter python zlib1g gnome-control-center xserver-xephyr gnome-3.0 gir1.2-atk-1.0 gir1.2-clutter-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gsettings-desktop-schemas libatk1.0-0 libc0.1 libc6 libcairo-gobject2 libcairo2 libcamel1.2-19 libclutter-1.0-0 libcroco3 libdbus-glib-1-2 libdconf0 libdrm2 libffi5 libfontconfig1 libfreetype6 libgcc1 libgdk-pixbuf2.0-0 libgirepository-1.0-1 libgstreamer0.10-0 libgtk-3-0 libgtk2.0-0 libical0 libjson-glib-1.0-0 libmozjs2d libmozjs5d libnspr4-0d libnss3-1d libpango1.0-0 libpolkit-agent-1-0 libpolkit-gobject-1-0 libsoup2.4-1 libsqlite3-0 libstartup-notification0 libtelepathy-glib0 libtelepathy-logger2 libx11-6 libxcomposite1 libxdamage1 libxext6 libxfixes3 libxi6 libxml2 mesa-utils pkg-config libgnutls26
Pin: release experimental
Pin-Priority: 990

Package: *gnome* libglib2.0* *vte* *pulse* *peas* libgtk* *gjs* *gconf* *gstreamer* alacarte *brasero* cheese ekiga empathy* gdm3 gcalctool baobab *gucharmap* gvfs* hamster-applet *nautilus* seahorse* sound-juicer *totem* remmina vino gksu xdg-user-dirs-gtk dmz-cursor-theme eog epiphany* evince* *evolution* file-roller gedit* metacity *mutter* yelp* rhythmbox* banshee* system-config-printer transmission-* tomboy network-manager* libnm-* update-notifier shotwell liferea *software-properties* libunique-3.0-0 libseed-gtk3-0 libnotify* libpanel-applet-4-0 libgdata11 libcamel* libcanberra* libchamplain* libebackend* libebook* libecal* libedata* libegroupwise* libevent* gir1.2-* libxklavier16 python-gmenu libgdict-1.0-6 libgdu-gtk0 gnome-shell gconf2 gir1.2-gconf-2.0 gir1.2-gkbd-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomekbd-3.0 gir1.2-mutter-2.91 gir1.2-networkmanager-1.0 gjs gnome-bluetooth gnome-control-center gnome-icon-theme-symbolic libcanberra0 libdbus-1-3 libebook1.2-10 libecal1.2-8 libedataserver1.2-14 libedataserverui-3.0-0 libgconf2-4 libgjs0b libgl1-mesa-glx libgl1 libglib2.0-0 libgnome-desktop-3-0 libgnome-menu2 libmutter0 libpulse-mainloop-glib0 libpulse0 mutter python zlib1g gnome-control-center xserver-xephyr gnome-3.0 gir1.2-atk-1.0 gir1.2-clutter-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gsettings-desktop-schemas libatk1.0-0 libc0.1 libc6 libcairo-gobject2 libcairo2 libcamel1.2-19 libclutter-1.0-0 libcroco3 libdbus-glib-1-2 libdconf0 libdrm2 libffi5 libfontconfig1 libfreetype6 libgcc1 libgdk-pixbuf2.0-0 libgirepository-1.0-1 libgstreamer0.10-0 libgtk-3-0 libgtk2.0-0 libical0 libjson-glib-1.0-0 libmozjs2d libmozjs5d libnspr4-0d libnss3-1d libpango1.0-0 libpolkit-agent-1-0 libpolkit-gobject-1-0 libsoup2.4-1 libsqlite3-0 libstartup-notification0 libtelepathy-glib0 libtelepathy-logger2 libx11-6 libxcomposite1 libxdamage1 libxext6 libxfixes3 libxi6 libxml2 mesa-utils pkg-config
Pin: release unstable
Pin-Priority: 950

# gnome-settings-daemon

Package: *
Pin: release experimental
Pin-Priority: 150 
```
[*]Open terminal & **sudo apt-get update**.
[*]Purge gstreamer0.10-plugins-bad [**sudo apt-get purge gstreamer0.10-plugins-bad**], it also removes other files but you can reinstall when done.
[*]Do a dist-upgrade, **sudo apt-get dist-upgrade**.  It will add, remove & upgrade quite a few files.
[*]Shutdown/Restart
[*]**sudo apt-get update** & **sudo apt-get upgrade**
[*]Run update manager & update suggested files.
[*]Install gnome-shell [**sudo apt-get install gnome-shell**] Hopefully all dependencies are met, if not you might have to do some research.
[*][LEFT]Install gnome-tweak-tool [**sudo apt-get install gnome-tweak-tool**].[/LEFT]
[*]Install gnome-themes-standard [**sudo apt-get install gnome-themes-standard**].
[/LIST]
That should get you an installation of Gnome 3.0 shell & fallback installed on Linux Mint Debian Edition upgraded to Sid, otherwise known as Mogwai. :)

Installing user theme & extension support will be another post, but the simple way is to add the natty .debs from launchpad, make sure you install the ones for gnome-shell 3.0.2.

You will likely only have gnome-session-fallback when you log on from the gdm (don't forget to select your DE).  You can install your video drivers via synaptic or use the smxi script (link in post #1).

I'm sure there are some errors, and shortcuts I didn't try, but overall I think this is a good start.


Conclusion ........

O k I have brought this to the end again ...... as it is a good recipe

1 ...... Evince ..... does cause a problem as you go through the install and still does at the end
of the install .... not sure why it should though ..... yet

2 ...... Remastersys ..... if you intend making a DVD ,,,, to give to friends ..... this possibly wants installing right at the beginning of the process

3 ...... Thats it ..... they are the only major hassles .....

[IMG]http://img263.imageshack.us/img263/1653/tronbike.jpg[/IMG]


I now have a new version fully uptodate on my main computer ...... swapped the xorg.conf
to allow two monitors ,,,,, and thats a winner ...... :D :KS :KS :KS

Now 2 version uptodate ..... one on the desktop and one on the laptop ,,, its good ..... and now is my main system

[IMG]http://img855.imageshack.us/img855/775/mintdebiantron.jpg[/IMG]


[IMG]http://img854.imageshack.us/img854/5651/conkynvidia.jpg[/IMG]

---

### Post by cbowman57 on 2011-08-03
Nice Keith, thanks.  That gnome pinning file is a moving target, changes day-to-day, but I'm glad that it's at least a good starting point.

I ran the recipe on a fresh installation of aptosid last night, went fairly well & I learned some shortcuts with synaptic to avoid some conflicts, went well but it's missing something, doesn't have the functionality the LMDE version has but it's just due to a couple missing pacakges that elude me for now.

My thinking was to eliminate the LMDE vs Remastersys installer conflict and use aptosid for a base, which hopefully cooperates better.

Either one make for a very fast & light distro, and having an Xfce desktop is a bit of a bonus, it runs lightning fast and can be made to act very gnome2-like.

Oh well, I actually thought this would have generated more participation.  I guess people are either content with their Ubuntu versions or the Debian users just aren't into using G-S. :)

---

### Post by 23dornot23d on 2011-08-03
Its getting plenty of views and other threads are starting up too on the subject ....

The Mint-debian Distro is lightning fast ...... and it wins hands down .... at the moment
( yet to see what Onereic turns out like ..... but am following that too .... even did the
Mint version ...... 

I just went back into my Onereic upgrade of mint 11 to see the difference and it locks up
completely on my 512 Meg memory machine ..... even after removing Ubuntuone .... which
is a real killer - if you do not use it or need it .... 

> 
My thinking was to eliminate the LMDE vs Remastersys installer conflict  and use aptosid for a base, which hopefully cooperates better.
Ok well I hope it works ok ...... not sure what I am doing tonight now ..... there was another thread here
where someone is having problems with squashfs ..... but it may be something to do with later updates
in the repositories ...... as my new one is not as neat as the first Tron-Mint one .... both 32 bit ....

May go for the 64 bit one now ...... but I still need another USB drive ..... :( or a newer computer ...

I noticed the Mint forum is busy now .... too ..... and some of the names ring bells ..... 
> 
Anyone visiting this thread should also keep an eye on this [one in the [COLOR=Lime]Linux Mint[/COLOR] ]("http://forums.linuxmint.com/viewtopic.php?f=141&t=65745&sid=b3bf2ab542523b09669c8710ad7a5a19&p=455995#p455995")forum.

---

### Post by cbowman57 on 2011-08-03
I haven't noticed any other threads on the subject, but this one has been getting viewed?  Cool, maybe I'll do a search.

aptosid manages their security in a way I'm not familiar with, different paths, etc.. from LMDE & possibly Debian.  I think that's what might be causing the strange behavior, wallpaper only being available from certain folders and the file search tool doesn't work.

I might just see if I can use just a bare bones Debian CD, but I always get confused when I go looking for one.  They have CD's 1,2,3, etc.. is there a single disk for doing an installation?

---

### Post by 23dornot23d on 2011-08-03
This may be a starting place .... [LINK]("http://www.debian.org/CD/netinst/")

but I have never tried it out ......

Here is a link for the DVD .... but you probably already saw this .... [Link]("http://www.debian.org/releases/stable/debian-installer/")

---

### Post by cbowman57 on 2011-08-03
I think I tried that once, I'd give it a go again if I could point it to my local repo folder. :(

I saw in another thread that they also have a multi-arch DVD, think I'll go and see if I can hunt that down.

---

### Post by 23dornot23d on 2011-08-03
I have used Knoppix and Kanotix before ..... but I have no idea how uptodate they are

but I should imagine its just a case of adding the repos ...... have done this before
in the past .....

[URL="https://sites.google.com/site/23dornot23d/"]
[/URL]

---

### Post by cbowman57 on 2011-08-03
Well, I think the quickest & easiest way to build a Debian Gnome 3.0 shell installation is with net install.  **Nothing but Gnome!**  Virtually eliminates conflicts and you get a system that isn't constructed from meta-packages.

I installed a base system, booted into another installation (could probably do it from live CD) and edited/created/copied the files in the recipe.  Booted into the fresh bare installation, did a dist-upgrade, then installed gnome-shell, gdm3 and a couple other packages.  Rebooted, installed synaptic & started installing the stuff I wanted.  Added video driver for nvidia.

Then spent some time installing & carefully going through the smxi script to tweak it some more. (smxi installed the most recent nvidia 280.13).

Very compact & fast. :)

If Remastersys behaves I might use the same method to put a distro/respin together.

This is the best way to build a Debian system with Gnome 3.0 shell. :guitar:

---

### Post by 23dornot23d on 2011-08-04
Nice .... glad it worked out ok .....

I am on the thread above this one in the list .... just got the RC2 from Mint .... and its getting there
again .... this is the 3rd install now .... of the 32 bit .....  so will stick to the recipe best I can.

Then maybe tomorrow night have a go with pure Debian ..... ;)

All good fun ..... and finding funny little quirks ..... but none are show stoppers .... :D

---

### Post by cbowman57 on 2011-08-04
Well not having to deal with working around an existing desktop certainly makes it easier.  Dependencies & conflicts are easy to deal with when you don't have to worry about breaking something that already exists.

Did I mention it is fast? :D

Save those .debs, really makes the process quick.

---

### Post by 23dornot23d on 2011-08-04
The mint-debian one was fast - so if you managed to get improvements on that one you are doing very
well indeed .....

I just got a LXDE one going .... from the other thread ...
[URL="http://img580.imageshack.us/img580/6851/screenshotat20110804073.jpg"][B]
SCREENSHOT[/B][/URL] ..... KATYA and ONEIRIC ....

Weird the way Oneiric changes all the menus ..... have not got a clue now where things are ....

Most are in Other (menu option) though .....

---

### Post by cbowman57 on 2011-08-04
I'm just completely taken with how this latest experiment went, and I think this combination looks fantastic.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=199208&d=1312443568[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=199209&d=1312443568[/IMG]

---

### Post by 23dornot23d on 2011-08-04
Looking good now ..... think you have a winner with that one ...... ;) :KS :KS :KS

---

### Post by cbowman57 on 2011-08-04
> **23dornot23d said:**
> Looking good now ..... think you have a winner with that one ...... ;) :KS :KS :KS

Thanks Keith, I don't think it can get any better than this.  BTW, once I figured out how to activate compositing it feels even quicker.  Love how it looks & how it works.

One problem though, cannot make an iso that works from it. Tried different versions, kernels, gdm & gdm3, still a no-go.  Might try lxdm, with Debian it might pull it in without all of LXDE.

But yeah, I've waited about 18 years for a desktop that works this well. :)

---

### Post by 23dornot23d on 2011-08-04
I must admit going 18 years back ...... lols ..... 

I had a[[COLOR=Blue]_*** TI 99 with high resolution graphics ***_[/COLOR]]("http://en.wikipedia.org/wiki/Texas_Instruments_TI-99/4A")..... ( wow they were blocks as big as your fingers )

Amazing really how far they have come ...... and the way people strive to make them better

in another 20 years time .... 

I could not imagine what we will have ..... :D

Ok with the one you have ...... lock it down too ..... or make a clone ..... you probably already have done ....

Shame it will not go onto a ISO yet ...... but if the recipe works ...... then its a job for me tonight

Will see how it goes ..... and maybe go invest in another USB drive or computer .....

---

### Post by cbowman57 on 2011-08-04
I never had a TI, though I used to make circuit boards for TI in the late 70's. :)

My first computer was a Timex Sinclair, had that membrane keyboard and you had to save your work to a cassette deck.  The concept of a desktop was unheard of back then. :lol:

I'm looking at AptonCD right now, if I can't make an image maybe I can at least package an installer to install the necessary programs from a working package.

---

### Post by 23dornot23d on 2011-08-04
Wow the [[COLOR=Blue]_***ZX81***_[/COLOR]]("http://oldcomputers.net/ts1000.html") ...... with a full 10k of ram upgraded .....

I know some good programmers started on these and you are one of them .....

> 
I used to make circuit boards for TI in the late 70's. :smile:
Thats brilliant .... you are more into the hardware then ..... and understand deeper what goes on
inside the machines .....

I have built many but never put solder on one ..... just assembled the parts ....

Ok ...... got carried away there ....... will try the Debian one tonight ...... have come full circle really .....
Kanotix was always my favourite ..... Distro ..... was the first that booted from CD
if I remember correctly .... and picked up all the hardware automatically ....

---

### Post by cbowman57 on 2011-08-04
Man, we're old. :)

Speaking of old.  Where's Cecil?  :lol:

---

### Post by 23dornot23d on 2011-08-04
I was thinking that Cecil would be either on a bike ride ....... or having a few cans
  ........ and enjoying life .....

That reminds me ...... need to get out more and enjoy the countryside  ...... :)

---

### Post by cbowman57 on 2011-08-04
Me too, but it's so damn hot here this time of the year.  Hell, I guess it's hot everywhere.

Just got back from a bike ride though.

Learned something interesting about AptonCD, it can create a meta-package.  Now I just have to figure out how to convert the deb download script so it can copy the installed files to a folder, copy those into /var/cache/apt.. & create a meta-package out of it.  Oh well, might be something that never gets done. :)

---

### Post by 23dornot23d on 2011-08-04
Yep looking on this link now ..... [**LINK**]("http://forums.debian.net/viewtopic.php?t=30271")

---

### Post by cbowman57 on 2011-08-04
Yeah, if I can't create an iso, maybe a package to automate the installation.

---

### Post by cecilpierce on 2011-08-04
> **cbowman57 said:**
> Man, we're old. :)

Speaking of old.  Where's Cecil?  :lol:

I'z here, somewhere ???

Went to ride the bike this morning and had to cruz on back home, too hot, nobody was at the beach.
Went to the everglades yesterday to finish working on my airboat and there were fires all over from lightning and the fire dept was starting break fires right nex to where I was tring to do some electrical stuff, had to head west about a mile to get out of the smoke for awhile.
When I got back to finish I looked at the temp guage in the truck and it was 101F, and that was it the shade.
Just spent 300 bucks fixing the AC in it and cruzin out there it was 71, I like that :P

Havent fooled with this new Mint thing, you guys are too far ahead of me...
Well we have a little storm coming this way, need more rain and a break in this heat !

---

### Post by cbowman57 on 2011-08-04
Good to know you're still kickin'. :)

Just figured that the way you like to break things this would be right up your alley.

---

### Post by 23dornot23d on 2011-08-04
Hi Cecil good to see you are still around .....


A air boat that sound like a interesting project ...... 


Forest fires and heat is not good though ..... we are getting it too hot here .....
although we had rain last night and tonight ..... my grass is still brown .....



This mint thing ...... if it goes anything like last time there will be distro's soon

I could put one up tonight ..... but its not that user friendly .... similar to last
time ..... mine are basically backups ...... and might work might not on another
computer ......

A few more days with this and something may come out of it ....... other than a
recipe to follow ..... and it does work ..... but it just takes time .....

Evince ( really needs removing at the start  )

Remastersys 

( probably wants loading early on - but only if its included to make backups easier )

I did try a clean Distro and although it burned it ok ... it was not quite right ....
( may try again ..... as its good fun ..... )

Its getting closer though ......

---

### Post by cecilpierce on 2011-08-04
Im on the Mint DVD install now but don't know where to start to get it broke real good, any suggestions ?
Im going to dump that Mint CD and put the DVD on in its place so if I break one and can look at the other :P

Where did you get that background with the Debian thing on the end, mine says 11 ?

Hmmm! can't find screen shot, to show you what it looks like, maybe I have a different version ?

---

### Post by 23dornot23d on 2011-08-04
The one that comes up with 11 is the wrong one ..... 

It should have a debian symbol on it ...... 



As the only one I could find comes up 10 ...... initially on the background screensavers

this was the link I used [COLOR=Red]**[xfce 32 bit]("http://www.linuxmint.com/edition.php?id=79")** [/COLOR]

Linux Mint Xfce 32-bit (201104)

Best from the Official site I believe ...... [COLOR=Red]**[xfce 32 bit]("http://www.linuxmint.com/edition.php?id=79")** [/COLOR]

---

### Post by cbowman57 on 2011-08-04
Well, I just put another one together for 32-bit from the Debian net install.

Really getting to like this method.

---

### Post by 23dornot23d on 2011-08-04
I have Kanotix running on my main screen now ..... which is debian 6.0.1 ....

I am going to follow the recipe again ..... but first wondering about getting
a disk out after this ...... as I am prettz sure we will get Gnome Shell


Ok so back to the beginning

---

### Post by cecilpierce on 2011-08-04
WOW! took me 2 hours to DL that DVD, bummer, good thing there was a good movie on TV to watch.
Now to find a place to put it, decisions, decisions :confused:

---

### Post by cbowman57 on 2011-08-04
Ok, got one that burned & installed well.  I used gdm, not gdm3.  It has to be installed with the Remastersys installer if you edit the debian installer .desktop files to use gksu instead of su-to-root (or whatever it is) it might work.

I installed no proprietary drivers but did add the nvidia experimental GL module so it actually did a live boot to the shell.  It's pretty much barebones, but it's sid with G-S. Used the net install for a base.

---

### Post by 23dornot23d on 2011-08-04
Keep it safe ..... it sounds good ...... 

am just wondering what to do here ...... got the kanotix updated ......

Just a 

**aptitude safe-upgrade**

so far ...... but this is in KDE environment ...... so will be interesting to see if it will work
ok


[**SCREENSHOT**]("http://img508.imageshack.us/img508/6932/kanotix2.jpg")

It was clean no dependancy problems ..... interesting mix of repos too ....

ok going to download remastersys .... now ..... and try to get it in early ....

Ok Remastersys seemed to go in well this time

```

root@KanotixBox:/home/keith/Downloads# ls
remastersys_2.0.20-1_all.deb  xorg.conf
root@KanotixBox:/home/keith/Downloads# gdebi remastersys_2.0.20-1_all.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 

Requires the installation of the following packages: 
busybox  hwdata  laptop-detect  live-boot  live-boot-initramfs-tools  live-config  live-config-sysvinit  live-initramfs  memtest86+  squashfs-tools  syslinux 
Debian system remaster
 This script creates a livecd of the installed system.
 You can either make a distributable livecd or backup of your system.
 For more information, please visit http://www.remastersys.com
Do you want to install the software package? [y/N]:y
Get:1 http://kanotix.com/files/hellfire/ ./ syslinux 2:4.03+dfsg-12 [92.9 kB]                                 
Get:2 http://ftp.de.debian.org/debian/ squeeze/main busybox i386 1:1.17.1-8 [292 kB]                          
Get:3 http://ftp.de.debian.org/debian/ squeeze/main hwdata all 0.230-1 [393 kB]                               
Get:4 http://ftp.de.debian.org/debian/ squeeze/main laptop-detect i386 0.13.7 [5212 B]                        
Get:5 http://ftp.de.debian.org/debian/ squeeze/main live-boot-initramfs-tools all 2.0.15-1 [29.8 kB]          
Get:6 http://ftp.de.debian.org/debian/ squeeze/main live-boot all 2.0.15-1 [76.5 kB]                          
Get:7 http://ftp.de.debian.org/debian/ squeeze/main live-config-sysvinit all 2.0.15-1 [7732 B]                
Get:8 http://ftp.de.debian.org/debian/ squeeze/main live-config all 2.0.15-1 [41.4 kB]                        
Get:9 http://ftp.de.debian.org/debian/ squeeze/main live-initramfs all 2.0.15-1 [5152 B]                      
Get:10 http://ftp.de.debian.org/debian/ squeeze/main memtest86+ i386 4.10-1.1 [221 kB]                        
Get:11 http://ftp.de.debian.org/debian/ squeeze/main squashfs-tools i386 1:4.0-8 [114 kB]                     
Fetched 1279 kB in 0s (0 B/s)                                                                                 
Preconfiguring packages ...
Preconfiguring packages ...
Selecting previously deselected package busybox.
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 108385 files and directories currently installed.)
Unpacking busybox (from .../busybox_1%3a1.17.1-8_i386.deb) ...
Selecting previously deselected package hwdata.
Unpacking hwdata (from .../hwdata_0.230-1_all.deb) ...
Selecting previously deselected package laptop-detect.
Unpacking laptop-detect (from .../laptop-detect_0.13.7_i386.deb) ...
Selecting previously deselected package live-boot-initramfs-tools.
Unpacking live-boot-initramfs-tools (from .../live-boot-initramfs-tools_2.0.15-1_all.deb) ...
Selecting previously deselected package live-boot.
Unpacking live-boot (from .../live-boot_2.0.15-1_all.deb) ...
Selecting previously deselected package live-config-sysvinit.
Unpacking live-config-sysvinit (from .../live-config-sysvinit_2.0.15-1_all.deb) ...
Selecting previously deselected package live-config.
Unpacking live-config (from .../live-config_2.0.15-1_all.deb) ...
Selecting previously deselected package live-initramfs.
Unpacking live-initramfs (from .../live-initramfs_2.0.15-1_all.deb) ...
Selecting previously deselected package memtest86+.
Unpacking memtest86+ (from .../memtest86+_4.10-1.1_i386.deb) ...
Selecting previously deselected package squashfs-tools.
Unpacking squashfs-tools (from .../squashfs-tools_1%3a4.0-8_i386.deb) ...
Selecting previously deselected package syslinux.
Unpacking syslinux (from .../syslinux_2%3a4.03+dfsg-12_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: /boot/initrd.img-2.6.38-7-generic has been altered.
update-initramfs: Cannot update. Override with -t option.
Setting up busybox (1:1.17.1-8) ...
Setting up hwdata (0.230-1) ...
Setting up laptop-detect (0.13.7) ...
Setting up live-boot-initramfs-tools (2.0.15-1) ...
update-initramfs: deferring update (trigger activated)
Setting up live-config-sysvinit (2.0.15-1) ...
Setting up live-config (2.0.15-1) ...
Setting up memtest86+ (4.10-1.1) ...
Generating grub.cfg ...
Found background image: /usr/share/images/grub/kanotix-logo.png
Found linux image: /boot/vmlinuz-2.6.38-7-generic
Found initrd image: /boot/initrd.img-2.6.38-7-generic
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ multiboot image: /boot/memtest86+_multiboot.bin
File descriptor 3 (pipe:[15567]) leaked on lvs invocation. Parent PID 3169: /bin/sh
  No volume groups found
Found Ubuntu 10.10 (10.10) on /dev/sda6
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda8
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
Found PCLinuxOS on /dev/sda9
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
Found Linux Mint Xfce Edition (1) on /dev/sdb10
Found Ubuntu 11.04 (11.04) on /dev/sdb11
Found Ubuntu oneiric (development branch) (11.10) on /dev/sdb12
Found Ubuntu 11.04 (11.04) on /dev/sdb13
Found Ubuntu 11.04 (11.04) on /dev/sdb14
Found Ubuntu 11.04 (11.04) on /dev/sdb15
Found Ubuntu oneiric (development branch) (11.10) on /dev/sdb16
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sdb3
Found Ubuntu jaunty (development branch) (9.04) on /dev/sdb4
Found Ubuntu natty (development branch) (11.04) on /dev/sdb6
Found Ubuntu 11.04 (11.04) on /dev/sdb7
Found Ubuntu 11.04 (11.04) on /dev/sdb9
done
Setting up squashfs-tools (1:4.0-8) ...
Setting up syslinux (2:4.03+dfsg-12) ...
Processing triggers for initramfs-tools ...
update-initramfs: /boot/initrd.img-2.6.38-7-generic has been altered.
update-initramfs: Cannot update. Override with -t option.
Setting up live-boot (2.0.15-1) ...
update-rc.d: warning: live-boot start runlevel arguments (none) do not match LSB Default-Start values (S)
Setting up live-initramfs (2.0.15-1) ...
Selecting previously deselected package remastersys.
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 108584 files and directories currently installed.)
Unpacking remastersys (from remastersys_2.0.20-1_all.deb) ...
Setting up remastersys (2.0.20-1) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
root@KanotixBox:/home/keith/Downloads# 


```
Not sure about this line though ...
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.

Also going to load in Cairo-dock ..... before anything else .....

aptitude install cairo-dock

---

### Post by cbowman57 on 2011-08-05
> **papamama17 said:**
> I've used Mint before, and toyed with Debian some but this is new ground for me so I'm making plenty of mistakes.

That's great! :)

@Keith, well I actually came up with an iso that will fit on a CD.  Made some changes and am putting it on a usb stick now.  Will let you know how it goes.  Really want to use the Debian installer.

---

### Post by 23dornot23d on 2011-08-05
Thats brilliant ..... how much memory was it using at initial boot into the desktop
sounds great if it will go on a CD ..... how long to get it out onto Linuxtracker.

> 
I've used Mint before, and toyed with Debian some but this is new ground for me so I'm making plenty of mistakes.
Me too and we still make mistakes ..... and hopefully learn from them ,,,, its getting 
so we can install a new version a night now in a couple of hours ....

But if the Distro gets put out ...... it will save at least 2 hours for people and a lot of headaches too .....

[IMG]http://img38.imageshack.us/img38/914/screenshot10fl.jpg[/IMG]

[**YET ANOTHER SCREENSHOT**]("http://img215.imageshack.us/img215/5684/screenshot10bw.jpg") ..... quite Plain this time though

---

### Post by cbowman57 on 2011-08-05
2 hours?  More like 10. :lol:

Used about 180 Mb with the exp drivers.  I tweaked the debian installer but it still didn't work.  The Remastersys installer isn't creating the user, beginning to **** me off. :)

When I jump back to that install I'll see if there is a different version I can try.  Could be the one I'm using came out of experimental.  Perplexing.

I gravitate towards dark themes but Linux Mint always has a nice finished look.

---

### Post by slavinzing56 on 2011-08-05
Well it's up to you how you want to continue but I'm going to base mine on LMDE :smile:

Starting with LMDE is a completely different animal than using Ubuntu or Mint.

---

### Post by cbowman57 on 2011-08-05
Big difference.  You doing a 32 or 64 bit first?

---

### Post by 23dornot23d on 2011-08-05
> 
2 hours?  More like 10. :lol:


I will meet you half way ...... 
I usually start at midnight and finish by 6 in the morning ..... but doing other things too,

so lets say 6 Hours ...... ;)

Who's counting ...... its all good fun .....  :D

---

### Post by cbowman57 on 2011-08-05
> **23dornot23d said:**
> I will meet you half way ...... 
I usually start at midnight and finish by 6 in the morning ..... but doing other things too,

so lets say 6 Hours ...... ;)

Who's counting ...... its all good fun .....  :D

Somewhat dependent on speed of the connection. :)

Well, my 32-bit install bit the dust.  I used ext2 for that one, trying to see if there was a performance boost, but something went wrong & I formatted it.   So, it's the weekend, who knows what will happen.  I think I need to back off and see what happens.

So, not sure if I'll even try to make an iso but if I do I will:

1. Start with a net install.
2. Gnome only.
3. No proprietary video drivers.
4. Make every effort to make it fit on a CD sized image.
5. KISS (Keep it simple stupid)

---

### Post by 23dornot23d on 2011-08-05
There are many factors in the Debian one .... and while using testing and unstable :confused:

Well 3.2 is not that far away ..... looking at sometime in September I seem to recall
from a schedule I saw on the Gnome 3 site .... ( but maybe my memory is not that good )

The Mint one runs just fine ...... and with the 3.0.0.1 kernel too .....

So going to stick with this through the weekend and see how well it runs .... :D

Best of luck getting a new Distro out though .....

---

### Post by cbowman57 on 2011-08-05
Yeah, gonna put the idea of a distro on the back burner, not sure there is enough interest to warrant the effort.

Here's the tip for the day though, make sure you turn on compositing, if you're used to Ubuntu and it's tools (even LMDE has an app with Xfce) getting it turned on in Debian requires the use of gconf-editor.

Here's where to look:

[ATTACH]199310[/ATTACH]

---

### Post by 23dornot23d on 2011-08-06
Cheers for the tip ..... 

I had a nightmare day today ... carefully going through everything and it would just die
the hard drive would stop in its tracks .... at first I put it down to one of the applications
but 3rd time was enough .... the drive is naff .... :(

Going to get a new one on Monday ... so annoying too had almost got to the end of
a second big dist-upgrade on Kanotix carefully adding and removing packages to get to
a point where it would do it ..... was running really well until the hard drive was telling me 
it was read only ...... and nothing would alter it ... :confused:

Seemed I had had my privileges revoked ... and even a reboot would not let me do a fsck
on it ..... it would wipe and repartition though . 

Well I put it down to all the hot weather we have been having lately and this USB is not as
good as the Seagates ..... the Iomega 1T has no fan in it to keep it cool ......

Well another Seagate on Monday 1 Terra here is still 89 euros .... unless I get off of Amazon - but cannot wait for delivery ... need it now .... :)  ...... will move all my data across before it departs for good.

---

### Post by cbowman57 on 2011-08-06
Ouch!  I hate hardware failure, especially when it's a drive.  Hope you don't lose anything important.

---

### Post by 23dornot23d on 2011-08-06
Am ok got a new drive today .... lucky too was last one of the Seagates left and 1 Terra
I like these very quiet and very fast too ..... seems like a new machine again.

Ok now to start playing with the OS's .... lots of room now. 
( I have formatted and set the HD out ready ....  )

Got Kanotix 64 Bit on ... ( Debian Based - no alterations yet )
Just about to put Mint 10 Xfce on 
( Debian and Mint - its refused twice to go on my older computer 512 Meg ram - maybe have to use the 32 bit but did not want to mix all my systems up )

so

Its going to be a 64 Bit drive with all my Best things on it ...... finally getting organized ... 
only taken me 53 years .....

Will put the Gnome Shell Tron backup on it too thats 64 Bit as well ..... ( so that should cover everything - this is a 3.8Gig compressed install and fingers crossed this is going on ok ..... )

---

### Post by cbowman57 on 2011-08-06
Sounds like a full day so far. :)

---

### Post by 23dornot23d on 2011-08-06
Yep its going well .... just trying Debian Mint again .... this time with a better CD/DVD reader ..... hopefully it was due to me burning it on a different DVD drive 
( so now am using the same one I burnt it on ..... takes away any compatibility problems between different cd drives ) 

( update - thats sorted it copied all the files across now .... onto the drive - just the final part now and we are in business - its done )

I do not like giving up on a job ...... this will keep me busy all tonight and tomorrow now
hopefully by Monday I will have the latest release ......

Interesting using the new DVD drive its error checking routine may be better - instead of stalling where it did last time ...... its making more of an effort to read the drive ...
will see ..... still a long way to go ..... will post some pictures once I get to a reasonable stage ..... 

Updates and Upgrades take the time as you know , but then I will start to document on here
what I do again ...... it may be useful to others .

My main aim - so I do not forget now ..... is to get a Debian-Mint version based on [_***Kanotix***_]("http://all-things-linux.blogspot.com/2011/06/kanotix-2011-05-hellfire-review.html").

[IMG]http://img691.imageshack.us/img691/6321/snapshot2vi.jpg[/IMG]

Will be interesting as Kano has used a few scripts that tend to make the user not getting
full sudo privileges ....... but the good thing is he has a script thats setting the graphics up perfectly even from the Live CD ..... and the install there is no messing installing graphics drivers ..... not sure how he has achieved it yet .....

The other good thing is Kanotix has its own installer Acrotonix I think I spelled it right  
maybe it can be used for a new install ..... who know :confused:

[IMG]http://img14.imageshack.us/img14/416/snapshot5c.jpg[/IMG]

Anyway plenty to do now ..... and got a :D back on my face again ..... thats what life's about.


Still a little to do .... all the repositories are loaded and working .... the thing is this is so quick now
and runs in 320 Meg on top of KDE ...... by itself I am getting it at 200 Meg .....

This was a crazy simple upgrade ..... after doing it 3 times yesterday on a faulty drive ....
I think practice helps . ( still not fully finished yet as its running from LXDE )
But I do this while resolving things ..... like extensions for themes etc ....
( you can see any errors in a terminal window and kill it and still be ok in a LXDE desktop environment )
as shown in the first screenshot .... that is running in KDE though - 
as that is what Kanotix originally runs on ....

? Do I switch it to multiple monitors now ...

---

### Post by cbowman57 on 2011-08-07
In case anyone is interested I do have a working 32-bit Remastersys dist iso built on Debian Sid that contains nothing but Gnome 3.0 shell & fallback.  By only installing basic packages I've managed to keep it relatively small (591 MB).

The installation process is a little different, uses Remastersys Installer & it doesn't create a user, but that can be done after logging on as root.  It's a bit goofy but it works.

So, I'll seed it if there are a few people interested in it.

Here's a screenshot using nouveau drivers with Iceweasel & Gnome system monitor loaded.

[ATTACH]199432[/ATTACH]

With Nvidia 280.13 installed.

[ATTACH]199433[/ATTACH]

Running latest aptosid kernel.

[ATTACH]199434[/ATTACH]

Themed with some extensions.

[ATTACH]199435[/ATTACH]

---

### Post by 23dornot23d on 2011-08-07
Looking good ..... 

Iceweasel running and the system monitor on top of the shell the memory is only 371 Meg on the version you have posted  .... which is almost 300 Meg below the similar running in either UNITY or GNOME SHELL on Ubuntu ..... therefore it runs incredibly well on computers with
512 Meg ...... 

Really is good and should be a good download to have ready for when 3.2 comes out .....

I really do like the Remastersys Installer too .... ok one more days work on the Kanotix Mint
version too ..... 

If anyone is interested .... the procedure I used was a little different ..... due to it starting in KDE .

aptitude update 
aptitude safe upgrade
install lxde
install gnome-desktop
add all of the repositories ( Ricotz - Mint etc )
install gnome-shell

At the moment ..... that is all I have really done to get a working version of Gnome-Shell on
kanotix .

oh and loaded in Mint-debian update ........
Seems to fly though ... and is still on Gnome 2.32 .....

Now its ready for the upgrade to Gnome 3.1
But as I say we are now only a month away from Gnome 3.2

I am looking forward to seeing how well the new version runs ....

---

### Post by cbowman57 on 2011-08-07
Oh, I stumbled on a bit of a trick yesterday.  It seemed to make it easier to install gnome-shell with contrib & non-free disabled, just the main repositories active.  Once the dist-upgrade was done I turned them back on for the safe-upgrade.

Don't know if I stumbled on something useful or it was just the state of the repositories.

I just can't believe how responsive this gnome only system is, and it was snappy even with the nouveau experimental driver, which might be a factor on lower memory systems.

After all this experimentation I'm really tempted to try a gnome only build on an Ubuntu  minimal install. :)

---

### Post by 23dornot23d on 2011-08-07
> 
After all this experimentation I'm really tempted to try a gnome only build on an Ubuntu  minimal install. :)
Thats a very good idea ..... as it will show the difference in memory usage etc with a bare system ..... then we can see if its just all the extra packages for Ubuntuone and all ....
that are making the difference .... or if its the OS itself that is quicker and leaner.

I am just doing the 32 bit version of kanotix as I quite like this one .... and I have come full circle as it was my starting Distro that really triggered me into using Linux ..... :)

> 
Oh, I stumbled on a bit of a trick yesterday.  It seemed to make it  easier to install gnome-shell with contrib & non-free disabled, just  the main repositories active.  Once the dist-upgrade was done I turned  them back on for the safe-upgrade.

Good to know might try this too - I usually enable ricotz and install gnome-shell then disable it straight after
I do not use the tweak tool or any of the extensions out of his repo though as I can never get them to work properly.

The gnome tweak tool I use is the 3.0.4 one now as I find its the better one ....

Ok the 32 bit is installed - time to work on it ...... will follow my recipe above and see if it varies any ....... may add and remove details ...... as the 32 bit may be different .....

so to start .... 

First lets see what happens

**1 . aptitude update**

**2 . install lxde** 

**3 . Swap into LXDE** as working with 512M memory is in the edge and memory lock ups are not unheard of
so just trying same again from LXDE environment .... ( thats allowed it to work ...... how bizarre is that* [COLOR=Red][it would lock up in kde at gconf2][/COLOR]*)

[IMG]http://img708.imageshack.us/img708/7446/snapshot1kj.jpg[/IMG]

**3 . install gnome-desktop**  ( in progress on new drive - when complete this may become my main distro of choice ) 
( doing this - it removes one file to satify dependencies ...._***[ libgpod4-nogtk ]("http://packages.debian.org/sid/libgpod4-nogtk")***_)
This is a biggy 476 Meg .... download to add gnome desktop ( in progress )
It asks a question in this - kde or gdm3 ( I choose kdm )

4 . **Swap into Gnome Desktop now .....**

[IMG]http://img89.imageshack.us/img89/359/gnome23.jpg[/IMG]


[COLOR=Red][B]UPTO HERE YOUR SYSTEM SHOULD BE STABLE ....... once you go beyond this point we are into testing
and experimental ..... so do not do this unless you know what you are doing ........ 
[/B][/COLOR]( as all of this from here on - is still in development - repository contents change from day to day too so this may only be useful at this point in time )

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

add all of the repositories ( _[[COLOR=Red]**Ricotz - Mint etc**[/COLOR]]("https://sites.google.com/site/23dsources/")_ ) I have 7 commented out to start with as we need to dist-upgrade here
to get the system up to date ready for the newer files/programs .... ( ok upto here ..... all is ok ..... not completed the rest yet )

aptitude update
aptitude dist-upgrade ( I accepted the first option here  ) 300 Meg upgrade ......

```

These were the answers I gave to questions asked along the way ..... 
usually just accept the defaults ....

USA keyboard 
WORKGROUP
yes upgrade glibc now
restart kdm and cups ..... the screen will go off and back on here ... 
the processes are still running though check htop needs a reboot too ....


```reboot the system here .......


Check that all the upgrades completed ... too

aptitude update
aptitude dist-upgrade ( at this point if you watch the packages all the 3.0.2 packages should be appearing and being installed )

if it goes blank press Alt+CTRL +F1 ,,,,,login,,,,,, always check HTOP to see what is running ......
*wait till all process's to do with dpkg are completed ,,,,,, *
I chose not to use the kano sudoers listing .... 
( might not have been a good decision - so next time leave it in - reason not picking up the graphics card automatically )
and although its not a big deal ..... it is one more thing the user need not worry about .... so maybe see what it does

it may be as simple as loading the header the image and the nvidia drivers in the right order. who knows ...


Here - doing CTRL+ALT+F7 will take you back into your desktop normally ......

[IMG]http://img543.imageshack.us/img543/5061/screenshot3sze.jpg[/IMG]
 
 


_________________________________________________________________________ ok to here ....... redo after here ( starting again )


[[COLOR=Red]_**initramfs**_[/COLOR]]("http://en.wikipedia.org/wiki/Initrd") ..... ?

>  quoted from the above link - at this moment in time ... In the **initramfs** scheme (available in Linux 2.6.13 onwards), the image may be a [cpio]("http://en.wikipedia.org/wiki/Cpio") archive (optionally compressed). The archive is unpacked by the kernel into a special instance of a [tmpfs]("http://en.wikipedia.org/wiki/Tmpfs")  that becomes the initial root file system. This scheme has the  advantage of not requiring an intermediate file system or block drivers  to be compiled into the kernel.[]("http://en.wikipedia.org/wiki/Initrd#cite_note-landley-3")
[B]
Mount preparations[/B]

 Some Linux distributions will generate a customized initrd image  which contains only whatever is necessary to boot some particular  computer, such as [ATA]("http://en.wikipedia.org/wiki/Advanced_Technology_Attachment"), [SCSI]("http://en.wikipedia.org/wiki/SCSI") and filesystem [kernel modules]("http://en.wikipedia.org/wiki/Loadable_kernel_module"). These typically embed the location and type of the root file system.
 Other distributions (such as Fedora and Ubuntu) generate a more  generic initrd image. These start only with the device name of the root  file system (or its [UUID]("http://en.wikipedia.org/wiki/UUID"))  and must discover everything else at boot time. In this case, a complex  cascade of tasks must be performed to get the root file system mounted:

and quoted from the kernel link above back to wiki

Loadable kernel modules in Linux are loaded by the [modprobe]("http://en.wikipedia.org/wiki/Modprobe") command. They are located in /lib/modules and they have had the extension .ko ("kernel object") since version 2.6.

[IMG]http://img594.imageshack.us/img594/4210/finvq.jpg[/IMG]


rebooting again .... to finish the process .....

Go into synaptic ..... enable the 7 repositories from earlier ..... and in synaptic ..... reload twice .
second time all the gnome-shell extensions will show up .....  but we just want gnome-shell  

So mark for installation .... just to ..... 
( nothing else do not get tempted to add tweak tools or extensions we can not go back but we can always go forward after)

[IMG]http://img11.imageshack.us/img11/5719/screenshot8s.jpg[/IMG]

**[SCREENSHOT FULL]("http://img13.imageshack.us/img13/4593/screenshot8a.jpg")**



Taken 5 hours for me to get here ..... including having my dinner .... so ..... if we produce a distro .... we probably do
save 5-6 hours work for someone ......

aptitude install gnome-shell

(should have disabled the ricotz testing here ...... and the experimental ....)

and aptitude install gnome-control-center

reboot

[COLOR=Red]THIS DID NOT GO AS WELL AS WHEN I DID THE 64 BIT ONE .... so what is different ..... and can I now revise this
may do another later on tonight .... while its fresh in my head .... 8.22pm here now and loading in the latest kernel and
graphics drivers now ...... that could have gone a lot better than it did ,,,,,

Will run gnome-shell once the new kernel and graphics drivers are in .... as its in low graphics at the moment ..... 
no glx so mutter will not run
[/COLOR] 
remastersys v20 can be added here .... if all goes to plan ( I have already done this on the 64 bit version and it works )

ok and other things that I do .... add conky .... change icon theme to Clarity .....

---

### Post by cbowman57 on 2011-08-07
@Keith, this is a fresh desktop Gnome 3.0 shell w/Nvidia 270.41 & Firefox 5.0 built from Ubuntu minimal install iso.  It has a light footprint too.

[ATTACH]199489[/ATTACH]

Damn, that is REALLY light.  I have a dilemma. :)

---

### Post by cbowman57 on 2011-08-07
@Keith, this is practically unbelievable.  About all I did after installation was to purge ubuntuone*.

[ATTACH]199492[/ATTACH]          [ATTACH]199493[/ATTACH]

---

### Post by 23dornot23d on 2011-08-07
That is the thing ,,,, for people not using ubuntuone ...... its a killer ....

I also get rid of Mono too ...... and add gnote ..... for the notes .... its written in C but its not
as complete as MONO ..... but then again if you do not use it  ..... whats the point of them

especially for those of us with 512 Meg memory .....

Great work by the way ......  :D

> 
Damn, that is REALLY light.  I have a dilemma. :smile:


whats the dilemma ?

---

### Post by cbowman57 on 2011-08-07
> **23dornot23d said:**
> 

whats the dilemma ?

If I had a brain in my head I'd chose an installation & tweak the hell out of it.  Problem is they all run so sweet, I need to pick the one that runs the best for me & stick with it I suppose.  I'm still of the opinion that even on a 64-bit machine the 32-bit versions are more responsive & more conservative in their use of memory.  Probably due to the 64-bit loading both libraries so it can support 32-bit apps.

As far as appearance & functionality I can totally personalize my installation in about an hour or so.  Gotta love it. :)

---

### Post by 23dornot23d on 2011-08-07
> 
As far as appearance & functionality I can totally personalize my installation in about an hour or so.  Gotta love it. :smile:
Thats brilliant ..... 

I too set a directory with all my gnome shell stuff in it and just copy it across to customize the way I like it now ..... that bits reasonably easy now ....

The big thing is do you start with less ..... to upgrade a system and the answer is yes ....

As less dependency problems occur .... but to maintain all the functionality for everyone ....

the Mint Repos need adding in my mind as they are more ..... shall we say polished than the others
in my way of thinking anyway  .....

The reason for kanotix is its always been good at picking up hardware ..... and if kano has solved the problem with getting the graphics

drivers to load automatically - then that is a big headache gone right away



I am still plugging away at it - am confident .... this is a fresh install and its taken me 10 
minutes and gnome-shell is loading in - now

---

### Post by cbowman57 on 2011-08-07
Yeah, Mint has a good look to it but I'm at the point now that I don't really need what they have.

I'm committed to G-S as my desktop of choice, my personal comfort level while using it has made everything else seem backwards by comparison.  With that in mind, whatever I use will contain nothing but Gnome, everything else takes up space & doesn't get used.

---

### Post by 23dornot23d on 2011-08-07
From start to finish in 10 Mins .....

will load in lxde at the end and take a look see what we have now ...... missing themes ..... at moment ...

ok time is run out .... scrabble time .... this was just a quick rush had enough today ......
( I think I did this out of pure frustration ..... but its running amazingly  )

Dropped in the repos .... then just upgraded till it would accept gnome-shell ....... but now there is lots to fix 

aptitude install bluetooth
aptitude install gnome-themes-standard
aptitude install lxde

and there is more to come ..... (later) chances are its going to fail somewhere .....
although all the dependencies were met - it removed so much it may not work

but amazingly the network is up
iceweasel works ....
gnome-shell works ( but still needs some additional work to it ..... ) 
kde works
lxde works

So I may spend an hour on it ... to see if its worth doing any more to it .....
I am after a working version of Kanotix - with the ability to update from Debian Mint repos ....
I have used Ricotz ppa purely to get a up to date gnome-shell ( then I drop the repo )



```



keith@KanotixBox:~$ su
Password: 
root@KanotixBox:/home/keith# aptitude update
Hit http://www.debian-multimedia.org testing Release.gpg
Ign http://www.debian-multimedia.org/ testing/main Translation-en               
Ign http://www.debian-multimedia.org/ testing/main Translation-en_US            
Ign http://www.debian-multimedia.org/ testing/non-free Translation-en           
Ign http://www.debian-multimedia.org/ testing/non-free Translation-en_US        
Hit http://kanotix.acritox.com trialshot Release.gpg                            
Ign http://kanotix.acritox.com/debian/ trialshot/main Translation-en            
Hit http://kanotix.com ./ Release.gpg                                           
Ign http://kanotix.com/files/excalibur/ ./ Translation-en                       
Hit http://www.debian-multimedia.org testing Release                            
Hit http://ftp.de.debian.org squeeze Release.gpg                                
Ign http://ftp.de.debian.org/debian/ squeeze/contrib Translation-en             
Hit http://ppa.launchpad.net oneiric Release.gpg                                
Ign http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main Translation-en 
Ign http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main Translation-en_US
Ign http://kanotix.acritox.com/debian/ trialshot/main Translation-en_US         
Hit http://kanotix.acritox.com trialshot Release                                
Ign http://kanotix.com/files/excalibur/ ./ Translation-en_US                    
Hit http://kanotix.com ./ Release.gpg                                           
Ign http://kanotix.com/files/hellfire/ ./ Translation-en                        
Ign http://kanotix.com/files/hellfire/ ./ Translation-en_US                     
Hit http://kanotix.com ./ Release.gpg                                           
Ign http://kanotix.com/files/fix/lo/ ./ Translation-en                          
Ign http://kanotix.com/files/fix/lo/ ./ Translation-en_US                       
Hit http://kanotix.com ./ Release                                               
Hit http://ppa.launchpad.net oneiric Release.gpg                                
Ign http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ oneiric/main Translation-en
Ign http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ oneiric/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                  
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en  
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ftp.debian.org testing Release.gpg                                   
Ign http://ftp.debian.org/debian/ testing/contrib Translation-en                
Ign http://ftp.debian.org/debian/ testing/contrib Translation-en_US             
Ign http://ftp.de.debian.org/debian/ squeeze/contrib Translation-en_US          
Ign http://ftp.de.debian.org/debian/ squeeze/main Translation-en                
Ign http://ftp.de.debian.org/debian/ squeeze/main Translation-en_US             
Ign http://ftp.de.debian.org/debian/ squeeze/non-free Translation-en            
Ign http://ftp.de.debian.org/debian/ squeeze/non-free Translation-en_US         
Hit http://ftp.de.debian.org squeeze Release                                    
Hit http://security.debian.org testing/updates Release.gpg                      
Ign http://security.debian.org/ testing/updates/contrib Translation-en          
Ign http://security.debian.org/ testing/updates/contrib Translation-en_US       
Hit http://kanotix.com ./ Release                                               
Hit http://kanotix.com ./ Release                                               
Hit http://ppa.launchpad.net oneiric Release                                    
Ign http://ftp.debian.org/debian/ testing/main Translation-en                   
Ign http://ftp.debian.org/debian/ testing/main Translation-en_US                
Ign http://ftp.debian.org/debian/ testing/non-free Translation-en               
Ign http://ftp.debian.org/debian/ testing/non-free Translation-en_US            
Hit http://ftp.debian.org unstable Release.gpg                                  
Ign http://ftp.debian.org/debian/ unstable/contrib Translation-en               
Ign http://ftp.debian.org/debian/ unstable/contrib Translation-en_US            
Ign http://security.debian.org/ testing/updates/main Translation-en             
Ign http://security.debian.org/ testing/updates/main Translation-en_US          
Ign http://security.debian.org/ testing/updates/non-free Translation-en         
Ign http://security.debian.org/ testing/updates/non-free Translation-en_US      
Hit http://security.debian.org squeeze/updates Release.gpg                      
Ign http://security.debian.org/ squeeze/updates/contrib Translation-en          
Ign http://security.debian.org/ squeeze/updates/contrib Translation-en_US       
Hit http://ppa.launchpad.net oneiric Release                                    
Hit http://ppa.launchpad.net lucid Release                                      
Hit http://www.debian-multimedia.org testing/main i386 Packages/DiffIndex       
Ign http://ftp.debian.org/debian/ unstable/main Translation-en                  
Ign http://ftp.debian.org/debian/ unstable/main Translation-en_US               
Ign http://ftp.debian.org/debian/ unstable/non-free Translation-en              
Ign http://security.debian.org/ squeeze/updates/main Translation-en             
Ign http://security.debian.org/ squeeze/updates/main Translation-en_US          
Ign http://security.debian.org/ squeeze/updates/non-free Translation-en         
Hit http://kanotix.acritox.com trialshot/main Sources                           
Get:1 http://packages.linuxmint.com debian Release.gpg [198 B]                  
Ign http://packages.linuxmint.com/ debian/import Translation-en                 
Ign http://packages.linuxmint.com/ debian/import Translation-en_US              
Ign http://ftp.debian.org/debian/ unstable/non-free Translation-en_US           
Hit http://ftp.debian.org testing Release                                       
Hit http://ftp.debian.org unstable Release                                      
Ign http://packages.linuxmint.com/ debian/main Translation-en                   
Ign http://security.debian.org/ squeeze/updates/non-free Translation-en_US      
Hit http://security.debian.org testing/updates Release                          
Hit http://security.debian.org squeeze/updates Release                          
Hit http://www.debian-multimedia.org testing/non-free i386 Packages/DiffIndex   
Hit http://kanotix.acritox.com trialshot/main i386 Packages                     
Ign http://kanotix.com ./ Sources                                               
Hit http://ftp.de.debian.org squeeze/main Sources                               
Ign http://kanotix.com ./ Packages                                              
Hit http://ppa.launchpad.net oneiric/main Sources                               
Hit http://kanotix.com ./ Sources                                               
Ign http://kanotix.com ./ Sources                                               
Ign http://kanotix.com ./ Packages                                              
Ign http://kanotix.com ./ Packages                                              
Hit http://ftp.de.debian.org squeeze/contrib Sources                            
Ign http://packages.linuxmint.com/ debian/main Translation-en_US                
Ign http://packages.linuxmint.com/ debian/upstream Translation-en               
Ign http://packages.linuxmint.com/ debian/upstream Translation-en_US            
Hit http://ftp.de.debian.org squeeze/non-free Sources                           
Hit http://ftp.de.debian.org squeeze/main i386 Packages                         
Hit http://ftp.de.debian.org squeeze/contrib i386 Packages                      
Hit http://ftp.de.debian.org squeeze/non-free i386 Packages                     
Get:2 http://packages.linuxmint.com debian Release [12.1 kB]                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages                         
Hit http://ppa.launchpad.net oneiric/main i386 Packages                         
Hit http://ppa.launchpad.net lucid/main Sources                                 
Hit http://ppa.launchpad.net lucid/main i386 Packages                           
Hit http://ftp.debian.org testing/main i386 Packages/DiffIndex                  
Hit http://security.debian.org testing/updates/main i386 Packages           
Hit http://kanotix.com ./ Packages                                           
Hit http://kanotix.com ./ Sources                                            
Hit http://kanotix.com ./ Packages                                           
Hit http://ftp.debian.org testing/contrib i386 Packages/DiffIndex               
Hit http://ftp.debian.org testing/non-free i386 Packages/DiffIndex              
Hit http://ftp.debian.org unstable/main Sources/DiffIndex                       
Hit http://security.debian.org testing/updates/contrib i386 Packages            
Hit http://security.debian.org testing/updates/non-free i386 Packages           
Ign http://packages.linuxmint.com debian/main i386 Packages                     
Hit http://ftp.debian.org unstable/contrib Sources/DiffIndex         
Hit http://ftp.debian.org unstable/non-free Sources/DiffIndex        
Hit http://ftp.debian.org unstable/main i386 Packages/DiffIndex      
Hit http://ftp.debian.org unstable/contrib i386 Packages/DiffIndex   
Hit http://ftp.debian.org unstable/non-free i386 Packages/DiffIndex  
Hit http://kanotix.com ./ Packages                                   
Hit http://security.debian.org squeeze/updates/main Sources          
Ign http://packages.linuxmint.com debian/upstream i386 Packages              
Hit http://security.debian.org squeeze/updates/contrib Sources               
Hit http://security.debian.org squeeze/updates/non-free Sources
Hit http://security.debian.org squeeze/updates/main i386 Packages
Hit http://security.debian.org squeeze/updates/contrib i386 Packages
Hit http://security.debian.org squeeze/updates/non-free i386 Packages
Ign http://packages.linuxmint.com debian/import i386 Packages
Get:3 http://packages.linuxmint.com debian/main i386 Packages [9,149 B]
Get:4 http://packages.linuxmint.com debian/upstream i386 Packages [5,208 B]
Get:5 http://packages.linuxmint.com debian/import i386 Packages [19.3 kB]
Fetched 45.9 kB in 6s (7,568 B/s)                                               
                            
root@KanotixBox:/home/keith# aptitude install gnome-shell
The following NEW packages will be installed:
  dconf-gsettings-backend{a} gir1.2-atk-1.0{a} gir1.2-clutter-1.0{a} 
  gir1.2-freedesktop{a} gir1.2-gconf-2.0{a} gir1.2-gdkpixbuf-2.0{a} 
  gir1.2-glib-2.0{a} gir1.2-gtk-3.0{a} gir1.2-json-1.0{a} 
  gir1.2-mutter-3.0{a} gir1.2-pango-1.0{a} gir1.2-polkit-1.0{a} 
  gir1.2-soup-2.4{a} gir1.2-telepathyglib-0.12{a} 
  gir1.2-telepathylogger-0.2{a} gir1.2-upowerglib-1.0{a} gjs{a} 
  glib-networking{a} gnome-icon-theme{a} gnome-icon-theme-symbolic{a} 
  gnome-shell{b} gsettings-desktop-schemas{a} libatk1.0-data{a} 
  libcairo-gobject2{a} libcanberra-gtk3-0{a} libcanberra0{a} 
  libclutter-1.0-0{a} libgdk-pixbuf2.0-0{a} libgirepository-1.0-1{a} 
  libgjs0b{a} libgnome-menu2{a} libgtk-3-0{a} libgtk-3-bin{a} 
  libgtk-3-common{a} libjpeg8{a} libjson-glib-1.0-0{a} libmozjs5d{a} 
  libmutter0{a} librsvg2-common{a} libtdb1{a} libtelepathy-glib0{a} 
  libtelepathy-logger2{a} libupower-glib1{a} libxcb-util0{a} 
  multiarch-support{a} mutter-common{a} pkg-config{a} sgml-base{a} 
The following packages will be REMOVED:
  libeggdbus-1-0{u} libgsf-1-114{u} libgsf-1-common{u} 
  libpango1.0-common{u} libxcb-event1{u} plymouth{u} 
The following packages will be upgraded:
  gconf2-common libatk1.0-0 libc-bin libc6 libgconf2-4 libgcrypt11 
  libglib2.0-0 libgnutls26 libgpg-error0 libgtk2.0-0 libltdl7 libpango1.0-0 
  libpcre3 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 
  libpulse0 librsvg2-2 libsoup2.4-1 libstartup-notification0 libwmf0.2-7 
  libxfixes3 locales policykit-1 
The following packages are RECOMMENDED but will NOT be installed:
  gnome-control-center libc6-i686 libcanberra-gtk3-module 
  libclutter-1.0-common libglib2.0-data libgtk2.0-bin x-ttcidfont-conf 
24 packages upgraded, 48 newly installed, 6 to remove and 821 not upgraded.
Need to get 51.6 MB of archives. After unpacking 82.7 MB will be used.
The following packages have unmet dependencies:
  libgail18: Depends: libgtk2.0-0 (= 2.20.1-2) but 2.24.5-4 is to be installed.
  gnome-shell: Depends: gnome-bluetooth (>= 3.0.0) but it is not going to be installed.
               Depends: libecal1.2-9 (>= 3.1.3.1) which is a virtual package.
               Depends: libedataserver1.2-14 (>= 3.1.3.1) but it is not going to be installed.
               Depends: libedataserverui-3.0-1 (>= 3.1.3.1) which is a virtual package.
               Depends: libgnome-desktop-3-2 (>= 2.91.5) which is a virtual package.
               Depends: libmozjs185-1.0 (>= 1.8.5~hg20110306r6) which is a virtual package.
               Depends: gnome-settings-daemon (>= 2.91.5.1) but it is not going to be installed.
               Depends: gir1.2-gkbd-3.0 which is a virtual package.
               Depends: gir1.2-gnomebluetooth-1.0 which is a virtual package.
               Depends: gir1.2-networkmanager-1.0 which is a virtual package.
  plymouth-drm: Depends: plymouth (= 0.8.3-1 but it is not going to be installed.
  libc-dev-bin: Depends: libc6 (< 2.12) but 2.13-14 is to be installed.
  gconf2: Depends: gconf2-common (< 2.29) but 2.32.4-1 is to be installed.
  libpulse-mainloop-glib0: Depends: libpulse0 (= 0.9.21-3+squeeze1) but 0.9.23-1 is to be installed.
  libc6-dev: Depends: libc6 (= 2.11.2-10) but 2.13-14 is to be installed.
open: 201; closed: 185; defer: 119; conflict: 146                              .The following actions will resolve these dependencies:

       Remove the following packages:                       
1)       amarok                                             
2)       ark                                                
3)       bluedevil                                          
4)       build-essential                                    
5)       dolphin                                            
6)       g++                                                
7)       g++-4.4                                            
8)       gconf2                                             
9)       gdebi-kde                                          
10)      gecko-mediaplayer                                  
11)      gimp                                               
12)      gimp-gutenprint                                    
13)      gksu                                               
14)      gnome-mplayer                                      
15)      gstreamer0.10-plugins-good                         
16)      gwenview                                           
17)      hplip-gui                                          
18)      k3b                                                
19)      k3b-i18n                                           
20)      kaffeine                                           
21)      kappfinder                                         
22)      kate                                               
23)      kcalc                                              
24)      kde-config-touchpad                                
25)      kde-plasma-desktop                                 
26)      kde-window-manager                                 
27)      kdebase                                            
2      kdebase-apps                                       
29)      kdebase-bin                                        
30)      kdebase-runtime                                    
31)      kdebase-workspace                                  
32)      kdebase-workspace-bin                              
33)      kdelibs5-plugins                                   
34)      kdemultimedia-kio-plugins                          
35)      kdepasswd                                          
36)      kdepim-runtime                                     
37)      kdm                                                
3      kdm-theme-kanotix-starrise                         
39)      kfind                                              
40)      khelpcenter4                                       
41)      klipper                                            
42)      kmahjongg                                          
43)      kmix                                               
44)      knm-runtime                                        
45)      konqueror                                          
46)      konqueror-nsplugins                                
47)      konsole                                            
4      konversation                                       
49)      ksnapshot                                          
50)      ksplash-theme-kanotix-starrise                     
51)      ksysguard                                          
52)      kuser                                              
53)      kvkbd                                              
54)      kwalletmanager                                     
55)      kwrite                                             
56)      libc-dev-bin                                       
57)      libc6-dev                                          
5      libgail18                                          
59)      libgksu2-0                                         
60)      libgstfarsight0.10-0                               
61)      libk3b6                                            
62)      libk3b6-extracodecs                                
63)      libkcddb4                                          
64)      libkdewebkit5                                      
65)      libkhtml5                                          
66)      libknotifyconfig4                                  
67)      libkonq5                                           
6      libkwineffects1a                                   
69)      libkworkspace4                                     
70)      libokularcore1                                     
71)      libphonon4                                         
72)      libplasma3                                         
73)      libplasmaclock4a                                   
74)      libplasmagenericshell4                             
75)      libprocessui4a                                     
76)      libpulse-mainloop-glib0                            
77)      libpurple0                                         
7      libqt4-webkit                                      
79)      libstdc++6-4.4-dev                                 
80)      libweather-ion4a                                   
81)      libwebkit-1.0-2                                    
82)      network-manager-kde                                
83)      okular                                             
84)      phonon                                             
85)      phonon-backend-xine                                
86)      pidgin                                             
87)      pidgin-skype                                       
8      plasma-dataengines-addons                          
89)      plasma-dataengines-workspace                       
90)      plasma-desktop                                     
91)      plasma-runners-addons                              
92)      plasma-scriptengine-javascript                     
93)      plasma-widget-folderview                           
94)      plasma-widgets-addons                              
95)      plasma-widgets-workspace                           
96)      plymouth-drm                                       
97)      plymouth-theme-kanotix-logo                        
9      python-kde4                                        
99)      python-qt4                                         
100)     system-config-printer-kde                          
101)     systemsettings                                     
102)     xorg                                               

       Keep the following packages at their current version:
103)     gir1.2-mutter-3.0 [Not Installed]                  
104)     gnome-shell [Not Installed]                        
105)     libmutter0 [Not Installed]                         
106)     mutter-common [Not Installed]                      



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

      Remove the following packages:                                            
1)      build-essential                                                         
2)      g++                                                                     
3)      g++-4.4                                                                 
4)      libc6-dev                                                               
5)      libdrm-nouveau1                                                         
6)      libstdc++6-4.4-dev                                                      
7)      xserver-xorg-video-all                                                  
  xserver-xorg-video-nouveau                                              

      Install the following packages:                                           
9)      libdrm-nouveau1a [2.4.26-1 (testing, unstable)]                         

      Keep the following packages at their current version:                     
10)     gconf2-common [2.28.1-6 (now, stable)]                                  
11)     gir1.2-gconf-2.0 [Not Installed]                                        
12)     gir1.2-mutter-3.0 [Not Installed]                                       
13)     gnome-shell [Not Installed]                                             
14)     libgconf2-4 [2.28.1-6 (now, stable)]                                    
15)     libmutter0 [Not Installed]                                              

      Upgrade the following packages:                                           
16)     libc-dev-bin [2.11.2-10 (now, stable) -> 2.13-14 (unstable)]            
17)     libgail18 [2.20.1-2 (now, stable) -> 2.24.5-4 (unstable)]               
1     libpulse-mainloop-glib0 [0.9.21-3+squeeze1 (now, stable) -> 0.9.23-1 (te
19)     plymouth [0.8.3-18 (<NULL>, now) -> 0.8.3-19 (unstable)]                
20)     plymouth-drm [0.8.3-18 (<NULL>, now) -> 0.8.3-19 (unstable)]            



Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  glib-networking{a} gsettings-desktop-schemas{a} libatk1.0-data{a} 
  libdrm-nouveau1a{a} libgdk-pixbuf2.0-0{a} libjpeg8{a} libxcb-util0{a} 
  multiarch-support{a} 
The following packages will be REMOVED:
  build-essential{a} g++{a} g++-4.4{a} libc-dev-bin{u} libc6-dev{a} 
  libdrm-nouveau1{a} libeggdbus-1-0{u} libgsf-1-114{u} libgsf-1-common{u} 
  libpango1.0-common{u} libstdc++6-4.4-dev{a} libxcb-event1{u} 
  xserver-xorg-video-all{a} xserver-xorg-video-nouveau{a} 
The following packages will be upgraded:
  libatk1.0-0 libc-bin libc6 libgail18 libgcrypt11 libglib2.0-0 libgnutls26 
  libgpg-error0 libgtk2.0-0 libltdl7 libpango1.0-0 libpcre3 
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 
  libpulse-mainloop-glib0 libpulse0 librsvg2-2 libsoup2.4-1 
  libstartup-notification0 libwmf0.2-7 libxfixes3 locales plymouth 
  plymouth-drm policykit-1 
The following packages are RECOMMENDED but will NOT be installed:
  libc6-i686 libglib2.0-data libgtk2.0-bin plymouth-themes-all 
  x-ttcidfont-conf 
26 packages upgraded, 8 newly installed, 14 to remove and 813 not upgraded.
Need to get 19.7 MB of archives. After unpacking 32.0 MB will be freed.
Do you want to continue? [Y/n/?] y
Get:1 http://ftp.debian.org/debian/ unstable/main locales all 2.13-14 [4,814 kB]
Get:2 http://ftp.debian.org/debian/ unstable/main libc-bin i386 2.13-14 [1,024 kB]
Get:3 http://ftp.debian.org/debian/ unstable/main libc6 i386 2.13-14 [3,901 kB] 
Get:4 http://ftp.debian.org/debian/ unstable/main multiarch-support i386 2.13-14 [140 kB]
Get:5 http://ftp.debian.org/debian/ unstable/main plymouth-drm i386 0.8.3-19 [109 kB]
Get:6 http://ftp.debian.org/debian/ testing/main libdrm-nouveau1a i386 2.4.26-1 [418 kB]
Get:7 http://ftp.debian.org/debian/ unstable/main libpcre3 i386 8.12-4 [223 kB] 
Get:8 http://ftp.debian.org/debian/ testing/main libglib2.0-0 i386 2.28.6-1 [1,503 kB]
Get:9 http://ftp.debian.org/debian/ unstable/main plymouth i386 0.8.3-19 [141 kB]
Get:10 http://ftp.debian.org/debian/ unstable/main libpango1.0-0 i386 1.28.4-2 [439 kB]
Get:11 http://ftp.debian.org/debian/ unstable/main policykit-1 i386 0.102-1 [58.4 kB]
Get:12 http://ftp.debian.org/debian/ unstable/main libpolkit-backend-1-0 i386 0.102-1 [48.1 kB]
Get:13 http://ftp.debian.org/debian/ unstable/main libpolkit-agent-1-0 i386 0.102-1 [23.9 kB]
Get:14 http://ftp.debian.org/debian/ unstable/main libpolkit-gobject-1-0 i386 0.102-1 [47.0 kB]
Get:15 http://ftp.debian.org/debian/ testing/main libatk1.0-data all 2.0.1-2 [215 kB]
Get:16 http://ftp.debian.org/debian/ testing/main libatk1.0-0 i386 2.0.1-2 [91.8 kB]
Get:17 http://ftp.debian.org/debian/ testing/main libxfixes3 i386 1:5.0-4 [21.2 kB]
Get:18 http://ftp.debian.org/debian/ unstable/main libgail18 i386 2.24.5-4 [445 kB]
Get:19 http://ftp.debian.org/debian/ testing/main libgpg-error0 i386 1.10-0.3 [69.2 kB]
Get:20 http://ftp.debian.org/debian/ unstable/main libgcrypt11 i386 1.4.6-8 [286 kB]
Get:21 http://ftp.debian.org/debian/ unstable/main libgnutls26 i386 2.12.7-4 [780 kB]
Get:22 http://ftp.debian.org/debian/ unstable/main libgtk2.0-0 i386 2.24.5-4 [2,701 kB]
Get:23 http://ftp.debian.org/debian/ testing/main libjpeg8 i386 8c-2 [131 kB]   
Get:24 http://ftp.debian.org/debian/ testing/main libwmf0.2-7 i386 0.2.8.4-8.1 [190 kB]
Get:25 http://ftp.debian.org/debian/ unstable/main librsvg2-2 i386 2.34.0-2 [152 kB]
Get:26 http://ftp.debian.org/debian/ unstable/main libgdk-pixbuf2.0-0 i386 2.23.5-3 [667 kB]
Get:27 http://ftp.debian.org/debian/ testing/main libxcb-util0 i386 0.3.8-1 [24.3 kB]
Get:28 http://ftp.debian.org/debian/ testing/main libstartup-notification0 i386 0.12-1 [25.6 kB]
Get:29 http://ftp.debian.org/debian/ testing/main gsettings-desktop-schemas all 3.0.1-1 [80.0 kB]
Get:30 http://ftp.debian.org/debian/ testing/main glib-networking i386 2.28.7-1 [66.9 kB]
Get:31 http://ftp.debian.org/debian/ unstable/main libltdl7 i386 2.4-3 [345 kB] 
Get:32 http://ftp.debian.org/debian/ testing/main libpulse-mainloop-glib0 i386 0.9.23-1 [22.9 kB]
Get:33 http://ftp.debian.org/debian/ testing/main libpulse0 i386 0.9.23-1 [253 kB]
Get:34 http://ftp.debian.org/debian/ unstable/main libsoup2.4-1 i386 2.34.3-1 [206 kB]
Fetched 19.7 MB in 20s (974 kB/s)                                               
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 107442 files and directories currently installed.)
Removing build-essential ...
Removing g++ ...
Removing g++-4.4 ...
Removing libstdc++6-4.4-dev ...
Removing libc6-dev ...
Removing libc-dev-bin ...
Processing triggers for man-db ...
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106180 files and directories currently installed.)
Preparing to replace locales 2.11.2-10 (using .../locales_2.13-14_all.deb) ...
Unpacking replacement locales ...
Preparing to replace libc-bin 2.11.2-10 (using .../libc-bin_2.13-14_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.13-14) ...
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106205 files and directories currently installed.)
Preparing to replace libc6 2.11.2-10 (using .../libc6_2.13-14_i386.deb) ...
Checking for services that may need to be restarted...
Checking init scripts...
Unpacking replacement libc6 ...
Setting up libc6 (2.13-14) ...
Installing new version of config file /etc/ld.so.conf.d/i486-linux-gnu.conf ...
Checking for services that may need to be restarted...
Checking init scripts...

Restarting services possibly affected by the upgrade:
  cups: restarting...done.
  cron: restarting...done.

Services restarted successfully.
Selecting previously deselected package multiarch-support.
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106208 files and directories currently installed.)
Unpacking multiarch-support (from .../multiarch-support_2.13-14_i386.deb) ...
Preparing to replace plymouth-drm 0.8.3-18 (using .../plymouth-drm_0.8.3-19_i386.deb) ...
Unpacking replacement plymouth-drm ...
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106211 files and directories currently installed.)
Removing xserver-xorg-video-all ...
Removing xserver-xorg-video-nouveau ...
Removing libdrm-nouveau1 ...
Processing triggers for man-db ...
Setting up multiarch-support (2.13-14) ...
Selecting previously deselected package libdrm-nouveau1a.
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106192 files and directories currently installed.)
Unpacking libdrm-nouveau1a (from .../libdrm-nouveau1a_2.4.26-1_i386.deb) ...
Preparing to replace libpcre3 8.02-1.1 (using .../libpcre3_8.12-4_i386.deb) ...
Unpacking replacement libpcre3 ...
Preparing to replace libglib2.0-0 2.24.2-1 (using .../libglib2.0-0_2.28.6-1_i386.deb) ...
Unpacking replacement libglib2.0-0 ...
Preparing to replace plymouth 0.8.3-18 (using .../plymouth_0.8.3-19_i386.deb) ...
Unpacking replacement plymouth ...
Preparing to replace libpango1.0-0 1.28.3-1+squeeze2 (using .../libpango1.0-0_1.28.4-2_i386.deb) ...
Unpacking replacement libpango1.0-0 ...
Preparing to replace policykit-1 0.96-4 (using .../policykit-1_0.102-1_i386.deb) ...
Unpacking replacement policykit-1 ...
Preparing to replace libpolkit-backend-1-0 0.96-4 (using .../libpolkit-backend-1-0_0.102-1_i386.deb) ...
Unpacking replacement libpolkit-backend-1-0 ...
Preparing to replace libpolkit-agent-1-0 0.96-4 (using .../libpolkit-agent-1-0_0.102-1_i386.deb) ...
Unpacking replacement libpolkit-agent-1-0 ...
Preparing to replace libpolkit-gobject-1-0 0.96-4 (using .../libpolkit-gobject-1-0_0.102-1_i386.deb) ...
Unpacking replacement libpolkit-gobject-1-0 ...
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: /boot/initrd.img-2.6.38-7-generic has been altered.
update-initramfs: Cannot update. Override with -t option.
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106205 files and directories currently installed.)
Removing libeggdbus-1-0 ...
Selecting previously deselected package libatk1.0-data.
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106198 files and directories currently installed.)
Unpacking libatk1.0-data (from .../libatk1.0-data_2.0.1-2_all.deb) ...
Preparing to replace libatk1.0-0 1.30.0-1 (using .../libatk1.0-0_2.0.1-2_i386.deb) ...
Unpacking replacement libatk1.0-0 ...
Preparing to replace libxfixes3 1:4.0.5-1 (using .../libxfixes3_1%3a5.0-4_i386.deb) ...
Unpacking replacement libxfixes3 ...
Preparing to replace libgail18 2.20.1-2 (using .../libgail18_2.24.5-4_i386.deb) ...
Unpacking replacement libgail18 ...
Preparing to replace libgpg-error0 1.6-1 (using .../libgpg-error0_1.10-0.3_i386.deb) ...
Unpacking replacement libgpg-error0 ...
Preparing to replace libgcrypt11 1.4.5-2 (using .../libgcrypt11_1.4.6-8_i386.deb) ...
Unpacking replacement libgcrypt11 ...
Preparing to replace libgnutls26 2.8.6-1 (using .../libgnutls26_2.12.7-4_i386.deb) ...
Unpacking replacement libgnutls26 ...
Preparing to replace libgtk2.0-0 2.20.1-2 (using .../libgtk2.0-0_2.24.5-4_i386.deb) ...
Unpacking replacement libgtk2.0-0 ...
Selecting previously deselected package libjpeg8.
Unpacking libjpeg8 (from .../libjpeg8_8c-2_i386.deb) ...
Preparing to replace libwmf0.2-7 0.2.8.4-6.1+b1 (using .../libwmf0.2-7_0.2.8.4-8.1_i386.deb) ...
Cleaning up font configuration of libwmf0.2-7...
Cleaning up category type1..
Cleaning up category truetype..
Unpacking replacement libwmf0.2-7 ...
Preparing to replace librsvg2-2 2.26.3-1 (using .../librsvg2-2_2.34.0-2_i386.deb) ...
Unpacking replacement librsvg2-2 ...
Selecting previously deselected package libgdk-pixbuf2.0-0.
Unpacking libgdk-pixbuf2.0-0 (from .../libgdk-pixbuf2.0-0_2.23.5-3_i386.deb) ...
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106419 files and directories currently installed.)
Removing libgsf-1-114 ...
Removing libgsf-1-common ...
Removing libpango1.0-common ...
W: libwmf0.2-7 is already removed. It is recommended to run defoma-app purge libwmf0.2-7.
Purging font configuration of pango...
Purging category xfont..
Processing triggers for man-db ...
Selecting previously deselected package libxcb-util0.
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106379 files and directories currently installed.)
Unpacking libxcb-util0 (from .../libxcb-util0_0.3.8-1_i386.deb) ...
Preparing to replace libstartup-notification0 0.10-1 (using .../libstartup-notification0_0.12-1_i386.deb) ...
Unpacking replacement libstartup-notification0 ...
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106386 files and directories currently installed.)
Removing libxcb-event1 ...
Selecting previously deselected package gsettings-desktop-schemas.
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106381 files and directories currently installed.)
Unpacking gsettings-desktop-schemas (from .../gsettings-desktop-schemas_3.0.1-1_all.deb) ...
Selecting previously deselected package glib-networking.
Unpacking glib-networking (from .../glib-networking_2.28.7-1_i386.deb) ...
Preparing to replace libltdl7 2.2.6b-2 (using .../libltdl7_2.4-3_i386.deb) ...
Unpacking replacement libltdl7 ...
Preparing to replace libpulse-mainloop-glib0 0.9.21-3+squeeze1 (using .../libpulse-mainloop-glib0_0.9.23-1_i386.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Preparing to replace libpulse0 0.9.21-3+squeeze1 (using .../libpulse0_0.9.23-1_i386.deb) ...
Unpacking replacement libpulse0 ...
Preparing to replace libsoup2.4-1 2.30.2-1 (using .../libsoup2.4-1_2.34.3-1_i386.deb) ...
Unpacking replacement libsoup2.4-1 ...
Setting up locales (2.13-14) ...
Generating locales (this might take a while)...
  en_US.UTF-8... done
Generation complete.
Setting up libdrm-nouveau1a (2.4.26-1) ...
Setting up libpcre3 (8.12-4) ...
Setting up libglib2.0-0 (2.28.6-1) ...
Setting up libpango1.0-0 (1.28.4-2) ...
Setting up plymouth (0.8.3-19) ...
update-initramfs: deferring update (trigger activated)
Setting up libpolkit-gobject-1-0 (0.102-1) ...
Setting up libpolkit-agent-1-0 (0.102-1) ...
Setting up libpolkit-backend-1-0 (0.102-1) ...
Setting up policykit-1 (0.102-1) ...
Setting up libatk1.0-data (2.0.1-2) ...
Setting up libatk1.0-0 (2.0.1-2) ...
Setting up libxfixes3 (1:5.0-4) ...
Setting up libjpeg8 (8c-2) ...
Setting up libgdk-pixbuf2.0-0 (2.23.5-3) ...
Setting up libgpg-error0 (1.10-0.3) ...
Setting up libgcrypt11 (1.4.6-8) ...
Setting up libgnutls26 (2.12.7-4) ...
Setting up libgtk2.0-0 (2.24.5-4) ...
Setting up libgail18 (2.24.5-4) ...
Setting up libwmf0.2-7 (0.2.8.4-8.1) ...
Setting up librsvg2-2 (2.34.0-2) ...
Setting up libxcb-util0 (0.3.8-1) ...
Setting up libstartup-notification0 (0.12-1) ...
Setting up gsettings-desktop-schemas (3.0.1-1) ...
Setting up glib-networking (2.28.7-1) ...
Setting up libltdl7 (2.4-3) ...
Setting up libpulse0 (0.9.23-1) ...
Setting up libpulse-mainloop-glib0 (0.9.23-1) ...
Setting up libsoup2.4-1 (2.34.3-1) ...
Processing triggers for initramfs-tools ...
update-initramfs: /boot/initrd.img-2.6.38-7-generic has been altered.
update-initramfs: Cannot update. Override with -t option.
Setting up plymouth-drm (0.8.3-19) ...
                                         
Current status: 813 updates [-35].
root@KanotixBox:/home/keith# aptitude install gnome-shell
The following NEW packages will be installed:
  dconf-gsettings-backend{a} gir1.2-atk-1.0{a} gir1.2-clutter-1.0{a} 
  gir1.2-freedesktop{a} gir1.2-gconf-2.0{a} gir1.2-gdkpixbuf-2.0{a} 
  gir1.2-glib-2.0{a} gir1.2-gtk-3.0{a} gir1.2-json-1.0{a} 
  gir1.2-mutter-3.0{a} gir1.2-pango-1.0{a} gir1.2-polkit-1.0{a} 
  gir1.2-soup-2.4{a} gir1.2-telepathyglib-0.12{a} 
  gir1.2-telepathylogger-0.2{a} gir1.2-upowerglib-1.0{a} gjs{a} 
  gnome-icon-theme{a} gnome-icon-theme-symbolic{a} gnome-shell{b} 
  libcairo-gobject2{a} libcanberra-gtk3-0{a} libcanberra0{a} 
  libclutter-1.0-0{a} libgirepository-1.0-1{a} libgjs0b{a} 
  libgnome-menu2{a} libgtk-3-0{a} libgtk-3-bin{a} libgtk-3-common{a} 
  libjson-glib-1.0-0{a} libmozjs5d{a} libmutter0{a} librsvg2-common{a} 
  libtdb1{a} libtelepathy-glib0{a} libtelepathy-logger2{a} 
  libupower-glib1{a} mutter-common{a} pkg-config{a} sgml-base{a} 
The following packages will be upgraded:
  gconf2-common libgconf2-4 
The following packages are RECOMMENDED but will NOT be installed:
  gnome-control-center libcanberra-gtk3-module libclutter-1.0-common 
2 packages upgraded, 41 newly installed, 0 to remove and 811 not upgraded.
Need to get 33.0 MB of archives. After unpacking 74.0 MB will be used.
The following packages have unmet dependencies:
  gnome-shell: Depends: gnome-bluetooth (>= 3.0.0) but it is not going to be installed.
               Depends: libecal1.2-9 (>= 3.1.3.1) which is a virtual package.
               Depends: libedataserver1.2-14 (>= 3.1.3.1) but it is not going to be installed.
               Depends: libedataserverui-3.0-1 (>= 3.1.3.1) which is a virtual package.
               Depends: libgnome-desktop-3-2 (>= 2.91.5) which is a virtual package.
               Depends: libmozjs185-1.0 (>= 1.8.5~hg20110306r6) which is a virtual package.
               Depends: gnome-settings-daemon (>= 2.91.5.1) but it is not going to be installed.
               Depends: gir1.2-gkbd-3.0 which is a virtual package.
               Depends: gir1.2-gnomebluetooth-1.0 which is a virtual package.
               Depends: gir1.2-networkmanager-1.0 which is a virtual package.
  gconf2: Depends: gconf2-common (< 2.29) but 2.32.4-1 is to be installed.
The following actions will resolve these dependencies:

      Remove the following packages:                       
1)      gconf2                                             
2)      gecko-mediaplayer                                  
3)      gksu                                               
4)      gnome-mplayer                                      
5)      gstreamer0.10-plugins-good                         
6)      libgksu2-0                                         
7)      libgstfarsight0.10-0                               
8)      libpurple0                                         
9)      pidgin                                             
10)     pidgin-skype                                       

      Keep the following packages at their current version:
11)     gir1.2-mutter-3.0 [Not Installed]                  
12)     gnome-shell [Not Installed]                        
13)     libmutter0 [Not Installed]                         
14)     mutter-common [Not Installed]                      



Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  gconf2{a} gecko-mediaplayer{a} gksu{a} gnome-mplayer{a} 
  gstreamer0.10-nice{u} gstreamer0.10-plugins-bad{u} 
  gstreamer0.10-plugins-good{a} libass4{u} libavahi-glib1{u} 
  libavc1394-0{u} libcdaudio1{u} libcelt0-0{u} libdca0{u} libdiscid0{u} 
  libdv4{u} libenca0{u} libexempi3{u} libflite1{u} libgadu3{u} 
  libgksu2-0{a} libgme0{u} libgssdp-1.0-2{u} libgstfarsight0.10-0{a} 
  libgtkspell0{u} libgupnp-1.0-3{u} libgupnp-igd-1.0-3{u} libiec61883-0{u} 
  libiptcdata0{u} libkate1{u} liblircclient0{u} libmeanwhile1{u} 
  libmimic0{u} libmms0{u} libmusicbrainz3-6{u} libneon27-gnutls{u} 
  libnice0{u} libnotify1{u} liboil0.3{u} libopenspc0{u} libpurple0{a} 
  libshout3{u} libsilc-1.1-2{u} libsilcclient-1.1-3{u} libslv2-9{u} 
  libsoundtouch1c2{u} libsoup-gnome2.4-1{u} libwildmidi1{u} libzbar0{u} 
  libzephyr4{u} mplayer{u} pidgin{a} pidgin-data{u} pidgin-skype{a} 
The following packages will be upgraded:
  gconf2-common libgconf2-4 
2 packages upgraded, 0 newly installed, 53 to remove and 775 not upgraded.
Need to get 2,020 kB of archives. After unpacking 84.5 MB will be freed.
Do you want to continue? [Y/n/?] y
Get:1 http://ftp.debian.org/debian/ testing/main libgconf2-4 i386 2.32.4-1 [282 kB]
Get:2 http://ftp.debian.org/debian/ testing/main gconf2-common all 2.32.4-1 [1,738 kB]
Fetched 2,020 kB in 2s (685 kB/s)         
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 106470 files and directories currently installed.)
Removing pidgin ...
Removing gksu ...
Removing libgksu2-0 ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode.
Removing pidgin-skype ...
Removing libpurple0 ...
Removing libgstfarsight0.10-0 ...
Removing gstreamer0.10-plugins-good ...
Removing gecko-mediaplayer ...
Removing gnome-mplayer ...
Removing gconf2 ...
Removing gstreamer0.10-nice ...
Removing gstreamer0.10-plugins-bad ...
Removing libass4 ...
Removing libavahi-glib1 ...
Removing libavc1394-0 ...
Removing libcdaudio1 ...
Removing libcelt0-0 ...
Removing libdca0 ...
Removing libmusicbrainz3-6 ...
Removing libdiscid0 ...
Removing libdv4 ...
Removing mplayer ...
Removing libenca0 ...
Removing libexempi3 ...
Removing libflite1 ...
Removing libgadu3 ...
Removing libgme0 ...
Removing libnice0 ...
Removing libgupnp-igd-1.0-3 ...
Removing libgupnp-1.0-3 ...
Removing libgssdp-1.0-2 ...
Removing libgtkspell0 ...
Removing libiec61883-0 ...
Removing libiptcdata0 ...
Removing libkate1 ...
Removing liblircclient0 ...
Removing libmeanwhile1 ...
Removing libmimic0 ...
Removing libmms0 ...
Removing libneon27-gnutls ...
Removing libnotify1 ...
Removing liboil0.3 ...
Removing libopenspc0 ...
Removing libshout3 ...
Removing libsilc-1.1-2 ...
Removing libsilcclient-1.1-3 ...
Removing libslv2-9 ...
Removing libsoundtouch1c2 ...
Removing libsoup-gnome2.4-1 ...
Removing libwildmidi1 ...
Removing libzbar0 ...
Removing libzephyr4 ...
Removing pidgin-data ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for hicolor-icon-theme ...
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 104703 files and directories currently installed.)
Preparing to replace libgconf2-4 2.28.1-6 (using .../libgconf2-4_2.32.4-1_i386.deb) ...
Unpacking replacement libgconf2-4 ...
Preparing to replace gconf2-common 2.28.1-6 (using .../gconf2-common_2.32.4-1_all.deb) ...
Unpacking replacement gconf2-common ...
Processing triggers for libglib2.0-0 ...
Setting up gconf2-common (2.32.4-1) ...
Setting up libgconf2-4 (2.32.4-1) ...
                                         
Current status: 775 updates [-38].
root@KanotixBox:/home/keith# aptitude install gnome-shell
The following NEW packages will be installed:
  dconf-gsettings-backend{a} gconf2{a} gir1.2-atk-1.0{a} 
  gir1.2-clutter-1.0{a} gir1.2-freedesktop{a} gir1.2-gconf-2.0{a} 
  gir1.2-gdkpixbuf-2.0{a} gir1.2-glib-2.0{a} gir1.2-gtk-3.0{a} 
  gir1.2-json-1.0{a} gir1.2-mutter-3.0{a} gir1.2-pango-1.0{a} 
  gir1.2-polkit-1.0{a} gir1.2-soup-2.4{a} gir1.2-telepathyglib-0.12{a} 
  gir1.2-telepathylogger-0.2{a} gir1.2-upowerglib-1.0{a} gjs{a} 
  gnome-icon-theme{a} gnome-icon-theme-symbolic{a} gnome-shell{b} 
  libcairo-gobject2{a} libcanberra-gtk3-0{a} libcanberra0{a} 
  libclutter-1.0-0{a} libgirepository-1.0-1{a} libgjs0b{a} 
  libgnome-menu2{a} libgtk-3-0{a} libgtk-3-bin{a} libgtk-3-common{a} 
  libjson-glib-1.0-0{a} libmozjs5d{a} libmutter0{a} librsvg2-common{a} 
  libsoup-gnome2.4-1{a} libtdb1{a} libtelepathy-glib0{a} 
  libtelepathy-logger2{a} libupower-glib1{a} mutter-common{a} pkg-config{a} 
  sgml-base{a} 
The following packages are RECOMMENDED but will NOT be installed:
  gnome-control-center libcanberra-gtk3-module libclutter-1.0-common 
0 packages upgraded, 43 newly installed, 0 to remove and 775 not upgraded.
Need to get 31.2 MB of archives. After unpacking 74.2 MB will be used.
The following packages have unmet dependencies:
  gnome-shell: Depends: gnome-bluetooth (>= 3.0.0) but it is not going to be installed.
               Depends: libecal1.2-9 (>= 3.1.3.1) which is a virtual package.
               Depends: libedataserver1.2-14 (>= 3.1.3.1) but it is not going to be installed.
               Depends: libedataserverui-3.0-1 (>= 3.1.3.1) which is a virtual package.
               Depends: libgnome-desktop-3-2 (>= 2.91.5) which is a virtual package.
               Depends: libmozjs185-1.0 (>= 1.8.5~hg20110306r6) which is a virtual package.
               Depends: gnome-settings-daemon (>= 2.91.5.1) but it is not going to be installed.
               Depends: gir1.2-gkbd-3.0 which is a virtual package.
               Depends: gir1.2-gnomebluetooth-1.0 which is a virtual package.
               Depends: gir1.2-networkmanager-1.0 which is a virtual package.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 775 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
root@KanotixBox:/home/keith# aptitude install gnome-shell
The following NEW packages will be installed:
  dconf-gsettings-backend{a} gconf2{a} gir1.2-atk-1.0{a} 
  gir1.2-clutter-1.0{a} gir1.2-freedesktop{a} gir1.2-gconf-2.0{a} 
  gir1.2-gdkpixbuf-2.0{a} gir1.2-glib-2.0{a} gir1.2-gtk-3.0{a} 
  gir1.2-json-1.0{a} gir1.2-mutter-3.0{a} gir1.2-pango-1.0{a} 
  gir1.2-polkit-1.0{a} gir1.2-soup-2.4{a} gir1.2-telepathyglib-0.12{a} 
  gir1.2-telepathylogger-0.2{a} gir1.2-upowerglib-1.0{a} gjs{a} 
  gnome-icon-theme{a} gnome-icon-theme-symbolic{a} gnome-shell{b} 
  libcairo-gobject2{a} libcanberra-gtk3-0{a} libcanberra0{a} 
  libclutter-1.0-0{a} libgirepository-1.0-1{a} libgjs0b{a} 
  libgnome-menu2{a} libgtk-3-0{a} libgtk-3-bin{a} libgtk-3-common{a} 
  libjson-glib-1.0-0{a} libmozjs5d{a} libmutter0{a} librsvg2-common{a} 
  libsoup-gnome2.4-1{a} libtdb1{a} libtelepathy-glib0{a} 
  libtelepathy-logger2{a} libupower-glib1{a} mutter-common{a} pkg-config{a} 
  sgml-base{a} 
The following packages are RECOMMENDED but will NOT be installed:
  gnome-control-center libcanberra-gtk3-module libclutter-1.0-common 
0 packages upgraded, 43 newly installed, 0 to remove and 775 not upgraded.
Need to get 31.2 MB of archives. After unpacking 74.2 MB will be used.
The following packages have unmet dependencies:
  gnome-shell: Depends: gnome-bluetooth (>= 3.0.0) but it is not going to be installed.
               Depends: libecal1.2-9 (>= 3.1.3.1) which is a virtual package.
               Depends: libedataserver1.2-14 (>= 3.1.3.1) but it is not going to be installed.
               Depends: libedataserverui-3.0-1 (>= 3.1.3.1) which is a virtual package.
               Depends: libgnome-desktop-3-2 (>= 2.91.5) which is a virtual package.
               Depends: libmozjs185-1.0 (>= 1.8.5~hg20110306r6) which is a virtual package.
               Depends: gnome-settings-daemon (>= 2.91.5.1) but it is not going to be installed.
               Depends: gir1.2-gkbd-3.0 which is a virtual package.
               Depends: gir1.2-gnomebluetooth-1.0 which is a virtual package.
               Depends: gir1.2-networkmanager-1.0 which is a virtual package.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] nn

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
root@KanotixBox:/home/keith# aptitude update
Hit http://www.debian-multimedia.org testing Release.gpg
Ign http://www.debian-multimedia.org/ testing/main Translation-en
Ign http://www.debian-multimedia.org/ testing/main Translation-en_US
Ign http://www.debian-multimedia.org/ testing/non-free Translation-en
Ign http://www.debian-multimedia.org/ testing/non-free Translation-en_US
Hit http://ppa.launchpad.net oneiric Release.gpg                                
Ign http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main Translation-en 
Ign http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main Translation-en_US
Hit http://kanotix.acritox.com trialshot Release.gpg                            
Ign http://kanotix.acritox.com/debian/ trialshot/main Translation-en            
Hit http://kanotix.com ./ Release.gpg                                           
Ign http://kanotix.com/files/excalibur/ ./ Translation-en                       
Hit http://www.debian-multimedia.org testing Release                            
Hit http://ppa.launchpad.net oneiric Release.gpg                                
Ign http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ oneiric/main Translation-en
Ign http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ oneiric/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                  
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en  
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net oneiric Release                                    
Hit http://ftp.de.debian.org squeeze Release.gpg                                
Ign http://ftp.de.debian.org/debian/ squeeze/contrib Translation-en             
Ign http://ftp.de.debian.org/debian/ squeeze/contrib Translation-en_US          
Ign http://kanotix.acritox.com/debian/ trialshot/main Translation-en_US         
Hit http://kanotix.acritox.com trialshot Release                                
Ign http://kanotix.com/files/excalibur/ ./ Translation-en_US                    
Hit http://kanotix.com ./ Release.gpg                                           
Ign http://kanotix.com/files/hellfire/ ./ Translation-en                        
Ign http://kanotix.com/files/hellfire/ ./ Translation-en_US                     
Hit http://kanotix.com ./ Release.gpg                                           
Ign http://kanotix.com/files/fix/lo/ ./ Translation-en                          
Ign http://kanotix.com/files/fix/lo/ ./ Translation-en_US                       
Hit http://kanotix.com ./ Release                                               
Hit http://ftp.debian.org testing Release.gpg                                   
Ign http://ftp.debian.org/debian/ testing/contrib Translation-en                
Ign http://ftp.debian.org/debian/ testing/contrib Translation-en_US             
Ign http://ftp.de.debian.org/debian/ squeeze/main Translation-en                
Ign http://ftp.de.debian.org/debian/ squeeze/main Translation-en_US             
Ign http://ftp.de.debian.org/debian/ squeeze/non-free Translation-en            
Ign http://ftp.de.debian.org/debian/ squeeze/non-free Translation-en_US         
Hit http://ppa.launchpad.net oneiric Release                                    
Hit http://ppa.launchpad.net lucid Release                                      
Ign http://ftp.debian.org/debian/ testing/main Translation-en                   
Ign http://ftp.debian.org/debian/ testing/main Translation-en_US                
Ign http://ftp.debian.org/debian/ testing/non-free Translation-en               
Ign http://ftp.debian.org/debian/ testing/non-free Translation-en_US            
Hit http://ftp.debian.org unstable Release.gpg                                  
Ign http://ftp.debian.org/debian/ unstable/contrib Translation-en               
Ign http://ftp.debian.org/debian/ unstable/contrib Translation-en_US            
Hit http://kanotix.com ./ Release                                               
Hit http://kanotix.com ./ Release                                               
Hit http://ftp.de.debian.org squeeze Release                                    
Ign http://ftp.debian.org/debian/ unstable/main Translation-en                  
Ign http://ftp.debian.org/debian/ unstable/main Translation-en_US               
Ign http://ftp.debian.org/debian/ unstable/non-free Translation-en              
Get:1 http://packages.linuxmint.com debian Release.gpg [198 B]                  
Ign http://packages.linuxmint.com/ debian/import Translation-en                 
Ign http://packages.linuxmint.com/ debian/import Translation-en_US              
Ign http://packages.linuxmint.com/ debian/main Translation-en                   
Ign http://ftp.debian.org/debian/ unstable/non-free Translation-en_US           
Get:2 http://ftp.debian.org experimental Release.gpg [836 B]                    
Ign http://ftp.debian.org/debian/ experimental/contrib Translation-en           
Ign http://ftp.debian.org/debian/ experimental/contrib Translation-en_US        
Ign http://ftp.debian.org/debian/ experimental/main Translation-en              
Ign http://ftp.debian.org/debian/ experimental/main Translation-en_US           
Ign http://ftp.debian.org/debian/ experimental/non-free Translation-en          
Ign http://ftp.debian.org/debian/ experimental/non-free Translation-en_US       
Hit http://ftp.debian.org testing Release                                       
Hit http://ftp.debian.org unstable Release                                      
Hit http://www.debian-multimedia.org testing/main i386 Packages/DiffIndex       
Hit http://ppa.launchpad.net oneiric/main Sources                               
Get:3 http://ftp.debian.org experimental Release [138 kB]                       
Ign http://packages.linuxmint.com/ debian/main Translation-en_US                
Ign http://packages.linuxmint.com/ debian/upstream Translation-en               
Ign http://packages.linuxmint.com/ debian/upstream Translation-en_US            
Hit http://www.debian-multimedia.org testing/non-free i386 Packages/DiffIndex   
Get:4 http://packages.linuxmint.com debian Release [12.1 kB]                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages                         
Hit http://kanotix.acritox.com trialshot/main Sources                           
Ign http://kanotix.com ./ Sources                                               
Hit http://kanotix.acritox.com trialshot/main i386 Packages                     
Hit http://ppa.launchpad.net oneiric/main i386 Packages                         
Ign http://kanotix.com ./ Packages                                              
Hit http://ppa.launchpad.net lucid/main Sources                                 
Hit http://ppa.launchpad.net lucid/main i386 Packages                           
Hit http://kanotix.com ./ Sources                                               
Ign http://kanotix.com ./ Sources                                               
Ign http://kanotix.com ./ Packages                                              
Hit http://ftp.de.debian.org squeeze/main Sources                               
Hit http://kanotix.com ./ Packages                                              
Ign http://kanotix.com ./ Packages                                              
Hit http://kanotix.com ./ Sources                                               
Hit http://ftp.debian.org testing/main i386 Packages/DiffIndex                  
Hit http://ftp.debian.org testing/contrib i386 Packages/DiffIndex               
Hit http://ftp.debian.org testing/non-free i386 Packages/DiffIndex              
Hit http://ftp.de.debian.org squeeze/contrib Sources                            
Hit http://ftp.de.debian.org squeeze/non-free Sources                           
Hit http://ftp.de.debian.org squeeze/main i386 Packages                         
Hit http://ftp.de.debian.org squeeze/contrib i386 Packages                      
Hit http://ftp.de.debian.org squeeze/non-free i386 Packages                     
Hit http://kanotix.com ./ Packages                                              
Hit http://kanotix.com ./ Packages                                              
Hit http://ftp.debian.org unstable/main Sources/DiffIndex                       
Ign http://packages.linuxmint.com debian/main i386 Packages                     
Hit http://ftp.debian.org unstable/contrib Sources/DiffIndex                    
Hit http://ftp.debian.org unstable/non-free Sources/DiffIndex                   
Hit http://ftp.debian.org unstable/main i386 Packages/DiffIndex                 
Hit http://ftp.debian.org unstable/contrib i386 Packages/DiffIndex              
Hit http://ftp.debian.org unstable/non-free i386 Packages/DiffIndex             
Hit http://security.debian.org testing/updates Release.gpg                      
Ign http://security.debian.org/ testing/updates/contrib Translation-en          
Ign http://security.debian.org/ testing/updates/contrib Translation-en_US       
Ign http://security.debian.org/ testing/updates/main Translation-en             
Ign http://security.debian.org/ testing/updates/main Translation-en_US          
Ign http://security.debian.org/ testing/updates/non-free Translation-en         
Ign http://security.debian.org/ testing/updates/non-free Translation-en_US      
Hit http://security.debian.org squeeze/updates Release.gpg                      
Ign http://security.debian.org/ squeeze/updates/contrib Translation-en          
Ign http://security.debian.org/ squeeze/updates/contrib Translation-en_US       
Get:5 http://ftp.debian.org experimental/main Sources [189 kB]                  
Ign http://security.debian.org/ squeeze/updates/main Translation-en             
Ign http://security.debian.org/ squeeze/updates/main Translation-en_US    
Ign http://security.debian.org/ squeeze/updates/non-free Translation-en   
Ign http://security.debian.org/ squeeze/updates/non-free Translation-en_US
Hit http://security.debian.org testing/updates Release                    
Hit http://security.debian.org squeeze/updates Release                    
Ign http://packages.linuxmint.com debian/upstream i386 Packages                 
Ign http://packages.linuxmint.com debian/import i386 Packages              
Get:6 http://packages.linuxmint.com debian/main i386 Packages [9,149 B]         
Get:7 http://ftp.debian.org experimental/contrib Sources [2,620 B]              
Get:8 http://packages.linuxmint.com debian/upstream i386 Packages [5,208 B]     
Get:9 http://ftp.debian.org experimental/non-free Sources [2,721 B]             
Get:10 http://ftp.debian.org experimental/main i386 Packages [412 kB]           
Hit http://security.debian.org testing/updates/main i386 Packages               
Hit http://security.debian.org testing/updates/contrib i386 Packages            
Hit http://security.debian.org testing/updates/non-free i386 Packages           
Hit http://security.debian.org squeeze/updates/main Sources                     
Hit http://security.debian.org squeeze/updates/contrib Sources                  
Hit http://security.debian.org squeeze/updates/non-free Sources                 
Hit http://security.debian.org squeeze/updates/main i386 Packages               
Hit http://security.debian.org squeeze/updates/contrib i386 Packages            
Hit http://security.debian.org squeeze/updates/non-free i386 Packages           
Get:11 http://packages.linuxmint.com debian/import i386 Packages [19.3 kB]      
Get:12 http://ftp.debian.org experimental/contrib i386 Packages [4,249 B]       
Get:13 http://ftp.debian.org experimental/non-free i386 Packages [4,975 B]      
Fetched 800 kB in 8s (93.2 kB/s)                                                
                            
Current status: 35935 new [+531].
root@KanotixBox:/home/keith# aptitude install gnome-shell
The following NEW packages will be installed:
  dconf-gsettings-backend{a} gconf2{a} gir1.2-atk-1.0{a} 
  gir1.2-clutter-1.0{a} gir1.2-freedesktop{a} gir1.2-gconf-2.0{a} 
  gir1.2-gdkpixbuf-2.0{a} gir1.2-gkbd-3.0{a} gir1.2-glib-2.0{a} 
  gir1.2-gnomebluetooth-1.0{a} gir1.2-gtk-3.0{a} gir1.2-json-1.0{a} 
  gir1.2-mutter-3.0{a} gir1.2-networkmanager-1.0{a} gir1.2-pango-1.0{a} 
  gir1.2-polkit-1.0{a} gir1.2-soup-2.4{a} gir1.2-telepathyglib-0.12{a} 
  gir1.2-telepathylogger-0.2{a} gir1.2-upowerglib-1.0{a} gjs{a} 
  gnome-icon-theme{a} gnome-icon-theme-symbolic{a} gnome-shell{b} 
  libcairo-gobject2{a} libcanberra-gtk3-0{a} libcanberra0{a} 
  libclutter-1.0-0{a} libgirepository-1.0-1{a} libgjs0b{a} 
  libgnome-bluetooth8{a} libgnome-menu2{a} libgnomekbd7{ab} libgtk-3-0{a} 
  libgtk-3-bin{a} libgtk-3-common{a} libjson-glib-1.0-0{a} libmozjs5d{a} 
  libmutter0{a} libnm-glib4{a} libnm-util2{a} librsvg2-common{a} 
  libsoup-gnome2.4-1{a} libtdb1{a} libtelepathy-glib0{a} 
  libtelepathy-logger2{a} libupower-glib1{a} mutter-common{a} pkg-config{a} 
  sgml-base{a} 
The following packages will be upgraded:
  libxklavier16 
The following packages are RECOMMENDED but will NOT be installed:
  gnome-control-center libcanberra-gtk3-module libclutter-1.0-common 
1 packages upgraded, 50 newly installed, 0 to remove and 774 not upgraded.
Need to get 32.6 MB of archives. After unpacking 76.5 MB will be used.
The following packages have unmet dependencies:
  libgnomekbd7: Depends: libgnomekbd-common (>= 3.0.0.1-1) but it is not going to be installed.
  gnome-shell: Depends: gnome-bluetooth (>= 3.0.0) but it is not going to be installed.
               Depends: libecal1.2-9 (>= 3.1.3.1) which is a virtual package.
               Depends: libedataserver1.2-14 (>= 3.1.3.1) but it is not going to be installed.
               Depends: libedataserverui-3.0-1 (>= 3.1.3.1) which is a virtual package.
               Depends: libgnome-desktop-3-2 (>= 2.91.5) which is a virtual package.
               Depends: libmozjs185-1.0 (>= 1.8.5~hg20110306r6) which is a virtual package.
               Depends: gnome-settings-daemon (>= 2.91.5.1) but it is not going to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gir1.2-gkbd-3.0 [Not Installed]                    
2)     gnome-shell [Not Installed]                        
3)     libgnomekbd7 [Not Installed]                       



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Install the following packages:                      
1)     libgnomekbd-common [3.0.0.1-1 (experimental)]      

     Keep the following packages at their current version:
2)     gnome-shell [Not Installed]                        



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

      Install the following packages:                        
1)      evolution-data-server-common [3.0.0-1 (experimental)]
2)      gnome-bluetooth [3.0.0-1 (experimental)]             
3)      gnome-desktop3-data [3.0.2-2 (testing, unstable)]    
4)      gnome-settings-daemon [3.0.2-1 (experimental)]       
5)      gnome-shell [3.0.2-1+b1 (experimental)]              
6)      libcamel-1.2-23 [3.0.0-1 (experimental)]             
7)      libcamel1.2-19 [2.32.3-1 (testing, unstable)]        
8)      libebook1.2-10 [3.0.0-1 (experimental)]              
9)      libecal1.2-8 [2.32.3-1 (testing, unstable)]          
10)     libedataserver1.2-14 [3.0.0-1 (experimental)]        
11)     libedataserverui-3.0-0 [3.0.0-1 (experimental)]      
12)     libgdata-common [0.6.4-3 (testing, unstable)]        
13)     libgdata7 [0.6.4-3 (testing, unstable)]              
14)     libgnome-control-center1 [1:3.0.1.1-1 (experimental)]
15)     libgnome-desktop-3-0 [3.0.2-2 (testing, unstable)]   
16)     libgnome2-common [2.32.1-1 (testing, unstable)]      
17)     libgnomekbd-common [3.0.0.1-1 (experimental)]        
18)     libnotify4 [0.7.3-2 (unstable)]                      
19)     nautilus-data [3.0.2-2 (experimental)]               



Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  dconf-gsettings-backend{a} evolution-data-server-common{a} gconf2{a} 
  gir1.2-atk-1.0{a} gir1.2-clutter-1.0{a} gir1.2-freedesktop{a} 
  gir1.2-gconf-2.0{a} gir1.2-gdkpixbuf-2.0{a} gir1.2-gkbd-3.0{a} 
  gir1.2-glib-2.0{a} gir1.2-gnomebluetooth-1.0{a} gir1.2-gtk-3.0{a} 
  gir1.2-json-1.0{a} gir1.2-mutter-3.0{a} gir1.2-networkmanager-1.0{a} 
  gir1.2-pango-1.0{a} gir1.2-polkit-1.0{a} gir1.2-telepathyglib-0.12{a} 
  gir1.2-telepathylogger-0.2{a} gir1.2-upowerglib-1.0{a} gjs{a} 
  gnome-bluetooth{a} gnome-desktop3-data{a} gnome-icon-theme{a} 
  gnome-icon-theme-symbolic{a} gnome-settings-daemon{a} gnome-shell 
  libcairo-gobject2{a} libcamel-1.2-23{a} libcamel1.2-19{a} 
  libcanberra-gtk3-0{a} libcanberra0{a} libclutter-1.0-0{a} 
  libebook1.2-10{a} libecal1.2-8{a} libedataserver1.2-14{a} 
  libedataserverui-3.0-0{a} libgdata-common{a} libgdata7{a} 
  libgirepository-1.0-1{a} libgjs0b{a} libgnome-bluetooth8{a} 
  libgnome-control-center1{a} libgnome-desktop-3-0{a} libgnome-menu2{a} 
  libgnome2-common{a} libgnomekbd-common{a} libgnomekbd7{a} libgtk-3-0{a} 
  libgtk-3-bin{a} libgtk-3-common{a} libjson-glib-1.0-0{a} libmozjs5d{a} 
  libmutter0{a} libnm-glib4{a} libnm-util2{a} libnotify4{a} 
  librsvg2-common{a} libsoup-gnome2.4-1{a} libtdb1{a} libtelepathy-glib0{a} 
  libtelepathy-logger2{a} libupower-glib1{a} mutter-common{a} 
  nautilus-data{a} pkg-config{a} sgml-base{a} 
The following packages will be upgraded:
  libxklavier16 
The following packages are RECOMMENDED but will NOT be installed:
  gnome-control-center gvfs-backends hwdata libcanberra-gtk3-module 
  libclutter-1.0-common nautilus notification-daemon 
  notification-daemon-xfce notify-osd pulseaudio xfce4-notifyd 
1 packages upgraded, 67 newly installed, 0 to remove and 774 not upgraded.
Need to get 47.6 MB of archives. After unpacking 125 MB will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main libclutter-1.0-0 i386 1.6.18~git20110718.e0e9c3fc-0ubuntu1~11.10~ricotz0 [849 kB]
Get:2 http://ftp.debian.org/debian/ unstable/main libcairo-gobject2 i386 1.10.2-6.1 [589 kB]
Get:3 http://ftp.debian.org/debian/ testing/main libjson-glib-1.0-0 i386 0.13.4-2 [133 kB]
Get:4 http://ftp.debian.org/debian/ unstable/main libtdb1 i386 1.2.9-3 [39.7 kB]
Get:5 http://ftp.debian.org/debian/ testing/main dconf-gsettings-backend i386 0.7.5-3 [35.4 kB]
Get:6 http://ftp.debian.org/debian/ experimental/main evolution-data-server-common all 3.0.0-1 [2,378 kB]
Get:7 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main gir1.2-clutter-1.0 i386 1.6.18~git20110718.e0e9c3fc-0ubuntu1~11.10~ricotz0 [393 kB]
Get:8 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main mutter-common all 3.1.3.1+git20110719.fccd6266-0ubuntu1~11.10~ricotz0 [1,549 kB]
Get:9 http://ftp.debian.org/debian/ testing/main gconf2 i386 2.32.4-1 [175 kB]  
Get:10 http://ftp.debian.org/debian/ testing/main libgirepository-1.0-1 i386 0.10.8-2 [107 kB]
Get:11 http://ftp.debian.org/debian/ testing/main gir1.2-glib-2.0 i386 0.10.8-2 [150 kB]
Get:12 http://ftp.debian.org/debian/ testing/main gir1.2-atk-1.0 i386 2.0.1-2 [62.9 kB]
Get:13 http://ftp.debian.org/debian/ testing/main gir1.2-freedesktop i386 0.10.8-2 [18.9 kB]
Get:14 http://ftp.debian.org/debian/ testing/main gir1.2-json-1.0 i386 0.13.4-2 [77.9 kB]
Get:15 http://ftp.debian.org/debian/ unstable/main gir1.2-pango-1.0 i386 1.28.4-2 [128 kB]
Get:16 http://ftp.debian.org/debian/ testing/main gir1.2-gconf-2.0 i386 2.32.4-1 [103 kB]
Get:17 http://ftp.debian.org/debian/ unstable/main gir1.2-gdkpixbuf-2.0 i386 2.23.5-3 [13.6 kB]
Get:18 http://ftp.debian.org/debian/ unstable/main libgtk-3-common all 3.0.12-1 [7,099 kB]
Get:19 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main libmutter0 i386 3.1.3.1+git20110719.fccd6266-0ubuntu1~11.10~ricotz0 [555 kB]
Get:20 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main gir1.2-mutter-3.0 i386 3.1.3.1+git20110719.fccd6266-0ubuntu1~11.10~ricotz0 [234 kB]
Get:21 http://ftp.debian.org/debian/ unstable/main libgtk-3-0 i386 3.0.12-1 [3,275 kB]
Get:22 http://ftp.debian.org/debian/ unstable/main gir1.2-gtk-3.0 i386 3.0.12-1 [1,390 kB]
Get:23 http://ftp.debian.org/debian/ testing/main libxklavier16 i386 5.1-2 [65.9 kB]
Get:24 http://ftp.debian.org/debian/ experimental/main libgnomekbd-common all 3.0.0.1-1 [110 kB]
Get:25 http://ftp.debian.org/debian/ experimental/main libgnomekbd7 i386 3.0.0.1-1 [61.7 kB]
Get:26 http://ftp.debian.org/debian/ experimental/main gir1.2-gkbd-3.0 i386 3.0.0.1-1 [13.7 kB]
Get:27 http://ftp.debian.org/debian/ experimental/main libgnome-bluetooth8 i386 3.0.0-1 [183 kB]
Get:28 http://ftp.debian.org/debian/ experimental/main gir1.2-gnomebluetooth-1.0 i386 3.0.0-1 [148 kB]
Get:29 http://ftp.debian.org/debian/ testing/main libcanberra0 i386 0.28-1 [42.8 kB]
Get:30 http://ftp.debian.org/debian/ testing/main libcanberra-gtk3-0 i386 0.28-1 [15.1 kB]
Get:31 http://ftp.debian.org/debian/ testing/main sgml-base all 1.26+nmu1 [11.9 kB]
Get:32 http://ftp.debian.org/debian/ experimental/main libnm-util2 i386 0.8.9997-1 [339 kB]
Get:33 http://ftp.debian.org/debian/ experimental/main libnm-glib4 i386 0.8.9997-1 [302 kB]
Get:34 http://ftp.debian.org/debian/ experimental/main gir1.2-networkmanager-1.0 i386 0.8.9997-1 [260 kB]
Get:35 http://ftp.debian.org/debian/ unstable/main gir1.2-polkit-1.0 i386 0.102-1 [14.0 kB]
Get:36 http://ftp.debian.org/debian/ testing/main libtelepathy-glib0 i386 0.15.4-1 [803 kB]
Get:37 http://ftp.debian.org/debian/ testing/main gir1.2-telepathyglib-0.12 i386 0.15.4-1 [45.8 kB]
Get:38 http://ftp.debian.org/debian/ testing/main libtelepathy-logger2 i386 0.2.10-2 [83.3 kB]
Get:39 http://ftp.debian.org/debian/ testing/main gir1.2-telepathylogger-0.2 i386 0.2.10-2 [6,020 B]
Get:40 http://ftp.debian.org/debian/ testing/main libupower-glib1 i386 0.9.12-1 [33.4 kB]
Get:41 http://ftp.debian.org/debian/ testing/main gir1.2-upowerglib-1.0 i386 0.9.12-1 [12.6 kB]
Get:42 http://ftp.debian.org/debian/ unstable/main libmozjs5d i386 5.0-6 [1,410 kB]
Get:43 http://ftp.debian.org/debian/ unstable/main libgjs0b i386 1.29.0-1 [217 kB]
Get:44 http://ftp.debian.org/debian/ unstable/main gjs i386 1.29.0-1 [12.8 kB]  
Get:45 http://ftp.debian.org/debian/ experimental/main libgnome-control-center1 i386 1:3.0.1.1-1 [1,277 kB]
Get:46 http://ftp.debian.org/debian/ unstable/main libnotify4 i386 0.7.3-2 [30.1 kB]
Get:47 http://ftp.debian.org/debian/ experimental/main gnome-bluetooth i386 3.0.0-1 [989 kB]
Get:48 http://ftp.debian.org/debian/ testing/main gnome-desktop3-data all 3.0.2-2 [308 kB]
Get:49 http://ftp.debian.org/debian/ unstable/main libgtk-3-bin all 3.0.12-1 [1,182 kB]
Get:50 http://ftp.debian.org/debian/ unstable/main librsvg2-common i386 2.34.0-2 [70.5 kB]
Get:51 http://ftp.debian.org/debian/ testing/main gnome-icon-theme all 3.0.0-4 [8,978 kB]
Get:52 http://ftp.debian.org/debian/ testing/main gnome-icon-theme-symbolic all 3.0.0-2 [166 kB]
Get:53 http://ftp.debian.org/debian/ testing/main libgnome-desktop-3-0 i386 3.0.2-2 [146 kB]
Get:54 http://ftp.debian.org/debian/ testing/main libgnome2-common all 2.32.1-1 [1,616 kB]
Get:55 http://ftp.debian.org/debian/ experimental/main nautilus-data all 3.0.2-2 [4,191 kB]
Get:56 http://ftp.debian.org/debian/ experimental/main gnome-settings-daemon i386 3.0.2-1 [1,304 kB]
Get:57 http://ftp.debian.org/debian/ experimental/main libedataserver1.2-14 i386 3.0.0-1 [300 kB]
Get:58 http://ftp.debian.org/debian/ testing/main libcamel1.2-19 i386 2.32.3-1 [576 kB]
Get:59 http://ftp.debian.org/debian/ experimental/main libcamel-1.2-23 i386 3.0.0-1 [634 kB]
Get:60 http://ftp.debian.org/debian/ experimental/main libebook1.2-10 i386 3.0.0-1 [319 kB]
Get:61 http://ftp.debian.org/debian/ unstable/main libsoup-gnome2.4-1 i386 2.34.3-1 [42.3 kB]
Get:62 http://ftp.debian.org/debian/ testing/main libgdata-common all 0.6.4-3 [102 kB]
Get:63 http://ftp.debian.org/debian/ testing/main libgdata7 i386 0.6.4-3 [219 kB]
Get:64 http://ftp.debian.org/debian/ testing/main libecal1.2-8 i386 2.32.3-1 [296 kB]
Get:65 http://ftp.debian.org/debian/ experimental/main libedataserverui-3.0-0 i386 3.0.0-1 [326 kB]
Get:66 http://ftp.debian.org/debian/ testing/main libgnome-menu2 i386 2.30.3-2+b1 [71.4 kB]
Get:67 http://ftp.debian.org/debian/ testing/main pkg-config i386 0.26-1 [58.7 kB]
Get:68 http://ftp.debian.org/debian/ experimental/main gnome-shell i386 3.0.2-1+b1 [870 kB]
Fetched 47.6 MB in 51s (931 kB/s)                                               
Extracting templates from packages: 100%
Selecting previously deselected package libcairo-gobject2.
(Reading database ... 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed.
(Reading database ... 104707 files and directories currently installed.)
Unpacking libcairo-gobject2 (from .../libcairo-gobject2_1.10.2-6.1_i386.deb) ...
Selecting previously deselected package libjson-glib-1.0-0.
Unpacking libjson-glib-1.0-0 (from .../libjson-glib-1.0-0_0.13.4-2_i386.deb) ...
Selecting previously deselected package libclutter-1.0-0.
Unpacking libclutter-1.0-0 (from .../libclutter-1.0-0_1.6.18~git20110718.e0e9c3fc-0ubuntu1~11.10~ricotz0_i386.deb) ...
Selecting previously deselected package libtdb1.
Unpacking libtdb1 (from .../libtdb1_1.2.9-3_i386.deb) ...
Selecting previously deselected package dconf-gsettings-backend.
Unpacking dconf-gsettings-backend (from .../dconf-gsettings-backend_0.7.5-3_i386.deb) ...
Selecting previously deselected package evolution-data-server-common.
Unpacking evolution-data-server-common (from .../evolution-data-server-common_3.0.0-1_all.deb) ...
Selecting previously deselected package gconf2.
Unpacking gconf2 (from .../gconf2_2.32.4-1_i386.deb) ...
Selecting previously deselected package libgirepository-1.0-1.
Unpacking libgirepository-1.0-1 (from .../libgirepository-1.0-1_0.10.8-2_i386.deb) ...
Selecting previously deselected package gir1.2-glib-2.0.
Unpacking gir1.2-glib-2.0 (from .../gir1.2-glib-2.0_0.10.8-2_i386.deb) ...
Selecting previously deselected package gir1.2-atk-1.0.
Unpacking gir1.2-atk-1.0 (from .../gir1.2-atk-1.0_2.0.1-2_i386.deb) ...
Selecting previously deselected package gir1.2-freedesktop.
Unpacking gir1.2-freedesktop (from .../gir1.2-freedesktop_0.10.8-2_i386.deb) ...
Selecting previously deselected package gir1.2-json-1.0.
Unpacking gir1.2-json-1.0 (from .../gir1.2-json-1.0_0.13.4-2_i386.deb) ...
Selecting previously deselected package gir1.2-pango-1.0.
Unpacking gir1.2-pango-1.0 (from .../gir1.2-pango-1.0_1.28.4-2_i386.deb) ...
Selecting previously deselected package gir1.2-clutter-1.0.
Unpacking gir1.2-clutter-1.0 (from .../gir1.2-clutter-1.0_1.6.18~git20110718.e0e9c3fc-0ubuntu1~11.10~ricotz0_i386.deb) ...
Selecting previously deselected package gir1.2-gconf-2.0.
Unpacking gir1.2-gconf-2.0 (from .../gir1.2-gconf-2.0_2.32.4-1_i386.deb) ...
Selecting previously deselected package gir1.2-gdkpixbuf-2.0.
Unpacking gir1.2-gdkpixbuf-2.0 (from .../gir1.2-gdkpixbuf-2.0_2.23.5-3_i386.deb) ...
Selecting previously deselected package libgtk-3-common.
Unpacking libgtk-3-common (from .../libgtk-3-common_3.0.12-1_all.deb) ...
Selecting previously deselected package libgtk-3-0.
Unpacking libgtk-3-0 (from .../libgtk-3-0_3.0.12-1_i386.deb) ...
Selecting previously deselected package gir1.2-gtk-3.0.
Unpacking gir1.2-gtk-3.0 (from .../gir1.2-gtk-3.0_3.0.12-1_i386.deb) ...
Preparing to replace libxklavier16 5.0-2 (using .../libxklavier16_5.1-2_i386.deb) ...
Unpacking replacement libxklavier16 ...
Selecting previously deselected package libgnomekbd-common.
Unpacking libgnomekbd-common (from .../libgnomekbd-common_3.0.0.1-1_all.deb) ...
Selecting previously deselected package libgnomekbd7.
Unpacking libgnomekbd7 (from .../libgnomekbd7_3.0.0.1-1_i386.deb) ...
Selecting previously deselected package gir1.2-gkbd-3.0.
Unpacking gir1.2-gkbd-3.0 (from .../gir1.2-gkbd-3.0_3.0.0.1-1_i386.deb) ...
Selecting previously deselected package libgnome-bluetooth8.
Unpacking libgnome-bluetooth8 (from .../libgnome-bluetooth8_3.0.0-1_i386.deb) ...
Selecting previously deselected package gir1.2-gnomebluetooth-1.0.
Unpacking gir1.2-gnomebluetooth-1.0 (from .../gir1.2-gnomebluetooth-1.0_3.0.0-1_i386.deb) ...
Selecting previously deselected package libcanberra0.
Unpacking libcanberra0 (from .../libcanberra0_0.28-1_i386.deb) ...
Selecting previously deselected package libcanberra-gtk3-0.
Unpacking libcanberra-gtk3-0 (from .../libcanberra-gtk3-0_0.28-1_i386.deb) ...
Selecting previously deselected package sgml-base.
Unpacking sgml-base (from .../sgml-base_1.26+nmu1_all.deb) ...
Selecting previously deselected package mutter-common.
Unpacking mutter-common (from .../mutter-common_3.1.3.1+git20110719.fccd6266-0ubuntu1~11.10~ricotz0_all.deb) ...
Selecting previously deselected package libmutter0.
Unpacking libmutter0 (from .../libmutter0_3.1.3.1+git20110719.fccd6266-0ubuntu1~11.10~ricotz0_i386.deb) ...
Selecting previously deselected package gir1.2-mutter-3.0.
Unpacking gir1.2-mutter-3.0 (from .../gir1.2-mutter-3.0_3.1.3.1+git20110719.fccd6266-0ubuntu1~11.10~ricotz0_i386.deb) ...
Selecting previously deselected package libnm-util2.
Unpacking libnm-util2 (from .../libnm-util2_0.8.9997-1_i386.deb) ...
Selecting previously deselected package libnm-glib4.
Unpacking libnm-glib4 (from .../libnm-glib4_0.8.9997-1_i386.deb) ...
Selecting previously deselected package gir1.2-networkmanager-1.0.
Unpacking gir1.2-networkmanager-1.0 (from .../gir1.2-networkmanager-1.0_0.8.9997-1_i386.deb) ...
Selecting previously deselected package gir1.2-polkit-1.0.
Unpacking gir1.2-polkit-1.0 (from .../gir1.2-polkit-1.0_0.102-1_i386.deb) ...
Selecting previously deselected package libtelepathy-glib0.
Unpacking libtelepathy-glib0 (from .../libtelepathy-glib0_0.15.4-1_i386.deb) ...
Selecting previously deselected package gir1.2-telepathyglib-0.12.
Unpacking gir1.2-telepathyglib-0.12 (from .../gir1.2-telepathyglib-0.12_0.15.4-1_i386.deb) ...
Selecting previously deselected package libtelepathy-logger2.
Unpacking libtelepathy-logger2 (from .../libtelepathy-logger2_0.2.10-2_i386.deb) ...
Selecting previously deselected package gir1.2-telepathylogger-0.2.
Unpacking gir1.2-telepathylogger-0.2 (from .../gir1.2-telepathylogger-0.2_0.2.10-2_i386.deb) ...
Selecting previously deselected package libupower-glib1.
Unpacking libupower-glib1 (from .../libupower-glib1_0.9.12-1_i386.deb) ...
Selecting previously deselected package gir1.2-upowerglib-1.0.
Unpacking gir1.2-upowerglib-1.0 (from .../gir1.2-upowerglib-1.0_0.9.12-1_i386.deb) ...
Selecting previously deselected package libmozjs5d.
Unpacking libmozjs5d (from .../libmozjs5d_5.0-6_i386.deb) ...
Selecting previously deselected package libgjs0b.
Unpacking libgjs0b (from .../libgjs0b_1.29.0-1_i386.deb) ...
Selecting previously deselected package gjs.
Unpacking gjs (from .../archives/gjs_1.29.0-1_i386.deb) ...
Selecting previously deselected package libgnome-control-center1.
Unpacking libgnome-control-center1 (from .../libgnome-control-center1_1%3a3.0.1.1-1_i386.deb) ...
Selecting previously deselected package libnotify4.
Unpacking libnotify4 (from .../libnotify4_0.7.3-2_i386.deb) ...
Selecting previously deselected package gnome-bluetooth.
Unpacking gnome-bluetooth (from .../gnome-bluetooth_3.0.0-1_i386.deb) ...
Selecting previously deselected package gnome-desktop3-data.
Unpacking gnome-desktop3-data (from .../gnome-desktop3-data_3.0.2-2_all.deb) ...
Selecting previously deselected package libgtk-3-bin.
Unpacking libgtk-3-bin (from .../libgtk-3-bin_3.0.12-1_all.deb) ...
Adding 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Adding 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Selecting previously deselected package librsvg2-common.
Unpacking librsvg2-common (from .../librsvg2-common_2.34.0-2_i386.deb) ...
Selecting previously deselected package gnome-icon-theme.
Unpacking gnome-icon-theme (from .../gnome-icon-theme_3.0.0-4_all.deb) ...
Selecting previously deselected package gnome-icon-theme-symbolic.
Unpacking gnome-icon-theme-symbolic (from .../gnome-icon-theme-symbolic_3.0.0-2_all.deb) ...
Selecting previously deselected package libgnome-desktop-3-0.
Unpacking libgnome-desktop-3-0 (from .../libgnome-desktop-3-0_3.0.2-2_i386.deb) ...
Selecting previously deselected package libgnome2-common.
Unpacking libgnome2-common (from .../libgnome2-common_2.32.1-1_all.deb) ...
Selecting previously deselected package nautilus-data.
Unpacking nautilus-data (from .../nautilus-data_3.0.2-2_all.deb) ...
Selecting previously deselected package gnome-settings-daemon.
Unpacking gnome-settings-daemon (from .../gnome-settings-daemon_3.0.2-1_i386.deb) ...
Selecting previously deselected package libedataserver1.2-14.
Unpacking libedataserver1.2-14 (from .../libedataserver1.2-14_3.0.0-1_i386.deb) ...
Selecting previously deselected package libcamel1.2-19.
Unpacking libcamel1.2-19 (from .../libcamel1.2-19_2.32.3-1_i386.deb) ...
Selecting previously deselected package libcamel-1.2-23.
Unpacking libcamel-1.2-23 (from .../libcamel-1.2-23_3.0.0-1_i386.deb) ...
Selecting previously deselected package libebook1.2-10.
Unpacking libebook1.2-10 (from .../libebook1.2-10_3.0.0-1_i386.deb) ...
Selecting previously deselected package libsoup-gnome2.4-1.
Unpacking libsoup-gnome2.4-1 (from .../libsoup-gnome2.4-1_2.34.3-1_i386.deb) ...
Selecting previously deselected package libgdata-common.
Unpacking libgdata-common (from .../libgdata-common_0.6.4-3_all.deb) ...
Selecting previously deselected package libgdata7.
Unpacking libgdata7 (from .../libgdata7_0.6.4-3_i386.deb) ...
Selecting previously deselected package libecal1.2-8.
Unpacking libecal1.2-8 (from .../libecal1.2-8_2.32.3-1_i386.deb) ...
Selecting previously deselected package libedataserverui-3.0-0.
Unpacking libedataserverui-3.0-0 (from .../libedataserverui-3.0-0_3.0.0-1_i386.deb) ...
Selecting previously deselected package libgnome-menu2.
Unpacking libgnome-menu2 (from .../libgnome-menu2_2.30.3-2+b1_i386.deb) ...
Selecting previously deselected package pkg-config.
Unpacking pkg-config (from .../pkg-config_0.26-1_i386.deb) ...
Selecting previously deselected package gnome-shell.
Unpacking gnome-shell (from .../gnome-shell_3.0.2-1+b1_i386.deb) ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libgdk-pixbuf2.0-0 ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'virtual/bluedevil-input'

Unknown media type in type 'virtual/bluedevil-audio'

Unknown media type in type 'virtual/bluedevil-sendfile'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up libcairo-gobject2 (1.10.2-6.1) ...
Setting up libjson-glib-1.0-0 (0.13.4-2) ...
Setting up libclutter-1.0-0 (1.6.18~git20110718.e0e9c3fc-0ubuntu1~11.10~ricotz0) ...
Setting up libtdb1 (1.2.9-3) ...
Setting up dconf-gsettings-backend (0.7.5-3) ...
Setting up evolution-data-server-common (3.0.0-1) ...
Setting up gconf2 (2.32.4-1) ...
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
WARNING: node <gettext_domain> not understood below <schema>
Setting up libgirepository-1.0-1 (0.10.8-2) ...
Setting up gir1.2-glib-2.0 (0.10.8-2) ...
Setting up gir1.2-atk-1.0 (2.0.1-2) ...
Setting up gir1.2-freedesktop (0.10.8-2) ...
Setting up gir1.2-json-1.0 (0.13.4-2) ...
Setting up gir1.2-pango-1.0 (1.28.4-2) ...
Setting up gir1.2-clutter-1.0 (1.6.18~git20110718.e0e9c3fc-0ubuntu1~11.10~ricotz0) ...
Setting up gir1.2-gconf-2.0 (2.32.4-1) ...
Setting up gir1.2-gdkpixbuf-2.0 (2.23.5-3) ...
Setting up libgtk-3-common (3.0.12-1) ...
Setting up libgtk-3-0 (3.0.12-1) ...
Setting up gir1.2-gtk-3.0 (3.0.12-1) ...
Setting up libxklavier16 (5.1-2) ...
Setting up libgnomekbd-common (3.0.0.1-1) ...
Setting up libgnomekbd7 (3.0.0.1-1) ...
Setting up gir1.2-gkbd-3.0 (3.0.0.1-1) ...
Setting up libgnome-bluetooth8 (3.0.0-1) ...
Setting up gir1.2-gnomebluetooth-1.0 (3.0.0-1) ...
Setting up libcanberra0 (0.28-1) ...
Setting up libcanberra-gtk3-0 (0.28-1) ...
Setting up sgml-base (1.26+nmu1) ...
Setting up mutter-common (3.1.3.1+git20110719.fccd6266-0ubuntu1~11.10~ricotz0) ...
Setting up libmutter0 (3.1.3.1+git20110719.fccd6266-0ubuntu1~11.10~ricotz0) ...
Setting up gir1.2-mutter-3.0 (3.1.3.1+git20110719.fccd6266-0ubuntu1~11.10~ricotz0) ...
Setting up libnm-util2 (0.8.9997-1) ...
Setting up libnm-glib4 (0.8.9997-1) ...
Setting up gir1.2-networkmanager-1.0 (0.8.9997-1) ...
Setting up gir1.2-polkit-1.0 (0.102-1) ...
Setting up libtelepathy-glib0 (0.15.4-1) ...
Setting up gir1.2-telepathyglib-0.12 (0.15.4-1) ...
Setting up libtelepathy-logger2 (0.2.10-2) ...
Setting up gir1.2-telepathylogger-0.2 (0.2.10-2) ...
Setting up libupower-glib1 (0.9.12-1) ...
Setting up gir1.2-upowerglib-1.0 (0.9.12-1) ...
Setting up libmozjs5d (5.0-6) ...
Setting up libgjs0b (1.29.0-1) ...
Setting up gjs (1.29.0-1) ...
Setting up libgnome-control-center1 (1:3.0.1.1-1) ...
Setting up libnotify4 (0.7.3-2) ...
Setting up gnome-bluetooth (3.0.0-1) ...
Setting up gnome-desktop3-data (3.0.2-2) ...
Setting up libgtk-3-bin (3.0.12-1) ...
Setting up librsvg2-common (2.34.0-2) ...
Setting up gnome-icon-theme (3.0.0-4) ...
update-alternatives: using /usr/share/icons/gnome/scalable/places/debian-swirl.svg to provide /usr/share/icons/gnome/scalable/places/start-here.svg (start-here.svg) in auto mode.
Setting up gnome-icon-theme-symbolic (3.0.0-2) ...
Setting up libgnome-desktop-3-0 (3.0.2-2) ...
Setting up libgnome2-common (2.32.1-1) ...
Setting up nautilus-data (3.0.2-2) ...
Setting up gnome-settings-daemon (3.0.2-1) ...
Setting up libedataserver1.2-14 (3.0.0-1) ...
Setting up libcamel1.2-19 (2.32.3-1) ...
Setting up libcamel-1.2-23 (3.0.0-1) ...
Setting up libebook1.2-10 (3.0.0-1) ...
Setting up libsoup-gnome2.4-1 (2.34.3-1) ...
Setting up libgdata-common (0.6.4-3) ...
Setting up libgdata7 (0.6.4-3) ...
Setting up libecal1.2-8 (2.32.3-1) ...
Setting up libedataserverui-3.0-0 (3.0.0-1) ...
Setting up libgnome-menu2 (2.30.3-2+b1) ...
Setting up pkg-config (0.26-1) ...
Setting up gnome-shell (3.0.2-1+b1) ...
                                         
Current status: 774 updates [-1].
root@KanotixBox:/home/keith# 



```Amazing logged out and back in and its all running .... will it stand a reboot ... ;)

wow loaded gnome-themes-standard in and its running

---

### Post by cbowman57 on 2011-08-07
You ever wonder how many people that peek in here probably just scratch their heads & wonder what is going on? :lol:

---

### Post by 23dornot23d on 2011-08-07
Sometimes ...... its a testing ground for grown ups ... lols .... :)

and I have it working amazingly .....


So doing a dist-upgrade after adding missing dependencies now ... 87 % complete ... using testing repos

---

### Post by cbowman57 on 2011-08-07
That's what matters, that we have a good time. ;)

---

### Post by 23dornot23d on 2011-08-07
Ok I carried on with it ..... and a few hours later ... its on my main machine now .... :)

Always enjoy trying to get things solved - got one problem remaining now 

gnome-tweak-tool

something to do with line 20 ..... see screenshot
no module named gi ...... 

got it 

aptitude install pygobject

[**SCREENSHOT FULLSIZE**]("http://img51.imageshack.us/img51/2564/screenshot11sl.jpg")

[IMG]http://img808.imageshack.us/img808/8377/screenshot11sh.jpg[/IMG]

---

### Post by cbowman57 on 2011-08-07
Are you using all debian repositories or did you mix in some Ubuntu?

You might just have a corrupt deb, I'd delete it & download it fresh to be sure.

---

### Post by 23dornot23d on 2011-08-07
> 
Are you using all debian repositories or did you mix in some Ubuntu?
All debian ... except for Mint+Debian ..... and its looking pretty good .... will test it
temps are very low speed is incredibly fast ..... and now for some 3D 

Will load in Wings 3D and Blender ..... and do some rendering ,,,, that should test it
also got to burn a DVD to see if remastersys worked as it should .... I used gdm too
so we may get a proper login as well I hope ...


Its ok was pygobject missing ,,,

[IMG]http://img819.imageshack.us/img819/960/screenshot12se.jpg[/IMG]

Cheers .... everything is pretty good now ... :D

I say pretty good its fantastic speed wise .... having to slow down with the mouse
and the compiz effects when I switch to compiz are amazingly quick



ok loaded in session manager common and two others related to it ...

[IMG]http://img98.imageshack.us/img98/5851/screenshot14s.jpg[/IMG]


We have a winner ..... 

Just one more thing gdebi remastersys ....... see if I can get a snapshot .... its worked

[IMG]http://img27.imageshack.us/img27/5038/rs1bn.jpg[/IMG]


[IMG]http://img52.imageshack.us/img52/1962/screenshot4sg.jpg[/IMG]


Although the DVD burned ok it stopped at the kano script ...... ( I need to look at this )

So no DVD yet .... but I would like to keep this one ...... its got potential ......

---

### Post by cbowman57 on 2011-08-08
Well after having this Gnome 3.0 minimal install process down I've had a chance to compare nearly identical desktops on the different ditros.

My observations so far.

1. Ubuntu is more "user friendly", mostly due to ppa's.
2. Performance based on how it "feels" & resources used, comparable.
3. Stability, even with unstable & experimental repos, I have to give to Debian.

What do you think Keith?

---

### Post by cbowman57 on 2011-08-08
[Link to handy way to duplicate systems that use dpkg.]("http://www.coredump.gr/linux/debian-package-list-backup-and-restore/")

Dpkg-Backup

```
#!/bin/sh
# dpkg-backup.sh
 
dpkg --get-selections > /tmp/dpkg-list.txt


```Dpkg-Restore

```
#!/bin/sh
# dpkg-restore.sh
 
if [ -f /tmp/dpkg-list.txt ]
then
    /usr/bin/dpkg --clear-selections
    /usr/bin/dpkg --set-selections < /tmp/dpkg-list.txt
    /usr/bin/dpkg --get-selections | sed -e \'s/deinstall/purge/\' > /tmp/dpkg-list.txt
    /usr/bin/dpkg --set-selections < /tmp/dpkg-list.txt
    rm /tmp/dpkg-list.txt
    /usr/bin/apt-get dselect-upgrade
else
    echo "You must use dpkg-backup first."
fi


```I relocated the files from /tmp and commented out the **rm**.  With this we can create virtually identical installations with minimal or net installs.  Great for a Gnome only installation.

For instance, with that restore script and this list you could create a duplicate of my gNatty Gnome only installation.

```
accountsservice                    install
acpid                        deinstall
adduser                        install
adobe-flash-properties-gtk            install
adobe-flashplugin                install
alacarte                    install
apg                        install
app-install-data                install
apparmor                    install
apparmor-utils                    install
appmenu-gtk                    install
apt                        install
apt-transport-https                install
apt-utils                    install
apt-xapian-index                install
aptdaemon                    install
aptdaemon-data                    install
aptitude                    install
apturl                        install
apturl-common                    install
aspell                        install
aspell-en                    install
at                        install
bamfdaemon                    install
baobab                        install
base-files                    install
base-passwd                    install
bash                        install
bash-completion                    install
bind9-host                    install
binutils                    install
bluez                        install
brasero                        install
brasero-cdrkit                    install
brasero-common                    install
bridge-utils                    install
bsdmainutils                    install
bsdutils                    install
build-essential                    install
busybox-initramfs                install
busybox-static                    install
bzip2                        install
ca-certificates                    install
ca-certificates-java                install
cabextract                    install
cmap-adobe-japan1                install
command-not-found                install
command-not-found-data                install
compiz-core                    install
compiz-plugins                    install
console-setup                    install
console-terminus                install
consolekit                    install
coreutils                    install
cpio                        install
cpp                        install
cpp-4.5                        install
cpu-checker                    install
cron                        install
customizer                    install
dash                        install
dbus                        install
dbus-x11                    install
dconf-gsettings-backend                install
dconf-tools                    install
debconf                        install
debconf-i18n                    install
debianutils                    install
defoma                        install
desktop-file-utils                install
dictionaries-common                install
diffstat                    install
diffutils                    install
discover                    install
discover-data                    install
dkms                        deinstall
dmidecode                    install
dmsetup                        install
dmz-cursor-theme                install
dnsmasq-base                    install
dnsutils                    install
docbook-xml                    install
dosfstools                    install
dpkg                        install
dpkg-dev                    install
dvd+rw-tools                    install
dvdauthor                    install
e2fslibs                    install
e2fsprogs                    install
ed                        install
eject                        install
empathy-common                    install
eog                        install
evolution-data-server                install
evolution-data-server-common            install
fakeroot                    install
file                        install
file-roller                    install
findutils                    install
firefox                        install
firefox-gnome-support                install
fontconfig                    install
fontconfig-config                install
freepats                    install
friendly-recovery                install
ftp                        install
fuse-utils                    install
g++                        install
g++-4.5                        install
gambas2-gb-form                    install
gambas2-gb-gtk                    install
gambas2-gb-gui                    install
gambas2-gb-qt                    install
gambas2-gb-settings                install
gambas2-runtime                    install
gamin                        install
gcc                        install
gcc-4.5                        install
gcc-4.5-base                    install
gconf-cleaner                    install
gconf-defaults-service                install
gconf-editor                    install
gconf2                        install
gconf2-common                    install
gdebi                        install
gdebi-core                    install
gdm                        install
gedit                        install
gedit-common                    install
genisoimage                    install
geoip-database                    install
gettext                        install
gettext-base                    install
gfxboot                        install
gfxboot-dev                    install
ghostscript                    install
gir1.2-atk-1.0                    install
gir1.2-clutter-1.0                install
gir1.2-dbusmenu-glib-0.4            install
gir1.2-dee-0.5                    install
gir1.2-freedesktop                install
gir1.2-gconf-2.0                install
gir1.2-gdkpixbuf-2.0                install
gir1.2-gkbd-3.0                    install
gir1.2-glib-2.0                    install
gir1.2-gnomebluetooth-1.0            install
gir1.2-gnomedesktop-3.0                install
gir1.2-gtk-2.0                    install
gir1.2-gtk-3.0                    install
gir1.2-gtksource-3.0                install
gir1.2-json-1.0                    install
gir1.2-mutter-3.0                install
gir1.2-panelapplet-3.0                install
gir1.2-pango-1.0                install
gir1.2-peas-1.0                    install
gir1.2-polkit-1.0                install
gir1.2-soup-2.4                    install
gir1.2-telepathyglib-0.12            install
gir1.2-telepathylogger-0.2            install
gir1.2-unity-3.0                install
gir1.2-upowerglib-1.0                install
gir1.2-vte-0.0                    install
gjs                        install
gksu                        install
glib-networking                    install
gnome-about                    install
gnome-activity-journal                install
gnome-applets                    install
gnome-applets-data                install
gnome-backgrounds                install
gnome-bluetooth                    install
gnome-control-center                install
gnome-control-center-data            install
gnome-desktop-data                install
gnome-desktop3-data                install
gnome-dictionary                install
gnome-disk-utility                install
gnome-doc-utils                    install
gnome-icon-theme                install
gnome-icon-theme-symbolic            install
gnome-keyring                    install
gnome-media                    install
gnome-menus                    install
gnome-mime-data                    install
gnome-panel                    install
gnome-panel-bonobo                install
gnome-panel-data                install
gnome-power-manager                install
gnome-screenshot                install
gnome-search-tool                install
gnome-session                    install
gnome-session-bin                install
gnome-session-canberra                install
gnome-session-common                install
gnome-session-fallback                install
gnome-settings-daemon                install
gnome-shell                    install
gnome-shell-extensions-common            install
gnome-shell-extensions-user-theme        install
gnome-system-log                install
gnome-system-monitor                install
gnome-terminal                    install
gnome-terminal-data                install
gnome-themes-selected                install
gnome-themes-standard                install
gnome-tweak-tool                install
gnome-user-guide                install
gnome-user-share                install
gnome-utils                    install
gnome-utils-common                install
gnupg                        install
gpgv                        install
grep                        install
groff-base                    install
growisofs                    install
grub-common                    install
grub-gfxpayload-lists                install
grub-pc                        install
gs-cjk-resource                    install
gsettings-desktop-schemas            install
gsfonts                        install
gstreamer0.10-ffmpeg                install
gstreamer0.10-fluendo-mp3            install
gstreamer0.10-pitfdll                install
gstreamer0.10-plugins-bad            install
gstreamer0.10-plugins-bad-multiverse        install
gstreamer0.10-plugins-base            install
gstreamer0.10-plugins-good            install
gstreamer0.10-plugins-ugly            install
gstreamer0.10-plugins-ugly-multiverse        install
gstreamer0.10-pulseaudio            install
gstreamer0.10-x                    install
gtk2-engines                    install
gtk3-engines                    install
gvfs                        install
gvfs-backends                    install
gzip                        install
hdparm                        install
hicolor-icon-theme                install
hostname                    install
hunspell-en-ca                    install
hunspell-en-us                    install
hwdata                        install
icedtea-6-jre-cacao                install
icedtea-6-jre-jamvm                install
icedtea-netx                    install
icedtea-plugin                    install
icedtea6-plugin                    install
ifupdown                    install
indicator-applet                install
indicator-applet-appmenu            install
indicator-applet-complete            install
indicator-applet-session            install
indicator-application                install
indicator-appmenu                install
indicator-messages                install
indicator-session                install
indicator-sound                    install
info                        install
initramfs-tools                    install
initramfs-tools-bin                install
initscripts                    install
insserv                        install
install-info                    install
installation-report                install
intltool-debian                    install
iproute                        install
iptables                    install
iputils-arping                    install
iputils-ping                    install
iputils-tracepath                install
irqbalance                    install
isc-dhcp-client                    install
isc-dhcp-common                    install
iso-codes                    install
java-common                    install
kbd                        install
keyboard-configuration                install
klibc-utils                    install
language-pack-en                install
language-pack-en-base                install
language-pack-gnome-en                install
language-pack-gnome-en-base            install
language-selector-common            install
language-support-en                install
language-support-writing-en            install
laptop-detect                    install
launchpad-integration                install
less                        install
liba52-0.7.4                    install
libaa1                        install
libaccess-bridge-java                install
libaccess-bridge-java-jni            install
libaccountsservice0                install
libacl1                        install
libaio1                        install
libalgorithm-diff-perl                install
libalgorithm-diff-xs-perl            install
libalgorithm-merge-perl                install
libapparmor-perl                install
libapparmor1                    install
libappindicator1                install
libappindicator3-1                install
libapt-pkg-perl                    install
libarchive1                    install
libart-2.0-2                    install
libasound2                    install
libasound2-plugins                install
libaspell15                    install
libass4                        install
libatasmart4                    install
libatk1.0-0                    install
libatk1.0-data                    install
libatkmm-1.6-1                    install
libatm1                        install
libattr1                    install
libaudio2                    install
libavahi-client3                install
libavahi-common-data                install
libavahi-common3                install
libavahi-glib1                    install
libavahi-ui-gtk3-0                install
libavc1394-0                    install
libavcodec-extra-52                install
libavformat52                    install
libavutil-extra-50                install
libbamf0                    install
libbind9-60                    install
libblkid1                    install
libbluetooth3                    install
libbonobo2-0                    install
libbonobo2-common                install
libbonoboui2-0                    install
libbonoboui2-common                install
libboost-iostreams1.42.0            install
libboost-serialization1.42.0            install
libbrasero-media3-1                install
libbsd0                        install
libburn4                    install
libbz2-1.0                    install
libc-bin                    install
libc-dev-bin                    install
libc6                        install
libc6-dev                    install
libcaca0                    install
libcairo-gobject2                install
libcairo-perl                    install
libcairo2                    install
libcairomm-1.0-1                install
libcamel-1.2-23                    install
libcamel1.2-19                    install
libcanberra-gtk-module                install
libcanberra-gtk0                install
libcanberra-gtk3-0                install
libcanberra-gtk3-module                install
libcanberra-pulse                install
libcanberra0                    install
libcap-ng0                    install
libcap2                        install
libcap2-bin                    install
libcdaudio1                    install
libcdio-cdda0                    install
libcdio-paranoia0                install
libcdio10                    install
libcdparanoia0                    install
libcelt0-0                    install
libck-connector0                install
libclass-accessor-perl                install
libcloog-ppl0                    install
libclutter-1.0-0                install
libclutter-1.0-common                install
libcomerr2                    install
libcroco3                    install
libcrypt-passwdmd5-perl                install
libcups2                    install
libcupsimage2                    install
libcurl3-gnutls                    install
libcwidget3                    install
libdatrie1                    install
libdb4.8                    install
libdbus-1-3                    install
libdbus-glib-1-2                install
libdbusmenu-glib3                install
libdbusmenu-gtk3                install
libdbusmenu-gtk3-3                install
libdc1394-22                    install
libdca0                        install
libdconf0                    install
libdecoration0                    install
libdee-1.0-1                    install
libdevmapper-event1.02.1            install
libdevmapper1.02.1                install
libdigest-hmac-perl                install
libdigest-sha1-perl                install
libdirac-encoder0                install
libdirectfb-1.2-9                install
libdiscover2                    install
libdns69                    install
libdpkg-perl                    install
libdrm-intel1                    install
libdrm-nouveau1a                install
libdrm-radeon1                    install
libdrm2                        install
libdv4                        install
libdvdnav4                    install
libdvdread4                    install
libebackend-1.2-1                install
libebook1.2-10                    install
libecal1.2-8                    install
libedata-book-1.2-9                install
libedata-cal-1.2-11                install
libedataserver1.2-14                install
libedataserverui-3.0-0                install
libedataserverui1.2-11                install
libedit2                    install
libegroupwise1.2-13                install
libelf1                        install
libelfg0                    install
libemail-valid-perl                install
libenca0                    install
libenchant1c2a                    install
libept1                        install
libevent-1.4-2                    deinstall
libevent-2.0-5                    install
libexempi3                    install
libexif12                    install
libexpat1                    install
libfaac0                    install
libfaad2                    install
libffi5                        install
libfftw3-3                    install
libfile-basedir-perl                install
libfile-desktopentry-perl            install
libfile-mimeinfo-perl                install
libflac8                    install
libflite1                    install
libfolks-telepathy22                deinstall
libfolks-telepathy24                install
libfolks22                    deinstall
libfolks24                    install
libfont-afm-perl                install
libfontconfig1                    install
libfontenc1                    install
libfreetype6                    install
libfribidi0                    install
libfuse2                    install
libgail-3-0                    install
libgail18                    install
libgamin0                    install
libgcc1                        install
libgck0                        install
libgconf2-4                    install
libgcr-3-0                    install
libgcrypt11                    install
libgdata-common                    install
libgdata11                    install
libgdbm3                    install
libgdict-1.0-6                    install
libgdk-pixbuf2.0-0                install
libgdu-gtk0                    install
libgdu0                        install
libgee2                        install
libgeoip1                    install
libgif4                        install
libgirepository-1.0-1                install
libgjs0b                    install
libgksu2-0                    install
libgl1-mesa-dri                    install
libgl1-mesa-glx                    install
libglade2-0                    install
libglapi-mesa                    install
libglib-perl                    install
libglib2.0-0                    install
libglib2.0-data                    install
libglibmm-2.4-1c2a                install
libglu1-mesa                    install
libgme0                        install
libgmime-2.4-2                    install
libgmp3c2                    install
libgmpxx4ldbl                    install
libgnome-bluetooth8                install
libgnome-control-center1            install
libgnome-desktop-2-17                install
libgnome-desktop-3-0                install
libgnome-keyring0                install
libgnome-media-profiles-3.0-0            install
libgnome-menu2                    install
libgnome2-0                    install
libgnome2-common                install
libgnomecanvas2-0                install
libgnomecanvas2-common                install
libgnomekbd-common                install
libgnomekbd7                    install
libgnomeui-0                    install
libgnomeui-common                install
libgnomevfs2-0                    install
libgnomevfs2-common                install
libgnutls26                    install
libgomp1                    install
libgpg-error0                    install
libgphoto2-2                    install
libgphoto2-port0                install
libgpm2                        install
libgs9                        install
libgs9-common                    install
libgsm1                        install
libgssapi-krb5-2                install
libgstreamer-plugins-base0.10-0            install
libgstreamer0.10-0                install
libgtk-3-0                    install
libgtk-3-bin                    install
libgtk-3-common                    install
libgtk2-perl                    install
libgtk2.0-0                    install
libgtk2.0-bin                    install
libgtk2.0-common                install
libgtkhotkey1                    install
libgtkmm-3.0-1                    install
libgtksourceview-3.0-0                install
libgtksourceview-3.0-common            install
libgtkspell0                    install
libgtop2-7                    install
libgtop2-common                    install
libgucharmap7                    install
libgudev-1.0-0                    install
libgweather-3-0                    install
libgweather-common                install
libgweather1                    install
libhtml-format-perl                install
libhtml-parser-perl                install
libhtml-tagset-perl                install
libhtml-tree-perl                install
libhunspell-1.2-0                install
libical0                    install
libice6                        install
libicu44                    install
libid3tag0                    install
libidl0                        install
libidn11                    install
libido-0.1-0                    install
libiec61883-0                    install
libijs-0.35                    install
libimobiledevice2                install
libindicate-gtk2                install
libindicate5                    install
libindicator3                    install
libindicator3-3                    install
libio-pty-perl                    install
libio-string-perl                install
libipc-run-perl                    install
libisc62                    install
libisccc60                    install
libisccfg62                    install
libisofs6                    install
libjack-jackd2-0                install
libjasper1                    install
libjbig2dec0                    install
libjpeg62                    install
libjs-jquery                    install
libjson-glib-1.0-0                install
libk5crypto3                    install
libkate1                    install
libkeyutils1                    install
libklibc                    install
libkrb5-3                    install
libkrb5support0                    install
liblaunchpad-integration-3.0-1            install
liblaunchpad-integration-common            install
liblaunchpad-integration1            install
liblcms1                    install
libldap-2.4-2                    install
libllvm2.9                    install
liblocale-gettext-perl                install
liblockfile1                    install
liblqr-1-0                    install
libltdl7                    install
liblua5.1-0                    install
liblvm2app2.2                    install
liblwres60                    install
liblzma2                    install
liblzo2-2                    install
libmad0                        install
libmagic1                    install
libmagickcore3                    install
libmailtools-perl                install
libmetacity-private0                install
libmimic0                    install
libmjpegtools-1.9                install
libmms0                        install
libmng1                        install
libmodplug1                    install
libmozjs185-1.0                    install
libmp3lame0                    install
libmp4v2-0                    install
libmpc2                        install
libmpcdec6                    install
libmpeg2-4                    install
libmpfr4                    install
libmtdev1                    install
libmusicbrainz4c2a                install
libmutter0                    install
libnautilus-extension1                install
libncurses5                    install
libncursesw5                    install
libnet-dns-perl                    install
libnet-domain-tld-perl                install
libnet-ip-perl                    install
libnewt0.52                    install
libnfnetlink0                    install
libnih-dbus1                    install
libnih1                        install
libnl1                        install
libnm-glib-vpn1                    install
libnm-glib2                    install
libnm-util1                    install
libnotify1                    install
libnotify4                    install
libnspr4                    install
libnss3                        install
libnss3-1d                    install
libntfs-3g79                    install
libntfs10                    install
libofa0                        install
libogg0                        install
liboil0.3                    install
libopencore-amrnb0                install
libopencore-amrwb0                install
libopenjpeg2                    install
libopenobex1                    install
libopenspc0                    install
liborbit2                    install
liborc-0.4-0                    install
libpam-ck-connector                install
libpam-gnome-keyring                install
libpam-modules                    install
libpam-modules-bin                install
libpam-runtime                    install
libpam0g                    install
libpanel-applet-3-0                install
libpango-perl                    install
libpango1.0-0                    install
libpangomm-1.4-1                install
libpaper-utils                    install
libpaper1                    install
libparse-debianchangelog-perl            install
libparted0debian1                install
libpcap0.8                    install
libpci3                        install
libpciaccess0                    install
libpcre3                    install
libpcsclite1                    install
libpeas-1.0-0                    install
libpeas-common                    install
libpipeline1                    install
libpixman-1-0                    install
libplist1                    install
libplymouth2                    install
libpng12-0                    install
libpolkit-agent-1-0                install
libpolkit-backend-1-0                install
libpolkit-gobject-1-0                install
libpopt0                    install
libpostproc51                    install
libppl-c2                    install
libppl7                        install
libprotobuf6                    install
libprotoc6                    install
libproxy0                    install
libpulse-browse0                install
libpulse-mainloop-glib0                install
libpulse0                    install
libpython2.7                    install
libqt3-mt                    install
libquicktime1                    install
libquvi0                    install
librarian0                    install
libraw1394-11                    install
libreadline6                    install
librest-0.7-0                    install
librpc-xml-perl                    install
librsvg2-2                    install
librsvg2-common                    install
librtmp0                    install
libsamplerate0                    install
libsasl2-2                    install
libsasl2-modules                install
libschroedinger-1.0-0                install
libsdl1.2debian                    install
libsdl1.2debian-alsa                install
libselinux1                    install
libsepol1                    install
libsgutils2-2                    install
libshout3                    install
libsidplay1                    install
libsigc++-2.0-0c2a                install
libslang2                    install
libsm6                        install
libsmbclient                    install
libsndfile1                    install
libsoundtouch0                    install
libsoup-gnome2.4-1                install
libsoup2.4-1                    install
libspeex1                    install
libspeexdsp1                    install
libsqlite3-0                    install
libss2                        install
libssl0.9.8                    install
libstartup-notification0            install
libstdc++6                    install
libstdc++6-4.5-dev                install
libsub-name-perl                install
libswscale0                    install
libsysfs2                    install
libtag1-vanilla                    install
libtag1c2a                    install
libtalloc2                    install
libtasn1-3                    install
libtdb1                        install
libtelepathy-glib0                install
libtelepathy-logger2                install
libterm-readkey-perl                install
libtext-charwidth-perl                install
libtext-iconv-perl                install
libtext-wrapi18n-perl                install
libthai-data                    install
libthai0                    install
libtheora0                    install
libtiff4                    install
libtimedate-perl                install
libtotem-plparser17                install
libts-0.0-0                    install
libtwolame0                    install
libudev0                    install
libunique-1.0-0                    install
libunique-3.0-0                    install
libunistring0                    install
libunity4                    install
libupower-glib1                    install
liburi-perl                    install
libusb-0.1-4                    install
libusb-1.0-0                    install
libusbmuxd1                    install
libutouch-evemu1                install
libutouch-frame1                install
libutouch-grail1                install
libuuid1                    install
libv4l-0                    install
libva1                        install
libvisual-0.4-0                    install
libvisual-0.4-plugins                install
libvorbis0a                    install
libvorbisenc2                    install
libvorbisfile3                    install
libvpx0                        install
libvte-2.90-9                    install
libvte-common                    install
libvte9                        install
libwavpack1                    install
libwbclient0                    install
libwebkitgtk-1.0-0                install
libwebkitgtk-1.0-common                install
libwebkitgtk-3.0-0                install
libwebkitgtk-3.0-common                install
libwildmidi1                    install
libwnck-3-0                    install
libwnck-3-common                install
libwnck-common                    install
libwnck22                    install
libwrap0                    install
libwww-perl                    install
libx11-6                    install
libx11-data                    install
libx11-xcb1                    install
libx264-106                    install
libx86-1                    install
libxapian22                    install
libxau6                        install
libxaw7                        install
libxcb-atom1                    install
libxcb-aux0                    install
libxcb-render0                    install
libxcb-shape0                    install
libxcb-shm0                    install
libxcb1                        install
libxcomposite1                    install
libxcursor1                    install
libxdamage1                    install
libxdmcp6                    install
libxext6                    install
libxfixes3                    install
libxfont1                    install
libxft2                        install
libxi6                        install
libxinerama1                    install
libxkbfile1                    install
libxklavier16                    install
libxml-parser-perl                install
libxml2                        install
libxml2-utils                    install
libxmu6                        install
libxmuu1                    install
libxpm4                        install
libxrandr2                    install
libxrender1                    install
libxres1                    install
libxslt1.1                    install
libxt6                        install
libxtst6                    install
libxv1                        install
libxvidcore4                    install
libxvmc1                    install
libxxf86dga1                    install
libxxf86vm1                    install
libzbar0                    install
libzeitgeist-1.0-1                install
lintian                        install
linux-firmware                    install
linux-generic                    install
linux-headers-2.6.38-11                install
linux-headers-2.6.38-11-generic            install
linux-headers-generic                install
linux-image-2.6.38-11-generic            install
linux-image-generic                install
linux-libc-dev                    install
linux-sound-base                install
locales                        install
lockfile-progs                    install
login                        install
logrotate                    install
lsb-base                    install
lsb-release                    install
lshw                        install
lsof                        install
ltrace                        install
lzma                        install
make                        install
makedev                        install
man-db                        install
manpages                    install
manpages-dev                    install
mawk                        install
memtest86+                    install
menu                        install
mesa-utils                    install
metacity                    install
metacity-common                    install
mime-support                    install
mktemp                        install
mlocate                        install
mobile-broadband-provider-info            install
modemmanager                    install
module-init-tools                install
mount                        install
mountall                    install
mousetweaks                    install
msr-tools                    install
mtools                        install
mtr-tiny                    install
multiarch-support                install
mutter-common                    install
myspell-en-au                    install
myspell-en-gb                    install
myspell-en-za                    install
nano                        install
nautilus                    install
nautilus-data                    install
nautilus-open-terminal                install
nautilus-sendto                    install
nautilus-sendto-empathy                install
ncurses-base                    install
ncurses-bin                    install
net-tools                    install
netbase                        install
netcat-openbsd                    install
network-manager                    install
network-manager-gnome                install
network-manager-pptp                install
network-manager-pptp-gnome            install
notification-daemon                install
ntfs-3g                        install
ntfsprogs                    install
ntpdate                        install
obex-data-server                install
obexd-client                    install
openjdk-6-jre                    install
openjdk-6-jre-headless                install
openjdk-6-jre-lib                install
openssh-client                    install
openssl                        install
os-prober                    install
p7zip-full                    install
parted                        install
passwd                        install
pastebinit                    install
patch                        install
pciutils                    install
perl                        install
perl-base                    install
perl-modules                    install
pkg-config                    install
plymouth                    install
plymouth-theme-ubuntu-text            install
pm-utils                    install
policykit-1                    install
policykit-1-gnome                install
popularity-contest                install
powermgmt-base                    install
ppp                        install
pppconfig                    install
pppoeconf                    install
pptp-linux                    install
procps                        install
protobuf-compiler                install
psmisc                        install
pulseaudio                    install
pulseaudio-esound-compat            install
pulseaudio-module-x11                install
pulseaudio-utils                install
python                        install
python-apport                    install
python-apt                    install
python-apt-common                install
python-aptdaemon                install
python-aptdaemon-gtk                install
python-aptdaemon.gtk3widgets            install
python-aptdaemon.gtkwidgets            install
python-cairo                    install
python-central                    install
python-chardet                    install
python-configglue                install
python-configobj                install
python-crypto                    install
python-dbus                    install
python-debian                    install
python-defer                    install
python-egenix-mxdatetime            install
python-egenix-mxtools                install
python-gconf                    install
python-gdbm                    install
python-gmenu                    install
python-gnome2                    install
python-gnomecanvas                install
python-gnomekeyring                install
python-gnupginterface                install
python-gobject                    install
python-gobject-cairo                install
python-gst0.10                    install
python-gtk2                    install
python-gtkspell                    install
python-httplib2                    install
python-imaging                    install
python-indicate                    install
python-keyring                    install
python-launchpadlib                install
python-lazr.restfulclient            install
python-lazr.uri                    install
python-libproxy                    install
python-libxml2                    install
python-mako                    install
python-markupsafe                install
python-minimal                    install
python-notify                    install
python-oauth                    install
python-openssl                    install
python-pam                    install
python-pkg-resources                install
python-problem-report                install
python-protobuf                    install
python-pycurl                    install
python-pygments                    install
python-pyinotify                install
python-pyorbit                    install
python-serial                    install
python-simplejson                install
python-software-properties            install
python-support                    install
python-twisted-bin                install
python-twisted-core                install
python-twisted-names                install
python-twisted-web                install
python-vte                    install
python-wadllib                    install
python-webkit                    install
python-wnck                    install
python-wsgi-intercept                install
python-xapian                    install
python-xdg                    install
python-zope.interface                install
python2.7                    install
python2.7-minimal                install
qemu                        install
qemu-common                    install
qemu-kvm                    install
rarian-compat                    install
readline-common                    install
rsync                        install
rsyslog                        install
rtkit                        install
screen-resolution-extra                deinstall
seabios                        install
sed                        install
sensible-utils                    install
sessioninstaller                install
sgml-base                    install
sgml-data                    install
shared-mime-info                install
software-properties-gtk                install
sound-theme-freedesktop                install
squashfs-tools                    install
strace                        install
sudo                        install
synapse                        install
synaptic                    install
syslinux                    install
syslinux-common                    install
sysv-rc                        install
sysvinit-utils                    install
tar                        install
tasksel                        install
tasksel-data                    install
tcl                        install
tcl8.4                        install
tcpd                        install
tcpdump                        install
telnet                        install
time                        install
transmission                    install
transmission-common                install
transmission-gtk                install
tsconf                        install
ttf-dejavu-core                    install
ttf-dejavu-extra                install
ttf-liberation                    install
ttf-mscorefonts-installer            install
tzdata                        install
tzdata-java                    install
ubufox                        install
ubuntu-extras-keyring                install
ubuntu-keyring                    install
ubuntu-minimal                    install
ubuntu-restricted-addons            install
ubuntu-restricted-extras            install
ubuntu-sso-client                install
ubuntu-standard                    install
ubuntu-system-service                install
ubuntu-tweak                    install
ucf                        install
uck                        install
udev                        install
udisks                        install
ufw                        install
unattended-upgrades                install
unrar                        install
unzip                        install
update-manager-core                install
upower                        install
upstart                        install
ureadahead                    install
usb-creator-common                install
usb-creator-gtk                    install
usb-modeswitch                    install
usb-modeswitch-data                install
usbmuxd                        install
usbutils                    install
util-linux                    install
uuid-runtime                    install
vbetool                        install
vgabios                        install
vim-common                    install
vim-tiny                    install
wamerican                    install
wbritish                    install
wget                        install
whiptail                    install
wireless-crda                    install
wodim                        install
wpasupplicant                    install
x-ttcidfont-conf                install
x11-common                    install
x11-utils                    install
x11-xkb-utils                    install
x11-xserver-utils                install
xauth                        install
xdg-utils                    install
xfonts-base                    install
xfonts-encodings                install
xfonts-utils                    install
xinit                        install
xkb-data                    install
xml-core                    install
xserver-common                    install
xserver-xephyr                    install
xserver-xorg                    install
xserver-xorg-core                install
xserver-xorg-input-all                install
xserver-xorg-input-evdev            install
xserver-xorg-input-mouse            install
xserver-xorg-input-synaptics            install
xserver-xorg-input-vmmouse            install
xserver-xorg-input-wacom            install
xserver-xorg-video-all                install
xserver-xorg-video-apm                install
xserver-xorg-video-ark                install
xserver-xorg-video-ati                install
xserver-xorg-video-chips            install
xserver-xorg-video-cirrus            install
xserver-xorg-video-fbdev            install
xserver-xorg-video-geode            install
xserver-xorg-video-i128                install
xserver-xorg-video-i740                install
xserver-xorg-video-intel            install
xserver-xorg-video-mach64            install
xserver-xorg-video-mga                install
xserver-xorg-video-neomagic            install
xserver-xorg-video-nouveau            install
xserver-xorg-video-openchrome            install
xserver-xorg-video-qxl                install
xserver-xorg-video-r128                install
xserver-xorg-video-radeon            install
xserver-xorg-video-rendition            install
xserver-xorg-video-s3                install
xserver-xorg-video-s3virge            install
xserver-xorg-video-savage            install
xserver-xorg-video-siliconmotion        install
xserver-xorg-video-sis                install
xserver-xorg-video-sisusb            install
xserver-xorg-video-tdfx                install
xserver-xorg-video-trident            install
xserver-xorg-video-tseng            install
xserver-xorg-video-vesa                install
xserver-xorg-video-vmware            install
xserver-xorg-video-voodoo            install
xsltproc                    install
xul-ext-ubufox                    install
xz-utils                    install
yelp                        install
yelp-xsl                    install
zeitgeist                    install
zeitgeist-core                    install
zeitgeist-datahub                install
zeitgeist-extension-fts                install
zeitgeist-fts-extension                install
zenity                        install
zenity-common                    install
zip                        install
zlib1g                        install
```And you'll need the sources.list

```
# deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted

# deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
# deb http://security.ubuntu.com/ubuntu natty-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-backports restricted main multiverse universe
```

I think you can also use the restore script to remove packages by using **deinstall** instead of **install** in the dpkg-list.txt.

---

### Post by 23dornot23d on 2011-08-08
Great link .... and explanation ty

I will use those scripts .... and am reproducing them now ...... shame they are not zipped in
a download ..... will not take long to do though and its good as I altered them a little ...... cheers


My thoughts so far are similar to yours ..... Ubuntu is a really well made product and very
user friendly ...... 

The downside now is it contains a lot of things that I never use ( but that said I may use them in the future ) but ..... for resource hungry applications like ubuntuone .... some form of question needs to be asked at install ..... 

Do you want to use cloud based  systems - as this may slow things down somewhat  ...... 
( and it can always be added back later on - from the software center )


Debian on the other hand is giving me what I want at the moment .... and I can add to it .....

I have just got my system fully uptodate ..... and it is running so well now .....

The repos I used and I am sticking to now are shown below in this update/upgrade.

Will see how well it goes now ........ ( time will tell ) 

but I want it ready for the 3.2 and am going to try not to destroy it by using testing or
experimental .....

```

root@KanotixBox:/home/keith# aptitude update
Hit http://security.debian.org squeeze/updates Release.gpg
Ign http://security.debian.org/ squeeze/updates/contrib Translation-en          
Ign http://security.debian.org/ squeeze/updates/contrib Translation-en_US       
Hit http://kanotix.com ./ Release.gpg                                           
Ign http://kanotix.com/files/hellfire/ ./ Translation-en                        
Ign http://kanotix.com/files/hellfire/ ./ Translation-en_US                     
Hit http://ftp.de.debian.org squeeze Release.gpg                                
Ign http://ftp.de.debian.org/debian/ squeeze/contrib Translation-en             
Ign http://security.debian.org/ squeeze/updates/main Translation-en             
Ign http://security.debian.org/ squeeze/updates/main Translation-en_US          
Ign http://security.debian.org/ squeeze/updates/non-free Translation-en
Ign http://security.debian.org/ squeeze/updates/non-free Translation-en_US
Hit http://security.debian.org squeeze/updates Release               
Hit http://kanotix.com ./ Release.gpg                                           
Ign http://kanotix.com/files/fix/lo/ ./ Translation-en                          
Ign http://kanotix.com/files/fix/lo/ ./ Translation-en_US                       
Hit http://kanotix.com ./ Release                                               
Ign http://ftp.de.debian.org/debian/ squeeze/contrib Translation-en_US          
Ign http://ftp.de.debian.org/debian/ squeeze/main Translation-en                
Ign http://ftp.de.debian.org/debian/ squeeze/main Translation-en_US             
Ign http://ftp.de.debian.org/debian/ squeeze/non-free Translation-en            
Ign http://ftp.de.debian.org/debian/ squeeze/non-free Translation-en_US         
Hit http://ftp.de.debian.org squeeze Release                                    
Hit http://kanotix.com ./ Release                                               
Hit http://security.debian.org squeeze/updates/main Sources                     
Ign http://kanotix.com ./ Sources                                               
Ign http://kanotix.com ./ Packages                                   
Hit http://ftp.de.debian.org squeeze/main Sources                    
Hit http://security.debian.org squeeze/updates/contrib Sources       
Hit http://security.debian.org squeeze/updates/non-free Sources      
Hit http://security.debian.org squeeze/updates/main i386 Packages    
Hit http://security.debian.org squeeze/updates/contrib i386 Packages 
Hit http://security.debian.org squeeze/updates/non-free i386 Packages
Get:1 http://packages.linuxmint.com debian Release.gpg [198 B]       
Ign http://packages.linuxmint.com/ debian/import Translation-en      
Ign http://packages.linuxmint.com/ debian/import Translation-en_US   
Ign http://packages.linuxmint.com/ debian/main Translation-en        
Ign http://kanotix.com ./ Packages                                   
Hit http://ftp.de.debian.org squeeze/contrib Sources                 
Hit http://ftp.de.debian.org squeeze/non-free Sources
Hit http://ftp.de.debian.org squeeze/main i386 Packages              
Hit http://ftp.de.debian.org squeeze/contrib i386 Packages           
Hit http://ftp.de.debian.org squeeze/non-free i386 Packages
Hit http://kanotix.com ./ Sources              
Hit http://kanotix.com ./ Packages             
Ign http://packages.linuxmint.com/ debian/main Translation-en_US
Ign http://packages.linuxmint.com/ debian/upstream Translation-en
Ign http://packages.linuxmint.com/ debian/upstream Translation-en_US
Get:2 http://packages.linuxmint.com debian Release [12.1 kB]
Hit http://kanotix.com ./ Packages                    
Ign http://packages.linuxmint.com debian/main i386 Packages
Ign http://packages.linuxmint.com debian/upstream i386 Packages
Ign http://packages.linuxmint.com debian/import i386 Packages
Get:3 http://packages.linuxmint.com debian/main i386 Packages [9,152 B]
Get:4 http://packages.linuxmint.com debian/upstream i386 Packages [5,208 B]
Get:5 http://packages.linuxmint.com debian/import i386 Packages [19.3 kB]
Fetched 46.0 kB in 1s (23.4 kB/s)
                            
root@KanotixBox:/home/keith# aptitude safe-upgrade
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
root@KanotixBox:/home/keith# 



```

---

### Post by aeronutt on 2011-08-08
> **cbowman57 said:**
> Yeah, Mint has a good look to it but I'm at the point now that I don't really need what they have.

I'm committed to G-S as my desktop of choice, my personal comfort level while using it **has made everything else seem backwards by comparison**.  With that in mind, whatever I use will contain nothing but Gnome, everything else takes up space & doesn't get used.

I completely agree!
(FYI, I'm also playing with the alpha3 release of Oneiric. No crashes, and GS loads and runs fine! I do like the idea of a GS only load.)

---

### Post by cbowman57 on 2011-08-08
> **aeronutt said:**
> I completely agree!
(FYI, I'm also playing with the alpha3 release of Oneiric. No crashes, and GS loads and runs fine! I do like the idea of a GS only load.)

The post above with the scripts make it so easy, and it works with any distro or platform that uses dpkg.  What I did was install a base system using a net or minimal install iso, then went in from another installation for access to place the files in the appropriate places, then ran an update, followed by the restore script.

The idea of having both Unity & G-S for instance just seems stupid anymore.  Good for somebody testing to see what they like, but way too much overhead & wasted space.

@Keith, yeah, we're coming along nicely. :)

Been many years since I've gone this deep into the system I'm running. Hopefully someone will find these threads useful at some point.

---

### Post by 23dornot23d on 2011-08-08
People may use these pages to see what we were trying to do at the time Gnome-Shell 
was first being set up for multiple platforms .....

I could put you 3 screenshots on here now and it would be difficult if not impossible
to tell me which System I was in ..... all Gnome Shell all running across all platforms
you cannot say that for many new desktops now ..... ;)

[IMG]http://img12.imageshack.us/img12/4938/screenshot7js.jpg[/IMG]

Kanotix Mint above .... ;)

and in Classic mode with compiz enabled

[IMG]http://img695.imageshack.us/img695/9956/classic2.jpg[/IMG]

The thing is now we can go from Ubuntu .... to Fedora .... to Kanotix .... to Mint ..... etc


And have the same looking but custom desktop across all the systems you use now .....

Which means that people do not have to start re-learning where everything is .....

Similar wirth the old Gnome 2 ....... now this is Gnome 3

---

### Post by cbowman57 on 2011-08-08
We've broken a lot of ground when it comes to figuring out Gnome 3.0.  Time well spent. :)

---

### Post by 23dornot23d on 2011-08-08
Yep .... what we going to do next ...... upgrade which system now to Gnome Shell

 ..... Sabayon ? ...... ;)

Might be time for me to do some photography and get out more before summer is over.

If you come up with any more ideas - let us know ....


( I might try the update list above in a spare partition ..... too ..... something to do tonight )

Here is a link to download my latest one if you want to try it out too ..... [**LINK**]("https://sites.google.com/site/23dsources/home/source-lists/dpkg-list.txt?attredirects=0&d=1") ..... purely for testing .....
you may find things still need adding to it ..... but it will be less rather than more.

Not sure how you can do it though without a full repository listing ...... so will add that too shortly ......
LINK for Kanotix - Mint - Debian - Gnome-Shell - Sources listing ........  [**LINK**]("https://sites.google.com/site/23dsources/home/xorgconf/sources.list?attredirects=0&d=1")

Obviously you need the keys too to set it up ..... 


```

gpg --keyserver pgp.mit.edu  --recv-keys 3EE67F3D0FF405B2 
gpg --export 3EE67F3D0FF405B2 > 3EE67F3D0FF405B2.gpg 
apt-key add ./3EE67F3D0FF405B2.gpg 

gpg --keyserver pgp.mit.edu  --recv-keys 07DC563D1F41B907
gpg --export 07DC563D1F41B907 > 07DC563D1F41B907.gpg
apt-key add ./07DC563D1F41B907.gpg


gpg --keyserver pgp.mit.edu  --recv-keys F1773AF13B1510FD
gpg --export F1773AF13B1510FD > F1773AF13B1510FD.gpg
apt-key add ./F1773AF13B1510FD.gpg

gpg --keyserver pgp.mit.edu  --recv-keys 75CFD31C9E5DB0C8
gpg --export 75CFD31C9E5DB0C8 > 75CFD31C9E5DB0C8.gpg
apt-key add ./75CFD31C9E5DB0C8.gpg

apt-get update

```and it needs to be done ontop of a 32 bit [Kanotix Hellfire 2011-05]("http://www.kanotix.com/Article246.html") - Install 
 
Most things I need are already running .....

---

### Post by cbowman57 on 2011-08-08
[This might be interesting if you get bored.]("http://u-customizer.sourceforge.net/")

[[ATTACH]199586[/ATTACH]]("http://u-customizer.sourceforge.net/")



Hey, do you know how to use an image in this forum to activate a link?

---

### Post by 23dornot23d on 2011-08-08
Just add the Link underneath the picture .... and say where its going to or what its
going to do ..... a lot of people do not like clicking on links ...... security reasons
often quoted - when I see people saying about that ,,,,, 

[_*[COLOR=Red]**Firebug**[/COLOR]*_]("http://getfirebug.com/") is a good addon to have ..... for people worried as it shows the link by just 
hovering over whateve link it is.

But I guess its personal choice - 
( with pictures its different - imageshack use it though so it must work ) .

  or maybe they have disabled it for normal Picture clicking ..... don't really know ..... :confused:

But will have a look at customizer ...... ty

---

### Post by el_koraco on 2011-08-08
You guys are completely crazy :D

---

### Post by cecilpierce on 2011-08-08
> **el_koraco said:**
> You guys are completely crazy :D

Yep, but never bored
:P

---

### Post by cbowman57 on 2011-08-08
> **el_koraco said:**
> You guys are completely crazy :D


Thank you? 

 :lol:

---

### Post by 23dornot23d on 2011-08-08
> 
You guys are completely crazy :D


Jumping off a cliff with a bag of washing on your back is crazy ...... what we do is organized CHAOS .... seem to remember some fine programmers by that name ....

CRAZY ....... now theres a name for a new DISTRO if ever I heard of one .....

Complete Raz And Zany Yours .......... for free ...... :D

---

### Post by cbowman57 on 2011-08-08
Ok, if you want to duplicate my Debian Sid w/ nothing but Gnome 3.0 using a net or minimal install the files are attached.

---

### Post by 23dornot23d on 2011-08-08
Ok cheers and back to it ..... ;)

Thanks have downloaded it and will see what we can do with it ....... 

is there a step by step ....
  
1 ... load Debian minimal Network ISO up ok same as post 91 on here then [**LINK to distro page**]("http://www.debian.org/CD/netinst/")

(   [[COLOR=Red]**ok gone for the i386**[/COLOR]]("http://cdimage.debian.org/debian-cd/6.0.2.1/i386/iso-cd/debian-6.0.2.1-i386-netinst.iso") 32 bit or 64 bit ) ?
 
2 ... copy restore script to ? 

(home or Desktop)


3 ... run it ......

:)

---

### Post by cbowman57 on 2011-08-08
1. With the network or minimal install just put a base system, no DE at all (unless you want one)
2. Reboot into another installation & place the files in the tarball into the correct locations on the mini install. (I'd change the location of the list.txt and comment out the **rm** line in the script in case you want to run it again.)
3. Boot into the mini installation. (Might have to use atl+alt+f1 from a dark screen to get to terminal)  **su** to root  Update it with either apt-get or aptitude. 
4. Navigate to the folder you placed the restore script in and execute with ./scriptname.sh.
5. Depending on your connection & computer speed go watch a movie, take a walk or take a ****. :)

That should get you started, I'm sure you'll have to figure out some minor steps but if I could do it you certainly can.

---

### Post by 23dornot23d on 2011-08-08
ok cheers already downloaded the >>> debian-6.0.2.1-i386-netinst.iso

ready to go for it ..... this should be fun .... :D

ok burning it now lowest speed 10 x ( done )

transfer to desktop machine and install on a USB hard drive .... 

got to find a small partition for it ..... 15 Gig

ok ready

using thunar as I prefer this

apt-get update
apt-get install aptitude
aptitude update
aptitude install thunar

gksu thunar

pick the files and move them ....... into place .....

so copying dpkg-list.txt to /tmp/     (done)

next sources.list and the 2 folders also belong here ......
this belongs in /etc/apt/

had to create a folder Mogwai in home directory .....


Now it is running ....... 3 and a half gig of data ....... as you say ..... this will be early morning
before it completes or tomorrrow sometime ..... on this old computer ...



Cannot wait to find out what happens though

---

### Post by cbowman57 on 2011-08-08
Awful quiet Keith.  You go to bed or run into a problem?

---

### Post by 23dornot23d on 2011-08-08
Had a problem - sorted it now .....

and we have a long wait ..... ;) 

its running ....  :)

---

### Post by cbowman57 on 2011-08-08
> **23dornot23d said:**
> Had a problem - sorted it now .....

and we have a long wait ..... ;) 

its running ....  :)

Cool. Hopefully you'll fill in some of the gaps in explaining the steps.

---

### Post by 23dornot23d on 2011-08-08
My drive has messed up again ..... its definately a gonna .. seems to be the last part of it ... :(

Going to try testdisk on it ..... but the Iomega 1 Terra as never been like the Seagates
they pick up first time everytime

Well ....... mmmmm  ( what to do - ? will try it on another debian install that already exists )

I have a kanotix debian one that might be ok ..... will give it a try now

---

### Post by cbowman57 on 2011-08-08
I'm beginning to think el_koraco is right, we are a bit off. ;)

---

### Post by cbowman57 on 2011-08-08
Sam (samrigg) over on the LMDE forum has been working on this shell theme. I found a metacity, Firefox & cursor theme that complimented it.  Thought I'd throw it up for a viewing.

I'm sure Unity will catch up eventually but I dare anybody to say that you can't customize Gnome 3.0.

[ATTACH]199625[/ATTACH]    [ATTACH]199626[/ATTACH]

---

### Post by cecilpierce on 2011-08-08
> **cbowman57 said:**
> I'm beginning to think el_koraco is right, we are a bit off. ;)


Yep, time for a new hobby, I spent all day screwing with 100% cpu usage and multiple terminals running my memory down to zilch, it was the new and improved "nVidia driver causing the prob, there was a thread on O.O. but didnt read it till mc4man jumped in and told me abt it.
I wish I was a speed-reader :P:P:P

---

### Post by cecilpierce on 2011-08-08
> **cbowman57 said:**
> Sam (samrigg) over on the LMDE forum has been working on this shell theme. I found a metacity, Firefox & cursor theme that complimented it.  Thought I'd throw it up for a viewing.

I'm sure Unity will catch up eventually but I dare anybody to say that you can't customize Gnome 3.0.

[ATTACH]199625[/ATTACH]    [ATTACH]199626[/ATTACH]

WOW! that looks really neeeeat, how much does it cost, I wana buy it !

---

### Post by cbowman57 on 2011-08-08
I had a problem with the 280.13 that came through the official repo, but x-org-edgers had one that works great.

---

### Post by cbowman57 on 2011-08-08
He's going to start working on the metacity & the gtk themes next.  He's a professional artist & sure knows his way around his software.

---

### Post by 23dornot23d on 2011-08-08
> 
I'm beginning to think el_koraco is right, we are a bit off. :wink:
Maybe a little crazy ......

I have a minimal system now ...... :)

Its running .... with nearly everything removed now ..... as the script took everything out
including apt-get and aptitude ...... 

So my advice .... be very careful what you do run it on ......

I am in the process now of trying to put aptitude or apt-get back on ..... 

I doubt its possible ... [*_**/usr/bin/apt-get **_*]("http://www.google.com/search?q=%2Fusr%2Fbin%2Fapt-get+&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=iceweasel-a")

I just hope anything it relies on is still there ,,,,,

Think the easy option is just re-install .... but I am intrigued as to whether its easy or not to
get aptitude or apt-get to run again ...... another way .

A few places mention using wget to get a .deb package ..... so as long as you have gdebi
installed you could probably still do it .....

---

### Post by cbowman57 on 2011-08-09
Look at the list & see if there were deinstall lines in it.

Sure didn't do that here.  If dpkg is still on it though you should be able re-run the scipt & put apt back in it.  Not sure.

---

### Post by 23dornot23d on 2011-08-09
Nope the list did not ..... but with me having things already on the system it asked to remove them ..... 
my fault for not checking through them carefully ....

Just for some reason I expected it to keep things in memory that it was actually using
at the time to run the job .....

Guess you live and learn ....

Not sure if I could have held them in Synaptic ....

I can still reinstall back into it without formatting the drive ..... hope fully will be in a position to run
it again that way

No big deal but I like to let people know its not all plain sailing ..... still making mistakes and learning.

---

### Post by cbowman57 on 2011-08-09
Ah, ok.

---

### Post by 23dornot23d on 2011-08-09
Interesting .... dpkg is still there ..... if I had kept the system running it may have been possible to have done something with it .....

I need to know nore about [[COLOR=Blue]**apt-get dselect-upgrade**[/COLOR]]("http://www.google.com/search?q=apt-get+dselect-upgrade&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=iceweasel-a")

Before I try it again .... the few blogs I have read so far say its a low level installer 
which maybe means not so much checking goes on with it ......

Will read some more ..... about it before doing it again ....

apt-clone is another way

Everything is back to normal now ..... :)

---

### Post by cbowman57 on 2011-08-09
Glad to know you've got it back to normal.

You applied the script to an existing system, not a fresh minimal install?

---

### Post by el_koraco on 2011-08-09
> **23dornot23d said:**
> Interesting .... dpkg is still there ..... if I had kept the system running it may have been possible to have done something with it .....

I need to know nore about [[COLOR=Blue]**apt-get dselect-upgrade**[/COLOR]]("http://www.google.com/search?q=apt-get+dselect-upgrade&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=iceweasel-a")

Before I try it again .... the few blogs I have read so far say its a low level installer 
which maybe means not so much checking goes on with it ......

Will read some more ..... about it before doing it again ....

apt-clone is another way

Everything is back to normal now ..... :)

dselect is a higher level interface to apt, just like Synaptic. apt wasn't designed as a user-level tool, people just use it because it's awesome. So without apt, you're not gonna be able to use the dselect upgrade option.

---

### Post by 23dornot23d on 2011-08-09
I followed the script right upto the bit where the debian network install and my 
computer came into conflict ....... so reverted to plan B .......

One day ....... in the not so distant future two linux guys will do the same thing ..... lols ;)

When I start to use other peoples ideas to the full thats when the experimenting 
and enjoyment will have gone ....... but till that day ,,,, 

I will try my hardest not to deviate too much .....  :confused:

> 
dselect is a higher level interface to apt, just like Synaptic. apt  wasn't designed as a user-level tool, people just use it because it's  awesome. So without apt, you're not gonna be able to use the dselect  upgrade option.
Cheers El_karaco

I am learning ...... will try it again sometime ....... seems I have a lot to learn yet ...... but I am getting to know the
system more now .... got to try things out to find things out .....

I realised I needed it and thats when I stopped in my tracks so to speak .... last night was not good for me,

I have to admit .... somehow I need to have a backup ready to replace them if it happens again .....
not sure if its possible .... to just re-insert apt-* .... to get it working ..... all the files it needed were there
in the /etc/apt/ ( directory )

Just not sure how many files apt uses ..... in /usr/bin/ (directory) and whether it jumps to other parts of the file
system for more information too ..........

---

### Post by cbowman57 on 2011-08-09
@Keith, if we ain't braking something, we must be sleeping. :lol:

@el_koraco, Please don't hesitate to make comments, suggestions or corrections to any of the things we're talking about.  Obviously  you have a lot of experience & really understand the inner workings, we're just feeling our way along. :)

---

### Post by 23dornot23d on 2011-08-09
I don't sleep anymore ..... 

I just keep adding more systems  :)

[**System 1 - Ubuntu 320gig USB**]("http://img9.imageshack.us/img9/9001/system1320gigusbubuntu.jpg")

[_**System 2 - Ubuntu Oneiric 1 Terra USB**_]("http://img854.imageshack.us/img854/4392/system2oneiriconeterrau.jpg")

[**System 3 - Kanotix Mint Debian 1 Terra USB**]("http://img64.imageshack.us/img64/6488/kanotixmintdebian.jpg")

[_**System 4 - Ubuntu Oneiric 3.1.4 Gnome-shell 500 Gig USB**_]("http://img268.imageshack.us/img268/9641/system4oneiric314gnomes.jpg")

[_**System 5 - Mint - Debian Desktop**_]("http://img577.imageshack.us/img577/972/system5ondesktopmintdeb.jpg")

[_**System 6 is the Kanotix one - forgot the System Monitor shot**_]("http://img16.imageshack.us/img16/8602/system6.jpg")

But I have them all set up the same .... so its easy to swap between them now ....

There is also a Fedora one ..... too .... but I messed that up adding new Fonts .....
( you cannot just grab a dirctory of fonts and drop them in there .... was interesting though )

---

### Post by bulldog on 2011-08-09
You guys are amazing!

I wanted to get into a rolling distro so I didn't had to reinstall that much,and safe some time for other stuff.

But I have a busy job at the moment and I have not find the time to explore more about the pro's and cons of such a distro.
So I put it on hold till I have more time to do any research.

And you guys are deep into a Debian with the gnome-shell working.

I'll have to wait till the weekend to see if there's any time to read and understand all of your experimenting,maybe I can install a Debian myself and see if I can get a gnome-shell working.

But for now I have to let it go,I don't have enough time to spent,to set something up.

But I am very glad with gNatty,and I will sure try to get the Mogwai.

---

### Post by cbowman57 on 2011-08-09
Hey bulldog!  Glad you popped in.  As usual we're going in a dozen directions at once.  I'm sure Keith has an opinion & suggestions but I prefer a Gnome only installation onto a minimal or net install.

It's light, it's fast and who needs anything but Gnome? :)

---

### Post by 23dornot23d on 2011-08-09
We have tried every which way to produce a complete package

I guess at the moment the recipe is the best and easiest way ....

[ Update - beat me to it Chuck .....  ]

> 
The Debian Minimal ...... be careful ..... the Installer at the beginning - if it messes up can leave the drive in
a state ...... ( if it goes straight through .... with no problems then great - but it put me off last night )

If you use it I would say on a single system disk ........ not a USB ..... just through my
bad experience with it but who knows you might be fine ..... would love to hear if someone does it successfully.
Looking at the themeing and customization going on too this is going to make it even
better .... 

( I have a 2 gig backup DVD done on rematersys like last time ..... if you want I can try to upload it for you to grab ..)
user keith

I will give it one more go tonight with remastersys .... 

on this one the 

[COLOR=SeaGreen]**Kanotix - Debian - Mint **[/COLOR]- this has a script that messes up after the DVD is loaded up though ..... got a rsync error on it ..... but since then have loaded in some more packages ...... ( will try again and test with qemu )

ok first one ..... and it ran through - but with errors - [**REMASTERSYS LOG and ERRORS**]("https://sites.google.com/site/problems7730zg/home/remastersys")

```

cryptsetup: WARNING: failed to detect canonical device of /dev/sdb13
cryptsetup: WARNING: could not determine root device from /etc/fstab
live-boot: core filesystems devices utils:memdisk udev wget blockdev.
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
E: /usr/share/initramfs-tools/hooks/pcidetect failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-7-generic

```ok so it does not like the way fstab is set up ......

I know last time when I upgraded again it renamed these to UUID as it asked me if it was ok to do so 
 .... but the downside was it seemd to go into a read only state for the partition not sure if it was due 
to that or to something else though and do not know how to set this up manually ... yet

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb13
/dev/sdb13      /               ext4    errors=remount-ro 0       1
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0


```> 
The mdadm utility can be used to create, manage, and monitor MD
(multi-disk) arrays for software RAID or multipath I/O.

This package automatically configures mdadm to assemble arrays during the
system startup process. If not needed, this functionality can be disabled.
How do you disable it - I do not use it ..... and its giving me a warning nad 
a error ... on 
E: /usr/share/initramfs-tools/hooks/pcidetect failed with return 1. update-initramfs: failed for /boot/initrd.img-2.6.38-7-generic


so now the ....... 

**[COLOR=SeaGreen]Debian Mint[/COLOR]** one ....... ( only problem here is this is on the old USB hd ...... will transfer it to the main computer if I can )

[URL="http://img811.imageshack.us/img811/8362/debianmint.jpg"][U][I][B]Fullsize Screenshot
[/B] [/I][/U][/URL]
[IMG]http://img836.imageshack.us/img836/8362/debianmint.jpg[/IMG]


 not sure if I used the right remastersys ...... used the debian one on this but there is a mint one too ..... 
but I guessed that was just ubuntu based so it probably will not work ...... will stick with the v20 for
debian .....

FSTAB
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# /dev/sdb10
UUID=d9b8f176-faa5-4bd0-acae-76f4d37f2ad1 / ext3 relatime,errors=remount-ro 0 1
# /dev/ home
UUID= /home ext3 relatime 0 0
# /dev/sdb8
UUID=9e7cf2ea-3b4f-4f65-834c-ae3c1c1fc49d none swap sw 0 0
# cdrom
/dev/sr1 /media/cdrom udf,iso9660 user,noauto,exec,utf8 0 0


```But the full system is mounted .... the Iomega HDD .....  

( am making a new system now on new disk - using remastersys installer disk to disk .... not sure if it will work )
[IMG]http://img827.imageshack.us/img827/9742/copyek.jpg[/IMG]


Well it created it and the right size too .... [URL="http://img193.imageshack.us/img193/1759/createdit.jpg"][U][I][B]SCREENSHOT WAS ABOUT 8 GIG
[/B][/I][/U][/URL]

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda11            15931424  13178748   1943412  88% /
tmpfs                     5120         0      5120   0% /lib/init/rw
tmpfs                   311000      1024    309976   1% /run
udev                   1550220         0   1550220   0% /dev
tmpfs                   621996       124    621872   1% /run/shm
/dev/sda9            115281544  72495420  36930868  67% /media/16f79f1e-44c0-407d-a7e7-ef59fac8b4f2
/dev/sda15             2616508     69528   2414068   3% /media/3f9f49dd-38ea-4086-a309-2e2826ae902c
/dev/sda14           101308816   1664856  94497696   2% /media/1be905e9-edc5-4d01-a0e9-6da05f37d25c
/dev/sda7             28835836   6696036  20675020  25% /media/db84f679-b877-4b80-8de0-db88c0fd042a
/dev/sda13            10972180   8421348   1993380  81% /media/7aa2ad6d-45fa-46b2-a4aa-41246a6152ab__
/dev/sda1            425585912 324842548 100743364  77% /media/Iomega HDD
/dev/sda16            10972180   8550080   1864648  83% /media/7aa2ad6d-45fa-46b2-a4aa-41246a6152ab
/dev/sda8             57669892   5247720  49492724  10% /media/dfddf782-e265-4be2-99cd-42d3bc20910c
/dev/sda6             29299580  10154304  17656948  37% /media/e860d5c5-a371-4284-bc63-53b3c2f9aa46
/dev/sda5             35378932  20722036  12859728  62% /media/dbc42f18-1e39-4e16-8226-b59336681606
/dev/sda12            17710012  12452644   4357732  75% /media/b33b9d2d-0cff-4267-8545-f13df3d8473d
/dev/sda10            10086940   5758780   3815692  61% /media/ffbb3353-b7aa-4336-838b-4e4a53d3388e


```Unless Chuck has one he can make available ... its not  the creating of the ISO thats
the problem ...... its getting it to work on other systems ..... 
Mine I can install directly from one drive to another ..... but to get a DVD to do the same is a mystery .:confused:

ok something to do for tonight though .....

```

debianmint keith # remastersys dist  
 
Distribution Mode Selected
Checking if the /home/remastersys/remastersys folder has been created
Copying /var and /etc to temp area and excluding extra files
find: `/home/remastersys/remastersys/dummysys/var/crash': No such file or directory
Setting up live options for dist mode
update-initramfs: Generating /boot/initrd.img-3.0.0-1-686-pae
live-boot: core filesystems devices utils:memdisk udev wget blockdev.
ldconfig: /lib/libuuid.so.1 is not a symbolic link

Copying your kernel and initrd for the livecd
Creating filesystem.squashfs   ... this will take a while so be patient
Adding stage 1 files/folders that the livecd requires.
Parallel mksquashfs: Using 2 processors
Creating 4.0 filesystem on /home/remastersys/remastersys/ISOTMP/live/filesystem.squashfs, block size 1048576.
[===========================================================|] 11826/11826 100%
Exportable Squashfs 4.0 filesystem, gzip compressed, data block size 1048576
    compressed data, compressed metadata, compressed fragments, compressed xattrs
    duplicates are not removed
Filesystem size 154138.79 Kbytes (150.53 Mbytes)
    41.20% of uncompressed filesystem size (374092.76 Kbytes)
Inode table size 161142 bytes (157.37 Kbytes)
    34.18% of uncompressed inode table size (471467 bytes)
Directory table size 145296 bytes (141.89 Kbytes)
    39.58% of uncompressed directory table size (367098 bytes)
No duplicate files removed
Number of inodes 13615
Number of files 11622
Number of fragments 107
Number of symbolic links  1191
Number of device nodes 0
Number of fifo nodes 0
Number of socket nodes 0
Number of directories 802
Number of ids (unique uids + gids) 23
Number of uids 9
    root (0)
    daemon (1)
    lp (7)
    debian-transmission (111)
    keith (1000)
    man (6)
    Debian-gdm (108)
    libuuid (100)
    Debian-exim (101)
Number of gids 20
    root (0)
    daemon (1)
    dip (30)
    lp (7)
    Debian-exim (103)
    fuse (111)
    ssl-cert (113)
    debian-transmission (123)
    dialout (20)
    keith (1000)
    Debian-gdm (112)
    libuuid (101)
    mlocate (104)
    sambashare (114)
    debianmint (1001)
    staff (50)
    lpadmin (110)
    adm (4)
    mail (8)
    crontab (102)
Adding stage 2 files/folders that the livecd requires.
Found a valid exportable SQUASHFS superblock on /home/remastersys/remastersys/ISOTMP/live/filesystem.squashfs.
    Compression used gzip
    Inodes are compressed
    Data is compressed
    Fragments are compressed
    Xattrs are compressed
    Fragments are present in the filesystem
    Always_use_fragments option is specified
    Duplicates are not removed
    Xattrs are stored
    Filesystem size 154138.79 Kbytes (150.53 Mbytes)
    Block size 1048576
    Number of fragments 107
    Number of inodes 13615
    Number of ids 23

Parallel mksquashfs: Using 2 processors
Scanning existing filesystem...
Read existing filesystem, 13614 inodes scanned
Appending to existing 4.0 filesystem on /home/remastersys/remastersys/ISOTMP/live/filesystem.squashfs, block size 1048576
All -b, -noI, -noD, -noF, -noX, no-duplicates, no-fragments, -always-use-fragments,
-exportable and -comp options ignored

If appending is not wanted, please re-run with -noappend specified!

No recovery data option specified.
Skipping saving recovery file.

[=========================================================-] 169425/169425 100%
Exportable Squashfs 4.0 filesystem, gzip compressed, data block size 1048576
    compressed data, compressed metadata, compressed fragments, compressed xattrs
    duplicates are not removed
Filesystem size 2376614.14 Kbytes (2320.91 Mbytes)
    36.31% of uncompressed filesystem size (6546231.38 Kbytes)
Inode table size 2421034 bytes (2364.29 Kbytes)
    29.06% of uncompressed inode table size (8329780 bytes)
Directory table size 2387614 bytes (2331.65 Kbytes)
    41.35% of uncompressed directory table size (5773485 bytes)
No duplicate files removed
Number of inodes 237858
Number of files 186588
Number of fragments 3559
Number of symbolic links  31011
Number of device nodes 0
Number of fifo nodes 0
Number of socket nodes 7
Number of directories 20252
Number of ids (unique uids + gids) 32
Number of uids 12
    root (0)
    daemon (1)
    lp (7)
    messagebus (103)
    debian-transmission (111)
    keith (1000)
    man (6)
    Debian-gdm (108)
    libuuid (100)
    Debian-exim (101)
    avahi (104)
    debianmint (1001)
Number of gids 29
    root (0)
    daemon (1)
    dip (30)
    lp (7)
    Debian-exim (103)
    fuse (111)
    ssl-cert (113)
    debian-transmission (123)
    dialout (20)
    keith (1000)
    Debian-gdm (112)
    libuuid (101)
    mlocate (104)
    sambashare (114)
    debianmint (1001)
    staff (50)
    lpadmin (110)
    adm (4)
    mail (8)
    crontab (102)
    avahi (107)
    messagebus (106)
    pcscd (121)
    utmp (43)
    shadow (42)
    tty (5)
    ssh (105)
    nogroup (65534)
    utempter (122)
Creating customdist.iso in /home/remastersys/remastersys
Creating customdist.iso.md5 in /home/remastersys/remastersys
/home/remastersys/remastersys/customdist.iso is ready to be burned or tested in a virtual machine.
 
Check the size and if it is larger than 700MB you will need to burn it to a dvd
 
2.3G /home/remastersys/remastersys/customdist.iso
 
It is recommended to run 'sudo remastersys clean' once you have burned and tested the customdist.iso
 
debianmint keith # 


```Now that went much better ..... and I have tried Distro mode ......

so now to run qemu

ran it in qemu it stuck on gdm3

so now trying kdm

Interesting - did not take me to the login screen .... but did give me a  

$ or hash

will try failsafe mode now .... ) nope but the way it runs through everything looks promising

Wonder if a script could be set up to re-install gdm .... and reboot .....

[B]I am reasonably sure now that it works ...... as far as setting everything but the
display driver up properly now ......[/B] 

so what to do ..... ? ( remove the xorg.conf - but does not safe mode do the same thing ? )

---

### Post by 8_Bit on 2011-08-10
You've definitely got my attention with this project, and I want to try it, but I remember reading that Gnome 3 is still really buggy and incomplete on Debian. Is that still the case?

By the way, there's this great Gnome 3 Linux Mint theme here. Maybe you can get in contact with the artist to get permission and have it installed by default in Mogwai.

[http://gnome-shell.deviantart.com/gallery/28081982#/d410rpk](http://gnome-shell.deviantart.com/gallery/28081982#/d410rpk)

---

### Post by 23dornot23d on 2011-08-10
Looking at the [*_**schedule for Gnome 3.2 release September the 28 th**_*]("http://live.gnome.org/ThreePointOne#Schedule") looks good for
it to be stable .....

So until then on any system ....... we cannot say it will be ...... ;)

But my opinion .... 

I can burn DVD's
I can Render 3D images in Blender
I can login and out without a problem
I can type messages on here
I can do screenshots
I have just done a 100 Mb video using - recordmydesktop - showing I can still swap between compiz and Gnomeshell 
( while the video is still recording and while conky is running switching systems - yet to upload )

What I cannot do ......

Lets think ...... ( I will post back here when something does not work as I expect it to )

I cannot get You-Tube to load up ogv videos ..... without first going through a few steps to convert them to mpegs ..... or mov files ....... ( but thats a You-Tube problem) ;) ( so for me first render it in Pitivi then put into Openshot for you-tube)

---

### Post by cbowman57 on 2011-08-10
Yeah, maybe we can get the mod to move this to 'Debian' since we went off in a few directions pretty quickly.

Started out with LMDE but now we've tried the process on plain Debian & a few other distros. 

Gnome shell on Debian has been more troublefree than running it on Ubuntu IMO, and on Ubuntu it's pretty good.

---

### Post by cbowman57 on 2011-08-10
Welcome to the thread  [8_Bit.]("http://ubuntuforums.org/member.php?u=1284745")

Be prepared to break things and have a backup plan in effect. :)

---

### Post by 23dornot23d on 2011-08-10
> 
Gnome shell on Debian has been more troublefree than running it on Ubuntu IMO, and on Ubuntu it's pretty good.
I think we should highlight any problems and resolve them early ,,,, 

in the next 50 or so days .... what could be done to improve Gnome Shell .....

That has not been done yet ......

I like to read what ranch hand puts in his thread ..... he is very open and honest about most things as far as I can tell .......  [[COLOR=Red]**Link**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1797866") ...... ;)

Be quite interesting to hear your views on it ..... and 
if what he needs can be addresed in any way ..... 

I know we can add the XFCE panel - we started that way .... maybe ranch hand needs a neat way to add it too.

I always get one error at start up ..... it says two panels cannot occupy the same space .....

But after that it runs great ...... 
( its just that I do not like to see errors .... if I find one its a problem then to solve it - but that 
one is not within my capabilities yet - as I do not know how to disable the Gnome shell bottom panel .....)

My only other problem is getting codecs that work for openshot and installing them properly.

I have Pitivi working fine and am about to upload a video to You-Tube ..... will post it here soon
but it does show that we can swap between environments even in Debian / Mint / Kanotix ..... mix

My thoughts are - if people think that this is not stable .... or is lacking in some way ..... to highlight a
problem and see if its replicable on our systems ...... 

( then we can tell if its a real problem or just something that may need tweaking )

or maybe just needs an extension adding that they do not know about or cannot find yet ....

and I am sure many more will be written in the future too ....

---

### Post by cbowman57 on 2011-08-10
Yeah, I monitored that thread for awhile.  I think most everything has been addressed but he can't expect to be as familiar with G-S as he is with a DE he's been using for years.

When I first started using Gnome I had no idea how to modify or customize it, that is just something that comes with a lot of use.

We know the panel thing can be addressed quite a few ways, and there is an extension that fixes your number of workspaces.  I don't use it but I think I also stumbled over a method to open certain apps on designated workspaces.

What shortcomings have you come across that you still hope will be solved?

---

### Post by 23dornot23d on 2011-08-10
None for me really ..... as all the apps I use are ok ..... and the way the workspaces work is a dream come true .....

The old way is difficult to go back to now ..... as I keep going top left to orgnise things quickly ......

I needed a dock though .... and the one I use now is great ..... even when
swapping my usb drive from

 (desktop m/c) single monitor 
to 
 (laptop) double monitor TV  + a CRT and back again .....

I can quickly get to what I want ..... using any number of methods.

---

### Post by cbowman57 on 2011-08-10
Yeah, it's so easy to add Cairo, AWN or Xfce4-panel, or a number of freedesktop panels. I don't use a panel, just synapse, but I was doing that before either Unity or G-S, before that cardapio, so I was used to being less dependent on buttons & menus anyway.

I've completely adapted to G-S too, just feels so right.

---

### Post by cbowman57 on 2011-08-10
Never mind, thought Gnome 3.0 was moved to "testing" but I missed it, still in "experimental".

---

### Post by 23dornot23d on 2011-08-10
Funny but I was going through things in synaptic tonight too .... was also looking for newer file  repositories - seems Gnome-Shell is getting closer now to being stable.

I am not sure how exactly they make the choice to move things but the testing for me is fine
seems to be solid .....

I can upgrade in debian without the worries that I was having in the Ubuntu one  ..... so its definately been a good choice for me to run (kanotix debian GS) and the (debian-mint GS) one too ....

Am trying to go to sleep at a reaonable time tonight - want to sort my garden out for the weekend :D 3:44am here ..... ok catch you later ..... 

Have fun .... ;)

---

### Post by cbowman57 on 2011-08-10
I'm not sure who/how they make that decision but I think the packages in their repository has actually been more stable than the one for Ubuntu.

Enjoy a good rest.

---

### Post by 23dornot23d on 2011-08-11
All rested ty

ok 1 things still to do ....

1  .... Post my video onto you tube ( can do this once You-Tube understands ogv files as the conversions are not be added either  )

[http://ubuntuforums.org/showthread.php?t=1501566](http://ubuntuforums.org/showthread.php?t=1501566)

So am going to use this command to do it .....

mencoder out.ogv -o foo.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000


```

keith@KanotixBox:~$ mencoder out.ogv -o foo.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
MPlayer SVN-r33367 (C) 2000-2010 MPlayer Team
success: format: 0  data: 0x0 - 0x5f010ca
libavformat file format detected.
[ogg @ 0xaaf8360] max_analyze_duration reached
[lavf] stream 1: video (theora), -vid 0
VIDEO:  [theo]  3200x1072  0bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x6F656874  size:3200x1072  fps:15.000  ftime:=0.0667
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [fftheora] vfm: ffmpeg (FFmpeg Theora)
==========================================================================
Movie-Aspect is 2.99:1 - prescaling to correct movie aspect.
videocodec: libavcodec (3200x1072 fourcc=34504d46 [FMP4])
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.1s      2f ( 3%)  0.00fps Trem:   0min  13mb  A-V:0.000 [0:0]
[VD_FFMPEG] DRI failure.
Pos: 263.5s   3952f (100%) 24.89fps Trem:   0min  68mb  A-V:0.000 [2164:0]

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 2164.070 kbit/s  (270508 B/s)  size: 71270052 bytes  263.467 secs  3952 frames
keith@KanotixBox:~$ 


```It picks my twin screen as being one big one I wonder if this is the problem here 
3200x1072

Aha .... well it worked M4v ....... using handbrake ........

[COLOR=Red] [**LINK**]("http://www.youtube.com/watch?v=v0O36xzMM3c")[/COLOR]

Its not brilliant ..... but its honest ..... the switching of screens where it goes blue is only on
recording using gtk-recordmydesktop ..... if I do it with a camera/video recorder you do
noy see this blue effect ....

Ok the other annoying thing ...... the stop button or ctrl Alt S ...... do not work for gtk-record my desktop
in Gnome-shell ..... 

I had to resort to using HTOP ..... as you will see ,,,,,, 

But at least I finally got a full screen and reasonable quality video out as it will go f11 now and looks 
reasonable .....

Two things - 

You-Tube need to add a proper file converter for ogv files ...........

Gnome-Shell and Gtk-Record my desktop need to get together and sort out the glitches ....

other than that everything is just rosy ..... ;)

---

### Post by el_koraco on 2011-08-11
> **23dornot23d said:**
> 
I have to admit .... somehow I need to have a backup ready to replace them if it happens again .....
not sure if its possible .... to just re-insert apt-* .... to get it working ..... all the files it needed were there
in the /etc/apt/ ( directory )


I think all the config files are in /etc/apt
Trawl through /usr/lib to see any reference to it. 

What you could do, I guess, when apt is working, do an 

```
apt-cache depends apt
```

See the dependencies, make a note of them. Then do an 

```
apt-get install --download-only apt
```

Go to /var/cache/apt and pull the debs for apt, place them somewhere for safekeeping. If it breaks, go to the special place and install it with dpkg. Just thinking aloud. You will have to check out whether apt's dependencies have been borked by the upgrade in question, though.

---

### Post by cbowman57 on 2011-08-11
Good suggestion el_koraco, I've made it a habit to maintain a local Folder copied from /var/cache/apt/archives periodically.  Makes experimentation so much quicker since I don't have to re-download all those packages every time I want to try something new.

---

### Post by el_koraco on 2011-08-11
Yeah, but I'd mark this one as especially important, since if apt goes away and you forget where you put the debs, you might as well build a GSlack3 :D

---

### Post by cbowman57 on 2011-08-11
> **el_koraco said:**
> Yeah, but I'd mark this one as especially important, since if apt goes away and you forget where you put the debs, you might as well build a GSlack3 :D

Don't get me started. :lol:

Slackware have G-S 3 in their repositories?  (or whatever they call theirs)

---

### Post by cbowman57 on 2011-08-11
el_koraco, you are diabolical.


[**quote]can i run gnome 3 on slackware 13.37 ??**      
                                
  
  
           [COLOR=#00681C]slackware[/COLOR]                        More options      Jun 28, 1:59 pm                     
         [FONT=Courier, Monospaced]Hi there 
 can i run gnome 3 on slackware 13.37 ?? 
 and how ?[/FONT]   
   
   
[COLOR=#790619]ranzes tamar da silva[/COLOR]                        More options      Jun 28, 2:00 pm                     
            [FONT=Courier, Monospaced]Yes, You can! 
 [/FONT]
[FONT=Courier, Monospaced]follow this: 
 [/FONT]
[FONT=Courier, Monospaced][http://www.ranzes.com.br/dicas/7-linux/47-gnome-30-no-slackware-1337]("http://www.google.com/url?sa=D&q=http://www.ranzes.com.br/dicas/7-linux/47-gnome-30-no-slackware-1337") 
 [/FONT]
[FONT=Courier, Monospaced]2011/6/28 slackware <slackwar[...]("http://groups.google.com/groups/unlock?_done=/group/gsb-users/browse_thread/thread/d96966dfcdae6f66&msg=792150766bacd692")@gmail.com> [/quote]

[/FONT][http://groups.google.com/group/gsb-users/browse_thread/thread/d96966dfcdae6f66](http://groups.google.com/group/gsb-users/browse_thread/thread/d96966dfcdae6f66)


[ATTACH]199872[/ATTACH]
[FONT=Courier, Monospaced]
 [/FONT]

---

### Post by 23dornot23d on 2011-08-11
@El Korako

> 
I think all the config files are in /etc/apt
Trawl through /usr/lib to see any reference to it. 
Yep all the config files seemed to stay there ..... it seemed just the binaries were removed.

Seems like we have a new project now ..... lols ..... ;)

[**Screenshot**]("http://img717.imageshack.us/img717/3739/slackandapt.jpg")

```

keith@KanotixBox:/var/cache/apt/archives$ apt-cache depends apt
apt
  Depends: debian-archive-keyring
  Depends: gnupg
  PreDepends: libc6
  PreDepends: libgcc1
  PreDepends: libstdc++6
  PreDepends: zlib1g
 |Suggests: aptitude
 |Suggests: synaptic
  Suggests: wajig
  Suggests: dpkg-dev
  Suggests: apt-doc
  Suggests: bzip2
  Suggests: lzma
    xz-lzma
  Suggests: python-apt
  Conflicts: python-apt
  Replaces: manpages-pl
keith@KanotixBox:/var/cache/apt/archives$ 
keith@KanotixBox:/var/cache/apt/archives$ apt-get install --download-only apt
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

keith@KanotixBox:/var/cache/apt/archives$ su
Password: 
root@KanotixBox:/var/cache/apt/archives# apt-get install --download-only apt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  apt-doc lzma
The following packages will be upgraded:
  apt
1 upgraded, 0 newly installed, 0 to remove and 634 not upgraded.
Need to get 2,190 kB of archives.
After this operation, 45.1 kB of additional disk space will be used.
Get:1 http://ftp.debian.org/debian/ testing/main apt i386 0.8.15.5 [2,190 kB]
Fetched 2,190 kB in 4s (506 kB/s)
Download complete and in download only mode
root@KanotixBox:/var/cache/apt/archives# 



```apt_0.8.15.5_i386.deb

ok got it now :) ty El Korako

Getting a copy now .....will put it in /etc/apt/
as that does not alter ....

[IMG]http://img51.imageshack.us/img51/598/aptn.jpg[/IMG]

Just realised this could be catch22 ...... need gdebi to open the archive .... and if gdebi goes missing you cannot to it
and putting gdebi there does not help either as its needed to unarchive itself

Cannot say that I have ever used Slackware before .... but will also have a look at it ....

---

### Post by el_koraco on 2011-08-11
Download the dependencies as well, just to be sure. 
Strange, the apt dependency list is different in Sid as opposed to Squeeze. Check mine out. Not the dependencies, just the config

```
&#9484;&#9472;&#9472;&#9472;|elkoraco@crunchbang|&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;|~|
&#9492;&#9472;&#9472;&#9472;&#9508;#! apt-cache depends apt
apt
  Depends: libc6
  Depends: libgcc1
  Depends: libstdc++6
  Depends: zlib1g
  Depends: debian-archive-keyring
  Depends: gnupg
 |Suggests: aptitude
 |Suggests: synaptic
  Suggests: wajig
  Suggests: dpkg-dev
  Suggests: apt-doc
  Suggests: bzip2
  Suggests: lzma
    xz-lzma
  Suggests: python-apt
  Conflicts: python-apt
  Replaces: manpages-pl

```

---

### Post by el_koraco on 2011-08-11
Slackware has kicked Gnome out od the official reposa while ago, but those guys have workarounds for everything. I think I'm gonna try it with a tiling WM or something, just to get a feel for the distro. Seems to me they have a good vibe going. Edit - you don't need GDebi, that's a high level tool. 

A simple dpkg -i apt.numbers_and-stuff.deb stuff will suffice.

---

### Post by 23dornot23d on 2011-08-11
Well in 46 minutes it should be downloaded ....  a few mins to burn a Dvd .....
30 mins to install ... at a guess ....

Might be wrong things usually take longer ....  so by about 2:16 am Fr time we will be ready to go. ;)

---

### Post by cbowman57 on 2011-08-11
Also going to look at Gentoo, messed with it before but can't remember much about it other than it seemed quick.  Their latest distro has Gnome 3.0 as an option. :)

My download is running like molasses today, it might be the weekend before I can experiment.

---

### Post by 23dornot23d on 2011-08-11
Ok I liked Gentoo last time I used it ..... cannot remember why I no longer have it .....

Will be interesting to see where they are now ..... everything progresses so quickly and
each system goes in slightly different directions too ..... but all seem to manage to run almost all the same applications ..... 

Looking forward to doing something else now .... :D

---

### Post by cbowman57 on 2011-08-11
IIRC Gentoo "builds" itself from tarballs, and was extremely fast.  Can't remember why I didn't continue trying it out, maybe because I had so much time & effort invested in my Ubuntu setup.

---

### Post by 23dornot23d on 2011-08-11
Ok Slackware is installing ..... that was a new experience .....

reminds me of installing the first Red Hat disks I had .... all like dos screen based ....

My Linux Book may come in useful too ..... this is old school ..... :D

Could be a while 6 Gig .....  and the installer does not look to be fast .....

I doubt I can move this across to the laptop ..... will see later on ...

Ok it does what Mandriva used to do ....... will post some screen shots ....
[URL="http://img220.imageshack.us/img220/774/boot1zm.jpg"][B]
BOOT 1[/B][/URL]
[URL="http://img11.imageshack.us/img11/2632/boot2x.jpg"][B]
BOOT 2[/B][/URL]

Probably me not knowing enough here to get it started ..... but it boots off of a flash stick
that part is ok Flash ZIP it comes up as on my start screen .....

But its not determining the boot on sdb5 ..... which is where Iset it ....
I did not let it format first though ..... I tried to let it add itself to an existing Ubuntu system
My bad .......

Will maybe try it again if I get really bored  ..... also it wants to set Network up and I did not have all the info available
but Iwill next time as I can look at an existing setup on the same computer .....

I like that its constantly letting you know exactly what is happening though .... this
has been lost along the way ..... so as to not scare new users ......

But in times of trouble its very useful indeed .......

I also know my Limitations and I doubt Slackware is for me ...... so will stick with Debian-Mint for now

---

### Post by cbowman57 on 2011-08-12
Well I looked at Gentoo via LiveDVD but the installation ritual baffled me, I either need a book or another computer to reference the how-to as I try and do it.  The installation is intimidating.  Gave up trying to get Slackware downloaded, so I'm on the dumbed down verison, Salix.  Going to see if Gnome 3.0 can be installed on it using the Slackware link I posted earlier.

In the process of downloading the Gnome 3.0 packages from [http://gnomeslackbuild.org/download/](http://gnomeslackbuild.org/download/).

Hard to get used to slapt-get but I'm cutting & pasting away. :)

---

### Post by el_koraco on 2011-08-12
It should work, slapt-get pointing to their repos is the only difference to the original Slack, I think. I know that Slack users sometimes cheat by installing spapt-get and pointing it to Salix repos.

---

### Post by cbowman57 on 2011-08-12
Well I've got a fantastic Xfce installation, and I got Gnome 3.0 installed but all I get is a bare blue striped desktop with nothing on it, no top panel, nothing.

No matter how it turns out I'll gain something from the experience.  Right now I'm thinking I really appreciate Debian & Ubuntu. :)

Running something called "Slackbot" now, downloading, building & upgrading.  I've seen a few packages that belong with Gnome 3 so I'm hoping it will fix the problem.

---

### Post by cecilpierce on 2011-08-12
@Chuck

I gota nice Slakware 2 disk set I cud mail ya  :P

---

### Post by cbowman57 on 2011-08-12
Thanks Cecil, but I'm finding that it's just frustrating the hell outta me.

If you want a fast, basic system it's pretty good but trying to add anything is too complicated for me.  I'm going to bed.

---

### Post by 23dornot23d on 2011-08-12
:confused:  Don't know how we managed it but the full version of Slackware

[http://img263.imageshack.us/img263/2987/snapshot6t.jpg](http://img263.imageshack.us/img263/2987/snapshot6t.jpg) is in and up and running ......

So where next ?

Working so far .... KDE ... Network .... Graphics ..... not sure if Nvidia is being used yet ..... :confused:

No Package Manager ... so where now .....  ?

---

### Post by cbowman57 on 2011-08-12
Congrats Keith!  My Salix is installed & working but I feel really lost trying to set it up & use it.

I've adapted so much to how G-S works that even Xfce feels wrong.  Oh well, it's only taking up 20 GB, maybe I'll re-visit it if I stumble upon a solution to a working Gnome 3.0.  The Slackware philosophy is so much different than what I've grown used to with Ubuntu & Debian.

---

### Post by 23dornot23d on 2011-08-12
Similar ..... need to get the [_***jhbuild ***_]("http://live.gnome.org/GnomeShell").... and see if it will compile and install ok ...

but need some packages first ...... build-essentials .... are they already loaded ....

Its loaded loads on here ...... (so for the minute lets imagine everything is on here) 

but I am not seeing the things I want yet ...... :confused:

We will see how far we get ...... maybe two steps and its over .....

---

### Post by cbowman57 on 2011-08-12
The Salix Xfce install is very light, I don't know if it has build-essentials or not.  I found it frustrating, will look at it again when I'm in that kind of mood, but will be following your progress in the hopes of learning something.

---

### Post by 23dornot23d on 2011-08-12
Aha ......

bash-4.1# curl -O [http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  7886  100  7886    0     0   8427      0 --:--:-- --:--:-- --:--:-- 11597
bash-4.1# /bin/bash gnome-shell-build-setup.sh
GNOME 2.26 or newer is required to build GNOME Shell
bash-4.1# 

First stumbling block ......

so how do we load Gnome 2.26 in ... the hard way ? :confused:

---

### Post by cbowman57 on 2011-08-12
Dunno, this is what I used to install Gnome 3.0 [http://gnomeslackbuild.org/](http://gnomeslackbuild.org/)

The older packages might be more reliable, or it's possible I needed an earlier version for 3.0 to work right?  I'm as confused as you are. :)

---

### Post by 23dornot23d on 2011-08-12
Found this link and am just upgrading ..... 

[http://translate.google.fr/translate?hl=fr&langpair=fr|en&u=http://frederic.bezies.free.fr/blog/%3Fp%3D5590]("http://translate.google.fr/translate?hl=fr&langpair=fr%7Cen&u=http://frederic.bezies.free.fr/blog/%3Fp%3D5590")

using the commands on it ...... its a start .... also found the xfce package ... but need the gnome one


slackpkg update 

slackpkg upgrade-all 

just seeing how it loads things in ..... found this too the [xfce repo]("http://translate.googleusercontent.com/translate_c?hl=fr&langpair=fr%7Cen&rurl=translate.google.fr&u=http://connie.slackware.com/%7Erworkman/xfce-4.8.0/packages/x86_64/&usg=ALkJrhjiounyPggCdtooDpuWFxckfeLzRg") ..... for some reason the link is not working properly

---

### Post by cbowman57 on 2011-08-12
Well I somehow managed to break my Salix install before I fell asleep this morning.  I'll give it another go with Slackware 13.37 at a later date.

One problem with Slackware I have is that it's benevolent dictator is hostile to Gnome, so it will never make any official repository, unlike Debian. :(

Beginning to think that if I want the installation hassle but want real Gnome support in the future I may as well figure out how to install Arch.

---

### Post by el_koraco on 2011-08-12
Yakonw guys, I was just joking when I mentioned G3 on Slack. And you both went for the full Monty :D

---

### Post by cbowman57 on 2011-08-12
@el_koraco, had to go for it, even though I wasn't up to the challenge. :)

---

### Post by 23dornot23d on 2011-08-12
I found [_***this ***_]("http://gnomeslackbuild.org/"),,, seems its already being done :confused:

[http://gnomeslackbuild.org/download/#slaptget](http://gnomeslackbuild.org/download/#slaptget)


This looks to be interesting full set of Repos 

[http://ftp.osuosl.org/pub/gsb/gsb64-2.30_slackware64-13.1/gsb64/ad/](http://ftp.osuosl.org/pub/gsb/gsb64-2.30_slackware64-13.1/gsb64/ad/)


I am trying this ..... 

```


lynx --source [http://gnomeslackbuild.org/net-install/64](http://gnomeslackbuild.org/net-install/64) | bash


```if it breaks its no big deal its only been on the computer 4 hours or so .... ( its for a earlier version . 13.1 )

so maybe it will fail .....

Never know if you never try though ....

---

### Post by el_koraco on 2011-08-12
> **cbowman57 said:**
> @el_koraco, had to go for it, even though I wasn't up to the challenge. :)

I understand what you mean. i got my #! install working better than any OS I've ever had (even the few things Debian does differently make for a good learning experience), so I'm not really into hopping anytime soon, but the vibe around Slack makes me wanna give it a go. I guess you gotta really commit.

---

### Post by 23dornot23d on 2011-08-12
What I like about it the short time I have been on it ......

Its telling me everything I need to know ..... never seen such well documented code ....

gives me a good vibe ...... 

If this Gnome install goes to plan ....... then somehow I will back it up ......

Before trying to run Gnome-shell ......

( they have already got it running so its not impossible ..... always think positive .... ;)   )

---

### Post by cbowman57 on 2011-08-12
Yeah, I'm learning something every day, even if I can't figure it out it usually helps my understanding of how things work and I incorporate it in some fashion on another project.

It's good to peer over the edge once in awhile.

---

### Post by el_koraco on 2011-08-12
You learn by breaking stuff.

---

### Post by cbowman57 on 2011-08-12
> **23dornot23d said:**
> What I like about it the short time I have been on it ......

Its telling me everything I need to know ..... never seen so well documented code ....

gives me a good vibe ...... 

If this Gnome install goes to plan ....... then somehow I will back it up ......

Ok, you're going with gnomeslackbuild?  What version you going for?

---

### Post by cbowman57 on 2011-08-12
> **el_koraco said:**
> You learn by breaking stuff.

Exactly.  I've become so comfortable with Ubuntu that it's rarely a challenge anymore.

---

### Post by 23dornot23d on 2011-08-12
Its 13.1 ........ but it pulls into an existing build ..... 

I am doing it back to front

and pulling it into a later release ...... it may break things who knows ....  :confused:

Its one big download though still going .... and installing as it goes ..... no errors yet .... 

althoough saying thet is tempting fate ..... DONE

the moment of truth .....

---

### Post by cbowman57 on 2011-08-12
Maybe that was my problem.  gnomeslackbuild was set up for 13.1, not 13.37 which is what version Salix I installed.  Maybe I should start with 13.1 too.

Gonna look for a minimal 13.1 iso.

---

### Post by 23dornot23d on 2011-08-12
Ok I have decided to move this to here now ......

[http://ubuntuforums.org/showthread.php?p=11147402#post11147402](http://ubuntuforums.org/showthread.php?p=11147402#post11147402)

Because we went a little astray there ..... after all we have covered Debian and Mint
but Slackware is not really any part of this ....

[COLOR=Blue][B]If a Mod wants to take the History from where we started on Slackware here and put it in the other thread I started  - it may tidy things up a little  ......
[/B][/COLOR]

---

### Post by cbowman57 on 2011-08-13
Well, woke up early & thought I'd give Sabayon (another Gentoo for dummies like me) a trial.  It aborted during installation, guess it didn't like /dev/sda9.  Anyway, even though I told it explicitly NOT to format anything it decided to wipe out my partition table anyway.  Makes me think linux mid-1990's. :)

So, running testdisk now in the hopes of a recovery, if that fails I guess it's time to come up with a partition scheme for a fresh 1TB drive.  So burn a candle, light some incense, say a prayer, cross your fingers, throw a dead cat over your shoulder at midnight in a cemetery.. or just wish me luck and give me some moral support.


One day I'll have to learn when I've pushed the envelope far enough, but it probably won't be today. :lol:

In the old days I would have already formatted & started over.  I've become so patient & sedate, it's almost scary.

[ATTACH]199973[/ATTACH]

---

### Post by 23dornot23d on 2011-08-13
I have found testdisk to be very good ..... 

I hope you get everything back ok - as you know it usually seems to wipe out the pointers
to the partitions when you format ..... so hopefully all the data is still sitting there


What I have is another Flash disk or USB drive ..... it keeps the pointers to the filesystems

i.e the MBR .... there is always a copy on the disk in question too ..... testdisk should use it ...
to reset it up ....... but if you have a grub listing that points to one of the partitions on it
it should still find it ok .....

Just plug that in and I can quickly rebuild the partition table from the latest install

( obviously once I have booted to a partition on the disk in question - it then becomes easier . 
presuming the partition you get into is reasonably uptodate ) 

by just doing grub-install /dev/sdb - or sdc or whatever the disk was identified as ...... 



As I say hope you get it all back ok .......

---

### Post by cbowman57 on 2011-08-13
Whatever happens Keith, it serves me right. :)

---

### Post by 23dornot23d on 2011-08-13
We all take chances ..... some to a greater degree than others ....

Me I am a little cautious ..... photos etc that I do not want to lose are always backed up
twice and my accounts music etc .....

The Testdisk looks ok ...... no sign of Sabayon on there now is there ....

You can always do a deepscan too ...... but it goes through byte by byte .....

and then gives you the choice at the end how it all fits back together again .....

Let us know how it goes ....... do not write loads of data to the disk until you know its ok.

The least you write to it the more chance of recovering things ......

Obviously you need to write the MBR back at some point though ....

---------------------------------------------------------------------
You probably already know all this ...... but its just me ..... caution is best and slow is good ....

Go through it pull off as much as you can to another disk too .....

( As you know my 1 Terra Iomega gave me problems too .... 
but I have been getting smartmon reporting for a while now that a disk was dying - 
its always been my test disk and has done quite well - 2-3 years old now )

---

### Post by cbowman57 on 2011-08-13
Can never be too cautious.  I've been fighting the urge to pick up either an external USB drive or another internal, just for backups in case something like this happens.  Guess I fought it too long, was in the store not more than 3 days ago and saw a 500 GB USB for cheap, should have grabbed it & started using it immediately.  Oh well, don't think I've had a linux distro do something like this to me since about 1997.

[hm417308919kathy]("http://ubuntuforums.org/member.php?u=1401447"), yes, lesson learned. :)

---

### Post by 23dornot23d on 2011-08-13
USB external drives are so cheap now .... they are the cheapest way of storing data 

(We always used to  work out the cost per megabyte in the old days ,,,,)

it still applies now .... 

I have 4 x USB drives 3 x 1 Terra and 1 x 500 Meg .....

Only one is usually plugged in at any one time sometimes two ..... so chances of messing everything up become slim ...... learnt probably from mistakes made in the past ,,,,

---

### Post by cbowman57 on 2011-08-13
Testdisk has found quite a few partitions but I'm not finding it very intuitive.  Do I need to designate recovery by cylinder?  Starting over from scratch isn't a terrible option, I just know that if I select the wrong option & write to disk the chance of recovery become nil.

Oh well, did something, even if it's wrong.  It says I have to reboot to see changes.  Back in a minute. :)

---

### Post by 23dornot23d on 2011-08-13
Post some screenshots of what testdisk is showing you ......

---

### Post by cbowman57 on 2011-08-13
I think it's too late for screenshots. :)  I'm trying gpart now to see if it can magically recover something.  Whatever I did in testdisk definitely wasn't the correct answer.

Hey, have you heard anything good about using a hybrid drive with linux?

---

### Post by 23dornot23d on 2011-08-13
Testdisk should have done it ...... and you can always do a deep search which gives more options ....

Whatever you want to do ..... You know what you have on there ...... 

I do not ...... 

( But usually I can get back to my data - you can run testdisk again it only seems to change the pointers - as the data remains on the disk where you put it .....  )

---

### Post by 23dornot23d on 2011-08-13
Not heard of hybrid drives - just looking now

[http://www.google.com/search?um=1&hl=en&client=ubuntu&channel=fs&tbm=isch&sa=1&q=hybrid+drive+with+linux&aq=f&aqi=&aql=&oq=](http://www.google.com/search?um=1&hl=en&client=ubuntu&channel=fs&tbm=isch&sa=1&q=hybrid+drive+with+linux&aq=f&aqi=&aql=&oq=)

Are they optical .... whats the story on them ?

Toms Hardware

[http://www.tomshardware.co.uk/forum/237635-38-linux-hybrid-drives](http://www.tomshardware.co.uk/forum/237635-38-linux-hybrid-drives)

---

### Post by cbowman57 on 2011-08-13
Ok, I didn't do the deep search earlier.  Will try that and post some screenshots if the choices aren't obvious.  Thanks Keith.

I really didn't have anything on here that can't be replaced.  I just dread having to download a lot of it again.  Though one thing I know for sure, if I start over from scratch it's going to be either Debian or Ubuntu minimal, Gnome 3 only.

---

### Post by 23dornot23d on 2011-08-13
Ok best of luck ..... with Deep Search ...... post the results .....

It takes a while too ..... in this case it may be best to do the full disk ....... as the copy
it used must have been wrong in some way ..... 

Windows 7 ..... being on there is something I know nothing about as I do not use Windows
so that may throw a spanner in the works for me ....... as I could not tell you how to set that up .....?

[IMG]http://img9.imageshack.us/img9/935/drivetd.jpg[/IMG]

Looking at this first screen shot .... it seems 

Windows may be ok .... ends at 6449 and the next follows on at 6450

linux 6513 to 9129 is a big jump though unless you leave unpartitioned spaces between 

same with the ones that follow .....

---

### Post by cbowman57 on 2011-08-13
The hybrids are a standard drive with a 4 GB SSd built in, supposed to keep frequently accessed files on the SSD.

Oh well, not finding the deep search option, probably right under my nose.  Where should I look?  started with the simple 'sudo testdisk', doesn't seem to be many startup options.

Another thing that might make testdisk unable to solve the problem is that I have 18 partitions on the drive, might be what screwed up Sabayon too.

Ok, found a decent tutorial here [http://totallynoob.com/index.php?id=159](http://totallynoob.com/index.php?id=159) 

I see I don't get a deep search option until the drive has been quick searched.

---

### Post by 23dornot23d on 2011-08-13
Its after you do Analyse - Quick Search - Deeper Search

it quickly finds one table

then do deep search there

Google search ..... ( will do it on mine too ..... and get a screen shot )

[http://www.google.com/search?client=ubuntu&channel=fs&q=test+disk+deep+search&oe=utf-8&um=1&hl=en&ie=UTF-8&sa=N&tab=iw](http://www.google.com/search?client=ubuntu&channel=fs&q=test+disk+deep+search&oe=utf-8&um=1&hl=en&ie=UTF-8&sa=N&tab=iw)


My screenshot ..... may give you some idea of what it may look like .....

[[COLOR=Red]_***SCREENSHOT FULLSIZE***_[/COLOR]]("http://img812.imageshack.us/img812/5189/screenshot6dy.jpg")

First run of it looks like this and takes alittle time to run ,,

[IMG]http://img268.imageshack.us/img268/7826/firstrun.jpg[/IMG]

Then Enter to continue

then you get the option to do a deeper search ....

[IMG]http://img202.imageshack.us/img202/3936/deeper.jpg[/IMG]


Then its time to go Fishing ..... as this will now take a very long time on a 1 Terra drive ...

[IMG]http://img594.imageshack.us/img594/1584/gofishing.jpg[/IMG]


by the way I am no expert on this piece of software - but it has saved me a couple of times
now from starting from scratch ......

and of course ...... _***[The official page for Testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")***_ too

---

### Post by cbowman57 on 2011-08-13
Yeah, doing the deep search now. Slow going, but it's chugging away.  03%, it already found a partition that was overwritten a very long time ago.  Will I have the option of choosing a more recent one or is this the result of it finding the most intact superblock?

37%

---

### Post by 23dornot23d on 2011-08-13
It finds a list of old and new ..... then you have the choice at the end to pick what is more relevant .....

Usually you can tell this by the start and end of each partition ..... and testdisk at the end
will usually let you know if the partition table is not logically set up .... with the choices you make .....

You also do have the choice to backout without doing anything at the end .....

47% here ..... started mine around the same time too ..... want to see if it finds any thing odd on
mine too ......

---

### Post by cbowman57 on 2011-08-13
While I'm sitting here waiting & thinking, it dawns on me, probably shouldn't wait for a catastrophe to get familiar with this type of software.  << note to self :)

I'm going to be a little ticked off if it recovers evreything but my favored installation.

---

### Post by 23dornot23d on 2011-08-13
Was your favoured installation running ok after the Sabayon install ..... 

or was everything linux gone ?

57% here .....

[]("http://drehsen.com/compusectools/testdisk/testdisk/doc/testdisk.html")

---

### Post by cbowman57 on 2011-08-13
Everything linux gone, left Windows but left it un-bootable.

Like I said, quite possible they never anticipated it would be installed on a drive with as many as 18 partitions.

50%

Hey,am I interpreting the tutorial correctly.  Does this also give me the ability to delete some old, dead partition references?

---

### Post by 23dornot23d on 2011-08-13
Yep

it removes them from the records ..... if you press delete ....

am pretty sure it then shows as unallocated space after doing that .....

But you need to read up and be sure ......

I think I used it once for overlapping partitions ..... 

I got into serious problems once though ..... so do not take this lightly .... :confused:
( it sets the hard drive up and it can make things really difficult too )


[https://sites.google.com/site/problems7730zg/sda-layout-after-testdisk---30402](https://sites.google.com/site/problems7730zg/sda-layout-after-testdisk---30402)

( As you will see above - I decided to move vista left ...... it would no longer boot although the data was there ..... best thing I ever did really ...... never used windows since .... )

If you are unsure of anything ..... and the tables do not look correct then sometimes
re-partitioning can be safer .......

I never let anything bother me ...... but I sort of like solving problems ......

78 %   [[COLOR=Blue]_***SCREENSHOT ***_[/COLOR]]("http://img846.imageshack.us/img846/2101/screenshot13oz.jpg")..... gives an idea .... the original is on the left

---

### Post by cbowman57 on 2011-08-13
84%

Yeah, I plan to take things slow.  One thing that is going to make it a little tough on me is that I shuffled/resized partitions a couple weeks ago for a more practical layout.  Unfortunately it left a lot of markers to old locations.  I can only try, if I have to start from scratch I'll have something to occupy my time for a few days.

---

### Post by 23dornot23d on 2011-08-13
[COLOR=Red][B]When its finished

Do not press enter until you have gone through the list and set it up as you think it should be ,,,[/B][/COLOR]

You will have to set each partition up now with the correct flags .....

look carefully at each one - I seem to remember them turning green if testdisk thinks they are right ..
but that may be at the end .....



If you are anything like me - which from what we have done so far

whichever way it goes you will make the best from it ....

and like me with that new drive ..... its already half full ..... but am having

a great time now filling it up lols ..... we keep learning .... :D

================

Just a thought

Do you have any flash drives you used recently with the boot info on them

If you have it may boot straight into an old partition .... mine did .....

96 %

[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)


[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")


100 % .... [COLOR=Blue]_*[**my screenshot**]("http://img855.imageshack.us/img855/2503/backuplists.jpg")*_[/COLOR] showing the original and the one it gives back ...... then
you have to make the choices ......


[COLOR=Red]**Do not press enter until you have gone through the list and set it up as you think it should be ,,,**[/COLOR]

Otherwise

It just kicks you out to the beginning and you have to go through th whole process again ..... 
as I just found out - and cannot see a way of returning ...

that was two hours wasted for me anyways......

also to see the log afterwards .....


gedit testdisk.log



-------------------------------------------------------------------------------
Ok it can take some time ...... best if you have old layouts of the drive too
but if you recently re-shuffled they may not help here.

---

### Post by cbowman57 on 2011-08-13
Yeah, I accidentally exited out too.  Oh well, taking off for a bit, going to just let it chug along for another hour or so. :(

---

### Post by 23dornot23d on 2011-08-13
Ok the data on the drive is going nowhere .... and while its doing it you have chance
to go out and enjoy something else ....

raining cats and dogs here ..... catch you later .....

---

### Post by cbowman57 on 2011-08-13
> **23dornot23d said:**
> Ok the data on the drive is going nowhere .... and while its doing it you have chance
to go out and enjoy something else ....

raining cats and dogs here ..... catch you later .....

Went for a long bike ride, came home, tried to restore some helpful partitions, got nowhere.  Wiped the partition table, picked up another HDD so now I can at least maintain my clones on another physical drive.  Doing the net install in a few minutes, well actually the base is installed.  In a live session now so I can download that little package I posted a couple pages back, going to locate the essential files, run that restore script & watch some TV while it downloads & installs itself.

I'm jealous of your rain. :)  We need a good soaker, even if it's just enough to clean the sand off the shoulders.  I'm getting tired of riding in a sand blaster.

bbl.. chuck

---

### Post by 23dornot23d on 2011-08-13
The rain is ok in moderation .... ;)

There is a band playing here today 3:00 am and its about 3 miles away but can hear it
as clear as a bell ...

Ok good to see you are back in business ..... 

I am getting nowhere quick with the Slackware one ..... it drives me mad .....

Basically do not know enough commands yet to use it properly ...... its a little like learning a new language for me .....

I am in the Kanotix version at the moment ..... but have spent the last few hours on slackware going round and round in circles ..... one minute it see's a package called ffi the next it does not ..... :confused:

I did my disk too ..... this is a screenshot of how it changes to green as you select the ones that are ok

[[COLOR=Green]_***SCREENSHOT***_[/COLOR]]("http://img706.imageshack.us/img706/9533/fixedwl.jpg")

and if you should pick one wrong it goes red at the bottome and deselects everything and warns you

[[COLOR=Red]_***SCREENSHOT***_[/COLOR]]("http://img810.imageshack.us/img810/5506/wrongh.jpg")

Just in case anyone wanted to see what happened and the moment of truth is reboot time ....
as it happens I kept most of mine the same as it was before .....

But I had lost some space at the end of the drive and it had got a little mixed up
but everything is ok now .....

[[COLOR=Blue]_***GPARTED***_[/COLOR]]("http://img806.imageshack.us/img806/3503/screenshot9c.jpg")

I still have one problem ..... but the drive before I did this was showing 
as completely empty space all across ..... it ......

---

### Post by cbowman57 on 2011-08-14
Well don't know what my problem is today, everything is just going wrong.  Tried twice already to get a minimal Gnome 3 on debian installed and it just isn't happening. Installing LMDE Gnome now just so I have a desktop I can work from.  Guess I'll get Transmission up & running to download a copy of gNatty.  Find it difficult not having Gnome shell.

Not sure if the repositories are in transition for G-S 3 or what's going on. :(

---

### Post by 23dornot23d on 2011-08-14
You could be right 3.1.5 comes out tomorrow

[http://live.gnome.org/Schedule](http://live.gnome.org/Schedule)

[[COLOR=Blue]_***FULL SCHEDULE***_[/COLOR]]("http://live.gnome.org/ThreePointOne")

I must admit - most of my systems now have a way to get to gnome-shell ... the ones that do not become very frustrating
so used to going to the top left now to organise and see things .... so quick and yet so simple to see exactly what is 
running and quickly pick the one that you want ......

---

### Post by bulldog on 2011-08-14
I finally done it.
Did cost me the best part of the day,but I have GS running on a Debian net-install.
Have some problems though,but it's boot able and I can do some work on it.
Think I will write things I've done on a piece of paper,and do it again next weekend.
Have not done any theming or install any extension,but that's the easy part :)

See you guys are going to try to get GS on Slackware,I'll pass on that one.
Will try Debian SID for a while and see if it's any good for my needs,if so,I'll leave Ubuntu for what it is and focus on Debian.

---

### Post by 23dornot23d on 2011-08-14
I think I have bitten off more than I can chew with Slackware .....

But that looks good ..... and Debian is familiar territory so similar to Ubuntu

Ubuntu being based on Debian .... its going back to the roots .

What sort of problems are you encountering ..... sometimes they can be resolved

by dropping the experimental repository and going back to the testing one .....

Just have to be careful when adding things - as you may find to install other things

the package manager sometimes wants to remove Gnome-shell ..... or at least

that was the case on the Mint Debian one .....

---

### Post by cbowman57 on 2011-08-14
Still plugging away from a stock LMDE install, having some coffee.  Will try to resolve the G-S installation problem later I guess.  3.1.5 probably won't hit Debian any time soon, though it will probably be in the Oneiric repos within a few days.

Left the machine on last night trying to get a copy of gNatty 64 downloaded, not much progress so far.

@bulldog, congrats.  You're having better luck this weekend than I am.   Based on my catastrophe caused by my experimentation with Sabayon I think I'll stick with Debian & Ubuntu for now.  :)

The faster I try to go the behinder I get. :lol:

[ATTACH]200044[/ATTACH]

---

### Post by bulldog on 2011-08-14
Problem one,I'll get used to drop a tar.gz in a directory and choose unpack here,this seems missing in this install.
Problem two,my system-settings menu,under my name in the top right corner,doesn't do anything.
Problem three,in the over sight menu,most application seems to be double,one clear and shiny icon and a blurry one.
But overall it's working okay.

I have to admit I did a whole lot of installing and removing files before I get the GS working,even had to install xfce and lxde to get a working desktop again.
But finally I kind of sort out things,but I'm afraid I did remove to many files I should have kept.

So I try a clean install next weekend and try to find a better way to install GS.
Think I made it to hard for myself,should be an easier way to do 
things.

Will read the thread carefully,to see what you guys came up with,instead of jumping into deep water without the skills to swim properly.

But learned a lot today,mostly how things shouldn't be done :(

@chuck,
Seeding the x64v3,can let the computer run for 7 hours if you want me to.

---

### Post by cbowman57 on 2011-08-14
I'm still figuring it out too, and having my share of problems, so I don't rate it as "easy" by any means. The duplicate apps in overview are probably the results of having lxde & xfce installed.  If it's worth your time you can edit the .desktop files to have them visible only in certain DE.

Thanks for seeding it bulldog, with the speed of my connection it's a tedious process, which is why I try to store packages I've used for installation in a local folder, saves me time.  Wiping my HDD yesterday really put me back at square 1. :)

---

### Post by 23dornot23d on 2011-08-14
@Bulldog

> Problem one,I'll get used to drop a tar.gz in a directory and choose unpack here,this seems missing in this install.
[B]aptitude install arj
aptitude install xarchiver[/B]
**aptitude install p7zip-full**
**aptitude install gzip**

there are others too ..... take a look in synaptic

[B]aptitude install synaptic
[/B]

> Problem two,my system-settings menu,under my name in the top right corner,doesn't do anything.[B](  possibly check for things like gnome-settings / gsettings in synaptic ...... ) :confused:

[/B]
> Problem three,in the over sight menu,most application seems to be double,one clear and shiny icon and a blurry one.
As Chuck says this is picking two or 3 sets of icons up - one probably from LXDE .... the other XFCE maybe
I have seen this too - but does not bother me as I use Cairo-Dock for my App Launcher.

> But overall it's working okay.
Good to hear ...... :D

---

### Post by cbowman57 on 2011-08-14
Hey bulldog, not positive but I think that if you go into synaptic and look at file-roller you can select the suggested & recommends.

Well my adventure continued today.  Found the simplest way to get G-S 3 on Debian (or Ubuntu) minimal is to use **aptitude install -t experimental gnome-shell** , that seems to take care of pretty much everything, no pinning file, just make sure you have unstable, experimental added in your sources.list.  Makes me think that I've been trying to over-think the whole procedure.

---

### Post by cbowman57 on 2011-08-15
Ok, yesterday's recovery used this for a sources.list:

```

deb http://mirrors.kernel.org/debian/ squeeze main contrib non-free
deb http://mirrors.kernel.org/debian/ testing main contrib non-free
deb http://mirrors.kernel.org/debian/ unstable main contrib non-free
deb http://mirrors.kernel.org/debian/ experimental main contrib non-free

deb-src http://mirrors.kernel.org/debian/ squeeze main contrib non-free
deb-src http://mirrors.kernel.org/debian/ testing main contrib non-free
deb-src http://mirrors.kernel.org/debian/ unstable main contrib non-free
deb-src http://mirrors.kernel.org/debian/ experimental main contrib non-free


deb http://security.debian.org/ squeeze/updates main contrib non-free
deb http://security.debian.org/ testing/updates main contrib non-free
deb-src http://security.debian.org/ squeeze/updates main contrib non-free
deb-src http://security.debian.org/ testing/updates main contrib non-free


# squeeze-updates, previously known as 'volatile'
deb http://mirrors.kernel.org/debian/ squeeze-updates main contrib non-free
deb-src http://mirrors.kernel.org/debian/ squeeze-updates main contrib non-free

# Multi-media #
deb http://www.debian-multimedia.org squeeze main non-free
deb http://www.debian-multimedia.org testing main non-free
deb http://www.debian-multimedia.org unstable main non-free
deb http://www.debian-multimedia.org experimental main non-free

# Liquorix Repository #
deb http://liquorix.net/debian/ sid main

# aptosid sources added by smxi
deb http://aptosid.com/debian/ sid main fix.main
deb http://http.us.debian.org/debian/ sid contrib non-free main
# deb-src http://aptosid.com/debian/ sid main fix.main
```I used the daily multi-arch Debian 'testing' net install iso.

No 'local' file.
No 'gnome' pinning file.
I didn't do a dist-upgrade.  My system is a mix of everything from stable to experimental.  It dawned on me that I was only increasing the level of difficulty trying to upgrade to sid then throw gnome-shell on top of that.
After I had a basic shell & fallback DE installed I went into synaptic & filled in the gaps.  Using the search function for versions I put in 3.0. and looked for packages I recognized that weren't installed.  Also selected the installed status and clicked on each package to see what suggested & recommended were missing.  **Tip:**  If you go install or upgrade something and it tells you it wants to remove everything from alacarte to whatever, it's probably not a good idea to install it.  Don't be afraid to use the 'force' version either.

After the basic installation I used the smxi script to do some tweaking behind the scenes.  

Not really related to the installation.  I added a Seagate 1TB drive that seems to out perform the 1TB Western Digital Black I was using so the WD is relegated to being used to hold my non-system partitions (Downloads, Music, Backups)

---

### Post by 23dornot23d on 2011-08-15
As time passes I am sure it is going to get simpler too ...... not long now to the release
date ......

But that is great news one command and we can now have gnome-shell on Debian ... :)

I really like the Seagates too ..... good drives ..... for me and my system anyway .....

---

### Post by cbowman57 on 2011-08-15
Yeah, using aptitude anyway.  Not sure if apt-get would give the same results.

There are of course some things that aren't automagically installed but we've become so familiar with what goes into gnome-shell that it's almost second nature now.

Anyhow, still downloading myself a copy of gNatty 64. :)

I'm attaching a copy of the installed package list I ripped with the dpkg-backup script.  Somebody might find it helpful as a guide if they aren't sure what to include.  << Remember, the script could be harmful to an existing installation.  I recommend this only for installation on a minimal or net install.  Should work with Ubuntu as well.

---

### Post by bulldog on 2011-08-15
To be honest,I was in a hurry to set up the Debian and did not read much of the topic.
Did not use a pinning file either,just added the unstable and experimental.
Then before doing anything to upgrade,I used the smxi script and did a whole lot of things which most of them I can't remember.
But the goal was the nvidia driver,but it could update and upgrade the install as well,so I did.
Installed xfce what became handy later on.
Maybe this was wrong,and made it harder to install Gnome.

Of course the blame is on the smxi script rather than me,because it gave me so many options to try out,and I couldn't resist.:)

But maybe I was a little carried away by the script. 

So I will try a fresh install next weekend and will read the tips and tricks first.

About my problems,wel I can unpack tar.gz but it's a little harder to do,can't install file roller,seems to be a dependencie problem of some kind,and the 3890 icons in the overview are not a real problem.
Thank you for thinking with me.

If you have tips or short cuts don't be shy and tell me all about it.

I read the one from chuck just add the repo's and install GS without the usual dist-upgrade.
Could work,so maybe I'll try that one.

Looking in synaptic and add gnome 3.0 stuff and the recommended and suggested is something I did yesterday.
That takes some time I can tell you.
But it works so it can be done again.

---

### Post by cbowman57 on 2011-08-15
You will probably have to do a force install of the 3 series file-roller, it tries to default to the 2.32 version.

[ATTACH]200103[/ATTACH]

That smxi script is powerful, seems like I find something new every time I use it.  Sure saves a lot of time searching the web for drivers & things though. :)

---

### Post by bulldog on 2011-08-15
I can try that,the -f option I mean.

I wonder if it makes a difference when you use the script.
Is it better to use it before or after the GS install,I'm not sure about that,because I did a whole lot more with it that's for sure.

I'm not putting much efford in this install,because I made my mind up,and will do a fresh install for keeps.
But I will have it as clean as possible , no xfce just gnome-shell and fall-back mode.

So if you have any good advice,it will be very much appreciated.

Keith does a very good job too,I like to read his postings,although I don't understand always what he means.
But he like's to add several DE's which isn't bad at all,but I know I won't use them that much,so why bother to install.

And before I forget,thank you for the tip for the nice steam-punk theme,I have it in use on gNatty.

Rest me to say I used the amd64 Debian install,maybe there's a difference with the 32bit system.

---

### Post by cbowman57 on 2011-08-15
Yeah, Keith gets really creative and comes up with some wild combinations, but he was pretty much a KDE user when he started playing with this I think.

I'm not sure about the smxi before or after, my theory is that it should be run after, but since you got yours up & running using it first it kills my theory. :)

I used the 64-bit version also.  I also like the minimal installation, I think it reduces the chance of dependency conflicts, plus all I care to use is Gnome.  I did use Clonezilla last night to make a backup, the installation was only using 3.7 GB drive space.  That's a space savings of almost 1 GB compared to gNatty 64-bit with Unity.

---

### Post by 23dornot23d on 2011-08-15
> 
But he like's to add several DE's which isn't bad at all,but I know I won't use them that much,so why bother to install.
I sort of like seeing what will work with what else ...... so that is the reason .....

Sometimes I just add LXDE ....... because it seems the quickest and smallest install
it also gives me a desktop to drop back to - say things should go wrong in Gnome-Shell .

KDE .... I used to really like it .... but a long time back now ..... its too much for my smaller
machine ..... and even on the 2 core ..... takes a lot longer to finish loading in than
Gnome-Shell .....

Well in just over one months time now - it will be time to get the full version of Gnome-Shell ......

So at the moment I am just trying to see how far I can get with it on Slackware .....

I like the idea of the mix ...... but the chances will get better once the final release is out
also there is a team of people already working on it .... 

I will not be changing to slackware though ...... who is going to compile everything they
need for a system ....... when you can download a binary on nearly every other system
with no real problems .....

I like Fedora ..... once they sort the Fonts out ..... it will be on par with Debian

I like Debian and the logical way things work .... and its speed and low memory usage ...

I like Ubuntu because it has a very professional approach to the customer demand .....

I like Mint - Debian ...... because it takes Ubuntu and removes any sharp edges it  finds ....

__________________________________________________________

I most of all like Gnome Shell though , because it is consistent on all of the above platforms ...... and more to come ..... ;)

---

### Post by cbowman57 on 2011-08-15
Good assessment Keith.  
I saw your thread about using Slackware & gnome, looks like that is keeping you plenty busy. :)  I have a bit of a philosophical difference with Slackware & how they go about things, their open hostility towards Gnome makes the Ubuntu/Gnome drama look like a romance.

---

### Post by 23dornot23d on 2011-08-15
> 
I saw your thread about using Slackware & gnome, looks like that is keeping you plenty busy.
I tend to spend an hour or so each night on it ..... but its not something I think I will use
much ..... although ...... up to just no real breakage .... and I have updated  everything
I can ..... and also set up a couple of users .....

As well as altering the system by adding the things needed for Gnome Shell .....

In the future if all the Linux community and Distros were brought together with one
magical idea and piece of software that could work the same between all of them ....

Then it stands a chance against Microsoft .......

Familiar Desktop ..... machine to machine ..... thats what Microsoft had going for it ...

People get scared and dare not touch things in case they break them ...... when not 
easy to use ..... rarely get lost on the Shell .....


> 
I have a bit of a philosophical difference with Slackware & how they go about things, 
open hostility towards Gnome makes the Ubuntu/Gnome drama look like a romance.
Not seen this do you have a link ..... to something ?

---

### Post by cbowman57 on 2011-08-15
> Not seen this do you have a link ..... to something ?

Can't remember where I saw it but when I was trying to install Gnome I ran across some comments to that effect.  Slackware just isn't designed to install Gnome easily, that's why it's not in an official repository, if you want to install it you have to go to a third party.

---

### Post by 23dornot23d on 2011-08-15
I found this from a lot of years back in 2005 ...... but the main reasons seemed to be packaging
Gnome and its dependencies on lots of other libraries .....

[http://tech.slashdot.org/story/05/03/28/009237/Gnome-Removed-From-Slackware](http://tech.slashdot.org/story/05/03/28/009237/Gnome-Removed-From-Slackware)

Maybe Gnome Shell will not be so bad .....

---

### Post by cbowman57 on 2011-08-15
That's interesting.  If Gnome is that hard to package I guess I can understand their stance.  I think I liked it when I didn't know how things worked, or how difficult it was, to incorporate a DE into a distro.

Xfce is a solid DE, no disputing that.


I just finally got a gNatty iso this afternoon.  Installing it now, forgot what it was like to get it installed. :)

---

### Post by 23dornot23d on 2011-08-15
> 
I just finally got a gNatty iso this afternoon.  Installing it now, forgot what it was like to get it installed. :smile:
Don't know if you have looked at my homepage here recently ..... but I have been taking
a walk in the not so distant past ..... one of the first versions of Gnome-Shell ..... 

and at the moment I am in a 10.10 release ..... its the quickest one I have on Ubuntu
still with everything working ..... launchers .... themes ..... gnome advanced tweak tool ....
conky and the visibility/transparency ..... launchers on the desktop ..... cairo-dock ....

[IMG]http://img811.imageshack.us/img811/9922/screenshot6x.jpg[/IMG]

Get quite a good feeling now jumping from one to the other ..... shows how much things
change and change has to be for the better for people to be happy ...... :D

---

### Post by cecilpierce on 2011-08-16
gOneiric seems to be working better after updates,
gnome-session went to v3.1.5 but not gnome-shell and all but 2 themes are working, had to go back to murphy weather, venemo crapped out for some reason.

---

### Post by cbowman57 on 2011-08-16
I think there is a more recent version of venemo, but Murphy's weather is a good one.

Yeah, I've been keeping an eye on Oneiric, but haven't tried it in over a month.  Do they have it available as a minimal iso yet?

---

### Post by cecilpierce on 2011-08-16
> **cbowman57 said:**
> I think there is a more recent version of venemo, but Murphy's weather is a good one.

Yeah, I've been keeping an eye on Oneiric, but haven't tried it in over a month.  Do they have it available as a minimal iso yet?

I haven't checked but I doubt it.
I always used venemo but it quit, where is the new one ?

---

### Post by cbowman57 on 2011-08-16
[https://github.com/simon04/gnome-shell-extension-weather](https://github.com/simon04/gnome-shell-extension-weather)

---

### Post by cecilpierce on 2011-08-16
> **cbowman57 said:**
> [https://github.com/simon04/gnome-shell-extension-weather](https://github.com/simon04/gnome-shell-extension-weather)

Thanks Chuck

---

### Post by cbowman57 on 2011-08-16
It will be nice when Gnome.org gets Sweet Tooth up & running.  Probably won't see that until 3.2 comes out.

---

### Post by 23dornot23d on 2011-08-16
I had to check up on that one ...... looks a good idea ... :)

[http://www.linuxplanet.org/blogs/?cat=4118](http://www.linuxplanet.org/blogs/?cat=4118)

I keep checking for 3.1.5 too ..... Harry said there are a few packages available
but I have only found 1 or 2 but not the ones he mentioned on the [[COLOR=Red]_***Oneiric Thread***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1826041")

---

### Post by cbowman57 on 2011-08-17
Link for the latest LMDE iso, both the Gnome & Xfce are labeled as RC [http://ftp.heanet.ie/pub/linuxmint.com/testing/](http://ftp.heanet.ie/pub/linuxmint.com/testing/)

---

### Post by cbowman57 on 2011-08-19
Well Keith's journey with Slackware got me to take another look at Arch.  It's different, but I think I could get used to it.

[ATTACH]200338[/ATTACH]

---

### Post by bulldog on 2011-08-19
I'm downloading a version of aptosid and will have a go to install this.
Taking the XFCE version and try to get GS on it this weekend.
Have no idea yet if this is a better choice instead of the Debian SID,but I soon find out.

First some reading about aptosid,maybe I'll change my mind later on;)

Nevermind,Gnome is not supported with aptosid.
It can be done,but it takes a lot of time I think.

---

### Post by 23dornot23d on 2011-08-19
> **cbowman57 said:**
> Well Keith's journey with Slackware got me to take another look at Arch.  It's different, but I think I could get used to it.

[ATTACH]200338[/ATTACH]


Good choice ..... we should make a list now ..... 
of the ones Gnome-Shell is working on ..... and which it is not .....

I got closer today to having it running on Slackware ...... but tend to work on it till I get stuck ..... and then
go away doing other things but still thinking about it ......

Its a little like blackjack ...... I find ...... push it too far ..... and you bust .......

Which then can mean a re-install ..... although its not been too bad up
to just - as it can be written back without destroying everything you have done ....
Then just re-compile the Gnome-Shell on top ..... again ... ;)

Look forward to seeing what it looks like on Arch ..... :D

---

### Post by cbowman57 on 2011-08-20
Well Arch is boring, it just works. :)

The installation was easy (this time) using the net install.  With Gnome 3 as the default gnome it's super easy to install & stable as a rock.  Every extension that works on my Debian installations work perfect.  Software applications are easy to find & install, official & unofficial. The online knowledge base is amazing, which frankly takes some fun out of it, no need to interact in a forum. Just about every answer you need is already answered in the forum or a wiki.  I do kind of dig the community spirit, does seem to closely adhere to old-school linux ideals.

It lacks a synaptic of course but there are a few independent gui frontends for pacman.  I personally like the command line for installing software but I'm using a gui called AppSet to browse, and occasionally install from.  Anything unofficial is usually just a matter of googling with "AUR packagename".

I have no idea when G-S 3.1.5 will be introduced in official channels, or if they will wait for 3.2. (3.1.5 doesn't seem available yet unofficially either)

If I wasn't already somewhat used to net installs and the packages required for Gnome it probably would have been intimidating.  Maybe the planets were just aligned right the other night, or my mood was right, but I just cruised right through it.

Dressed it up in a manner that seems to compliment the Arch philosophy.

[ATTACH]200454[/ATTACH]

Also noticed that they just announced the release of new isos today.  That may have made things even easier, though I'm not certain of that.

---

### Post by 23dornot23d on 2011-08-20
I like that screenshot ..... looking good ..... 

I am just downloading the DVD 32bit version of Slackware again .... going to try to graft 
two packages together ...... 

Slackex and the original 32 bit ..... 13.37 ...... see what dependencies break ....

;)

---

### Post by cbowman57 on 2011-08-20
I'll let you break trail on that one. :)

---

### Post by sanderd17 on 2011-08-21
> **cbowman57 said:**
> Well Arch is boring, it just works. :)



yes, I know, I'm also on Arch right now

> 
The installation was easy (this time) using the net install.  With Gnome 3 as the default gnome it's super easy to install & stable as a rock.  Every extension that works on my Debian installations work perfect.  Software applications are easy to find & install, official & unofficial. The online knowledge base is amazing, which frankly takes some fun out of it, no need to interact in a forum. Just about every answer you need is already answered in the forum or a wiki.  I do kind of dig the community spirit, does seem to closely adhere to old-school linux ideals.


I believe Arch has a great wiki (which Ubuntu doesn't have) but the forums on Arch aren't so big
> 

It lacks a synaptic of course but there are a few independent gui frontends for pacman.  I personally like the command line for installing software but I'm using a gui called AppSet to browse, and occasionally install from.  Anything unofficial is usually just a matter of googling with "AUR packagename".

For installing packages, I like the CLI tool yaourt. You just type 

```

yaourt gnome shell

```

And you get a list of all gnome-shell related packages from which you can choose, both official and user contributed packages. The only disadvantage of yaourt is that you have to enter a lot of times 'y' or 'n'. Always 'y' to "do you want to install xyz" and always 'n' to "do you want to edit configuration file xyz". This should be easier.
> 

I have no idea when G-S 3.1.5 will be introduced in official channels, or if they will wait for 3.2. (3.1.5 doesn't seem available yet unofficially either)


I believe Arch always has the latest stable release in their repos. So 3.1 will never be included
> 

If I wasn't already somewhat used to net installs and the packages required for Gnome it probably would have been intimidating.  Maybe the planets were just aligned right the other night, or my mood was right, but I just cruised right through it.

I believe Arch will always be intimidating for new users, gnome 3 or not.
> 

Dressed it up in a manner that seems to compliment the Arch philosophy.

[ATTACH]200454[/ATTACH]

Also noticed that they just announced the release of new isos today.  That may have made things even easier, though I'm not certain of that.

The only problem I got with Arch was that I selected the Belgian Belnet server as mirror. Apparently that one hasn't been updated for 2 years, so I installed gnome and I was surprised I was on G2. When I changed the mirror and updated everything, I got a bunch of dependency problems (which is not so weird if you try updating an installation CD from May with packages that are 2 years old).

So I did a second installation, and this time I chose a Dutch server (a French server refused me because my ip wasn't French).

---

### Post by sanderd17 on 2011-08-21
I do have one other problem with GS or Arch.

I don't like the black cursor theme, so I selected Vanilla-DMZ in gnome-tweaktool (maybe I installed that theme first, can't remember). But changing the theme doesn't work.

When I'm in Firefox, the cursor theme is Vanilla-DMZ, but when I'm in any other program, it's still the original Adwaita. Sometimes Firefox also shows me Adwaita, and once I got Vanilla-DMZ for my complete shell, until I opened Gedit. Gedit changed it back to Adwaita, and all other programs followed.

I don't know if this is a Gnome-Tweaktool issue, a GS issue or an Arch issue.

---

### Post by bulldog on 2011-08-21
I'll keep it simple,I did a fresh minimal Debian install,no DE only the basics,from there I installed Gnome3 and the shell.
Have it reasonable working,some little annoyance,but I will try to solve that later on.

Now I'm gonna try to install some extensions and themes.
The gnatty-pack should work on Debian as well,I presume,so I will try that one first.

System-settings are working now,should have missed something in the previous install.

---

### Post by cbowman57 on 2011-08-21
> **sanderd17 said:**
> I do have one other problem with GS or Arch.

I don't like the black cursor theme, so I selected Vanilla-DMZ in gnome-tweaktool (maybe I installed that theme first, can't remember). But changing the theme doesn't work.

When I'm in Firefox, the cursor theme is Vanilla-DMZ, but when I'm in any other program, it's still the original Adwaita. Sometimes Firefox also shows me Adwaita, and once I got Vanilla-DMZ for my complete shell, until I opened Gedit. Gedit changed it back to Adwaita, and all other programs followed.

I don't know if this is a Gnome-Tweaktool issue, a GS issue or an Arch issue.

Pretty sure it's a GS issue.  I had a real fancy cursor theme installed with the Steampunk theme and in the browser they showed up, go anywhere else and they would shift back..

---

### Post by cbowman57 on 2011-08-21
> **bulldog said:**
> I'll keep it simple,I did a fresh minimal Debian install,no DE only the basics,from there I installed Gnome3 and the shell.
Have it reasonable working,some little annoyance,but I will try to solve that later on.

Now I'm gonna try to install some extensions and themes.
The gnatty-pack should work on Debian as well,I presume,so I will try that one first.

System-settings are working now,should have missed something in the previous install.

Yeah, easy to do, took me a couple days with the minimal installs to get everything running.  One little thing that annoyed me was getting the weather extension working, it required a libsoup package (don't remember the exact name).  Using looking glass helped me track that problem down.

---

### Post by bulldog on 2011-08-21
Not that easy,lol,but with a lot of errors I came to a working solution,no printer working though,and I need that damn thing everyday.
But I got it to work without installing other DE's so I have a clean app-menu.
Sound and internet are working but no network icon in the top-bar.
It's to be expected I find more of those little things which are not properly working,but overall it works.

To get everything solved I'll need a couple of days for sure :D
But I have a working fallback-session and now I have to wait until some updates will break the install.

But if I can keep this install up and running,I won't install Ubuntu anymore,and I will switch to Debian for my primary desktop use.

Time will tell.

---

### Post by cbowman57 on 2011-08-21
You should be able to get a network icon.  Look for the network-manager (maybe networkmanager) .8997 & nm-applet.  8997 isn't exactly the right number but it's close.  Printer problems I can't help with, don't have one. ;)

---

### Post by bulldog on 2011-08-21
Thanks Chuck,network icon is present,it was indeed network-manager not installed.
Still fighting with my printer,no problem though,I can use gNatty for printing.

---

### Post by cbowman57 on 2011-08-21
No problem bulldog, glad I could offer some moral support. :)

So is the system lacking cups or is it a specific driver problem?

Maybe use rcconf and see if the cups service is running?

---

### Post by bulldog on 2011-08-21
I should think it's a cups thingy,when you install with a desktop,the printer was always up and running.
Had a problem with one of the gNatty's,but the printer was always found.
Now it says no printer found.

Well I call it a day,get a headache staring at the screen :D

If I have the time,I'll look into it tomorrow.

Have a nice evening,Chuck,talk to you later.

Update:
Printer is running fine,another problem solved :)

---

### Post by bulldog on 2011-08-22
Extensions are working.
Only the alternative status menu will not behave.
And some minor issues with the gnome-tweak-tool,it doesn't display the buttons to change the date to display.
Will look for that tomorrow.
Pretty pleased with this install :p

---

### Post by cbowman57 on 2011-08-22
You need to ditch alternate-status & use fpmurphy's poweroptions extension.

Navigate to /usr/share/gnome-tweak-tools and edit the .ui to resizable=true, that should let you stretch it enough to hit the button. :)

Glad it's working good for you. Sounds like it's just a few little things so far but I'm fairly certain we can get it running right.

---

### Post by bulldog on 2011-08-22
> **cbowman57 said:**
> You need to ditch alternate-status & use fpmurphy's poweroptions extension.

Navigate to /usr/share/gnome-tweak-tools and edit the .ui to resizable=true, that should let you stretch it enough to hit the button. :)

Glad it's working good for you. Sounds like it's just a few little things so far but I'm fairly certain we can get it running right.

Thank you,both hit the nail and are working now.
Now I have to search for problems,most obvious are solved,now I have to use it and see if more problems come around the corner.

One little thing you might know,tweaktool say 'user theme extension not enabled' but it works anyway.
I'm not very good in searching config files, and you seem to know quite a bit of it.

Got another one,not critical but annoying.
In Ubuntu you have one password for administration rights.
Debian uses two and that's fine and if you want to install something you always have to be root,no problem with that.
But nautilus gives me only the users map in bookmarks,and to change that,you'll need to be root.
It changes only for root not for user.
So you can't go straight to say downloads or documents.
My thought was to give user some administration rights to perform
such minor changes,but I can't seem to find anything to add a user or to change user permissions.
This would be the set back of a minimal install I presume.
I'm not that knowledgeable to know where to look.
Maybe you have some idea's?
But as said this is not a big issue,just minor annoyances.

Thanks in advance.

---

### Post by cbowman57 on 2011-08-23
Ok, that's odd.  The simplest solution is to just install gnome-shell-extension-user-theme [https://launchpad.net/~ferramroberto/+archive/gnome3/+sourcepub/1764077/+listing-archive-extra](https://launchpad.net/~ferramroberto/+archive/gnome3/+sourcepub/1764077/+listing-archive-extra)

---

### Post by mips on 2011-08-23
> **sanderd17 said:**
> 
For installing packages, I like the CLI tool **yaourt**. You just type

You should try [packer]("https://aur.archlinux.org/packages.php?ID=33378") ;)

---

### Post by cbowman57 on 2011-08-23
> **mips said:**
> You should try [packer]("https://aur.archlinux.org/packages.php?ID=33378") ;)

Yeah, just installed it tonight.  Still learning my way around.  Been spending the last few days installing Arch to a software RAID0 partition, biggest problem I'm having is pulling in the other installations into grub but after messing with it I'm sure this is going to be my favorite & preferred distro.  If I need to get to any other installation I can use supergrubdisk2.  The performance improvement easily outweighs the inconvenience.

---

### Post by mips on 2011-08-23
Geez, you start posting early in the morning :biggrin:

---

### Post by cbowman57 on 2011-08-23
I woke up with a bit of an epiphany, had to try it out. :)

---

### Post by cbowman57 on 2011-08-23
Alright, I got grub2 installed in my Arch Raid setup, installed os-prober from AUR. Followed the instructions in the wiki & now I have easy access to my other installations, should I ever need to use one of them.

Beginning to get a little more comfortable with Arch, though installing it using software Raid0 did make it a bit more interesting, and faster. :)

So, it looks like all the experimentation & distro-hopping in search of the perfect Gnome 3.0 shell system brought me to this.  I'm really happy with it.

ps. Wish a couple SSD's were in my budget. ;)

---

### Post by bulldog on 2011-08-28
It's very quiet over here......well nothing news to report really,so I show a screenshot of the Debian-sid.
Things are going well,have sorted out a number of small issues,and have some more to go.
I can use my Debian as I choose and that's the most important thing for me.

I won't follow Chuck and Keith on the path of Arch and Slackware.
I'll read the topics to see how things go along,but I won't install them.

Because there's not really much to do here,I say thanks to Chuck and Keith,and all others who came around,for the effort they put in gNatty and LMDE,to get a working GS environment on Ubuntu and Debian.

Thanks and see you around I guess :)

---

### Post by cbowman57 on 2011-08-28
Still here bulldog. :)

Really glad you've enjoyed the little journey.  What I've discovered through all of it is that I really like using Gnome shell & look forward to watching it develop.  Another thing we've established is that G-S on Ubuntu/Debian can be as good or better than what came on the distributions that seem to get recommended for that "perfect Gnome shell experience".

Ubuntu (Linux Mint was actually my gateway distro) was/is the distribution that really got me comfortable with linux, even though I'd experimented with different distros all the way back to the mid-90's.

Debian to me is like the mother distro, so Ubuntu & the pursuit of a challenge sent me down that road & I learned a lot more in just a few weeks.  Without the education I've gotten over the past few months I would have never tackled Arch.

Which brought me to Arch, which I wouldn't recommend to anyone that just wants to do a quick install and go at it.  It's a great distro for those that really want to reach into the bowels of the OS, it's like a trip down the rabbit hole. :)

So, still here, still enjoy interacting with you guys. I feel like we've had a lot of fun & I enjoy the Ubuntu forums.  Hope to keep seeing you around. :)

---

### Post by 23dornot23d on 2011-08-28
> **bulldog said:**
> It's very quiet over here......well nothing news to report really,so I show a screenshot of the Debian-sid.
Things are going well,have sorted out a number of small issues,and have some more to go.
I can use my Debian as I choose and that's the most important thing for me.

I won't follow Chuck and Keith on the path of Arch and Slackware.
I'll read the topics to see how things go along,but I won't install them.

Because there's not really much to do here,I say thanks to Chuck and Keith,and all others who came around,for the effort they put in gNatty and LMDE,to get a working GS environment on Ubuntu and Debian.

Thanks and see you around I guess :)

Nice to see that you got it all working on Debian the [_***steampunk theme (by Sam Riggs)***_]("http://gnome-look.org/content/show.php/Gnome+Shell+Old+Steampunk?content=144320") is class ..... also thanks for helping out too on the exploits with Gnome Shell .... 

It has been a great couple of months - and I possibly learned more in the last few months on here than in the years previous.

It really does help bouncing ideas around here ....... and hope to see you around again
here or on the net somewhere ...... 

Keith .....

---

### Post by bulldog on 2011-08-28
Well I'm not going away from this forums.
I'll started my journey in 1999 with SuSe and after that Fedora.
Fooled around with them and some others, but always kept a Windows install on hand.
Then in 2006 I tried Ubuntu and stayed with it,till now.
I have a windows XP on my hdd,but I never use it anymore,I'll keep it for sentimental reasons,I guess :)
But the last months opened my eyes,Ubuntu goes a road which isn't for me.
I will surely keep an eye on Ubuntu,and how it handles with Gnome Shell.
And maybe,if all goes well,I'll install it again.
But for now is Debian the closest one to replace Ubuntu.

Have to say this last months get me awake again,you can do so much more if you want to get into it.
Before that,I started my computer into Ubuntu,did what I had to do and shut the thing off.

Now I'll explore more options and I will try other distro's as well.
But I think Arch is to much for me to handle,I simply have not the time to dive into that one.

But I learned to explore again,and not be happy with what they trow at you,mostly thanks to you guys.

---

### Post by cbowman57 on 2011-08-28
Yeah, these past few months have really energized & excited me about computers again.

Having you guys to act as a sounding board, ask questions, making suggestions, offering moral support, etc... really made it a lot of fun.

Maybe I'll start a thread over in the community cafe called the "gNatty Bunch" just so we can socialize and have a bit of a home base.

---

### Post by bulldog on 2011-08-28
> **cbowman57 said:**
> Yeah, these past few months have really energized & excited me about computers again.

Having you guys to act as a sounding board, ask questions, making suggestions, offering moral support, etc... really made it a lot of fun.

Maybe I'll start a thread over in the community cafe called the "gNatty Bunch" just so we can socialize and have a bit of a home base.

That's a great idea,I felt a little lost :P now everything is working fine.

I'll bring the beer :guitar:

---

### Post by cbowman57 on 2011-08-28
WTH!  Here we go. :lol:

[The gNatty Bunch http://ubuntuforums.org/showthread.php?p=11196012#post11196012]("http://ubuntuforums.org/showthread.php?p=11196012#post11196012")

---

### Post by cbowman57 on 2011-09-01
Restoring the old Delete key behavior.  This isn't my fix, and I've seen  it on other blogs & articles but the last time I tried it would not  work.  This method did.

Stolen from the Arch forum

> 
Quick fix:
Run dconf-editor, and open:
org -> gnome -> desktop -> interface
Enable "can-change-accels".
 Open nautilus, select any file/directory, then click "Edit" from menubar, and hover on "Move to Trash" menuitem.
While hovering, click on your delete key. The accel should change from "cntrl+del" to "del".
 Make sure you have selected a file, else the "Move to Trash" menuitem will be greyed out.
 I suggest you disable "can-change-accels" afterwards, to prevent accidental accel changes.

If it didn't work create an empty folder ~/.gnome2/accels & try again.

---

