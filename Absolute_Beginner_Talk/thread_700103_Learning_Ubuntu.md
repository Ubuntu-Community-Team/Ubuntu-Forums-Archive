---
title: "Learning Ubuntu"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-02-18
So, hi, i'm the next newbie to cry. :]
I searched a little for help, but am having trouble with the tutorials actually..
There probably are tutorials around to suit my level (low) and so that's why im posting, to request a referral to a good tutorial :D

So this is my experience:
Ubuntu Gutsy installed perfectly and was an absolute delight to use.
Messing around with it has taught me little, but that's fine, I simply haven't probed hugely, on account of getting slightly overwhelmed ^.^
I thought I would start with installing WINE, to try and install and use Warcraft III.
So I googled some tutorials, and found one that looked nice. However, many of the points stumped me. This is the tutorial:

[http://www.pcmech.com/article/windows-to-ubuntu-transition-guide/](http://www.pcmech.com/article/windows-to-ubuntu-transition-guide/)

The first thing that burped was that I couldnt instantly locate Synaptic. My admin folder had only 6 links in it, of which none were Synaptic.
So found the file on the harddrive.
At this point I'm on the second page of that tut.
Then it says select Settings>Repositories, now, this option is greyed out :)
AT THIS point, I went to bed, but not because I was frustrated! Now Im up at the crack of dawn, to learn this beautiful thing! Please help!

P.S. Oh yes, and when editing the menus, I try to select Synaptic or some other elements, and after a second, they deselect themselves. It feels like a permissions thing, but I have no idea where to search to edit such things :(

---

### Post by tango_ninja on 2008-02-18
Hi, welcome to the forum! I'm still new myself...but I think I can help a little: You should be able to edit the menu items you see (including synaptic manager) by opening your Main Menu applet. This can be found under : 
[B]
System > Preferences > Main Menu
[/B]
or alternatively if its not there you can open via terminal:

```
alacarte
```

What sort of tutorials are you looking for? (i.e. what do you want to learn how to do)..something that might be pretty good to familiarise yourself with Terminal (your best friend) would be **[www.linuxcommand.org](www.linuxcommand.org) **

Let me know what exactly you're wanting to learn, might be easier to recommend help......

---

### Post by hungryOrb on 2008-02-18
Thanks for the reply :)
Well, using the main menu applet, only certain things will happily stay enabled, most others deselect themselves, I thought this was a permissions issue, but even setting permissions is beyond me at the moment :(
Synaptic is greyed out and there are no immediate answers :)
using Gutsy.

---

### Post by tango_ninja on 2008-02-18
hmm.... certain menu items will only stay enabled if there is something enabled under them...otherwise they will deselect. usually this is only the case with folders.

try running your Main Menu in the Terminal as sudo:

```
sudo alacarte
```

if there are any permissions issues this should help...

---

### Post by oedha on 2008-02-18
just like tango_ninja said.......
or
open software sources :==> system - administratrion - software source
here you have to activate 4 checkboxes...to get your repositories
if you're done...close it...and click reload button

open terminal :==> application - accesories - terminal
type :==> sudo apt-get update
then type :==> sudo apt-get install [I]application name

[/I]that's the terminal mode....if you can't find synaptic
or after software source...got to application - add/remove
search *program name* in *all available applications*

---

### Post by hungryOrb on 2008-02-18
Thanks for replies. :)
Running with terminal link: sudo alacarte
first asks for password, then does nothing.
Second time just does nothing as well, but without the password.

Software sources does not exist in that menu currently. I can see it in the main menu applet but cannot enable it as all of the items in that folder deselect themselves automatically and do not stay enabled.

Opening Synaptic gives very few options.
BTW, how do you take and save screenies in ubuntu? ^.^

---

### Post by hungryOrb on 2008-02-18
I'm more sure now that its a permissions issue. I can't install flash/gnash swf because sudo stops. But how do you access the user settings? When installing, Im pretty sure it didnt ask me about an admin account..

---

### Post by oedha on 2008-02-18
when installing....you will be asked username and password.....did you make it ?
this username and password can act as the root/superuser.......
how bout alacarte only.......i never use it with sudo

---

### Post by yoghurt on 2008-02-18
In ubuntu, the very first account you create has sudo privileges (the others might have it as well ... not sure) so you would typically do
```

sudo xxx (xxx being the command you want to run)

```

You'll get asked for sudo password - that is your account's password. I'm not very experienced myself, but you can find plenty of help on ```
http://ubuntuguide.org/wiki/Ubuntu:Gutsy
```.

PS: sorry if I'm breaking any forum rules by posting links to different websites...

---

### Post by hungryOrb on 2008-02-18
Oh ._. I realise, I did make 2 accounts :D Found it and all is resolved :) Thanks guys ^^
really silly meh :(

---

### Post by tango_ninja on 2008-02-18
ah..beat to it.

as yoghurt said, you should have created a sudo (super user do all :)) account during your install...running **sudo xxxxxx** will ask for the password on that account, and entering it in Terminal will allow you to run that command (in this case **alacarte** / Main Menu) with sudo permissions. you won't be able to see the password you type in, but if you type it correctly and press 'enter' you should see Main Menu run....

as for screen shots, if you haven't changed any keyboard shortcuts in Ubuntu since install, taking a complete screen shot can be done by pressing **printscreen** and taking a screenshot of the active window can be done by pressing **alt + printscreen**

---

