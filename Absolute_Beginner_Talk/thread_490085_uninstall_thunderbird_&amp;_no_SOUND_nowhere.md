---
title: "uninstall thunderbird &amp; no SOUND nowhere"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Haus Neuerburg on 2007-07-02
1.) is it poss to uninstall Thunderbird? I tried evolution out of curiousity and am well satisfied with it as it is faster(not offering so many gadgets but an integrated working calendar). As memory space is a big issue for my prehistoric machine I tried to uninstall Thunderbird via Synaptic but was then prompted that I wud also hav to uninstall the xfce desktop. Thus I abandoned this idea but am still interested whether it is at all possible.
2.) Almost all sound is gone! I can't play any musicfiles with xfmedia, evolution doesn't ring a bell when new mail arrives (that worked with Thunderbird though) only the system beep works and all sound-playing websites are mute. Where do I search for sound? Which pakets do I have to have and for which settings do I have to watch out?
Thankful for any hints and ideas
Haus Neuerburg
P.S. playing CDs with xfmedia worked before I had installed evolution, does that give any clue?

---

### Post by Haus Neuerburg on 2007-07-02
still haven't solved any of the mentioned points-anybody any idea?
Thnx

---

### Post by microsoft92sucks on 2007-07-02
I don't think you can uninstall stuff that comes with the x/k/ubuntu. And my sound stop working a few days ago and when I restarted it worked again so try that.

---

### Post by davidjmayo on 2007-07-02
If you are not running Thunderbird then it should not be using memory so need to uninstall it. 
(someone correct me if that's wrong)

however if it runs at boot (startup) we need to do something to stop that

I never used evolution so don't know if it makes any problems.

BTW
4 hours is not so long to wait for a reply-no need to bump. Remember the people in Europe who can help you are probably at work and our American friends are just waking up to go work so have been sleeping since you posted your question

---

### Post by Haus Neuerburg on 2007-07-02
thanks for your hints so far....@ davidjmayo: I didn't mean to be pushy,only feared that my questions might get lost on page 4,5,6,7....and as I'm a newbie I've no idea how to solve the problem.
I understood so far: as long as Thunderbird is unused it doesn't need any memory, so I leave it where it is. Is there any possibility to remove it from the applications-menue?
I still have the sound problem: where can I look for sound? Which pakets do I need? Which settings do I have to watch out for? Does anybody have an idea concerning the sound? Xfmedia doesn't play any CD at all.
Thnx again for any hints

---

### Post by davidjmayo on 2007-07-02
> Is there any possibility to remove it from the applications-menue?
I still have the sound problem: where can I look for sound? Which pakets do I need? Which settings do I have to watch out for? Does anybody have an idea concerning the sound? Xfmedia doesn't play any CD at all.


To remove thunderbird from the applications menu:

right click on applications menu
click edit menus
click internet
on thunderbird click the little box with the tick so it goes to an empty box then click close and you wont see it

I just checked and thunderbird is using next to nothing running on my system

to check open a terminal (applications==>accessories==> terminal

```
top
```

as to the sound I don't play mp3 but watch movies and never had sound problems

Try looking in on the right at the speaker icon
put the mouse over it and it will show master % (% of volume)
to change it right click then open volume control

If that does not help post back and I'll try to help

---

### Post by Haus Neuerburg on 2007-07-03
thanks a lot davidjmayo
-----the sound problem must be situated somewhere else......the sound percentage is 87%, xubuntu does play a sound prompting me to sign in at the splash screen when booting my computer and it also confirms correct login with a different sound (as set), but it doesn't play any cds no matter which format and all websites that play music e.g. remain mute.
As to the menu editing: I tried that but I must have missed something because Internet/Network doesn't appear as an option: here's a screenshot of what is available

---

### Post by davidjmayo on 2007-07-03
> the sound problem must be situated somewhere else.

whoops the instructions were for gnome not xfce. I've never used xfce.

For sound in gnome there is another way (It may be somewhere different in xfce).
System==>Preferences==>sound 

What media player are you using? Have you tried  different media players?

---

### Post by Haus Neuerburg on 2007-07-03
I'm using xfmedia that came with xubuntu
no, I haven't tried different media-players as it worked before I installed evolution ;) so I'm still suspetcing any kind of weird pakets or settings that were disabled with evolution

---

### Post by davidjmayo on 2007-07-03
There is a much easier way!  

minimise all windows so you can only see the desktop 

hit F1 key which will open ubuntu help center

in the search box type **sound**

this brings up a list of all things sound related (volume, music player, movie player etc.)

click on xfmedia

now you should see links relating to use; playing; volume etc. (or something like that)
follow the links and check your settings (I've never used fxmedia so can't advise on the settings but this should help you)

---

### Post by Haus Neuerburg on 2007-07-03
thanks a lot davidjmayo, but unfortunately xfce doesn't open help if F1 is pressed-I tried the help entry in the menu but that hasn't helped much either, there is no search box provided only a read-only html-doc called documenatation.......and that's not dealing with sound problems/settings...maybe I have to sleep a couple of nights over the problem and maybe it solves itself eventually?:confused:

---

### Post by alex_anthony on 2007-07-03
If I heard rightly you were worried about uninstalling the package 'xubuntu-desktop'?
I believe that is just a meta-package (it tells your computer to install other packages) so it can be removed without changing your system

---

### Post by davidjmayo on 2007-07-04
> If I heard rightly you were worried about uninstalling the package 'xubuntu-desktop'?
I believe that is just a meta-package (it tells your computer to install other packages) so it can be removed without changing your system


Are you **sure** that removing xubuntu-desktop won't cause any problems? I've seen posts before where people add KDE to gnome for example then remove gnome and cause many problems.

This is why I was looking for other ways to fix the problems.

If Haus wants to continue running xfce maybe we should consider (**not do** - yet) the Microsoft approach - a new install just with xbuntu. (I'm guessing that  Haus installed gnome first then added the xfce desktop. How did you install originally Haus?).

Of course if you reinstall you would need to backup your data especially the emails in Evolution.

David

EDIT: just came across this in another post (thread in full here [http://ubuntuforums.org/showthread.php?t=491804&highlight=meta-package](http://ubuntuforums.org/showthread.php?t=491804&highlight=meta-package)
> 
ubuntu-desktop is indeed a metapackage, which means that installing it will install all the applications associated with it. While it will have almost no effect, it's best to keep this package around in case you want to get rid of all those applications (for example if you installed kubuntu-desktop and no longer want GNOME et all).


the same should apply to xbuntu

David

---

### Post by Haus Neuerburg on 2007-07-07
thanks david and alex: I'm not too keen on any tinkering, so I just leave Thunderbird where it is. I still didn't manage to remove it from the applications menu, as that doesn't seem to be a feature in xubuntu.
No, I did not install ubuntu first, I had WIN98 on my computer, heard about ubuntu & its siblings and decided that xubuntu might be the best for my dinosaur;-) after "only" three installations everything works fine, except for the sound.
Does any one have any idea as to where I have to look? Which packages do i need? I stil think that my evolution install killed my sound as it had worked fine before that.
have a nice weekend
Haus Neuerburg

---

### Post by davidjmayo on 2007-07-07
Hi Haus

since you've been away I came across this "Comprehensive Sound Problem Solutions Guide v0.5e" [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

hope this can help you
D

---

### Post by Haus Neuerburg on 2007-07-08
thanks david: but if the soundcard wud not be supported than no sound at all wud be audable, right? I can hear the prompting sound when logging in and I can also hear the confirmation sound when logged in. But after than no more sound, well that's not quite true: I ran a small video the children made with a digital camera (format *.mov) and xfmedia did play the sound but not the pictures, still there was sound!!
It's all very confusing:confused::confused::confused::confused:::confused::confused::confused::confused:

---

### Post by davidjmayo on 2007-07-08
ummmm

if you followed the guide in the link not just for set up but the tests as well then I don't know

If you don't get anymore help how would you feel about a reinstall?

---

### Post by Haus Neuerburg on 2007-07-10
ummmmmmmmmmm, a reinstall? Gotta think about it hard and seek any other help option first.....until then this computer will remain mute .....THANKS a mill davidjmayo

---

### Post by davidjmayo on 2007-07-10
Haus 

don't give up yet - a new thread with a similar problem
Help may be here? [http://ubuntuforums.org/showthread.php?t=497755](http://ubuntuforums.org/showthread.php?t=497755)

---

### Post by Haus Neuerburg on 2007-07-11
david, no I won't give up, that poor guy with no sound after a Thunderbird installations hasn't found a solution either yet. I found something at least: follwing this link: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs)
I manage to play mp3-files in mpg123, still not in xfmedia, but at least some music on this machine ;-))

---

### Post by Haus Neuerburg on 2007-07-12
:popcorn:I seem to have solved it: after I had set mpg123 as standard application for *.mp3 and that had worked (a bit weird for a 20-years-long-Windows3.11 to XP-user to klick on a file, music is playing but you notice no obvious application opening), I installed the libxine-extracodecs and now xfmedia plays *.mp3! Maybe I can now listen to ordinary music cds aswell? That wud be just tooooooo gooooood!
But why was it disabled after I had installed evolution? Anyone any idea?
again, a big THNX to you david for all your efforts!

---

