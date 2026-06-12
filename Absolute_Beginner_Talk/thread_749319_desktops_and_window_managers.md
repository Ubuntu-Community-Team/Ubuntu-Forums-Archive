---
title: "desktops and window managers"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-08
Hello forum people,

i am getting a little confused with Linux again.

My confusion is around desktop environments and window managers...

i read that Gnome is a DE  (Desktop environment)

and something like Fluxbox is a WM  (Window manager)

i read that Gnome uses a WM called metacity inside itself....

i read that the tools that Gnome offers the user ONLY work with that specific WM (metacity.)..hence the whole thing of gnome wraps up-together to become a DE  (Desktop environment)

so if i install ubuntu ....then i install and use the Fluxbox  WM......does this mean that NON of the tools offered by ubuntu will show up in my Fluxbox WM applications options?

also, what happens when i want to install a tool from within Fluxbox that says it needs Gnome?

hope you can explain this simple differentiation between a DE and a WM...

thanks

Vince.

---

### Post by abhiroopb on 2008-04-08
I'll try and give this a go.

Ubuntu is sort of like the entire package. A desktop environment is sort of like the GUI that allows interaction between the user and the operating system (ubuntu). Gnome and KDE are two different iterations of a desktop environment. A window manager is much like a theme (not the best way of describing it), its sort of like another layer on the desktop environment, but while the DE is like the nuts and bolts, the WM is usually more to do with eye candy.

Correct me if i'm wrong!

---

### Post by vinceUUUU on 2008-04-08
Hello,

thanks for your reply...

yes, i understand what you say about desktops and window managers....

so is my assumption correct?....in my first post here?

is it correct to say what i say about gnome tools and other WM's?


thanks

VInce.

---

### Post by abhiroopb on 2008-04-08
I think if u use fluxbox then u will be alright...but don't quote me...I suggest waiting for a few more replies on this thread

---

### Post by Therion on 2008-04-08
It IS confusing, isn't it?  abhiroopb is correct I believe, as well.  Too build on that, yes, you've got the Desktop Environment which controls how the user works with the operating system to a certain degree.  This is Gnome or KDE or Fluxbox or what have you.  Each have their own ideas about how best to do that and offer differing choices to the user.

Then you have the Windows Decorator, the Windows Manager and the Windows Compositor.  Metacity is a windows Manager.  It controls how certain aspects of your windows look (radio buttons and slider-bars for instance).  

The Windows decorator (usually GTK or Emerald in Ubuntu) determines how your window borders and min/max/close buttons look.

The Windows Compositor (Compiz in Ubuntu by default) determines how windows act in the operating system (like wobbling, minimize and maximize animations and such to name just a couple possibles).

That's MY understanding of the whole situation, but feel free to correct me as well!

---

### Post by vinceUUUU on 2008-04-08
Hello again,

yes, thanks for your reply...

it's tricky isn't it

i understand what we have spoken of so far....

.....i presume therefor...something like the Fluxbuntu distro...has had those nuts and bolts we talked about, wired into the Fluxbox WM from ubuntu gnome tools....to make a full distro called Fluxbuntu...(gnome derivative distro)...giving a Fluxbox style DE

so i guess then that certain WM's are derivatives of gnome...and others lend themselves to KDE styles of linking?...and other WM's derive from yet other things....

like you say though...wait for some more education on this forum

thanks

VInce.

---

### Post by kolisikepu on 2008-04-08
> **Therion said:**
> It IS confusing, isn't it?  abhiroopb is correct I believe, as well.  Too build on that, yes, you've got the Desktop Environment which controls how the user works with the operating system to a certain degree.  This is Gnome or KDE or Fluxbox or what have you.  Each have their own ideas about how best to do that and offer differing choices to the user.

Then you have the Windows Decorator, the Windows Manager and the Windows Compositor.  Metacity is a windows Manager.  It controls how certain aspects of your windows look (radio buttons and slider-bars for instance).  

The Windows decorator (usually GTK or Emerald in Ubuntu) determines how your window borders and min/max/close buttons look.

The Windows Compositor (Compiz in Ubuntu by default) determines how windows act in the operating system (like wobbling, minimize and maximize animations and such to name just a couple possibles).

That's MY understanding of the whole situation, but feel free to correct me as well!

You've hit the nail on the head... just in a few posts above, I think Fluxbox was mistaken as a windows decorator (in a way it is), but it is an environment similar to Gnome and KDE.  It is built to run on not so grunty pc's, hence why it is used in DamnSmallLinux.  It's small enough, because it doesn't have all the bells and whistles like Gnome or KDE.

I was going to attach in another way, but Therion explained it alot nicer.

---

### Post by herbster on 2008-04-08
To keep it as simple as possible, Gnome and KDE are DEs because they kind of include everything you need: a WM, pre-laid out menus, startup daemons and  settings, all of that good stuff. WMs do not, you must set everything up yourself-- startup daemons/programs, menus, etc.

You can use Gnome with nearly any WM as far as I can tell. That's what Compiz is, a WM, as is Metacity, fluxbox, openbox, dwm, awesome, wmii, xmonad, etc.

---

### Post by herbster on 2008-04-08
> **Therion said:**
> It IS confusing, isn't it?  abhiroopb is correct I believe, as well.  Too build on that, yes, you've got the Desktop Environment which controls how the user works with the operating system to a certain degree.  This is Gnome or KDE or Fluxbox or what have you.  Each have their own ideas about how best to do that and offer differing choices to the user.

Then you have the Windows Decorator, the Windows Manager and the Windows Compositor.  Metacity is a windows Manager.  It controls how certain aspects of your windows look (radio buttons and slider-bars for instance).  

The Windows decorator (usually GTK or Emerald in Ubuntu) determines how your window borders and min/max/close buttons look.

The Windows Compositor (Compiz in Ubuntu by default) determines how windows act in the operating system (like wobbling, minimize and maximize animations and such to name just a couple possibles).

That's MY understanding of the whole situation, but feel free to correct me as well!

Compiz is a Window Manager, it just happens to use OpenGL compositing to do its thing.

---

### Post by vinceUUUU on 2008-04-08
Hello Therion...i think

thaks for your reply....yes it IS a litte tricky to understand..

i don't want to get ahead of myself here AT ALL....this is after all...beginners talk

but you say..."correct me if i am wrong"

well i think you are wrong with one aspect in your post....you list Fluxbox as a desktop environment DE....but it is not.....it is a window manager...WM

once Fluxbox is made into something like Fluxbuntu.....a full distro of linux that is gnome derived....then it becomes of whole wrapped up DE

that is my understanding Therion

Thanks 

Vince.

---

### Post by kolisikepu on 2008-04-08
> **vinceUUUU said:**
> Hello Therion...i think

thaks for your reply....yes it IS a litte tricky to understand..

i don't want to get ahead of myself here AT ALL....this is after all...beginners talk

but you say..."correct me if i am wrong"

well i think you are wrong with one aspect in your post....you list Fluxbox as a desktop environment DE....but it is not.....it is a window manager...WM

once Fluxbox is made into something like Fluxbuntu.....a full distro of linux that is gnome derived....then it becomes of whole wrapped up DE

that is my understanding Therion

Vince,

Therion IS correct with what he is saying and you are as well... to an extent.

Fluxbox is a very light version of a Windows Environment.  Built to run on machines that don't have the guts to run a full exploded version of Gnome or KDE.

Fluxbox is used in another distro of Linux, in DamnSmallLinux because of the size of it's WE.  Running distro's such as Suse, Ubuntu, Mandrake, on some of these old machines will probably won't even load.
Making any sense?

---

### Post by herbster on 2008-04-08
> **kolisikepu said:**
> Fluxbox is a very light version of a Windows Environment.  Built to run on machines that don't have the guts to run a full exploded version of Gnome or KDE.

Actually, no. I use fluxbox on a Q6600 + 4gb. Like openbox and others, the key for many of us it its being lightweight and customizable.

Old machines can certainly run those distros, and also, DamnSmall replaced flux with JWM.

---

### Post by bodhi.zazen on 2008-04-08
Here is a nice review :

[http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)

and a nice review of some of the options for window managers :

[http://xwinman.org/](http://xwinman.org/)

Often something like fluxbox/openbox or icewm is referred to as "roll your own". The window manager takes care of the basic graphical environment (video, keyboard, mouse, windows, buttons, menus) and you then can use any application you like. 

You can use gnome apps on KDE or xfce or fluxbox , or KDE apps, up to you. Running both gnome and kde aplications adds some overhead (libraries).

People who run window managers (Fluxbox / openbox) tend to prefer to tweak the system if you will. Personally I prefer to install a minimal installation and add only those applications I need. I work at least 50% from the command line and prefer Fluxbox. A minimal installation preserve RAM and disk space for applications, half or 3/4 of the applications  installed with ubuntu-desktop I never use, so why install them ? Keeping installed applications to a minimum reduces the amount of updates and increases security.

If you would like to see what Fluxbox can do, try a distro like Wolvix or march

[http://marchlinux.wikidot.com/](http://marchlinux.wikidot.com/)

March is based on Arch Linux but is very very well done.

HTH.

---

### Post by Therion on 2008-04-08
> **herbster said:**
> Compiz is a Window Manager, it just happens to use OpenGL compositing to do its thing.
I stand corrected.  Compiz is a compositing XWindow Manager. Fluxbox, by itself is also an XWindow Manager.  Thank you for clarifying.  
This stuff still makes my head spin sometimes.

---

### Post by vinceUUUU on 2008-04-08
Hello,

yes.....it is still a bit of a grey area though

Gnome and Kde are like library's concerning desktop attributes right?....they exist between the BASE distro and the higher levels like the window manager WM...(they are environment/al  library's)

it makes sense....right?

would it be true to say then....that most BASE distros of linux are either kde or gnome based...or both?

but you can get certain desktop environments that don't talk to or support gnome or kde....they are wired directly to the BASE distro through custom code of their own...?

i am a bit dyslexic see...and pedantic....it is difficult for me to consider concepts until i can form a framework overview of facts.....for the entire Linux concept.

Vince.

---

### Post by arbulus on 2008-04-08
You asked if Gnome apps would still work in Fluxbox:
Yes, they will work just fine.  I use Gnome, but I also use the Openbox WM often and all of my applications work just as they do in Gnome.

---

### Post by Therion on 2008-04-08
> **vinceUUUU said:**
> Gnome and Kde are like library's concerning desktop attributes right?
To put it simply, if a user did NOT have either Gnome or KDE or some other DE installed, then that user would have to use the command line interface to communicate with the operating system.  The DE is the GUI that allows the user to operate the operating system... well... *graphically*.

> **vinceUUUU said:**
> would it be true to say then....that most BASE distros of linux are either kde or gnome based...or both?
I think it's safe to say the majority of linux distros use either KDE or Gnome as the default Desktop Environment, yes; but I can't say that with authority.  You have to choose to use one or the other, though, for any particular session - you can't use both at the same time.  You *can* switch between one or the other while using the same distro though, if both DE's are installed.  For instance I can choose to use KDE, Gnome or Enlightenment from the Session Manager when I boot Ultimate Edition.  I choose to use Gnome, but I have the *choice* of using any of three installed DE's:  KDE, Gnome or Enlightenment.

---

### Post by vinceUUUU on 2008-04-08
Hello Therion

thanks again for replying...

it is becoming clearer now....which is good news...

most WM's talk to and support gnome and KDE...and most WM's allow you to install and use gnome or kde styled Linux tools...

most base distros have gnome or kde or both at the ready ....they are ready to be exploited by whatever WM is used....

some windows managers are more advanced...and can be concidered as windows environments...gui user environments....not just managers...

i think this is right

the basic reason i asked all this was.........

since trying different window managers infront of ubuntu i noticed that some applications are not listed....but then they ARE listed when i boot into another WM's

why would that happen?......are those applications bespoke to the distro....like ubuntu...are can't port over to another WM?

thanks

Vince.

---

### Post by herbster on 2008-04-08
The menus are different, as I stated earlier. You must configure the menus in the WMs if running them alone.

---

### Post by Therion on 2008-04-08
Are you saying that if you boot into one desktop environment certain applications show up; but when you boot into a different desktop environment a different set of  applications is listed?

If that's the case I don't know...  I would have no idea why that would be happening.

---

### Post by vinceUUUU on 2008-04-08
hELLO Therion

that's exactly what i am saying yes...

i boot into say ubuntu....install a tool like cross over office....it works fine and is listed in the application menu

then i boot into ubuntu with say KVWM crystal  window manager......and cross over office is no longer listed....or say Swiftfox is not listed...


is it simply a case of configuring the menus of WM's to show gnome and kde styled tools?

like you say...and said?

thanks

Vince.

---

### Post by vinceUUUU on 2008-04-08
Hello,

yes.....sorry....it seams some applications show up in all WM's without any editing required....other applications don't show up in all WM's...

i put swiftfox into ubuntu...but it does not show up when i use the KWVMcrystal window manager into ubuntu...

however...i put XARA extreme application into ubuntu......and that shows up in both window managers...

why would that be?..

V. 

ps

(no manual configuring of any menus took place...in either instance)

---

### Post by herbster on 2008-04-08
Because different WMs behave differently.

You would be wise to read any of the documentation on these WMs, a lot of your confusion/misunderstanding is because you clearly have not, and all the answers are there, from the creators themselves.

---

### Post by vinceUUUU on 2008-04-08
Hello Therion

fair comment yes...true

i am always looking for a quik fix answer...to something that i don't want to be complex...

but it is often made more complex by my own lack of action in initially reading up....then i get frustrated and go and blag away on the forums...

i started reading about those WM's and edting menus....it starts to get more complex...it's not just a single command and click affair...

thanks for replying....

:-)

V.

---

### Post by herbster on 2008-04-08
BTW, I'm herbster :)

And it's not that complex, it just takes adjustment and familiarity. Complex is sending a piece of metal to the moon ;)

---

### Post by arbulus on 2008-04-08
> **vinceUUUU said:**
> Hello Therion

fair comment yes...true

i am always looking for a quik fix answer...to something that i don't want to be complex...

but it is often made more complex by my own lack of action in initially reading up....then i get frustrated and go and blag away on the forums...

i started reading about those WM's and edting menus....it starts to get more complex...it's not just a single command and click affair...

thanks for replying....

:-)

V.


Fluxbox and Openbox are very similar.  When you first login to a fresh Openbox install, there will be very little on your right-click menu.  The same is true I believe in Fluxbox.  You have to edit your menu's config file to add the applications you want to launch. They're still installed and supported, you just have to tell the WM how to launch them.  For example, if you want to add Firefox to your right-click menu, you have to add an entry for "Firefox" and tell it what the command is to launch it, which is "firefox".  

Running just a window manager definitely leads to configuring a lot more text files by hand.  You can get a very sleek and fast system, but you do sacrifice some of the ease of point-and-click configuration.  However, in Openbox there is an app called obmenu which gives you an easy GUI for configuring your menu.  I'm not sure about something similar in Fluxbox though.

---

### Post by herbster on 2008-04-08
Yep, there's fluxconf for flux.

---

### Post by vinceUUUU on 2008-04-08
Hello arbulus

thanks very much for your reply.

Openbox has crossed my path...

currently my system has a lovely WM called FVMWcrystal....it has a setting called "dock" .....which is like an apple mac desktop

also it already had a Debian menu in it.....a lot of my applications showed up right away...

it looks like a good WM

will try openbox and the gui menu editor you mentioned.

thanks very much

hopefully my penyitum 3 machine will end up performing well with Linux...

thanks

Vince.

---

### Post by urukrama on 2008-04-08
As herbster pointed out, a lot of the window managers work differently, and that is why the documentation is essential.

Some window managers require you to set up the menus. You can do that manually (by editing the right text files) or with an application like [Menumaker]("http://menumaker.sourceforge.net/"). For Fluxbox, have a look [here]("http://ubuntuforums.org/showthread.php?t=371144"). For Openbox you can use a handy application called [Obmenu]("http://obmenu.sourceforge.net/download.html").

Docks etc, as provided by FVWM-Crystal, can be added to other window managers as well. See [wbar]("http://freshmeat.net/projects/wbar/"), for example. The philosophy behind several of the light window managers is that they just manage the windows, and allow you to add other applications for the rest (panels, docks, system trays, desktop backgrounds, desktop icons, etc.). In this way you can build a working environment that fully suits your needs or wants.

If you need help configuring Openbox, have a look [here]("http://urukrama.wordpress.com/openbox-guide/").

---

