---
title: "MythTV Customizing Questions"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by bconverse on 2007-10-29
Hi all,
Ok, I've recently started dual booting XP and Ubuntu Gutsy.  I love it and may very well switch, that is, if I can get MythTV properly configured.  I am new to Ubuntu, so the guides for configuration online are not always easy to follow and I often think that I am simply forgetting a simple step, so hopefully I can get this stuff figured out. 

I installed MythTV using Mythbuntu, basically because the control center was a lot easier to use.  I set the remote to Happaugue Remote, as I have a WinTV PVR-350.  The remote works, but I can't seem to use all of the buttons.  I don't know if this is just how it functions on Ubuntu, but, is there a way that I can activate all the buttons? (its the 45 button remote)

Also, I'd Set the Green Power button on the remote to start/stop the front end.  I've found a few instructions on how to do this in command line, but I don't seem to be having much luck. Again, I may just be entering commands incorrectly, but I have no idea.

Next issue.  I have pictures and video on a media hard drive that is NTFS formatted.  I was able to get my music to display in mythtv using the music plugin, but the picture and video stuff, even when I set the directory to where it is located on the media disk, nothing shows up in the frontend. I've tried re-entering the directories several times, but still no files show up. Both plugins are installed, so I am not too sure what is happening there. 

Next..When I am watching TV, the picture is "centered" on the screen.  I have a widescreen monitor, and I'd like it to fill the screen, despite a little distortion.  In the front end setup, I selected to have the video output be the same resolution as the GUI, but, no such luck. 

This next question is more of a linux noob question than anything, but, I am trying to add new themes to Myth.  I downloaded the tarballs, but, I can't seem to install them properly.  When I enter the command, and where to extract it to, it tells me the file does not exist.  I downloaded them to the desktop.  I've tried this both in and out of root, and I can't seem to get anything.  
Along these lines, I am also trying to install a new OSD theme. There is an option to change the MythTV main theme, but I can't find anything on changing the OSD theme? There is obviously a way, as alternate OSD themes exist, but how?

One final thing (I know, getting long) I cannot play .avi files in *any* player, including VLC. Once a file is opened, the player shows a series of colors.  There is audio, but the picture just stays that way.  I've noticed this seems to be a common problem..any solutions as of yet?

Ok, well, I don't expect everything to be anwsered,  but if you can help, try and give me really detailed directions, as using the command line is still new to me, and even the simplest, common sene type step would be useful to me.


Thanks for any assistance.

---

### Post by BatPenguin on 2007-11-02
Hello there,

I'm not an expert by any means but been using Ubuntu and Myth for about a year or so now, so hopefully I can help a bit. I did pretty much what you did (dual boot with XP, experiment with Ubuntu) around the time of 6.06 and 6.10 and now  (Gutsy) I've finally actually given up on XP altogether. So I hope I can be of some help...first of all, hang in there, Myth can be pretty terrilbe to set up. So, I'm no expert but a couple things I probably might be able to help with:

1) can you please post EXACTLY what you're trying to do with the theme installs. A good way to start is to copy the download file to your home directory and then type the tar commands from there. Use nautilus (file manager) to copy and extract the downloaded files if you want to (I do), but do the copying to myth folders in the terminal to see messages. Try that and post what happens, I'm sure we'll figure this out. Post the links to the themes you want too, I'll see if they work on my machine. Use sudo if the install goes to directories that need it.

2) The video directories (NTFS) are all local, right? I You're not trying to be fancy with links or anything? Just making sure. I presume you've triple-checked all typing...case sentive and all. For me these problems have always been a) permissions or b) typos and such. So if no typos, just make sure the windows directories are readable by the Mythtv user. My guess is this, permissions. You can check this by going to the directory (or the one right above it) in the file manager and selecting Properties. See if mythtv user (or "others") can read the files. If that's the problem, you need to change the permissions so your myth user can see the files.

3) And the video playback issue: you have an Nvidia card, I guess? I've been having video playback issues ever since switching to Gutsy too. Really annoying. Same thing, audio fine, video just colored lines etc. What I've done to help this: 

- see if disabling or enabling Compiz-Fusion helps (Preferences -> Apperance -> Disable effects) helps
- update to the latest Nvidia driver by installing envy (look up instructions on this elsewhere on the forums)
- change playback to use OpenGL OR to use XV, just see what works. For me, I have: latest nvidia driver (7950 is my card), Compiz-Fusion on, video programs use OpenGL (except Myth which works anyway).

I was using beryl with 6.10 and 7.04 without video problems...seems like Gutsy broke some things. Very disappointing, frankly.

I have the hauppage 150, don't know about the 350's remotes, so can't really help you there. Try looking for a thread about that card and setting up lirc for more.
 
Anyway, this is just a start, I'd be happy to try to help you more if I can.I'll subscribe to this thread, lemme go how it goes!

---

### Post by scmason on 2007-11-06
If you want to change the OSD theme in Myth TV, it is kind of hidden.

Goto Utilities/Setup -> Setup -> TV Settings -> Playback and it is about the 8th menu in, under 'On-Screen Display'

As far as installing regular themes, jst unzip/extract them locally and then move them to /usr/share/mythtv/themes.

---

### Post by bconverse on 2007-11-06
Thanks guys, I acutally forgot I posted this. Whoops. I managed to get that stuff worked out, Myth is now working like a charm.

Thanks agian!

---

