---
title: "Gnome won't accept my username/password?"
date: 2008-04-23
forum: Arch and derivatives
---

### Post by handy on 2008-04-23
I'm in the process of installing Arch on my Alu' 24" iMac.  I have installed almost all of the Gnome/extras, set up the config files as per the Arch beginners install guide, added some fonts & yaourt, firefox & a few other things, BUT, when I try to load Gnome  my usernames / passwords are denied?

I have not yet been able to start Gnome.

I have no trouble with either the root account or my normal user account under any other circumstance.

Any clues greatly appreciated?

---

### Post by mevem on 2008-04-23
Maybe you have a wrong keyboard layout while running X?

---

### Post by handy on 2008-04-23
> **mevem said:**
> Maybe you have a wrong keyboard layout while running X?

There was no indication of that.

I can change accounts just fine before I gdm.

---

### Post by finferflu on 2008-04-23
Try to stop Gdm, and to log in at the console prompt. 
Put this into your .xinitrc (and comment out anything else, if present)
```
exec gnome-session
```
and then issue
```
startx
```

That way you should be able to access Gnome and inspect things from within. If X refuses to start even with this method, perhaps you got some clues there.

---

### Post by handy on 2008-04-23
> **finferflu said:**
> Try to stop Gdm, and to log in at the console prompt. 
Put this into your .xinitrc (and comment out anything else, if present)
```
exec gnome-session
```
and then issue
```
startx
```

That way you should be able to access Gnome and inspect things from within. If X refuses to start even with this method, perhaps you got some clues there.

I had already removed gdm from the rc.conf file to make it easier to make changes to the system & then test by inputting gdm.

I had a look in /home & found that .xinitrc doesn't exist.  So I created one using the one in my other Arch install as a guide.  It made no difference unfortunately.

I installed all the files that I had previously chosen not to install from the Gnome & Gnome-extra, just to be sure that I hadn't left out something important.  That made no difference either.

Also, I swapped to another USB keyboard, just in case the iMac one was doing something strange.  That made no difference too.

I have posted in the Arch forums & here too, obviously, I guess I'll have to try my luck in the Gnome forum, though my previous experiences there have been very slow.

I tend to think that this problem is really easy to fix, though it may take days to eventually find the solution.

Linux surely can be like that! :lolflag:

---

### Post by MisfitI38 on 2008-04-23
> **handy said:**
> I'm in the process of installing Arch on my Alu' 24" iMac.  I have installed almost all of the Gnome/extras, set up the config files as per the Arch beginners install guide, added some fonts & yaourt, firefox & a few other things, BUT, when I try to load Gnome  my usernames / passwords are denied?

I have not yet been able to start Gnome.

I have no trouble with either the root account or my normal user account under any other circumstance.

Any clues greatly appreciated?

You are saying that your username and password are being denied by GDM, right?
So, if you were to do 'xinit /usr/bin/gnome-session', what happens?

---

### Post by handy on 2008-04-23
> **MisfitI38 said:**
> You are saying that your username and password are being denied by GDM, right?
So, if you were to do 'xinit /usr/bin/gnome-session', what happens?

I just entered the command from the root account (it did warn me about that) & I'm in! & feeling happy & relieved.

I just re-entered Gnome using startx from my normal user login account.  :-)

Ok, I just rebooted & logged in as normal user, then input gdm which of course brings me back to the initial problem.

So, how do I appease gdm?

I'd be happy to skip the login screen & automatically start a gnome session with my normal user account.

---

### Post by handy on 2008-04-24
I have found that I can't use sudo, gksudo or access the root terminal from inside of gnome.

I have worked around this problem & can use sudo to some extent without a password though this is not ideal.

I am also able to login to gnome automatically, thus avoiding the need to use the terminal & the following command:

xinit /usr/bin/gnome-session

Which is ok in its own way, but I do still have a very serious thus far unidentified problem lurking in my installation.

---

### Post by finferflu on 2008-04-24
Just for you to notice: I regularly use sudo without a password. That is ideal only if nobody has physical access to you machine. If someone is able to login with the normal user account s/he will be already able to use sudo, so I don't really see the point of having the password. 

See [http://wiki.archlinux.org/index.php/Disable_root_password_and_gain_su_sudo_with_no_password](http://wiki.archlinux.org/index.php/Disable_root_password_and_gain_su_sudo_with_no_password)

Anyway, more than that, I have no clue so far on your particular problem...

---

### Post by MisfitI38 on 2008-04-24
> **handy said:**
> I have found that I can't use sudo, gksudo or access the root terminal from inside of gnome.

I have worked around this problem & can use sudo to some extent without a password though this is not ideal.


Try adding this to /etc/profile:
```
export XAUTHORITY=/home/non-root-usersname/.Xauthority
```
Then as root do:
```
source /etc/profile
```
Then start an X session as non-root user and see if that allows you to run X apps as root.

---

### Post by handy on 2008-04-24
> **finferflu said:**
> Just for you to notice: I regularly use sudo without a password. That is ideal only if nobody has physical access to you machine. If someone is able to login with the normal user account s/he will be already able to use sudo, so I don't really see the point of having the password. 

See [http://wiki.archlinux.org/index.php/Disable_root_password_and_gain_su_sudo_with_no_password](http://wiki.archlinux.org/index.php/Disable_root_password_and_gain_su_sudo_with_no_password)

Anyway, more than that, I have no clue so far on your particular problem...

I am using the following, which allows me to keep the root account functioning too:

root ALL=(ALL) ALL
handy ALL=(ALL) ALL

%wheel ALL=(ALL) ALL
%wheel ALL=(ALL) NOPASSWD: ALL

The above has made it possible for me to use the broken Gnome.  It is interesting how flexible Linux is, there are so many ways around a problem, even though the problem still exists. :lolflag:

> **MisfitI38 said:**
> Try adding this to /etc/profile:
```
export XAUTHORITY=/home/non-root-usersname/.Xauthority
```
Then as root do:
```
source /etc/profile
```
Then start an X session as non-root user and see if that allows you to run X apps as root.

I did the above Misfit138, but it unfortunately made no difference. Before I did it I commented out the NOPASSWD: line quoted earlier in this post.

---

### Post by handy on 2008-04-26
Well, after removing all of the additional parts of Gnome & Gnome-extra that I added in a vain attempt to solve the Gnome password problem, I have Arch setup pretty nicely, with the essentials that I use,  except that I can't get sound out of it, & that I have to use a number of tricks to be able to use Gnome, due to the username password problem effecting Gnome & apart from Alt-F2, I can't use function keys or adjust my monitors brightness via the keyboard (the only way).

After the 3 days of getting Arch to this point, I am thinking of scrapping it & starting again from scratch.  I don't expect anyone with the knowhow will be prepared to spend the time to help me find the  Gnome/password problem, which I'm wondering if the cause was the Apple aluminium keyboard possibly finding a way to change from num-lock on/off in the install process, as those keyboards don't have a num-lock key or any led's to indicate what their settings are?  So, for the next install I'll use an MS Digital Media Keyboard that I had laying around.

Anyway, I really like Arch, & it will be my full time number one OS, when I can eventually get sound out of it.  That is another problem that no one at the Arch forums seems interested in.  I think the alu' iMacs are a bit too new & also not used for Linux by many users, so well worn paths have not been established for both the sound & keyboard problems, though I'm under the impression that the 1.0.16 ALSA package has sorted out the iMac sound problem, though my experience says I may be wrong?

---

### Post by handy on 2008-04-28
I've reinstalled Arch on the iMac.

I have partitioned like so:

 48Gb - HFS+ = OS X
 15Gb - Ext3 = /
 30Gb - JFS  = /home
  2Gb - swap = swap
200Gb - JFS  = thevoid (storage)

The Gnome password problem no longer exists thankfully. :-D

The function keys now work on the MS Digital Media keyboard, but I still don't know how to set it up so I can control the monitor brightness?

Sound is still broken too?

Arch is very usable at this stage, though I certainly have got a lot more learning to do to be able to get everything working just right.

---

### Post by finferflu on 2008-04-28
Who knows, it could have just been a dodgy installation. Sometimes things just go wrong. As for the sound, since you have a patched version of ALSA, as far as I understand, you could try to create your own PKGBUILD, and see if you can apply it yourself. Don't worry if you don't feel expert enough, there is a section on the forums dedicated to help on PKGBUILDs, and you can even ask people to write one for you. However it's very convenient for you to learn it, as creating Arch packages can always come... well... *handy* :D

---

### Post by handy on 2008-04-28
> **finferflu said:**
> Who knows, it could have just been a dodgy installation. Sometimes things just go wrong. As for the sound, since you have a patched version of ALSA, as far as I understand, you could try to create your own PKGBUILD, and see if you can apply it yourself. Don't worry if you don't feel expert enough, there is a section on the forums dedicated to help on PKGBUILDs, and you can even ask people to write one for you. However it's very convenient for you to learn it, as creating Arch packages can always come... well... *handy* :D

I really do think that the aluminium iMac keyboard was responsible for my Gnome login problem, though I'll never be able to prove it.  Those keyboards have no num-lock key or (just like the computer) any LED's to indicate anything...  So you have no manual control or feedback regarding the status of the numeric keypad, & my password is numeric.  Anyway that problem is gone, & it caused me in a round about way to learn more things about Linux & Arch in particular, which has to be a good thing. :-)

I'll get to the sound & screen brightness problems soon.  Thanks for the info' about building my own package, I'll look into that; if I do find success that way, other Arch iMac users will be able to benefit from it.

---

### Post by mips on 2008-04-30
> **handy said:**
> 
I'll get to the sound & screen brightness problems soon.  Thanks for the info' about building my own package, I'll look into that; if I do find success that way, other Arch iMac users will be able to benefit from it.

I responded to your sound/brightness issues on the Arch forums with a few suggestions and links. Dunno how helpfull they will be though.

---

### Post by handy on 2008-04-30
> **mips said:**
> I responded to your sound/brightness issues on the Arch forums with a few suggestions and links. Dunno how helpfull they will be though.

Thanks mips, I'll check them out now before I go to bed.

---

### Post by handy on 2008-05-01
Mips your help got me much further down the track my Arch powered iMac now has sound (of sorts) & an easily controlled screen brightness.
 
I expect you will read my reply to you in the Arch forum but I thought I'd post a link to the thread, in case some iMac owner wants to migrate from Ubuntu to Arch in the future, they could benefit from it.

Here is a link to the Arch forums, where I have an evolving post on installing & setting up Arch on an aluminium iMac, see post 5 in the following thread:

***_[http://bbs.archlinux.org/viewtopic.php?id=35355](http://bbs.archlinux.org/viewtopic.php?id=35355)_***

---

### Post by mips on 2008-05-01
handy,

Looks like things are not absolutely perfect in MacLand (although better than before), I will keep my eyes peeled for anything that might help and let you know about it.

---

### Post by handy on 2008-05-01
> **mips said:**
> handy,

Looks like things are not absolutely perfect in MacLand (although better than before), I will keep my eyes peeled for anything that might help and let you know about it.

Yes, I'm trying to get help on the Arch forum to convert nicfagn's Ubuntu patch how-to into Arch speak.  I have been meeting early resistance, but I reckon I'll get there in the end.  Perhaps it can be done with ABS?  Something else for me to learn about! :-)

---

### Post by handy on 2008-05-02
I received a PM from nicfagn, telling me that his patch has not been submitted to ALSA, as far as he is aware, because he does not have the 24" iMac & therefore can't fully test it himself.

He also told me that using ***model=_mpb3_*** in the following line in ***/etc/modrobe.conf*** does the same as his patch on ALSA 1.0.16 & later:

***options snd-hda-intel model=mbp3***

Using this setting gives me a full working alsamixer & the headphones function properly, I have not tested Line Out, or Mic.

For anyone unaware of it, the following line needs to be placed above the previously quoted line in ***/etc/modprobe.conf*** :

***alias snd-card-0 snd-hda-intel***

---

