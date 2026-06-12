---
title: "Noob question like u wouldnt beleive ! firefox install úber noob"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by combat squirrel on 2006-02-22
Hey all, hows things going !

Just built myself a Ubuntu Linux box, purely to learn the ways of linux, a friend of mine recommended me Ubuntu.

Running on a 1.7ghz celeron, 512meg ram, 9200 ATI card,10gig hd, 15" tft

Anyways on2 the problem, wanting to update firefox, discovered its just not a simple, click a exe file or whatever and it install (told u im NOOB !:mrgreen: )

discovered I have to go 2 the terminal to install stuff and copied and pasted instucations from:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

Now when i try to run firefox from the applications menu it doesnt work, says

'Cannot launch icon, failed to execute child process 'firefox' No such file or directory

Its probably a dumb question and everyone knows the answer, but what do i do ? Also why is it not possible to just 'double' click something and let it install in linux ? Before ya say, just go back to windows mr squirrel, I want to learn the ways ! :D

---

### Post by kaamos on 2006-02-22
> Also why is it not possible to just 'double' click something and let it install in linux ? Before ya say, just go back to windows mr squirrel, I want to learn the ways !
Because you can do it with a single click in synaptic. :) [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

That does not apply for the newest firefox because it cannot be updated to the repositories. That would break other applications. But the wiki page tells a good way to install. Troubleshooting: open a terminal (applications->accessories->terminal) and type "firefox". Does it give an error?

---

### Post by combat squirrel on 2006-02-22
Hi there, I type firefox and get:

bash:firefox: command not found

I tried going to add applications and reinstalling the old firefox, it reinstalled and still does the same, 'not found'

thanks for replyin so far!:)

---

### Post by Estariel on 2006-02-22
double clicking an .exe file in order to install something is being debated all the time.
it is a rather controversial issue, but i'll come to that in a minute.

at the moment installing software works the following: software gets developed in an open source way. thus, the source is available, and the authors of the program most of the time do not care about providing you with a binary. 
providing you with a binary is done by your distribution. that means, if an application you want is not available in the ubuntu repositories you have a (slight) problem.

why many people think this is superior to the windows approach (which you at the moment might feel is easier) is because we eliminate the occurence of spyware and viruses. all packages that are in the repositories have been built from source and therefore you can be sure that there is nothing bad in them (as long as you trust the official ubuntu developers).

this approach however makes it hard to get the newest versions of all packages. in effect, you only get updates when a new version of ubuntu is released. for some people, who like to live on the cutting edge, this is a little frustrating.

there are options to this "problem" however.
the KDE project developed an application called "klik" which lets you very easily install binary packages from debian unstable (thus, very recent packages, and not as unstable as it sounds).
also, to not mess up your system they do not get installed system wide but live in your home directory.
it is a very neat way of doing things (it got invented by apple btw; this is how OSX does it) and i have a amarok and a krita snapshot installed this way, and i absolutely love it.
check it out:

[http://klik.atekon.de](http://klik.atekon.de)

I think you have to use konqueror though to access the klik software repositories, although i'm not sure of that.

even though they don't mention ubuntu explicitly on their website, it works very well.

The second way would be to get a different distribution with adds the most recent packages almost instantly. The only such distribution I know about that does this is Gentoo, and it is a real pain in the *** to administrate it (e.g. get your hardware working). I still have my non-production computer running gentoo because i like to play with the newest possible software, but the thing breaks every week and requires a lot of time to get it running again.

hope i could help,
estariel

edit: if you decide to give klik a try (please do it, it is great), they tell you on the website to do the following:
wget klik.atekon.de/client/install -O -|sh
you MUST add sudo in front of this command in ubuntu! otherwise klik cannot edit some system files it needs to edit in order to run.

---

### Post by heimo on 2006-02-22
Did you follow all the steps? Including (especially the second line):
```
 
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

---

### Post by kaamos on 2006-02-22
Are you shure you have done this:
[quote=https://wiki.ubuntu.com/FirefoxNewVersion] # First, /usr/bin/firefox
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox
 # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox[/quote]
Btw Try not to touch the old firefox installation now.

---

### Post by qwazert on 2006-02-22
Same thing happened to me after "upgrading" Firefox via the Synaptics. 
Use AUTOMATIX to upgrade instead. 

There's an article about it in the "sticky" sections.

I also had to delete the shortcut and create a new launcher. I believe the name changes (after the update) from Firefox to MozillaFirefox....or something like that!

---

### Post by depu on 2006-02-22
the wiki method worked fine for me...
may i suggest that u try installing again
maybe u havent done this part yet.
<quote>
To ensure it is used as the default version, modify the symbolic link in /usr/bin:

 # First, /usr/bin/firefox
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox
 # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
 

The dpkg-divert command will move the original system-wide /usr/bin/firefox to a new name. The ln command will place a symlink to the newly installed firefox in /usr/bin
</quote> 
thats from the wiki

---

### Post by combat squirrel on 2006-02-22
hi ok, iv typed in the above things, and it no longer says it cannot find it I now get a 'starting firefox' on the bottom bar, the 'start bar', as if its minimised, but after about 10 sec it just vanishes and firefox doesnt load

EDIT: everyone is saying the 'In' command, that just says 'In: command not found: if i use Ln as in L it then does something, i carnt tell if you mean l or i

---

### Post by kaamos on 2006-02-22
Does running it in a terminal give a different error than before?

Did you do this:
[quote=https://wiki.ubuntu.com/FirefoxNewVersion]You need package 'libstdc++5' installed.```
sudo apt-get install libstdc++5
```[/quote]
?

---

### Post by combat squirrel on 2006-02-22
yea ran that before, now did it again and it works !:) thanks guys, now have a feeling for how linux installs stuff and works, step 1 of 983123098120 :D, now to try and install some ATI drivers for my vid card..........any clues? :D or is it just a bad idea? lol

---

### Post by towsonu2003 on 2006-02-22
[QUOTE=combat squirrel]
EDIT: everyone is saying the 'In' command, that just says 'In: command not found: if i use Ln as in L it then does something, i carnt tell if you mean l or i[/QUOTE]
that's an L as in lol

As for ATI drivers, there are two threads in Tips and Tricks section, one for the drivers in the repo, one for the newest driver (I guess this is better?). you might wanna get used to ubuntu before goin into ati drivers.... (and if you don't need 3d, your current configuration should be good enough, with the open sourced drivers?)

On an ati radeon mobility 9000, I tried the latest drivers, but open source drivers (already installed by default) were better...

---

