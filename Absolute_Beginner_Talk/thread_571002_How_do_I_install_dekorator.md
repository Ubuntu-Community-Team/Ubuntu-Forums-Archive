---
title: "How do I install dekorator"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by mtgrocks04 on 2007-10-08
How do I install dekorator on feisty. I try  sudo apt-get install dekorator. It says it cannot find the package. How do I go about installing it, and further, how exactly does it work?

---

### Post by ThrobbingBrain66 on 2007-10-08
```
sudo apt-get install kwin-style-dekorator
```

---

### Post by mtgrocks04 on 2007-10-08
I have run that and installed the package. How do I use dekorator? I am really clueless.

---

### Post by Incense on 2007-10-08
Never head of this app, but I found this on the [kde-look]("http://www.kde-look.org/content/show.php?content=31447") site, hope it helps!

> Hi there,

this is the deKorator kwin deco,
deKorator is based on the HOWTO: KWin Window Manager Decorations posted in here: [http://kde-look.org/content/show.php?content=6332](http://kde-look.org/content/show.php?content=6332)
and done by Brandybuck, 10x david:)
the man that responsible for all the art design is jon clarke AKA ArbitraryReason, and if you don't know him by now all you should do is just look at the highest rated scores of this site:)
the nice thing about deKorator it's that it loads is images from
some user defined directory(something quiet similar to what iceWM is doing ),
thats means that everything is themeable with no time and no programming knowledge is needed.
one thing to note is that if you would like to see the changes instantly when designing the tiles, you need to run "kwin --replace&".

few notes:
when installing the new version, log out and login back, or run "kwin --replace&" to load the new version.
if for some reason some options dont seem to work, remove your old kwindeKoratorrc file and let deKorator produce a new one.

i will update my site with some more documentation, samples, template-themes, and other usefull stuff for the theme makers,
so don't forget to check it out, it will be located in the "goodies" directory.

how to install new theme - there r 3 ways to install new theme I'll name them out,

1 - downlad theme tarball and extract it to $HOME/.kde/share/apps/deKorator/themes

2 - download theme tarball, go to deKorator "themes" tab push the "install new theme" push button, you'll be presented with a dialog box, enter your theme URL or just use the little push button to locate your theme on your file system.

3 - go to kde-look and search for some 0.2 deKorator theme, in the theme post right click on the download link and "copy link address", then just go to deKorator "themes" tab push the "install new theme" button and paste the link onto the address bar, deKorator will download and install it for you.

most importent after any installation type, if you'd like to use the theme you need to press on the "set theme path's" push button.

And PLEASE if you got any comment good or bad, suggestion, feature request, other tiling format idea, please feel free to shout it...

10x to eyal the project is hosted now at [www.cheetux.org.il](www.cheetux.org.il), you could also find there some theme's i've ported from 0.1 to 0.2. 

---

### Post by mtgrocks04 on 2007-10-08
This doesn't do much for me. I have installed the kwin-style-dekorator package, how do I use the program? Is there some sort of gui? I really need help on this one.:confused:

---

### Post by Incense on 2007-10-08
I think it runs in your theme manager under Kcontrol. Once you install the theme in the right directory, you select deKorator in the theme manager, then configure from there.

BTW to get there click the K menu, click Run Program type

> kcontrol

Open up appearance & themes, click on theme manager.

---

### Post by mtgrocks04 on 2007-10-09
That seems to be helping, I have found the theme manager. I unziped the file and moved it to the .kde/shared/apps/dekorator. I cannot see it. How do I install a theme?

---

### Post by mtgrocks04 on 2007-10-09
Any help here would be really really appreciated.

---

