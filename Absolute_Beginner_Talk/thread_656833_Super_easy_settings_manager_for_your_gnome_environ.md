---
title: "Super easy settings manager for your gnome environment! (by me :D)"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-03
**[COLOR=Red]NEW!! - I finally sorted it! :D[/COLOR]**

I have made a little script that works by changing keys in the gnome configuration "registry" (gconf) but to keep it easy, I have made it as user friendly as humanly possible as far as I'm concerned, and limited it to 28 of (what I think are) the most useful and most desired options to be able to change without hunting around for them!  To use it, simply download, extract, and run! (by double clicking the icon). [COLOR=Silver]You can run it in the terminal, or just plain old "Run", it doesn't really matter, but for appearances sake, just use "Run"[/COLOR]

FAQ (that I've bade up ;)):

Q) How to achieve such a sickening level of friendliness, comfort, and overall ease of use?
A) For one thing, having nothing that could scare the user is good - even when you are warning them, it is a good idea to state is as "information" and not have the big "warning" icon on your dialogs ;). For another, my theme just gets me in the mood - clearlooks with an olive/nature colour set :)

If there was one thing I could improve on, it would be the sorting of it ...

Q) Why make this utility?
A) I needed a simple way to just open one simple program, do some things, and leave all in one window in under a minute - I think maybe others can benefit from this too ;)  Think of it this way - you just come to a new install and you want to make sure your system will run the way you want - fire this up, check everything is how you like it, change some stuff and your done just like that! :p

Q) How did you learn to write any of this code?
A) I completely self taught myself what I know about bash by experimenting, previous programming experience in different languages, examining other scripts, and knowledge of any command and how it can be used (very useful!).  the program zenity, which is used to make all the graphical dialogs appear, I learned from man pages and a couple sites around the net.  To see the full power of this tool, check out my [(split) RAR maker]("http://ubuntuforums.org/showthread.php?t=556756") (yes, it can make split archives! :D)!  Another essential tool for the Linux user! ;)

Q) Why after using gconf-cleaner does it think I'm running GNSM for the first time again?
A) GNSM plants a key in /apps/GNOME-NAUTILUS-EDITOR/FIRST_RUN (boolean value) and gconf-cleaner sees it as unnecessary, thus making GNSM think it is a new computer.  This may also be true with other automatic cleaning tools.

Note: For the time being, I want to keep this proprietary, therefor you will not be able to edit the script!

Enjoy![INDENT]-ryanVickers

[/INDENT][COLOR=Silver]Please be aware that I do not endorse, condone, look down on, or favour the use of illegal torrents and content on Limewire and of the like just because that safety option is on in my pic - its on be default!![/COLOR]

---

### Post by ~LoKe on 2008-01-03
Could you tell us what 16 options is offers?

---

### Post by ryanVickers on 2008-01-03
oh, yes I suppose that would be a good idea... :rolleyes: lol
sorry :p, yes, it offers...

1. to show icons or not show icons on the desktop
2. to show or not show device icons on the desktop (Cd's, mp3 players, etc.)
3. to use single or double click
4. to use your home folder as your desktop
5. to display the mimetype warning (this happens under certain circumstances when the file extension and header data do not match up)
6. to put the text beside icons like windows tiles view
7. to use the tighter icon layout
8. to allow for manual arrangement of icons
9. to sort in reverse order
10 - 13: to show or not show the icons on the desktop for: computer, home, network, and trash
14. to confirm to empty trash and delete
15. to add a "delete" option to the menu along with the "move to trash"
16. to show "advanced" (more UNIX-like (apparently)) file permissions (as check marks instead of option-menus - I think this is much easier and nicer actually...)

I realize not all of these are hard to find ;), but for the sake of an easy way to do all this in one place... :D
and if you have any suggestions for more options... ;)

---

### Post by ~LoKe on 2008-01-03
That's a nice idea, I'm surprised it hasn't been done before (unless it has).  Are there any dependencies that a user would have to install in order to use it (a quick look tells me there aren't).

---

### Post by ryanVickers on 2008-01-03
it uses zenity - thats all, and I believe it comes pre-installed on all *buntu's, but I'm 100% sure it comes on Ubuntu

---

### Post by ~LoKe on 2008-01-03
> **ryanVickers said:**
> it uses zenity - thats all, and I believe it comes pre-installed on all *buntu's, but I'm 100% sure it comes on Ubuntu

Yep, it's installed by default in Ubuntu, and it should be default in kubuntu/xubuntu/etc as well.

---

### Post by ryanVickers on 2008-01-03
ok, a new feature is after the first time running the program, the user will be prompted afterwards with 2 dialogs asking for a mark our of 3 to do with how user friendly it is, and how good the selection of options are. :p\
I'm working on some enhancements to this, but for now it will simply say to please visit this site and say why its not good enough if they rate it lowly.

(I don't encourage tampering with my code ;), but if you want to simulate a first run again, go /apps/GNOME-NAUTILUS-EDITOR and turn on first run)

---

### Post by ryanVickers on 2008-01-03
It's interesting... the gTweak UI apps are rated 3 stars, and yet this is not getting nearly any attention... when I released my split rar maker, people just jumped on that like "I MUST HAVE IT!!!" and that was before the script was even graphical, before it had features for picking KiB, MiB, GiB, etc. even back when 10MiB meant 10 million bytes and not 10 real MiB :p

---

### Post by dimbulb1024 on 2008-01-03
cool script, thanks

---

### Post by Vadi on 2008-01-03
The looong list isn't too appealing. Imo, would be nicer if you teamed up with the ubuntu tweak guy,

---

### Post by PinkFloyd102489 on 2008-01-03
I like it. Fine just the way it is!


Keep up the good work.

---

### Post by ryanVickers on 2008-01-03
> **Vadi said:**
> The looong list isn't too appealing. Imo, would be nicer if you teamed up with the ubuntu tweak guy,

yeah, I know it's slowly getting too big, but I think it's nicer than hunting around in the gconf-editor for all this stuff, right?;)

---

### Post by Vadi on 2008-01-03
Not really, I don't even know how to find that one. It's either a specific programs preferences or ubuntu tweak (which already has everything organized neatly and in a scalable manner -hint-)

---

### Post by ryanVickers on 2008-01-03
Yeah, I think if there's one thing I need to do now is make it *look* as nice and easy as it really is... ;)

---

### Post by ExBuM on 2008-01-06
Nothing happens when I double click it :[

```
./GNSM-28_OPTIONS-SORTED
```
comes up with 
```
o&#1250;&#65533;;&#65533;&#65533;JT&#65533;&#65533;&#65533;?&#65533;P^
```

>_>

---

### Post by ryanVickers on 2008-01-06
works perfectly for me... are you sure you have the version in the tar.bz2 and not just the bz2? I noticed this with that one and fixed it my archiving the executable property :D

---

### Post by ExBuM on 2008-01-06
I'm not sure... I just downloaded it to my desktop and clicked extract here. When I right click there's nothing like "Run" only "Open." (Clicking that doesnt do anything) :/

---

### Post by Blutack on 2008-01-06
Whilst I am sure you are honorable in your intentions you realise there is no way of verifying your application will not damage my system, maliciously or not.

Any particular reason you do not wish to share the source, esp if as you claim it is just zenity?

Whilst you appear to be a community member of good standing this type of app sets a dangerous precedent, as you are essentially saying running an unverified binary file you found in a forum on a system is fine.

---

### Post by ryanVickers on 2008-01-06
I admire your paranoia :D ... in some instances it is a good thing to have ;)

I'll email you the code... like I said I just don't want people seeing it because as much as I'd like this to be GPL one day and have people expand on it, at the time being it's really a disaster from a code point of view... great to use, not great to base stuff off of ;)

---

### Post by ryanVickers on 2008-01-06
> **ExBuM said:**
> I'm not sure... I just downloaded it to my desktop and clicked extract here. When I right click there's nothing like "Run" only "Open." (Clicking that doesnt do anything) :/

ok, if you promise me you'll do the world a favour and not try to build on this mess ;), I'll give you the link to the normal file... *sigh*

[http://www.mediafire.com/?ftms3vnhzyn](http://www.mediafire.com/?ftms3vnhzyn)

---

### Post by ExBuM on 2008-01-06
> **ryanVickers said:**
> ok, if you promise me you'll do the world a favour and not try to build on this mess ;), I'll give you the link to the normal file... *sigh*

[http://www.mediafire.com/?ftms3vnhzyn](http://www.mediafire.com/?ftms3vnhzyn)
Thanks I can use it now x]
Don't worry I don't know how to build or whatever.. Total noob right here >_>

---

### Post by Blutack on 2008-01-06
Why not just unobsucificate the bash?  Your target audience don't care how it works anyway, and I would be much happier if I could at least see it WAS bash :-)

To be honest, most of my bash scripting is truly a thing of horror too!  All I would like to do is have a quick flick through for random rm's and wget's.  If there is anything glaringly obviously wrong people will post and complain, offer patches, you will fix it and you will learn and improve.  It's your app at the end of the day.  Everyone benefits.

Apologies for my paranoia but I can very easily envisage something like your application or an automatix knockoff being used to spread malware.

---

### Post by JoshuaRL on 2008-01-06
I know this is off-topic but Blutack has the coolest sig ever.  Ever.

---

### Post by Blutack on 2008-01-06
What's the problem?  I've seen packaged /etc/init.d scripts messier than that! :-)
Many thanks!
P.S If the shell script is the same as the binary it's clean and nicely written, and shouldn't eat any small animals you may or may not own.
P.P.S When it's Chuck against actually educating people, Chuck always wins.

---

### Post by ryanVickers on 2008-01-07
> **Blutack said:**
> What's the problem?  I've seen packaged /etc/init.d scripts messier than that! :-)
wow, beause I think this is something of a disaster compared to what I usually write... It works fine, that's the number 1 goal, but the code is a mess ;)

> **Blutack said:**
> 
P.S If the shell script is the same as the binary it's clean and nicely written, and shouldn't eat any small animals you may or may not own.
Yes its the same, I just isn't want anyone to make the mistake of using this as a base for something else yet (see above ;))

---

as for your signature, what if you have backups? :p

---

### Post by Xavieran on 2008-01-09
Clonezilla my friend ,Clonezilla ;)


P.S...Another nice script ;)...I would use it,but I like control...

---

### Post by nikoPSK on 2008-02-06
oh, fun. Never noticed these before in your sig...

---

### Post by ryanVickers on 2008-02-06
> **nikoPSK said:**
> oh, fun. Never noticed these before in your sig...

lol yea, it doesn't stick out like a sore thumb and catch your attention or anything... :p

---

### Post by nikoPSK on 2008-02-06
> **ryanVickers said:**
> lol yea, it doesn't stick out like a sore thumb and catch your attention or anything... :p

cool, I need to learn basic scripting... :)

---

### Post by ryanVickers on 2008-02-06
Yea, it's pretty much a must in Linux, but not just for making things, also for being able to read through a file so you can tell its good :p (lol me saying this and then providing a locked version of the code... :rolleyes:... oh well you can all trust me right? ;))

---

### Post by nikoPSK on 2008-02-06
> **ryanVickers said:**
> Yea, it's pretty much a must in Linux, but not just for making things, also for being able to read through a file so you can tell its good :p (lol me saying this and then providing a locked version of the code... :rolleyes:... oh well you can all trust me right? ;))

I can trust you... ;)

---

### Post by Kopachris on 2008-02-07
Looks good!  As soon as I get my 2node cluster up ([here]("http://ubuntuforums.org/showthread.php?p=4284737#post4284737").  Might have to scroll down or go back a few pages), I'll download and try this.  If I like it, do you mind if I include it in the Linux distro I'm making ([Dustbunny OS]("http://www.dustbunnyosd.tk")) as long as I give you credit for making it?  The plan for Dustbunny OS is to make an operating system with the power and customization of Linux and the ease-of-use and aesthetics of Mac OS X (and maybe some aesthetics of Vista.  It does *look* good).  This'll take a huge load off of me, because I won't have to program it.  Thanks!

---

### Post by ryanVickers on 2008-02-07
Sure!  It is supposed to be a lightweight distro, because with a name like that it could be - something for old hardware, but if not fine...
I'm just wondering because it requires the installation of zenity, and gnome, and gnome is not as light on the system as it could be ;)

To get to the point, I would love to have it included, but I'll make some modifications first, it's more of a stand-alone product fighting to the top :p

EDIT: Ok the new code is almost done, Very nice site by the way!  Looks very professional :p  (if it was me however, I might do something else with that thing that stays with you at the top)

---

