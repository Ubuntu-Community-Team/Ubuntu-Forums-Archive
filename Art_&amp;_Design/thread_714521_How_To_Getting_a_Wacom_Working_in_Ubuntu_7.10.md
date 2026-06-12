---
title: "How To: Getting a Wacom Working in Ubuntu 7.10"
date: 2008-03-03
forum: Art &amp; Design
---

### Post by ShadowMKII on 2008-03-03
This is a tutorial I found online that helped me to get my tablet working. This is fairly recent - February 15, 2008 - in terms of Wacom tutorials, so this should be a large help to those who have purchased a Wacom tablet in the past couple of years.

This tutorial is intended to be for those who are running GNU/Linux Ubuntu 7.10 "Gutsy Gibbon" and who have some minor experience with the terminal client. As I am a relatively new Linux user (about six months now), this was definitely enough to help me. This is also keeping in mind that I am not entirely terminal savvy, but I do have some experience using the terminal to get such things as video cards, multiple kinds of software (or freeware (see, I still do not know it all yet)) and some repositories working without Synaptic, until I got Gutsy in late October of 2007. After that, I still used terminal, but not to such an extent.

My primary experience with a tablet is in The GIMP, but that is not to say that this tutorial deals with only that application. In fact, it deals with Blender, XTerm and the Ubuntu Graphical User Interface (GUI), otherwise known as "X." 

Here is the link that helped me get my tablet working. 



[http://cgi.feureau.com/2008/02/how-to-get-wacom-tablet-fully-working.html](http://cgi.feureau.com/2008/02/how-to-get-wacom-tablet-fully-working.html)



If this link does not explain things fully enough to you, please contact me. I apologize in advance for my tardy responses, as I log on here only about once a week.

Lastly, for those of you to keep in mind, I had already tried the routes of the Linux Wacom Project and other workarounds. The Linux Wacom Project proved to be far too difficult and lengthly while still accomplishing the same amount that one of the workarounds I was supplied with on the forums here. (Thank you kind sir.) I followed the workaround and I got my pressure sensitivity working, but it was not customizable (not that it mattered - at the time) to my preference, nor did the Expresskeys and Touchstrip work. After searching for about four months, I came across this, which eliminated the need for me to use the previous workaround and eventually, after some questions that you will see on the blog there, I was able to get everything working just as I wanted it to.

This tutorial was very helpful and made my Linux Wacom experience very enjoyable. If you follow it with the correct operating system and some experience with the terminal, you should be fine.



*NOTE* 

This is advice to those who do not know already - it should be <b>imperative</b> that you save a copy of the original file of any that you have to/decide to edit. By following this tutorial and saving the files, you will be in the root account (just refer to your left-hand navigation bar in the file folder browser, otherwise referred to as "Nautilus"), which is exactly what you want.

Also, I may post the entire blog on here if I am able to get the permission of the blog owner so that in case the link breaks the information will still be available.



I hope this helps to those who have been struggling or simply want there tablet working. It sure helped me! ^-^

---

### Post by ShadowMKII on 2008-03-04
As promised, here is the rest of the How To by Feureau in his blog.

This is licensed under the Creative Commons 3.0 NC-SA, so feel free to distribute and/or alter this for non-commercial/non-profit use.


**HOW TO begins here**


**How to get a Wacom Tablet Fully Working in Ubuntu Linux**


I mean, FULLY WORKING not those half working tablets where the pressure don't work 100% and the expresskeys and the touch strip not working. I mean this guide is to help non-programmer artists get their ubuntu system working with their wacom tablets. Just like they do in their Apple Macs and *shudder* windows.

The first thing I'd like to point out is that, this guide is not intended for programmers. This guide is for computer dummies like myself who wanted to escape to a free OS. If you're just trying out to see if wacom works under ubuntu, don't waste your time. The tablet is not as easy to setup as in a Mac or Windows. No complete installer is provided by wacom. However, your tablet will work with Ubuntu out of the box. There's no extra setup needed. But the expresskeys and the touch strip will not work by default.

To get a wacom tablet fully working, the only mental faculty you need is already present if you have ever finished a Legend of Zelda game. Except zelda II that one just sucks. I'm sorry if you ever played that one. Or the CD-i Zelda.

Now, some of the instructions presented here will be in the form of codes. It'd be nice if you try to learn and understand what they mean. They will be very useful to your Ubuntu future. But if you're intimidated by strings of nonsensical characters randomly strung up by an evil genius geek deep in his dragon infested dungeon, just think of it as looking for a particular icon in other OSes like OS X or windows. Or just looking for the any key. Only, in this particular OS, it's already provided for you to copy paste.

I hope you're running Ubuntu 7.10 or higher. The codename for that version is Gutsy Gibbons. If you're not, please run your automatic software update till you run Gutsy. (If you're already running previous version of Ubuntu, you wouldn't need to read the dumbingdowness parts of this guide)

So, anyway, let's begin.

Although Wacom tablet runs out of the box in Ubuntu, you'll need to enable it in Ubuntu. That's just how linux works. If something is unnecessary, it just won't load it. Unlike windows which becomes bloated because it loads practically everything at starts up.

**Part 1. Running a wacom tablet.**

This part is lifted from ubuntuguide. You might want to use that one if you already know what you're doing. And return here for the second part.
First, you'd have to fire up the terminal. Go to Applications > Accesories > Terminal

[[img=http://img518.imageshack.us/img518/7070/desktopkc7.th.jpg]](http://img518.imageshack.us/my.php?image=desktopkc7.jpg)

And boom! You got this terminal window:

[[img=http://img518.imageshack.us/img518/742/terminalfo9.th.jpg]](http://img518.imageshack.us/my.php?image=terminalfo9.jpg)

Hooray! You've just prepared yourself everything that is necessary to complete this howto guide. Isn't that easy? Even mere mortals can do it. Most people are just too chicken to try.

Now let's open the editor and edit xorg.conf. All you need to do is copy this:

_____________________________________________________________

    gksu gedit /etc/X11/xorg.conf

_____________________________________________________________

And paste it to the terminal by pressing Ctrl-Shift-V. Then just press enter to open the editor with xorg.conf. You might be asked for password now. Just put in your login password and it'll open the editor.
Look for the part that says:

_____________________________________________________________

    #Section "InputDevice"
    #Driver "wacom"
    #Identifier "stylus"
    #Option "Device" "/dev/input/wacom"
    #Option "Type" "stylus"
    #Option "PressCurve" "50,0,100,50"# Custom preference
    #Option "ForceDevice" "ISDV4"# Tablet PC ONLY
    #EndSection

    #Section "InputDevice"
    #Driver "wacom"
    #Identifier "eraser"
    #Option "Device" "/dev/input/wacom"
    #Option "Type" "eraser"
    #Option "PressCurve" "50,0,100,50"# Custom preference
    #Option "ForceDevice" "ISDV4"# Tablet PC ONLY
    #EndSection

    #Section "InputDevice"
    #Driver "wacom"
    #Identifier "cursor"
    #Option "Device" "/dev/input/wacom"
    #Option "Type" "cursor"
    #Option "ForceDevice" "ISDV4"# Tablet PC ONLY
    #EndSection
_____________________________________________________________

And remove the # sign before each line until the three parts looks like this:

[[img=http://img135.imageshack.us/img135/8242/xorgconfetcx11geditew9.th.jpg]](http://img135.imageshack.us/my.php?image=xorgconfetcx11geditew9.jpg)

Then save.
And we're done with part 1! All you have to do is restart and you'll have a fully working tablet now! Or, if you're smart, just press Ctrl-Alt-Backspace.

**Part 2. Getting to drive the expresskeys.**

If you restarted as told, and done playing with your working pen, you'll notice that the expresskeys and the touch strips don't work. If you have a Graphire 3, then you can immediately draw in Gimp. Have fun! But the rest of us, we have to increase our productivity by utilizing these touch strips.

The first thing is to launch the Terminal as we did in the first part.

Then you paste this code:

_____________________________________________________________

    sudo aptitude install xlibs-dev

_____________________________________________________________

Run it by pressing enter, and it'll display a jumble of things. Don't worry about it. After it's done, just paste in and run this code:

_____________________________________________________________

    sudo aptitude install wacom-tools

_____________________________________________________________

Those two codes will ensure that your computer is fully prepared to compile the program that will run expresskey and touchstrips.

Now, launch your firefox browser, and head to Expresskeys. And get the latest tar/gz thing. As of this writing, it's expresskeys-0.4.1.tar.gz.

Then you just right click on it and select extract here . After that, in your terminal, go to the folder that you've just extracted. In short, paste and run this code:

_____________________________________________________________

    cd Desktop/expresskeys-0.4.1

_____________________________________________________________

Change the version number as necessary.
And inside that, run these commands line by line. Don't try to do it all in one go, copy one line and past it then run it, after that run the next line. It's maybe tedious, but if anything goes wrong, you'll know which part went wrong and it'd be easier to fix.

*EDIT*

Make sure that you enter "sudo" before each of the following commands.

*EDIT*

____________________________________________________________

    ./configure
    make
    make install

____________________________________________________________

After that, we'll need to open xorg.conf again, so like before, just run this command:

____________________________________________________________

    gksu gedit /etc/X11/xorg.conf

____________________________________________________________

And add this section immediately above or below (it doesn't matter) the three we edited in the first part.

____________________________________________________________

    Section "InputDevice"
    Driver "wacom"
    Identifier "pad"
    #c~b Option "Device" "/dev/ttyS0"
    Option "Device" "/dev/input/wacom"
    Option "Type" "pad"
    Option "USB" "on"
    EndSection

____________________________________________________________

Then look for the part that says

____________________________________________________________

    Section "ServerLayout"

____________________________________________________________

And immediately below the line, add:

____________________________________________________________

    InputDevice "pad" #c~b Intuos3

____________________________________________________________

And that's it, we have set up the necessary programs to get the touch strip and the expresskeys to work.
Just save and reset your machine or press Ctrl-Shift-Backspace.

**Part 3. Near instant gratification.**

Just like in part 1, start your terminal. And run this code:

____________________________________________________________

    expresskeys -d

____________________________________________________________

If you did everything right, it wouldn't spit out any thing and returns to the terminal like nothing happened.

Fire up gimp and try out your touchstrips and expresskeys!! :)

But wait, what if you want to customize the expresskeys and the touchstrip?

It's easy, you just need to know the key combination and edit the expresskeys config file.

To edit the config file, first you must be able to see it.
Go to your home folder: Just select Places > Home Folder. If you're running ubuntu, I don't need to illustrate this anymore. In your home folder menu, press Ctrl-H to show some hidden files and folder (Ctrl-H again to hide them. Look for a folder named .expresskeys (with the . (dot) before the expresskey) and inside, you'll find a file named intuos3.conf1. Just double click to open it.

Follow the instructions in the file to edit each and every function of the expresskeys and touchstrip.

Oh, and one more thing, to get the keycode, start your terminal and enter:

_________________________________________________________

    xev

_________________________________________________________

A small window will appear and your terminal will be spitting a bunch of code. Put your pointer inside the small window and leave it there. Don't move even for a pixel. If you're using the tablet, just lift your pen.
Press the key that you want the keycode of on your keyboard, and immediately it will appear on your terminal as marked:

[[img=http://img337.imageshack.us/img337/3747/xevjd8.th.jpg]](http://img337.imageshack.us/my.php?image=xevjd8.jpg)

Good night good luck, and most of all, have fun with your fully functional tablet! :)


**HOW TO ends here**

---

### Post by lyceum on 2008-03-04
Did not work :( I am now wondering if my tablet it broken.

---

### Post by ShadowMKII on 2008-03-13
Do not worry, I am almost certain that your tablet should not be broken!

Just type the term "xev" into your terminal after you open it and move your stylus around. If there are a bunch of codes that come up from you moving your stylus around, then you know that it is working! Sometimes the tablet issue can be quite complicated, so do not worry.

Did everything go as planned as stated on the tutorial? Are there any places that you could have messed up? Did you try restarting your computer after you finished? Lastly, did you type "expresskeys -d" into your terminal after you finished doing all that was listed in the tutorial? (You have to type that in each time you want to use your expresskeys and touchstrip.)

---

### Post by days_of_ruin on 2008-03-13
Or you could wait until hardy comes out.It's supposed to have
built in support for wacom tablets.

---

### Post by shendric on 2008-03-14
Hey,

Maybe you can help.  I'm running Gutsy, with a Graphire 3(it may be 2, I can't remember).  When I use the stylus, it moves the mouse pointer around, and using xev, I get codes, just like with the mouse.  However, both Inkscape and GIMP don't recognize the tablet as an input device.  I just get No Extended Input Devices, when I try to configure extended input devices.   Any thoughts?  It won't draw anything, although, apparently I can draw two-node paths in Inkscape, even if I have it set to the Calligraphic tool.

---

### Post by ShadowMKII on 2008-03-15
I find that odd that you are getting signals but it is not registering as an input device. I know that once a tablet is plugged in it begins to work immediately and can be substituted for a mouse, but I have not heard of it ever half working like you described.

I guess the first question to ask is if your tablet is Serial or USB, seeing as how you mentioned you have a Graphire that is older than Graphire 4. As for why your tablet is not registering in the GIMP or Inkscape, I cannot really comment on. When I plugged in mine it began to work immediately in all software, except the Expresskeys, Touchstrip and pressure sensitivity were all inert. If I had a Graphire I would test it out, but my Intuos3 is fairly new and would probably not produce the same results. Sorry.

Are there any other threads that are Graphire oriented? Also, seeing as how you mentioned your tablet was a bit old, does it every have problems being read on the pad? If there are some complications like that you may want to invest in a new tablet, as that is the sign that they may stop working.

---

### Post by shendric on 2008-03-17
Thanks for the response.  It's a USB tablet.  I only bought it about 2 years ago, so it's not really that old.  It was working perfectly until I upgraded to Gutsy about a couple of months ago.

---

### Post by ShadowMKII on 2008-03-17
USB version should make it a little bit easier to install. Did you buy it used? If you bought it new it should be a Graphire 4 because that is the latest model.

Check your kernel version just in case. If your kernel is not one of the newer versions, some of the software that you download for your tablet to work might not work properly.

If you want some additional support, do not be afraid to visit the website where this tutorial originally came from as well. If you have information coming from two sources, you are more likely to get answers faster.

---

### Post by dibujante on 2008-03-28
I got it working but am still getting an obnoxious error. My mouse sometimes ignores clicks, seemingly randomly. Any tips?

---

### Post by flaviocpontes on 2008-04-04
I just gought an Intuos3 6x11 and plugged it in.

The mouse doesn't work at all and the stylus only moves the cursor while touching the pad. Clicks are totally erratic, meaning sometimes it works sometimes not.

I thought the tablet was faulty, but I tested it at my neighbours computer and it worked perfectly.

The feeling I get is that the signal threshold is being cut too short.

Anyone experienced this symptoms too?

Im running gutsy right now, but I tested it in the Hardy live and get the same problem.

I really need to get it working smoothly soon, because I need it to do a job.

Thanks in advance.

---

### Post by ShadowMKII on 2008-04-08
You said that all you did was plug your tablet in, correct? If that is the case, you still need to install the drivers that are necessary to run it. Just look at the tutorial on the first page of this thread and that should help you. If not, message me back and I will see what I can do. This happened to me in the past and I can verify that your tablet is not faulty - you just do not have any drivers.

As for the erratic mouse clicking, I have not used my mouse so much with my tablet so I am not entirely sure how to solve it. It is my guess that these drivers are more attuned to getting the stylus working more than the mouse, but I would not say that is confirmed just yet. A good place to get answers on that would be to go to GIMPTALK by searching in Google, and then reading the sticky that shows how to get a tablet completely working. From what I understand, it is about the exact same as what I have listed, but with a couple more steps that might be more complicated. Just be wary, that is all.

---

### Post by jmmmp on 2008-05-18
Hi,

I already had my intuos3 6x8 working, but without the pads + expresskeys. Thanks, that seems to have everything in order. Could you maybe make availble an example of your intuos3.conf1 file, just for reference?

It also happens that now and then the pads don't work, and after a while they work again. But I don't know exactly what triggers that (I haven't configured the expresskeys yet).

One other thing: all the time my pen buttons are switched compared to windows. That is, when you hold the pen up, the right-button is the upper one, and the double-click is the bottom one. Do you know anything about that? It always behaved like that for me, but besides telling xorg to listen to the wacom input, I found no other possibility of configuring that.

Thanks,

João Pais

---

### Post by ShadowMKII on 2008-06-08
Not a problem; here is the code:

```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"		#USB ONLY
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"		"on"		#USB ONLY
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"	#USB ONLY
	Option		"Type"		"cursor"
	Option		"Mode"		"relative"
	Option		"USB"		"on"		#USB ONLY
	Option		"ForceDevice"	"ISDV4"		#Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  #c~b Option   "Device"        "/dev/ttyS0"          	#SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   	#USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  	#USB ONLY
EndSection

```

The other part of the code is here:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "eraser"    "SendCoreEvents"
    InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
    InputDevice    "pad"   #If you have Intuos3/Cintiq 21UX/Graphire4 tablets. It should NOT send core event
EndSection

```

Sometimes the lack of response from the pads happened to me as well. I do not know why. You would have to contact someone more advanced about this than me. I also do not know why the buttons like to switch on you, but I think either the xorg.conf file can take care of that.

Now that I have upgraded to Hardy, I am having some problems with my expresskeys and scrollbar, so I will start a new thread about getting help on that.

Sorry for the late reply! ^^;

---

