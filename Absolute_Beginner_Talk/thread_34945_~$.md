---
title: "~$"
date: 2005-05-16
forum: Absolute Beginner Talk
---

### Post by happyparadox on 2005-05-16
Downloaded "Hoary Hedgehog" to CD and installed to older Dell latitude.  HDD was formatted and the installation went easily it appears.  However I login w/user name and password then get a line that says: "you have mail"  and a command line which says: rgv2seek@satori:~$ and flashing cursor.  It wants a response and I haven't a clue what it wants. Well, I barely have a clue at all but moving along, the rgv2seek and satori are names I gave it on prompt during installation.  They are owner and user, password is something else.

---

### Post by bored2k on 2005-05-16
[QUOTE=happyparadox]Downloaded "Hoary Hedgehog" to CD and installed to older Dell latitude.  HDD was formatted and the installation went easily it appears.  However I login w/user name and password then get a line that says: "you have mail"  and a command line which says: rgv2seek@satori:~$ and flashing cursor.  It wants a response and I haven't a clue what it wants. Well, I barely have a clue at all but moving along, the rgv2seek and satori are names I gave it on prompt during installation.  They are owner and user, password is something else.[/QUOTE]
 It's your terminal session. Something that resembles the Disk Operative System aka DOS. Nothing to be worried about. Mine would be 
"ennuie@noir:~$"

It is not actually waiting for your inputting, it's just sitting there, having a [bud](http://www.mondobirra.org/sfondi/BudLight.sized.jpg).

---

### Post by happyparadox on 2005-05-16
But that's all it does.  I think it is on the [bud](http://www.drugdetection.com/pot.jpg)

---

### Post by bored2k on 2005-05-16
[QUOTE=happyparadox]But that's all it does.[/QUOTE]
 Well.. what do you want to do ? It's powerful, but it's no [psychic](http://www.unifiedftheory.com/psychic.jpg).

---

### Post by happyparadox on 2005-05-16
I want it to run the OS.

---

### Post by bored2k on 2005-05-16
[QUOTE=happyparadox]I want it to run the OS.[/QUOTE]
 Uhh.. you are in the OS. Xorg (Graphics) not starting is a while different *shabang*. Type startx. What's the [error](http://fmsales.net/images/microsoft-windows-logo-2.gif) ?

---

### Post by happyparadox on 2005-05-16
[QUOTE=bored2k]Uhh.. you are in the OS. Xorg (Graphics) not starting is a while different *shabang*. Type startx. What's the [error](http://fmsales.net/images/microsoft-windows-logo-2.gif) ?[/QUOTE]
 command not found

---

### Post by bored2k on 2005-05-16
[QUOTE=happyparadox]command not found[/QUOTE]
 O.o ?! What type of install did you do ? server ?

---

### Post by Sam on 2005-05-16
[QUOTE=happyparadox]command not found[/QUOTE]
What about```
$ sudo /etc/init.d/gdm start
``` ?

---

### Post by happyparadox on 2005-05-16
[QUOTE=bored2k]O.o ?! What type of install did you do ? server ?[/QUOTE]
 I downloaded to a CD on another computer.  Then used the CD

---

### Post by bored2k on 2005-05-16
[QUOTE=happyparadox]I downloaded to a CD on another computer.  Then used the CD[/QUOTE]
 Yes but when you installed it, did you select server install or something ? type sudo apt-get install ubuntu-desktop.

---

### Post by happyparadox on 2005-05-16
[QUOTE=bored2k]Yes but when you installed it, did you select server install or something ? type sudo apt-get install ubuntu-desktop.[/QUOTE]
 I do have this vague thing floating in my mind about server at the beginning of the install. 

Ok, typing sudo apt.....

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]I do have this vague thing floating in my mind about server at the beginning of the install. 

Ok, typing sudo apt.....[/QUOTE]
 If you did a "server" install, you got the "non GUI" install. You can download the "GUI" :? though.

---

### Post by happyparadox on 2005-05-17
I may have to give up for tonight.  I have a bad e on my keyboard and e is in my password.   When I typed sudo apt-get install ubuntu-desktop it then asked for my password.

With the barely functioning e key the password failed 3 times so now I have to reboot and I don't have another keyboard handy to plug in. Though I may borrow my friends if she isn't using her computer right now.

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]I may have to give up for tonight.  I have a bad e on my keyboard and e is in my password.   When I typed sudo apt-get install ubuntu-desktop it then asked for my password.

With the barely functioning e key the password failed 3 times so now I have to reboot and I don't have another keyboard handy to plug in. Though I may borrow my friends if she isn't using her computer right now.[/QUOTE]
 No wait, you can get root access !
Reboot the computer , and from the grub menu select recovery.

---

### Post by happyparadox on 2005-05-17
[QUOTE=bored2k]No wait, you can get root access !
Reboot the computer , and from the grub menu select recovery.[/QUOTE]
 Ok did that. It's all busy now.

---

### Post by happyparadox on 2005-05-17
still have that ror temporary failure in name resolution.  But it now says root@satori:~#

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]Ok did that. It's all busy now.[/QUOTE]
 I wonder what you did during the install .. for a server install one needs to type server , and you would remember doing so.

What if you apt-get install ubuntu-desktop ?

---

### Post by happyparadox on 2005-05-17
[QUOTE=bored2k]I wonder what you did during the install .. for a server install one needs to type server , and you would remember doing so.

What if you apt-get install ubuntu-desktop ?[/QUOTE]
 Yes, I'm sure I would.  If it were just checking or unchecking a box I could have blown over it but not typing it in.

---

### Post by happyparadox on 2005-05-17
[QUOTE=happyparadox]Yes, I'm sure I would.  If it were just checking or unchecking a box I could have blown over it but not typing it in.[/QUOTE]
 It got busy and put up a screen with a barrel-o-words that don't mean much to me.  But at the end it says it has to get OB/354MB of archives. After unpacking 1243MB of additional disk space will be used.

Do you want to continue [y/n]?

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]Yes, I'm sure I would.  If it were just checking or unchecking a box I could have blown over it but not typing it in.[/QUOTE]
 Click **YES** and let it rip.
edit -- type Y not click LOL

---

### Post by happyparadox on 2005-05-17
All the other words seem to be a list of programs.

---

### Post by happyparadox on 2005-05-17
[QUOTE=bored2k]Click **YES** and let it rip.
edit -- type Y not click LOL[/QUOTE]
 typed y, it says [working]
extracting templates from packages 44% and climbing.

---

### Post by happyparadox on 2005-05-17
moving real fast now

---

### Post by happyparadox on 2005-05-17
Looks like the Matrix

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]All the other words seem to be a list of programs.[/QUOTE]
 That is correct. That means that the programs got copied to your disc, but werent installed [why a 0MB/300MB to download appears]. I dont know why this happened, but they are installing now. It will take a bit.

---

### Post by kvidell on 2005-05-17
Apologies for off topic ness but I just wanted to point out that for some reason this is the most entertaining and some how "cute" Forum-Chat I've seen in a long time.
Specifically "looks like the matrix"
That made my day.
Thank you.

- Kev

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]Looks like the Matrix[/QUOTE]
 lol !@!@!

---

### Post by bored2k on 2005-05-17
[QUOTE=kvidell]Apologies for off topic ness but I just wanted to point out that for some reason this is the most entertaining and some how "cute" Forum-Chat I've seen in a long time.

- Kev[/QUOTE]
 W3rd !!

---

### Post by happyparadox on 2005-05-17
[QUOTE=kvidell]Apologies for off topic ness but I just wanted to point out that for some reason this is the most entertaining and some how "cute" Forum-Chat I've seen in a long time.
Specifically "looks like the matrix"
That made my day.
Thank you.

- Kev[/QUOTE]
 May as well have fun when being frustrated by a machine eh?

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]May as well have fun when being frustrated by a machine eh?[/QUOTE]
 You better have fun now. Once the GUI starts, it'll run so nice its almost boring not having something to tweak :\ .. not :-P

---

### Post by happyparadox on 2005-05-17
To some of you this is pretty mundane stuff.  To me it's major triumph.  I really appreciate the help. 

It's still working at it.  Writing line after line.

---

### Post by kvidell on 2005-05-17
[QUOTE=bored2k]You better have fun now. Once the GUI starts, it'll run so nice its almost boring not having something to tweak :\ .. not :-P[/QUOTE]
 Oh, he'll probably have to masacre all those stupid enlightenment packages that were getting in everyone's way for awhile.
Should we preemptively point him at all of Gandalf and BB's howto's on migrating to Alsa? hehe.
- Kev

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]To some of you this is pretty mundane stuff.  To me it's major triumph.  I really appreciate the help. 

It's still working at it.  Writing line after line.[/QUOTE]
 Welcome to Ubuntu Forums by the way :-P

** This is the longest "one on one" thread I have seen here .

---

### Post by happyparadox on 2005-05-17
I've been wanting to get into the Linux pool for a long time.  I've had this Dell sitting around for quite some time.  Nice machine but I got a big Ole 17" whizbang of a computer/laptop using the term loosely, but kept the Dell because I wanted to use it to get comfy with Linux and then make it my OS on the new rig.

---

### Post by bored2k on 2005-05-17
[QUOTE=kvidell]Oh, he'll probably have to masacre all those stupid enlightenment packages that were getting in everyone's way for awhile.
Should we preemptively point him at all of Gandalf and BB's howto's on migrating to Alsa? hehe.
- Kev[/QUOTE]
 First I'd do is point him to Openbox, so he can replace metacity slowness without feeling anything ;) [I just did, its uber fast]. 

But dude, you want to mv him to Gandalf's ALSA thread ? you want him to run away screaming right lol.

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]I've been wanting to get into the Linux pool for a long time.  I've had this Dell sitting around for quite some time.  Nice machine but I got a big Ole 17" whizbang of a computer/laptop using the term loosely, but kept the Dell because I wanted to use it to get comfy with Linux and then make it my OS on the new rig.[/QUOTE]
 You'll be glad you chose Ubuntu. I'm not going to tell you what apt-get can do, but just know this: it has supercow powers. Ok maybe I will. With ubuntu you install software using the "apt-get install" command. No need to search for funny-looking .exe or hard to find applications, its all there, and apt away. I bet you cant wait for it to finish ;P.

---

### Post by happyparadox on 2005-05-17
[QUOTE=kvidell]Oh, he'll probably have to masacre all those stupid enlightenment packages that were getting in everyone's way for awhile.
Should we preemptively point him at all of Gandalf and BB's howto's on migrating to Alsa? hehe.
- Kev[/QUOTE]
 Easy, I'm an old guy.  Slide rules were high tech to me not to many years ago.

---

### Post by happyparadox on 2005-05-17
So now it wants me to select a resolution.

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]Easy, I'm an old guy.  Slide rules were high tech to me not to many years ago.[/QUOTE]
 Don't worry about not understanding things at first ;). This community is quite good at helping people out.

Tip: grab a marker, write this down:
[http://ubuntuguide.org/](http://ubuntuguide.org/)
It will become your most visited website in a few minutes.

---

### Post by kvidell on 2005-05-17
> **bored2k]First I'd do is point him to Openbox, so he can replace metacity slowness without feeling anything  said:**
> . 

But dude, you want to mv him to Gandalf's ALSA thread ? you want him to run away screaming right lol.
 Hey.. I just made that move too ^.^
Actually... I dropped Gnome completely.
I saw it in someone's signature and decided to give it a go. It's the swiftness I love in Fluxbox without all the... well I feel really awkward saying this... but.. without all the bloat.

And it's config files are a hell of a lot easier.

---

### Post by bored2k on 2005-05-17
[QUOTE=kvidell]Hey.. I just made that move too ^.^
Actually... I dropped Gnome completely.
I saw it in someone's signature and decided to give it a go. It's the swiftness I love in Fluxbox without all the... well I feel really awkward saying this... but.. without all the bloat.

And it's config files are a hell of a lot easier.[/QUOTE]
 You wiped Gnome ? for what ? Openbox ? Lol i havent even logged out to see if there's an openbox entry in the GDM ^_^
[http://www.ubuntuforums.org/member.php?userid=14878](http://www.ubuntuforums.org/member.php?userid=14878)
[b]
edit -- [/b] Ok so I just tried Openbox... I think I'll stay with gnome + ob ;)

---

### Post by happyparadox on 2005-05-17
> **bored2k]Don't worry about not understanding things at first  said:**
> http://ubuntuguide.org/[/url]
It will become your most visited website in a few minutes.
 I was told that would be the case.  Not disappointed so far.

---

### Post by happyparadox on 2005-05-17
Setting up ubuntu-desktop(0.43)...
root@satori:~#flashing cursor

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]Setting up ubuntu-desktop(0.43)...
root@satori:~#flashing cursor[/QUOTE]
 One thing  : if you have a faulty keyboard, change your user's password with
```
passwd thenameoftheuser
```

Then do startx [hopefully it will work]

---

### Post by happyparadox on 2005-05-17
May have another problem.  red * then, Changes will take effect when all current X sessions have ended.
invoke'rc.d: initscript gdm, action "reload" failed.

Then a list of setting up:
Setting up gnome-games etc.

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]May have another problem.  red * then, Changes will take effect when all current X sessions have ended.
invoke'rc.d: initscript gdm, action "reload" failed.

Then a list of setting up:
Setting up gnome-games etc.[/QUOTE]
 Try sudo reboot then select normal ubuntu from the boot loader, to -see- if "X" starts correctly.

---

### Post by happyparadox on 2005-05-17
[QUOTE=bored2k]Try sudo reboot then select normal ubuntu from the boot loader, to -see- if "X" starts correctly.[/QUOTE]
 It's up.  Thanks, thanks very much.  I'm sure I'll be back often in the next few weeks.  Hope to run into you again, bored you really did a good job of guiding me through.  I'm really eager to get into this now. But I'm going to call it victory for now and call it a night.

---

### Post by bored2k on 2005-05-17
[QUOTE=happyparadox]It's up.  Thanks, thanks very much.  I'm sure I'll be back often in the next few weeks.  Hope to run into you again, bored you really did a good job of guiding me through.  I'm really eager to get into this now. But I'm going to call it victory for now and call it a night.[/QUOTE]
 No problem. I'm a frequent here so you'll likely bump into /me again. If you need anything else, you can PM [private message] me @ any time :).

---

### Post by bored2k on 2005-05-17
[http://www.ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script](http://www.ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script) < great for newcomers.

---

