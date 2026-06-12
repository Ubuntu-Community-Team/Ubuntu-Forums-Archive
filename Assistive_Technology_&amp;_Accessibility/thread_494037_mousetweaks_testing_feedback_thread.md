---
title: "mousetweaks testing feedback thread"
date: 2007-07-06
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2007-07-06
Hello, 

The mousetweaks are being implemented as a Google Summer of Code project. The mousetweaks offer systemwide dwelling and delayclick (i.e. opening the contextual menu with a left click and hold). 

You can find version 0.1.0 on the [developers blog.]("http://gerdk.blogspot.com/") However, I will attach a more recent version to this post, namely version 0.1.2.

Please keep in mind that this software is currently in development and consequently may not work properly. If you decide to use it, it is at your own risk. 

Nevertheless, if you are trying it, don't hesitate to post any comments or suggestions. 

Here are a few known issues: 
- dwelling ctw mode: grab icon does not always show up; for example it does not show up on the scrollbar 
- gesture mode: cannot open programs from within applications menu; this is a major show stopping.
- delay click does not work in Firefox, but works in epiphany

Francesco 

PS: You have to compile the mousetweaks yourself, as there is no debian package available yet.

---

### Post by frafu on 2007-07-10
Hello, 

A few words about how to compile and install it. You need an user account with administrative privileges to do it. Please consider that I don't have a complete knowledge about this. Consequently, the instructions below might contain errors. If you use them, it is at your own risk.  

1) First you have to install the packages needed for compilation. Open the Synaptic Package Manager and install the following packages: 

build-essential 
libgconf2-dev
libglade2-dev
libpanel-applet2-dev
libatspi-dev
libdbus-glip-1-dev

2) Uncompress the source archive posted above by double clicking on it. An archive manager should start to help you uncompress it. 

3) Now it should be possible to compile it without errors by doing the following: 

- open the terminal 
- change the working directory of the terminal to the uncompressed mousetweaks folder. You can do it this way: type "cd" without quotes followed by a space in the terminal; take the uncompressed archive, drop it onto the terminal and the path to the archive will automatically appear in the terminal; hit the return key on the keyboard. The working directory of the terminal should now be set to the uncompressed archive; you should see its path in the terminal left to the cursor. 
- type "./configure" without quotes in the terminal and hit return. Wait until you see the cursor on a new prompt and check whether there is no error in the last lines before the prompt. If there is no error, you can continue, other you have to correct the error before continuing. 
- type "make" without quotes in the terminal and hit return. Wait until you see the cursor on a new prompt and check whether there is no error in the last lines before the prompt. If there is no error, you can continue, other you have to correct the error before continuing. 
- type "sudo make install" without quotes in the terminal and hit return; you will be asked for your password. Wait until you see the cursor on a new prompt and check whether there is no error in the last lines before the prompt. If there is no error, everything is set up now. 

The mousetweaks have been installed in the Accessibility and in the Accessories menu under the Applications menu. You can start using them. 

Francesco

PS: To uninstall the mousetweaks, you have to use the terminal again: 
- open the terminal 
- change the working directory of the terminal to the uncompressed mousetweaks folder
- type "sudo make uninstall" without quotes in the terminal and hit return

---

### Post by frafu on 2007-07-10
Hello, 

I have built a debian package of the mousetweaks-0.1.2. After downloading it, do a double click on the downloaded package to start its installation. 

However, be aware that it is the first debian package that I have ever built and don't know whether it works as it should. If you are going to use it, it is at your own risk. 

Francesco

---

### Post by sach87 on 2007-07-11
Hi! 
I tried your deb pack on another pc and worked smooth and clean!
nice job!

---

### Post by frafu on 2007-07-11
@sach87

Thanks for the confirmation that it works. 

Francesco

---

### Post by frafu on 2007-07-14
The developer Gerd Kohlberger has posted an updated version, namely mousetweaks-0.1.4.

Here are the changes that have been made since version 0.1.2. 
	* use gnome mouse icon and honor current theme
	* add 'Disable' option to dwell gesture menus
	* don't allow impossible gesture settings
	* improve warning dialogs
	* fix: bug in the ctw context menu
	* fix: under certain conditions disabling and reenabling
	       dwell-click failed
	* set dialog type hint for ctw and preferences

Below in this post, you will find a package with the source code posted by the developer and a debian package that I built from that source code and that is targeted for Ubuntu Feisty. As before, if you decide to use it, it is at your own risk. 

Francesco

---

### Post by frafu on 2007-07-16
Hello,

The developer has discovered a dialogue bug and fixed it; however without changing the version number. 

I will attach his updated source and the debian package that I derived from it. If you decide to use them, it is at your own risk. 

Have a nice day. 

Francesco

---

### Post by Gen2ly on 2007-07-17
Hi there frafu, I tried to compile 1.4 and got;
> 
./configure
configure: error: No cspi-1.0 package information found

---

### Post by frafu on 2007-07-17
Hello, 

You have to install the following libraries in order to be able to compile the mousetweaks: 

libgconf2-dev
libgtk2.0-dev
libglade2-dev
libpanel-applet2-dev
libatspi-dev
libdbus-glib-1-dev

Especially for your error, I think that it is libatspi-dev that is missing. 

Francesco

---

### Post by frafu on 2007-07-27
Hello,

An updated version of mousetweaks has appeared; namely 0.1.6.

New features:

* dwelling drag click now shows a drag cursor
* gnome-help support (no actual documentation)

More details in the ChangeLog.

---

### Post by frafu on 2007-07-29
And here are the debian packages of version 0.1.6 for ubuntu feisty and gutsy. To use only at your own risk.

---

### Post by bicchi on 2007-08-25
Here is my feedback based on: Mousetweaks version 0.2.2 
Keep in mind that I have only used it for 20 minutes.

I have a tablet (1024x600 resolution) running Feisty that does not detect the right click functionality when I hold the stylus for a period of time. For some reason I am having problems configuring the evtouch driver in my xorg. Anyway, that is another story. 

When I first ran mousetweaks it asked me to run the Assistive Technology Preference. Why couldn't mousetweaks start that program for me? Or even turn the feature needed for it to work. The program is called: gnome-at-properties

My main use for the program is the "Delay Click" feature. Why only make the threshold 30 pixels in the General tab? I would like to have a number as big as my screen size; that way I can drag all the icons in my desktop and the right click menu would kick in. The user should have the option to set this amount as high as he/she pleases. Having a big range would not hurt anybody but It would give us a better choice. 
If you do not like this idea at least make it more that 30 pixels for people that do not have good hand control. Say 200 pixels? Anyway, I would consider giving this one some thought.
*Note to self: cut down on caffeine.*

I am still trying to understand what Dwell Click does? This is me been ignorant plus for now I just care to have right clicks.

I like the fact that I can right click on Firefox. Can I use mousetweaks to do scroll up/down using gestures? That would be nice.

I am looking at the screenshot here: [https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks/mousetweak5](https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks/mousetweak5)
I do not have a "Single Click" tab? 

A less  important feature for me. I would like to be able to remove the icon from the notification area. I do not need the icon there and would prefer if the program just stays in the background all the time. The program should have an option to terminate and another to remove the icon from the notification bar.

The most important feature would be to have this package in the repositories. 

Cheers,

---

### Post by frafu on 2007-08-25
First of all, thanks for your feedback. 

> 
When I first ran mousetweaks it asked me to run the Assistive Technology Preference. Why couldn't mousetweaks start that program for me? Or even turn the feature needed for it to work. The program is called: gnome-at-properties.
 

That is a good point. I will tell the developer about it. 

>  
My main use for the program is the "Delay Click" feature. Why only make the threshold 30 pixels in the General tab? I would like to have a number as big as my screen size; that way I can drag all the icons in my desktop and the right click menu would kick in. The user should have the option to set this amount as high as he/she pleases. Having a big range would not hurt anybody but It would give us a better choice. 
 

I don't really understand what you mean by "drag all the icons and right click". If you want to open the contextual menu on multiple items, why not make it in 2 steps: First step: do the selection. Second step: delay click. 

But you might be right with the fact that setting a higher maximum value will not hurt anybody. 

>  
I am still trying to understand what Dwell Click does? This is me been ignorant plus for now I just care to have right clicks.
 
Mousetweaks performs automatically the click specified in the clicktype window after the pointer has been motionless for the time specified by the slider in the corresponding preferences tab. This is for example useful for people that cannot click with a hardware button. 

>  
I like the fact that I can right click on Firefox. Can I use mousetweaks to do scroll up/down using gestures? That would be nice.
 

The author of mousetweaks is developing the gestures feature separately from mousetweaks. It is called chickenscratch and you can find it on his [blog]("http://gerdk.blogspot.com/"). 

By the way, the website of firefox offers mousegestures addons for firefox. 

>  
I am looking at the screenshot here: [https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks/mousetweak5](https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks/mousetweak5)
I do not have a "Single Click" tab? 
 

Mousetweaks is still under development; it has not been implemented yet. 

>  
A less  important feature for me. I would like to be able to remove the icon from the notification area. I do not need the icon there and would prefer if the program just stays in the background all the time.
 

The author is already aware of the fact that the icon in the notification area is not very helpful; different propositions have been made, for example combining it with the dwell applet. But as the panels don't offer the functionality to applications to add or remove applets from it, this question is not resolved yet. (at least I think so) 

>  
The program should have an option to terminate and another to remove the icon from the notification bar.
 

Why not simple disable the features in the preferences of mousetweaks? (I think that if they are disabled, it is as if mousetweaks is not running.) 

>  
The most important feature would be to have this package in the repositories. 


I think it will be shipped in Ubuntu 7.10.

Have a nice day. 

Francesco

---

### Post by lowfi on 2007-08-25
> **bicchi said:**
> When I first ran mousetweaks it asked me to run the Assistive Technology Preference. Why couldn't mousetweaks start that program for me? Or even turn the feature needed for it to work. The program is called: gnome-at-properties
Starting the AT daemon requires a session restart (login/out). Unfortunately there's nothing mousetweaks can do about that.

> **bicchi said:**
> My main use for the program is the "Delay Click" feature. Why only make the threshold 30 pixels in the General tab? I would like to have a number as big as my screen size; that way I can drag all the icons in my desktop and the right click menu would kick in. The user should have the option to set this amount as high as he/she pleases. Having a big range would not hurt anybody but It would give us a better choice. 
If you do not like this idea at least make it more that 30 pixels for people that do not have good hand control. Say 200 pixels? Anyway, I would consider giving this one some thought.
I don't really get what it is your trying to do and doesn't work. The threshold is intended as a tremor suppression feature. More than say 100 pixels wouldn't make sense in that context. However 30 seems too low in any case. 

> **bicchi said:**
> *Note to self: cut down on caffeine.*
tell me about it. :)
 
> **bicchi said:**
> I would like to be able to remove the icon from the notification area.
Should be gone in the next release.
> **bicchi said:**
> The most important feature would be to have this package in the repositories.  If everything works out, it will be in gutsy.

Cheers

---

### Post by skyy007 on 2007-08-25
Advertisement removed by frafu

---

### Post by bicchi on 2007-08-25
What I am trying to do by making the threshold big enought is this: 
[LIST=2]
[*]Say I have 20 icons on my desktop spread in a radius of 500 pixels square. I should be able to select all of them an hold the mouse for 3 seconds and the right click option would allow me to make a decision on those 20 icons.

[*]In OpenOffice I select a picture box some text and just hold the mouse for 3 seconds to apply some option to those objects.
[/LIST]

What this would avoid is doing a second click after the selection. 

Regarding starting the "Assistive Technology Preference."
I am not asking to force a session restart of gnome but at least fire up the "Assistive Technology Preference." that way the user can turn on the feature that is needed. 
In my case I was able to run gnome-at-properties before doing a restart. 
Then I needed to restart gnome. 
Maybe I am missing your point?

---

### Post by frafu on 2007-10-17
Hello, 

It might take some time until Mousetweaks will be available in the Universe repository of Ubuntu 7.10.

Consequently, I am offering it in the meantime by using the Personal Package Archive (PPA) service offered by Launchpad. The PPA can be seen as personal repositories that users can setup to offer their programs to the public. 

By adding my PPA to the Software Sources in Ubuntu, you will be able to install Mousetweaks with the Synaptic Package Manager in the same way that you do it for other programs. However, I  give you the permission to use my PPA and the software offered by it, only if you do so at your own risk. 

My PPA is located here: 
for the binaries (i396 and amd64 architectures): 
```
 
deb http://ppa.launchpad.net/frafu/ubuntu gutsy main restricted universe multiverse

``` 
for the source 
```
 
deb-src http://ppa.launchpad.net/frafu/ubuntu gutsy main restricted universe multiverse

``` 

You can find more information about how to add my PPA to your software sources in the "Install Mousetweaks and an updated the version of onboard" section of the following page: 
[https://wiki.ubuntu.com/Accessibility/doc/OnboardAndDwellAtGDM](https://wiki.ubuntu.com/Accessibility/doc/OnboardAndDwellAtGDM)


By the way, Mousetweaks is hosted on Launchpad at the following address: 
[https://launchpad.net/mousetweaks](https://launchpad.net/mousetweaks)


Francesco

---

