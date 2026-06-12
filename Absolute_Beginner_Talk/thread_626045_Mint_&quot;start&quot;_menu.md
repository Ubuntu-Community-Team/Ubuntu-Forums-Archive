---
title: "Mint &quot;start&quot; menu"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Karakh on 2007-11-28
Hi guys, quick question.

I tried Mint over the weekend, and although I wasn't impressed enough to switch, I did like the layout of the start menu. Is there any way to make the ubuntu menu behave in the same way?

I'm currently using the "one icon" version, I only use one panel and the "three drop-down menus" were consuming the precious little space I have.

Thanks, Kris.

---

### Post by master_kernel on 2007-11-28
I don't think so, but you can try Affinity, brother of Avant Window Navigator: [http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon)

---

### Post by Krydahl on 2007-11-28
Not sure if this is what you're looking for because I don't know what the Mint start menu looks like, but...

Right click on your start menu and remove it from the panel.

Then right click and select "add to panel" and select "Main Menu" instead of "Menu Bar". (They both use the standard Ubuntu icon.) This puts the icon on your panel but no menus (apps, system places). When you click on the icon you get a drop down with all these things on. Takes up much less space.

If you don't like it you can remove it and put the menu bar back and all will be as it was.

---

### Post by Dr Small on 2007-11-28
The Linux Mint menu looks like this:

---

### Post by jordanmthomas on 2007-11-28
I believe that's called slab.
[https://wiki.ubuntu.com/Slab](https://wiki.ubuntu.com/Slab)  (note:  old link)

---

### Post by davejrice on 2007-11-28
I'm running the Mint menu right now!  Works a treat :) and customisable to an extent with a right click (brings up gnome conf)

I added the mint repository, 

```

deb http://www.linuxmint.com/repository daryna main upstream import

```

then

```

sudo apt-get update
sudo apt-get install mintmenu

```

then removed the repository (it conflicts a bit) and do another update

```

sudo apt-get update

```

Then removed the traditional menu from the bar then 'added' the mint menu.  It appears in the 'add to panel' options.

Hope that helps 

cheers

---

### Post by markharding557 on 2007-11-28
linu mint slab menu and other things can be added to ubuntu by adding linx mints repositorys to your apt list.
you don't say which version of ubuntu you are using
if using gutsy then you need mint reps for daryna(based on gutsy)or celena if you are on fiesty

---

### Post by MonkeeOfEvil on 2007-11-28
That looks like a custom version of the "SLAB"  menu from SuSe, which was developed by looking at tons of Usability data.

[https://wiki.ubuntu.com/Slab](https://wiki.ubuntu.com/Slab)

---

### Post by Karakh on 2007-11-28
Awesome, I added "deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna main upstream import" to the repos but I get a 404, is this the right url?

---

### Post by MonkeeOfEvil on 2007-11-28
[http://ubuntuforums.org/showthread.php?t=208131&highlight=slab](http://ubuntuforums.org/showthread.php?t=208131&highlight=slab)

---

### Post by SunnyRabbiera on 2007-11-28
> **Karakh said:**
> Hi guys, quick question.

I tried Mint over the weekend, and although I wasn't impressed enough to switch, I did like the layout of the start menu. Is there any way to make the ubuntu menu behave in the same way?

I'm currently using the "one icon" version, I only use one panel and the "three drop-down menus" were consuming the precious little space I have.

Thanks, Kris.

Yes it is very possible to install the mint menus into ubuntu, in fact I have done it myself.
though personally I suggest using a older version of the mint menu as there is a troublesome bug involving using the quit function.
To get mints main menu running you will need:
mintdisk
mintconfig
and the menu itself.
the first two can be found here:
[the bianca reopository]("http://www.linuxmint.com/repository/bianca/")
and the menu can be found here:
[the celena repository]("http://www.linuxmint.com/repository/celena/")

install the mintdisk first (as the others depend on it) and go on from there.
like I said I suggest an older version due to the quit function bug.

---

### Post by Jerry N on 2007-11-28
Interesting - I didn't like the way the LinuxMint menu worked so I changed it to work like Ubuntu.  To each his own, if he can figure out how to get it!

Jerry

---

### Post by laidback on 2007-11-28
I have to agree over the Mint menu, it is nice, but I too have stayed with Ubuntu.

---

### Post by davejrice on 2007-11-29
hmm, strange it doesn't work - that repo is out of the Mint sources.lst!

try just:

```

deb http://www.linuxmint.com/repository daryna

```

or just download the .deb directly:

```

wget http://www.linuxmint.com/repository/daryna/mintmenu_2.8_i386.deb

```

then

```

sudo dpkg -i mintmenu_2.8_i386.deb

```

i don't think it has any dependacies

let us know how you get on

cheers

---

### Post by Karakh on 2007-11-29
Hmm.. think I've found the problem. No 64bit version, anyone know a workaround?

---

### Post by tech9 on 2007-11-29
> **Karakh said:**
> Hi guys, quick question.

I tried Mint over the weekend, and although I wasn't impressed enough to switch, I did like the layout of the start menu. Is there any way to make the ubuntu menu behave in the same way?

I'm currently using the "one icon" version, I only use one panel and the "three drop-down menus" were consuming the precious little space I have.

Thanks, Kris.

mint is a distro of ubuntu. It has the same functionality. Why don't you stick with Mint if you like the menu so much.

personally, I don't like mint's printing setup

---

### Post by davejrice on 2007-11-30
I liked mint quite a lot - but there are a few bits that are nearer to Debian, not a bad thing i suppose!

But I switched back to Ubuntu for the Gutsy release.  When I get the chance I might switch back to Mint now that it is Gusty based also!

As for the 64bit mint menu, there isn't one ;)  you'll either have to switch to 32bit ubuntu (thats what i do - 64bit still has lots of things missing for me - ie flash plugin) or grab the source and re-build, but that might not work.

hope that's useful - not sure it is!

cheers

---

