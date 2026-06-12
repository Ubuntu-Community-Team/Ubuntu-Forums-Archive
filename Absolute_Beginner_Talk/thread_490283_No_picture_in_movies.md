---
title: "No picture in movies"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-07-02
Hi, none of the films/DVDes on my computer work anny more. i can hear the sound but cannot se the picture, it's just black. that includes the Experience ubuntu.ogg movie so it can't be a problem with the codecs. 

I have tryed with Totem and VLC

---

### Post by Seisen on 2007-07-02
Did you accidentlly remove the codecs somehow and did they work fine before this?

---

### Post by ajmannen on 2007-07-02
Yes, they where all fine.  the problems started today

[[img]http://bildr.no/thumb/82262.jpeg[/img]](http://bildr.no/view/82262)

---

### Post by Seisen on 2007-07-02
Did you do any upgrades or anything major today before all this happened?

---

### Post by Inxsible on 2007-07-02
Not to ask the obvious, but did you connect your computer to another screen (monitor or TV) thru S-Video or any other means and then not remove the connection yet ?
 
This (black screen with sound) could happen because your computer is still projecting the video to the primary screen(TV or another monitor).

---

### Post by ajmannen on 2007-07-02
i have newer connected it to another screen then the one i'm using right now (some kind of Dell screen)

---

### Post by pudgymoogle on 2007-10-13
Obviously this is an old thread, but I'm having similar problems and I found it through a Google Search.

Both Totem AND VLC will play movies with sound and no image. (Just a black screen)

I'm an Ubuntu noob and it's the same with streaming videos from the Net. In VLC Player the videos will start, but if I access the program at all, it'll go black but continue playing the sound and counting down. Pausing/unpausing does not help. 

Most of the movies opened with Totem do not work except for sound. 

I'm using Ubuntu 7.04 and have all of the codecs in the default repos. 

Anyone have a clue? It's really starting to bother me, is it possibly my video drivers?

Thought it might have been the Window Effects but I turned those off and still have the same problem. Also there are certain windows that I will close, but they will remain in the taskbar and on screen. If I try to click close again, it will close the window behind it. 

I think there's a problem with my video drivers but I'm unsure how to go about fixing it. 

Thanks in advance for any help. 

-pudgymoogle

---

### Post by rfugger on 2007-10-24
I have the same problem.  I just upgraded from 7.04 to 7.10, so maybe the codecs changed somehow?

---

### Post by sujoy on 2007-10-24
well i have no such problems now in gutsy but earlier in fiesty, i could not play videos at all. The apps would just close at the moment i tried to play some video file, no matter what format.

so i guess its a problem with drivers. try getting the proper drivers (although it didnt help with my fiesty as i used it on my desktop with intel 946 chipset which had no drivr for linux) , but now my laptop with an intel 945 chipset works just fine.

however, try this at the command mode

dpkg reconfigure xserver-xorg

and follow the insstructions

---

### Post by stormoog on 2007-11-03
Solved similar problems using these instructions:

[http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/](http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/)

> Solving Video playback problems in Compiz Fusion / Beryl

Well, surely you love all of the wonderful effects that Compiz Fusion or Beryl can give to your desktop. But surely you also found out a lot of problems when trying to watch movies with your prefered Video player. An ugly black screen instead of you preferred TV show, full screen windows becoming semi-transparent…. well, that surely is not good. I’ve been looking in the net for a solution to all of this problems and I found this great article for what concerns the black screen but no info for the transparent fullscreen mode. Then I posted in the Compiz Fusion FOrum and I found a solution to this problem too :)

So let’s start working and see how we can get rid of all the problems with these very used movie players: GStreamer, vlc, Mplayer, xine e Realplayer.

Gstreamer

That’s the default Ubuntu player, used by Totem. To correctly visualize you video files with Totem proceed as follows:

1) Open a terminal and enter:

    gstreamer-properties

2) Move to the Video tag.
3) In default video plugin select “X Window System (without Xv)”.
4) Click on try to verify if it works fine.
5) Close this window, problems solved.

Vlc

That’s my preferred player, I always use it and surely many of you do too. It is very important to have it working correctly, so:

1) Run vlc.
2) Settings –> Preferences.
3) Selct Video and then outpoot modules.
3) Check the little “Advanced options” check box on the button left corner of this window.
4) New options will now appear, so in Video outpoot choose “X11 video out”.
5) Save and exit. Mission completed.
Mplayer

I never use it and every time I try to open something with it, it never works ;P but if you use it…:

1) Run Mplayer.
2) Right click on the screen and select Preferences.
3) Select the video tag and in available drivers choose X11 (XImage/Shm).
4) Save and restart the application.

Xine

Very useful if you use Kaffeine or Totem with xine:

1) Run xine.
2) File –> configure –> preferences.
3) In experience_level select “Master Of The Known Universe” so that all the setting become visible.
4) Select the video tag.
5) In driver choose “xshm”.
6) Restart Xine.

Real Player

Few passages are needed to configure it:

1) Run Real Player.
2) Move to Settings –> preferences.
3) Select the “Hardware” tab.
4) Uncheck the check box “UseXVideo”.
5) Restart Real Player.

Transparent Full Screen problem

This is a problem that only occurs with Compiz Fusion. So to set it properly we’ll need CompizConfig Settings Manager. You can access it from System –> Preferences in Gnome or using the Compiz Fusion Icon I described you in THIS article.

Now click on the “General” button (On the left) and then select the General Options button. Move to the Opacity Settings tab. Select the existing string, edit it and substitute it with this line:

    ((type=Unknown | Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer | state=fullscreen | name=^x11$ | name=^xv$ | name=^xine Video Window$)

Set the Opacity Value to 100 and click OK. The trick is done, try it yourself! The people there at opencomposite say that this is not a bug but a simple setting issue… well, that’s exactly what a bug is. Something unsolved that makes a program behave in a different way than that it should be meant to act. So, call it whatever you like, for me it is a bug and I’m sure you agree with me since it has to be solved manually and sistematically on each Compiz Fusion installation ;P



---

