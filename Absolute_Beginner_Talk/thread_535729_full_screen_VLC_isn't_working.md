---
title: "full screen VLC isn't working?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-08-26
I am having trouble getting vlc full screen.  When I play things full screen now since I'm using 64bit ubuntu, I can't seem to get a real full screen.  In that it won't take over the entire screen.  I still have the panel bars on the bottom and the top, which is annoying if I'm trying to watch a video with VLC.

any help is appreciated.

---

### Post by S15_88 on 2007-08-26
i've got the same issue, quick question do u use beryl or any other desktop effects programs and do u have desktop on a cube enabled.  

what i do to get around it is open VLC on one workspace, then play the movie, drag the small screen to another workspace...fullscreen it, and that's where i can still see the panels adn if i have GDesklets or any windows in that workspace they cover the movie as black space...so then if i click on the fullscreen movie everything goes black then i ctrl+alt+left or right to another workspace then back again and everything is fine but if the movie isn't widescreen with the black space above and below the panels will show up just as black in the screen.  

very annoying problem if anyone can help us out it would be greatly appreciated!

Thanks, Alain

---

### Post by chessercizes on 2007-08-26
hey guys

i had this problem and i found a solution that worked for me

Open up VLC and go to Settings > Preferences.
Check the Box that says "advanced options".
Then expand the Video section in the left side.
Click on where it says Output Modules and change it to XVideo extension video output.
Then go to  XVideo under Output Modules, and check the option that says alternate fullscreen method

This got it to work for me i hope it does for you to.

Best of luck!

---

### Post by bone2006 on 2007-08-27
S15_88 I do not have berly or any desktop effects enabled.  I'm not sure if it's something to do with the video driver.  I was using ubuntu 32bit for awhile and never had an issue and reinstalled ubunut a few times.

I've switched to the 64bit version and now is when I'm seeing this problem, so not sure if it could be the restricted nvidia driver that's the issue or something else.

I'm using mythtv and the audio is out of sinc with mplayer, yet when I'm not using mythtv and I play the video with vlc it works out just fine, which if I'm not mistaken vlc uses it's own built in codec, so it seems to play everything.   

chessercizes thanks for the repsonse.................I'm not infront of my machine right now, but as soon as I get a chance I'll try it out.

---

### Post by S15_88 on 2007-08-27
> **chessercizes said:**
> hey guys

i had this problem and i found a solution that worked for me

Open up VLC and go to Settings > Preferences.
Check the Box that says "advanced options".
Then expand the Video section in the left side.
Click on where it says Output Modules and change it to XVideo extension video output.
Then go to  XVideo under Output Modules, and check the option that says alternate fullscreen method

This got it to work for me i hope it does for you to.

Best of luck!
tried that, it actually made it worse haha the picture would full screen to the panels only!  i'm going to try some of the other settings, thanks for the input though can't find an answer without trying other things!

Thanks, Alain

---

### Post by bone2006 on 2007-08-27
It worked, but it didn't.  I tested it over and over and it only works if I open the file and quickly double click to make it full screen, if I take it out of full screen I'll get the top panel.  If I need to fastford or rewind as I normally do out of full screen I can't return to full screen without the top panel.

---

### Post by jw5801 on 2007-08-27
It's a known 64-bit issue!
Here's my solution:
As an alternative to using the "alternate fullscreen method" (I've had vlc crash whilst fullscreen using the alternate method and not being able to switch to any other windows to fix it), you can leave the normal "fullscreen" (opens a new window with only a titlebar), and then use gnome to put this window to fullscreen (stops displaying the gnome-bar and the titlebar of the window, you can do it for any window). You'll need to enable a global shortcut key to do it (System > Preferences > Keyboard Shortcuts, and there will be an option for it under the "Window Management" section called "Toggle fullscreen mode." I have it set to WinKey+f) and it eliminates the problem of the top bar returning.

There's also already a lot of threads about this, the one I posted the above in is [here](http://ubuntuforums.org/showthread.php?t=87085).

Also, it's a Metacity issue, as I don't encounter it using Compiz-Fusion. Although that has it's own little potful of issues (it is only alpha after all).

---

### Post by Ux64 on 2007-12-25
Description wasnt enough detailed, so I'm not sure if this is same problem.

Only overlay area is updated. What's outside overlay area might be left untouched, or not. It depends from time to time. If I full screen 10 times, full screen might work correctly 3 times out of those 10. ;)

Here is screenshot during the problem. When playing movies (wider image) edges are even larger because overlay area is smaller due different aspect ratio.

- Ux64

Click for full resolution version.

[[IMG]http://picozilla.com/files/147187tedges.jpeg[/IMG]](http://picozilla.com/en/147187/edges.png.html)

Version information:
Ubuntu 7.10 GG 64 bit, VLC 0.8.6c

---

### Post by jw5801 on 2007-12-25
You're seeing a different issue. The issue in this thread was that when using: Gnome + Metacity on 64-bit Feisty, VLC running fullscreen would appear behind the top and bottom panels. The picture itself rendered fine. I'm not sure what's causing your issue, but a new thread will probably get more hits!

---

### Post by clubsoda on 2007-12-27
> **bone2006 said:**
> ...double click to make it full screen...Nice!  The hotkey detection for fullscreen is broken here - it's been driving me batty.

---

### Post by bone2006 on 2007-12-28
Kind of strange I saw this post today...............my full screen in 64bit ubuntu is working with VLC now.  Just today I tried playing something with VLC and forgot that full screen doesn't work for that system, but when I tried full screen came up.  It was an mkv file, which I never play though

---

### Post by jw5801 on 2007-12-28
Fullscreen works fine in Gutsy. It has since the release. This issue was present under feisty 64-bit + metacity. :p

---

