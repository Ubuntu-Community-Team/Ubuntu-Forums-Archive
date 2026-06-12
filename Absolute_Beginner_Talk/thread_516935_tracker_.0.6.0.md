---
title: "tracker .0.6.0"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by luckyd on 2007-08-03
are there any ubuntu .debs for tracker .0.6.0?

---

### Post by idn on 2007-08-04
> **luckyd said:**
> are there any ubuntu .debs for tracker .0.6.0?

trying to find these myself, i can only find the sources so far, let me know if you find the debs, thanks!

---

### Post by luckyd on 2007-08-04
I would use the sources, its just that they dont seem to come with the new version of the gui search tool :(

---

### Post by Hakker on 2007-08-04
I hope this is the correct page but hopefully it will help
[http://www.gnome.org/projects/tracker/start.html](http://www.gnome.org/projects/tracker/start.html)

---

### Post by luckyd on 2007-08-05
yah there arnt any feisty .debs :(

---

### Post by Frak on 2007-08-05
Do you have universe enabled, it should be in there.

---

### Post by luckyd on 2007-08-05
thats version .0.0.5 not .0.0.6
 :)

---

### Post by Frak on 2007-08-05
OK then, I could give it a shot at trying to build one.

---

### Post by luckyd on 2007-08-05
cool thank you :)

---

### Post by tuxcantfly on 2007-08-05
> OK then, I could give it a shot at trying to build one.

Sweet thanks, I'm just subscribing to this thread so I'll be notified when the new deb is posted.

---

### Post by tuxcantfly on 2007-08-05
hmm wait come to think of it no need for Frak to build a package, there's already one over here (found it linked through the tracker download page):

[http://debs.michaelbiebl.de/dists/feisty/main/binary-i386/](http://debs.michaelbiebl.de/dists/feisty/main/binary-i386/)

deb [http://debs.michaelbiebl.de/](http://debs.michaelbiebl.de/) feisty main

gpg key: [http://www.michaelbiebl.de/biebl.asc](http://www.michaelbiebl.de/biebl.asc)

---

### Post by Frak on 2007-08-05
Thank you so much, I was having trouble not only creating the .dsc file, but I didn't know how to solve the glib 2.0.0 (>=) glib 2.1.0 error. I bet its trivial, but still.

Thanks!

---

### Post by luckyd on 2007-08-06
cool when i posted this thread his repo was down, sorry for the trouble. ;)

---

### Post by luckyd on 2007-08-06
wait a minute, that one doesn't work, when i type in the search it just shows that categories but not the files in the search tool :( are you guys getting this?

---

### Post by Frak on 2007-08-06
I'll give it another shot and see what happens.
EDIT
Right now I have to fix Grub as I had to have Office '07 for work. Shouldn't take long.

---

### Post by luckyd on 2007-08-06
these might help...

---

### Post by Frak on 2007-08-06
Thanks, that'll save me the time of packaging and installing the libraries.

Thanx

---

### Post by kendyjm on 2007-08-07
hi,

i've got this error :

[http://debs.michaelbiebl.de/dists/feisty/Release:](http://debs.michaelbiebl.de/dists/feisty/Release:) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

...i have an AMD64.............

is there another source with amd64 support please? 

thanks

---

### Post by Frak on 2007-08-07
Unfortunately your going to have to compile it yourself, I would help, but I have just a regular i386.
Just ask for help if you need it, I will be glad to help.

---

### Post by luckyd on 2007-08-07
those .debs don't work anyway, so dont worry about it kendyjm

---

### Post by Frak on 2007-08-07
Hey, luckyd, where did you find those libraries?

---

### Post by luckyd on 2007-08-07
[http://buzz.ulx.ru/gimp.html](http://buzz.ulx.ru/gimp.html) why?

---

### Post by Frak on 2007-08-08
because I needed libglib-dev, but its best to use all of the same files for consistency reasons.

---

### Post by Corbelius on 2007-08-08
> **kendyjm said:**
> hi,

i've got this error :

[http://debs.michaelbiebl.de/dists/feisty/Release:](http://debs.michaelbiebl.de/dists/feisty/Release:) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

...i have an AMD64.............

is there another source with amd64 support please? 

thanks

[http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

[http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093)

---

### Post by Frak on 2007-08-09
I finally got it compiled and built (after 3 days, sorry, I'm not a pro, I'm still training to be a MOTU), and here it is, hopefully it should work.
NOTE, if it doesn't auto install the dependencies, let me know, and I'll fix it.

---

### Post by luckyd on 2007-08-09
shoot it does the same thing as the other .deb look in the search tool it brings up the categories but you cannot click on them.

---

### Post by Frak on 2007-08-09
Your luckier than me, I can't get it to search.
This is clearly a bug in the program, not the packaging.

---

### Post by Frak on 2007-08-09
I have created a version for Gutsy Gibbon, maybe it'll work if its stood up against higher libraries:)

---

### Post by satkata on 2007-08-09
Hi,

I have built a i386 package of the updated 0.6.1 version, but I can not upload here, because of the max size limitation.

I used checkinstall and the package size become 1.5 mb.

BTW, it runs just fine on my Feisty and has none of the above described problems.

Does anybody know, how can I shrink it, to be able to upload it here? :confused:

Till then, if somebody wants it, just put your email here and I'll send it to you.

-------------------------------

NOTE:

[COLOR="Red"]**The package will not take care of any dependencies**[/COLOR], as I'm installing with every one package the according package-dev too and the package I made was just for personal purpose. 
But If you take care about installing the dependency packages, you will be set.

Just, download the source from the web site: 
[http://www.gnome.org/projects/tracker/download.html]("http://www.gnome.org/projects/tracker/download.html")

and run "./configure" within the source directory. It will tell you, if and what you have to install.

---

### Post by luckyd on 2007-08-09
[email]2hayden2@gmail.com[/email] or compress it right click, create archive of

---

### Post by luckyd on 2007-08-09
ok, i have exactly the same problem with your package as fraks, when i open up the search tool i get categories yet no files as shown in the screenshot. Obviously now its a problem with my computer. When I run ./configure from the source it runs perfectly so I have all the dependencies. satkata: are there any other tracker related dependencies or related packages that you installed that might fix this problem for me?

---

### Post by Frak on 2007-08-09
How about installing all the packages,[ recommended and suggested packages.]("http://packages.ubuntu.com/feisty/utils/tracker")
EDIT
And mine won't work either, so I really just think its a bug in the software.

---

### Post by satkata on 2007-08-09
Well, I really don't think this could be a bug in the software, because as I previously said, I don't have any problems with it.

Look at the screenshot.

Have you eventually installed some system critical packages from non-ubuntu repositories?

I never replace/upgrade important for the system stability packages from non-ubuntu repositories.

I could post a list with all of my installed packages and/or my sources.list, if this may help you.

----

Have you removed the old version first? "Mark for complete removal" in Synaptic or --purge with dpkg.

---

### Post by Frak on 2007-08-09
Didn't think about the complete removal, thanks.
And don't mind me asking, what did you use to get your docker bar like that anyhow?
Is it Kiba Dock, or AWN?

---

### Post by luckyd on 2007-08-09
thats a new version of kiba from reacocards repo

---

### Post by satkata on 2007-08-09
No, that's not Kiba-Dock.

It's AWN, the svn version.
Just paste this to your sources.list.

deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

---

### Post by Frak on 2007-08-09
Thanks

---

### Post by luckyd on 2007-08-09
i guess il just go with beagle till gusty :(

---

### Post by satkata on 2007-08-09
luckyd, still not working?

Didn't the removal first help at all?

Are you getting some messages, when you run "tracker-search-tool" it from the command-line?

with tracker-status, you can check what's the daemon currently doing and try to search via:
#tracker-search your_search_term

---

### Post by Frak on 2007-08-09
Oh, it works, just had to give it time to search my filesystem.
Luckyd, it may be something wrong with your computer.
Mine just didn't search yet, I forgot that most meta search engines take time to search the filesystem.

---

### Post by luckyd on 2007-08-09
i get some messages like this > (tracker-search-tool:5645): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -7 and height 107

(tracker-search-tool:5645): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -7 and height 79

(tracker-search-tool:5645): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -7 and height 107

(tracker-search-tool:5645): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -7 and height 109
 i think that thats normal though...

---

### Post by Frak on 2007-08-09
Looks like your having difficulties with glib, try
```
sudo aptitude reinstall libglib2
```
I just learned, use the version out of the repo's, not the downloaded version.
EDIT
Thats not normal output.

---

### Post by luckyd on 2007-08-10
i reinstalled a glib packages, but still same output :(

---

### Post by pt123 on 2007-09-06
Thanks the update worked perfectly fine.

---

