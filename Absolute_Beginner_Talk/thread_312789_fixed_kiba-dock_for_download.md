---
title: "fixed kiba-dock for download"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by shivshakti on 2006-12-04
This is an update of my original post... the package that I built is now very ancient indeed and there now exists a maintainer for the subversion build:


This is the kiba-dock.org website and the maintainer page:

[http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Dependencies]("http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Dependencies")

> Treviño manages a repo with kiba-dock, These can be accessed by adding the following to your sources.list file: Note: Currently, there are only 32 bit (x86) deb packages available, 64 bit users can use SVN.

   1. Configure your system to be using Treviño's repository by adding the following to lines in your /etc/apt/sources.list file:
          * If you are using Edgy Eft (6.10):
                o deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
                o deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
          * If you are using Feisty (7.04):
                o deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
                o deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
   2. Import Trevino's GPG key:
      $ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
   3. $ sudo apt-get update
   4. $ sudo apt-get install kiba-dock
   5. $ sudo apt-get install kiba-dock-dev
   6. $ sudo apt-get install kiba-plugins

PLEASE NOTE: this is a daily svn repo, which means you're dealing with snapshots of the latest and greatest, but not always the most stable!

This version really kicks. The package I tried works great. Even if you don't have 3D, it still runs in a basic mode which is a really nice touch.

Cheers all,
matt

>>>original post

Hi folks,

I've recently been playing around with kiba-dock. I couldn't find a deb package (although now I see some in this forum) so I built one to share, as compiling it wasn't a "just works" experience. I also feel that this hilarious program needs a wider audience!

My other motivation was to see how to make a Deb package as well :)

In this build, I have modified the source code to skip around the ^2 bug with some drivers/cards. What that means in plain English is that when zooming and pulsing, there will no longer be a white flash when the icon sizes to 32, 64 and 128 pixels and so on - you can see it happening in some of the Youtube / Google videos if you don't know what I mean.

I also took the liberty of including a desktop file (so it appears in the applications menu) and four starting profiles which sport a simple Ubuntu flavoured dock. I also changed the preload list of applications because some of them were not on the standard Edgy install as far as I recall.

Further instructions and some usage help are to be found in the README file. See the package description text prior to install as that will tell you where to find it, if you are not sure. Don't forget to execute the preload script before running it for the first time.

You will need compiz or beryl running to enjoy transparent icon backgrounds.

As this is my first Debian, I was only able to install it on my machine (under several user accounts) so *hopefully* it will work. Will some brave soul kindly post a success/fail message for the benefit of everyone and myself? Thank you kindly.

Enjoy!
matt

ps: As noted below, this is "expecting" GNOME, so if you use KDE (or XFCE perhaps), only one icon - The Gimp - will appear. Please have a peek at reply#15 on how to tidy things up nicely.


//deleted url//

See the attached picture. Sorry for the OS X icons :-#

---

### Post by nickburns on 2006-12-05
Works on my Edgy Eft...

---

### Post by shivshakti on 2006-12-05
Thanks for that! Quite a relief!

---

### Post by bornakke on 2006-12-07
Nice work!

---

### Post by shivshakti on 2006-12-08
Thanks mate!

I should have also mentioned that after starting it for the first time, you may have to restart it again for everything to be ship-shape

---

### Post by flapane on 2006-12-10
how to use on amd64?

---

### Post by shivshakti on 2006-12-10
Hi there. Sorry, I have absolutely no idea, I've yet to play with 64bit architectures. But if you want to build it yourself from CVS, I can post up the simple changes to the source code in the kiba-render.c file. You'll just need to insert a few lines in Gedit, save and then compile. I think some other folks have posted how to compile this... it's not totally straightforward, but not crazy either.

what say you?

cheers,
matt

---

### Post by flapane on 2006-12-10
that I am going to try first the 32version here, now the dock loads up, but it says:
flapane@a64:~/Desktop$ kiba-icon-editor.py
Traceback (most recent call last):
  File "/usr/bin/kiba-icon-editor.py", line 14, in ?
    import gconf
ImportError: No module named gconf

if I click on icon editor or open manually the icon editor.
how to fix it?

---

### Post by flapane on 2006-12-10
I've done it 
[http://www.youtube.com/watch?v=MiETvEIF-rE](http://www.youtube.com/watch?v=MiETvEIF-rE)

---

### Post by Rodneyck on 2006-12-10
It did not work for me and I am running edgy with beryl.

I got the icon in the menu, but nothing. I then ran it from the terminal and it gave me this...

 No such file or directory: '/home/rodney/.kiba-dock/profiles

I looked, and there is no .kiba-dock .  Any idea what is going on?

---

### Post by hollaburoo on 2006-12-10
> **Rodneyck said:**
> It did not work for me and I am running edgy with beryl.

I got the icon in the menu, but nothing. I then ran it from the terminal and it gave me this...

 No such file or directory: '/home/rodney/.kiba-dock/profiles

I looked, and there is no .kiba-dock .  Any idea what is going on?

I have the same problem.........

---

### Post by shivshakti on 2006-12-10
did you run from the command line:

populate-dock.sh

? That will create .kiba-dock if it doesn't already exists

Also, it will give you some starter profiles and some icons

If you did that and nothing happened, were you using another user account at the time?

matt

---

### Post by flapane on 2006-12-10
it added only gimp icon to me, (i use kde:P )

---

### Post by Rodneyck on 2006-12-10
> **shivshakti said:**
> did you run from the command line:

populate-dock.sh

? That will create .kiba-dock if it doesn't already exists

Also, it will give you some starter profiles and some icons

If you did that and nothing happened, were you using another user account at the time?

matt

No, I did not know I was suppose to do that. 

I did it, and it works, thanks!

---

### Post by shivshakti on 2006-12-11
> **flapane said:**
> it added only gimp icon to me, (i use kde:P )

Ahh, I only set it up for GNOME, I didn't think KDE would be so different. I suggest - if you haven't already - to open up the Icon Editor and delete all the icons except for the Gimp, because it will still be looking for them otherwise (and spewing out lots of errors). Then you can either drag and drop new icons in to the dock or manually input them via the editor. The editor is a better bet because the dock doesn't handle launcher %options very well right now.

matt :)

---

### Post by Rodneyck on 2006-12-11
Does anyone know if you can add any of the sytem applications to the dock, like trash can and Tomboy Notes, etc?

---

### Post by Julolidine on 2006-12-11
Heres the problem I get.  I can start kiba, and I see the little black thing.  I get the downward blue arrows where its supposed to be, but when I drag something on the dock I get this message

```

got desktop file: x-nautilus-desktop:///CD-RW%20Drive.volume
** Message: Cant handle Relative path
Use a programm for dragging wich sends a fullpath
xfce4-appfinder for example should work

```

Anyone figure this one out?  This is happened to me on two seperate computers.

EDIT:Ok this problem was fixed by running the same populate-dock.sh

---

### Post by flapane on 2006-12-11
> **shivshakti said:**
> Ahh, I only set it up for GNOME, I didn't think KDE would be so different. I suggest - if you haven't already - to open up the Icon Editor and delete all the icons except for the Gimp, because it will still be looking for them otherwise (and spewing out lots of errors). Then you can either drag and drop new icons in to the dock or manually input them via the editor. The editor is a better bet because the dock doesn't handle launcher %options very well right now.

matt :)

yep I exactly did in this way and added my icons you can see in the youtube video, it works better than kxdocker with beryl.

---

### Post by shivshakti on 2006-12-12
> **Rodneyck said:**
> Does anyone know if you can add any of the sytem applications to the dock, like trash can and Tomboy Notes, etc?

Well, not really because the program is still quite young, but it will happen at some point according to the comments in the source code.

The issue is lack of drag-and-drop to the icons and the way Kiba executes command lines. Once that is resolved I suspect everything will be peachy. 

You can create a pseudo bin by creating an icon, that executes the following (assuming GNOME):

nautilus /home/<!-username->/.Trash

Where <!-username-> is replaced with Rodneyck or whatever you log in as. You would think that $HOME/.Trash would make more sense, but kiba doesn't yet recognise that and literally calls nautilus with "$HOME/.Trash" which means absolutely nothing to nautilus.

Regarding Tomboy, you can call it from kiba but it's not a good way of doing it. If you create an icon and give it the execution line of "tomboy" it will run tomboy and tuck it away in the system tray - invisibly. But if you press ALT-F11/F12 it works just fine.

I am sure there's a better way of doing that though!

matt

---

### Post by Rodneyck on 2006-12-12
Thanks matt, good to know. I may wait and bring it out later when more development has gone underway. I really rely on a lot of the system applications and like them docked, just a personal thing. 

I do like the app. Glad that Linux has such a rival.

---

### Post by HighD on 2006-12-12
Great job! Now if I could only fix this...

My background style are these blue stripes. Any idea how I can fix this? Change themes? I have beryl but I don't want to use it right now, so no transparency.

[ATTACH]20937[/ATTACH]

---

### Post by Rodneyck on 2006-12-12
I got that also. I am sure there is a better and easier fix for this. 

The way I fixed it was to download someone elses Kiba-dock profile and replace it with the default one. Search under the official beryl forums for the kiba-dock profiles.

---

### Post by croppyboy on 2006-12-13
Thanks for the work Matt! I installed the deb just fine . . . I running it on Edgy with Beryl 0.1.3 . . .

My only problem is with the text . . . it looks almost like double-vision . . . any idea on how to correct this?

[IMG]http://files.myopera.com/croppyboy/albums/125565/Screenshot.png[/IMG]

---

### Post by flapane on 2006-12-13
I enabled the auto hide, but the dock shows up too early, even when I put the arrow mouse 
at 20% of the screen, while it should show up only when I touch the lower edge of the screen. How can I set the no-hide area?

---

### Post by shivshakti on 2006-12-13
> **HighD said:**
> Great job! Now if I could only fix this...

My background style are these blue stripes. Any idea how I can fix this? Change themes? I have beryl but I don't want to use it right now, so no transparency.



Thanks. If you run populate-dock.sh from the command line (hit alt-f2) it will set things up for you and remove the icky background. If you have icons you will probably loose them, however it's kinda neccessary to run that script. Alternatively, run this from the command line:

```
cp /usr/share/kiba-dock/dock.txt $HOME/.kiba-dock
cp /usr/share/kiba-dock/rope.txt $HOME/.kiba-dock
cp /usr/share/kiba-dock/spring4all.txt $HOME/.kiba-dock
cp /usr/share/kiba-dock/wobbly.txt $HOME/.kiba-dock
```

You will need to restart kiba (possibly twice...) before it will see these profiles.

> **Rodneyck said:**
> I got that also. I am sure there is a better and easier fix for this. 

The way I fixed it was to download someone elses Kiba-dock profile and replace it with the default one. Search under the official beryl forums for the kiba-dock profiles.

Am I right in thinking you ran populate-dock.sh yet have no profiles available? 

> **croppyboy said:**
> Thanks for the work Matt! I installed the deb just fine . . . I running it on Edgy with Beryl 0.1.3 . . .

My only problem is with the text . . . it looks almost like double-vision . . . any idea on how to correct this?

You're very welcome. Re the text... not sure how you got that, the populate-dock.sh script should have changed all of that... but anyway, you will need to run Gset-kiba (from the sys tray icon) and click on the upper TEXT tab. Change the TEXt BG STYLE box from "gnome-dock" to "gradient" to remove the stripes. From there you will need to select SIZE/POS tab and change the "Shadow Offset" setting. I have it at "1"

Then select the COLOUR/ALPHA tab and do something sensible with the colours (unless you like it striped). It appears colours 4 & 5 have no effect with the gradient setting]

> **flapane said:**
> I enabled the auto hide, but the dock shows up too early, even when I put the arrow mouse 
at 20% of the screen, while it should show up only when I touch the lower edge of the screen. How can I set the no-hide area?

Aha, you'll need to do this: execute Gset-kiba from the sys-tray icon then on the DOCK tab and under the STYLE/MISC sub-tab to the right you will see some sliders for AUTOHIDE. You need to waggle the "Hide Area" one to a lower value

:) 
matt

---

### Post by croppyboy on 2006-12-13
Thanks, Matt! Worked like a charm . . .

---

### Post by DJ-Power on 2006-12-21
I get this when I run the deb file anyone know how to fix?

ERROR: Dependency is not satisfiable: libatk1.0-0

I am sure this must be simple to fix but then so am I lol
Regards
DJP :)

---

### Post by xopher on 2006-12-21
Nice work yeah, do you have debianized sources uploaded somewhere too, or is someone else doing an amd64 version of this? ;)

Thanks

---

### Post by flapane on 2006-12-21
> **shivshakti said:**
> 
Aha, you'll need to do this: execute Gset-kiba from the sys-tray icon then on the DOCK tab and under the STYLE/MISC sub-tab to the right you will see some sliders for AUTOHIDE. You need to waggle the "Hide Area" one to a lower value

:) 
matt

thank you so much!!!!!!!

---

### Post by nibi on 2006-12-22
Can anyone tell me how to fix this dependency error that i am getting? I am sorry if its a really obvious but i am totally new to this and thought just installing the deb package would do it.

---

### Post by nibi on 2006-12-28
Managed to fix all the dependencies and installed kiba-dock without any problems. When i try running it however, nothing happens. I tried the populate-dock.sh thing but that doesn't work either. Can anyone tell me whats wrong or what i need to do? I am using Beryl on Kubuntu (KDE) by the way.

---

### Post by croppyboy on 2007-01-06
flapane,

I had kiba working under 32-bit Ubuntu but I decided to go ahead and install the 64-bit (both Ubuntu and Kubuntu) . . .

How did you get kiba to work on the 64-bit architecture?

---

### Post by flapane on 2007-01-07
I fixed all the 32bit lib dependencies

---

### Post by Weav on 2007-01-08
Hi when I try to install the deb it gives me: "Error Dependency is not satisfiable: libatk1.0-0"

But I check libatk1.0-0 and i already have it installed and on my computer but yet i still get this error?

Anyone know what is going on? Thanks

---

### Post by shivshakti on 2007-01-12
Sorry been away for a while, hence being so quiet.

Weav, are you running Dapper? I quickly googled your dependency issue and apparently it's an Edgy/Dapper thing. Have you tried forcing the install? Maybe you'd want to research it if it doesn't work.... maybe the edgy library will work in Dapper, but I am just supposing as I have no idea about that kind of thing. Perhaps someone else could advise?

As per the 64bit folks out there... If I still have the source code, I will post up the mods - it's only a few lines of code (a real anticlimax). The remainder of the package should hold good though, so given a self compile, you could copy over the config files in the .deb to get you started. I think there are some howto's on CVS compilation elsewhere in this forum.

I've recently given my pc away as I'm going walkabout very soon but may still have the source code... will check it out late next week when I next see that particular computer. I have no idea if CVS has changed since my compile, so if I find the mods I made, good luck with inserting them!!!

matt

---

### Post by amaan on 2007-02-28
so when i try running kiba-dock from terminal, i get a dock with all these blue stripes in the background...? heres what i get in the terminal window:

** Message: error parsing desktop file for /apps/kiba/launchers/spring: /home/amaanr/.kiba-dock/spring4all.txt is not a .desktop file

** Message: error parsing desktop file for /apps/kiba/launchers/wo: /home/amaanr/.kiba-dock/wobbly.txt is not a .desktop file

** Message: error parsing desktop file for /apps/kiba/launchers/DSC0: /home/amaanr/.kiba-dock/DSC00099.JPG is not a .desktop file

** Message: found unused desktop file in homdir
try to merge /home/amaanr/.kiba-dock/dock.txt to gconf

** Message: Failed to merge unused desktop file /home/amaanr/.kiba-dock/dock.txt. notifications: Bad key or directory name: "/apps/kiba/launchers//file": Can't have two slashes (/) in a row

(kiba-dock:5387): GConf-CRITICAL **: gconf_client_get_string: assertion `err == NULL || *err == NULL' failed
** Message: found unused desktop file in homdir
try to merge /home/amaanr/.kiba-dock/rope.txt to gconf

** Message: Failed to merge unused desktop file /home/amaanr/.kiba-dock/rope.txt. notifications: Bad key or directory name: "/apps/kiba/launchers//file": Can't have two slashes (/) in a row

(kiba-dock:5387): GConf-CRITICAL **: gconf_client_get_string: assertion `err == NULL || *err == NULL' failed
** Message: found unused desktop file in homdir
try to merge /home/amaanr/.kiba-dock/spring4all.txt to gconf

---

### Post by shivshakti on 2007-03-02
It looks to me like you didn't run populate-dock.sh from the command line. Try that and then ll your problems will resolve. I am assuming you are running on Edgy, 32bit and GNOME.

--

Regarding the source code for 64bit compiles, I don't have it any more and as I'm now travelling I won't be hacking through it again, sorry.


I have no idea if Feisty will run with this package - I'm not in a position to change things right now, so if it doesn't work out that's life I guess.

Tashi delek!
matt

---

### Post by wataboutbob on 2007-03-02
Hi!

It was nice getting kiba to run in the 1st place. But despite my best efforts, I'm unable to remove the icky blue background. 

I tried running populate-dock.sh from terminal and Alt-F2. I get kiba now on the taskbar so to speak. But for whatever reason, any changes I make under gset-kiba don't get saved. Dock BG Style, Text BG Style - nothing. Only autohide... and I don't even use that :D

Any ideas?

I'm running 6.10 with Beryl running on nVidia-glx drivers.

---

### Post by shivshakti on 2007-03-03
Well, it seems like GConf is incorrect, but populate-dock should have sorted that out for you. Do you have a .kiba-dock directory? Does it have some desktop files and also some .txt files (profiles) in it? You ran populate-dock as a regular user? If you run as root it will probably fail.

I suggest using gconftool (I think that's the one... it's been a while since I've been using Linux) which will allow you to edit the "registry" so-to-speak. Again, I cannot give you specific instructions due to my present mobility, however in the applications area there should be *something* for Kiba-dock.  I suggest removing it, then try running ```
sh populate-dock.sh
``` again.

I hope that fixes it for you.

Good luck!
matt

---

### Post by philipho on 2007-03-13
Hi,

I am rather lost.

I downloaded the .deb file in this post to my desktop. Double clicked on this file and installed successfully. Following i did alt+F2 and typed in populate-dock.sh. Subsequently i am able to see kiba dock at application->system tools->kiba dock. When i click on kiba dock, another icon will appear on my top panel. I assume kiba dock is running already.

However, i am not able to see any default dock on my desktop. Does anyone know the reason? Help please =)

---

### Post by philipho on 2007-03-13
Anybody know what is the problem? It is something that has got to do with schemas?

When i go to kiba dock->preferences->launchers, each launcher will have an "exclaimation" giving schema error.

---

### Post by calvinthomas on 2007-03-13
For those who are unsure about Kiba-Dock or have problems with it (I got frustrated because after restarts, even with the rope model, the icons rarely went in a line and I had to restart it a couple of times, has this been fixed?) consider using Kooldock, its very nice, get the version from kde-apps.com (it works in gnome or KDE provided you have kde libraries) and a .deb is available on there. Use that version not any in repos because if you use those in repos you get an annoying border if you use beryl!

BTW Sorry for half hijacking the thread, if Kiba-Dock is working properly it is the nicest and most fun of the docks!

---

### Post by Necrome on 2007-03-18
Hi,

Kiba-dock seems to be working fine with me, except that the icons do not stop moving for a long time.. Is there a way to solve this problem?

Thanks..

---

### Post by shivshakti on 2007-03-19
Hi there, I think if you increase the "K" factor in the physics section it will dampen things down a little (in the readme.txt file it tells you how to do that). The various sliders interact with each other quite a lot, so be careful how you adjust them or things can go seriously Vista.

have fun!
matt

---

### Post by Lymen on 2007-03-20
Thank you!  It worked beautifully in my edgy!

---

### Post by bchan90 on 2007-03-20
finally got kiba-dock installed thanks to that .deb

buuut of course im running into some problems now...the dock wont allow me to add any app's onto the dock...i only have two on there now (terminal and instant messenger).  any help would be appreciated thanks!

---

### Post by Slimshady on 2007-03-30
Can someone tell me what about the 64bit arch?     will it work well on 64 systems?

---

### Post by flapane on 2007-03-30
sure

---

### Post by Slimshady on 2007-03-31
when i try to install i get the error:
"E: Couldn't find package kiba-dock_0.1cvs20061110matt-1_i386.deb"
help....

---

### Post by dixy on 2007-03-31
I've installed this version and played with it for a while. It looks nice but unfortunatelly the dock sits on top of all windows whereas, normally, it should stay below. The option for putting the dock below windows is only in the newest versions but those versions are crashing.

---

### Post by nevernamed on 2007-05-28
Do you need to have beryl to install this?

---

### Post by Monstroxus on 2007-06-05
yes, otherwise you will not have the translucency, but a black color instead.

---

### Post by Inxsible on 2007-06-05
Does this work on Ubuntu Feisty ?

---

### Post by nevernamed on 2007-06-27
I just installed beryl on my system and I decided to try kiba-dock again, however, when I installed this package, everything looked like it worked out fine, but when I clicked on the icon Applications>System Tools> Kiba Dock nothing happens. Can someone please tell me what is causing this problem and how to fix it? Thanks!

---

### Post by BrandonD92 on 2007-10-21
Hey,
everytime i try and download it the package install window pops up but it says "Error dependency is not satisfiable: libatk1.0-0. what do i do??

---

### Post by shivshakti on 2007-10-21
Hi

This version of Kiba dock is one year old... and was built for Edgy Eft, so right now, things are looking pretty grim for it. I am amazed at how many people are still downloading this... it should have stopped ages ago. However, once I sneak a download of Gutsy, I will build a new version of it assuming the present CVS is working. I have the new files and everything has changed, hopefully the packaging will be more straightforward than the last time.

So anyway, give me a few weeks and I will insert new links to the new package. I will see if I can build for AMD64 as well, some clever people have been trying to fish it out of the directory, but there simply isn't a package to catch.

As stated at the top, I'm on my travels however I succumbed to buying a laptop and we all know where that will lead me to :)

all the best
matt

ps: try opening the terminal, ensure you're online, and enter "sudo apt-get install libatk"

I'm on a windows machine as I write this, so I can't be certain "libatk" is right, but that should do the trick. If you're running Gutsy then I have no idea if Kiba will work.

---

### Post by nevernamed on 2007-10-21
Wow, really? Yeah. I have Fiesty and I'm still using it. That would be really great if you could repost the new package when you get it working!!! I'll definitely download it :-D

---

### Post by GavinRoskamp on 2007-10-23
Hello, everybody!

I am glad to announce that Kiba-Dock Works in Ubuntu 7.10, Gusty Gibbons!!!

If you are trying to install it in gusty, there are a few things you should know:

After downloaded and installed, you must launch it from Applications-System Tools.
After it has launched, you must go to the Terminal, and type in "populate-dock.sh"

This will either refresh the dock, or create a directory, I have no clue what it does, but it works :)

If you need further instruction, e-mail me at [email]GavinsTipsAndTricks@Gmail.com[/email], and I will give you step-by-step instructions, if you ask for them.

Also, I believe that Kiba-Dock does NOT work in Ubuntu 6.06: If I am wrong, please feel free to correct me, by e-mail preferably

Thanks!!!

GavinRoskamp
P.S. The Same rules go for Feisty Fawn!!! (7.04):lolflag:

---

### Post by GavinRoskamp on 2007-10-23
> **shivshakti said:**
> Hi

This version of Kiba dock is one year old... and was built for Edgy Eft, so right now, things are looking pretty grim for it. I am amazed at how many people are still downloading this... it should have stopped ages ago. However, once I sneak a download of Gutsy, I will build a new version of it assuming the present CVS is working. I have the new files and everything has changed, hopefully the packaging will be more straightforward than the last time.

So anyway, give me a few weeks and I will insert new links to the new package. I will see if I can build for AMD64 as well, some clever people have been trying to fish it out of the directory, but there simply isn't a package to catch.

As stated at the top, I'm on my travels however I succumbed to buying a laptop and we all know where that will lead me to :)

all the best
matt

ps: try opening the terminal, ensure you're online, and enter "sudo apt-get install libatk"

I'm on a windows machine as I write this, so I can't be certain "libatk" is right, but that should do the trick. If you're running Gutsy then I have no idea if Kiba will work.
Hey, Shivshakti:
I have Gusty on a CD, and am just running it from the live cd, and it works just fine.
No need to recompile it, unless you really want to, so just thought you might wanna know!

Thanks
GavinRoskamp

P.S. -- I tried the "Sudo apt-get install libatk" and it came back with the message "Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libatk"

I am not a very experienced Linux or Ubuntu user, but from my knowledge, it seems as if it can't find "Libatk", whatever that is.
I hope you can fix it for the people needing it!!!
cheers!

Gavin

---

### Post by GavinRoskamp on 2007-10-23
> **nevernamed said:**
> I just installed beryl on my system and I decided to try kiba-dock again, however, when I installed this package, everything looked like it worked out fine, but when I clicked on the icon Applications>System Tools> Kiba Dock nothing happens. Can someone please tell me what is causing this problem and how to fix it? Thanks!
NeverNamed: Try typing in "Populate-dock.sh" this will hopefully fix your problem.
If it doesn't work, then keep trying to launch it, and then after a few more tries, go back to terminal, and type in populate-dock.sh again.

Hope this works!!!

Gavin

---

### Post by nevernamed on 2007-10-24
> **GavinRoskamp said:**
> Hello, everybody!


After downloaded and installed, you must launch it from Applications-System Tools.
After it has launched, you must go to the Terminal, and type in "populate-dock.sh"


Where does one download and install it? Has the new debian package been posted?
Thanks!!

---

### Post by GavinRoskamp on 2007-10-25
> **nevernamed said:**
> Where does one download and install it? Has the new debian package been posted?
Thanks!!
Well, it is the Download in the first post by the maker of it: it works with fiesty and gusty, so no matter what you are looking for it will work, just type in the code to reload it or whatever it does =-P

---

### Post by GavinRoskamp on 2007-10-25
> **nevernamed said:**
> Where does one download and install it? Has the new debian package been posted?
Thanks!!
Sorry, I haden't read what you were replying to... lol


Well, to download it, you just click on that link with a working internet connection, then after it has downloaded, it will probably automatically open itself with a program called "GDebI" or something to that effect.  Click "Install Package" when that window shows up, it will install, and you have it under Applications<System Tools<Kiba-Dock.

Click on it, and it should make a little icon appear in the notification area.  If it doesn't, then try to open kiba-dock a few more times.  If it still fails to create the notification icon, then open terminal in "Applications<Accesories<Terminal."

Once the Terminal opens up, type in "Populate-Dock.SH" and press <ENTER>

This will do its magic, whatever it does :) and it will make the icon appear, and possibly even the dock on the bottom of the screen!!!

If the dock doesn't come up, try launching it again, then populate-dock.sh again, and so on and so on.  If it still doesn't work, e-mail me at [email]GavinsTipsAndTricks@Gmail.com[/email] (I know, sounds weird, but its for my YouTube Show, GTT :) )


 would be happy to help you, since I am a Windows XP user, I don't use Ubuntu all that much, and only check this post when I'm in Ubuntu, so I can try any codes out, so if you e-mail me, I should be able to help you quicker.  Thanks for asking: I LOOOVE helping with computers ;)


GavinRoskamp

---

### Post by ehcualp on 2007-10-29
I tried "Populate-Dock.SH" but it failed to do anything. I tried "**p**opulate-Dock.SH" , with a lowercase 'p' and it sprung kiba-dock open.
I have a problem though, i can't change the settings. by going into the terminal, and typing in kiba-dock settings, nothing comes up. by typing in kiba-dock, nothing comes up. Im worried!
Edit: i forgot. im running gusty.
And for some reason it displays double lettering.
[http://img508.imageshack.us/img508/5524/screenshotpq4.png](http://img508.imageshack.us/img508/5524/screenshotpq4.png)

Edit(again): I discovered that by resetting, the settings box will now appear. But the double text still prevails~! i going to try to mess around with the settings and see if i can get it to go away.

---

### Post by kvonb on 2007-10-30
I got it working after loading one of the profiles and messing with the colours and transparency settings.

Feisty, Intel8255 (i810) running Beryl.

---

### Post by GavinRoskamp on 2007-10-31
> **ehcualp said:**
> I tried "Populate-Dock.SH" but it failed to do anything. I tried "**p**opulate-Dock.SH" , with a lowercase 'p' and it sprung kiba-dock open.
I have a problem though, i can't change the settings. by going into the terminal, and typing in kiba-dock settings, nothing comes up. by typing in kiba-dock, nothing comes up. Im worried!
Edit: i forgot. im running gusty.
And for some reason it displays double lettering.
[http://img508.imageshack.us/img508/5524/screenshotpq4.png](http://img508.imageshack.us/img508/5524/screenshotpq4.png)

Edit(again): I discovered that by resetting, the settings box will now appear. But the double text still prevails~! i going to try to mess around with the settings and see if i can get it to go away.
Well, I don't know why the double-text is there,,,, Mine doesn't have that....... oh, and you have to select a profile, then change it from there: sorry for not telling you :)

Good luck!!!
(I have no clue on the text!! :p)

---

### Post by ehcualp on 2007-11-02
Dont worry about it now. the double text disappeared, so its now back to normal.
i dont know why it was doing that, but im good now!

---

### Post by shivshakti on 2007-11-24
Guys, try going to the kiba-dock.org website, the whole gig has totally changed since I last looked at it, last year. Below is from this page:

[http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Dependencies]("http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Dependencies")

> Treviño manages a repo with kiba-dock, These can be accessed by adding the following to your sources.list file: Note: Currently, there are only 32 bit (x86) deb packages available, 64 bit users can use SVN.

   1. Configure your system to be using Treviño's repository by adding the following to lines in your /etc/apt/sources.list file:
          * If you are using Edgy Eft (6.10):
                o deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
                o deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
          * If you are using Feisty (7.04):
                o deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
                o deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
   2. Import Trevino's GPG key:
      $ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
   3. $ sudo apt-get update
   4. $ sudo apt-get install kiba-dock
   5. $ sudo apt-get install kiba-dock-dev
   6. $ sudo apt-get install kiba-plugins

PLEASE NOTE: this is a daily svn repo, which means you're dealing with snapshots of the latest and greatest, but not always the most stable!

This version really kicks. The package I tried works great. Even if you don't have 3D, it still runs in a basic mode which is a really nice touch.

I'm going to post this at the top of the thread too, because I'm receiving crazy amounts of downloads for this (now) ancient package of mine - over 500 for this month alone. So I hoped you enjoyed it, but try the above for something seriously fab!

Cheers all,
matt

---

### Post by celticbhoy on 2007-11-24
Tried the script on Gutsy all goes well, but after the initial populate command, how do I add other launchers ??

---

### Post by celticbhoy on 2007-11-24
Just worked out if I create a launcher on my desktop and open '.kiba-dock' from my home folder, then copy from the desktop to the .kiba-dock folder, and restart kiba-dock the new launcher will be there. Just need to figure out how to put a window switcher there.

---

