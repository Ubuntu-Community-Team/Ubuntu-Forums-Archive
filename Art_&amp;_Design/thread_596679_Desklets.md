---
title: "Desklets"
date: 2007-10-29
forum: Art &amp; Design
---

### Post by Source4 on 2007-10-29
Hello,
I just updated to Gutsy and am starting to get settled into it, but I have seen screen shots online where they have the mac starter bar.  I would like to have that and be able to add new desklets.

I have downloaded Gdesklet and played around with it, but I am still pretty confused.

Or if anyone has any good mac themes and how to install it.  

Basically I want my screen to be filled of eye candy! :P


One last thing, I have been working with Compiz Fusion and everything works except the cube feature, (I know these are un-related topics, but I am overwhelmed getting my desktop back to what I want)

Thanks so much!!

---

### Post by lpb331 on 2007-10-29
Hey. While Gdesklets has a starter bar, it doesn't look nearly as nice as Avant Window Manager or Kiba Dock. Personally I use Avant, though Kiba is better as far as eye candy is concerned. From what I've seen, Kiba is a bit more buggy, but still pretty stable. A quick search of the internet should give you an idea of what each looks like, and you can make a decision from there.

As for the cube feature, what happens when you try to use it?

---

### Post by Crafty Kisses on 2007-10-29
> **Source4 said:**
> Hello,
I just updated to Gutsy and am starting to get settled into it, but I have seen screen shots online where they have the mac starter bar.  I would like to have that and be able to add new desklets.

I have downloaded Gdesklet and played around with it, but I am still pretty confused.

Or if anyone has any good mac themes and how to install it.  

Basically I want my screen to be filled of eye candy! :P


One last thing, I have been working with Compiz Fusion and everything works except the cube feature, (I know these are un-related topics, but I am overwhelmed getting my desktop back to what I want)

Thanks so much!!
I don't really like desklets.

---

### Post by Crafty Kisses on 2007-10-29
The temperature desklet is actually helpful.

---

### Post by k0rfain on 2007-10-29
yeah, but does anyone know how to get kiba or awn working on gutsy? I installed them bu neither of them started.. Tell me how you did it?

---

### Post by Crafty Kisses on 2007-10-29
> **k0rfain said:**
> yeah, but does anyone know how to get kiba or awn working on gutsy? I installed them bu neither of them started.. Tell me how you did it?

What do you mean by not starting?

---

### Post by k0rfain on 2007-10-29
When I tried starting it from the menu it just didnt start. Hold on, Ill try to reinstall it and ill post my results :D

---

### Post by Crafty Kisses on 2007-10-29
> **k0rfain said:**
> When I tried starting it from the menu it just didnt start. Hold on, Ill try to reinstall it and ill post my results :D

Yeah, then I'll try to take a look at it.

---

### Post by k0rfain on 2007-10-29
```
kiba-dock: error while loading shared libraries: libakamaru.so.0: cannot open shared object file: No such file or directory

```

i installed it using the script from the kiba-dock forum

---

### Post by Source4 on 2007-10-29
> **k0rfain said:**
> yeah, but does anyone know how to get kiba or awn working on gutsy? I installed them bu neither of them started.. Tell me how you did it?

Ditto here, I did all the steps on both sites but with absolutely no results!  Kinda sad.

Any help?

And the square, It just doesn't happen.

---

### Post by dRock1286 on 2007-10-29
I am using Gutsy and I got AWN to work.  I installed it from source and don't recal hitting any snags.  Try using [http://wiki.awn-project.org/...InstallingFromSource]("http://wiki.awn-project.org/index.php?title=InstallingFromSource") this as your guide.

---

### Post by Source4 on 2007-10-29
Installation failed

The package could not be installed because it contained no installable files.



I get this when I try

---

### Post by dRock1286 on 2007-10-29
Do you have all of the dependencies that it lists?

---

### Post by Source4 on 2007-10-29
I entered all the codes listed on the page.....I am not that good at the whole code thing... :(

---

### Post by dRock1286 on 2007-10-30
all you need to do is enter

> sudo apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf gnome-common python-dev python-gtk2-dev python-cairo-dev python-gnome2-dev python-gnome2-desktop gnome-panel python-glade2


Let that run...you may or may not have those already
download the file
CD to where the .gz file is of awn.

> tar -xzvf avant-window-navigator-0.2.tar.gz

cd into the new file

> ./configure
make
make install
ldconfig

and that should do it.  that is what I used exactly and got it to work...

---

### Post by Source4 on 2007-10-30
Quote:  Let that run...you may or may not have those already
download the file
CD to where the .gz file is of awn.


Call me a noob, but that comand kinda confused me, I understand the rest I'm pretty sure, but that tripped me up.

Thanks!

---

### Post by k0rfain on 2007-10-30
> **dRock1286 said:**
> all you need to do is enter



Let that run...you may or may not have those already
download the file
CD to where the .gz file is of awn.



cd into the new file



and that should do it.  that is what I used exactly and got it to work...

Thanks alot, that got awn to work =)

---

### Post by Source4 on 2007-10-30
Now my keyboard is lagging like crazy!!!  It takes a couple seconds for the text to pop up after I type it.
Please help, AWN can wait!
It was fine untill i entered all the comands to try to get AWN.

---

### Post by dRock1286 on 2007-10-30
> **Source4 said:**
> Now my keyboard is lagging like crazy!!!  It takes a couple seconds for the text to pop up after I type it.
Please help, AWN can wait!
It was fine untill i entered all the comands to try to get AWN.

Are you still having that problem?

---

### Post by dRock1286 on 2007-10-30
Do you have compiz-fusion installed?  I have read somewhere that AWN needs beryl or compiz to work properly...

---

### Post by dRock1286 on 2007-10-30
check out this thread: [http://ubuntuforums.org/showthread.php?p=2307772]("http://ubuntuforums.org/showthread.php?p=2307772")

---

### Post by smartboyathome on 2007-10-30
> **dRock1286 said:**
> Do you have compiz-fusion installed?  I have read somewhere that AWN needs beryl or compiz to work properly...

You just need a compositing Window Manager to have it work. I know xfwm (XFCE's window manager) works well, as well as xcompmgr, and both are pretty light on resources. Use those if Compiz Fusion doesn't work. If using XFCE, go to Window Manager Tweaks, and select "enable compositing".

---

### Post by santiagoward2000 on 2007-10-30
> **Codename said:**
> I don't really like desklets.

You could try Screenlets. They look better, but are a little heavier.

---

### Post by Source4 on 2007-10-30
Yeah, I am still having that problem majorly!!  Its a deal -breaking problem.  I need to fix it.
But yes i do have complitz installed.

Also when I open windows on my desktop it leaves lines behind it.

Please help! :(

---

### Post by Source4 on 2007-10-30
Now my entire system is becoming glitchy.
Can this be fixed or
Can I downgrade? back to 7.04 till the buggs are fixed?

---

### Post by capturesteve on 2007-10-30
Here is my blog article on how to get desklets working
[http://blog.spocore.com/?p=31](http://blog.spocore.com/?p=31)

---

### Post by Source4 on 2007-10-30
Thanks, but I am much more intrested in getting my computer lag free.  
Any thoughts?

---

### Post by capturesteve on 2007-10-30
I would try turning off a lot of stuff in compiz, since really most of the affects are not helpful. They just slow down the computer.

---

### Post by Source4 on 2007-10-31
That worked, I switched back to Beryl.
The problem fixed its self.

Can I still have AWN or screenlets while running beryl?

---

### Post by smartboyathome on 2007-10-31
Absolutely! Beryl and Compiz are basically the same thing, Beryl just used a lot of hacks.

---

### Post by Source4 on 2007-11-02
I was still unable to get AWN to run.

Can I get step by step instructions for downloading it on 7.10 running Beryl.  Thank you!

---

### Post by MagickalHack on 2007-11-28
> **k0rfain said:**
> yeah, but does anyone know how to get kiba or awn working on gutsy? I installed them bu neither of them started.. Tell me how you did it?

I have AWN working just fin on my Gutsy install.
Just follow the instructions on the Site below.
[AWN wiki.]("http://wiki.awn-project.org/index.php?title=Installation")

And just because it helped me, here's the FAQ from there as well.
[AWN-wiki FAQ.]("http://wiki.awn-project.org/index.php?title=FAQ")

If you have AWN installed and it isn't showing up try going into Applications -> Accessories and you should see something that says Avant Window Navigator. Click on that and you should be able to get it working.

---

### Post by smartboyathome on 2007-11-29
Also, try opening them both up in a terminal and posting the output if there are still errors.

---

