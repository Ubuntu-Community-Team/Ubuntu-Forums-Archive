---
title: "Help me not switch back to Windows"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Kindred on 2005-12-22
I could do with some help, I have been running Ubuntu for a week or so but at this point i'm almost tempted to switch back to windows.  I could probably write a longer list of issues/problems but I will start with these smaller things and hope I can resolve some of them.  They are a bit random.

'List View' (Windows style) is easily the best way to view files for me.  Nautilus version is more like 'details', and it's still not as good because you can't do any kind of region selecting?  Is there anything better than Nautilus for Gnome?  In general I don't really like it. 

Right clicking and dragging files/folders in windows allows me to 'copy/move/create shortcut', this kind of thing is useful.  Maybe you have to add a script or something to do this kind of thing?

Mouse speed is pretty slow even at full sensitivity.  I really need to speed this up, any ideas?

No suitable dialup information/method so far (all I want is something to show connection speed and allow me to connect/disconnect, something that actually matches the gnome interface rather than those ugly system monitor things.  Gnome-ppp is alright except for the fact you can't close the connection information window? And no connection speed..)  

No integrated search in Nautilus? I don't understand.. 

Those gnome panels.. I can't seem to add my own separators between things/icons.  I've seen some screenshots with seperators but I can't figure it out.

Any help on these things would be appreciated.

Maybe I should try KDE? I'm finding everything a bit limited.  Or maybe it's just because I don't know how to do what I want.

---

### Post by Knomefan on 2005-12-22
Yep, really sounds to me like you should try KDE.
You might like Konqueror better as a file manager and it gives you the option to copy/move/create shortcut out of the box.

P.S.: If you try it I'd recommend using the semi-official kde-3.5:
[http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

---

### Post by audax321 on 2005-12-22
As far as the copy/move/create shortcut menu, it appears by dragging with middle-click. Also, what kind of mouse do you have? The only thing I can think of why your mouse would be too slow is because its a Logitech with an MX engine and you need to adjust the DPI to get a higher speed or something... other than that, I've never heard of anyone complain their mouse is too slow.

Also, to make file searching more convenient, you could right click a panel > Add to Panel... > scroll all the way down adn add Search for Files...   This will add a little magnifying class to your panel that you can click to launch the file searching utility. Also, you just gave me an idea for a quick script I could right to add this functionality by just right clicking and going to the scripts menu... I'll give it a try and post back if you want to use it.

---

### Post by LoclynGrey on 2005-12-22
Do this
get a white board, write on it in bold capitals.
MICROSOFT WINDOWS
under the heading put the following
- navigation
- installation of new programs
- compatibility to peripherals etc
- cost of ownership


Now...
Grab a cloth, go up to the board again and wipe the board clean. Rub it all out and then forget anything and everything to do with how you did things in Microsoft Windows.

cool?
Awesome dude, welcome to Ubuntu Linux.
> this is where you start. (where most of us do)
Most answers to the questions/frustrations that seem to hold you back can be found in this Ubuntu forum, alternatively there is [Google]("http://www.google.com") which, like the people here on[ Ubuntu forums]("http://www.ubuntuforums.org") are/is your friend(s).

The key things are to _never give up_, _be persistent_, _be patient_.
You are learning a new OS language and you will get there like everyone else. The most important thing to stop doing, which I used to do badly, so are very guilty of it &#8220;Is stop thinking the MS Windows way&#8221;. :) haha

---

### Post by audax321 on 2005-12-22
I completely agree with Loclyn Grey, a lot of people forget that Linux is NOT Windows. It has its own way of doing things and in my opinion Windows is actually harder for me to use now since I've been using Linux so long.

Anyway, here is the search script if you want it do the following:

1. Applications > Accessories > Text Editor

2. Paste the following code in:

```

#!/bin/sh

# Searches either the currently selected directory or current directory that is being viewed.

DIR_NAME="$(pwd)"/"$1"

if [ -d "$DIR_NAME" ]; then
	gnome-search-tool --path="$DIR_NAME"
else
	gnome-search-tool --path="$(pwd)"
fi

```

3. Save the file as: Search Directory

4. Go to the saved file in Nautilus, right click and go to properties and then the permissions tab and make sure the permissions are set to 755 (everything under read checked, the top box under write checked, and everything under execute checked).

5. Right click in Nautilus > go to the scripts menu > select open Scripts folder (or if that isn't available go to /home/username/.gnome2/nautilus-scripts) and copy paste the file you created in there.

Now when you right click in Nautilus, you can go to the scripts folder and there will be an option to Search Directory in there.

---

### Post by bscbrit on 2005-12-22
Help you not switch back to Windows - easy. Give your Windows CD to charity and give yourself some time.  Its a steep hill at first, but the view from higher up is worth it!

---

### Post by Kindred on 2005-12-22
Hey, thanks for the replies.  I didn't know about the middle button thing, thanks for that.  The mouse speed is still an issue as are Nautilus' shortcomings but i'll keep going..

---

### Post by patrick295767 on 2005-12-22
[http://www.ubuntuforums.org/showthread.php?t=64557&page=8]("http://www.ubuntuforums.org/showthread.php?t=64557&page=8")
  
My progress thread, and after all this, no return to windows,... it's rather crappy ... 

I love linux !

---

### Post by Totzo on 2005-12-22
wait for the "dapper" release or try it out another partition- I find it pretty stable at the moment. Nautilus has integrated search and sendto bluetooth now

:p

---

### Post by KLineD on 2005-12-22
Hey, there's no shame in going back to Windows. I did that several times in the past until I tried Ubuntu, now I have never looked back. I even got some of my friends and coworkers to try GNU/Linux and some of them also adopted it as their preferred OS.

The very beauty of GNU/Linux is that you have a choice about things. Don't like nautilus? Try Kubuntu, or XFCE (Xubuntu?? I don't know if that's the name) and there are many more I sure you can find one that suits you.

---

### Post by futz on 2005-12-22
[QUOTE=Kindred]Hey, thanks for the replies.  I didn't know about the middle button thing, thanks for that.  The mouse speed is still an issue as are Nautilus' shortcomings but i'll keep going..[/QUOTE]
Nautilus is pretty damn clumsy compared to windoze explorer, but I got used to it. To do some things you're used to doing easily in a single explorer,  you have to have 2 nautilus windows running side by side and drag/drop from one to the other.

Ah well, like all things in linux, it's always improving. Slowly but surely...

---

### Post by estel on 2005-12-22
What alternative FMs are out there in the repositiories at the moment that people use?

---

### Post by Kindred on 2005-12-22
[QUOTE=KLineD]Hey, there's no shame in going back to Windows. I did that several times in the past until I tried Ubuntu, now I have never looked back. I even got some of my friends and coworkers to try GNU/Linux and some of them also adopted it as their preferred OS.

The very beauty of GNU/Linux is that you have a choice about things. Don't like nautilus? Try Kubuntu, or XFCE (Xubuntu?? I don't know if that's the name) and there are many more I sure you can find one that suits you.[/QUOTE]

Yeah, the thing is, XP/2000 have run almost flawlessly for me for years.  I don't run any anti virus/spyware at all and I have had no problems at all.  My system under XP completely crashes perhaps once a year on average.  I don't mind Microsoft.   

but,

I wanted to at least try to take advantage of my 64bit system
I don't like the way Windows and DRM are heading
I wanted something lighter and less bloated, I get the feeling Vista will be more bloated than anything
I wanted a change
Few other reasons I can't think of right now.

I'm just a little underwhelmed at the minute but i'm determined to like it. :)

---

### Post by estel on 2005-12-22
>  I wanted to at least try to take advantage of my 64bit system

Windows x64 is working great ;).

> I wanted a change

No harm in sticking with dual boot then? :)

---

### Post by John Nilsson on 2005-12-22
> 'List View' (Windows style) is easily the best way to view files for me. Nautilus version is more like 'details', and it's still not as good because you can't do any kind of region selecting? Is there anything better than Nautilus for Gnome? In general I don't really like it.

In a nautilus window: Edit->Preferences >> "List Columns" tab (Also pay atention to the "Views" tab)


> Right clicking and dragging files/folders in windows allows me to 'copy/move/create shortcut', this kind of thing is useful. Maybe you have to add a script or something to do this kind of thing?

Besides the middle mouse mentioned you can can press Shift+Ctrl before releasing the mouse button to create a link. Make sure to read the help section about basic use: System->Help >> Desktop->User Guide->Basic Skills


> Mouse speed is pretty slow even at full sensitivity. I really need to speed this up, any ideas?

If you mean that you have the Sensitivity slider in System->Preferences->Mouse >> "Motion" tab all the way to the right I guess that you actually want to play with the Acceleration slider. I have attached a screenshot of how I've configured it with an MX 510 mouse.


> No integrated search in Nautilus? I don't understand.. 

This might be a Dapper only feature, but Ctrl+F in my nautilus brings up a search interface.


> Those gnome panels.. I can't seem to add my own separators between things/icons. I've seen some screenshots with seperators but I can't figure it out.


I think this is done with [this]("http://www.gnomefiles.org/app.php?soft_id=298"). I couldn't reash the project page though, and it isn't availble with synaptic either.

---

### Post by Kindred on 2005-12-22
[QUOTE=John Nilsson]In a nautilus window: Edit->Preferences >> "List Columns" tab (Also pay atention to the "Views" tab)

Besides the middle mouse mentioned you can can press Shift+Ctrl before releasing the mouse button to create a link. Make sure to read the help section about basic use: System->Help >> Desktop->User Guide->Basic Skills

If you mean that you have the Sensitivity slider in System->Preferences->Mouse >> "Motion" tab all the way to the right I guess that you actually want to play with the Acceleration slider. I have attached a screenshot of how I've configured it with an MX 510 mouse.

This might be a Dapper only feature, but Ctrl+F in my nautilus brings up a search interface.

I think this is done with [this]("http://www.gnomefiles.org/app.php?soft_id=298"). I couldn't reash the project page though, and it isn't availble with synaptic either.[/QUOTE]

Thanks, i've played with Nautilus quite a bit but its 'list view' is not really what I want.  I might try rox-filer in a minute though.

Ahh.. that way of configuring the mouse is much better.  Great.

I also figured out a workaround with gnome-ppp and I can live with that for the moment, so I am getting there. 

thank you.

---

### Post by bscbrit on 2005-12-22
My sig says it all..

---

### Post by TimelessRogue on 2005-12-22
Well, Kindred, you've now witnessed another reason NOT to switch back ... back-and-forth occassionally, yes ... but not back permanently.  These forums are the very foundation of a superbly supportive group of peers ... if you want to know something about Ubuntu or Linux in general, this is where you will find it.  And help?  I don't think you'll be able to come up with a problem that you won't find an answer for here.

Now that said, I have to admit I suffered the same insecurities of unfamiliarity when I first began with Linux back in the early RedHat days, experimented with a couple of different flavors as time passed and finally took up with Ubuntu.  I DID bounce back and forth in the beginning ... to the point of making myself dizzy with wondering which I was using.

But no longer ... I'm here and I'm staying here.  I have yet to find something that I can't do in Linux that I used to be able to or actually needed to do with MS.  Oh, I know that doesn't hold true necessarily 100 percent but sufficiently so for my needs and the needs of most others.  And at far less overhead both financially and with system resources.  One of the neat things, too, is that you (or someone) can tweak to your hearts' content to make your own system work the best for you ... without violating any licensing or purchase agreements.

So welcome ... hope you stick around ... dual boot for a while 'til you are totally comfortable before switching for good ... come back for help if you need to ... you'll find no shame in that around here ... and plenty of support ...

Oh, and Kindred?  Check out some of the other threads going in these forums ... you'll find more of the same supportwise and informationwise ...

---

