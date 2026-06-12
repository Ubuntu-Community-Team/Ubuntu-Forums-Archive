---
title: "The Simple On-screen Keyboard (SOK)"
date: 2006-06-09
forum: Assistive Technology &amp; Accessibility
---

### Post by Henrik on 2006-06-09
I'm just starting a thread for discussion about the simple on-screen keyboard currently under development. I wrote a review of the Gnome On-screen Keyboard (GOK) some time ago, pointing out some of it's usability flaws.

In an attempt to address these we have started a a python-based version that has a primary goal of being simple and functional first, and then add features as plug-ins later as needed. 

I'd be interested to hear from those who have used on-screen keyboards, which features are important and your experience of existing systems. The main contributor to the project at the moment is Chris Jones, under the Google Summer of Code scheme. Please help him with encouragement, feedback and patches ;)

Our current working plan can be seen here: [https://wiki.ubuntu.com/Accessibility/Specs/SOK](https://wiki.ubuntu.com/Accessibility/Specs/SOK)

---

### Post by t0rtois3 on 2006-06-09
Frafu wrote:
> The systemwide scope of the modifier-keys of KeyStrokes is generally
> true: for example if I click the shift-modifier on KeyStrokes and
> someone presses a letter on the physical keyboard, the letter written
> will be a caps-letter.

Thanks frafu, it's quite useful to hear the sort of things people find useful from current onscreen keyboards. So if anyone else has comments like this they will be well received.

In response: I think this is a good idea, it would make sense from an implementation standpoint as well.  All X keyboard emulation libraries I've looked at don't seem to work like this.  Instead they send a shift flag, with the character keycode.  It should be possible to just emulate the pressing of the shift key.  So it would have the same behaviour as KeyStrokes. 

 I shall look into it.

Chris Jones

---

### Post by t0rtois3 on 2006-06-09
Well, I looked into it, and it works.

---

### Post by frafu on 2006-06-10
[QUOTE=t0rtois3]Francesco Fumanti wrote:
> The systemwide scope of the modifier-keys of KeyStrokes is generally
> true: for example if I click the shift-modifier on KeyStrokes and
> someone presses a letter on the physical keyboard, the letter written
> will be a caps-letter.

Thanks frafu, it's quite useful to hear the sort of things people find useful from current onscreen keyboards. So if anyone else has comments like this they will be well received.

In response: I think this is a good idea, it would make sense from an implementation standpoint as well.  All X keyboard emulation libraries I've looked at don't seem to work like this.  Instead they send a shift flag, with the character keycode.  It should be possible to just emulate the pressing of the shift key.  So it would have the same behaviour as KeyStrokes. 

 I shall look into it.
[/QUOTE]

Hello t0rtois3,

Sorry for being at the origin of a misunderstanding: the example of the keypress on the onscreen keyboard interacting with a keypress on the physical keyboard was only to illustrate what I meant with the expression "systemwide scope". It is not an example of something I do; it is an invented example. 

Moreover, while talking about "systemwide scope", I assumed that the onscreen keyboard needed to act systemwidely to be able to do anything that a user can do with a physical keyboard. 

The real idea behind it was, that the onscreen keyboard should emulate the physical keyboard as much as possible in order to work in every situation and not only with applications of a certain kind. Maybe that the best way to achieve it, is by making the operating system not see any difference between a keypress-event coming from the onscreen keyboard and a keypress-event coming from a physical keyboard. 

But as I don't know how Ubuntu works internaly, I cannot tell whether that idea is correct, nor whether it is possible to implement it. 

frafu

---

### Post by Henrik on 2006-06-10
frafu,

Slightly off-topic, but have you ever tried dasher? You might find it quite an efficient mode of text entry. 

See: [http://www.inference.phy.cam.ac.uk/dasher/](http://www.inference.phy.cam.ac.uk/dasher/)

---

### Post by frafu on 2006-06-10
[QUOTE=Henrik]frafu,

Slightly off-topic, but have you ever tried dasher? You might find it quite an efficient mode of text entry. 

See: [http://www.inference.phy.cam.ac.uk/dasher/](http://www.inference.phy.cam.ac.uk/dasher/)
[/QUOTE]

I have read about it, but did not have the opportunity to test it yet (unfortunately there is no MacOSX version). I hope that I will be able to try it in a few weeks... 

I am wondering how it compares to an onscreen keyboard. 

frafu

---

### Post by Henrik on 2006-06-11
You should be able to try it on an Ubuntu Live CD if you have a decent internet connection and enough RAM (265 MB at least, ideally 512). Then you can just install dasher into the live running system using Add Applications or Synaptic.

---

### Post by frafu on 2006-06-11
@Henrik, 

Thanks for telling me about the possibility of installing software in a LiveCD session. That's good to know as I have adsl and 512MB of RAM on my G4.

cu

frafu

---

### Post by frafu on 2006-06-12
Unfortunately, the LiveCD does not boot on my older mac. It is probably the bug already filed that makes Dapper hang on boot on different g4 machines. Otherwise its my ide-pci card. If it is the bug, a daily build will probably solve the issue as a fix seems to be around. Otherwise I will probably have the opportunity to test it on a pc in some weeks. 

Anyhow, after reading your explanation [in this thread]("http://ubuntuforums.org/showthread.php?t=193749") that the written text goes in a field in Dasher, I wonder whether it is not somewhat limiting!? 

I hope that sok will enable a user, that uses exclusively the pointer to interact with his computer, to control it completely; this way (at least in my opinion), it will really be useful...

---

### Post by Henrik on 2006-06-14
I've updated the spec after talking with chris today. After he's made his changes we will submit it for formal approval. I would prefer that others please don't make major changes to the spec at this point.

I've also seen Chris' working pre-alpha version today, and it looks very promising :) I'm sure we'll have something available for wider testing in a few weeks.

---

### Post by frafu on 2006-06-14
Hello, 

I have looked at the new specs of sok and it seems to be good from my standpoint as an m2 user, except for 2 points (This time I will be more explicit in order to avoid misunderstandings like above with the interaction between onscreen and physical keyboard):


1) The first point about iconizing the onscreen keyboard comes from my reallife experience: 

I really miss the option to iconize the onscreen keyboard. The onscreen keyboard that I am using now can be resized to any size that the user wants. But it also has a key that reduces the keyboard to the size of an icon. That icon also floates and is resizable. When I click on that icon, the onscreen keyboard reappears with the size that it had before iconzing it. 

In fact, I keep my onscreen keyboard nearly all the time in its iconized state because I want it to cover the desktop the least possible. When I have to type something, I click on the icon; the onscreen keyboard appears and I type what I want to type with the onscreen keyboard; as soon as I am finished with typing, I put the onscreen keyboard back to its iconized state. 

Further, I want to explain why the fact of being able to resize the onscreen keyboard cannot totally replace the fact of being able to iconize it: I am using the onscreen keyboard with a determined size which I am accustomed to. By clicking on the icon, I get the onscreen keyboard back at exactly that size. It would be a pain if I had to resize it every time by dragging the resizing corner of the onscreen keyboard window to that determined size. 

Of course, if Ubuntu (that I don't really know yet) already has the ability to make an application disappear by a single click and reappear by another click somewhere on the desktop, the iconizing feature will be useless. Otherwise, I hope that you will be able to add it already to the first release of sok. 

(To be complete, when the onscreen keyboard that I use is in its "iconized" state, I think it is not really an icon, but it still is a small window as there is a small empty titlebar on top of the icon.) 

2)  The second point is about the scanning feature and it does not come from my reallife experience, but something I thought about, while reading the new specs: 

A user that relies on scanning will not be able to click on the button to activate scanning. Or do I miss anything? Maybe that you already considered this, and the specs are not explicit enough!? 


frafu



PS: Could you please tell me what you mean with the 3rd point in the design section about the ability to easily configure the layout and the localisation? Do you mean that the user can choose where he wants to place the keys on the main and secondary window? Or do you mean that the user can also choose what keys he wants on the main and secondary window? 

Can I for example imagine the layout configuration window this way: there are
- the 2 empty keyboard windows
- different shape-templates for keys
- all the letters and functions provided by the onscreen keyboard 
The user can associate a letter or a function to a shape and choose where to put shape on the keyboard?

---

### Post by Henrik on 2006-06-14
1. **Resizing:** At the moment we haven't actually included a button for resizing/minimizing, but you easily could (see point 3). At the moment we only use the window decoration button to minimize. This brings the keyboard down to a minimised state at the taskbar, as any other window. Clicking on that taskbar entry will bring the window back to its original size and location (ie. it remembers the changes you made to it). We will also have the option of having a taskbar applet instead of the normal taskbar entry. I think the floating icon idea is a Mac-ish thing, which I guess doesn't have a taskbar. I don't think we need that, but if we do, it should be fairly easy to make.

2. **Scanning:** You are right that a user who needs scanning won't be able to click that button with a normal mouse. You could say that that is a proof-of concept implementations, which allos us to implement all the other aspects of scanning, such as how the scan pattern goes through the keys, setting speed, etc. We would then want to provide several ways in which that input signal could be provided. The mouse button is a fair place to start because some people will make a swith using parts from a mouse. Others will use a spacebar, while others again will use special switching equipment connected to the serial or USB port.

3. **Key placement:** I think you will find that the layout system for this keyboard will be more flexible than anything you have seen so far :)  We talk of two keyboards, but that's just the default layout we will implement first. Others can implement other variants, with 3-4 keyboards including macros and scripts or all the keys on a single keyboard. The keyboard layouts are generated in any drawing program that supports SVG such as [http://www.inkscape.org/](http://www.inkscape.org/) The keys can be any shape (well, just rectangles for now) or size and have any position. A keypad can have 3 or 100 keys and be in any language.

So if you want to contribute to the development at this point, the best thing to do might be to learn how to use inkscape and draw some useful keyboard layouts. There even seems to be a Mac OS X version available :)

---

### Post by frafu on 2006-06-15
Hello Henrik, 

First of all, thanks for your reply. 

1. **Resizing:** You guessed it right: Macs don't have a taskbar. The solution of minimizing to the taskbar is probably good in most cases. However, there is at least one case where another solution has to be considered: Applications that hide the taskbar: For example a movieplayer running at fullscreen. Could you please tell me how you planned for a m2-user to make the onscreen keyboard reappear when no taskbar is available? 

By the way, what is a taskbar applet? 

2. **Scanning:** I thought that the specs would refer to the final application. After reading your explanation, I assume the specs will evolve with the different milestones you defined in the accessibility-list. 


3. **Key placement:** So, I assume that the onscreen keyboard will parse the svg-file and "learn" the layout. Keys with letters will be no problem; but keys like modifiers, return-key, pageup-key,... will probably have to be coded in a determined way!? I don't expect an answer to this question now, because I suppose that a precise answer will only be possible after the implementation. 

There is indeed a MacOSX-version of inkscape available; thanks for pointing me to it. 


frafu

---

### Post by t0rtois3 on 2006-06-17
1. Resizing: That's a fair point.  Though all applications I have tried let you exit fullscreen with the mouse.  An example of a panel applet would be the clock on the bar at the top of your screen, and the workspace switcher.  Ubuntu ships with a whole host of these, you can add more by right clicking on the panels at the top and bottom of your screen.  

A panel applet would unfortunately also suffer the problem you mention.

3. Key placement: Inkscape assigns every object, be it a box or a drawing made with lines and curves a unique identifier.  This can be seen by right clicking on an object and selecting object properties.  I then have a seperate file which describes the actions of each key in turn.

Chris

---

### Post by frafu on 2006-06-17
[QUOTE=t0rtois3]1. Resizing: That's a fair point.  Though all applications I have tried let you exit fullscreen with the mouse. [/QUOTE]

Though I am not interested in games, I wonder whether you considered them? 

By the way, thanks for the explanation. 

frafu

---

### Post by frafu on 2006-07-24
Hello,

In the thread titled "GOK alternative" of this "Accessibility Talk"  Forum I read about another onscreen keyboard called xvkbd. I went to the homepage of xvkbd and learned about a feature called "Quick-modifiers" that seems quite interesting: if I understood it correctly, when the button-up of a key-click does not occur on the clicked key (in other words the pointer is moved away from the key before releasing the mousebutton) it performs the same action as a "modifierclick+keyclick". 

Maybe it could be a good idea to also implement a similar feature in sok. 

Have a nice day. 

frafu

---

### Post by Henrik on 2006-07-25
Interesting. And by modifier you typically mean Shift I guess.

I was thinking of a similar function for those who have two mouse buttons available (left and right). A right click on a button would be the same as a Shift+click.

Alternatively one of these input techniques could give you a space after the letter, thus forming a word (saving you one click per word).

---

### Post by frafu on 2006-07-25
> **Henrik said:**
> Interesting. And by modifier you typically mean Shift I guess.

I was thinking of a similar function for those who have two mouse buttons available (left and right). A right click on a button would be the same as a Shift+click.

Alternatively one of these input techniques could give you a space after the letter, thus forming a word (saving you one click per word).

In fact, I thought at first to leave the user the choice of what modifier it should replace: user customizable in the settings. 

Now I wonder, why not expand the idea: for example moveup before releasing = shift, movedown=alt, moveleft=ctrl, moveright=space.
:)  

However I think it should be fully customizable in the settings; maybe a gui like this: 
A main checkbox to activate/deactivate the "quickmodifiers"; below a secondary checkbox to differentiate between "any move has the same action" and "each move has a different action"; finally in the third level 4 checkboxes (moveup, movedown, moveleft, moveright) that are only active when "each move has a different action" is active; and next to each of the 4 checkboxes a popup to set the wanted action. (If more actions are available: up+left, up+rught, right+up, right+down, down+left,...) 

Maybe an alternative could be an empty list with an add, edit and remove button; by clicking on the add-button, the user gets a dialogue where he can define a new mousegesture by using 2 popups: the first popup containing a list of mousegestures and the second popup with the available actions...  


Finally, I wonder now whether the ubuntu desktop offers the mousegestures more generally to replace different right-button-clicks as an accessibility option. It would probably be appreciated when the desktop would provide at least a mousegesture for the right click to get to the contextual menu: in fact, the main reason why I use Firefox instead of the browser shipped with my OS is because a "click and hold" in Firefox (I am talking about MacOSX; I don't know for other OSes) makes the contextual menu appear; the other browsers instead require a right click. Are general mousegestures already available under ubuntu? 


frafu

---

### Post by Henrik on 2006-07-25
> **frafu said:**
> Now I wonder, why not expand the idea: for example moveup before releasing = shift, movedown=alt, moveleft=ctrl, moveright=space.
:)  

OK, this is getting a bit complex now :)

I'm not sure having this range of options is actually more efficient. First of all you use Ctrl and Alt quite rarely compared with the typing letters. Shift gets used 3-4 perhaps in each sentene (first word and some names). Space gets used once for every word though. 

Second, click-and-hold + move-up is a fairly complex opperation that will take extra consentration and slow down the process. If the next letter you wanted in a different direction you then have to stop and change direction to get to it. 

Of course points 1 and 2 do cancel each other out to some extent :) Since you normally don't use the Ctrl and Alt keys during normal typing it is less jarring to configure them to drag like this.

I guess only real-life trials will decide if it works. 

> Finally, I wonder now whether the ubuntu desktop offers the mousegestures more generally to replace different right-button-clicks as an accessibility option. It would probably be appreciated when the desktop would provide at least a mousegesture for the right click to get to the contextual menu: in fact, the main reason why I use Firefox instead of the browser shipped with my OS is because a "click and hold" in Firefox (I am talking about MacOSX; I don't know for other OSes) makes the contextual menu appear; the other browsers instead require a right click. Are general mousegestures already available under ubuntu? 

I don't think so. This would be a good feature to have as part of the underlying X framework. There is some support in individual applications AFAIK, such as GDM and Firefox via extensions. 

What we could do quite easily (I think) is to add an (optional) button to SOK that was a sticky mouse button reverser. If you click on it once it changes the active mouse button until you click the mouse somewhere else. Clicking it twice makes the change stick.

---

### Post by frafu on 2006-07-25
> **Henrik said:**
> OK, this is getting a bit complex now :)

I'm not sure having this range of options is actually more efficient. First of all you use Ctrl and Alt quite rarely compared with the typing letters. Shift gets used 3-4 perhaps in each sentene (first word and some names). Space gets used once for every word though. 

I guess only real-life trials will decide if it works. 

 

You are probably making a good point when saying that the shift-modifier is more often used than the alt- and ctrl-modifier. So only using a general action for the shift could be really more efficient than some complex gestures requiring concentration. 

Further, I want to point out, that your suggestion about the space is only useful as long as the deferred feature "word prediction and completion" is not implemented. Afterwards, won't an automatic space be an option of the word prediction? 

By the way: the Keyboard.py source file contains this line: 
```
 
modifiers = {"shift":1,"caps":2, "control":4, "mod1":8, "mod2":16, "mod3":32, "mod4":64, "mod5":128}

``` 
Why isn't the alt-modifier explicitely named? 


>  
*Click and hold to make the contextual menu appear* would be a good feature to have as part of the underlying X framework.
 

Does this mean that it would still be possible to implement it, so that it would work with all the applications that already exist? (I mean adding it to the X framework without having to change caracteristques that already exist in order to avoid braking existing applications.)


> 
What we could do quite easily (I think) is to add an (optional) button to SOK that was a sticky mouse button reverser. If you click on it once it changes the active mouse button until you click the mouse somewhere else. Clicking it twice makes the change stick.

Click and hold to make the contextual menu appear in every application would be very nice for people only using one mousebutton. But as it is not the case, your idea about making the mousebutton reverser (I suppose you are talking about the feature of switching the left and right mousebutton of the specs) only stick when you doubleclic it is probably a good way to go. 

(In fact, as far as I know, a similar behaviour is also planned for the modifiers.) 


frafu

---

### Post by anasofiapaixao on 2006-08-13
**EDIT:** Never mind me. I wasn't saving the canvas size in pixel units... ](*,) 


I am not sure if this is known or not, but when changes to an svg are saved in InkScape, the modified canvas size is stored like this:
```
   width="590pt"
   height="230pt"
```

Which is responsible for this output:
```
Traceback (most recent call last):
  File "./sok.py", line 203, in ?
    s = Sok()
  File "./sok.py", line 41, in __init__
    self.load_layout(filename,folder)
  File "./sok.py", line 87, in load_layout
    viewPortSizeX = float(svgdoc.attributes['width'].value)
ValueError: invalid literal for float(): 590pt
```

Which happens because "590pt" is not a number...

Removing the "pt" from the canvas size in the svg file solves the question, but perhaps it would be a good ideia to add a string check that would make sure it is composed of numeric characters only; and if it isn't, ignore the numeric chars.

---

### Post by Henrik on 2006-08-15
> **anasofiapaixao said:**
> **EDIT:** Never mind me. I wasn't saving the canvas size in pixel units... ](*,) 

It's probably still a good idea to have the string heck though so it can fail more gracefully.

... so are you making some cool new layouts? Can we see? :)

---

### Post by anasofiapaixao on 2006-08-19
I just made some small changes to adapt the layout to my tablet usage. ;)  [I have made a thread]("http://www.ubuntuforums.org/showthread.php?t=236405") with a screenshot, my changes and the file, for people who want to use SOK for everyday use right away.

I've only tweaked the main pane, the other two are in the old Ubuntu layout are look a little weird :-? I'll get on that...

Probably this layout may not be good for U.S users, as it is based on the portuguese layout (I explain it in the thread).

TODO's I found: Add the key next to the zero number key - In my layout it contains the apostrophe and the question mark, and I've missed them quite some times already - and add the right shift. So, so many times I go to the non-existent right shift in order to type an uppercase L, or P,... even though I don't touch right shift on the physical keyboard, with the stylus it is different. Only problem with the latter is WHERE - there is literally no free space! :p 

Also, is there a way to change from the default black key borders and numbers? I looked at the code to change to a dark orange/brown and couldn't find it...

*(Mind you I know almost nothing about programming; only C basics.)*

Hope someone finds this useful!

---

### Post by puccaso on 2006-09-10
what about implementing some sort of autocomplete feature?
i mean, bash accepts it.. and not only for file names, but if u type tar - it will auto complete x v f  etc.... and if u chooce xjpv with tar - then it will only give u .bz2 filenames.. i mean the oppertunies are endless

currently
how do u make shortcuts/macro's for certain terms like sudo apt-get
like, i want sudo apt-get as one button
i want wget -c as one button, how do we do this?

---

### Post by frafu on 2006-09-10
Hello, 

As far as I know, Word prediction/completion is planned for the second stage: see "deferred features" on [this]("https://wiki.ubuntu.com/Accessibility/Specs/SOK") page. 

Unfortunately, I am not able to help you with the macros. 

frafu

---

### Post by frafu on 2006-09-16
Hello, 

I have finally got (with much delay) a CeleronBox with Ubuntu (Dapper Desktop i386) and wanted to try onboard. Unfortunately, I am not able to install the python2.4-virtkey-041.deb package. 

Indeed, it tells me that the dependency libc6 is not satisfiable. It keeps telling me the same even after the installation and reinstallation of libc6 with the Synaptic Package Manager. 
Then, I also installed libc6-dev and libc6-dbg; but it did not help either. 

Does anybody have an idea? 

frafu

---

### Post by puccaso on 2006-09-17
thats probably because, its only avaliable on edgy.
i wouldnt reccomend the download/upgrade if you dont have alot of patience.

the worst thing for me on edgy, is the rhythmbox issue (you cant add music from folders/ smb mounts)

but you can play through daap so i am ok.

edgy is faster, and snappier then dapper.
u just got ur system - 
christen it with some edgy water.

(im not a christian, but we dont have an equivelant) haha.

enjoy.

---

### Post by frafu on 2006-09-17
Is there a way to upgrade to edgy without losing my configuration of nfs, ssh, nx, wol, vnc? 

By the way, why the restriction to edgy? 

Thanks in advance. 

frafu

---

### Post by puccaso on 2006-09-17
well i mean nfs ssh and vnc would be no problems. just make a copy of all files in /etc or in ~/. and ur set.. as for nx - it is having some issues with edgy at the moment... although i use xtight and a persistant gdm/xdcmp - which is much faster then vino

why the restriction, well im sure it will be backported once edgy is out
edgy wont be out until octobr, so u have 2/3 weeks minimum until its backported..

---

### Post by frafu on 2006-09-17
Hello pucasso,

Thanks for your reply, and particularly for telling me about the problems of nx in edgy. In fact, being a newbie in linux, I opted for nx because they offer both an nx server for Ubuntu and a client for macosx out of the box. 

I don't know yet what I am going to do... 

frafu

---

### Post by puccaso on 2006-09-17
if you are using nx commercial - ie nx machine - then there might be hope...  because they could suppose you *maybe* just dont tel them u use edgy. lol - let them figure it out.

otherwise, freenx definatly is not stable... 

however, from what i remember hearing - nomachine has become 2xterminalserver or something like that? and they are going gpl in a year or so, so by that time - it will definatly work.
what you might try tho - the original file you said wouldnt install - you might want to try and compile it against ur own glibc.. 

newbie hu? i remeber those days - tho i would reccomend gentoo to u for a year or so - just so u understand the ins and outs, ubuntu will get u too comfortable too quick with a gui - ... plus in gentoo...
if u wanted to install sok - it would automatically upgrade anytthing needed for sok to work - tho i dont know is sok is a ubuntu thing - or a gnome thing.... do some research - :) enjoy

---

### Post by ashrack on 2006-09-25
> **puccaso said:**
> thats probably because, its only avaliable on edgy.
i wouldnt reccomend the download/upgrade if you dont have alot of patience.

the worst thing for me on edgy, is the rhythmbox issue (you cant add music from folders/ smb mounts)

but you can play through daap so i am ok.

edgy is faster, and snappier then dapper.
u just got ur system - 
christen it with some edgy water.

(im not a christian, but we dont have an equivelant) haha.

enjoy.
So SOK wont work on DAPPER?

---

### Post by puccaso on 2006-09-25
well, from what ive heard its for edgy,
it compiles against some new python stuff i think
that isnt avaliable in dapper.
but the only way you might be able to install it
is to compile from source

---

### Post by t0rtois3 on 2006-09-25
> **ashrack said:**
> So SOK wont work on DAPPER?

It does though it's not in the repo's.  Grab debs here [https://wiki.ubuntu.com/Accessibility/Projects/onBoard/dev](https://wiki.ubuntu.com/Accessibility/Projects/onBoard/dev)

The keys are further apart for odd reasons and the system tray icon doesn't work on dapper.  Other than that it works fine.

---

### Post by frafu on 2006-09-25
Yesterday I downloaded the new version (onboard_0.85_all.deb virtkey_0.41_i386.deb) from [here]("https://wiki.ubuntu.com/Accessibility/Projects/onBoard/dev") and they installed without error. 

Then I double clicked on the installed onboard file; I got the popup where I chose "run in terminal" and the keyboard appeared on the screen. 

I used it successfully with firefox; though it sometimes repeated a few characters. Did I type to quickly and the onscreen keyboard was not fast enough? Were my at-spi badly configured? I did not have the time to test it seriously. 

However the bottom line is that it now seems to work on dapper too. 

frafu

---

### Post by ashrack on 2006-09-26
At school we have 5computers using DAPPER and the current crappy GOK!
So now Im wondering should I upgrade them to EDGY when its out?
There are a lot of disabled students in our school which need OnScreenKeybord and also the Magnifier...

Which accesibility options are better in Edgy than in Dapper?

---

### Post by Henrik on 2006-09-26
The beta of Edgy will be out this week, and after that it should not change too much. You could even try upgrading now and then run an update again when it's out. 

In Edgy GOK will be replaced by onBoard and Gnopernicus replaced by Orca. The magnifier component will not change much though.

---

### Post by frafu on 2006-09-27
I am not able to type with onboard in the modal dialogbox asking for the admin password (for example when opening the Update Manager). 

Is this normal? 
(onboard on Dapper) 

frafu

---

### Post by t0rtois3 on 2006-10-02
> **frafu said:**
> 
I used it successfully with firefox; though it sometimes repeated a few characters. Did I type to quickly and the onscreen keyboard was not fast enough? Were my at-spi badly configured? I did not have the time to test it seriously. 
frafu

Does the repeating happen in other application or just firefox?  Does it occur all the time or only when for example you type in the address bar?

---

### Post by frafu on 2006-10-03
@t0rtois3

It does it also in gedit, in the modal dialogue box asking for the admin password, in the find box of the synaptic package manager,... 

I have found something interesting: when I type for example the letter 'a' and I leave the onboard window with the mouse, it repeats the letter 'a'; then I place the mouse on the onboard window again and leave the window without typing anything another time, then the letter 'a' is repeated again: and so on every time the mouse enters and leaves the onboard window. 

Maybe I should point out that I am using onboard on dapper and that I forward the ubuntusession using vnc to a macosx. (onboard does not start on a session  forwarded with nx) 

frafu

---

### Post by Henrik on 2006-10-04
vnc does stange things with the keyboard, esp. sticky keys. I suspect vnc is causing a lag and that is causing the repeat.

---

### Post by frafu on 2006-10-15
I have just upgraded my system to edgy and the repeating of the of the letters that I wrote about in a previous message does not happen anymore. (I am still using vnc and tested it shortly with firefox, gedit, synaptic update manager). 

However onboard still does not start on the desktop forwarded with nx. 

frafu

---

### Post by larsw on 2007-01-27
Hi all,

I have a problem with installing additional layouts in onboard 0.85 on ubuntu 6.10. 

I want to use either the ubuntu or tablet layouts as starting point for an even further reduced layout (I only need letters, del, backspace, space, enter to use for a touchscreen jukebox thingy on my old Stylistic3400).

I have downloaded the "onboard-tablet" layout from anna, and also the "sok-ubuntu" replacement layout (sok-ubuntu-0.1.tar.gz).

Both are copied to /usr/share/onboard/layouts.

Anna's tablet layout is now (after modifying her script a bit to match the ubuntu locations) loaded as standard in GDM login (I have it loaded for the login screen), and also when root starts onboard from a shell. 

However, when I run onboard-settings as normal user or root from a console, neither the ubuntu nor the tablet layouts are listed. 

I then click "add" and browse for the layouts. Selecting any of them and then clicking "open" brings me back to the configuration dialog, which still only lists "Default" and "Scan". At the same time, in the console from which I started the onboard-settings dialogue, I get the messages
```

key 'id' required in /usr/share/onboard/layouts/ubuntu.sok
key 'id' required in /usr/share/onboard/layouts/tablet.sok
key 'id' required in /home/moi/.sok/layouts//ubuntu.sok
key 'id' required in /home/moi/.sok/layouts//tablet.sok

```

The odd things here are: 
1) both files (ubuntu.sok and tablet.sok) are unchanged from the originals downloaded. So what 'id' entry are they missing? Any way to get a hint at the line in the layouts that cause the error?
2) I did not copy any of them to my (=moi) home dir. Guess onboard copies them there automatically?
3) Why are there two slashes in the path for the files in my home dir (layouts//ubuntu.sok i.s.o layouts/ubuntu.sok)
 
Hints appreaciated. 

Regards
Lars

PS and O.T.: Does anyone know a decent mp3/music player frontend that is optimized for a touchscreen? Basically, I want a good library search screen with artist/title/album/genre info, plus a full text search box, and then the alphabet keys next to that box (i.e. minimum keyboard integrated with the application). Then the option to add entire albums, genres, artists or single tracks to the playlist. The playlist itself should be on a separate tab or window, so that it does not eat screen space while selecting from the library. Any ideas?

---

### Post by frafu on 2007-01-27
Hello,

These are not direct replies to your questions, but I hope it will nevertheless be helpful, so that you will be able to create your personal loyout:
Do you know these three webpages: 

[https://wiki.ubuntu.com/Accessibility/Projects/onBoard?action=show&redirect=Accessibility%2FProjects%2FSOK](https://wiki.ubuntu.com/Accessibility/Projects/onBoard?action=show&redirect=Accessibility%2FProjects%2FSOK)

[https://wiki.ubuntu.com/Accessibility/Projects/onBoard/layouts](https://wiki.ubuntu.com/Accessibility/Projects/onBoard/layouts)

[https://wiki.ubuntu.com/Accessibility/Projects/onBoard/definitions](https://wiki.ubuntu.com/Accessibility/Projects/onBoard/definitions)

Here a few hints that might help: 

- open onboard (formerly called sok) 

- open the settings window from within onboard (click on the right bottom colored field) 

- use the 'Open layout folder' in the Settings window to open that folder

- hit the 'Personalize current layout' button in the settings window: you will be propted to give the new layout that is copied from the current layout a name. After providing a name, you will see the new layout files appear in the layout folder. I would suggest to copy the default layout. 

Then go on with editing the new layout files. 

Have a nice day. 

frafu

PS: Don't hesitate to write again if you continue to have problems; I will see what I can do. (I created a personalized layout some time ago with more buttons; at the moment I don't remember the details about how I did it, but if you continue having problems, I will try to look them up.)

---

### Post by t0rtois3 on 2007-02-04
I think the problem might be that you overwrote some of the .svg files in the /usr/share/onboard/layouts directory.  Try changing the file names of the ones you download so they don't conflict with the shipping ones.  You will have to change the .sok files to point to the right .svg files.

---

### Post by igolg on 2007-02-26
@igolg

I deleted your message because it was an advertisement that had nothing to do with accessibility. 

Please, don't misuse the forums. 

frafu

---

### Post by osarusan on 2007-07-07
I'm using onboard with a tablet PC, and I enabled it to start automatically on login. However, I'd like it to start minimized, rather than start already open. How could I change it to start minimized in the notification area?

---

### Post by frafu on 2007-07-07
@osarusan

I think that it is not possible to make it start in minimised form. Consequently, I filed a "request for enhancement" bug against onboard to ask for the option. 

Francesco

---

### Post by osarusan on 2007-07-07
Thank you for filing that. I hope it can be done.

---

### Post by t0rtois3 on 2007-07-07
This would be a trivial feature to add, I don't know how much demand there is for it though.  I don't want to clutter the settings dialog too much.

It probably would be worth making onboard start in the same state that it closed in perhaps.

If you want to get onboard to start in a minimized state on your own system insert the following code  in /usr/share/onboard/sok.py on around line 99:            

self.window.iconify()

edit the file with a command like `gksudo gedit /usr/share/onboard/sok.py` and make sure you get the indentation right, so the command is in line with that above and below it.

---

### Post by TheGuv on 2007-07-09
Hey, onboard is behaving rather well, and certainly easier to use than xvkbd as you don't have to lock the focus. There is one thing, I'd like to use onboard to login to GDM with. I can get it to launch at the right time, but the default size is rather large and it appears on top of the login text entry box so you can't see what's going on.

I realise that for a normal user you can edit ~/.conf/apps/sok/%gconf.xml and modify the sizes, but running with GDM it's not running as a user yet.

Anybody know how I can alter the default size under GDM? Also, is it possible to modify its default start position rather than bang in the centre?

Nice work guys.

'guv.

---

### Post by frafu on 2007-07-10
Hello TheGuv, 

Please, have a look at [this post]("http://ubuntuforums.org/showpost.php?p=2957545&postcount=10"); it might help. 

Francesco

---

### Post by frafu on 2007-07-10
> **t0rtois3 said:**
> This would be a trivial feature to add, I don't know how much demand there is for it though.  I don't want to clutter the settings dialog too much.

It probably would be worth making onboard start in the same state that it closed in perhaps.


If you are going to make it start in the same state that it closed, I wonder what happens to the users that have set it to appear at the login screen!? 

Will they see onboard at the login screen if they closed their session with onboard in the hidden state? 

Francesco

---

### Post by TheGuv on 2007-07-10
Hey Francesco,

> **frafu said:**
> 

t might help. 

Francesco

Thanks very much, indeed it did help, I now have a keyboard of a size I want. All I need to find out now is how to change where abouts it appears on screen - it's small now but still appears on top of the login box.

'guv

---

### Post by v.cecchetto on 2007-07-11
> **TheGuv said:**
> Hey Francesco,



Thanks very much, indeed it did help, I now have a keyboard of a size I want. All I need to find out now is how to change where abouts it appears on screen - it's small now but still appears on top of the login box.

'guv

sudo gedit /usr/share/onboard/KbdWindow.py

modify the lines 68,69
........................................................................
	      	x = 0
	        y = 0
........................................................................

in 
........................................................................
                x = 100
	        y = 200
........................................................................

try other numbers till you get the result you need.

Readin the code in KbdWindow.py can be useful to understand how it works but needs a little experience in python, not the most difficult language to learn.

 (This time instead of reading the code in deep, i only played with different values to get the result i was looking for :lolflag:)

---

### Post by rshortt on 2007-08-29
Hi everyone,

First of all, is this the official place to discuss onboard developments?

In any case, I am using onboard in a pygtk application.  This is a fullscreen app and I had issues getting the onboard keyboard to display above my app's window.  Even though the onboard window is told to stay above other windows this does not work with full screen applications.  My solution was to remove the call to gtk.main() and self.clean() in the OnboardGtk class in OnboardGtk.py.  In my app I instantiate the object and tell it's window to be a transient window (subwindow) of my app's main window.  Problem solved.

Ok, now my current issue.  I am getting double keystrokes!  Has anyone ever seen this issue or have an idea of where I could solve it?

FYI I am using kubuntu feisty and onboard from the BZR repository.  My target platform will eventually be a Fedora system but I have no problem with building the supporting software.

Thanks for your help,
-Rob

---

### Post by rshortt on 2007-08-29
Ok, this is strange, the only change I just made was to change the position and size of the keyboard and I no longer have repeating keys!  Oh well... I will post again if it comes back.

-Rob

---

### Post by jsmth on 2007-09-21
This is a promising application! I'm testing Kubuntu in a VM under Win XP to assess the accessibility situation. I use a virtual keyboard that I created myself under Windows which I am dependent on, but it seems like I can duplicate the functionality with a custom onBoard layout.
I've installed onBoard in Kubuntu (feisty) but it complains that glade is missing when I try to run onboard-settings - I assume that Kubuntu has a different default package list to Ubuntu so which glade packages are needed?
Another question - how do I make onBoard start on the login screen?
Anyway, keep up the good work :)

---

### Post by frafu on 2007-09-21
Hello, 

I have an ubuntu installation where I afterwards installed the complete kubuntu-desktop and xubuntu-desktop. onboard seems to run fine when I choose the kubuntu environment (I only tested it shortly). 

If you decide to install the "ubuntu-desktop" metapackage with Synaptic Package Manager, the complete GNOME environment will be added to your installation; consequently I **assume** that onboard will also work under kde. **But beware**: I don't know what happens to the system defaults if you are going to add the ubuntu-desktop. Maybe somebody else can tell you whether it is safe or not. 


Concerning onboard during GDM, please have a look at this tutorial for gutsy: 

[https://wiki.ubuntu.com/Accessibility/doc/OnboardAndDwellAtGDM](https://wiki.ubuntu.com/Accessibility/doc/OnboardAndDwellAtGDM)


Have a nice day. 

Francesco

---

### Post by jsmth on 2007-09-22
> **frafu said:**
> Hello, 

I have an ubuntu installation where I afterwards installed the complete kubuntu-desktop and xubuntu-desktop. onboard seems to run fine when I choose the kubuntu environment (I only tested it shortly). 

If you decide to install the "ubuntu-desktop" metapackage with Synaptic Package Manager, the complete GNOME environment will be added to your installation; consequently I **assume** that onboard will also work under kde. **But beware**: I don't know what happens to the system defaults if you are going to add the ubuntu-desktop. Maybe somebody else can tell you whether it is safe or not. 

Well it works OK with a default Kubuntu install for me, although onboard-settings requires python-glade2 to be installed and it still hangs when you enter a new name for your custom layout - what is supposed to happen when you click the 'customise' button?
> **frafu said:**
> 
Concerning onboard during GDM, please have a look at this tutorial for gutsy: 

[https://wiki.ubuntu.com/Accessibility/doc/OnboardAndDwellAtGDM](https://wiki.ubuntu.com/Accessibility/doc/OnboardAndDwellAtGDM)

Is there a way to script this instead of using gestures?

I would also like to know if there is a guide to creating a custom layout anywhere.

---

### Post by frafu on 2007-09-22
> **jsmth said:**
> Well it works OK with a default Kubuntu install for me, although onboard-settings requires python-glade2 to be installed and it still hangs when you enter a new name for your custom layout - what is supposed to happen when you click the 'customise' button?


I suppose you mean the "Personalise..." button. It creates a copy of the current layout and gives it the name that you typed in. The window that asks for the name remains stuck also in my kde environment; however, the copy of the layout is created in the layout folder. You can then edit the copied layout, but you have to do it manually with inkscape and an editor if I remember correctly. 

> 
Is there a way to script this instead of using gestures?


Have a look at the following thread for a method to automatically open onboard at the login screen: 
[http://ubuntuforums.org/showthread.php?t=304045](http://ubuntuforums.org/showthread.php?t=304045)

> 
I would also like to know if there is a guide to creating a custom layout anywhere.

You can find some explanation here: 
[https://wiki.ubuntu.com/Accessibility/Projects/onBoard/definitions](https://wiki.ubuntu.com/Accessibility/Projects/onBoard/definitions)

If you do a search in the wiki or in the forum, you might find more. You can use Inkscape to edit the .svg files.

Have a nice day. 

Francesco

---

### Post by jsmth on 2007-09-23
> **frafu said:**
> I suppose you mean the "Personalise..." button. It creates a copy of the current layout and gives it the name that you typed in. The window that asks for the name remains stuck also in my kde environment; however, the copy of the layout is created in the layout folder. You can then edit the copied layout, but you have to do it manually with inkscape and an editor if I remember correctly. 



Have a look at the following thread for a method to automatically open onboard at the login screen: 
[http://ubuntuforums.org/showthread.php?t=304045](http://ubuntuforums.org/showthread.php?t=304045)



You can find some explanation here: 
[https://wiki.ubuntu.com/Accessibility/Projects/onBoard/definitions](https://wiki.ubuntu.com/Accessibility/Projects/onBoard/definitions)

If you do a search in the wiki or in the forum, you might find more. You can use Inkscape to edit the .svg files.

Have a nice day. 

Francesco

OK, thanks for the help. I think I should be able to find the answers to my problems in those links...

---

### Post by frafu on 2007-09-23
@jsmth

Feel free to ask if you have further questions. 

Francesco

---

### Post by bcw on 2008-02-03
Hello,

I'm working on a text input system for tablets, and I notice onboard can do some things I need to do - not steal the focus from another window, and enter text into that window.

The second isn't so hard, but the first is of real interest.  I'm only a python beginner (I write mostly Java), so I'd like to ask about how it's done.

Is there a forum/mailing list for onboard I could ask at?  Or is this the place?

thanks,
Bret

---

### Post by frafu on 2008-02-03
Hello bcw,

There is no mailing list about onboard, that I know about.

I think that the developer of onboard sometimes looks into this forum. 

Finally, onboard is hosted on launchpad, where you can find more information about its developer. 

Regards 

Francesco

---

### Post by torstenkarusseit on 2008-04-13
Hi,
does anyone know how to make onboard accessible during the modal dialog to input root password for some applications requiring it (root terminal, synaptic, etc) ?
thank for your help

---

### Post by frafu on 2008-04-13
Open the menu System->Preferences->Assistive Technology and put a checkmark into the "Password dialog as normal windows" option. 

This will solve the problem for the gksu password dialog. (For example the dialog that you get when you open the Synaptic Package Manager.) 

However, since Ubuntu 8.04 some applications use a new method for authentification based on the new policykit. Unfortunately, the solution provided above does not work for this type of authentication dialog. (It is the dialog that you get when you click on the Unlock button in the Network panel (under System->Administration)). As far as I know, there is no solution of this problem yet. 

Could you please confirm the problem in the bugs that I filed against ubuntu 
[https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/209408](https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/209408)
and upstream 
[https://bugs.freedesktop.org/show_bug.cgi?id=15362](https://bugs.freedesktop.org/show_bug.cgi?id=15362)

Cheers

---

### Post by pnog on 2008-04-25
Hello,

I'm starting to look onboard, I'm doing a kiosk and I'm trying to use it.
But I'm having lots of dificulty to get documentation, where can I find it ?
Now I've removed the frame from the keyboard and now I can't configure it, how can I put back the frame so I could configure it ?

thanks.
Pedro

---

### Post by frafu on 2008-04-26
You can start onboard by command line by passing it parameter for its size, its location on the screen. You can also pass it a file with a custom layout... 

Please, type the following in the terminal to get details about the parameters: 
```
 
onboard --help

```  

If you look at the explanation about how to set up a system to start onboard during GDM, you can see an example where onboard is started with parameters:
[https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM](https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM)

Hoping that this helps, 

Francesco

---

### Post by sir_skiner on 2008-04-28
hi! 
there are some major problems with onboard on Hardy. take a look on that thread: [http://ubuntuforums.org/showthread.php?p=4821283&posted=1#post4821283](http://ubuntuforums.org/showthread.php?p=4821283&posted=1#post4821283)
and pleas, help...

---

### Post by frafu on 2008-04-29
Hello, 

Have you tried to reinstall onboard and python-virtkey with the Synaptic Package Manager? 

Have you tried to use a layout stored in your home directory instead of letting onboard create the layout when it gets started? 

Are you using it on the local computer or are you forwarding your gnome session to a remote computer and working remotely? (On my system, onboard is working locally, but not remotely.) 

Cheers

Francesco

---

### Post by sir_skiner on 2008-04-29
yes, I did reinstalled both whith no effect. and I use local access.

could you please tell me how to use custom layout?

---

### Post by frafu on 2008-04-29
Please have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=769521"). 

[This bug]("https://bugs.edge.launchpad.net/ubuntu/+source/virtkey/+bug/220475") might be related. 

You can find further information on [these wikipages]("http://ubuntuforums.org/showthread.php?t=769521"). 

To simplify things for you, I am uploading a custom layout from my computer. Uncompress it and put the 4 files the hidden ~/.sok/layouts folder. Start onboard-settings, set it to use the local layout and close onboard-settings. Start onboard. 

Hoping that this helps. 

Francesco

---

### Post by frafu on 2008-04-29
Here it is.

---

### Post by sir_skiner on 2008-04-29
unfortunatly nothing helps.

i can't work whith ubuntu whithout onboard so i'm unable to build patched python-virtkeys:(

---

### Post by sir_skiner on 2008-05-02
ok, so fix made by Chris Jones from the launchpad.net works almost fine, except now I can't type polish special chars. any ideas what to do?

here's patched build.

---

### Post by michaelwilliamson on 2008-06-12
im using sok (onboard) on a tabletpc and am trying to use it with some 3d graphics applications which use keyboard modifiers in combination with mouse clicks.... eg "alt" and "leftmouseclick" is rotate view, "ctrl" + "alt" + "leftmouseclick" is zoom view....

onboard doesn't seem to work like the real physical keyboard here. All I get are unmodified left mouse clicks.

am i missing something? do i need to add anything to xorg.conf? or is this just unsupported functionality?

---

### Post by Belathor on 2008-06-15
> **michaelwilliamson said:**
> im using sok (onboard) on a tabletpc...

Are you aware of cellwriter? It has an onscreen keyboard as well and is more geared for tabletpcs in that it emulates the TIP to a greater extent.

---

### Post by michaelwilliamson on 2008-06-16
Yes, I've tried cellWriter too and it seems to have the same problems unfortunately, though some other keyboard shortcuts seem to work better than with onboard....

Ah well.

---

