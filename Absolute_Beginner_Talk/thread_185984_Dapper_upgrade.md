---
title: "Dapper upgrade"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-06-01
Hi all !

I have a small problem here. 

I really want to try out Dapper. My concern is, I finally got Breezy set up with my drivers installed all the stuff I want, costumized Gnome to what I like and installed a lot of games and apps I love.

Now Im thinking of doing a sudo apt-get dist-update, but last time I did that (from breezy to dapper) my system broke, and I had to reinstall.

Is there any way I can make sure my system does not break when I do this update? Or is there a way I can install Dapper from the CD, and still keep my old settings?

Thanks a lot for reading.

---

### Post by PriceChild on 2006-06-01
If you use the update manager....

sudo update-manager -d

Then you should be fine. It will check out most problems before doing anything unreversible.

Make sure you have ubuntu-desktop installed.

My upgrade didn't like xubuntu or firestarter being installed.

Good Luck

---

### Post by hobbit1983 on 2006-06-01
I successfully upgraded from Breezy to dapper using the same method as price child suggested.  The great thing was that the update manager accepted that I may have customised some things and installed extra programs.  Even customised gnome. And it kept all those settings.

I would suggest however that backing up your system (or /home at least) before you upgrade.  Although everything should be fine, it's always good to have plan b

---

### Post by aktiwers on 2006-06-01
When I run the  sudo update-manager -d I get this. (see screenshot)

What should I do, so my Dapper upgrade goes painless? 

Thanks

---

### Post by R3linquish3r on 2006-06-01
do as it says.

First do a sudo apt-get dist-upgrade (make sure you /etc/apt/sources.list file is set to breezy and not dapper!) this will make sure you ahve the latest upgrade of the update manager.

Then do suo "update-manager -d" again

---

### Post by Turtle.net on 2006-06-01
It is important (I think) to do a complete upgrade of Breezy before installing Dapper. That is to say
```
$  sudo update-manager
```
to see all the available upgrade and then installing them.
The next step will be ```
$  sudo update-manager -d
```
and everything should goes just fine :)

---

### Post by aktiwers on 2006-06-01
Okey thanks!

It seamed that the python2.4-gd sun-j2re1.5 x11proto-gl-dev programs where blocking something or I dont know.. they kept saying they couldnt get updated. 

So I removed them all with

 sudo apt-get remove python2.4-gd sun-j2re1.5 x11proto-gl-dev

And now I did the 

sudo update-manager 
sudo update-manager -d
 
And everything seam to be okey now. 

I have a few more questions though. But thanks alot so fare.

1) Should I just click the "New Distribution release '6.06 LTS' is available. [Upgrade]" button in the Software Updates aplication?

2) Will I have to reinstall all my apps, games and drivers after this upgrade?

Thanks and sorry if im being a bit paranoid.

---

### Post by morequarky on 2006-06-01
I would like to upgrade using that method but it doesn't work for me.  My partitions are different and though each partition has space, the update tells me that I can't upgrade because I need 40 some mb of space, but I don't know where it wants the 40 some megs.  before I launch '-d' I check my partitions and I have enough space on each partition and it still fails.

'-d' just refuses to use my free space....how do I upgrade directly from the CD?

---

### Post by aktiwers on 2006-06-01
Morequarky, please make a new threat.

Can anyone answer the 2 questions above?

Thanks a lot, cant wait to try Dapper :)

---

### Post by Trab on 2006-06-01
1) yes just click that.
2) no, almost all of your programs and settings will be the same. the only issue would be if a dependancy failed, and it will tell you about that before you upgrade.

this is almost similar to the method i used to update, during flight 7, and it worked fine. just a suggestion for future reference, you should have your /home directory on a seperate partion, its much safer that way.

upgrade and enjoy!
-Trab

---

### Post by catlett on 2006-06-01
[http://www.ubuntuforums.org/showthread.php?t=178903](http://www.ubuntuforums.org/showthread.php?t=178903) Be carefull if you like your Breezy install. Dapprt might not turn out the way you want it. I was very surprised by my dist-upgrade

---

### Post by Turtle.net on 2006-06-01
Excuse me catlett but you should develop your post a little bit...why were you surprised ? That was a good surprise ? a bad one ?

Ok, sorry I didn't read all the message after the link.
Maybe a little be too enthousiast, isn't it ?

---

### Post by aktiwers on 2006-06-01
[quote=catlett][http://www.ubuntuforums.org/showthread.php?t=178903]("http://www.ubuntuforums.org/showthread.php?t=178903") Be carefull if you like your Breezy install. Dapprt might not turn out the way you want it. I was very surprised by my dist-upgrade[/quote]

Thanks a lot for your warning! The exact same thing happend to me 3 weeks ago. Thats why im so paranoid now. Well I just burned it to a CD, and just made a copy of my Home Folder, so I will give it a shut(and cross my fingers).

---

### Post by catlett on 2006-06-01
[QUOTE=Turtle.net]Excuse me catlett but you should develop your post a little bit...why were you surprised ? That was a good surprise ? a bad one ?[/QUOTE]
The link is to my post of what happened after my dist-upgrade. It killed my configuration. No x, no mounted partitions etc everything wiped out. No cofigurations were saved. I ended up doing a reformat and fresh install from cd.

---

### Post by aktiwers on 2006-06-01
Okey, here we go.

I just finished installing Dapper upgrade and I again not startx. So I looked in the error log, and saw it had something to do with my Video card drivers. Then I rememberd that I had them in my home folder, and I Installed them.

Now I can boot into Gnome, but only in FailSave Gnome. The normal Gnome Does not Load all the way, and I cant move the mouse in there.

Any ideas how to fix this?

---

### Post by LanDroid on 2006-06-01
Why oh why did I ignore my own decision to wait a week before "upgrading" to Dapper and try it on Day 1?  Why?

Why oh why, when the installation guide lists a preferred method, then immediately states "This has been reported as not working yet (as of June 1)" did I continue?  Why did I even begin?

Why oh why did the install program ask if I wanted to retain the old version of something or other or the new version then freeze?  (I have learned that for the non-Windows community OS/2, Linux, OSX, etc. that OS freezes are NOT crashes.)

Why oh why is the Ubuntu install program FUBAR after a 6 week delay?  

Why oh why is my Linux distro now so FUBAR that it won't boot?  

This is why I'm gonna try Fedora.  That is if I'm able to uninstall a botched Ubuntu install.

---

### Post by aktiwers on 2006-06-01
Same thing happend to you?

Hmm..  Failsave gnome runs great here.. but for some reason I cant log into gnome normally. Any other suggestions?

---

### Post by catlett on 2006-06-02
Did you use a cd from an iso or dist upgrade. If you used a cd did you use the live cd or the text mode?
I didn't like the live cd and the dist-upgrade went terrible but whenb I reinstalled with the text based cd everything went great. I'd recommend staying away from dist-upgrade and the live cd. The etxt is based on Breezy's text installer which was rock solid.

---

### Post by Mahmoud on 2006-06-02
[QUOTE=aktiwers]Same thing happend to you?

Hmm..  Failsave gnome runs great here.. but for some reason I cant log into gnome normally. Any other suggestions?[/QUOTE]
I had the same problem and got it fixed using:

```

sudo apt-get update
sudo apt-get install ubuntu-base unbuntu-desktop
sudo apt-get dist-upgrade
```

---

### Post by aktiwers on 2006-06-02
Thanks. I think I got it fixed now.

I first had to reinstall my ATI drivers, just to be able to log into X. But then I could only log in on FailSave Gnome. Now I just ran this :
```
sudo dpkg-reconfigure xserver-xorg
``` 

And now I can log into gnome normally!
Thanks a lot for all the help and support! I love this place :)

---

