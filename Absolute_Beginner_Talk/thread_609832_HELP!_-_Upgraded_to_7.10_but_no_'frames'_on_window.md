---
title: "HELP! - Upgraded to 7.10 but no 'frames' on windows"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by staib on 2007-11-11
I remember having this when first trying Beryl - and someone kindly helped me then. 

Today I decided to upgrade to 7.10 - all went well except that when Visual Effects are selected (seems to be the default) none of my windows have frames, so with no top bar visible can't be easiliy moved etc

Swiitching Visual Effects off fixes stuff, but there must be a better solution out there?!

Any help much appreciated - Nick

---

### Post by Happy_Man on 2007-11-11
When Visual Effects is active, press alt-f2 and enter ```
gtk-window-decorator --replace
``` Should get your titlebars back.

---

### Post by kshane on 2007-11-11
> **staib said:**
> I remember having this when first trying Beryl - and someone kindly helped me then. 

Today I decided to upgrade to 7.10 - all went well except that when Visual Effects are selected (seems to be the default) none of my windows have frames, so with no top bar visible can't be easiliy moved etc

Swiitching Visual Effects off fixes stuff, but there must be a better solution out there?!

Any help much appreciated - Nick

Try changing your themes.  You may need a different theme to define your windows better.

To move a window with no frame, try pressing <ALT> and left click hold and move the window that way.

Kevin

---

### Post by staib on 2007-11-11
> **Happy_Man said:**
> When Visual Effects is active, press alt-f2 and enter ```
gtk-window-decorator --replace
``` Should get your titlebars back.
Thanks HappyMan - this looks promising - I can't try it quite yet as my wife is working on the Linux box - doing her expense claims, so that has priority!
One other quick question - will I need to do that every time I log on?   If so, is there an easy way to launch it all automatically?
Thanks too kshane for the theme suggestion and tips about the 'alternative' way of moving a window :)

---

### Post by staib on 2007-11-11
Mmmm?

OK I tried HappyMan's suggestion - typing 'gtk-window-decorator --replace' into the Run command - but it had no effect.  Windows remain frameless and that other trick of using <Alt> and dragging doesn't work.  I also just noticed that the Close option (right clicking on the task bar at the bottom of the screen) also doesn't work.

Not sure if this helps but the other user (my wife) has no problems running Visual Effects :-(

Anyone got any other suggestions for me to try?!

Thanks - Nick

---

### Post by mahiyar on 2007-11-11
Just a guess on the premise that its working for one user but not the other. First come out of your Visual effects (right clicking desktop >change desktop background > visual effects whatever ) select the "None" in special effects. Now go to this directory ~/.config/compiz and rename the directory to oldcompiz or something. Log off and log in again. Then select the visual effects and see if it is ok.

---

### Post by staib on 2007-11-11
Well - it might have been a guess mahiyar, but it was a mighty intelligent one :)

Thank you so much.  That finally did the trick =D>

---

### Post by Happy_Man on 2007-11-11
That means you just messed up a setting somewhere. The directory Mahiyar told you to rename is where Effects (properly known as Compiz Fusion) stores its settings. WIthout the ~/.config/compiz directory found, the program just makes a new one and sets up the default settings. Just something you should know, in case this happens again. ;)

---

### Post by DutyDuty on 2007-11-11
Also, in the future ```
emerald --replace
``` may do the trick.

---

### Post by staib on 2007-11-12
Dear all,

I appear to have celebrated too soon :-(

Visual Effects is of course enabled by default - just came home, switched on and once again I have lost all window frames and there are strange graphics problems - at one stage Firefox seemed to have a mind of its own changing the shape of the window as I simply moved the mouse around - another time the desktop went pitch black!  The 'Appearances' window also opens tucked right up under the top bar...

This is all happening only on my profile (and disabling VE restores normal service).  The fact all is fine on my wife's profile suggests that its not really a hardware or driver issue (and on 7.04 all was dandy on both our profiles) but something is causing a problem on my profile - the trouble is I'm not really sure where to start looking...

What else can I sensibly check?!  I know someone has the answer (you always do!)

---

### Post by freddybob on 2007-11-12
if you are using an nvidia graphics card **[try this]("http://ubuntuforums.org/showpost.php?p=3572077&postcount=7")** it worked for me

---

### Post by staib on 2007-11-12
Thanks for that - I just noticed something that might offer more of a clue...

I went through the delete .config/compiz routine again and this time (like before) it seems to fix things.

I can see that the upper window frame (with VE enabled) has a glassy black look and stays that way regardless of the theme I choose when I am not in VE.  

I think that black theme (a sort of Vista look) was an old Emerald theme I had used in 6.10 or 7.04

How can I just get rid of it as I suspect this might be causing the problem!

---

### Post by mahiyar on 2007-11-12
In the earlier configuration (7.04) did you have beryl and emerald involved?

---

### Post by staib on 2007-11-12
Sorry Mahiyar - I got called through to dinner!

Yes - I did have beryl and emerald involved...   

Is this the problem?   Can it be resolved?!

Thanks,

Nick

---

### Post by DutyDuty on 2007-11-12
Sorry, I gave you the wrong code. Use ```
emerald --replace &
``` when you lose the frames.

---

### Post by staib on 2007-11-13
Thanks DutyDuty - I did just try that command but it had no effect :(

I am a wee bit confused here - should I have emerald installed in this version of Ubuntu?  Given the challenges of running Visual Effects on my profile I am beginning to wonder if it would be better to create a new profile and transfer my docs etc to that!    Failing that how can I make Ubuntu 7.10 remember my preference for no VE?  It always launches straight into a VE world.

---

### Post by Happy_Man on 2007-11-13
Well, if you don't have Emerald installed, that command won't work! :p

Have you looked in ~/.config/autostart? It may be that Compiz has put autostart directions for itself in there. Failing that, you may just have to go to System --> Preferences --> Sessions and disable the "Visual-AT" command in there. That should do it.

---

### Post by sailor2001 on 2007-11-13
alt/f2 type metacity --replace

---

### Post by staib on 2007-11-13
> **Happy_Man said:**
> Well, if you don't have Emerald installed, that command won't work! :p

Have you looked in ~/.config/autostart? It may be that Compiz has put autostart directions for itself in there. Failing that, you may just have to go to System --> Preferences --> Sessions and disable the "Visual-AT" command in there. That should do it.

OK - I checked ~/.config/autostart and there is indeed a Compiz Fusion and Emerald file in there - this contains the following:

Version=1.0
Encoding=UTF-8
Name=No name
Name[en_GB]=Compiz Fusion and Emerald
Exec=compiz --replace -c emerald --replace
X-GNOME-Autostart-enabled=true

Do I just delete this file - is it 'normal'?  Obviously I would far rather get VE working properly!

---

### Post by mahiyar on 2007-11-14
It might be that the old emerald file is creating a problem. Try renaming both the ~/.config/compiz/compizconfig/config file and ~/.emerald and ~/.beryl folders to "oldsomething", cross your fingers take a deep breath and restart / relog.

---

### Post by staib on 2007-11-14
It's certainly worth a try - sadly I can't do that from work and tonight I am only back home very late. but I'll try the re-naming of the config files to see if that sorts things out once and for all!

Added later: Mmmm? - no, it didn't help!

---

### Post by rasker on 2007-11-14
I'm a Fedora user but when I googled for my display problems I was sent to the many posts over here on the Ubuntu site about this very issue. I got enough info from the posts here that I was able to solve my problem.

So although the directory locations might be different I think I might be able to help solve this issue.

I have had the dissappearing window titles and  border thing a couple of times and it is quite the most annoying thing. I am trying to fix suspend/hibernate using the nvidia proprietary driver on my hp tx1000 laptop so I'm switching drivers quite a bit. Everytime I switch out of the proprietary driver I lose all my borders. Grrr

On Fedora there is a <home>/.gconf/apps/gnome-session/rh directory. Edit the %gconf.xml file and delete thethree lines that are the xml for the window manager. restart gnome (logout/login again or reboot). Everything should be back to normal. You will need to re-add the lines with a suitable window manager and the cleanest way is to enable and then disable desktop effects from the gnome desktop effects preferences tool.

Not sure if you will have a rh directory but the file will be somewhere around there.

Hope this helps someone out.

Cheers
R

---

### Post by mlissner on 2007-11-15
I am having this problem big time. I cannot for the life of me figure out how to get my borders back. I had them for a while there, and then for no reason at all, they seem to have gone away.

---

### Post by asafm on 2007-11-18
> **rasker said:**
> I'm a Fedora user but when I googled for my display problems I was sent to the many posts over here on the Ubuntu site about this very issue. I got enough info from the posts here that I was able to solve my problem.

So although the directory locations might be different I think I might be able to help solve this issue.

I have had the dissappearing window titles and  border thing a couple of times and it is quite the most annoying thing. I am trying to fix suspend/hibernate using the nvidia proprietary driver on my hp tx1000 laptop so I'm switching drivers quite a bit. Everytime I switch out of the proprietary driver I lose all my borders. Grrr

On Fedora there is a <home>/.gconf/apps/gnome-session/rh directory. Edit the %gconf.xml file and delete thethree lines that are the xml for the window manager. restart gnome (logout/login again or reboot). Everything should be back to normal. You will need to re-add the lines with a suitable window manager and the cleanest way is to enable and then disable desktop effects from the gnome desktop effects preferences tool.

Not sure if you will have a rh directory but the file will be somewhere around there.

Hope this helps someone out.

Cheers
R

dude, the file is empty (and it's in a different location).

Can some Ubuntu guys out there help??

---------
Here it is guys: the answer on another post:

[http://ubuntuforums.org/showthread.php?t=566765&highlight=visual+effects]("http://ubuntuforums.org/showthread.php?t=566765&highlight=visual+effects")

---

### Post by mlissner on 2007-11-18
For me the solution was to reinstall libdecoration0. I have no idea why that fixed it, but for some reason it did. Couldn't hurt.

---

