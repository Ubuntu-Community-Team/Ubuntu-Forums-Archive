---
title: "Got a virus on Firefox, how do I get rid of it?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2007-11-04
I've managed to get a virus on my system which I'm pretty sure has embedded itself in my Firefox. I accidentally clicked a link that brought me to one imagefap.com ( :-& ), and although I closed it right away, now whenever I go to an image dir on a site (for example, [http://altarstudio.mayshing.com/manga/](http://altarstudio.mayshing.com/manga/) ), I get redirected to imagefap. I've blocked the cookies, but somehow an imagefap css is getting put into the website and redirecting me. I know it's not the website itself, because I tried visiting it on another computer.

Aegis isn't picking up on any viruses at all, and deleting Firefox 1.5 and replacing it with 2.0 didn't do anything. I'm at a point where I'm considering reinstalling Ubuntu.

---

### Post by DutyDuty on 2007-11-04
Oh my. Quite the unfortunate place to get redirected to.

Seriously, though, have you tried the complete uninstall via Synaptic and then re-install? I had a problem a while back and that fixed it.

---

### Post by winh8r on 2007-11-04
you could try visiting the AVG site, they have a free anti virus for linux workstation you can download.
As for blocking the unwanted site- the firestarter firewall will allow you to block IP addresses fairly easily.
Hope this is of some help.

---

### Post by floke on 2007-11-04
Try deleting your .mozilla config file in your home directory - this will reset Firefox to vanilla mode.

---

### Post by arkara on 2007-11-04
this is weird
how did you manage to get a virus on a linux system???

---

### Post by mali2297 on 2007-11-04
Try resetting your personal settings:
```

mv ~/.mozilla ~/mozilla_backup

```
(in the terminal.)

---

### Post by testube_babies on 2007-11-04
EDIT:  four people just gave the same advice at the same time :)

---

### Post by SunnyRabbiera on 2007-11-04
> **arkara said:**
> this is weird
how did you manage to get a virus on a linux system???

its a rare bird but it can happen

---

### Post by Frak on 2007-11-04
> **arkara said:**
> this is weird
how did you manage to get a virus on a linux system???
Firefox settings and plugins work away from the actual Linux system, so getting a virus in your Firefox app can NOT touch the rest of your system. Just delete your .mozilla directory in your home folder and run
```
sudo dpkg-reconfigure firefox
```
to reset to default settings.

Also, a virus for Fx can infect all instances of Fx on ANY OS.

---

### Post by LinuxGuy1234 on 2007-11-04
> **Halfling Rogue said:**
> I've managed to get a virus on my system which I'm pretty sure has embedded itself in my Firefox. I accidentally clicked a link that brought me to one imagefap.com ( :-& ), and although I closed it right away, now whenever I go to an image dir on a site (for example, [http://altarstudio.mayshing.com/manga/](http://altarstudio.mayshing.com/manga/) ), I get redirected to imagefap. I've blocked the cookies, but somehow an imagefap css is getting put into the website and redirecting me. I know it's not the website itself, because I tried visiting it on another computer.

Aegis isn't picking up on any viruses at all, and deleting Firefox 1.5 and replacing it with 2.0 didn't do anything. I'm at a point where I'm considering reinstalling Ubuntu.

Simple, do these commands:
```

rm -rf ~/.mozilla
sudo dpkg-reconfigure firefox

```

To see if it works:
```

firefox

```

NOTE: sudo WILL ask you for your password that you use to log in to Ubuntu. Enter that in and press Enter.

---

### Post by Halfling Rogue on 2007-11-04
> **DutyDuty said:**
> Oh my. Quite the unfortunate place to get redirected to.

Seriously, though, have you tried the complete uninstall via Synaptic and then re-install? I had a problem a while back and that fixed it.

Did, and it was still there. Guess I'd better delete .mozilla.

---

### Post by Halfling Rogue on 2007-11-04
Uh.

```
halflingrogue@ubuntu:~$ sudo rmdir --ignore-fail-on-non-empty .mozilla
halflingrogue@ubuntu:~$ ls -a
.                 .gnome               .mplayer
..                .gnome2              musiclisting~
.aegisrc          .gnome2_private      .nautilus
.aspell.en.prepl  .gstreamer-0.10      okage 1~
.aspell.en.pws    .gtk-bookmarks       okage 2~
.bash_history     .gtkrc-1.2-gnome2    .openoffice.org2
.bash_logout      homework             .qt
.bash_profile     .hxplayerrc          .recently-used
.bashrc           .ICEauthority        Screenshot-1.png
botspecs~         .icons               stories
.cddbslave        .idlerc              .sudo_as_admin_successful
cheetor           .java                tanz_07_10_05.html
cheetor~          kayafraser~          temp
.comments         .kde                 temp1.html
.config           kink                 temp1.html~
Desktop           kink~                temp.html
.dmrc             .lesshst             .themes
drivers           livejournal~         .thumbnails
.esd_auth         .local               transformers~
Examples          lolmods.htm          .Trash
.fonts.cache-1    .macromedia          .update-notifier
.fullcircle       .mcop                .vlc
.gaim             .mcoprc              wallpapers
.gconf            mechspec.txt~        .Xauthority
.gconfd           .metacity            .xmms
.gimp-2.2         morepages.zip_FILES  .xsession-errors
.gksu.lock        .mozilla             zaeris
halflingrogue@ubuntu:~$
```


Any reason why it's not deleting?

---

### Post by mali2297 on 2007-11-04
**rmdir** can only remove empty directories, use instead
```

rm -rf ~/.mozilla

```
or safer
```

mv ~/.mozilla ~/mozilla_backup

```

---

### Post by Big_Croc7 on 2007-11-04
try ```
sudo rm -r .mozilla
```
(recursive remove), or try mv .mozilla moz-backup (move) - that keeps it as a backup
EDIT: you beat me to it ;-)

---

### Post by Halfling Rogue on 2007-11-04
Damn, removed .mozilla, but the virus is still there. Should I try installing Avast or something to look for it?

---

### Post by Frak on 2007-11-04
I'm not sure anymore if you have a virus anymore. Install ClamAV and let it scan your system.

---

### Post by mali2297 on 2007-11-04
> **Halfling Rogue said:**
> Damn, removed .mozilla, but the virus is still there. Should I try installing Avast or something to look for it?

I don't think that would help. The AV programs only search for Windows virus, afaik.

---

### Post by Halfling Rogue on 2007-11-04
> **mali2297 said:**
> I don't think that would help. The AV programs only search for Windows virus, afaik.

So ClamAV and Avast won't do me any good, then? Crap.

---

### Post by mali2297 on 2007-11-04
You could have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=535401](http://ubuntuforums.org/showthread.php?t=535401)

The problem seems similar...

---

### Post by Frak on 2007-11-04
Try using a different browser and see if it changes. You may be getting redirected.

---

### Post by Halfling Rogue on 2007-11-04
> **mali2297 said:**
> You could have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=535401](http://ubuntuforums.org/showthread.php?t=535401)

The problem seems similar...

My host file looks fine. I'll try another browser and see if it still does it.

---

### Post by mali2297 on 2007-11-04
Try adding this line to **/etc/hosts** :
```

127.0.0.1  imagefap.com

```
(From [here]("http://ubuntuforums.org/showthread.php?t=241460").)

---

### Post by Colro on 2007-11-04
Is it embedding code into every site you visit to redirect to that? Have you tried running the  [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) extension to see if it blocks the redirect? You might be able to use some of the data it provides to see just what file is trying to force the redirect. My guess is that it's in one of [these three files](http://www.mozilla.org/support/firefox/edit) -- but if removing .mozilla really didn't fix it, my theory's dead :(

---

### Post by mali2297 on 2007-11-04
> **Halfling Rogue said:**
> My host file looks fine. I'll try another browser and see if it still does it.

There is one [hhhobbit]("http://ubuntuforums.org/member.php?u=404314") on that thread that seems very knowledgeable. Read her/his posts.
(It might be related to Java.)

---

### Post by Halfling Rogue on 2007-11-04
> The other possibility is a Flash Player plugin
[http://ubuntuforums.org/showpost.php?p=3552289&postcount=61](http://ubuntuforums.org/showpost.php?p=3552289&postcount=61)

Actually, when it tries to redirect me now, I get a popup from Firefox saying I need to install Flash to "show all the content on this page". So I guess it's a Flash plugin problem.

---

### Post by mali2297 on 2007-11-04
Did you try Opera? It would be interesting to know if it is just Firefox...

---

### Post by Halfling Rogue on 2007-11-04
Working on it. My laptop's slow and is protesting my messing with it so much. XD Plus the syn package manager can't seem to find Opera.

---

### Post by benerivo on 2007-11-04
Opera isn't in the default reps. You may have to download the .deb from the opera site.

---

### Post by Frak on 2007-11-04
Goto software sources and in the third party tab, make sure Canonical parters (two rows) are checked, then try to install it.

---

### Post by Halfling Rogue on 2007-11-04
Couldn't I just check with Epiphany instead?

---

### Post by lordofchaos1984 on 2007-11-04
> **winh8r said:**
> you could try visiting the AVG site, they have a free anti virus for linux workstation you can download.
As for blocking the unwanted site- the firestarter firewall will allow you to block IP addresses fairly easily.
Hope this is of some help.
 
I don't know what everyone else thinks but [www.Avast.com]("http://www.Avast.com") has a great .deb for antivirus....only problem, you MUST register (free) to be able to use it

---

### Post by Halfling Rogue on 2007-11-04
> **Frak said:**
> Goto software sources and in the third party tab, make sure Canonical parters (two rows) are checked, then try to install it.

Where do I find software sources? In the syn package manager?

---

### Post by Halfling Rogue on 2007-11-04
> **lordofchaos1984 said:**
> I don't know what everyone else thinks but [www.Avast.com]("http://www.Avast.com") has a great .deb for antivirus....only problem, you MUST register (free) to be able to use it
I was already told it only looks for Windows viruses or something along those lines.

---

### Post by n3tfury on 2007-11-04
> **Halfling Rogue said:**
> Where do I find software sources? In the syn package manager?

yes

---

### Post by Frak on 2007-11-04
> **Halfling Rogue said:**
> Couldn't I just check with Epiphany instead?
sure

---

### Post by Frak on 2007-11-04
> **Halfling Rogue said:**
> Where do I find software sources? In the syn package manager?
In system->administration its right above syn package manager

---

### Post by Halfling Rogue on 2007-11-04
Still can't seem to find Opera; I'll go get the .deb from the site.

In the meantime, whenever I visit the altarstudio site and check Firefox's Error Console, I keep getting this:

```
Warning: Expected declaration but found '/'.  Skipped to next declaration.
Source File: http://www.imagefap.com/style.css
Line: 22

Warning: Unknown property 'fontsize'.  Declaration dropped.
Source File: http://altarstudio.mayshing.com/manga/style.css
Line: 331
```

KLinkStatus doesn't find anything unusual on either imagefap or the altarstudio site, except for a malformed adserver image on imagefap. Not sure if that's useful.

---

### Post by n3tfury on 2007-11-04
or system>administration>synaptics package manager>settings>repositories

---

### Post by houstonbofh on 2007-11-04
On the virus note, I did find something out by mistake.  I have a duel boot system with ext2-ifs for windows, and AVG in windows.  I left it up one night and it scanned my linux partitions!  Yes it found some virus tracks. (Samples from infected clients)  It deleted them.  And it is odd seeing a recycle bin on your / directory!

---

### Post by Halfling Rogue on 2007-11-04
> **houstonbofh said:**
> On the virus note, I did find something out by mistake.  I have a duel boot system with ext2-ifs for windows, and AVG in windows.  I left it up one night and it scanned my linux partitions!  Yes it found some virus tracks. (Samples from infected clients)  It deleted them.  And it is odd seeing a recycle bin on your / directory!

Heh, that'd be more useful if I was dual-booting. Maybe I'll try Avast after all.

---

### Post by Halfling Rogue on 2007-11-04
Great.

```
halflingrogue@ubuntu:/usr/lib/epiphany$ epiphany
epiphany: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory
halflingrogue@ubuntu:/usr/lib/epiphany$ 
```

---

### Post by Frak on 2007-11-04
Try Opera then.

---

### Post by Halfling Rogue on 2007-11-04
Looks like it's trying to do it in Opera, too. Which means it's Javascript, I guess? Here's Opera's Error Console when I go to [http://altarstudio.mayshing.com/manga/](http://altarstudio.mayshing.com/manga/) :

```
CSS - http://www.imagefap.com/style.css
Linked-in stylesheet
Declaration syntax error
Line 22:
    background-color: #FFFFFF; //#A0A5B2; 
  ---------------------------------------^

CSS - http://www.imagefap.com/style.css
Linked-in stylesheet
Declaration syntax error
Line 22:
    background-color: #FFFFFF; //#A0A5B2; 
  ---------------------------------------^

JavaScript - http://www.imagefap.com/image.php?id=1379347631
Inline script thread
Error:
name: ReferenceError
message: Statement on line 3: Reference to undefined variable: urchinTracker
Backtrace:
  Line 3 of inline#3 script in http://www.imagefap.com/image.php?id=1379347631
    urchinTracker();
JavaScript - http://www.imagefap.com/image.php?id=1379347631
Inline script thread
Error:
name: ReferenceError
message: Statement on line 3: Reference to undefined variable: urchinTracker
Backtrace:
  Line 3 of inline#3 script in http://www.imagefap.com/image.php?id=1379347631
    urchinTracker();
```

The hosts list keeps it from opening in Firefox now, but I can see in the status bar that it keeps trying to load itself anyway. I'd like to get rid of it if I can.

---

### Post by Halfling Rogue on 2007-11-04
Ugh. I ran the rm -rf .java command as per [here](http://ubuntuforums.org/showpost.php?p=3552289&postcount=61), and now Firefox won't even let me login to the forums; I have to use Opera. Do I have to reinstall Java with the syn package manager?

---

### Post by hhhobbit on 2007-11-05
If the Flash Player has something stuck in it, first close the browser, then do the following in an xterm:

$ cd
$ rm -fr .macromedia.

Then restart the browser.  It will be AUTOMAGICALLY recreated for you for a Flash Player app.
But it won't be recreated until you hit that app.  pbskids.org has some safe Flash apps to recreate it that are safe - anything else???  Maybe not safe.  That is why I recommend privoxy.

After removing your ${HOME}/.mozilla folder no sudo is required.  Here is all you need to do:

1. Close the browser
2. start a terminal and in it type:

   $ find .mozilla -type f -name bookmarks.html -print
   $ find .mozilla -type f -name bookmarks.html -exec cp -fp {} /tmp \;
   $ rm -fr .mozilla

3. Start the Firefox browser.  A new vanilla .mozilla is automagically created for you.  That is what it did the first time around!  It has NOTHING to do with installing Firefox itself.  Those are two separate processes (the same on Windows).  You may want to copy your old bookmarks.html file from /tmp.  But if you do that, FIRST, close the browser!  Then start an xterm and type:

   $ cd
   $ find .mozilla -type f -name bookmarks.html -print
   $ cp /tmp/bookmarks.html  COPY_OUTPUT_OF_PREVIOUS COMMAND

   You will have a different folder this time around.  If you want to be adventurous this MAY work (doubtful)

   $ cd
   $ find .mozilla -type f -name bookmarks.html -exec cp -fp /tmp/bookmarks.html {} \;

Just rememeber after you have started the browser your new .mozilla folder is automatically created for you.  NONE of this should cause Firefox to no longer work.  They should have just the opposite effect of starting you off with a fresh clean slate.  And you should NOT have to sudo ANYTHING to do ANY of it.  You do it ALL as a normal user.

There is a Trojan DNS.Changer for the Macintosh now:

[http://isc.sans.org/diary.html?storyid=3595](http://isc.sans.org/diary.html?storyid=3595)
[http://www.scmagazineus.com/Trojan-targets-Mac-users/article/58290/](http://www.scmagazineus.com/Trojan-targets-Mac-users/article/58290/)
[http://www.eweek.com/article2/0,1895,2210900,00.asp](http://www.eweek.com/article2/0,1895,2210900,00.asp)
[http://www.theregister.co.uk/2007/10/31/in_the_wild_osx_trojan/print.html](http://www.theregister.co.uk/2007/10/31/in_the_wild_osx_trojan/print.html)

[http://sunbeltblog.blogspot.com/2007/10/screenshot-of-new-mac-trojan.html](http://sunbeltblog.blogspot.com/2007/10/screenshot-of-new-mac-trojan.html)
[http://www.sunbelt-software.com/ihs/alex/virustotalmac12388.pdf](http://www.sunbelt-software.com/ihs/alex/virustotalmac12388.pdf)

There is a possibility you could have got it since porting from the Mac to Ubuntu Linux would be easy and the install mechanism is the same - you would do a sudo to install a "CODEC."  You get it only at a pseudo-porn site, and only if you do the sudo install.  I don't really think that is what is going on here, but if you did foolishly do that, boot to single user mode and do a:

# crontab -l

the restart of the trojan should be there.  But that assumes you know all of the stuff that was there in the first place.  Removing the following would get rid of it:

1. Remove the executable reported by the "crontab -l" command - duh!  Be careful what you remove - it would help to know what the real ones were at the start.

2. Remove that cron entry that restarts the trojan if it is killed.

3. Remove the start-up code for the trojan in the startup files.

I really don't think that is what is happening though.  It is more likely you have a faulty DNS server than doesn't report a host as dead but instead redirects you some place.  This can happen when you mistype the hostname you are going to.  Just remember to sudo only as a LAST RESORT, and never to install something from an untrusted source.  If you need a new codec to view or listen to something, unless you get it from Ubuntu - YOU DO NOT WANT IT!

---

### Post by houstonbofh on 2007-11-05
As a test, create a new clean user.  Can that user work without issues?  If yes, you can just wipe your browser type configs. (.mozilla and .java to start)

---

### Post by Halfling Rogue on 2007-11-05
> **hhhobbit said:**
> I really don't think that is what is happening though.  It is more likely you have a faulty DNS server than doesn't report a host as dead but instead redirects you some place.  This can happen when you mistype the hostname you are going to.  Just remember to sudo only as a LAST RESORT, and never to install something from an untrusted source.  If you need a new codec to view or listen to something, unless you get it from Ubuntu - YOU DO NOT WANT IT!

Definitely not that, because I know that the site in question that I'm trying to reach ( [http://altarstudio.mayshing.com/manga/](http://altarstudio.mayshing.com/manga/) ) is not dead, and the URL is fine. It loads the page, then after a second would redirect me to the imagefap site via Flash. When I vanilla'd Mozilla and lost the Flash plugin, it couldn't redirect me, but it kept giving me the bar at the top that says "you need to install this plugin to view all the stuff on this page", and the status bar said that it was receiving stuff from imagefap.com. I hadn't installed anything at all for weeks when I caught the virus, including codecs, so apparently visiting the website was all that was needed for me to get infected.

Fixing my /etc/hosts keeps it from redirecting now, but it's still *trying* to, so I know the virus is still there.

Also, I rm'd my .java, and now Firefox can't seem to use any java at all (including the js needed to let me log in to the Ubuntu forums ](*,) ). Do I have to reinstall it with the SPM or what?

---

### Post by LinuxGuy1234 on 2007-11-05
> **Halfling Rogue said:**
> Definitely not that, because I know that the site in question that I'm trying to reach ( [http://altarstudio.mayshing.com/manga/](http://altarstudio.mayshing.com/manga/) ) is not dead, and the URL is fine. It loads the page, then after a second would redirect me to the imagefap site via Flash. When I vanilla'd Mozilla and lost the Flash plugin, it couldn't redirect me, but it kept giving me the bar at the top that says "you need to install this plugin to view all the stuff on this page", and the status bar said that it was receiving stuff from imagefap.com. I hadn't installed anything at all for weeks when I caught the virus, including codecs, so apparently visiting the website was all that was needed for me to get infected.

Fixing my /etc/hosts keeps it from redirecting now, but it's still *trying* to, so I know the virus is still there.

Also, I rm'd my .java, and now Firefox can't seem to use any java at all (including the js needed to let me log in to the Ubuntu forums ](*,) ). Do I have to reinstall it with the SPM or what?

You got to re-configure it only:
```

sudo dpkg-reconfigure firefox

```

If that doesn't work, reinstall Firefox from the SPM. I think the site has stuff from there. Here's a temp. fix:
Add:
127.0.0.1 altarstudio.mayshing.com
to /etc/hosts
or just don't go there. I think that Firefox should run plugins in a sandbox (in other words mean, if a redirect is caught, Firefox should block it and warn the user that a redirect was made and it was blocked. Also, system-wide changes should not happen.) Until this is fixed and it gets backported to Dapper and Edgy, this is a temp. fix.:popcorn:

---

### Post by Halfling Rogue on 2007-11-06
> **LinuxGuy1234 said:**
> Here's a temp. fix:
Add:
127.0.0.1 altarstudio.mayshing.com
to /etc/hosts
or just don't go there.

I need to go there, I do editing for her. I blacklisted imagefap in /etc/hosts, and that keeps it from redirecting, but like I said, it's still there if I check the error console.

I got rid of .macromedia, .java, .mozilla, completely got rid of Firefox and then reinstalled it with the SPM, and it's *still* there. I have no idea where this thing is hiding itself. Guess I'll just have to settle for blocking it.

---

### Post by LinuxGuy1234 on 2007-11-07
> **Halfling Rogue said:**
> I need to go there, I do editing for her. I blacklisted imagefap in /etc/hosts, and that keeps it from redirecting, but like I said, it's still there if I check the error console.

I got rid of .macromedia, .java, .mozilla, completely got rid of Firefox and then reinstalled it with the SPM, and it's *still* there. I have no idea where this thing is hiding itself. Guess I'll just have to settle for blocking it.

I guess it's a rootkit that smucked up to your system. I have a clean Dapper machine without it. Can you reinstall Dapper?

---

### Post by Frak on 2007-11-07
> **LinuxGuy1234 said:**
> I guess it's a rootkit that smucked up to your system. I have a clean Dapper machine without it. Can you reinstall Dapper?
I doubt its a rootkit. Use a LiveCD and see if it happens to you then.

---

### Post by Halfling Rogue on 2007-11-07
> **Frak said:**
> I doubt its a rootkit. Use a LiveCD and see if it happens to you then.

I'll give it a shot. If it *is* a rootkit, how do I stop this from happening again?

---

### Post by Frak on 2007-11-07
> **Halfling Rogue said:**
> I'll give it a shot. If it *is* a rootkit, how do I stop this from happening again?
Reinstall, only way.

---

### Post by Halfling Rogue on 2007-11-07
> **Frak said:**
> Reinstall, only way.

No, I got that part, but after I reinstall, is there something I can do to upgrade my security so that this doesn't happen again somehow?

---

### Post by Frak on 2007-11-07
> **Halfling Rogue said:**
> No, I got that part, but after I reinstall, is there something I can do to upgrade my security so that this doesn't happen again somehow?
Use a later version of Ubuntu.

---

### Post by Halfling Rogue on 2007-11-07
Great. That would be less of a problem if I wasn't worried that that would completely kill my external hard drive. It's barely working on Dapper as it is, and won't mount to Windows at all.

---

### Post by LinuxGuy1234 on 2007-11-08
> **Halfling Rogue said:**
> Great. That would be less of a problem if I wasn't worried that that would completely kill my external hard drive. It's barely working on Dapper as it is, and won't mount to Windows at all.

My bet is to NOT use the other drive (not the one that contains /usr, /lib, etc.). If you want to be secure, install:
* Firestarter (which is a firewall)
* rkHunter (which scans rootkits)

The Windows problem, use the drive as an FAT32 volume (not the one that contains /usr, /lib, etc.) (if you have Vista use Gusty and use NTFS).

---

### Post by Frak on 2007-11-08
> **LinuxGuy1234 said:**
> * rkHunter (which removes rootkits)

Only scans, doesn't remove. It's too risky to mess with Kernel Modules to remove them. Best to just reinstall.

---

### Post by Jittoku on 2007-11-10
Isn't firestarter only a frontend for iptables, which is already present in Ubuntu?  Actually, I don't know about dapper, but certainly later versions?

---

### Post by Frak on 2007-11-10
> **Jittoku said:**
> Isn't firestarter only a frontend for iptables, which is already present in Ubuntu?  Actually, I don't know about dapper, but certainly later versions?
A GTK frontend; yes.

---

