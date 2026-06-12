---
title: "An Idea for the developers"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by BLTicklemonster on 2005-10-09
I'm new to all this, and being so, I'm a bit gullible when I see advice in a forum to do something like, oh heck, I don't know I think it was "press ctrl+alt+backspace" or something like that. Boom, no x server, no idea how to get back. This has happened to me twice, and I'm pretty sure I did it a different way the second time. Yes, I reinstalled ubuntu the first time, but this time, I have the hard drive it's on sitting there waiting for me to figure out how to bring it back up in x server or whatever.

CAN YOU AT LEAST PLEASE, IF ANY ONE IS GOING TO BE DOING SOMETHING LIKE THAT, AT LEAST HAVE A MICROSOFT TYPE PROMPT ASKING IF WE UNDERSTAND WHAT WE'RE DOING, MENTIONING THAT ONE MAY NOT BE ABLE TO GET BACK TO THE DESKTOP IF ONE HAS NO EARTHLY STINKING IDEA WHAT ONE IS DOING? (that would be me)

This is close to getting me to give up and crawl back under my window. 

(if I were admin, I'd search ever instance that does this, and take the time to copy and paste a warning in every post that had any information that would totally goob up somebody)

I think that covers everything.

---

### Post by cbudden on 2005-10-09
That *should* restart it aswell, but for future reference, press alt-F2, type killall gdm, then type gdm and your back.  Or just restart.

---

### Post by matthew on 2005-10-09
Or, instead of putting the responsibility on everyone else, perhaps we as users and reasonably intelligent humans could take our appropriate level of responsibility and not choose to do things we don't understand until we understand them. When you don't understand something it is appropriate to ask a question and you are very welcome to do so in these forums. Don't be like this guy:

"I don't know what happened! I just pushed the pedal thing on the floor and the car ran into the tree."

"Did you try to turn the steering wheel or push the brake pedal?"

"What are those? Why does everything have to be so complicated? All I want to do is drive my stinking car!!"

---

### Post by madjo on 2005-10-09
Have you already tried restarting the computer? 
What ctrl+alt+backspace does is resetting your x-window environment. and under normal circumstances it should just restart right then and there, but in your case something went wrong. What were you trying to achieve with this ctrl+alt+backspace thing? :)

btw, these microsoftian "are you sure" prompts were one (of many) reasons why I left Windows.

---

### Post by BLTicklemonster on 2005-10-09
Restarting does no good, and Matthew, please, that's totally unrealistic. Don't go there.

I've been trying to get nvidia drivers installed since I got Ubuntu yesterday. I've yet to get them to install. Even the basic nv-glx won't install. 

When it boots, it goes and asks for my login and password, and stays at the command prompt. What would I possibly type after the ~/home/bill $ or whatever to bring it back up?

---

### Post by poofyhairguy on 2005-10-09
The person who gave you that advise forgot to tell you that the command:

startx

will bring everything back. (or yes, a reboot works too, its just the xserver)

Sorry they forgot to say that.

---

### Post by BLTicklemonster on 2005-10-09
Thanks, I'll attempt that.

---

### Post by matthew on 2005-10-09
[quote=BLTicklemonster]Restarting does no good, and Matthew, please, that's totally unrealistic. Don't go there.
When it boots, it goes and asks for my login and password, and stays at the command prompt. What would I possibly type after the ~/home/bill $ or whatever to bring it back up?[/quote] It was not my intent to annoy you, just to maybe help you consider another point of view. Anyway, probably enough has been said on that.

From the command prompt you can type this to get gdm running again.
```
sudo /etc/init.d/gdm start
``` 
I had a couple of thoughts about what might have occurred and thought I would add them as well. It is likely that you used
```
Ctrl+Alt+F1
``` to reach a command line. There are 6 virtual terminals available in a standard Ubuntu installation and you can reach them via this method, substituting F1-F6 for each of them. If you hit
```
Ctrl+Alt+F7
``` in any of them while an X session is running you will return to your graphic display.

---

### Post by BLTicklemonster on 2005-10-09
Thanks Matthew. Sorry I went off on you.

Here's what we're looking at so far:

tried startx, got more than this, but this is all that showed on the screen

(==) Log File: "/uar/log/XFree86.0.log" time blah blah blah
(==) Using Config File: "/etc/x11/XF86config-4 
data incomplete
at least one device section is required

(EE) Problem parsing config file
(EE) Error from XF86HandleConfigFile

Fatal Server Error:
no screens found

XIO: fatal IO Error 104 (connection reset by peer)
On x server "0.0"
after "0" request (0 knownd processes)
with 0 remaining

Now that is before coming back and seeing the sudo command. I'll try that. 
Won't be back tonight, unfortunately, I have a meeting in less than 30 mins. (unless it comes up, then I'll come in here with a basket of roses), and I work, tomorrow, so I won't be able to even mess with this until about 7 Eastern Time.

Wish me luck.

---

### Post by BLTicklemonster on 2005-10-09
sudo /etc/init.d/gdm start

gets me

[COLOR="Red"][FAIL][/COLOR]


So um, I think I messed up pretty bad.

Oh, and I can tell you that on the release I have, ctrl+alt+f1 and ctrl+atl+backspace totally mess you up and leave you with no apparent way to get back to x server. Yes, f1 was the other one I did. I recognize it.

I suppose I'll reinstall. I know most of the stuff I did, and where to find it. No big deal. I'll learn something from this. 

But wait a second, there's a new version out, that Breezy one.. should I install it?

---

### Post by poofyhairguy on 2005-10-09
Wait. Before you reinstall try this command:

> sudo dpkg-reconfigure xserver-xorg

Breezy isn't stable yet, so it might give you problems.

---

### Post by Kyral on 2005-10-09
Hold the phone....why was it going for the XF86Config file? Ubuntu uses XOrg....

Are you sure you aren't in Debian?

And you have to stop gdm ( sudo /etc/init.d/gdm stop ) before you can start it

---

### Post by BLTicklemonster on 2005-10-09
"sudo" dpkg-reconfigure xserver-xorg (gotta be root, ya know)

and I get xser-org is broken or not fully functional.

Thanks for following me over here, Hairy.

I'll wait.

---

### Post by BLTicklemonster on 2005-10-09
[QUOTE=Kyral]Hold the phone....why was it going for the XF86Config file? Ubuntu uses XOrg....

Are you sure you aren't in Debian?

And you have to stop gdm ( sudo /etc/init.d/gdm stop ) before you can start it[/QUOTE]


No idea, bro. Running hoary.

---

### Post by Kyral on 2005-10-09
okay try this one..

sudo apt-get remove xserver-xorg (Yes I know what this means...)

then sudo apt-get install xserver-xorg.

Maybe a reinstall will help

---

### Post by BLTicklemonster on 2005-10-09
Let's see. I just started the meeting, we usually chat for 30 minutes or so, then we hit the server... not may people are on, so I may be able to bail on practice... I'll be back in around 30 minutes and let you know if removing xserver and reinstalling it will work. I tried sudo apt-get xserver-xorg not knowing what else to put, of course it didn't do squat. Thanks.

(im in here and over there at the same time, lmao)

---

### Post by BLTicklemonster on 2005-10-09
Nope. Just came up telling me a ton of stuff it couldn't do.

So I took the hard drive out, stuck it in some boiling water, then put it in the oven with some gravy, let it cook for 20 mins at 400 degrees. Removed it, placed it carefully out in the driveway, then ran over it several times with my car, then the riding mower for good effect. Next, I took a railroad spike and a sledge hammer and nailed it to the telephone pole in front of the house, and pourd battery acid all over it. I held a marshmallow over the fumes for a few minutes until it started mmmmelting, mmmmelting, and went and fed it to the neighbor's dog. 

After he quit writhing in agony, I came back in and dropped an old hard drive in and started loading ubuntu back up. It was only after partitioning that I suddenly realized that the hard drive I was using was the one with the cold fusion reactor data on it that I needed because the reactor we had been using (at .05% efficiency) all summer to run everything in the house had been used by the neighbor's dog as a chew toy (you knew there had to be a reason, didn't you?). 

So now I'm stuck with Ga power for ever, because there's no way I can redo all that work again, what with the steel plate in my head and all...

So anyway, what would I rather have, the distinction of being the man who freed the world of fossil fuels and was wealthy beyond compare, or have Ubuntu up and running on my box? Yeah, me too. I think I'll go kick the dog for good measure.


Anyway, all kidding aside, I decided to heck with it and just reinstalled. Why beat my head against it? Of course it dawned on me a moment ago that I probably could have pressed esc while in the first part of booting and gone into recovery mode, but let's just forget about that for now, shall we? 

Doing an update because it says in the bar up there that there's updates, and lo and behold I get this error already:

E: /var/cache/apt/archives/gzip_1.3.5-9ubuntu3.4_i386.deb:  cannot access archive: No such file or directory

Imagine that. I haven't even done anything and I'm already messing up!!!

---

### Post by Kyral on 2005-10-09
chillllllllll

Okay, so this is a FRESH install of Ubuntu 5.04 Hoary, RIGHT? (Going through my "Stupid Obvious Tech Support Questions" list right now to make sure I know EXACTLY what you are dealing with).

You just hit "Enter" at the install boot screen? You did default everything?
What are your machine specs? Just tell me everything + the kitchen sink. I wanna try to help you dude :D

---

### Post by BLTicklemonster on 2005-10-09
Athlon xp2600
768 megs ddr
nvidia fx5200
16x dvd
16x dvdrw

Yeah, just dropped it in, and did a clean install. Updated. Went to the synaptic and installed some stuff like xmms of course.

But the thing I want the most is to get my video drivers in here. Both times I attempted to do it, I got fragged. (btw, you can get xmms and a ton of other stuff through synaptic... I wonder how many people know that?)


(thanks dude)

---

### Post by erikpiper on 2005-10-09
How did you try to install the Nvidia drivers? I have a desktop with an nvidea Geforce 4- I simply installed nvidia-glx with synaptic. It worked with hardware acceleration and everything.

Or if you prefer:
sudo apt-get install nvidia-glx

-----------------------------------------------------------------------------------------------------------
Of cource, I am not nearly as knowlegable as most here.. And I know nothing about your nvidea model.....

Good luck!

---

### Post by BLTicklemonster on 2005-10-09
I tried that once before and got an error, I'll see if it does it again.

woot woot, the unix gods are smiling on me now. It worked that time without an error. they must not like that dog either, huh?

The error I was getting looked as if it were saying that there was a problem with the file on the cdrom. apparently it's okay now.

and I was about to ask if this was okay to do:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

but never mind, I guess.

*edit:

the device manager is messing me up. it says

Vendor: nVidia Corporation

Device: NV34 [GeForce FX 5200] ( i hope I didn't say 5600 a little while ago, lol)

Status: status

Bus type: PCI

okay that messes me up right there. It's an agp card.

---

### Post by erikpiper on 2005-10-10
Wait- Cd rom? Huh? I always use the internet with synaptic...

So how is it working?

---

### Post by BLTicklemonster on 2005-10-10
Haven't installed and run ut yet, but everything else is working great. I'll post back tomorrow night, or tonight, actually. It's after one here!

---

### Post by BLTicklemonster on 2005-10-10
mess. I couldn't figure out how to uninstall ut, so over wrote it. and now it's gone  from my applications menu. Never have gotten it to start from clicking the -bin file, either, even with all three places checked in properties. So THEN I found uninstall, and am now installing it. It won't let me install it unless I'm root for some reason now. Does this mean it won't let me play unless I'm logged in as root when it's done? I'm soooo close now, and this happens!

*edit:
Never mind, I found this useful information which is now copied and pasted into a text file in my home folder:


Quote:
1. What is the command for deleting a folder. I know rm is to delete files but it won't remove the folder itself.

rmdir <folder name>
It will only delete empty directories though.
"rm" will delete a folder and all of its contents if you pass it the -r option:
"rm -r <folder name>

Quote:
2. Could someone briefly explain how to use the killall command successfully or point me to a informative tutorial. Certain programs spontaneously won't close and when I use the killall command the frozen prgram won't close.

Usage is "killall <task name>". Sometimes the task name is not the same as the window or program name, in that case find the correct one using the system monitor or "ps" on the command line.
There is also the gnome force-quit panel applet and "xkill", both will give you a crosshair cursor, left-clicking a window then will kill it.

Quote:
3. Using the terminal, how do you delete a program? Because I don't want to use xine-ui and xmms anymore.

sudo apt-get remove <package name>

---

### Post by BLTicklemonster on 2005-10-10
Oookay, now I can't install ut unless I'm root. and I can't play unless Im root. and it says that if i play as root, the user info will be pathed wrong. and when I try to play, it won't. 
it says this:

Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?


How can I get back to not having to be root? and why me? lol

---

### Post by BLTicklemonster on 2005-10-10
Okay, I'm going to try something totally radical.

Using the information from here: [http://www.ubuntuforums.org/showthread.php?t=67657&highlight=change+permissions+root+user](http://www.ubuntuforums.org/showthread.php?t=67657&highlight=change+permissions+root+user)

I have set up so that I can boot as root (woot woot), then if UT wants me to be root, I will log in as root, change permissions, log back in as bill, then change so that I can't log in as root any more. THEN I'll see if I can play. Probably will still get the "set UT_DATA_PATH" again... hopefully not though, because if I'm not playing as root, it won't want to set the data to the root directory, right? Anybody even listening out there? Hellooooo?


*edit:

Nope. nada. unistalled it again. No idea why it's doing this.

---

### Post by BLTicklemonster on 2005-10-16
Lmao, I just did it again with the how to, and when I tried it, it said that gcc-3.4 was ut of date, I need gcc-4.0. Now I'm back locked out again. 

it tried to compile a new kernel, but said it could not.


So um... how stinking hard can this be, right? I had it all right there in front of me, followed it precisely.

---

### Post by BLTicklemonster on 2005-10-16
[QUOTE=matthew]It was not my intent to annoy you, just to maybe help you consider another point of view. Anyway, probably enough has been said on that.

From the command prompt you can type this to get gdm running again.
```
sudo /etc/init.d/gdm start
``` 
I had a couple of thoughts about what might have occurred and thought I would add them as well. It is likely that you used
```
Ctrl+Alt+F1
``` to reach a command line. There are 6 virtual terminals available in a standard Ubuntu installation and you can reach them via this method, substituting F1-F6 for each of them. If you hit
```
Ctrl+Alt+F7
``` in any of them while an X session is running you will return to your graphic display.[/QUOTE]


Oh, by the way, I'm getting errors saying that there's no way it's going into xserver, that gdm is broken and won't go back until it's fixed. I've tried ever single thing mentioned here, yet it's just sitting there smiling at me like a cheshire cat.

This is on Breezy, btw. Well, I'm on Hoary right now, I kept a back up drive to play with. But the other one was a fresh install of Breezy, not sure if that's been mentioned, but I think so.

By the way, did I mention that I'm on Breezy? well, not right now... I'm on Hoary...

---

### Post by BLTicklemonster on 2005-10-16
Got totally messed up following instructions to the t. Don't understand why. reinstalled breezy. Here we go again.

---

### Post by BLTicklemonster on 2005-11-18
To make a long story short, when one installs the nvidia-glx-config from synaptic, one must look down and notice this little gem:

To enable the driver, run "sudo nvidia-glx-config enable".


Everything is fine. (except that k3b reads my dvd player as the rw, and the rw as the player. Hit eject on the player, and voila, the rw kicks out, and vice versa)

---

### Post by BLTicklemonster on 2008-07-01
My my my, how things have progressed since then.

Running Hardy and lovin' it.

---

