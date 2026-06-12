---
title: "Dapper vs Edgy vs Feisty"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by jrlii on 2007-04-22
I've always been kind of conservative about updates, going back to the days when x.0 updates for the mainframe generally didn't work.

I understand Edgy was a release where they pushed the envelope a lot.

Is Feisty a release where they are consolidating stuff where they were pushing it on Edgy?

Is Edgy stable enough to upgrade at this point? Or is Feisty more stable, even at this point?

At the moment, I'm using Dapper for your ordinary browsing, e-mail (Thunderbird) & office stuff + Digital Audio Workstation duty and DVD player.

Feisty sounds cool, but is it stable enough for an old stick in the mud like me?

BTW: I don't have broadband at home. I'll need to download a ISO image at work and burn a CD, 'cause a 27+ hour download is unlikely to work. . . Which image should I download?

Thanks in advance!

---

### Post by oilchangeguy on 2007-04-22
look at all of the posts from the last few days from people having trouble with 7.04. if you've got 6.06 set up the way you like it, and everythings running fine. then there's no reason to upgrade. i'm going to stay with 6.06 until the next LTS version comes out. which should be sometime in 2009.

---

### Post by nixclusive on 2007-04-22
Better wait for a week or two and let the (lets not hope) bug reports roll in. Which image eh? try the live CD first, you'll get a feel of what's in it for you and how stable its going to be.

---

### Post by mabelrxu on 2007-04-22
plenty of people stay back, and have no problems ... but then again, although newer versions may have problems when they come out, they are all designed to be backwards compatible (not always work, but still ... they're trying), so upgrading shouldn't really harm you either ... I've heard a lot of people like the dapper network manager better, though, so you might want to lock that version, or something ... so if you're using wireless, you might want to think about that

i personally love upgrading cause of all the cool new wallpapers and effects and stuff, and as for version ... if you're using a i386 pc computer (if you don't know, you probably are), then you can either download the desktop version (for most people) or the server version (if you're really wild and want to give it a try ... i haven't even tried it yet ;) )  ... also, you can download alternative cd if you want, for more advanced configuration

oh yeah, if you already have (k, x)ubuntu, you don't need to download a cd at all ... just do a 
```

sudo apt-get update
sudo apt-get dist-upgrade

```
after you have locked the packages you want to keep, and apt-get will do the rest

p.s. you type those commands into the terminal window, and it will ask you for the root password, which is usually the password of the first account you created on that computer, unless you changed it or something weird happened

---

### Post by Seisen on 2007-04-22
The only difference is they updated the kernel and added some more packages to it. This might explain it better, just ignore the beta part.

[https://wiki.ubuntu.com/EdgyEft/Beta]("https://wiki.ubuntu.com/EdgyEft/Beta")

[http://www.ubuntu.com/testing/feistybeta]("http://www.ubuntu.com/testing/feistybeta")

---

### Post by old_geekster on 2007-04-22
I installed Edgy two months ago.  It was a bit less stable than I had hoped.  However, I finally got it setup the way I wanted it to be.  Then, along came Feisty.

I said that I would play the wait-and-see game.  This lasted until last Sunday.  I upgraded to Feisty Beta.  At this point, it was a great decision.  It has the feel of a far more mature OS.

I am using the 32-bit desktop version on my 64-bit rig.  I couldn't be more happy with it.

---

### Post by ubromtoo on 2007-04-22
MabelRXU :

  What does "after you have locked the packages you want to keep, and apt-get will do the 

  rest "  mean, in Newbie-speak ?   :-k 


              I'd like to go from Dapper (currently) to Edgy .  Thank you

---

### Post by Nythain on 2007-04-22
i started with dapper... then switched to edgy when it came out... edgy was great, stable as could be... had a few issues here and there... then somehow my kde got nuked a couple weeks before the official feisty release... at that point i grabbed the betta, and been runnin it since... i like it best so far... though ktorrent keeps crashing, but i think that has more to do with my hard drive than anything... moral of the story is i havent had any problems with any of them yet, and so far like feisty the most

---

### Post by kfehr911 on 2007-04-22
Well I upgraded from Dapper to Edgy to Feisty with in the last two weeks.  On the whole considering that we roughly do the same thing I would have to say that you are better off with Edgy.  I'm not very experienced with computers in general but I would have to say that if you want speed and stable Edgy is the way. I find that I'm a little sluggish with Feisty.  I need to post a few questions myself to figure out how to speed in up a bit.  If you are happy with Dapper you will be happy with Edgy.

---

### Post by 3rdgear on 2007-04-22
I'm an old-timer too. I had been using Dapper without too much trouble, but really wanted to try to upgrade. I had a major problem with feisty, as my mouse would not work with it once it was installed. Can't do anything without a mouse..........

I installed edgy today, and so far, seem to be happy with it. 

I like the live cd's because you can try it out before using, but found that the alternate cd is much easier and faster to install.  The live cd's take forever to boot, and are pretty sluggish running.

---

### Post by mabelrxu on 2007-04-22
ok ... so say, for example, that you absolutely love the dapper network manager and refuse to upgrade, even willing to put up with problems, but you want to upgrade the rest of your computer ... here's what you do

you goto synaptic, then find network-manager and network-manager-gnome ... select the packages and under the package menu, select "lock version" ... if it's not there, then you can goto command line and through apt-get, aptitude, or dpkg, do something like apt-get --help to find the correct command, then lock the version for both network-manager and network-manager-gnome

now, when you upgrade or dist-upgrade, network-manager and network-manager-gnome (and any other version locked packages) will not upgrade ... actually, i'm not sure about dist-upgrade, but I'm thinking it has the same behavior as plain old upgrade ...

---

### Post by pppetter on 2007-04-22
Any version of ubuntu gets more and more stable after it has been in use for a while, therefore I would say that if you really want a stable OS, continue to use dapper. Also note that upgrading to the next version MAY(unlikely, but it _may_) brake something.

Anyways. Since you don't have a broadband connection you will need to download the Alternate CD.
First of all, you will need the Edgy Alternate CD, becouse you cannot upgrade directly from Dapper to Feisty. You must first upgrade to Edgy, then you can move on to upgrading to Feisty.

Choose a doanload mirror and then 6.10 (Edgy) and Alternate CD
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by Billium on 2007-04-23
I'm finding Feisty fairly easy to work with, I had Dapper 64-bit, and was never really happy. The only problem is the nVidia driver situation. Screen resolution can't be changed and the driver is unsupported by the computer. I was told if I went with the 32-bit version this time, some of the problems would go away. We'll see over the next couple of days.
I have spent most of the day on the forums reading others problems and now my little screen resolution one doesn't seen so bad.

Still looking for help with the drivers.

---

### Post by kfehr911 on 2007-04-24
One thing that I would really like to know is speed.  Why do I feel that my system is lagging since I upgraded to Feisty. What have I really gained?  I heard more stable kernel ,which is important but I could care less about desk top effects.  But if it a better kernel would the over all performance and speed better hard drive since I used Dapper but I still feel that preformed better.  The only real tweak was that I was using Monzilla's version of Firefox 2.0.  Next was Edgy and things were good.  A more help on the command line and improved speed and performance, on board Firefox2.0 and a fresh look with or with out Beryl to make friends jaws hit the floor. Beryl is not practical because it is filthy  resource  pig but fun to play with.  But now with Feisty I'm at a loss.  Slower response time in general and a considerably slow Firefox 2.0 and Buggy little things. Not that the bugs are a problem I know that it is fresh to the public but even the little things like the repositories being so swamped that even downloading the upgrade was painful.  I would like to hear some solid options on some good reading ( I will take it from there)

---

### Post by mabelrxu on 2007-04-24
important keyboard shortcuts:

alt + F1 opens the applications menu in ubuntu, ctrl + esc opens the applications menu in xubuntu ... from there, you should be able to open a terminal to run anything you want ... or to edit your config files to see if you can get your mouse working ...

---

### Post by carloslosgrande on 2007-04-24
I've been running Dapper since about Sept last (I think) and recently added a new hard drive which is now running Feisty.
I've got a Dell 5150 about 12 months old. Dapper works well and is very stable and I'm keeping it for that very reason. Don't use it much anymore though.

I was never able to successfully load Edgy - it didn't like my ATI card, said I didn't have one actually.
Once, I got it through upgrade and it looked nice but it died on restart.

My opinion on Feisty is, its a lot easier than Dapper, there are many 'intuitive' parts to the system. Its much easier for to run my wireless and my vids and music and playing around with setup and its SSOOO much faster.
I'm certainly not an experienced user or much better than when I began with Ubuntu, but I'm happy to recommend Feisty for a first time user.

---

### Post by Dai Bando on 2007-04-24
I was running Dapper for a while when Edgy came out; so I downloaded the CD and installed it. I tried it for a while but didn't think it was as good as Dapper so I tried to re-install Dapper. There was no way that I could boot the CD; I made three(3) copies of the disc but the same thing happened. Then Fiesty came out so I thought I would try that, but same problem, I could not boot from the CD although I have no problem booting from the Edgy CD.

---

### Post by edgecoug71 on 2007-04-24
Feisty is ok in that I have encountered a few bugs myself and had to iron them out but once you do you will like it....If you are satisfied with your current setup, then I would continue to use it for a while longer.....I am running Feisty w/ beryl on my HP laptop and one of my desktops and I have it working fine now, with an occasional glitch with a piece of hardware but its worth it, trust me, its always a good thing to play around with the OS and alter it yourself so you can call it your own.....Hope all works out for you....

---

### Post by mabelrxu on 2007-04-26
> **Dai Bando said:**
> I made three(3) copies of the disc but the same thing happened. Then Fiesty came out so I thought I would try that, but same problem, I could not boot from the CD although I have no problem booting from the Edgy CD.

did you write the iso's using a **CD Image** writing software? just using a cd writing software's not good enough ... did you burn the iso for edgy from a windows computer?  I think the default burner that comes with windows is an image burning software, not only a data burning software ... for windows, I use ImageBurn ... have yet to find alternatives in ubuntu, since I don't burn stuff on my laptop all that often.

---

### Post by Dai Bando on 2007-04-28
I downloaded to my desktop and then burnt it with K3b as a data disc; is this wrong.

---

### Post by freesitebuilder on 2007-04-28
> **mabelrxu said:**
> ok ... so say, for example, that you absolutely love the dapper network manager and refuse to upgrade, even willing to put up with problems, but you want to upgrade the rest of your computer ... here's what you do

you goto synaptic, then find network-manager and network-manager-gnome ... select the packages and under the package menu, select "lock version" ... if it's not there, then you can goto command line and through apt-get, aptitude, or dpkg, do something like apt-get --help to find the correct command, then lock the version for both network-manager and network-manager-gnome

now, when you upgrade or dist-upgrade, network-manager and network-manager-gnome (and any other version locked packages) will not upgrade ... actually, i'm not sure about dist-upgrade, but I'm thinking it has the same behavior as plain old upgrade ...

So when Ubuntu is upgraded, will it also upgrade any packages that have later versions in the repositories? Or does this just refer to system packages, that are part of Ubuntu itself?

---

### Post by silkstone on 2007-04-28
AFAIK it will upgrade everything for which a newer package exists, but retain the settings in the /home/username folder.

I'm currently using Edgy on a desktop machine and Feisty on a laptop, and really I can't see a lot of difference except that Feisty is much better with wireless cards and some graphics cards straight out of the box. That's why I waited for Feisty before trying to install on the laptop.

However, there are some bugs in Feisty, and I'm not at all tempted to upgrade the desktop machine just yet. If it works, don't fix it - or at least wait until you're sure that the fix is going to be a genuine improvement.

---

### Post by kittyhawk63 on 2007-04-28
I would order a copy of Feisty just for a good backup. It will have a professional label as well. Below is a site where the CD and shipping are free.

```
https://shipit.ubuntu.com/
```kh

---

### Post by jerrylamos on 2007-04-28
Dapper was a great revelation for me, having given up on Red Hat et. al. after struggles.

Dapper "just worked" on 3 of the 6 computers on this line.  Fine.  Edgy did no better.  It so chanced that the 3 computers it did work on were best case for me.

Feisty Fawn I've been on through Alpha and Beta with bruises, no surprise.

I was surprised how many bugs there were left on the Feisty Fawn release level.  Four were showstoppers to me until workarounds were posted on Launchpad.  See my posting "Workarounds" on "Installation and Upgrades".  A couple more were/are anklebiters & annoyances.  However, after all that, Feisty works on all 6 computers.  I'm in process of trying wireless, which did work on Dapper.

I think I saw that with Gutsy Gibbon they were looking to polish existing function rather than install a bunch of new packages.....I would like "persistent" to work; CD Live can install packages, save files, portable across different computers, ...   Mid February the developers picked up some boot scripts from Debian which killed "persistent".  

One clue is to go to ubuntuforums.org and click on New Posts, and count the number of posts where people are having  trouble with whatever the latest release is, in this case Feisty.

That said, I'm running Feisty mostly, except when "persistent" is needed, then Puppy has the best menu driven setup, no line mode commands required.

Cheers, Jerry:(

---

### Post by mabelrxu on 2007-04-28
> **Dai Bando said:**
> I downloaded to my desktop and then burnt it with K3b as a data disc; is this wrong.

yes, writing an .iso as a data disk is bad since although it does write all the information correctly, it won't make your disk a bootable disk.  In K3b (based on screen shots) do this instead:

select copy cd (or dvd or whatever)
under source, see if you can select a .iso file
if not, goto advanced tab and search for it there

then, you should be able to burn your .iso directly onto cd ... this method ensures that the disk will be written as bootable AND with all the correct information

hope this helps ^_^

---

### Post by mabelrxu on 2007-04-28
dist-upgrade upgrades the version (aka edgy to feisty, for example) while upgrade just upgrades the regular packages ... upgrading the version of your linux also changes core packages ... or something like that ...

hope this helps ^_^

---

### Post by carloslosgrande on 2007-04-28
Yeah, you need to burn it as a CD or DVD ISO image file. Its an option in the 'tools' menu.

---

### Post by jrlii on 2007-04-29
Thanks for all the replies. I upgraded from Dapper to Edgy. 

I think I'll wait till Ubuntu Studio is done before upgrading to Feisty. . . That'll probably have a little more stable version of Feisty, and be packaged with all the multimedia stuff.

---

### Post by Dai Bando on 2007-04-30
Thank you mabelrxu that worked fine:)

---

