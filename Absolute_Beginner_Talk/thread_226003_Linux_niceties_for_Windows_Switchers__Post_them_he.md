---
title: "Linux niceties for Windows Switchers:  Post them here!"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by MikeMLP on 2006-07-30
This thread is for different things (especially linux conventions) that switchers from windows will either have to get used to, or might find to be better than in Windows.

For example:  I just discovered (even though I've been a linux user for about 2 months now) that you can highlight text to copy, and then paste with a simple middle mouse button click.  No control C, Control V required (although this method works as well).  This is certainly a small-deal feature, but one that I will use constantly (especially given the ammount of time I spend at the Terminal).

Another is the double-tab key press at the Terminal that lists commands similar to the one that I'm currently typing.  This came in handy when I was trying to set up 3d hardware acceleration (was that fglxrinfo or fglrxinfo...?  a double-tab press quickly resolved that problem.  I just needed to type "f+tab+tab" and the terminal listed all f* commands available.  Beautiful!

So post your little things that windows users might not know about here, especially tips like the ones above that can vastly speed up workflow in the linux environment.

---

### Post by mostwanted on 2006-07-30
> For example:  I just discovered (even though I've been a linux user for about 2 months now) that you can highlight text to copy, and then paste with a simple middle mouse button click

By FSM that is coolest feature I've never known! Thank you so much for telling me, I'm in ecstasy over this now! Well, not quite, but close!

> Another is the double-tab key press at the Terminal that lists commands similar to the one that I'm currently typing.

This also works for listing paths and listing available packages when you apt-get something (for example: apt-get install gnome- *tab tab* "would you like to list 117 possibilities?") as well as many more things I don't know about. It's called tab completion and it's absolutely brilliant

When I find out about something to post, I'll do so.

Update: Oh yeah, the built-in FTP features of Nautilus. If you have access to an FTP-server somewhere and register it with Nautilus, you can use it just like a mounted device. It will show up in your Places menu and you just click it and it'll open in a regular Nautilus window. You can then drag and drop files from the desktop or another window or whatever, and it'll upload or drag to your desktop and it'll download. Haven't needed a specialist FTP program since I found out about this.

---

### Post by IYY on 2006-07-30
Small things I miss in Windows:

- xkill: click any application and it gets terminated, without any waiting.

- shell scripts, to automate common actions and terminal commands to find things out.

- SSH access to my machine.

- apt-get to install software.

---

### Post by Lord Illidan on 2006-07-30
By George, I miss Amarok.

---

### Post by AirRaven on 2006-07-30
Pressing Alt+F2 in GNOME is a simple tool that most people don't realise exists until a while.

It just opens the "Run Application" dialog. 

Even more useful is the ability to set a keyboard shortcut to the Terminal. I find that Alt + ¬ is an excellent shortcut to use. So useful to have it your fingertips all the time.

---

### Post by Engnome on 2006-07-30
One click in the url window puts the | there instead of marking everything. First I was annoyed but then I realized that you double click instead, great: one click: put cursor there, double clicks: mark the whole url.

Then I noticed this worked in more places. One click: put cursor there, double clicks: mark the whole word, triple click: mark the whole part.

---

### Post by Lord Illidan on 2006-07-30
Also, yakuake is cool, check it out... a terminal which drops down from the surface.

I also miss KDE and GNOME. Their layout has become dear to me...

And synaptic.

---

### Post by MikeMLP on 2006-07-30
Wow! an hour old, and already so many posts.  Please keep posting, even if it starts to run pages... If there are enough posts I'll try to organize the info into some sort of newb guide pdf...  We'll see how it goes.

IYY: can you elaborate on these at all?

> - shell scripts, to automate common actions and terminal commands to find things out.

- SSH access to my machine.

Things that I would like to know are:
     Are there guides to writing shell scripts?  Where are they? How easy is shell scripting to learn?
     What is SSH?  is that at all like Remote Desktop?  Can you elaborate?

Thanks!

Some great tips so far, I had no idea about the xkill command or Alt+F2, or that Nautilus could do FTP...keep them coming!

---

### Post by Lord Illidan on 2006-07-30
Guides to writing shell scripts? All over the internet.

Google up bash scripts and see what you can find..

Scripts can be written in python, php, perl...you can do whatever you want.

---

### Post by mostwanted on 2006-07-30
Guide to shell scripting (BASH): [http://linuxcommand.org](http://linuxcommand.org)

Goes from basic terminal knowledge to advanced scripting.

---

### Post by H.E. Pennypacker on 2006-07-30
> For example: I just discovered (even though I've been a linux user for about 2 months now) that you can highlight text to copy, and then paste with a simple middle mouse button click. No control C, Control V required (although this method works as well). This is certainly a small-deal feature, but one that I will use constantly (especially given the ammount of time I spend at the Terminal).

I am not understanding this.  Exactly what have you discovered?  You select text, right-click, and select "Copy."  You then go somewhere else, right-click, and paste?  Is this what you're talking about?  If so, the same can be done in Windows.  I am not sure what you're describing, however.

I like that you can hover over an audio file, and Nautilus will automatically play the file (about 20 seconds or so).  Just go to a file in Nautilus, move your mouse over it, stay there, and you'll be able to listen to its contents.  Great feature!

---

### Post by chickengirl on 2006-07-30
> **H.E. Pennypacker said:**
> I am not understanding this.  Exactly what have you discovered?  You select text, right-click, and select "Copy."  You then go somewhere else, right-click, and paste?  Is this what you're talking about?  If so, the same can be done in Windows.  I am not sure what you're describing, however.

What he is describing is: You highlight the text you want to copy. Leave it highlighted. Then middle click where you want it pasted. That's it. No menus or right-clicking involved.

---

### Post by meney on 2006-07-30
[QUOTE=H.E. Pennypacker;1318715
I like that you can hover over an audio file, and Nautilus will automatically play the file (about 20 seconds or so).  Just go to a file in Nautilus, move your mouse over it, stay there, and you'll be able to listen to its contents.  Great feature![/QUOTE]

This sounds great, but it doesn't work for me. Is there an option for it somewhere?

EDIT: Hum, ok I seems to be ticked under the options, but the sound isn't going to my speakers lol. Of course when I open the file it plays normally.

---

### Post by mcduck on 2006-07-31
> **meney said:**
> This sounds great, but it doesn't work for me. Is there an option for it somewhere?

EDIT: Hum, ok I seems to be ticked under the options, but the sound isn't going to my speakers lol. Of course when I open the file it plays normally.

You need to install some CLI audio players for this to work. For some reason or other they aren't installed by default. mpg123 works for MP3-files, but I can't remeber right now what was needed for .ogg & .flac files..

---

### Post by mostwanted on 2006-07-31
> **mcduck said:**
> You need to install some CLI audio players for this to work. For some reason or other they aren't installed by default. mpg123 works for MP3-files, but I can't remeber right now what was needed for .ogg & .flac files..

ogg123 d'uh :)

---

### Post by swamytk on 2006-07-31
Ctrl+Alt+BackSpace to kill X-Windows (GUI Desktop) at any moment!

---

### Post by srikat on 2006-07-31
Another thing I learnt from mostwanted's .gif screencasts is that in a terminal window you can drag and drop a file or folder from desktop or any file explorer to have the path appear.

---

### Post by calx on 2006-07-31
ssh-x is handy, I use it to launch xmms on my desktop which is connected to my hifi and control the tunes with my laptop. A bulky remote control, but getting out of bed is a drag :D

---

### Post by mostwanted on 2006-07-31
> **srikat said:**
> Another thing I learnt from mostwanted's .gif screencasts is that in a terminal window you can drag and drop a file or folder from desktop or any file explorer to have the path appear.

That is a nice feature, but it actually also works in Windows using the command prompt. Not that you can use the command prompt for anything useful in Windows, but the feature is there nonetheless ;)

---

### Post by steve.horsley on 2006-07-31
> **mostwanted said:**
> 
Update: Oh yeah, the built-in FTP features of Nautilus. If you have access to an FTP-server somewhere and register it with Nautilus, you can use it just like a mounted device. It will show up in your Places menu and you just click it and it'll open in a regular Nautilus window. 

Dumb question: How do you "register" a place in Nautilus? 

I have a directory full of files that contain descriptions like this, which is a little convoluted:
> [Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=SERVER43
Type=Application
Exec=nautilus smb://MYDOMAIN;administrator@192.168.5.43/D$
TryExec=
X-GNOME-DocPath=
Terminal=false
GenericName=
Comment=
GenericName[en_GB]=


---

### Post by Orval on 2006-07-31
Things I miss most when I am using Windows:

* multiple desktops
* kio-slaves
* konqueror (I love it when I pop in a CD and I can just drag and drop mp3- or ogg-files)
* amarok
* digiKam
* the fact that I can change the complete look of my desktop
* speed
* lack of need for running virus-scanners and anti-spyware
* superkaramba
* free software updates and upgrades
* this wonderful forum

---

### Post by steve.horsley on 2006-07-31
> **MikeMLP said:**
> What is SSH?  is that at all like Remote Desktop?  Can you elaborate?


SSH is a remote access protocol. It is initiated from the command line, and gives you a command-line login to another box over an encrypted connection. An example might be:
> steve@dingly:~$ ssh steveh@192.168.5.32
steveh@192.168.5.32's password:
Last login: Fri Jun 30 13:57:37 2006 from 192.168.201.213
Sun Microsystems Inc.   SunOS 5.8       Generic Patch   October 2001
server32$


The neat thing is that if you use "ssh -X", then this asks for any X applications to be tunneled back to your PC to appear on your display. So then you can issue a command like "xeyes &" and the window appears on your screen. This is not like windows terminal access because it doesn't give you a desktop - just the application windows. Because the X is tunneled through the SSH  connection, it is also encrypted.

To install an SSH server, install  the package **openssh-server**. But don't leave it open to the internet umless you configure it to require certificates - there are lots of bots out there that connect to SSH servers and spend all day guessing passwords.

---

### Post by hellmet on 2006-07-31
yaa even i was annoyed when i got here into ubuntu from windows..
but now it works gr8

---

### Post by Denis on 2006-07-31
Some things that I like in Linux: 

- The window manager allows you to keep certain windows in front. This is very useful I think, in Windows you have to resize windows to keep it visible. 
- You can scroll windows that are not active. So you don't have to click on everything to activate it. 
- The terminal is great of course. With autocomplete (tab) e.g. you can browse to a directory very quickly. 
- The possibility to assign keyboard shortcuts. With the Pause/Break key I get the quit dialog. 
- Cron is great. You can execute any command at a time specified. 
- Themes are very easy to find, install and change. 

I'm sure there's a lot more...

---

### Post by FooAtari on 2006-07-31
> **IYY said:**
> Small things I miss in Windows:

- xkill: click any application and it gets terminated, without any waiting.

Hmmmm, I needed to terminate a hung app the other day, but couldnt figure it out.  How do you use it?

---

### Post by Drakkor on 2006-07-31
Don't know about xkill,but you can right-click the task bar>add to panel>under Desktop and windows>you can add the force quit button,says it stops misbehaving applications. Which is cool in Ubuntu the panel options ! :p

---

### Post by MikeMLP on 2006-07-31
How to use xkill:
1. open a terminal window
2. type "xkill"
3. use mouse button one (left click) to click the window you want to close.

---

### Post by HanZo on 2006-07-31
there's soooo many cool things I don't know where to start! well let's start... I'll try not to reapeat what others already mentioned...
[LIST]
[*]everything in the desktop environment is modular, you can arrange all the pieces to you needs, you can strip it down to the min or have everything you could ever need in the panel/s. And you can add functionality through applets. as mentioned before you can customize the look of al the UI parts... but the best thing is, while in windows I have to search for hours to find a visual style that's not completely crappy, for gnome I never know what to use because they are all so great! (well not all of them are great, but an amaizing lot of them are). Windows is a lot more restrictive on this.
[*]gome has the very usuful option to apply emblems to folders (or any other icon) this helps a lot in organizing the content of your hd... it's so useful you probably never have to use beagle to seach for a doc... because you already know where it is. Yys windows xp gives you the possibility to customize your folder icon... but it's not as practical.
[*]you can save favourite places and have them listed in your sidebar like osx, that's a better solution than favourites in windows explorer.
[*]tomboy notes... in my opinion the best programs to write and organize notes ever.
[*]Amarok: once you use it you wonder at how you could have gone so far without it. sure you've got some decent media players on wondows... but I found Amarok to beat them all!
[*]when you install a program it add just one entry in the menu and not 10 or more like it is usual on windows... no more over-cluttered and frustratingly un-elegant menus.
[*]you can define font for different parts of the UI you can have  a differnt font for the desktop, that's a small thing maybe... but I found it pretty useful. btw desktop menus look a lot more elegant on the gnome desktop than on windows IMHO.
[*]did I mention xgl/compiz? but I think that's been discussed enough already :D
[*]connect to server enables to you to connect to a lot of different server types... ftp, smb, and many more...btw samba on linux has way better network functionality than windows! I always have problem with windows pcs not showing up on the net... with samba I never had any problems... once I managed to set everything up of course, but that's another story
[*]there's some other great apps you won't fint on any other platform: planner... if you need to plan your projects... found it to be superior then lots of proprietary solutions. Fontforge, a not so good looking but very functional font editor, I use it a lot!
[*]alt+tab shows the window you'll be raising by highlighting it with a black border (even better with compiz of course)
[*]the calendar that appears when you click on the clock is in sync with the one in evolution
[*]and of course the community! It's just great! maybe this could seem less important... but if I think of osx... would be a nice os too... but the community sometimes really sucks... in my very personal and subjective opinion of course.
[/LIST]

---

### Post by FooAtari on 2006-07-31
Thanks Drakkor, Mike

---

### Post by hellmet on 2006-07-31
> You can scroll windows that are not active. So you don't have to click on everything to activate it.
+1

---

### Post by H.E. Pennypacker on 2006-07-31
> **MikeMLP said:**
> How to use xkill:
1. open a terminal window
2. type "xkill"
3. use mouse button one (left click) to click the window you want to close.

Why not just use System Monitor to kill it?  System > Administration > System Monitor.  No need to type anything, and it's all GUI.

---

### Post by RRS on 2006-07-31
> **H.E. Pennypacker said:**
> Why not just use System Monitor to kill it?  System > Administration > System Monitor.  No need to type anything, and it's all GUI.

For even quicker access;
Right click on a panel.
Add To Panel>Desktop and Windows>Force Quit

---

### Post by chickengirl on 2006-07-31
> **H.E. Pennypacker said:**
> Why not just use System Monitor to kill it?  System > Administration > System Monitor.  No need to type anything, and it's all GUI.
But xkill gives you that totally kickass skull-and-crossbones cursor. :D

---

### Post by ChadMMc on 2006-07-31
Two of the things that I found nice with the Ubuntu Linux are:
1) the ability to have the system show where the mouse cursor is just by pressing the control key. (System->Preferences->Mouse-> Pointers)

and
2) the ability to have a window roll-up when double-clicking the title bar.
(System->Preferences->Windows)

Small things, but they come in quite handy for me at times.

Oh, and the whole Assistive Technology Support is great!
:p :p

---

### Post by catlett on 2006-08-01
Just to clarify 2 things.
xkill.... You enter ```
xkill
```In the terminal and press enter. When you press enter your cursor becomes "jolly roger" a.k.a. a skull and cross bones. The terminal itself is in waiting mode. You go to the window of the app you want to kill and left click on it once. It's dead. Why not use the system monitor? Why use the system monitor? Personal preference.
The other thing is the mp3 "hover and play". With the right app installed you can hover over an mp3 or other supported file and the file plays without launching a music player or media player. I leave them on my desktop and hover around when I feal like it :D  Anyways to get mp3 and vorbis support install these
```
 sudo apt-get install mpg321 vorbis-tools
```I just posted this because earlier it was referred to as mpg123.

The thing I found useful has already been alluded to. One of my biggest problems early on was cd'ing to a folder. Or getting a path right. Now I use drag and drop. If there is a folder in the filesystem somewhere that I need to cd to, I browse to it in Nautilus and then in the terminal I enter cd then space. Next I drag and drop the folder and the path is written into the terminal. I then press enter and I am cd'ed to the folder. No more mix ups and no more constant 'tab' pressing.(I also use it just to know the correct path of a file/folder)
That's it, just thought I would drop in and share.

---

### Post by mcduck on 2006-08-01
> **catlett said:**
> 
```
 sudo apt-get install mpg321 vorbis-tools
```I just posted this because earlier it was referred to as mpg123.

That is because there is also mpg123 package, and that works just as fine as mpg321 does.. ;)

Anyway, thanks about the vorbis-tools, I have ogg preview working fine but I wasn't sure which package enables it.

---

### Post by catlett on 2006-08-01
> **mcduck said:**
> That is because there is also mpg123 package, and that works just as fine as mpg321 does.. ;)

Anyway, thanks about the vorbis-tools, I have ogg preview working fine but I wasn't sure which package enables it.

Sorry about that I had no idea about mpg123. I only know of mpg321 from the restricted formats page. 
I stand corrected. My apologies.

---

### Post by Drakkor on 2006-08-01
I have the preview play,but it usually skips and I did run across a fix for this,but can"t remember where ? Thanks :o

---

### Post by mostwanted on 2006-08-02
> **steve.horsley said:**
> Dumb question: How do you "register" a place in Nautilus? 

Well, I'm using it for FTP servers, but I can see some other options (windows, ssh, webdav, ...) as well:

Places &#8594; Connect to server... (or similar, I'm using Danish Ubuntu)

Then select the correct type of server in the pull-down menu and add your info. Then it'll integrate into your Nautilus bookmarks and be available in all Nautilus windows and all instances of the save and open file dialogs.

---

### Post by MikeMLP on 2006-08-14
Something I discovered by accident:

type ```
 Calendar 
```
into the terminal, and you will get a list of what happened on this day in history (and tomorrow too)  Includes both Linux-related events, and world history events.  Always nice to start the day with some trivia.

---

### Post by seshomaru samma on 2006-08-14
> **chickengirl said:**
> But xkill gives you that totally kickass skull-and-crossbones cursor. :D

You are absolutely right.
I added xkill to my panel!

---

### Post by steve.horsley on 2006-08-14
If you kill a gnome-terminal wilh xkill, it will kill **all** instances of gnome-terminal that are running. I just lost my VPN doing that.

Catlett:
re: Dragging folders to "cd " in terminal: 
If you install package nautilus-open-terminal, nautilus gets an "open in terminal" option when you right-click a folder, which opens a terminal in that folder of course. Wicked!

---

### Post by The Seeker on 2006-08-14
> **MikeMLP said:**
> Something I discovered by accident:

type ```
 Calendar 
```
into the terminal, and you will get a list of what happened on this day in history (and tomorrow too)  Includes both Linux-related events, and world history events.  Always nice to start the day with some trivia.

Wow that's really, really cool - thanks! :D

---

### Post by Drezliok on 2006-08-14
I was able to get unrealTournament plust all of my addons and a personally packaged installer to run and work perfictly in Wine and works BETTER. than it does on my windowsXP

Using Xubuntu.

---

### Post by sean_ on 2006-08-14
Forcekill actually kills instantly unlike windows~

---

### Post by Garyu on 2006-08-30
I didn't read through all of the posts here, sorry, but one thing I love about Ubuntu compared to window is the reliability of the network. In windows, it would be almost impossible to get a win98, win2000 and/or winxp (or even two winxp machines) to talk to eachother and share files. I have at least spent hours trying to figure this out.

In Ubuntu, just "sudo apt-get install ssh" on both machines, then go to Nautilus and Go to Location "ssh://machinename/share", log on and you have full access over a SECURE connection, can even be used over the internet to drag and drop files. Or open a terminal and ssh to your computer to start up services or apps. Once you get the hang of it, ssh is a GREAT thing.

Also, samba is a lot more reliable for windows sharing than windows itself ever was. :D

---

