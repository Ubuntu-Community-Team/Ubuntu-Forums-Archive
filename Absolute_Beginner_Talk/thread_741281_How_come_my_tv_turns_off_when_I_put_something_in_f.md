---
title: "How come my tv turns off when I put something in fullscreen?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-31
Okay, so I was having an issue a while back trying to figure out how to get my TV and monitor to simultaneously show the same display. I figured that out. The following is a post I had recently added to an unrelated topic:


Well, come to find out, in "NVIDIA X Server Settings", all I had to do was go into the "X Server Display Configuration" and change the TV Resolution to "Auto" and the Position to "clones", keeping the monitor with Resolution at "1024 x 768" and Position at "Absolute". I hit apply and, that works perfectly fine for the same display on my monitor as on my TV.

However, whenever I try to put something into fullscreen (from a media player that is, myspace works fine as its not actually truelly fullscreening) my tv cuts off and only the monitor continues to work. If it is a game that goes into fullscreen, such as alien arena, or an emulator, as soon as I leave the program, the TV display returns... unlike when I use a media player to watch a video file.

Whenever I go back into my "NVIDIA X Server Settings" I see that all my settings are set back to what they were before the TV cutoff. Once again, I can set everything to what I said I had things at previously and once I hit apply, BLAM! It's back to being on both screens... but if I put anything back into fullscreen then its back to having only my monitor again.

What can I do to make it so that once, I put something into fullscreen it will remain on my TV as well?

**_[COLOR="Red"]EDIT #1:[/COLOR]_** So, come to find out, the reason why it flipped back to only showing up on my monitor after I opened a full screen game was because all of those games had to be preconfigured. Also, the movie player I was using "Totem Movie Player" seems to have some sort of bug that forces the display back to the monitor shutting off the TV display. I've come to this after opening the AVI with another movie player "MPlayer Movie Player". However, if you go to Edit -> Preferences in "Totem Movie Player" Under the General tab is a little section called: TV-Out which has 3 options under it. No TV-out, TV-out in fullscreen by Nvidia (NTSC), and TV-out in fullscreen by Nvidia (PAL). The default selection seems to be "No TV-out" as the other two are "grayed out". Perhaps there is a fix for this somewhere I could download, but that's not really the issue anymore. I suppose the only problem I'm having anymore is that when ever I turn on my computer, I have to change all the settings in "NVIDIA X Server Settings" again. It always goes back to defaults even after I click "Save to X configuration file". So, if I want to use my TV I'll have to always go and first change the resolution on the TV from "Off" to "Auto", and make sure the position says Absolute under both the monitor and the TV. I know previously I was saying that I had to set one of them to clone, but I guess this is no longer true. As when I do the clone feature it tends to only have the TV work without the monitor, and only shows both displays when both say "Absolute". I have it set for Twinview and considered trying one of the other 2 options, but whenever I tried Seperate X Screen (Requires X Restart) and I applied what changes were possible to change, saved to the X configuration file, and restarted my X... Once again all the NVIDIA X Server Settings are right back to where they were originally. Its as if I'm not aloud to make any lasting changes in it, and everything reverts to a default after every restart. The other configuration option is just called "Disabled" and that didn't sound too pretty at all. I JUST WANT TO BE ABLE TO MAKE LASTING CHANGES!!!!

On a minor note:

I cannot access "Screens and Graphics" or "Frostwire" ever since I've begun messing around with the ever defaulting NVIDIA X Server Settings.

---

