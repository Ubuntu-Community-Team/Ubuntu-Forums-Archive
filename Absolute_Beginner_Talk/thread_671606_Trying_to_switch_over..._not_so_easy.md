---
title: "Trying to switch over... not so easy"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by VexenX on 2008-01-18
Brand new and feeling dizzy... any good suggestions for a newb appreciated too, been trying to dive in but I think I'm a little overwhelmed.

1.) Can't play mp3s, not sure why, tried adding and removing many players hoping one would help me with that, some say they are installing (Amarok) but it never does, and Kaffine I thought was supposed to be able to play mp3s by default. Pretty much I was under the impression the ability to play mp3s would be built in somehow and if it should, I'm not sure what happened.

2.) I've tried numerous times to install my video driver, but I know dos, not Unix, and pretty much I am forced to reinstall my OS every time I make an attempt at installing it. I'd like some tips, it is an NVidia GeForce 440 Go. Also, how do I ... not have to reinstall everything should I make an error, as undoubtedly I will while trying to learn.

3.) Can't get a psp to usb controller converter to work in EpsxE this is not nearly as important as the first two, but I have been able through much fiddling and exploring of suggestions to get it to spit out garbled garbage to the shell. 

4) Is there someplace that breaks down packages based on compatibility, I'm not sure if this is even a worth while question, but I've noticed that some solutions are complicated by compatibility. Please be patient with me, and I apologize for my ignorance.

System info:
OS: Fiesty Fawn 7.04 which appears to be Gnome based (Not sure if that is needed)

1.8 ghz Dell Latitude
256mb Nvidia GeForce 440 go
 512 mb of Ram
When stuff works, it works very well, and effectively, and when it doesn't, I feel like I've been locked in a cage with 1,000 keys and only a couple work. lol Thank you for responding, much appreciated.

---

### Post by oldb0y on 2008-01-18
About your first question. Try this in a terminal  ```
sudo apt-get ubuntu-restricted-extras
```

Oh! And about your Nvidia-card, have you tried enabling the restricted drivers? System>Administration>Restricted Drivers, Tick of for Nvidia;)

---

### Post by VexenX on 2008-01-19
sudo apt-get ubuntu-restricted-extras returned and invalid option error. But thanks for a suggestion of some sort heheheh, I'm still researching solutions, just have to take a break when it gets too confusing. On enabling the restricted Nvidia driver, that causes my system to lock up while booting, and at this point I lack mastery of the unix shell to get out of it without reinstalling. lol it is very strange relinquishing all of the power you've worked so hard for, so that waaay down the road you'll have more. Well, onward I guess.

---

### Post by thelatinist on 2008-01-19
> **VexenX said:**
> sudo apt-get ubuntu-restricted-extras returned and invalid option error. But thanks for a suggestion of some sort heheheh, I'm still researching solutions, just have to take a break when it gets too confusing. On enabling the restricted Nvidia driver, that causes my system to lock up while booting, and at this point I lack mastery of the unix shell to get out of it without reinstalling. lol it is very strange relinquishing all of the power you've worked so hard for, so that waaay down the road you'll have more. Well, onward I guess.

Before you do that, you need to go to System > Administration > Software Sources and make sure all but the last checkbox are checked.

Then go to terminal and do:

```
apt-get update
sudo apt-get **install** ubuntu-restricted-extras
```

Notice the missing option "install" in the command you used?

---

### Post by isparkes on 2008-01-19
I have to admit as an ex Windoze user myself, I have sympathy for you. The media area is one those that is confusing when you first get going - There are a LOT of options, and none of them seem to work. I can only give you the vague idea of what I did, but don't be disheartened, we always have to start somewhere, and you just have to recover from being "institutionalised" by the Windows world.

So, here are the things that I did:

I was a WinAmp user, so I installed **XMMS**, which is a good clone.

I had also used **VLC** on Windows, so I installed that as well. It's nice, but doesn't do playlists.

I'm not that keen on **Amarok**, and have removed it. Instead of this, I have gone over to **Rythmbox** which is an iTunes clone.

To get these working with the different media formats, I ended up installing everything for **GStreamer**. A lot of the players use this library, so it's fairly important to set it up.

Go into Add/Remove Applications, and search for "streamer". Then install everything that looks relevant. "Gstreamer extra plugins" is probably the one you need most.

Hope this helps. Keep with it - I'll never go back, and things get easier and easier as you go on.

---

### Post by acridfusion on 2008-01-19
I got mp3's to work by clicking on one, it opened through the movie player, then it prompted me to search for codecs. after agreeing to get the update it worked, then i closed that program, proceeded into my rythimbox and it worked in there too

---

### Post by VexenX on 2008-01-21
Interesting, this seems related to my mp3 playing issue since it mentions Gstreamer, which initially I suspected, but had gotten to bogged down by learning other stuff.

Could there be a package causing conflict with msttcorefonts? How would I check that... synaptic package manager perhaps? I'm gonna go and look. Thanks! :)


vexenx@vexenx-laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-restricted-extras: Depends: gstreamer0.10-plugins-ugly but it is not installable
                            Depends: msttcorefonts but it is not going to be installed
E: Broken packages

EDIT-------

Apparently cabextract is required for msttcorefonts. Hmm... I don't see that anywhere just yet... I'll look for something like that.

---

### Post by thelatinist on 2008-01-21
> **VexenX said:**
> Interesting, this seems related to my mp3 playing issue since it mentions Gstreamer, which initially I suspected, but had gotten to bogged down by learning other stuff.

Could there be a package causing conflict with msttcorefonts? How would I check that... synaptic package manager perhaps? I'm gonna go and look. Thanks! :)


vexenx@vexenx-laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-restricted-extras: Depends: gstreamer0.10-plugins-ugly but it is not installable
                            Depends: msttcorefonts but it is not going to be installed
E: Broken packages

EDIT-------

Apparently cabextract is required for msttcorefonts. Hmm... I don't see that anywhere just yet... I'll look for something like that.

You need to enable the universe and multiverse repositories in System > Administration > Software Sources.

---

### Post by oodledoodle on 2008-01-21
the problem here is not that ubuntu doesnt know how to deal with mp3s, but instead mp3 is a file format that carries several licensing issues and as such cannot be enabled by default. just so you don't go around thinking that linux can't do things... :D

---

### Post by VexenX on 2008-01-21
I have enabled universe and multiverse before the last post, and alas, still no luck. But still, a step in the right direction since I'm learning stuff... I was looking up the cabextract but didn't have much luck and it I don't see it under the synaptic dealy. Perhaps I can find information for installing it through google...?

EDIT: I tried this

vexenx@vexenx-laptop:~$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cabextract is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cabextract has no installation candidate
vexenx@vexenx-laptop:~$ 

Heheheh, nothing happened, but... well... at least I can use it for reference later...

Edit:

I had changed the update server from the main server to something else, I changed it back and my options blossomed like flowers in spring. Cabextract is installed, so is msttcorefonts, retrying "sudo apt-get install ubuntu-restricted-extras"

At this point I have to mention that I've noticed the most educational thing you can do is break your system arbitrarily based on ignorance, and then force yourself to fix it, learning what you broke and possibly why, but at least how to fix it... let's hope the learning continues...

---

### Post by thelatinist on 2008-01-21
You should not have to manually install those dependencies.  Could you please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by oldos2er on 2008-01-21
cabextract should be in the universe repo. Can you post the output of "cat /etc/apt/sources.list"?

---

### Post by biohypnotix on 2008-01-21
I am not very good at directions so I hope these links will help some.

> Can't play mp3s, not sure why.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/mp3](http://www.psychocats.net/ubuntu/mp3)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


> I've tried numerous times to install my video driver

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
[https://help.ubuntu.com/community/RestrictedDrivers](https://help.ubuntu.com/community/RestrictedDrivers)
[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIA](https://help.ubuntu.com/community/RestrictedDrivers/NVIDIA)


> Also, how do I ... not have to reinstall everything should I make an error

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)


> Fiesty Fawn 7.04 which appears to be Gnome based

Feisty Fawn Ubuntu 7.04 indeed uses Gnome desktop by default. The latest version of Ubuntu is 7.10 (Gutsy Gibbon) and also uses Gnome by default, you may want to upgrade when you have the free time.

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by VexenX on 2008-01-21
> **thelatinist said:**
> You should not have to manually install those dependencies.  Could you please post the output of:

```
cat /etc/apt/sources.list
```

vexenx@vexenx-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse


## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.) 
## Medibuntu - Ubuntu 7.04 "feisty fawn" 
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs) 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe

There ya go. Thank you for your help. :)

---

### Post by thelatinist on 2008-01-21
That looks right.  What happens if you do:

```
sudo apt-get update
```

?

---

### Post by VexenX on 2008-01-21
Okay, I got mp3s to play. After I expanded my options by selecting the right update server, I noticed that my errors in playing mp3s said something about a missing demux. I opened Synaptic package manager and searched for demux and installed any package that mentioned that, and now mp3s play. Now on to the other issues... namely updating the video card without my system crashing when I reboot... or at least mastering backing it up and restoring so I can fiddle around from before my last mistake.

Thx Thx!
   VexenX

---

### Post by ugm6hr on 2008-01-21
Is there a reason you are using an older version of Ubuntu?

The latest (7.10 Gutsy) will prompt you to install necessary codecs if you try and play a restricted format.

Just a thought....

As for the NVidia card - not sure if it compatible with latest drivers, but Envy might sort that out for you.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Also - if you are really struggling, I hear Linux Mint is easier to do these things on (although I have only briefly played with the LiveCD myself).

---

### Post by Presto123 on 2008-01-21
> **oldb0y said:**
> About your first question. Try this in a terminal  ```
sudo apt-get ubuntu-restricted-extras
```

Oh! And about your Nvidia-card, have you tried enabling the restricted drivers? System>Administration>Restricted Drivers, Tick of for Nvidia;)

After checking that it shows the driver (If it doesn't...just wait about following the link):

[http://ubuntuforums.org/showthread.php?t=594255](http://ubuntuforums.org/showthread.php?t=594255)

With 7.04, that seems to work fine and I did a couple of installs using the same drivers, unless it is an older card. Just follow it up to the point it starts talking about Beryl as Beryl is now outdated.

---

### Post by oldos2er on 2008-01-22
Go to System, Administration, Software Sources, and make sure multiverse, restricted, and main repos are enabled.

---

