---
title: "Mac mini:  simple script to use Apple remote in MythTV"
date: 2007-04-02
forum: Apple Intel Users
---

### Post by eldoran on 2007-04-02
I have a mac mini (intel duo core) running Ubuntu w/MythTV and wanted to use the built-in IR receiver and the supplied remote to control it.   I messed around with lirc for hours and became frustrated - couldn't make it work.   Then I saw some post somewhere about doing a 'cat /dev/hiddev0' ..   The Apple IR receiver is using device /dev/hiddev0.  So I typed that in a terminal session, and as I clicked my apple remote - I saw strange characters pop up on the screen.  Cool!  Just need to examine them and see what each key corresponds to.   So I built a script to do that and found what each key press on the remote corresponded to.   

Now what to do with it?   I happened to see in the MythTV doc about a telnet interface to allow you to control mythtv.   So I started up MythTV, enabled that feature (which listens on port 6546), restarted MythTV, and logged in via ssh and tried this:

echo "key down" | nc -q 0 localhost 6546

The highlighted item in the MythTV menu moved down!  Far out!  So now I have a way to grab input keys from my remote, and to send them to MythTV.

Before I go further - here's the script that I startup to capture the IR commands and send them to Myth (it's in REXX believe it or not, but I think it's very simple and readable):
```

#!/usr/bin/rexx
/* mpk>  Capture data from hiddev0 and send real cmds to Myth */

/* Ignore any of these byte values */
ignore = '0 255 135 238 122 247'
/* Setup an array with the 'real' commands and the key they correspond to */
cmd.3 = "escape"        /* Menu key */
cmd.5 = "enter"            /*  Play key  */
cmd.6 = "right"             /* rest match directions*/
cmd.9 = "left"
cmd.10 = "up"
cmd.12 = "down"

Do Forever
 in = c2d(charin())      /* Get a byte --  will wait until it gets one */
 If wordpos(in,ignore) > 0  Then Iterate     /* In our ignore list?  Then keep looping */
 Say cmd.in                            /* Output (this is for testing sake only - not needed)   */
 Call Sendmyth cmd.in       /*  Send our command */
End
Exit

Sendmyth:
Parse Arg sendcmd                 /* Get argument passed and put into 'sendcmd' */
                                                    /*  Issue the 'key command' to mythtv (port 6546) */
'echo "key' sendcmd'" | nc -q 0 localhost 6546'
Return


```

I execute:   cat /dev/hiddev0 | /home/eldoran/mpk       and when I go into MythTV, I can use my remote to control (most) menus.   Myth does provide a 'query location', which I would probably use to make more contextual keys..  (like send 'M' when you are in photo gallery to get to the menu).

Anyway - for my purposes, this worked great..  except when I tried to play videos..   mplayer was kicked off and of course, didn't receive anything I was sending to Mythtv.    I found you can start mplayer in slave mode and send it commands via standard input.  (e.g. send 'pause' and it pauses, send 'seek +10' and it goes forward 10 seconds).   Cool! -- I can use the same concept for mplayer -- so another script:

```

#!/usr/bin/rexx
/* mplayerm - send keys to mplayer  */
out = ''
ignore = '0 255 135 238 122 247'
cmd. = ''
cmd.3 = "quit"
cmd.5 = "pause"
cmd.6 = "seek +30"
cmd.9 = "seek -15"
cmd.10 = "vo_fullscreen"
cmd.12 = "vo_fullscreen"

Do Forever
 in = c2d(charin())
 If wordpos(in,ignore) > 0  Then Iterate 
 Call SendMplay cmd.in 
End
Exit

SendMplay:
Parse Arg sendcmd
Say sendcmd      /*  Just spit it out to mplayer */
If sendcmd = "quit" Then Exit      /*  Exit this script too if we are really quitting mplayer */
Return

```

Great - now I made another little bash script called 'mythmplay' that does this:

cat /dev/hiddev0 | /home/eldoran/mythmplay | mplayer -slave -quiet -fs $1

typed  in:  mythmplay  moviefile.avi

Bam!   mplayer pops up and my apple remote controls it -- pause/play - skip forward, back - and can toggle on/off fullscreen  and exit.

But here's my problem and mainly why I'm writing this post (besides feedback on how I've gone way off track here and am rebuilding a wheel):

-  If go to MythTV and put into my video player settings:    /home/rohling/mythmplay %s

When I select a video -- it just stays at '...Loading' and doesn't start up mplayer..    If I type the same command from a bash shell -- no problem - works great.

Any ideas, comments?  Is this worth pursuing or do I just need to get lirc going?   Since I was able to do so much with just a couple simple scripts, I got kind of excited and am maybe just trying to recreate lirc for apple.. I don't know.  But it mostly works, so I thought I'd share it and see if anyone can tell me why mythtv can't seem to call mplayer thru my script....

Thanks!

---

### Post by eldoran on 2007-04-02
Well - solved my own problem calling from mythtv - just needed to add:
#!/bin/bash

to the top of my script and now it seems to work..   However -- I am now sending keys to both mplayer and mythtv.  Mythtv just sort of 'saves' them.. and when I exit a video - it then executes them.   (like if I hit the right key to ff the video.. when I come back - mythtv acts like the right key was hit).   So I need to know the location where mythtv is and either ignore keystrokes or do something different depending on where I am.

The question stands though -- is this helpful or am I just building what's already been built?

---

### Post by Azathoth_ on 2007-04-02
Thanks... I suppose this works in Edgy, because in Feisty (in the Beta) apple remote works by default and to work with others software.

I have linked it in my blog ;) [http://magarto.com/blog/archivo/2007/04/02/script-para-usar-el-apple-remote-con-mythtv-en-ubuntu/](http://magarto.com/blog/archivo/2007/04/02/script-para-usar-el-apple-remote-con-mythtv-en-ubuntu/)

---

### Post by eldoran on 2007-04-02
Thanks!    I am downloading feisty now.. I appreciate the tip!  You were correct that I was running Edgy (6.10).

This was a good exercise just to understand how lirc probably works (it reads from the correct IR device much like I did)..   and how interfaces to various programs (like mythtv and mplayer) can be accomplished.   So even though I'll probably dump it after playing some more, it was a great learning experience.

I solved the problem of sending commands to both mythtv and mplayer:

-  Have mythmplay script do 'echo "YES" > /home/eldoran/mplaystat'
-  have my mpk script check if mplaystat contains YES -- if so - it doesn't send the commands to Mythtv.
-  Have mythmplay script do 'echo "NO" > /home/eldoran/mplaystat' before exiting
-  Mythtv is now passed commands

Anyway - next I'm going to play around with checking elapsed time between key presses and doing something different if they are less than a second apart..  Either for the same key or combinations.  (double click 'up' to zoom out - single click for volume, etc)

Linux is just too cool  ;-)

---

### Post by Azathoth_ on 2007-04-02
These would be great... we will wait for it ;)
Thanks

---

### Post by eldoran on 2007-04-03
Here is my updated script..  I abandoned a separate script for mplayer, because I found that setting MythTV players to 'Internal' let me keep talking to MythTV.  So - to use the script:

-  Set players to 'Internal' in MythTV
-  The play/pause key can be 'toggled' to either send 'enter'  (when you are in menus and selecting things) - or 'P'  (when you are playing video and want to pause/play).  You toggle by clicking play/pause twice quickly.  One downside is the first key is acted upon before the toggle occurs, but this hasn't caused me much problem.
-  I use a startup script as follows to make use of the script:

mythirstart
#!/bin/bash
cat /dev/hiddev0 | /home/eldoran/mythir

And here is 'mythir':

```

/* mythir:  Capture data from /dev/hiddev0 and send keys to MythTV */
cmd. = ''                 /* Null out cmd array */
cmd.3 = "escape"    /* Menu key */
cmd.5 = "enter"      /* play/pause key */
cmd.6 = "right"       /* direction right */
cmd.9 = "left"         /* direction left   */
cmd.10 = "up"        /* direction up */
cmd.12 = "down"   / * direction down */

Do Forever
 in = c2d(charin())                                 /* Read in one char, convert to decimal */
 If cmd.in = '' Then Iterate                     /* If not in our cmd array, then skip      */
 Say cmd.in                                          /* Remove to make this script quiet       */
 If in = 5 Then Do                                /* Did we press our 'toggle' key?          */
   lastenter = time('R')                          /* How long since last time?                  */
   If lastenter < .5 Then Do                   /* If less than half a second, then toggle */
     If cmd.5 = 'P' Then cmd.5 = 'enter'  
       Else cmd.5 = 'P'
   End
 End
 Call Sendmyth cmd.in                          /* Send the command to MythTV          */
End
Exit

Sendmyth:
Parse Arg sendcmd
'echo "key' sendcmd'" | nc -q 0 localhost 6546'
Return

```

I'm sure this could be coded in 'bash' and be more easily shared, but I am much better/faster at REXX then other languages.  Plus REXX has a handy time() function.   But the logic is boringly simple.

---

### Post by Azathoth_ on 2007-04-10
Good job

---

### Post by stueng on 2008-05-31
I have installed Hardy on my iMac and with after tweaking the source code for ubuntu-modules I have the remote working the way it is supposed out of the box with Hardy

A lot of tutorials about using lirc with mythtv always refer to /dev/hiddev0

This doesnt exist in Hardy

Any ideas what I am supposed to be substituting with, or how I get this /dev/hiddev0 ??

Stu

---

