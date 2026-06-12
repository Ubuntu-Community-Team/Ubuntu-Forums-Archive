---
title: "help  . . .  lost unity, taskbar, blank desktop  . . . ."
date: 2011-05-29
forum: Any Other OS
---

### Post by daveinuk on 2011-05-29
Hello folks  . . .  bit of a disaster lol  . . . .  basically i wanted to enable some of the extra effects, 3d cube, wobbly windows etc, went to the ubuntu blog and found the command to enable the compiz settings manager, did that ticked a few boxes, then the taskbar at the top went 'funny'/ random pixels/black, had some messages in compiz saying this and that weren't compatible, sorry the exact messages escape me now it all happened so fast. . . ..  

next thing i know, i restarted thinking it'd recover and i have nothing but the desktop background ! right click won't give me anything useful and i don't  know how to get the terminal up ? 

i found this command on the ubuntu site   -  but can't get the terminal up, so i'm lost ! I'm on lenovo T61 laptop dual booting with mint 11rc if that helps . . . . . 
unity --reset

---

### Post by linuxinstalledfromhdd on 2011-05-29
can you outline for us just exactly what you were doing with your system prior to this malfunction happening on your computer?  Have you made any changes to your system recently? Did you upgrade to 11.04 recently?

---

### Post by daveinuk on 2011-05-29
I literally bought the laptop a week ago, had win 7 on it and i bought it to use linux on as my main laptop, i have a t42 with mint on also, i installed mint 11rc, then ubuntu, basically i wanted to alter the icon sizes in the unity bar down the left side to make them smaller so i searched the ubuntu forum, found a 'how to' and set about doing it. 

while i was there i thought i may as well try some of the extra effects as they worked fine on my other laptop, 3d cube, wobbly windows etc, as i was ticking the extra settings the messages came up as to compatibility, didn't really understand the terminology so i guess i've maybe checked or unchecked some bad combination! 

there have been no mods to the machine as such it's a pretty bog standard 1.8ghz (i think) processor so i assumed it'd handle the extras ok as my other is not as good as this and it works fine. 

thank you

---

### Post by linuxinstalledfromhdd on 2011-05-29
Ok, hang in there for a while..  I'm going to bump this message. It might take some time for someone who has had this exact same thing happen to them.

BUMP!!!

---

### Post by daveinuk on 2011-05-29
No problem ;)

I've got my other laptop and a pc so i'm not short of a machine to use lol . . . .  up until this i was really impressed with the new layout and just getting used to it, only just got my bookmarks,passes and email sorted out so it'd be a pain to have to reinstall the whole OS all over again ! hopefully some clever person out there can help me get my desktop back !

---

### Post by wildmanne39 on 2011-05-29
> **daveinuk said:**
> Hello folks  . . .  bit of a disaster lol  . . . .  basically i wanted to enable some of the extra effects, 3d cube, wobbly windows etc, went to the ubuntu blog and found the command to enable the compiz settings manager, did that ticked a few boxes, then the taskbar at the top went 'funny'/ random pixels/black, had some messages in compiz saying this and that weren't compatible, sorry the exact messages escape me now it all happened so fast. . . ..  

next thing i know, i restarted thinking it'd recover and i have nothing but the desktop background ! right click won't give me anything useful and i don't  know how to get the terminal up ? 

i found this command on the ubuntu site   -  but can't get the terminal up, so i'm lost ! I'm on lenovo T61 laptop dual booting with mint 11rc if that helps . . . . . 
unity --reset
Hi, below this text in my signature it says reset unity or compiz,click on it and follow the instructions for resetting unity.

---

### Post by silkworm2.5 on 2011-05-29
you cant get a terminal up with alt+f2 or ctrl+alt+T? I know that whenever I enable new plugins in compiz unity crashes, but I always opened up a terminal and typed in "unity --replace".
Can you make a launcher on the desktop? If you can, make the command unity --replace and launch it. 

Last resort I can think of is to login to Ubuntu Classic (option at the login screen) and from there run "unity --reset"

---

### Post by daveinuk on 2011-05-30
Update: 

Somehow  . . .  I've got my desktop back :) 

I couldn't get a terminal up no matter what i tried, the shortcut keys weren't working in this instance for reasons unknown to me . . . .  so, I rebooted into safe mode and got back in to the classic? menu style, from there i went into compiz and unticked the boxes with the extra effects and then got the actual prompt to revert to the classic desktop, so i did. 

At that point i shutdown after going back to the 'basic/old style' look although I really liked the unity look. 

I went out for the day then and after starting the laptop up tonight . . .  it's all back to how it was ??? lol 

I don't know how, sure i'll find out one day  . . .  but for now what I think i need to know is how can i tell if this laptop is suitable for those effects?

 It would seem odd if this couldn't run them as my older cheaper t42 does !

---

### Post by daveinuk on 2011-05-30
mmmmm this is getting odder  . . . . . 

after getting it back to normal i thought i'd just try and see what i'd done last time, so in compiz i adjusted the icon sizes for the unity menu, that all went fine, when i adjusted some more of the settings it all started going pear shaped again ! so i've ended up opening the terminal and doing unity --replace and at this moment it's back to normal (for now lol)

this is the output from that if it helps?  I also took some screen shots to better explain what is happening which i'll upload shortly  . . . . . 

dave@dave-ThinkPad-T61:~$ unity --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing move options...done
Initializing grid options...done
Initializing mousepoll options...done
Initializing place options...done
Initializing session options...done
Initializing resize options...done
Initializing unitymtgrabhandles options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing animation options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing fade options...done
Initializing scale options...done
** (<unknown>:3820): DEBUG: Unity accessibility initialization
** (<unknown>:3820): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1440x900

** (<unknown>:3820): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:3820): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:3820): DEBUG: PlaceEntry: Applications
** (<unknown>:3820): DEBUG: PlaceEntry: Commands
** (<unknown>:3820): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:3820): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:3820): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:3820): DEBUG: Setting to primary screen rect: x=0 y=0 w=1440 h=900
** (<unknown>:3820): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


(<unknown>:3820): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:3820): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:3820): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:3820): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:3820): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:3820): DEBUG: IndicatorAdded: libme.so
** (<unknown>:3820): DEBUG: IndicatorAdded: libsession.so
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "flip_left_edge"
Setting Update "panel_opacity"
Setting Update "icon_size"

---

### Post by daveinuk on 2011-05-30
screen shots  . . .  notice the top bar and occasional missing icons ! I did get wobbly windows working at one point but didn't try desktop cube, looks like i might have to settle for it with less effects if the machine's not geared up for it ? 

[IMG]http://i64.photobucket.com/albums/h183/purpled_01/Screenshot-5.png[/IMG]


[IMG]http://i64.photobucket.com/albums/h183/purpled_01/Screenshot-3.png[/IMG]

[IMG]http://i64.photobucket.com/albums/h183/purpled_01/Screenshot-2.png[/IMG]

[IMG]http://i64.photobucket.com/albums/h183/purpled_01/Screenshot1.png[/IMG]

[IMG]http://i64.photobucket.com/albums/h183/purpled_01/Screenshot.png[/IMG]

---

### Post by daveinuk on 2011-05-30
I also saw another post just now from someone with a T41 with similar problems and then discovered I have optional grahics drivers available to me, so I've installed the recommended one but i won't attempt any more fiddling with these graphics until someone gives me the nod ! :)

---

### Post by silkworm2.5 on 2011-05-30
On my unity I had to run the command "unity --replace" after activating or deactivating any effects in compiz. I managed to get reflection, wobbly windows, and several other special effects running that way.
I would recommend you make a launcher on your desktop to re-start unity anyway if your gonna use it.
Just right click the desktop, click on 'Create Launcher' and type in the command field 'unity --replace' I am never gonna forget that command, I use it so much >.>

About the graphics drivers, do you know what graphics card you have? If you don't know, use the command "_lspci_" in a terminal. In the output should be a line similar to: "00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)" (That's mine at least.)
Your after the line beginning with "VGA compatible controller"
Then try googling for the drivers.
Also keep in mind that there may be personal package archives (PPAs) that can simplify driver installation.

---

### Post by wildmanne39 on 2011-05-30
> **daveinuk said:**
> I also saw another post just now from someone with a T41 with similar problems and then discovered I have optional grahics drivers available to me, so I've installed the recommended one but i won't attempt any more fiddling with these graphics until someone gives me the nod ! :)Hi, I have the cube in natty with several effects I went crazy as usual. I will give the link for the guide also you will have to tweak a few setting to make it smooth,mine lagged so I change a few setting like refresh rate. [http://ubuntu4beginners.blogspot.com...ty-ubuntu.html](http://ubuntu4beginners.blogspot.com...ty-ubuntu.html) after you have the setting for the cube installed from the first link then go to the second link. Hi, follow this guide for setting up the burn and such, when you change settings your windows will get messed up just log out then back in and it will fix it just do not disable the unity plugin.You also need to intall ccsm in synaptic with all plugins including fusion. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by daveinuk on 2011-05-31
Thanks for the replies guys, i tried lspci and got this back - 
01:00.0 VGA compatible controller: nVidia Corporation G84M [Quadro NVS 140M] (rev a1)

one of my previous posts did mention that there was a better driver available which i installed, i did try to follow some of the posted links, one didn't work but i had a crack tweaking around and it's just not having it lol  . . . . .  i keep getting back to the lost desktop scenario  but i do now have wobbly windows so that'll just have to entertain me! it was only to see if the extra effects work better on this than the previous machine, not something I'd use every day but it was handy, I do like the look of this as it is so i'm going to stick with it for a while as it's working fine now and i'd rather have a working laptop than a series of headaches ;)

I'll get used to the new layout before i fiddle any more but i have learnt a lot already in a short space of time about unity so it's not been a wasted effort, thanks again for all the replies, i'll mark me as 'fixed' for now :p

---

### Post by Perfect Storm on 2011-06-01
Moved to Other OS/Distro Talk.

---

### Post by BALD PATCHES on 2011-07-22
[SIZE=2][COLOR=Red][B]I lost my unity desktop while tinkering with compiz settings also....couldn't access anything!!!
[/B][/COLOR][/SIZE]
[CENTER][SIZE=3]**[COLOR=SeaGreen]CTRL+ALT+F2 = logout[/COLOR]**[/SIZE]
[SIZE=3]**[COLOR=SeaGreen]enter login details[/COLOR]**[/SIZE]
[SIZE=3]**[COLOR=SeaGreen]enter "unity --reset"[/COLOR]**[/SIZE]
[SIZE=3]**[COLOR=SeaGreen]CTRL+ALT+DELETE for a reboot[/COLOR]**[/SIZE]
[/CENTER]

[SIZE=4][I][B]It's that easy!!!
[/B][/I][/SIZE]

---

### Post by Morty007 on 2011-08-20
I just want to add that I had this problem as well, just a blank desktop, no launcher or anything and I could not get a terminal up. It happened while in CCSM.

---

