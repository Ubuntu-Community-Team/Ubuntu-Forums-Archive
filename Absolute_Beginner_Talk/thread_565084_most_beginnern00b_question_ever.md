---
title: "most beginner/n00b question ever"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by PegCitySkank on 2007-10-01
how do you zoom out of the desktop to get to the cube and make the windows go around the 3d cube

---

### Post by llamakc on 2007-10-01
1. You have to have Beryl/Desktop Effects/Compiz-Fusion installed & configured.

2. If you have already done that, you can hold down ctrl-alt and left-click your mouse to manipulate the cube.

---

### Post by Seisen on 2007-10-01
do you have beryl or compiz installed?

---

### Post by overlord.gaurav on 2007-10-01
Press the super key(windows key) and scroll backwords.

---

### Post by Beggar on 2007-10-01
> **overlord.gaurav said:**
> Press the super key(windows key) and scroll backwords.

You can do this, but it is kinda hard to control, easier way is hold left and right mouse buttons and then drag your mouse around.

Alternately ctrl-alt Left and right works just as well, just cant stare at the pretty :)

---

### Post by PegCitySkank on 2007-10-01
do i need both or just one or the other

---

### Post by llamakc on 2007-10-01
> **PegCitySkank said:**
> do i need both or just one or the other

Of what? Be specific. Are you replying to the suggestions about what commands to make it work, or what to install?

---

### Post by PegCitySkank on 2007-10-01
do i need both beryl and compiz   or either one will do

---

### Post by llamakc on 2007-10-01
[http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223) is the forum for these issues. What version of Ubuntu are you currently running? What sort of video card do you have? Have you tried enabling Desktop Effects yet?

---

### Post by overlord.gaurav on 2007-10-01
> do i need both beryl and compiz or either one will do
Either one will do.

> You can do this, but it is kinda hard to control, easier way is hold left and right mouse buttons and then drag your mouse around.

Alternately ctrl-alt Left and right works just as well, just cant stare at the pretty

Well, in that case, you can enter any combitnation you are comfortable with.
Launch CCSM >> Click on zoom desktop >> Action >> Double click the previous combination >> click on key >> Enter the NEW combination.

---

### Post by PegCitySkank on 2007-10-01
whats ccsm ( sorry i just got  linux/ubuntu today so i really don't know whats goin on) ( and before when i dragged the icon's to the side i could kinda see the cube turn, but now i can't

---

### Post by Faud on 2007-10-01
Ok, lets start from the beginning. What version of Ubuntu to you have installed ?

If you are running Fiesty Fawn then neither Beryl OR Compiz Fusion come installed with the operating system so you would have had to download them.

---

### Post by PegCitySkank on 2007-10-01
how do i check what version i have

---

### Post by Faud on 2007-10-01
It will say on the CD cover of the CD you have

---

### Post by coolen on 2007-10-01
Things you need:
Drivers you your graphics card. Go to a terminal and type in
```
glxinfo | grep direct
```
If it says Direct Rendering: Yes, then you're all set (to be sure, test out one of the screensavers...I like Atunnel).
Next (assuming you're using Ubuntu Feisty) go to System -> Preferences -> Desktop Effects and enable them. Your screen will lock up for a second or two, then come back with wobbly windows and a cube!
Next, install Compiz Fusion from Trevino's repository, or Amaranth's, because it's awesome and has better configuration options.

---

### Post by PegCitySkank on 2007-10-01
yea it's fiesty fawn,    so i have to download Beryl and compiz?

---

### Post by ryanVickers on 2007-10-01
this isn't the most noob question ever, I saw on some site this person asked "I just downloaded this file and I don't like it.  How do I download it back?" :p  Not kidding.

anyways, to help with this, they should just be in synaptic, so install them from there.

---

### Post by PegCitySkank on 2007-10-01
haha ok   that does win the most n00b/beginner question ever      so i download from here [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/) ?

---

### Post by ryanVickers on 2007-10-01
well, if you just type "gksudo synaptic" and search up "beryl, it *should* just show up...

---

### Post by PegCitySkank on 2007-10-01
type "gksudo synaptic"  where   goggle?

---

### Post by coolen on 2007-10-01
Alt + F2
gksudo synaptic

Alternatively, go to System -> Preferences -> Synaptiuc Pakcage Manager

Synaptic lets you install all available software for your system (you can add more repositories to get more software) and delete anything you have installed through APT, taking care of dependancies along the way.

---

### Post by ryanVickers on 2007-10-01
> **PegCitySkank said:**
> type "gksudo synaptic"  where   goggle?

hm, maybe "most noob" is appropriate :p

JK, in the terminal, or just go in System > admin > synaptic

it can install anything in found in your current repository list, like beryl (it *should* be in there...)

---

### Post by Faud on 2007-10-01
> **ryanVickers said:**
> hm, maybe "most noob" is appropriate :p

JK, in the terminal, or just go in System > admin > synaptic

it can install anything in found in your current repository list, like beryl (it *should* be in there...)

Yes, Beryl will be in there. Just click on it and mark for install, it will probaly pop up a window and say that it needs to install some other things as well...that is ok.

Then click apply

---

### Post by PegCitySkank on 2007-10-31
k i downloaded it    now what,  is it ready or do i have to do other stuff  if it's ready what key zooms in and out

---

### Post by coolen on 2007-11-01
Assuming you've got your drivers installed, hit alt+F2 and type beryl-manager.
Your screen should lock up for a few seconds, then you'll probably see a splash screen and your windows will wobble when you move them.

---

### Post by PegCitySkank on 2007-11-01
k i got it working thanks to everyone

---

### Post by PegCitySkank on 2007-11-04
it said    could not open location file:///beryl-manager   when i typed beryl-manager in gksudo synaptic

i had it before but then i restarted the computer and now it's not working

---

### Post by coolen on 2007-11-04
Where are you typing beryl-manager, exactly? You need to do it either in a terminal or the Run Application dialog (Alt+F2). The run application dialog is preferred, but if it doesn't work, then the terminal should give you more info.

---

### Post by PegCitySkank on 2007-11-04
nevermind i got it

---

### Post by PegCitySkank on 2007-11-25
i was messing with the settings of beryl and now when i turn the cube any windows i have up will move away from it  how do i fix it

---

### Post by coolen on 2007-11-25
Disable (or play with the settings of) the 3D window plugin (or whatever it's called).

---

