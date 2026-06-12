---
title: "64-bit menubar of hate"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Magiclamp on 2006-08-09
This is _week two of using Ubuntu_ (as well as Linux) at all, so please bare with me if I sound like an indiot. 

I am a **AMD 64-bit** user, and I know that there are quirky things about Ubuntu that require a little bit of tweaking in order to get them to work. Here are some things I haven't been able to find fixes for, or haven't got to work correctly...or are just plain weird! Any input would be much appreciated! 

The first issue I have, is that I have a permanent **menu-bar**. **(refering to the macintosh-like menu bar at the very top of the screen... with file, sessions, new, ect. tabs on them. It is an optional checkbox in the settings.)**. I cannot get rid of it now. I am almost getting used to it, but I hate that thing, haha. 

The second issue I am having is that I **cannot set-up file-sharing**. When I click on the "Administrator Mode" button to try and setup shared folders, my password box pops up...I input my password...and then nothing happens. I am unable to configure those settings, even though I have supplied the root password. I know that there is a command line to do this, but as I mentioned earlier, I am a first time linux user. The command line is still very new to me...and although I have a debian linux help command list as a PDF to study...I can't figure this out. **This also happens on another computer I have which is not 64-bit. **

Another issue is that **Blender does not work**. I think I need a 32 bit version, but I am unaware of how to get a copy or whatnot. Can it run on 64-bit? My slower computer, which also runs off of Kubuntu runs it okay. 

Also, I was a heavy movie-watcher on my windows computer. My computer has always been my television, and multimedia station. (I am even a musician, and I do all my recording on the computer.) I converted to linux because my brother thinks I am a loser for being such a windows user, and I wanted to learn something new...but now I feel very limited. My **movie files are not working**, and I cannot find out why. The torrent files I have downloaded won't extract because they are in **RAR format and my computer doesn't have something to extract them with**. 

Once I do get these things working, I would also like to start creating music again. Are there any good packages for studio environments? Are there any programs available with good samples and abilities to make drum-loops and patterns as well as record? I would hate to install windows on another dirve on this computer, just for my music stuff. (I want to go linux all the way eventually!) 

Anyways, if you can help you are awesome. I am at a loss at getting things going correctly.

---

### Post by o_fortuna on 2006-08-09
I can't help you with everything. For your first issue, I really don't understand what you mean. Maybe you could attach a screenshot (press the PrtScn button on your keyboard, which is to the left of F12)?

Sorry, I can't get filesharing to work properly either, and I don't use Blender.

If you want movie files and RARs to work, use Automatix ([http://www.getautomatix.com/]("http://www.getautomatix.com/")). Automatix can "automatixally" install RAR support and support for some movies.

Finally, I guess you could check out Ubuntu Studio ([http://ubuntustudio.com/wiki/index.php/Welcome%2C_Musicians%21]("http://ubuntustudio.com/wiki/index.php/Welcome%2C_Musicians%21")).

---

### Post by Magiclamp on 2006-08-09
The menu-bar in question is at the very top of the screen.. [IMG]http://www.workhurtsme.com/snapshot1.png[/IMG]

I will try automtix right now and see how that goes. Thank you for the lead on Ubuntu studio! I am going to check out all that stuff! 

Is it just a general problem with file-sharing with Ubuntu?...or something specific to 64-bit? I have to get networking to happen somehow.

---

### Post by bhoughton on 2006-08-09
Sorry that the menu bar won't go away.  Have you tried switching the setting to one of the three different options, system, app or none?

As for Blender, you might check out the forums on [http://www.blender3d.org](http://www.blender3d.org)

I believe that automatix installs RAR decoders if you choose.

---

### Post by Magiclamp on 2006-08-09
I am not sure what you mean by system, app or none. I have scoured the settings for the taskbar and other spots for any way to remove/change the bar, and the best I can do is change it's color to match the lower bar, haha. I am not sure what made me enable this mysterious bar, but I wish it could be taken off. 

I am not figuring out the Automatix installation. I have tried adding the entry to my sources using a text editor, and when I tried to save it, it said I didn't have permission. :-k 

*****
The Ubuntu Studio is cool though! Some of the programs do not work because I need to tweak the settings and some 64-bit difficulties...but I have found a few beat programs, which is always fun.

---

### Post by Jjohn on 2006-08-09
Hi Magiclamp,
            I too had some real issues with the 64bit distro.
 I resolved it by installing the regular 32bit 386 intall disc
            Now nearly everything works ncluding blender, I am too much of a newbie to help you with anything else but if you get blender to work will you pm me please?
regards John

---

### Post by bhoughton on 2006-08-09
Been a while since using KDE, but if memory serves, there is an option in the KDE Control Center for either Appearance/Theme or Look/Feel.  Seems like one of the options regarding windows deals with choosing a menu bar, either system, app or none.

I am planning to install KDE desktop soon...

---

### Post by o_fortuna on 2006-08-09
> **Magiclamp said:**
> I am not sure what you mean by system, app or none. I have scoured the settings for the taskbar and other spots for any way to remove/change the bar, and the best I can do is change it's color to match the lower bar, haha. I am not sure what made me enable this mysterious bar, but I wish it could be taken off. 

I am not figuring out the Automatix installation. I have tried adding the entry to my sources using a text editor, and when I tried to save it, it said I didn't have permission. :-k 

*****
The Ubuntu Studio is cool though! Some of the programs do not work because I need to tweak the settings and some 64-bit difficulties...but I have found a few beat programs, which is always fun.
So if you're running Kubuntu, here's the "good" way of adding automatix in for KDE:

   1. Start Adept by choosing K Menu->System->Adept (Package Manager) from the Desktop menu system.

   2. Select View->Manage Repositories in the Adept package manager window.

Then just click add, I think, and insert the line

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) kubuntu main

Like Jjohn mentioned, and as I've done, the regular i386 version seems to be better suited for everyday use now, so you might consider switching to that if you continue having troubles.

---

### Post by Magiclamp on 2006-08-09
Well, I installed automatix (by the way, thanks a lot for the Adept help! :D  ) But I still can't unrar. Maybe I am not doing something right? What program do you recommend extracting with? I am trying with Ark currently. My video files aren't working either. *This is dampering my enjoyment of my talladega nights torrent download. :cool:

---

