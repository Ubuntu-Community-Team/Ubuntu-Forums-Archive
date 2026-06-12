---
title: "How can I add the &quot;Workspace Switcher&quot; back to my panel?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-11-17
Hello, I lost my panels a few weeks pack and I was able to replace everything except the "Workspace Switcher" (the four squares).

It is not in xubuntu panel list for add ons.

I would like to know how to add the Firefox icon/launcher back to the top panel also.

Thank you,
-c.

---

### Post by crimesaucer on 2006-11-18
Four Squares on bottom panel?

---

### Post by Pudwud on 2006-11-18
Misunderstood question.

---

### Post by sgstarling on 2006-11-18
In Ubuntu:
To add the Firefox icon back to the top panel: go to Applications:Internet, then just left click drag'n'drop Firefox to the panel. 

Should be similar to xubuntu?

---

### Post by anaconda on 2006-11-18
right-click to an empty place in your panel and select add and from there workplace-switcher

And by the way you dont really need it. You can also use Ctrl-Alt and left or right arrows

---

### Post by crimesaucer on 2006-11-18
Well, "Workspace Switcher" is not on the list of my "add to panel" menu.

I'm actually fine without it, but I just installed "beryl" and I was thinking I would need the "Four Square" workspace switcher on my lower panel to have the "cube" and to be able to spin the cube properly.

Edit** Applications-->--Internet is not on xubuntu. I have a drop down menu that has Network-->--Firefox but that is unable to be drag and dropped to panel. I also tried to goto usr/share/x11/Firefox and add the launcher to desktop and then to panel, but that didn't work either. Don't worry though, it's only a little icon and as long as it's in my menu list, than it's cool.

---

### Post by CatKiller on 2006-11-18
If Beryl in Xubuntu is like Beryl in Ubuntu, you won't get four squares, anyway. You'll get a long oblong. I haven't used Xubuntu enough to know how to add the Workspace Switcher back though, I'm afraid.

As anaconda says, you don't need the switcher to switch faces on the cube. Ctrl-Alt left & right, same as normal, or scrolly mouse wheel on a blank patch of desktop, or Ctrl-Alt click-and-drag on a blank patch of desktop. And there's the Scale plugin for showing all your open applications at once, which will spin the cube round to the one you select. And probably others that I haven't noticed yet.

EDIT: The Xubuntu workspace switcher appears to be called "Pager".

---

### Post by rkn5555 on 2006-11-18
i too have that same problem , the first time i got beryl working, i was able to rotate cube.. then not too sure when it happened but i have the same problem as you. the workspaces turned into a single rectangle in the bottom right corner of task bar. and i am no longer able to rotate cube.
i cant find an answer either after 3 days of searching all over the place.

also i see alot of the same responses from people  that do not understand that you need the workspaces available, in order for the cube to rotate. i feel that the cube does not rotate , because it knows that there is only one workspace, so why rotate? as in the post above, i can try to do all the things to try and rotate cube, it doesn't rotate. and Yes, i have it enabled in beryl manager settings
Right click on the area of desktop spaces. in bottom right corner of task bar and click preferences. then you can change how many workspaces you want. but take a look in the box below. no new workspaces show up. 

you can quit beryl window manager and go into you regular gnome desktop and right click on the workspaces go to preferences and you will be able to add and subtract all the workspaces you want and it works. but once you go back into beryl, it goes to a single workspace.

this is the one thing that im upset about. I have everything else working fine, printers , everything.

---

### Post by CatKiller on 2006-11-18
> **rkn5555 said:**
> this is the one thing that im upset about. I have everything else working fine, printers , everything.

You should be very pleased, since everything important works. Beryl should be considered extremely experimental, and is there for play.

As I understand it (which is not at all, really) you don't need the display to show four seperate squares in order to rotate the cube - I think it is **supposed** to be considered a single wide workspace in order for the effect to work. Certainly when I enabled it in Gnome, it claimed that there was only one workspace, and the cube still works.

You can, I think (I'm away from the computer with Beryl on at the moment) click on the section of the wide wokspace to choose which face you want to see. Or use one of the other, cooler methods to turn the cube. I removed the workspace switcher because I found I never needed to use it.

If none of the methods for turning the cube work for you then you probably haven't enabled it properly. Sorry.

---

### Post by d3v1ant_0n3 on 2006-11-18
> **rkn5555 said:**
> i too have that same problem , the first time i got beryl working, i was able to rotate cube.. then not too sure when it happened but i have the same problem as you. the workspaces turned into a single rectangle in the bottom right corner of task bar. and i am no longer able to rotate cube.
i cant find an answer either after 3 days of searching all over the place.

also i see alot of the same responses from people  that do not understand that you need the workspaces available, in order for the cube to rotate. i feel that the cube does not rotate , because it knows that there is only one workspace, so why rotate? as in the post above, i can try to do all the things to try and rotate cube, it doesn't rotate. and Yes, i have it enabled in beryl manager settings
Right click on the area of desktop spaces. in bottom right corner of task bar and click preferences. then you can change how many workspaces you want. but take a look in the box below. no new workspaces show up. 

you can quit beryl window manager and go into you regular gnome desktop and right click on the workspaces go to preferences and you will be able to add and subtract all the workspaces you want and it works. but once you go back into beryl, it goes to a single workspace.

this is the one thing that im upset about. I have everything else working fine, printers , everything.

My pager works fine in xubuntu AND ubuntu-rotates my cube and everything. Beryl uses viewports rather than workspaces, as I understand it. The viewports are just one long desktop divided into 4 pieces (by my understnding)-hence the long oblong in Ubuntu's pager. You can still rotate the cube by either manually rotating (default CTRL+ALT+Mouse 1+Movement) or  the normal way (CTRL+ALT+Left or Right Cursor Key).

---

### Post by rkn5555 on 2006-11-18
Edited: dont pay attention to below. i hope others find this post...

you are right, beryl manager settings were not correct.

here is why, in settings i have the "Desktop Cube" checked..enabled..

so i figured that was the only setting concerning a cube..So then On the left window pane, Scroll down near the bottom , and 
you will see a Setting to ROTATE cube.
make sure you check that as well. 

ill post to beryl, that i believe ,if that you have put windows on a cube , enabled, then the cube should by
default Rotate. 
does that make sense to you guys? 

thanks for the rapid respones.

i have checked and it is set up properly to rotate.

ok, i understand the theory on viewports.

when i manually try to get it to rotate. using the
TRL+ALT+Mouse 1+Movement) or the normal way (CTRL+ALT+Left or Right Cursor Key).
that does not work. and thirdly, when i drag a window across the desktop and over the "edge" the cube does not rotate.

it used to do that when i first installed.

here is another, when i right click om a tiltle bar and choose .. move to another viewport.
the app does leave current viewport , and is represented in the wokspaces box in task bar.

but even then when i try to click on the area in workspace window, nothing happens. i can not get to that app.

hopefully others read this with similar problem and fix.

---

### Post by crimesaucer on 2006-11-19
Hello, I added "Pager" and I still did not get the four squares back, but I did get a small rectangle that shows applications running on the desktop workspace. And I also was able to use the cube and rotate cube with the commands on the beryl wiki page. And yes, the "rotate cube" should be checked as default and I think the "animations" shouldn't be default because some low grade  computers (like mine) can't really work well with all of the effects running, but as far as the nice window themes and the cube and hot corners, beryl is working nicely.

Now I have a new question about beryl since this thread sort of became a beryl thread, does the cpu usage being higher cause the temperatures to be hotter and possibly bad for my computer. I use xubuntu 6.10 on a hp pavilion dv4230us Intel Celeron M, with the 910 chipset and an Intel Media Accelerator 900 internal graphics card.

Is there a package I can install to monitor my CPU temperatures while I'm using my computer and also create a report on how hot my computer has ran after a session, like a graph to show temperature ranges and CPU usage.

Thanks.

---

### Post by rkn5555 on 2006-11-19
i believe you cant, while running beryl,its not neccesary.
in the workspace rectangle area. when you have open apps running on other desktops"viewports" they show up in the workspace area , spread out along the rectangle, you can click on them and youll be rotated over to the desktop.


and for your cpu question, 
yes if your cpu is running at higher usage , heat will build up , but for the most part you are still in safe operating ranges. as long as your cpu fan along with other fans and ventalation arent clogged up with dust.
you should be fine. i havent looked around yet in ubuntu for a cpu monitor, but im sure if you look around youll find one, go to synaptic in your admin area. type cpu in the search , seee what happens.

---

### Post by crimesaucer on 2006-11-19
The place where I'm staying is very very dusty. I hope that's not the problem.

---

### Post by rkn5555 on 2006-11-19
im presuming you know how to open up the case ,
two things i do, one is get a can of pressurized air.
and blow out your fans , power supply and other vent holes in the case.

or i ve used a vaccum with the soft bristle brush attatchment.

---

### Post by crimesaucer on 2006-11-19
I'm very new to computers, I've only owned a computer for the last year. So would this be possible with a notebook? And I can't seem to find a CPU temp and hard drive temp gauge in synaptic, I tried the gnome deskletts for cpu and memory but they were very buggy, and I tried a few other packages but none of them worked with my xfce and beryl xubuntu edgy. 

I guess I could check over on the xubuntu site's.

Thanks for the help anyway.

---

### Post by CatKiller on 2006-11-19
> **crimesaucer said:**
> And I can't seem to find a CPU temp and hard drive temp gauge in synaptic, I tried the gnome deskletts for cpu and memory but they were very buggy, and I tried a few other packages but none of them worked with my xfce and beryl xubuntu edgy.

I don't know if [this page]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29") will point you in the right direction. I think it was lm-sensors that I installed for my gnome-panel temperature display on a computer that has neither Beryl nor Xubuntu on. I'd imagine that you might need to do something slightly different.

Also, people have been posting pictures of their Conky setups, that display all sorts of information on the desktop. I haven't tried it myself, though.

---

### Post by rkn5555 on 2006-11-19
> **crimesaucer said:**
> I'm very new to computers, I've only owned a computer for the last year. So would this be possible with a notebook? And I can't seem to find a CPU temp and hard drive temp gauge in synaptic, I tried the gnome deskletts for cpu and memory but they were very buggy, and I tried a few other packages but none of them worked with my xfce and beryl xubuntu edgy. 

I guess I could check over on the xubuntu site's.

Thanks for the help anyway.
no , you dont want to open up your notebook,
when using thie notebook, make sure that it is not on something soft. like a couch or on your lap.you want it to be on a hard surface so that the heat can escape.

i dont feel that you are going to overheat the cpu just from running beryl.

laptops feel hot all the time, even when your not pushing it to the limit

---

### Post by crimesaucer on 2006-11-20
Cool, thanks, I'm probably just being a hypochondriac.

As for the lm-sensors, I looked at it in the wiki, and also thought about it in synaptic, but I wasn't sure about it. 

I didn't want to install it until I found out if it was compatible with xubuntu 6.10, Beryl, and my hp pavilion dv4230us Intel Celeron M, 910 GML chipset.

I also didn't know how it would be as a program, would it be graphs represented as deskletts, or would it be a separate program and in my menu's list? 

I always see CPU, swap, memory, and temperature graphs on screenshots of people's Linux desktops, and that is what I was trying to get.

---

### Post by CatKiller on 2006-11-20
> **crimesaucer said:**
> I also didn't know how it would be as a program, would it be graphs represented as deskletts, or would it be a separate program and in my menu's list? 

I always see CPU, swap, memory, and temperature graphs on screenshots of people's Linux desktops, and that is what I was trying to get.

I don't think it displays anything on its own. I could be wrong, but I think it is just used by other programs to find out the sensor information. Like the Hardware Sensor Monitor that I've got on my panel.

It's probably worth starting this question as a new post, since the title's not appropriate to this question anymore, and so that you get a new set of eyes looking at it. I've only done this once, it was a while ago, and I can't remember how I did it.

---

### Post by crimesaucer on 2006-11-21
I will, thanks for the help.

---

### Post by rare HERO on 2008-05-01
I made the same mistake of 'losing it'.

As mentioned previously, it is called 'pager'
[http://ubuntuforums.org/showthread.php?t=678872](http://ubuntuforums.org/showthread.php?t=678872)

---

### Post by crimesaucer on 2008-05-02
> **rare HERO said:**
> I made the same mistake of 'losing it'.

As mentioned previously, it is called 'pager'
[http://ubuntuforums.org/showthread.php?t=678872](http://ubuntuforums.org/showthread.php?t=678872)

This post was from my first month on xubuntu back in the fall of 2006, when I first got into Beryl 1.1... I didn't have much of a clue about anything Linux.

---

