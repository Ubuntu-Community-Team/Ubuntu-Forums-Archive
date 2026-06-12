---
title: "Epidermis 0.1 beta released!"
date: 2008-10-08
forum: Art &amp; Design
---

### Post by Flimm on 2008-10-08
**Epidermis 0.1 beta has been released!**

[I]Epidermis is a program that combines wallpapers, GTK, metacity, icons, splashes, usplash, cursors, grub themes and GDM themes in one GUI program for the GNOME desktop. It is has only been tested under Ubuntu Hardy and Intrepid (alpha).

The idea is to separate each customisation into 'pigments'. For example, a wallpaper can be a pigment, and so can an icon set. Pigments are downloadable from a central repository, and can be automatically installed, similar to the way programs are distributed through a deb repository. 'Skins' are pigments that link to one pigment of every type, so you could create a skin that is dark, and ensure that every part of your desktop is customised.
[/I]
At long last, I finally finished a first beta. You can do all the basics here, including installing and uninstalling pigments, browsing for new pigments online, and activating them selectively.

If you use Ubuntu Hardy Heron or Intrepid Ibex on GNOME, I'd love it if you give it a go.

If you find a problem, or you have an idea, please don't post blueprints, questions or bug reports on the Launchpad project. These shouldn't be enabled, but they are, [due to a bug](https://bugs.launchpad.net/launchpad-answers/+bug/210535). You can send your feedback here.

Even though I'm making a customisation program, I am not much of an artist, so I would love it if someone could create a new set of skins, I only need two or three really good ones to release 0.1 final. It'll also be an opportunity to proof-read the [Make Your Own Skin](http://epidermis.tuxfamily.org/?q=node/29) documentation. The Ubuntu Studio and Mac4Lin skins I created need a lot of polishing, so you're welcome to do that.

[Epidermis launchpad project](https://launchpad.net/epidermis)
[Epidermis 0.1 beta release](https://launchpad.net/epidermis/testing/0.1beta)
[Epidermis home page](http://epidermis.tuxfamily.org)

---

### Post by V for Vincent on 2008-10-08
trying it out as I'm writing. Think you could add a button to backup current settings? that'd be nice for experimenting...

---

### Post by Flimm on 2008-10-08
I've just created a script for you that will backup all the current settings. It doesn't restore the settings for you automatically though, you need to do that yourself, though it shouldn't be too hard if you know how to use gconf-editor.

---

### Post by Gutt on 2008-10-09
Looks pretty good :D , will try it soon.

---

### Post by Pasto on 2008-10-10
I'll take a look at the code as a process of learning python. :)

Seems like a nice language.

---

### Post by MadsRH on 2008-10-10
Great work Flimm!!! \\:D/

I have not tested it yet. However I just have one small comment. It seems a little award to be scrolling across and not down the screen. Anyway it does to me ;-)

**//MadsRH **

---

### Post by Orlsend on 2008-10-13
Awesome Work Flimm, **Epidermis** is one of the best projects I have seen :D

---

### Post by Flimm on 2008-10-23
I've released Epidermis 0.1 stable, now. I hope you all enjoy it.
I'll get round to including Epidermis in my PPA (personal repo) soon, for you all to enjoy. Right now you can download the deb file at [launchpad's download page](https://launchpad.net/epidermis/0.x/0.1).

---

### Post by digitalis_vulgaris on 2008-10-23
> **MadsRH said:**
> Great work Flimm!!! \\:D/

I have not tested it yet. However I just have one small comment. It seems a little award to be scrolling across and not down the screen. Anyway it does to me ;-)

**//MadsRH **

Agree with this comment completely! This is great idea and great work indeed, but You need to list items in way to avoid horizontal scrolling for any cost. "No horizontal scrolling" is one of Commandments of good GUI. :)

---

### Post by ToasterThief on 2008-10-23
Thanks. This is just a few steps from awesome!

---

### Post by skintythe1andonly on 2008-10-23
Hey looks good...not sure if im to report it here or somewhere else but is the default pigment repository down? I can only seem to download half the info. Is there another repository?

---

### Post by Flimm on 2008-10-24
> **skintythe1andonly said:**
> Hey looks good...not sure if im to report it here or somewhere else but is the default pigment repository down? I can only seem to download half the info. Is there another repository?

This is a known bug that I introduced while building .deb files. I discovered it an hour or two after I finished publishing the .deb files, so I quickly fixed it and republished fixed debs as the same version. I hoped no-one would notice, but it looks like you have. :oops:
All you have to do is reinstall Epidermis 0.1 from the [download files at launchpad](https://launchpad.net/epidermis/0.x/0.1).
Or you can just run:
```
python /usr/share/pyshared/epidermis/epidermis.py
```

This is why I would welcome any testers!

---

### Post by oedipuss on 2008-10-24
Oh this can give the gnome appearance utility a run for its money =D

I know it's kind of early to ask for more advanced features, but wouldn't it be nice if there was a button that collected your current desktop settings into a new skin?
Much much easier skin creation this way, as you can fix your desktop the way you like it (which is something most if not all of us do anyway), click a button and pick a name. 

Also would you consider panel themes ? I mean the whole panel setup (applets, position, autohide) as stored on gconf, not just the background or a special panel.rc. It's something that's generally missing from theming, and can alter one's desktop significantly.

---

### Post by days_of_ruin on 2008-10-25
> **oedipuss said:**
> oh this can give the gnome appearance utility a run for its money =d

i know it's kind of early to ask for more advanced features, but wouldn't it be nice if there was a button that collected your current desktop settings into a new skin?
Much much easier skin creation this way, as you can fix your desktop the way you like it (which is something most if not all of us do anyway), click a button and pick a name. 

Also would you consider panel themes ? I mean the whole panel setup (applets, position, autohide) as stored on gconf, not just the background or a special panel.rc. It's something that's generally missing from theming, and can alter one's desktop significantly.

+1

---

### Post by skintythe1andonly on 2008-10-28
Hey Im still having probelems getting this working correctly. I installed from source originally. When installing from source i usually use check install but in this case as there was no makefile just the python script i could not do that. I am having problems downloading the initial pigment file when i click on find more. I got it working on the PC in my sisters place and she thinks its good. I used the .deb file there.

I tried the .deb file on my laptop and i keep getting the following error

```
root@skint-laptop:/home/skint/Desktop# dpkg -i epidermis_0.1-0ubuntu0_all.deb 
(Reading database ... 163458 files and directories currently installed.)
Preparing to replace epidermis 0.1-0ubuntu0 (using epidermis_0.1-0ubuntu0_all.deb) ...
Unpacking replacement epidermis ...
Setting up epidermis (0.1-0ubuntu0) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing epidermis (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 epidermis

```

I think i will prob have to uninstall the original. Any ideas other than manually deleting every file??

---

### Post by morgengenuss on 2008-10-28
with me epidermis just dies when i try to reload the repository.

from the terminal output:
```
$ epidermis 
Epidermis, Copyright (C) 2008 David D Lowe
Epidermis comes with ABSOLUTELY NO WARRANTY; for details click on the About button, License
This is free software, and you are welcome to redistribute it
under certain conditions; for details click on the About button, License
/usr/lib/python2.5/site-packages/epidermis/epidermis.py:287: GtkWarning: gdk_window_set_icon_list: icons too large
  self.win.show_all()
python: ../../src/xcb_lock.c:33: _XCBUnlockDisplay: Assertion `xcb_get_request_sent(dpy->xcb->connection) == dpy->request' failed.
Aborted

```

---

### Post by Orlsend on 2008-10-29
I know **Flimm** in real life Ill give him a Call about this bugs, Just hold on there guys.

---

### Post by ad_267 on 2008-10-29
I get this trying to install the .deb package:

```

(Reading database ... 221392 files and directories currently installed.)
Preparing to replace epidermis 0.1-0ubuntu0 (using epidermis_0.1-0ubuntu0_all.deb) ...
Unpacking replacement epidermis ...
Setting up epidermis (0.1-0ubuntu0) ...
Compiling /usr/lib/python2.4/site-packages/epidermis/epidermis.py ...
  File "/usr/lib/python2.4/site-packages/epidermis/epidermis.py", line 1018
    class PigmentTypeData():
                          ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/epidermis/pigments/pack.py ...
  File "/usr/lib/python2.4/site-packages/epidermis/pigments/pack.py", line 27
    class Pack():
               ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/epidermis/pigments/pigment.py ...
  File "/usr/lib/python2.4/site-packages/epidermis/pigments/pigment.py", line 43
    class PigmentType():
                      ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/epidermis/shell.py ...
  File "/usr/lib/python2.4/site-packages/epidermis/shell.py", line 28
    class Shell():
                ^
SyntaxError: invalid syntax

pycentral: pycentral pkginstall: error byte-compiling files (25)
pycentral pkginstall: error byte-compiling files (25)
dpkg: error processing epidermis (--install):
 subprocess post-installation script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 epidermis

```

The application appears to work fine though. Good work.

---

### Post by Orlsend on 2008-10-29
Thank you for Submiting your error, I believe the latest version is the faulty.

I am trying to get in contact with **Flimm**.

---

### Post by rudihawk on 2008-10-29
Yehaw! Great program man! :)

---

### Post by Flimm on 2008-10-30
> **rudihawk said:**
> Yehaw! Great program man! :)
Thanks!

---

### Post by Flimm on 2008-10-30
For those experiencing problems with the .deb files, I'm sorry, but I don't have a quick and easy fix yet. I'll get to work on it next week, it'll be a week of holidays for me.
I guess this is the right moment to announce that I have enabled **bug tracking in my project**, so if you have a launchpad account, go ahead and report your bug at [https://bugs.launchpad.net/epidermis/](https://bugs.launchpad.net/epidermis/) .

> **morgengenuss said:**
> with me epidermis just dies when i try to reload the repository.

from the terminal output:
```
$ epidermis 
Epidermis, Copyright (C) 2008 David D Lowe
Epidermis comes with ABSOLUTELY NO WARRANTY; for details click on the About button, License
This is free software, and you are welcome to redistribute it
under certain conditions; for details click on the About button, License
/usr/lib/python2.5/site-packages/epidermis/epidermis.py:287: GtkWarning: gdk_window_set_icon_list: icons too large
  self.win.show_all()
python: ../../src/xcb_lock.c:33: _XCBUnlockDisplay: Assertion `xcb_get_request_sent(dpy->xcb->connection) == dpy->request' failed.
Aborted

```
I've encountered this bug a few times, and I have no idea what's causing it. It seems to be totally random, nothing I change in my code seems to make any difference. I'm upgrading to Intrepid Ibex from the alpha releases, I'll see if that does the trick. Otherwise, I'll need to research it more.

---

### Post by nintennuendo on 2008-11-02
It downloads the repository, downloads everything, then hangs on Installing.  Been going for about 30 minutes, is that normal?

---

### Post by Anduu on 2008-11-02
This looks very promising indeed...cannot wait to see how it all pans out :KS

---

### Post by Flimm on 2008-11-03
> **skintythe1andonly said:**
> Hey Im still having probelems getting this working correctly. I installed from source originally. When installing from source i usually use check install but in this case as there was no makefile just the python script i could not do that. I am having problems downloading the initial pigment file when i click on find more. I got it working on the PC in my sisters place and she thinks its good. I used the .deb file there.

I tried the .deb file on my laptop and i keep getting the following error

```
root@skint-laptop:/home/skint/Desktop# dpkg -i epidermis_0.1-0ubuntu0_all.deb 
(Reading database ... 163458 files and directories currently installed.)
Preparing to replace epidermis 0.1-0ubuntu0 (using epidermis_0.1-0ubuntu0_all.deb) ...
Unpacking replacement epidermis ...
Setting up epidermis (0.1-0ubuntu0) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing epidermis (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 epidermis

```

I think i will prob have to uninstall the original. Any ideas other than manually deleting every file??
I got a similar error message when installing the .deb on a fresh installation of Ubuntu Intrepid, I managed to fix it by running this command in a terminal:```
sudo atp-get install -f
```
I need to improve my packaging skills.

---

### Post by wispygalaxy on 2008-11-07
Looks good, Flimm!

Going off topic....

"Hey, Bart, your epidermis is showing!"

[http://www.youtube.com/watch?v=ClynhFKMs3c](http://www.youtube.com/watch?v=ClynhFKMs3c)

---

### Post by Orlsend on 2008-11-08
Yeah thank you for adding a little spice to this thread, me and Flimm are fan of the Simpson's too.

***News:**

Hold on there guys, Flimm is going to release a new tool to make the process of making pigments more easy.

---

### Post by wispygalaxy on 2008-11-09
No problem, haha!

---

### Post by Flimm on 2008-11-19
Epidermis 0.2 is out!

This release features a new utility called "Epidermis Creator", it lets you make pigments easily, since it uses a GUI. I've attached a screenshot. Hopefully, this will ignite the creative spark in you, if you want to submit any pigments to the repository, tell me here or in a PM.

To install a created pigment, click Open on the main screen of Epidermis. To activate it, you'll need to have one skin installed already, select it, click customise, and choose your newly created and installed pigment. Then click Apply. Enjoy!

[Announcement](http://epidermis.tuxfamily.org/?q=node/47) | [Downloads](https://launchpad.net/epidermis/0.x/0.2)

---

### Post by MadsRH on 2008-11-20
Looks great! Keep up the good work :-)

Isn't there a similar project (a theme manager) under Gnome? Are you in contact with the developers there?

---

### Post by Flimm on 2008-11-22
The only similar project I'm aware of is [GNOME Art NextGen](http://developer.berlios.de/projects/gnomeartng/), but it's not an official GNOME project. Plus it's written in C#, it's limited to the kind of themes art.gnome.org hosts, and it doesn't support non GNOME-related things like Usplash and Grub.
I should contact the develepor sometime if only to discuss our respective visions.

---

### Post by Maddy on 2008-12-12
Maybe theming for firefox would be nice :-)

I like the program a lot, 1 program to do all the theming. Now we need a bunch of themes.

---

### Post by peddy on 2008-12-13
Great app, but are there more themes than the 2 included, and where can I find them?

Cheers

---

### Post by benmoran on 2009-01-16
Sorry if you already answered this, but when do you plan to introduce new themes? 

And if we were to make our own themes, where should we submit them to for considering of being included?

I think with a handful of extra themes, this program would really become useful. Especially for a lot of new users who can't yet deal with the over complexity of the different window managers, etc.

---

### Post by Flimm on 2009-01-16
Yes, themes are being made, right now the plan is to make distro themes according to [this blueprint](https://blueprints.launchpad.net/epidermis/+spec/make-distro-skins).
The workflow for adding pigments to the repository is this:
- choose a few themes or images (wallpapers and so on) and package them into pigments using Epidermis Creator, a simple GUI app that should be easy to use for anyone used to theming.
- the pigments are sent to me, I review them, making sure that the license is mentioned and free, the copyright holders (authors) are mentioned, and that the theme is of decent quality.
- I upload the pigments to the repository.

Right now, [Orlsend](http://ubuntuforums.org/member.php?u=612732) is concentrating on packaging themes into pigments, while I'm concentrating on bug fixing!

The workflow is not ideal obviously, it would be nice to have a way to view and submits pigments on the web, but this workflow will have to do for now.

By the way, if you're running a distro other than Ubuntu, [you can help us](http://ubuntuforums.org/showthread.php?t=1019508).

---

### Post by registerdown on 2009-02-02
This is soo cool, have been thinking that we need a "one click" complete skin/visual change app for linux/ubuntu. Awesome! 
Thanks.

---

### Post by MadsRH on 2009-02-02
Hi Flimm
It really looks like Epidermis is taking off. On [my blog]("anotherubuntu.blogspot.com") I wrote a post about the project. I just have a few comments:

1: I've contacted [http://francois.vogelweith.com/]("http://francois.vogelweith.com/") and suggested that they should package their themes for Epidermis.

2: Have you considerer how to adapt when Gnome 3 is released?

3: The apply button should turn gray or unclickable!
If I click the "find more" menu, I can select the Apply button (of course nothing happens as no change were made).
Also when I select the themes I want and clicking Apply, the installer runs as it should. But afterwards, the themes are still selected and I can still click Apply.

4: Shouldn't my current theme be visible when I start the program for the first time? It made kind of nervous, what if I can't undo the theme and restore my current look 8-[

Just my 2 cent

---

### Post by Flimm on 2009-02-04
> **MadsRH said:**
> Hi Flimm
It really looks like Epidermis is taking off. On [my blog]("anotherubuntu.blogspot.com") I wrote a post about the project. I just have a few comments:Thanks, MadsRH. Rock the blogosphere.

> 1: I've contacted [http://francois.vogelweith.com/]("http://francois.vogelweith.com/") and suggested that they should package their themes for Epidermis.Mmmm, looks interesting. I'd love to upload their themes into the Epidermis repo.

> 2: Have you considerer how to adapt when Gnome 3 is released?To be frank, no. As far as I know theming in GNOME 3 has yet to be finalised.

> 3: The apply button should turn gray or unclickable!
If I click the "find more" menu, I can select the Apply button (of course nothing happens as no change were made).
Also when I select the themes I want and clicking Apply, the installer runs as it should. But afterwards, the themes are still selected and I can still click Apply.That's a good point. The first one is definitely a bug.

> 4: Shouldn't my current theme be visible when I start the program for the first time? It made kind of nervous, what if I can't undo the theme and restore my current look 8-[

Just my 2 centThere's [a blueprint related to this](https://blueprints.launchpad.net/epidermis/+spec/save-current-look), but it would take quite a lot of work, as I'd need to have automatic preview generation as well. It's in the long-term goals.

---

### Post by suffer1989 on 2009-02-20
late reply, but can you back-up your current settings, befire trying something new ?

---

### Post by Flimm on 2009-02-20
> **suffer1989 said:**
> late reply, but can you back-up your current settings, befire trying something new ?
Looks like you missed [reply number three](http://ubuntuforums.org/showpost.php?p=5931011&postcount=3) in this thread. ;)

---

### Post by vicky_love on 2009-02-24
Wow !! Very good !dea of having a One-Click tweak of your look and feel of Ubuntu.

Thanks and Best wishes from me. :)

---

### Post by Orlsend on 2009-02-24
Thanks! I being packaging some skin and pigments.a new skin should be one the way to the repos.

Along with new translations.

---

### Post by Volt9000 on 2009-03-22
I tried this guy out but it didn't work.
No matter what I selected, be it a cursor, theme, whatever, nothing happened. Nothing was changed.

---

### Post by Orlsend on 2009-03-23
Could you run in the terminal and post the output?

---

### Post by Flimm on 2009-04-10
[Epidermis 0.2.3 has been released](http://epidermis.tuxfamily.org/?q=node/77), everyone!

---

### Post by Orlsend on 2009-04-10
Woohoo! I am upgrading :D

---

### Post by Flimm on 2009-08-08
[Epidermis 0.3.1 has been released](http://epidermis.tuxfamily.org/news/09/08/08/031-is-the-good-stuff-minus-some-annoyances), everyone!

---

### Post by alex.rayu on 2009-08-08
A very handy program! why not yet included in a default setup yet?

---

### Post by days_of_ruin on 2009-08-08
> **alex.rayu said:**
> A very handy program! why not yet included in a default setup yet?

Did anyone ask? [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

---

### Post by alex.rayu on 2009-08-09
Vote for it!
[https://bugs.launchpad.net/ubuntu/+bug/411039](https://bugs.launchpad.net/ubuntu/+bug/411039)

---

### Post by Flimm on 2009-11-01
[Epidermis 0.4 has been released](http://epidermis.tuxfamily.org/news/09/11/01/xsplash-themes-here-we-come), and this version includes Xsplash theming! It also makes packaging themes into pigments easier, thanks to automatic preview generation.

I tried getting Epidermis into the Karmic repositories but [my upload](http://revu.ubuntuwire.com/p/epidermis) just sat there at revu.

---

### Post by nwarrenfl on 2009-11-02
Nice, but your user interface is ugly in my opinion.
Also using a tree view would be better i think to show theme elements. The buttons are also displayed very strangely.

Would be nice if HIG-compliant, otherwise it might be a good program... ;)

---

### Post by Flimm on 2009-11-02
> **nwarrenfl said:**
> Nice, but your user interface is ugly in my opinion.
Also using a tree view would be better i think to show theme elements. The buttons are also displayed very strangely.

Would be nice if HIG-compliant, otherwise it might be a good program... ;)
I agree with you full-heartedly, actually. [Designers are always welcome](http://epidermis.tuxfamily.org/contribute#design) at the Epidermis project. I have been working on a new interface in my spare spare-time ;) and here's a little screenshot. As you can see, it still needs a lot of work.

---

### Post by Flimm on 2010-01-14
> **Flimm said:**
> I agree with you full-heartedly, actually. [Designers are always welcome](http://epidermis.tuxfamily.org/contribute#design) at the Epidermis project. I have been working on a new interface in my spare spare-time ;) and here's a little screenshot. As you can see, it still needs a lot of work.
Well, unfortunately, the new design didn't make it in the next version. However, I did manage to make Epidermis cross-distro, Debian unstable is now supported in [version 0.5](http://epidermis.tuxfamily.org/news/10/01/14/epidermis-supports-debian-unstable-in-05).

---

