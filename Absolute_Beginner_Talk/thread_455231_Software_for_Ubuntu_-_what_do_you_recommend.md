---
title: "Software for Ubuntu - what do you recommend?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-26
Software for Ubuntu - what do you recommend?

I'm a relatively newbie to Ubuntu Linux but have been using it pretty intensely for the last couple months.

It seems everytime I read these forums, I find another great piece of software.  

I particuarly liked the following:

Beryl, NXSERVER, putty, psftp, ssh, wine, CrossOver, Automatix, ntfs-3g, MonoDevelop, Gimp, parted, etc.


Then there are all the configuration tips such as turning off ipv6, installing eSword, restoring all currently installed packages to a fresh install, building a kernel, etc.

So, what are some other goodies or tips out there that you recommend?

Thanks

Carl

---

### Post by meng on 2007-05-26
Where to start? So many possibilities, but it depends on what you use your machine for.
An alternative approach to asking this question is to say "I think it would be really cool if I could <insert wish here>" and then you will get specific suggestions about which program/s you may find useful.

---

### Post by starcraft.man on 2007-05-26
[Linux app finder ]("http://linuxappfinder.com/")for all software discovery needs, there is even a windows alternatives section on front page. Easy question to answer in only one line :D.

---

### Post by Bachstelze on 2007-05-26
Frozen Bubble !

---

### Post by cwmoser on 2007-05-26
So far I've been able to get much of my Windows XP functionality onto Ubuntu.  I've gotten Quicken and Quickbooks to work using Cross Over; remote desktop to Ubuntu via nxserver and ssh; eSword via wine; and superior eye candy than Vista using Beryl.


The only areas so far that I have come away disappointed is being able to setup a VPN to my work and getting ntfs-3g to work using the gui browser.  I've found openvnc ambigious and the selection of a VPN from the Nework-Manager applet does not exist on my configuration of Ubuntu.

All in all, I think Ubuntu can be a definite replacement to Windows once all these add-on packages are properly installed.  I think Dell would be smart if they delivered a fully configured Ubuntu along with a book documenting various ways to use Ubuntu.  I think Ubuntu is that close.  Oh well, I'm getting off topic.

Thanks

Carl

---

### Post by Ek0nomik on 2007-05-26
> **HymnToLife said:**
> Frozen Bubble !

I just installed frozen bubble and I have become enlightened.

---

### Post by seetho on 2007-05-26
I use it for work so the most useful apps for me (other than the preinstalled ones) are:

1. VYM (I use for planning almost everything - very useful - highly recommended).
2. Skype
3. Sudoku (Standard on Feisty)
4. Thunderbird

---

### Post by cwmoser on 2007-05-30
Now that was one heck of a recommendation - VYM - "View Your Mind".  Thanks.

VYM is a great tool that I think I can use a lot -- I just used VYM to describe a complex software project I am working on.

I too highly recommend it.

Thanks for the recommendation.

This is what I like about this thread -- getting input from others regarding software they have found especially useful.  Any other great recommendations?

Carl





> **seetho said:**
> I use it for work so the most useful apps for me (other than the preinstalled ones) are:

1. VYM (I use for planning almost everything - very useful - highly recommended).
2. Skype
3. Sudoku (Standard on Feisty)
4. Thunderbird

---

### Post by starcraft.man on 2007-05-30
Well if you use the terminal a lot, which I do, I recommend tilda, its a neat little app. Install it and give it a shot :).

---

### Post by ivesjd on 2007-05-30
I use yakuake instead of tilda, just like it more. Also another I cant do without is katapult. Like quicksilver in OS X, but not quite as good.


so 
yakuake
katapult

---

### Post by Lucifiel on 2007-05-30
Swiftfox(an enhanced version of Firefox which is quite crashy on Linux), Songbird(for music),  and Macopix(if you're into wide-eyed anime girls).

---

### Post by daimaru on 2007-05-30
if ur using vector graphics xara Xtreme 
install: sudo apt-get install xaraxl

ps: would be helpful if ppl posted apt-get commands, repositories or links to help others install those favorite progs of theirs.
im still looking for the "view your mind" program would have been easier to just paste a console command :(

---

### Post by cwmoser on 2007-05-31
I installed VYM via Synaptic Package manager.

i.e. System -> Administration -> Synaptic Package Manager.
Search for VYM

VYM is a great piece of software.

Carl

---

### Post by purplearcanist on 2007-05-31
You can try ClamAV, a virus scanner for Ubuntu (for all of the Windows viruses and malware).

```
sudo apt-get install clamav
```

If the installation has errors, run the command:

```
sudo apt-get -f install
```

---

### Post by 13thMonkey on 2007-05-31
```
sudo apt-get remove frozen-bubble
```

Helped speed up the user inputs on my PC no end :p

---

### Post by 13thMonkey on 2007-05-31
```
sudo apt-get remove frozen-bubble
```

Helped speed up the user inputs on my PC no end :p

---

### Post by DreamcastJack on 2007-05-31
I really enjoy Last.fm (in the repositories) "sudo apt-get install lastfm"  its awesome!

---

### Post by seetho on 2007-05-31
> **daimaru said:**
> ps: would be helpful if ppl posted apt-get commands, repositories or links to help others install those favorite progs of theirs.
im still looking for the "view your mind" program would have been easier to just paste a console command :(

Like cwmoser says - a good place to start is always to look at Synaptic Package Manager even if you finally decide to install with apt-get or aptitude or Add/Remove...

Of course there's Google!  Actually that's how I stumbled upon it in the first place.  If any of you are interested here the link to save you 0.03s of search time: [http://www.insilmaril.de/vym/](http://www.insilmaril.de/vym/)

But if you really want the commandline code:

```
 firefox http://www.google.com/search?q=view%your%mind
```

Enjoy...

---

### Post by Scheater5 on 2007-05-31
Personally, I can't like without AmaroK.  Music player that blows iTunes out of the water.  

> sudo aptitude install amarok

If you use gnome,then you already have Gaim, but if you use Kubuntu then I suggest installing gaim to use instead of Kopote.  

> sudo aptitude install gaim

I'm also beginning to think that QTparted is far more useful than Gparted.  Gparted is refered to as a "weapon of mass destruction," which I think is because it will let you do things you're not supposed to - like resizing an ex2 partition with data on it.  While you should probably know what you can and can't do to any given partition, QTparted more often than not won't let you break the rules.

---

### Post by 13thMonkey on 2007-05-31
@DreamcastJack

Amarok will also play/scrobble LastFM tracks and will incorporate them into smart playlists too.

---

### Post by ivesjd on 2007-06-25
something I find usefull  is ```
aptitude search "query" 
``` and inputing what your looking for in place of "query" will search in terminal.

---

