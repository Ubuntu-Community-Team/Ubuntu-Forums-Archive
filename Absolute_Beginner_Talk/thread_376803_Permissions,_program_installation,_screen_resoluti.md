---
title: "Permissions, program installation, screen resolution"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-03-05
Hey!

A couple of nights ago I successfully installed Ubuntu on my computer for the first time, with the kind help of some members of this forum.  Now that I have it, I’ve got about a million questions regarding what I ought to do with it, so I turn again to this forum for help.  Starting with the most pressing issue:

1) I seem to have made some kind of change to my “permissions” by accident: every time I log on now, I get a kind of error message to the extent that my Home directory is being ignored.  I think this problem occurred because

2) I tried to download and install the electric sheep screensaver.  I discovered to my surprise that I didn't have permission to change “root” directories.  So I went into the permissions file and fooled around with it in some manner, although I don’t really know what I did to it.  

:)

3)  I have just bought a wide screen LCD monitor.  Because of it's shape it requires a special height to width pixel ratio, namely 1.6.  The recommended resolution is 1440 x 900.  The recommended refresh rate is 60 Hz.  For some reason when I go into screen resolution folder the highest resolution option I find is 1280 x 1084, and the only refresh rate available is 75.

4) This monitor comes with a driver.  Easy to install in Windows, but I don’t understand the Linux instructions: “To execute the X-Window, you need to make the X86Config file, which is a type of system setting file,”  followed by instructions on what to do after executing the file.  How do I execute an X86Config file?

6) I need to install electric sheep, but that can come later, of course….

:)

Thanks in advance for help and advice!

(More questions will be posted soon.)

---

### Post by gosh on 2007-03-05
3) have you tried to change the resolutions in your xorg.conf?

---

### Post by Mr. Svinlesha on 2007-03-05
For what it’s the worth, the message I get at log-in is the following:

“User’s $HOME/.dmrc files is being ignored.  This prevents the default sessions and languages from being saved.  User’s home directory must be owned by user and not writeable by other users.”

Approximately.

**gosh**

Nope.  Don't know how to.

---

### Post by aysiu on 2007-03-05
> **Mr. Svinlesha said:**
> 
1) I seem to have made some kind of change to my &#8220;permissions&#8221; by accident: every time I log on now, I get a kind of error message to the extent that my Home directory is being ignored.  I think this problem occurred because Changing permissions can be problematic. Read this, for more details:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Are you getting an error about .dmrc? If so [this thread](http://ubuntuforums.org/showthread.php?t=91455) may help.

> 2) I tried to download and install the electric sheep screensaver.  I discovered to my surprise that I didn't have permission to change &#8220;root&#8221; directories.  So I went into the permissions file and fooled around with it in some manner, although I don&#8217;t really know what I did to it.  

:) These links will help you understand program installation better:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

Once you [have extra repositories enabled](http://www.psychocats.net/ubuntu/sources), you can install *electronicsheep* with this single [terminal](http://www.psychocats.net/ubuntu/terminal) command: ```
sudo aptitude update && sudo aptitude install electricsheep
```

> 3)  I have just bought a wide screen LCD monitor.  Because of it's shape it requires a special height to width pixel ratio, namely 1.6.  The recommended resolution is 1440 x 900.  The recommended refresh rate is 60 Hz.  For some reason when I go into screen resolution folder the highest resolution option I find is 1280 x 1084, and the only refresh rate available is 75.

4) This monitor comes with a driver.  Easy to install in Windows, but I don&#8217;t understand the Linux instructions: &#8220;To execute the X-Window, you need to make the X86Config file, which is a type of system setting file,&#8221;  followed by instructions on what to do after executing the file.  How do I execute an X86Config file? What's the exact model and manufacterer of the monitor?

Just about every screen resolution fix can be found [here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21).

By the way, notice all the links I put in this reply? Please read all of them before you start doing anything. As you know from your permissions issue, understanding must come before action.

---

### Post by Mr. Svinlesha on 2007-03-05
> Please read all of them before you start doing anything. As you know from your permissions issue, understanding must come before action.Aye, verily.

My .dmrc problem isn't horribly serious or unrepairable, though, I hope?

---

### Post by aysiu on 2007-03-05
> **Mr. Svinlesha said:**
> 
My .dmrc problem isn't horribly serious or unrepairable, though, I hope? No, it's probably an easy fix. Read the link I posted. Post back any further questions you may have.

---

### Post by Mr. Svinlesha on 2007-03-05
Already need to ask one stupid question -- are you sure you posted a link to the correct thread?  The link I've got leads to twenty pages about "Shelly the Republican".  I'm about 8 pages into it and haven't found a single mention of .dmrc.

---

### Post by aysiu on 2007-03-05
> **Mr. Svinlesha said:**
> Already need to ask one stupid question -- are you sure you posted a link to the correct thread?  The link I've got leads to twenty pages about "Shelly the Republican".  I'm about 8 pages into it and haven't found a single mention of .dmrc.
I had a bunch of tabs open. I copied the wrong link.

The link is now updated. Sorry about the confusion.

---

### Post by Songwind on 2007-03-05
The screen resolution issue is due to the fact that the applet only gives you the options defined in your /etc/X11/xorg.conf file.

There are a ton of possible configurations for that file, and it's very easy to break X so that it doesn't work anymore with it.  Read some online tutorials (I don't have my links here, but there are a bunch) and make a backup copy before you change anything.

Then if X breaks and you are stuck with the terminal window you can copy your known good configuration back and restart. :)

The configurations you're looking for are in the "Screen" section, on the "Modes" lines.

The refresh rate is calculated by the info Xorg has regarding the max and min vertical and horizontal refresh, and it always uses the highest.  If you want to have it use something lower, that can go in the Modes section, too.

---

### Post by Mr. Svinlesha on 2007-03-05
Wow.  I started with one of the absolutely easiest suggestions -- type "rm .dmrc" into the terminal -- and it seems to have worked like a charm.

But can anyone out there explain to me what, exactly, I just did?

---

### Post by aysiu on 2007-03-05
*rm* is short for *remove*.

You removed the file *.dmrc*

The .dmrc file specifies what session you use for your login. Go ahead. Open the .dmrc file with a text editor. You'll see what it does.

Go to Places > Home Folder. Then Press Control-H. This will show hidden files. One of the hidden files will be .dmrc (which should have been regenerated after you deleted it). Double-click that file and look inside.

For example, this (in bold) is what my .dmrc file contains: ```
ubuntu@ubuntu:~$ cat .dmrc
[b][Desktop]
Session=IceWM[/b]
ubuntu@ubuntu:~$ 
```

---

### Post by Mr. Svinlesha on 2007-03-05
Mine reads:

> [Session]
desktop=defaultThat sound about right?

Now I'm working on fixing my screen resolution problem.  I've made a backup of the xorg.conf file, and am about to start modifying it.  The instructions seem awfully hairy to a beginner such as myself, so any help would be appreciated.  I think I understand the first bit about the horizontal and vertical refresh rates; but the modeline has me a bit worried.

By the way, I've just purchased a Samsung SyncMaster 940BW, 19" wide-screen.  

I've found an online modeline tool, but it doesn't have my recommended screen resolution available in roll-down menu -- 1440 x 900.

Any and all help gratefully appreciated.

---

### Post by aysiu on 2007-03-05
This trick has always worked for me, but I'm not sure if you'll need to take extra steps or not.

Here are some commands to copy and paste. If you choose to retype, please be very careful and keep in mind that everything is case-sensitive.

Make a backup copy of your xorg file ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` Edit the file ```
gksudo gedit /etc/X11/xorg.conf
``` Find the lines in the Monitor section that say *HorizSync* and *VertRefresh* and modify them appropriately. If those lines don't exist, add them. Whether you have to add or modify them, they should eventually look like this (according to [Samsung's specifications for the monitor](http://www.samsung.com/ca/products/monitor/lcd_digital/ls19hawkbqxaa.asp?page=Specifications)): ```
HorizSync 30-81
VertRefresh 56-75
``` Then save the file and exit Gedit.

Make sure you close any programs you have open and press Control-Alt-Backspace. This will reset the X (graphical) server and make your changes take effect.

If, for some strange reason, it doesn't work, and you end up at the command prompt, you can restore your old configuration with these commands: ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

---

### Post by Mr. Svinlesha on 2007-03-05
Under the Monitor section I read:

Identifier:   "Generic Monitor"
Option:       "DPMS"

and no "End Section" line.

Should I insert 

HorizSync      30-81
VertRefresh    56-75
EndSection

With the correct values for my monitor here?  Do I need to change the identifier?

---

### Post by Mr. Svinlesha on 2007-03-05
Sorry -- posted before I read your reply.  Back in a few minutes.

---

### Post by aysiu on 2007-03-05
That's weird. There *should* be an End Section line. For example, mine says ```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection
```

---

### Post by Mr. Svinlesha on 2007-03-05
It popped up when I added the extra lines.

Before I execute, I got this error message after launching geedit:

> (gedit:6940): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Is that something I should be worried about?

---

### Post by Mr. Svinlesha on 2007-03-05
Well, I've followed all the steps so far, with no noticeble difference.  The screen resolution applet still has the same options.

Next step?

---

### Post by aysiu on 2007-03-05
> **Mr. Svinlesha said:**
> It popped up when I added the extra lines.

Before I execute, I got this error message after launching geedit:



Is that something I should be worried about? No, it's not. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **Mr. Svinlesha said:**
> Well, I've followed all the steps so far, with no noticeble difference.  The screen resolution applet still has the same options.

Next step? Darn. That's worked for me on two of my monitors.

There are a bunch of other things you can try, but I don't have experience with them:
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by Mr. Svinlesha on 2007-03-05
I've added both the HorizSync and VertRefrehs, and generated and insterted a modeline, and see thus far absolutely no difference.

Any other suggestions?

---

### Post by aysiu on 2007-03-05
> **Mr. Svinlesha said:**
> I've added both the HorizSync and VertRefrehs, and generated and insterted a modeline, and see thus far absolutely no difference.

Any other suggestions?
None from me. I'm hoping someone with more screen resolution problems experience will jump in.

---

### Post by Mr. Svinlesha on 2007-03-05
What about this "X-Window" and "X86Config" file, that I mentioned in the OP?

---

### Post by Mr. Svinlesha on 2007-03-05
Look, thanks anyway very much for your time.  I really appreciate it.

I'm sure I'll find an answer sooner or later.

---

### Post by Mr. Svinlesha on 2007-03-05
Moving on to the next problem, then...

When I paste:> sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list...in order the enable my extra repositories, I get the following error message:

> mv: cannot stat `/etc/apt/sources.list': No such file or directory

What now?

---

### Post by aysiu on 2007-03-05
Just skip that step, then and edit the blank document and paste in the appropriate code.

I don't know why you don't have an /etc/apt/sources.list, though. I thought a default Ubuntu installation always had one.

---

### Post by Mr. Svinlesha on 2007-03-05
Well, that seemed to work well enough.  Thanks, aysiu!

One final question before I sign off for tonight -- how do I activate the screensaver now that I've got it?  It doesn't show up on my list.

---

### Post by aysiu on 2007-03-05
That's weird. I just tried it out and didn't see electric sheep in the list either.

I did run the command *electricsheep* and got this output: ```
ubuntu@ubuntu:~$ electricsheep
please be patient while the first sheep is downloaded...


``` There's a blinking cursor. I'm not sure how patient you're supposed to be, but I've been waiting about three minutes, and nothing special's happened.

Then I saw if *electricsheep* had a manual by typing ```
man electricsheep
``` and it does, but I don't understand it: ```
ElectricSheep(1)                                                                                                                         ElectricSheep(1)

NAME
       electricsheep - a distributed screen-saver (version 2.6.8-debian1)

SYNOPSIS
       electricsheep [--nick name] [--url url] [--nrepeats N] [--max-repeats N] [--frame-rate N] [--nthreads N] [--server host/path] [--display-anim 0/1]
       [--show-errors 0/1] [--standalone 0/1] [--save-dir path] [--reset-fuse N] [--history N] [--nice  N]  [--proxy  URL]  [--proxy-user  user:password]
       [--timeout  N]  [--start-sheep  N]  [--root  0/1]  [--voting  0/1] [--anim-only 0/1] [--debug 0/1] [--player program] [--mplayer 0/1] [--zoom 0/1]
       [--player program] [-window-id id] [--bracket-begin date/id] [--bracket-end date/id] [--data-dir dir] [--logfile file]

DESCRIPTION
       Electric Sheep is a distributed screen-saver that harnesses idle computers into a render farm with the purpose of animating and  evolving  artifi&#8208;
       cial life-forms.  It requires a high-bandwidth, always-on connection to the internet such as DSL or cable-modem.

       The first time it runs, it normally takes about 10 minutes before a sheep (as the animations are called) is downloaded and displayed.  After that,
       it should come up immediately.  You can use BitTorrent to download more sheep faster, see the web site below for how.

       If you have installed the hacked xscreensaver that supports passing key-presses onto the graphics hack and this feature is enabled, then  pressing
       the  up  (or down) arrow-key transmits a vote for (or against) the currently displayed sheep to the server.  Vote for the sheep you like, and they
       will mate, reproduce, and evolve!

       The shepherds (those who wrote the software and run the server) use some of the sheep for commercial purposes in order to support the network  and
       develop  it  further.   For  example there&#8217;s the Spotworks DVD, and "Dreams in High Fidelity", a painting that evolves.  Some jobs rendered by the
       network may be for images or animations which are not sheep at all, and will not appear in the screen-saver.

       Users may not subvert the protocol of the sheep server.  If you want to change how the client communicates with the server, contact  the  server&#8217;s
       administrators first.

OPTIONS
       --anim-only 0/1
               If 1 then do not clear the background and display the logo.  The default is 0.

       --bracket-begin date/id
               Play no sheep before this one or this time.

       --bracket-end date/id
               Play no sheep after this one or this time.

       --data-dir dir
               Set the directory to find splash images and other data files.

       --debug 0/1
               If 1 then print copious debug information.  The default is 0.

       --display-anim 0/1
               If 1 then display the animated sheep, if 0 then do not.  Not displaying the sheep allows one to contribute rendering more rendering cycles
               because no CPU time is spent on display.  It also allows one to run on a computer without an X display at all.  The default is 1.

       --frame-rate N
               Specify the frame-rate for sheep display in frames per second.  The default is 23.  If your client is  having  trouble  completing  frames
               because  it is spending all its CPU time in the display process then decreasing this might help.  Or increase it if you have extra CPU for
               smoother display.

       --history N
               Set the number of sheep of history to keep.  Sheep in the history are not repeated if possible.  The history is written to  a  file  named
               "id" in the .sheep directory, with one sheep id per line, with the most recent one first.  The default history length is 30.

       --logfile file
               Write errors and diagnostics to this file instead of stderr and stdout.

       --max-megabytes N
               Specify  the  maximum number of megabytes of disk storage to use to store sheep (in the directory specified with --save-dir).  The default
               is 1000.  Zero (0) means there is no maximum.

       --max-repeats N
               Maximum number of times to repeat any sheep.  The default is 3.

       --mplayer 0/1
               If 1 then use MPlayer (http://mplayerhq.hu) instead of the built-in mpeg decoder.  The default is 0.

       --min-megabytes N
               Specify the minimum number of megabytes of disk storage to leave free.  The default is 1000. Zero (0) means there is no minimum.

       --nice N
               Specify the priority adjustment for render process and all non-display processes.  The default is 10.   Note  that  xscreensaver  normally
               nices the sheep process by 10 already.

       --nick name
               Specify  a nickname.  The server keeps credits the frames according to nickname and ranks nicknames according to who contributes the most.

       --nrepeats N
               Number of times to repeat each sheep.  The default is 2.  Transitions between sheep are not repeated.

       --nthreads N
               Specify the number of rendering threads.  By default there is one (1).

       --player program
               Specify a program to display the sheep.  The default is mpeg2dec_onroot.

       --proxy URL
               Specify a proxy as per curl(1).

       --proxy-user user:password
               Specify a proxy user and password as per curl(1).

       --reset-fuse N
               Specify the maximum number of sheep to display in continuous fasion before resetting and displaying a random sheep.  The default is 300.

       --root 0/1
               If 1 then display on the root window.  The default is 0 and to display in a new window.

       --save-dir path
               Specifies a directory to save the sheep in.  The default is ~/.sheep.

       --server host/path
               Specify the server to connect to.  Do not include the leading "http://" or a trailing slash.

       --show-errors 0/1
               If 0 then do not report problems connecting to server.  The default is 1.

       --standalone 0/1
               If 1 then run without connecting to the internet at all, just displays the sheep already downloaded and do no rendering.  The  default  is
               0.

       --start-sheep N
               Specify the ID of the sheep to display first.  The default is to display a random sheep.

       --timeout N
               Specify the timeout in seconds for server operations.  The default is 401.

       --tryagain N
               Specify the time in seconds to wait before retrying to contact the server.  The default is 696.

       --url name
               Specify a vanity URL to go with with the nickname.

       --voting 0/1
               If  1 then enable the voting interface.  This requires a hacked version of xscreensaver as described in the README in the source distribu&#8208;
               tion.  The default is 1.

       -window-id X
               Specify in hex the window ID to draw into.  Note the single leading dash (this option&#8217;s syntax is required by xscreensaver).  The  default
               is to display in a new window. If both --root and -window-id are specified then -window-id takes precedence.

       --zoom 0/1
               Zoom the sheep to fill the screen.  The default is 0.

ENVIRONMENT
       DISPLAY to get the default host and display number.

SEE ALSO
       X(1), xscreensaver(1), http://electricsheep.org,

AUTHOR
       spot aka Scott Draves

X Version 11                                                                                                                             ElectricSheep(1)
```

---

### Post by Mr. Svinlesha on 2007-03-06
Aysiu:

I tried PMing you but you weren't at home...so 

Hej, aysiu!

I just thought I'd let you know that I finally solved my screen resolution problem.  I discovered that I had missed a simple but crucial step: manually adding the desired resolution under the "Section Screen".  When I finally did that and restarted, it worked like a charm: well, except for the fact that refresh rate is 75 rather than 60.

Anyway, just wanted to thank you again for all the help.

By the way, about electric sheep: if you haven't tried it, you should.  The screen saver is a bit torrent downloader that works with other computers in a network to generate incredibly beautiful images.  But you do have to wait more than three minutes to get it to work...more like 12 hours the first time, while it downloads the first torrent.

Anyway, here's a manual walkthrough on how to install it, if you want to, only for dapper, apparently:

[http://ubuntuforums.org/showthread.php?t=355607](http://ubuntuforums.org/showthread.php?t=355607)  


See you around!

---

### Post by Songwind on 2007-03-06
You can set the refresh rate explicitly in the Section Screen

Instead of "1440x900" you should put in "1440x900_60"

---

### Post by aysiu on 2007-03-06
Thanks for the update. Glad it worked out for you. I think I'll pass on electric sheep, though.

---

