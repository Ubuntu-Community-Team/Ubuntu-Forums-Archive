---
title: "Remote administraton (with GUI)"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by lwf on 2006-07-10
Hi! I am an old Windows user that just have installed Ubuntu 6.06 on a HP NetServer E 60 (two PII@400MHz, 384MB RAM, some old ATI graphics card, no monitor however) to learn how to use Linux and setup some services (ftp, radius, whatever I can make up).

It’s very loud so I shall place it in a wardrobe and then control it over the network. So I installed SSH and setup VNC in the Remote Desktop Preferences and it worked really nice and I could connect to it from my Windows machines. But... it only works when I am already logged in!
I don’t want to leave the computer with that GUI on the screen, the server isn’t fast and gnome steals a little resources, it’s also not very secure even if it’s not really a problem in my home. I also have to keep a keyboard connected to the server so I can enter my username and password every time I reboot.

So what should I do? Can I login to the desktop with SSH and then connect to the VNC-server somehow? If this is possible, can deactivate the logonscreen (steals resources)? Or maybe there is a much better way, I saw something about XDMCP and X forwarding, maybe that is the way it should be done (whatever it means)?

Thank you very much for your time! :)

---

### Post by Brunellus on 2006-07-10
what do you need to administer on it that has to be done graphically?  you could just run the box headless and ssh into it for whatever you need.

---

### Post by lwf on 2006-07-10
Well, I am a new user and I feel kind of uncomfortable not having access to the GUI and I thought that Ubuntu would work with that. I love that synaptics program by the way. :D

---

### Post by uzi09 on 2006-07-10
i've seen this question come up before as well in the forums. i'll see if i can find the thread again.

i recall that people were talking about the "nohup" command (or something like that) that allows programs to run even after you've logged off.



EDIT: I think this might be what you're looking for:
[http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc+log](http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc+log)
although i'm not too sure what they mean by "resumable session".

---

### Post by lwf on 2006-07-10
Thank you, I will give it a shot. :)

---

### Post by stychman on 2006-07-10
The suggestion I have for you is not a very easy one and I don't know the exact steps to do it.  I use FreeNX to remote into my Ubuntu box from my Windows XP box.  You do not have to be logged in to remote into the pc.  Take a look around the forums and you will find many questions and answers about setting up FreeNX.  I suggest you do some research before trying to do this.  It takes a little bit of doing to get it right but it's not that difficult.  I'm fairly new to linux and was able to figure it out after a couple days of research.
After getting that set up you can change your Ubuntu machine to boot to a Command Line Interface instead of going straight into GUI.  Take a look at this thread[http://www.ubuntuforums.org/showthread.php?t=207693&highlight=runlevel]("http://www.ubuntuforums.org/showthread.php?t=207693&highlight=runlevel")to get your computer to boot to CLI.

---

### Post by lwf on 2006-07-10
Ok, I guess I should look at the diffrent ways of doing this first.

But is there really no way to login to the GUI over SSH so that I can boot it to CLI as default and then start X, VNC and all that when needed?

---

### Post by lwf on 2006-07-10
Now I tried connecting with Xming. I got the welcome/login-screen, but when I have entered my login and password the screen just goes black (but I can still se the mouse pointer). I didn’t make the VNC-server start either :(

---

### Post by uzi09 on 2006-07-10
well, for gui over ssh, i'm not too sure about the login screen, but otherwise, if you're on a computer that's already running x server (like another linux box) you can do the following:
```
ssh -X uzi@ubuntu
```
that -X switch will enable the x server and you can run *i believe* any gui program. again, i'm not too sure how well gdm will take it, but it's worth a shot.

now as far as doing this from a windows machine -- there is a way to run x-server on windows, but i must admit, when i gave it a try, it was quite resource intensive and really quite buggy.
if you'd like to go through with it, here is the guide (it's a program called cygwin):
[http://www.ap.stmarys.ca/~smuaps/software/cygwin_guide.pdf](http://www.ap.stmarys.ca/~smuaps/software/cygwin_guide.pdf)

for more tutorials, go to google and search the following:
cygwin x server

personally, i'd go with the link i first provided. it seems like that's exactly what they were trying to do and if it works -- seems to be the best route to go through.

uzi

---

### Post by brentoboy on 2006-07-10
if you dont care at all about security and you are only accessing it from your local area network then xdmcp is your answer.

on the main computer, open up the gnome System>Administration>LoginWindow app

click the remote tab, and eable remote login.
this will enable xdmcp

you might have to restart GDM in order for it to work, so, save everything, log out and then, click Ctrl+Alt+f1

this will take you to a terminal run this:
sudo /etc/init.d/gdm restart

you have to run it from a "real" terminal and not an X terminal becuase it will kill the xterminal as it closes gdm, and then it wont restart anything.  thus creating an ugly mess.

EDIT: rather than restarting gdm, if it is easier on you, just reboot the box

once you have restarted, you dont have to login here anymore, goto another PC.

if it is a linux PC and you are running Xwindows on it, then log off (back to the graphical login screen.  in the options menu there should be an option to "Remote login via xdmcp..." which will let you select remote PCs that offer xdmcp access.

if you are on the same subnet (or local network) it should let you choose your "server" and then login and run programs from there as though you were right there at the server.

--

if your client computer is running windows then you should install cygwin, and then you can use xdmcp from it.  It works nicely from my work laptop which has to be windows becuase... well, I write windows software for a living. :)

I have a post in another thread that talks about getting xdmcp working with cygwin... if you have trouble with it, I can hunt it down for you...

---

### Post by lwf on 2006-07-10
Thanks for your post! I didn’t expect these thing to be so hard. Or at least less hard :o

I can login with Xming, but when I have entered my login and password the screen remains brown and there is no nice GUI to click at. I don’t really understand how to do it in cygwin but I managed to open individual programs, like firefox, in cygwin with putty over ssh and x11 forwarding.

If it would help me I would be very happy if you found that topic. :)


EDIT: I now wrote "XWin.exe -query 192.168.1.XXX" in cygwin and the result was the same as with Xming. :(

EDIT2: Tried to reboot if that would fix anything, old Windows habit I guess. ;) But now I can only use 640x480, 60 Hz! There is nothing else in the list. Now I am really clueless. :-?

---

### Post by uzi09 on 2006-07-10
> **uzi09 said:**
> i've seen this question come up before as well in the forums. i'll see if i can find the thread again.

i recall that people were talking about the "nohup" command (or something like that) that allows programs to run even after you've logged off.



EDIT: I think this might be what you're looking for:
[http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc+log](http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc+log)
although i'm not too sure what they mean by "resumable session".

[http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc+log](http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc+log)
you didn't mention using this -- have you taken a look at it yet??
it's a how-to for the exact thing you're looking for, but i haven't tried it out myself.

---

### Post by lwf on 2006-07-10
Sorry, I tried that before but I guess it could be worth another chance. I got a lot of problems with X and it all ended that I wouldn’t start so I simply formatted the server again. Those problems started however in the same way as I am heading now, I am once again only able to use 640x480 resolution. I am starting to think that the resolution problem didn’t have anything to do with that last try get that” resumable session”, it must be something else.](*,)

---

### Post by brentoboy on 2006-07-10
[http://www.ubuntuforums.org/showthread.php?t=176463](http://www.ubuntuforums.org/showthread.php?t=176463)
[http://www.ubuntuforums.org/showthread.php?t=164861](http://www.ubuntuforums.org/showthread.php?t=164861)

Do either of these help?

---

### Post by lwf on 2006-07-11
I will try some suggestions, but I might not do it now or I might not reply for a while since I am going away, probably in a couple of days, for a few weeks. But I will try again, thank you.

Oh, and the resolution problem… well, I rebooted again and it simply started to work again. It freaks my out a little not having any idea whets going on but at least it seams to work. ;)

---

### Post by AsYouWish on 2006-07-11
Arg. I am having the same problem also using Xming. I am able to pull up the login screen, enter my username and password and then... nothing. dark brown/black background with visible and moveable mouse. 

The computer Im trying to set this up on has a barely functional mouse, so the the sooner I can get this working the sooner my BP will drop.

Thanks for any help

--Edit
I was doing this while my Ubuntu machine sat at the login screen. After Xming failed I went to log in and was told I was already logged in. Dont know if its relevant...

--More Edit
After (accidentally) leaving xming running for about 10 mins i found the Ubuntu background image had loaded... but nothing else. arg.

---

### Post by brentoboy on 2006-07-11
what speed is the connection between the two pcs?

that sounds a lot like what happened when I tried the same thing over a vpn from campus to my living room.

---

### Post by walmartshopper67 on 2006-07-12
I'm having the same problem (both boxes running updated to the day dapper). I have 100Mbps (switched) between the two. It just kind of sits there.

---

### Post by SigmaX on 2006-07-12
Um... did I miss something or can you not just log in via SSH on the command line, and then start a vncserver from there to admin graphically?  That's what I used to do back in my multi-OS days (While I stil fratenized with the Micro$oft enemy).  Less hectic to setup then all the Cygwin stuff for X; as long as it's over LAN the perofrmance difference isn't a biggie either.

But X forwarding is nice, I'll admit ;-).  Haven't used VNC in a year myself.

SigmaX

---

### Post by AsYouWish on 2006-07-12
I tried to log in via SSH and then start vncviewer. I got a 'could   not start display' or similar sort of deal. (ussing putty a problem?)

Anyway, I gave up on the xdmcp thing and just installed a vnc server and grabbed realvnc for my winXP machine and it works great. Alot less painful than I anticipated. Just followed the instrustions in the howto thread. THe only hangup was when I accidentaly enterd 124x... instead of 1024x... for the screen resolution. that was frustating, but easily solved and kinda funny afterwards.

The only complaint I have is that some of the graphical whatnot is screwed up. Menus are blacked out, I can only see the text when I scroll over. Same with parts of the desktop borders, and with the part of the background in syaptic.

My suggestion for those others with the xming not working is just install the vnc server. Its really not as bad as it looks.

---

### Post by walmartshopper67 on 2006-07-12
Hm. Maybe I'm barking up the wrong tree? I have a desktop and a laptop, both with Ubuntu dapper, and I would like to use my desktop (graphically) over my LAN. is xdmcp not what I'm looking for?

---

### Post by uzi09 on 2006-07-12
> **walmartshopper67 said:**
> Hm. Maybe I'm barking up the wrong tree? I have a desktop and a laptop, both with Ubuntu dapper, and I would like to use my desktop (graphically) over my LAN. is xdmcp not what I'm looking for?

yes [http://en.wikipedia.org/wiki/Xdmcp](http://en.wikipedia.org/wiki/Xdmcp)


> **SigmaX said:**
> Um... did I miss something or can you not just log in via SSH on the command line, and then start a vncserver from there to admin graphically?  That's what I used to do back in my multi-OS days (While I stil fratenized with the Micro$oft enemy).  Less hectic to setup then all the Cygwin stuff for X; as long as it's over LAN the perofrmance difference isn't a biggie either.

But X forwarding is nice, I'll admit ;-).  Haven't used VNC in a year myself.

SigmaX

whoever suggested the option to ssh into the machine and starting a vnc session -- that's actually a pretty good idea, never thought about that. thank you :D

anyway, for this to work SigmaX, you would need to (and people, please correct me if i'm wrong) start the vnc daemon so that you can actually log in remotely through vnc. the thing is, the vnc daemon stops running after you log out. so this is where ssh comes in, you can use ssh to log in and start the daemon, thus allowing you to minimize your ssh client and open up a vnc brower/viewer and connecting to the vnc server.

so basically, log in using ssh, then start up the vnc server. although i haven't tried this out yet practically, it all makes sense theoretically

---

### Post by frafu on 2006-07-27
[QUOTE=uzi09]

so basically, log in using ssh, then start up the vnc server. although i haven't tried this out yet practically, it all makes sense theoretically[/QUOTE]

Supposing that the remote computer running Ubuntu does boot into the CLI instead of booting into the GUI. 

Will I have to start (through ssh) gdm on the remote box before starting the vncserver? If so, could you please confirm and give me the commands to start/quit gdm and start/quit the vncserver? 

Further, I would like to point out, that being rather a newbie, I don't know exactly the meaning of gdm (I know that localy, a gdm allows you to login in a box and choose the desktop environment). But more precisely, I wonder whether the box passes from cli to gui by starting gdm and whether the box passes from gui to cli mode by quitting gdm!? If not, what commands do I have to type to pass the remote box from cli to gui mode and back from gui to cli mode? 

Many thanks in advance for any advice, help and clarification. 

frafu

---

### Post by Perkins on 2006-08-04
Using ssh or telnet to remotely start a VNC server is what I do with 90% of my servers when I need to use their graphical shell.  Works well for Ubuntu, Redhat, and puppy linux.  

The first thing you need is to make sure that you have a normal vnc server installed on your system.  Last time I checked, the one that comes installed on Ubuntu is a special purpose one for connecting to the running screen.  So if there is no running screen it gets all confuzzled and dies.  Look in Synaptic, there are several, pick one.  Unless you're doing something special, it probably doesn't matter much which. tightvncserver and vnc4server are both good choices, but look through the list and see what all's there.

After you've installed it, you'll probably need to set a password.  Depends on your system's security settings and which server you have.  Type:

vncpasswd

And then set the password you want to use.

Once you've done that, you'll need to start the server for the first time.  command should be:

vncserver :*display number*

replace *display number* with a number from 1 to 9, or leave it off to 
just open the next available display.  (It will tell you which one it used.)  Then, turn it off again with:

vncserver -kill :*display number*

Now, you may wonder why I said to turn it on and then off again.  If you were paying attention to the output though, you will have noticed these three lines when you started the server:

Creating default startup script /home/*your username*/.vnc/xstartup
Starting applications specified in /home/*your username*/.vnc/xstartup
Log file is /home/*your username*/.vnc/*your machine name*:1.log

The default on most systems is to start VNC as a simple graphical shell with a single instance of Xterm.  You can look at it if you really want.  It's no more useful than SSH, except you can kind of run graphical programs.  If you want to change that behaviour, then you need to edit ~/.vnc/xstartup

open it in your favourite text editor.  (I like vim, but I've been told that I'm just wierd.)  odds are, there's a line there that says, 
"# Uncomment the following two lines for normal desktop:"

Pretty self explanitory.  Do what it says.  If that line's not there, then try adding:

unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

to the top of the file, right after the #!/bin/sh  (Unless they're already there.  You don't want two copies of them.)

That should make the VNC display use the same defaults as the normal graphical shell installed on your system.  If you don't have one, then you'll have to set one up.  Sorry, I can't really help you with that.


After that, you can start the server from the command prompt, either on the console, or through ssh, telnet, or whatever other remote access you might have set up.  Then connect to it with your client and you should be good to go.

On a side note, you can specify just about any display size you want.  Read the manual for the vncserver program, it'll give you a list of options.  So you can actually match the window to the capabilities of the machine you're viewing from, rather than the server.

Anyway, sorry for the long explanation, but I was seeing a lot of "this should work"s and "I've never actually tried it"s, so I figured a complete explanation might be the most useful.  Hopefully it'll work for you.


GDM is the program that gives you the graphical login prompt.  you'll find it in system>administration>services.  If you don't want it anymore, turn it off.  After you do that, the system will only offer you a terminal login, but once you're logged in, you should be able to type "startx" to get the graphical shell going.  From there you can turn gdm back on in the service manager if you want.  Please note though, the only options in the graphical shutdown menu will probably be logout.  you'll have to kill X and then use the shutdown command to turn off the machine.  You'll probably need administrator rights to shut it down.

---

### Post by frafu on 2006-08-05
Hello Perkins,


> 
Anyway, sorry for the long explanation, but I was seeing a lot of "this should work"s and "I've never actually tried it"s, so I figured a complete explanation might be the most useful.

There's no reason to be sorry; in fact, I thank you very much for the effort you made to write the long "howto". It has given me valuable detailed information about how to proceed and it surely will save me a lot of time setting up my ubuntubox next week. (the various commands and things to edit; vncserver shipped with ubuntu being special purpose; default graphic shell not being the normal graphic shell; parametring the server to make the window match the remote display;...)

I am going to install the desktop version of ubuntu, so it will have a graphical shell by default.
 
As far as I could learn from reading around, I have to change runlevel to make it boot to cli. Ubuntu running in runlevel 2, I wonder what are the runlevels 3, 4 and 5. In a post, I have read to set it to runlevel 3 and disable the S??gdm script in runlevel 3. Thus my question: are runlevel 3, 4 and 5 copies of runlevel 2? Anyway, I will probably begin with having a look at the utility bum in order to change runlevel. 


Have a nice day.

---

### Post by Perkins on 2006-08-06
ubuntu appears to be a little...  unusual here. It only seems to use runlevels 1,2,and 6.  1 is single user mode and is basically what you get when you boot into recovery mode.  Most of your server processes won't be running, so that's not particularly useful.

Runlevel 2 is being used as multi-user mode with everything running.  That is...  unusual...  Most of the other distros I've seen split it up a little more into 3,4,and 5 with different things running in each.  To not boot the graphical shell, you'd simply tell it to use runlevel 3 instead of 5.  That would load everything but the graphical shell, and there you go...  On Ubuntu you can't do that since runlevels 3, 4, and 5 appear to indeed be merely copies of runlevel 2.

I am not entirely certain about how this works.  But I believe you will find the list of things it starts and stops for each runlevel in /etc/rc*runlevel*.d  /etc/init.d/rc appears to be the script that changes runlevel.  You only need a passing familiarity with the scripting language to get the gist of what it does.  I *think* you can simply remove the link to gdm from /etc/rc2.d to make it not use it by default.  I am not sure what all this will do to the rest of the system, and while I am curious, I am also not particularly enthusiastic about trying it on my desktop.  I *might* have time to test it at work on Monday, but no promises.

Can someone who is "In the know" please tell me why everything is crammed into two runlevels?  It would seem to me that this would simply make diagnostics and repairs more difficult, without making any difference to any technopeasant users, since they wouldn't know a runlevel from a CPU anyway...




Edit:  My curiosity overcame my better judgement.  That happens a lot...  I altered the list in runlevel 3 to not start gdm, then switched to 1 to kill everything and then to 3 to test it, and it does indeed not start gdm...

Unfortunately, this also seems to blow the graphical shell all to pieces.  Aparently on my system at least, it doesn't work without gdm...  The window and session managers don't start.  Since I have never been able to find a clear explanation of how these programs are supposed to work together, and graphical shells are not my forte anyway, I am at something of a loss.  So I'm going to have to hand this off to someone else.

---

### Post by frafu on 2006-08-06
> **Perkins said:**
> 
I am not entirely certain about how this works.  But I believe you will find the list of things it starts and stops for each runlevel in /etc/rc*runlevel*.d  /etc/init.d/rc appears to be the script that changes runlevel.  You only need a passing familiarity with the scripting language to get the gist of what it does.  

I have found at [BUM's Website]("http://www.marzocca.net/linux/bumdocs.html") an explanation of how the bootup scripts work in debian. It was quite interesting for me, though I think that you  already know all that. 


>  
Edit:  My curiosity overcame my better judgement.  That happens a lot...  I altered the list in runlevel 3 to not start gdm, then switched to 1 to kill everything and then to 3 to test it, and it does indeed not start gdm...

Unfortunately, this also seems to blow the graphical shell all to pieces.  Aparently on my system at least, it doesn't work without gdm...  The window and session managers don't start.  Since I have never been able to find a clear explanation of how these programs are supposed to work together, and graphical shells are not my forte anyway, I am at something of a loss.  So I'm going to have to hand this off to someone else.


I hope that making gdm start automatically will put runlevel 3 back in its original state. I would be sorry if you are getting into trouble because of it. 

Concerning graphical shells, it really seems to be a complex subject; there is: 
- X window system 
- X window manager 
- display manager 
- gdm
- gnome, kde, xfce,... 
- ...  

I begin to have a little idea of the meaning of these terms, but there is still a lot to learn for me. 

Anyway, thanks again for all the help you gave me so far.

frafu

PS: Maybe, that the creation of more different runlevels (with at least one that boots into the cli) would be an interesting suggestion for ubuntu edgy. However, I think that I am to new to ubuntu for making suggestions.

---

### Post by Perkins on 2006-08-06
Runlevel 3's not a problem since Ubuntu only uses 1 and 2 anyway.  I left it modified in case I ever need a cli with everything but X.  If I manage to figure out how to make the rest of it work I'll let you know.

---

### Post by puelly on 2006-08-07
FreeNX is the way to go with this type of task.  It's easy to install and fast.  You should give it a try, I use it all the time.

---

### Post by Perkins on 2006-08-07
Ok, it's something to do with my desktop at home.  I just tried disabling gdm on my mrtg server here at work, and the graphical shell still works just fine.  If I were you, I'd remove gdm from runlevel 2.  You should still be able to just type startx and have the graphical shell start.  VNC should still be able to use the window manager and whatnot, and if you need the graphical login for some reason you can just do a telinit 3 and runlevel 3 will start gdm for you.

---

### Post by jimcooncat on 2006-08-10
At work I use xming on my windows machine. With xming, I authorize the ip address of the ubuntu machine I keep in the cellar to have access to my  display. This wouldn't work if I had creeps on my LAN. I tell xming to run one window without decorations.

I then use ssh to log in to the Ubuntu machine, and issue an "export DISPLAY=*workmachine*:0" on it. Then I run "gnome-session". No need for xdmcp or gdm -- I'm logged in anyway.

I found it looks a lot nicer by installing a font server on the ubuntu machine, and setting up xming to use it. Very easy to set up this little tweak. 

This is a very lightweight setup, and seems to work better for me than vnc or nx. But it doesn't have the session on the ubuntu machine, so when xming crashes, it takes down my whole gnome session.

And it does crash. Certain dialog boxes will freeze xming. One that I think is really weird, well enough to remember, is if I do a search *for the second time* in synaptic.

I think I'd actually be happier with vnc if I could figure out the geometry and turn off all the compression stuff so I can get good graphics. I haven't had the patience with vncserver to get a nice looking display with it though. 

Ultravnc is a very nice client (and server) for Windows, and I have my boss hooked up with it through ssh on his Windows laptop and desktop. 

I've also tried multiwindows (hidden root window) mode with xming, issuing individual commands through ssh to start programs, like "mozilla-thunderbird &". It integrates nicely with the Windows desktop, but is a memory hog this way after several hours use, and some additional strangeness happens. Particularly, tooltips from a covered application will pop up right through a windows program. 

For instance, I'll be working in Quickbooks and move my mouse, and apparently Ubuntu's Gaim is in the window behind it. And a little yellow box showing one of my buddies' names will show right on top of my balance sheet!

---

### Post by Perkins on 2006-08-11
vncserver's actually a fairly simple creature.  

vncserver :*displaynumber* -geometry *width*:*height*  -depth *8,16,or24*

Most of the servers and clients I've seen don't do compression by themselves.  Often you have to direct it through a compressed SSH tunnel.  Most also do not do encryption.  Again, SSH tunnel.

If you're still having trouble with latency, there are a few Xvnc options that might help.  Check out vncconfig, it lets you modify settings on a running vnc server, and keep in mind, there are lots of server and client variants, each with their own strengths and weaknesses, so if the one you have isn't working well, try a different one.

---

### Post by frafu on 2006-09-13
First of all, sorry for the late reply.

> **puelly said:**
> FreeNX is the way to go with this type of task.  It's easy to install and fast.  You should give it a try, I use it all the time.

I decided to use nomachine's free edition of their nx server (the propriety version of freenx), because they also supply a client for MacOSX. Being rather a newbie, I assumed taking a server and client from the same brand would reduce my chances to get into trouble. 

NX client starts the X11 server shipped with MacOSX and opens a window that displays the new gui session. It allows before conecting to choose the display manager. It displays the different forms of the pointer: the arrow, the vertical line when entering text, the wait disk,... When using Ubuntu's vncserver and another vncviewer, the pointer never changed its shape; I don't know whether it was due to the server, to the client or to their combination. 


There is another notable difference between the two methods: when using nx, the restart and shutdown buttons are missing when I choose Quit. Maybe it is because in reality, nx is an xsession that forwards the whole desktop, while the other method is plain vnc, only forwarding screenshots of the desktop. This may also explain the pointer behaviours. But I am only making conjectures. 


frafu

---

### Post by jimcooncat on 2006-09-14
> **frafu said:**
> There is another notable difference between the two methods: when using nx, the restart and shutdown buttons are missing when I choose Quit.

Same behavior with my forwarded X sessions.

---

### Post by frafu on 2006-09-14
> **jimcooncat said:**
> Same behavior with my forwarded X sessions.

It seems to confirm, that in reality NX uses X forwarding, at least when running the server on Ubuntu and the client on MacOSX. 

By the way, to shutdown the remote computer, I type "sudo shutdown -h now" through a ssh-connection. 

frafu

---

### Post by Perkins on 2006-09-15
Remote desktops do not have a shut down option.  If you're using the in-built VNC server, then it's actually the currently running desktop, so the option is there, but with other servers, or XDMCP, or other detached desktops, it's not.  There's probably a way to change this, since there's no real reason a remote user *cannot* shutdown the machine, but it's probably more trouble than it's worth. 

I tried just disabling gdm in the services pane.  It didn't work well.  First the computer refused to start properly, and then when it did, it just reenabled it.  *shrug*  I vote that in the next version of Ubuntu they expand the runlevels to include the more useful single user, multi user, multi user with graphical shell distinctions.  Would be most helpful.

---

### Post by frafu on 2006-09-15
> **Perkins said:**
> 
I tried just disabling gdm in the services pane.  It didn't work well.  First the computer refused to start properly, and then when it did, it just reenabled it.  *shrug*  I vote that in the next version of Ubuntu they expand the runlevels to include the more useful single user, multi user, multi user with graphical shell distinctions.  Would be most helpful.

Thanks for telling about the problems you got by disabling the gdm in the services pane. You seem to have gotten similar problems that I had. Consequently, I removed the corresponding paragraph in my previous message. 

frafu

---

