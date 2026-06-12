---
title: "Did anything go wrong after upgrading ?"
date: 2008-10-10
forum: Arch and derivatives
---

### Post by Louis de Broglie on 2008-10-10
Hi,

Using arch for 1 week with xfce desktop. It's damn fast and cool. I configured it the way i want it to run. But i am bit confused about updating the system. Is there any chance that updating the system can overwrite/change the config files I set up ?:)

---

### Post by will1911a1 on 2008-10-10
> **Louis de Broglie said:**
> Hi,

Using arch for 1 week with xfce desktop. It's damn fast and cool. I configured it the way i want it to run. But i am bit confused about updating the system. Is there any chance that updating the system can overwrite/change the config files I set up ?:)


I've never had an upgrade overwrite my config files.  Just make a copy and put it somewhere else.  If something gets overwritten you can just copy the old one back over.

---

### Post by Pogeymanz on 2008-10-10
> **Louis de Broglie said:**
> Hi,

Using arch for 1 week with xfce desktop. It's damn fast and cool. I configured it the way i want it to run. But i am bit confused about updating the system. Is there any chance that updating the system can overwrite/change the config files I set up ?:)

I wouldn't worry about it. I've never had a config overwritten.

---

### Post by Rumor on 2008-10-10
> **Louis de Broglie said:**
> Hi,

Using arch for 1 week with xfce desktop. It's damn fast and cool. I configured it the way i want it to run. But i am bit confused about updating the system. Is there any chance that updating the system can overwrite/change the config files I set up ?:)

Most of your configs and settings are in your /home/user directory in the dotfiles. I've never had an update overwrite mine either in Gnome or in Fluxbox. Even jumping from one version of Gnome to the next has never caused me to lose any settings or preferences.

---

### Post by Barrucadu on 2008-10-10
Pacman is fairly good at telling you if any config files will be overwritten.

---

### Post by Louis de Broglie on 2008-10-10
> **Barrucadu said:**
> Pacman is fairly good at telling you if any config files will be overwritten.

Cool :D I have one more issue :

I installed xfce4.4.2 by pacman. But I think it is xfce 4.2 :( Because it looks like xfce 4.2 shown in the screenshots in the xfce website. I would like to have the look of xfce 4.4 shown in their site :

[http://www.xfce.org/about/screenshots](http://www.xfce.org/about/screenshots)

---

### Post by Pogeymanz on 2008-10-10
I'm sure it's 4.4. Those screenshots on the site are a little misleading. If yours looks more like the 4.2 screenshots, it's just because those are closer to default.

---

### Post by Rumor on 2008-10-10
> **Louis de Broglie said:**
> I installed xfce4.4.2 by pacman. But I think it is xfce 4.2 :( Because it looks like xfce 4.2 shown in the screenshots in the xfce website. I would like to have the look of xfce 4.4 shown in their site :

[http://www.xfce.org/about/screenshots](http://www.xfce.org/about/screenshots)

Most likely it *is* 4.4.2. Arch does not pre-configure any of the desktop environment packages. You're just getting a vanilla xfce package. If you want it to look like the various ones in the screenshots (note that they are all different), you'll have to tweak it to look that way.

---

### Post by Louis de Broglie on 2008-10-10
How do I tweak it to look like that? :)

---

### Post by Rumor on 2008-10-10
Well . . . I would try the settings manager?

[http://www.xfce.org/documentation/4.0/manuals/xfce-mcs-manager](http://www.xfce.org/documentation/4.0/manuals/xfce-mcs-manager)
[http://www.linux.com/feature/60203](http://www.linux.com/feature/60203)
[http://wiki.xfce.org/faq](http://wiki.xfce.org/faq)

---

### Post by Louis de Broglie on 2008-10-10
I have tried settings manager but i did not find any option there to get those icons shown in xfce4.4 screenshot. The icons in my desktop are those shown in xfce 4.2 screenshot. ](*,)

Also in the theme section i see themes up to xfce-4.2 not 4.4

---

### Post by Rumor on 2008-10-10
Hmm, I don't know what to tell you . . . Perhaps the icons on the xfce screenshot page are custom ones downloaded by the users?

Have you followed the wiki for xfce4?

[http://wiki.archlinux.org/index.php/Xfce](http://wiki.archlinux.org/index.php/Xfce)

---

### Post by Louis de Broglie on 2008-10-10
Yes, I have read the wiki.

> 
Perhaps the icons on the xfce screenshot page are custom ones downloaded by the users?


Maybe. I just found out that they are tango icon theme.

> 
[http://tango.freedesktop.org/Tango_Desktop_Project](http://tango.freedesktop.org/Tango_Desktop_Project)


:rolleyes:

---

### Post by kevinmchapman on 2008-10-10
The Tango icons package is in the Extra repository

---

### Post by crimesaucer on 2008-10-10
> **Louis de Broglie said:**
> Hi,

Using arch for 1 week with xfce desktop. It's damn fast and cool. I configured it the way i want it to run. But i am bit confused about updating the system. Is there any chance that updating the system can overwrite/change the config files I set up ?:)

Hello.... if you are talking about your files that you did when you installed, the way Archlinux updates your config files in the /etc directory is with files called ".pacnew" files.


As for files in your /home/folder, those conf files don't change unless you changed a configuration on your own. Or like with .mozilla, they import your old settings.


The configuration files you should know about are the ".pacnew" files.


If you miss the message in pacman (pacman will usually print any important messages about your configuration files if they need to be changed), or don't see the message posted on the Arch site, then you might get some things not working that had been working before you had upgraded if you don't edit your ".pacnew" files.


Basically, you just installed your brand new Archlinux and when you did that you made your rc.conf file and your pacman.conf file among others.....


If there are new updates to any of your /etc configuration scripts, they upgrade the script by giving you a new rc.conf.pacnew script that you will have to then edit with your old settings into the new file..... and then save that as your new rc.conf.


This can sometimes make a temporary break in somethings when the new upgrade wants to use the new file format when you might have not updated your rc.conf or other conf file with the .pacnew upgrade.... (I figured this out when I lost my manpages last year)


Basically all the conf files in /etc will get updated with .pacnew files, just recently Arch got rid of one of their repositories (it used to be community, current, extra, release, and unstable), and they also made all of the individual repository files into a mirrorlist..... it's much nicer this way in my opinion.


Recently Arch also changed the way they do the wireless in the rc.conf..... when they changed that, there were instructions in the new rc.conf.pacnew to show what changes were made and how to configure it.



My last thing I'll say is that you should try the gnome app called "Meld". It is a editor that will compare 2 files side by side to show changes, it will also show if only a word changed, or if a section is added..... plus you can just click and arrow to move your info into the new file and save it easily.

---

### Post by crimesaucer on 2008-10-10
> **Louis de Broglie said:**
> Cool :D I have one more issue :

I installed xfce4.4.2 by pacman. But I think it is xfce 4.2 :( Because it looks like xfce 4.2 shown in the screenshots in the xfce website. I would like to have the look of xfce 4.4 shown in their site :

[http://www.xfce.org/about/screenshots](http://www.xfce.org/about/screenshots)


xfce4 on Arch will look ugly at first..... it's not like xubuntu that has a nice theme for default. Check your version with the terminal or the "about" button.


This is my xfce4 on Archlinux:

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-54-1.png[/IMG]

Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-54.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-54.png)

---

### Post by handy on 2008-10-11
The .pacnew thing can be a pain in the Arch for new Arch users, it was for me when I hadn't done a pacmen -Syu for many months (I won't go into those details).

Anyway I started a thread here on the subject, learned of a variety of ways to compare the original config file with the .pacnew, though because I use Openbox & not Gnome/KDE most of the software like meld, was not available to me.

Anyway the two things I carried out of that thread to this day are when I do want to check an original against a .pacnew I just use two copies of nano to do it.  & the other thing was that an Arch veteran told me that he never updates his .conf files unless on the incredibly rare occasion something doesn't work after he has done an upgrade.

So far the leave it alone unless its broken works for me, though I haven't done a pacman -Syu for a month or so... :-)

---

### Post by Louis de Broglie on 2008-10-11
@crimesaucer: Cool desktop :D. Yes I have checked in about that it is 4.4.2 :) . Anyway, I will check out 'meld' when I feel like doing an upgrade. Currently , i guess i am off without updating like handy. ;)

---

### Post by Louis de Broglie on 2008-10-11
> **kevinmchapman said:**
> The Tango icons package is in the Extra repository

Thanks a lot :D

After installing the icons : I noticed a red cross in upper left corner of the copying window. That means no icon is available for copying. How to fix this ? :)

---

### Post by handy on 2008-10-12
> **Louis de Broglie said:**
> @crimesaucer: Cool desktop :D. Yes I have checked in about that it is 4.4.2 :) . Anyway, I will check out 'meld' when I feel like doing an upgrade. Currently , i guess i am off without updating like handy. ;)

Your statement is a little ambiguous, so I'll just make it clear that I do, do the pacman (actually I use yaourt) -Syu, I just don't worry about updating the .conf files that yaourt | pacman tells me about.

This method will very, very rarely ever cause any problems, if it does, then you go through & check your .conf files against the just added .pacnew files updating as necessary.

I probably didn't need to say that, but anyway it is clearer to me now. :lolflag:

---

### Post by crimesaucer on 2008-10-12
> **handy said:**
> Your statement is a little ambiguous, so I'll just make it clear that I do, do the pacman (actually I use yaourt) -Syu, I just don't worry about updating the .conf files that yaourt | pacman tells me about.

This method will very, very rarely ever cause any problems, if it does, then you go through & check your .conf files against the just added .pacnew files updating as necessary.

I probably didn't need to say that, but anyway it is clearer to me now. :lolflag:

also @ Louis de Broglie:

Usually it's just one line/word that needs to be changed, most of the time in a section that you might not even be using..... so it doesn't even matter.


But, sometimes it will be an important change and you will notice something stop working that you need like you manual pages.


Don't worry, just goto the Arch forums and look in the Pacman updates section to see any problems that others have experienced from a recent upgrade..... you would usually see at least one post with that same problem that you might have just encountered from an upgrade, and it's probably already been fixed with an explanation posted in that thread.


..... and thanks for the compliment on the desktop.

---

### Post by Louis de Broglie on 2008-10-12
Thanks a lot. :)

I noticed that if I uninstall something and that thing has config files. Pacman saves them as .pacsave. What is the reason behind this ? :)

I found in the pacman man page about .pacnew files. pacnew files are created when the current file in hard drive is different than what pacman is going to install, right ? :)

In that case, which file will be used by the system .conf or, .conf.pacnew ? :)

---

### Post by crimesaucer on 2008-10-12
> **Louis de Broglie said:**
> Thanks a lot. :)

I noticed that if I uninstall something and that thing has config files. Pacman saves them as .pacsave. What is the reason behind this ? :)

I found in the pacman man page about .pacnew files. pacnew files are created when the current file in hard drive is different than what pacman is going to install, right ? :)

In that case, which file will be used by the system .conf or, .conf.pacnew ? :)

Your old .conf will be used until you edit that file to include the new changes and template form of the .conf.pacnew.....


For example, rc.conf will be used, not rc.conf.pacnew..... but as other packages are upgraded, they will written to use the newer template of the rc.conf.pacnew file.


Recently, the rc.conf did a change of the way it uses Network profiles, so if you had a wireless network profile, it would of not worked until you corrected it in your old rc.conf to be written in the new way of the rc.conf.pacnew......


As for a .pacsave, that's for if you had configured your app or file the way you like it, and then removed the app for some reason, and then decided to re-install that app..... that way you have your old settings saved and used upon re-install.


If you did not like your old settings, and you want the default settings on re-install, then you can delete the .pacsave file before re-installing.

---

### Post by Louis de Broglie on 2008-10-12
Can you recommend a good desktop effect guide[ except this [faq]("http://ubuntuforums.org/showthread.php?t=809695")] so that I can edit the look of my desktop like a pro ? :)

---

### Post by crimesaucer on 2008-10-12
> **Louis de Broglie said:**
> Can you recommend a good desktop effect guide[ except this [faq]("http://ubuntuforums.org/showthread.php?t=809695")] so that I can edit the look of my desktop like a pro ? :)

That seems like that guide covers most things, you might also want to visit the Compiz-Fusion Forums, they have a section for "screenlets" (which is what I have on my desktop). You should also check out the app called conky: [http://conky.sourceforge.net/index.html](http://conky.sourceforge.net/index.html) (also on my desktop).


xfce4 also does compositing, and a lot of people like the "openbox/fluxbox" desktops....


But that guide talks about gnome-looks.org and compiz, besides that you should check out Life Hacker for info on some Linux themes/apps like AWN docks or whatever.....

---

### Post by handy on 2008-10-13
Today I used yaourt -Syu, the size of the unpacked files installation was well over 800Mb as I had not used the command for well over a month.

There was not a single .pacnew file created in the entire process. :-)

I did have to handle the klibc problem, which certainly had been made easy on the Arch home page. :-D

---

### Post by Louis de Broglie on 2008-10-13
Thanks for the links. Here is [My Desktop]("http://i34.tinypic.com/2v3q78x.jpg") ;)

Nice to hear that no editing was needed :)

---

