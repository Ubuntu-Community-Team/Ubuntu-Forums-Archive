---
title: "Compiz-Fusion"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-07
Does anyone know how to install Compiz-Fusion for Gutsy Gibbon?

---

### Post by llamakc on 2007-11-07
It's installed by default. What sort of video card do you have?

---

### Post by dhobbs on 2007-11-07
It comes in the standard installation.  You may want to install ccsm (compiz config settings manager) though, as that will give you the ability to customize each fusion plugin.

---

### Post by RobotoWorks on 2007-11-07
What do you mean?

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> Does anyone know how to install Compiz-Fusion for Gutsy Gibbon?

Didn't I give you this link before:

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by llamakc on 2007-11-07
> **RobotoWorks said:**
> What do you mean?

What do you mean? I asked a question. You need to answer that.

---

### Post by RobotoWorks on 2007-11-07
That is for Fiesty Fawn

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> That is for Fiesty Fawn

Read the documentation again.

---

### Post by dhobbs on 2007-11-07
Compiz Fusion is installed by default in Gutsy Gibbon (7.10).  In order to turn it on you need to go to System -> Preferences -> Appearance -> Visual Effects

From there you get to choose, though if you really want to customize it you need to install ccsm, as mentioned above.

As a side note, if you do this and the effects do not work you may have a graphics card problem, which will require more work.

---

### Post by RobotoWorks on 2007-11-07
Its says for Ubuntu7.04 and Kubutuntu, sorry for this but I also dont understand the steps, Im a total noob

---

### Post by llamakc on 2007-11-07
And we're back at my post #2 where I want to know the OP's video card.

---

### Post by RobotoWorks on 2007-11-07
Sorry I dont know what a video card is and how do I install ccsm?

---

### Post by dhobbs on 2007-11-07
> System -> Preferences -> Appearance -> Visual Effects

If you installed 7.10 then you already have Compiz Fusion installed, just click on the System menu and follow the trail to the rainbow.

---

### Post by akiratheoni on 2007-11-07
> **RobotoWorks said:**
> Sorry I dont know what a video card is and how do I install ccsm?

Applications -> Accessories -> Terminal

Type in 
```
sudo apt-get install ccsm
```

Should do the trick.

---

### Post by Paul820 on 2007-11-07
Go to System->Administration->Synaptic Package Manager and search for 'compizconfig-settings-manager' or go to the terminal and type, or copy and paste the following
> sudo apt-get install compizconfig-settings-manager

---

### Post by Paul820 on 2007-11-07
> **akiratheoni said:**
> Applications -> Accessories -> Terminal

Type in 
```
sudo apt-get install ccsm
```

Should do the trick.
 That won't work, it's 'compizconfig-settings-manager'

---

### Post by dhobbs on 2007-11-07
As for ccsm you go to Applications --> Add/Remove Programs.  Make sure that you have "Show: All Available Applications" selected in the upper right corner.  Then search for 'compiz' or 'Advanced Desktop Effects Settings (ccsm)' and install that.

p.s. A video card is a piece of hardware (usually by Nvidia, ATI, or Intel) that allows for very fast graphics acceleration.  If you see any of those names on a sticker plastered on your computer somewhere than you have a video card installed on your machine.  If not then you may be using onboard graphics which might not work with compiz.

---

### Post by RobotoWorks on 2007-11-07
What exactly would be the rainbow?

---

### Post by dhobbs on 2007-11-07
Forget the rainbow, just follow the menu trail to the Visual Effects tab and turn it on.

---

### Post by RobotoWorks on 2007-11-07
THanx for all the help, you guys are the best! I have it all working now

---

### Post by dhobbs on 2007-11-07
Success!!!

Hope you enjoy the eye candy!

---

### Post by llamakc on 2007-11-07
Woohoo! Congrats!

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> THanx for all the help, you guys are the best! I have it all working now

Good deal.  Please mark this SOLVED using the Thread Tools.

Thanks.:guitar:

---

### Post by Stikky on 2007-11-07
I have a couple of questions about Compiz-fusion and a couple of other things I figured I'd ask here instead of starting a new thread...

I installed the advanced desktop effects editor thing and that's cool, I have customised a few things in that and have got it how I like it.. I was just wondering, though, how do I get the expo thing to show me all the applications running on my desktop rather than showing me all my desktops when i press "Windows key + e"? Does anyone know how to do that? (Or even what I am talking about) I want it to do what OSX does where you can select something on the screen and it maximises it..

Also, I want to set up a shortcut whereby my desktop shows when I press "Windows key + m". I went into keyboard shortcuts in the System > Preferences thing but when I try and add a new shortcut to the "Hide all windows and focus to desktop" option, I press the windows key and it comes up with "Super L" (I assume the L is for left) and then when I hold it down and press "m" it just flashes and still says "Super L" in the shortcut box. Then, it makes the windows key my "show desktop" shorcut! I tried everything, I couldnt get it to recognise the windows key AND something as a shortcut :(

I probably havent explained myself very well, my brain isnt functioning today since it's (effectively) friday for me.. Anyhoo, any help anyone can offer would be awesome.

Thanks.

---

### Post by RobotoWorks on 2007-11-07
Off-Topic but when I try to install stuff through Terminal and I enter a sudo code, it asks for my password, but it wont let me type it in

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> Off-Topic but when I try to install stuff through Terminal and I enter a sudo code, it asks for my password, but it wont let me type it in

You password will not echo (display) on screen when you type it. Just type it in and hit ENTER.

---

### Post by dhobbs on 2007-11-07
Roboto - It is typing it in, as a security measure the characters you type are not displayed on the screen.

Stikky - What you are looking for is called 'Scale' and maybe even the Scale Addons.  That's the plugin that will show you all of the windows.  As for the hotkeys, I haven't messed with them yet so I can't tell you, sorry.

---

### Post by Zyphrexi on 2007-11-07
i'm lmao at this thread, but then again, i'm drunk. Disregard whatever I say.

you know what ticked me off about gutsy? having to install xgl-xserver in order to use compiz, what the heck is up with that?

---

### Post by RobotoWorks on 2007-11-07
Way Off-Topic, I installed the drivers(Atleast I think) for my Sierra Wireless AirCard 875 and it connects just find but when I try to go online it says that Im not porperly connected.And it wont let me visit any sites

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> Way Off-Topic, I installed the drivers(Atleast I think) for my Sierra Wireless AirCard 875 and it connects just find but when I try to go online it says that Im not porperly connected.And it wont let me visit any sites

Why don't you mark this SOLVED and start a new thread about the new problem.

---

### Post by RobotoWorks on 2007-11-07
> **akiratheoni said:**
> Applications -> Accessories -> Terminal

Type in 
```
sudo apt-get install ccsm
```

Should do the trick.
I did that but it said it couldnt find the package "ccsm"

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> I did that but it said it couldnt find the package "ccsm"

If you installed Compiz correctly, you should be able to type **ccsm** in a terminal and bring up the GUI.

---

### Post by RobotoWorks on 2007-11-07
I guess I didnt install this correctly, sorry bout bothering you guys, but I really dont understand this, can you guy give me the steps and the codes to installation? I also wan those cool 3d facts.

---

### Post by dhobbs on 2007-11-07
Follow these steps:  Open the System menu -->  Open the Administration menu --> click on the Synaptic Package Manage.  Now search for ```
compizconfig-settings-manager
```
Click on the checkbox next to the package name and then apply it.  That should download and configure the CCSM package which should then be accessible from the Appearance --> Visual Effects tab.

Another way of doing it is to open the Applications menu --> open the Add/Remove Applications program.  Search for Advanced Desktop Effect Settings and install that package (note: they are the same package, just different ways of getting to it).  If you don't see the Advanced Desktop Effect Settings program listed you need to make sure that you are viewing All Available Applications.

---

### Post by akiratheoni on 2007-11-07
> **Paul820 said:**
> That won't work, it's 'compizconfig-settings-manager'

Oops, my bad. I just installed fusion-icon and I can type in ccsm to open up the compizconfig-settings-manager so I thought that was it. Sorry!

---

### Post by RobotoWorks on 2007-11-07
How do I get the 3d effects?

---

### Post by RobotoWorks on 2007-11-07
Heres what I want: [http://gnome-look.org/CONTENT/content-files/68419-Captura_da_tela.png](http://gnome-look.org/CONTENT/content-files/68419-Captura_da_tela.png)
How do I get this?

---

### Post by dhobbs on 2007-11-07
You should enable and try out the various plugins in the compiz settings manager.  For the cube effect you need Desktop on a Cube and Cube rotate or something like that.  If you enable a plugin make sure you look at the hotkeys to trigger the effect or it'll be hard to know what they do.

As for the window borders that look Vista-ish in nature.  That's done by installing Emerald and using those themes, but there are plenty of forum posts out there on how to use Emerald.

---

### Post by thane1 on 2007-11-07
Unless the situation has changed since 7.10 was first released, Compiz is certainly installed by default.  However what may still not be installed by default, is compiz manager.  If you enter System-Administration-Synaptic Package Manager-<enter your administration password at the prompt>-Search-<enter compiz>-select and install "compiz settings manager", you will then have the management program, which will let you set up your compiz effects.  Then under System-Preferences-Advanced Desktop Effects Settings, you'll find all of your options to get Compiz up and running.  One of the things which make linux secure, is the installation program not automatically enabling everything possible under the sun by default.  Linux allows you the trade-off between security and compromising your security by opening a lot of doors by default.  Unfortunately this is part of the learning curve in linux and we (noobs) all have to deal with it in order to rid ourselves of our old ways of thinking :) .  In 7.04 loading Compiz was harder, as it needed to be done manually, but once loaded it automatically worked.  So its different, but only seems harder in 7.10.  Hope this answers, what I think your question was.  Cheers.

---

