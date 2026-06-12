---
title: "World Of Warcraft Graphics/FPS quality"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by peacebloom on 2007-06-05
I'm new to Ubuntu/Linux. I used guides and the wealth of informative posts to change my OS to Ubuntu and figure out how to run WoW through Wine. It was difficult but I finally got it running.

When I ran WoW in windows, I was able to use the Nvidia control panel and configure many graphical settings which I see no options for in the Ubuntu Nvidia settings. The game ran stunningly before, and held framerates around 50-60 consistantly. Now, when I use the game in Wine, using OpenGL, I get horrible framerates, and weird shaky graphics with rough edges that sort of make me sick. I've been tinkering all day with different settings, and I can't seem to improve the quality much.

Is there anything I can do to have the program run as beautifully as it did (I used quite high settings as my video card allowed it), or is that simply the limitation of running the program through Wine?

My system with 7.04 Feisty Fawn (64bit):
Asus A8N-SLI premium motherboard
AMD64 3500+ CPU
Nvidia GeForce 7800gt  (1.0-9755 drivers)
120gb hardrive
Dell 2007wfp @1680x1050

Any assistance is appreciated :D

---

### Post by rob1101 on 2007-06-05
im no linux expert but i don't think the game will ever run as good as it did on windows, because that is its native environment. you might want to try asking this in the gaming section of the forums.

---

### Post by khardbored on 2007-06-05
[http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)
GIve that a try..

---

### Post by pissedoffdude on 2007-06-05
Try adding the following lines to your config.wtf file:```
SET ffxDeath "0"
SET ffxGlow "0"
SET UIFaster "2"
```
You may also want to open up a terminal and type "regedit" then: 
1. Find HKEY_CURRENT_USER\Software\Wine\
2. Highlight the wine folder in the left hand pane by left clicking on it. The icon should change to an open folder.
3. Click right on the wine folder and select [NEW] then [KEY].
4. Replace the text "New Key #1" with OpenGL
5. Right click in the right hand pane and select [NEW] then [String Value].
6. Replace "New Value #1" with "DisabledExtensions" (without the quotes)
7.  Then double click anywhere on the line, a dialog box will open.
8. In the value field type "GL_ARB_vertex_buffer_object" (without the quotes). 

Be sure you have the following dlls in your /home/<username>/.wine/drive_c/windows/system32 (you might need to show hidden files from view>show hidden files) : 
[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)
[http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42)
[http://www.dll-files.com/dllindex/dll-files.shtml?riched20](http://www.dll-files.com/dllindex/dll-files.shtml?riched20)
[http://www.dll-files.com/dllindex/dll-files.shtml?riched32](http://www.dll-files.com/dllindex/dll-files.shtml?riched32)

---

### Post by meatpan on 2007-06-05
The nvidia-glx package has a utility, nvidia-settings, that provides some *basic* system level graphics configuration.  

One way to check a debian-based system (such as ubuntu) for the nvidia-glx package:

```
dpkg -l | grep nvidia-glx
```

If you don't have the package, it can be installed via ```
 sudo apt-get install nvidia-glx 
```
You can verify the nvidia-settings program exists and the locations of the associated installed files: ```
 dpkg -L nvidia-glx 
```

Good luck!

---

### Post by peacebloom on 2007-06-05
Thanks, I'll try those out and let you know how it went.

---

### Post by peacebloom on 2007-06-05
I already had:

SET ffxDeath "0"
SET ffxGlow "0"

in the config.wtf file, but I tried adding SET UIFaster "2" and it did nothing.

I already had done the regedit thing before I ever ran the game.

I checked for those dll files and I had 2/4, so I downloaded the other 2, placed them in the correct folder, and nothing changed.

I checked for the nvidia-glx package and I have it.

What next?

---

### Post by meatpan on 2007-06-05
I don't think I was very clear about what to do with the glx package.  I meant to say that you need to run the 'nvidia-settings' program.   Running the program should bring up a configuration gui that allows you to change some graphics preferences such as anti-aliasing.

---

### Post by peacebloom on 2007-06-05
I've done that and I've tried maxing out the settings just to see if the image quality would improve (disregarding FPS), and it still just doesn't look right. 

I understand if there are limitations to how well the graphics will look, but before I accept that, I want to be sure that there wasn't something I've missed, or something I haven't tried yet.

---

### Post by peacebloom on 2007-06-05
could it be something related to my CPU?

---

### Post by wylfing on 2007-06-05
First, a few facts.
1. WoW runs very well under wine.
2. Running under OpenGL does not limit the performance or visual quality of WoW.
3. Despite what rob1101 said, Windows is not the "native environment" of WoW. Blizzard always has a policy of equal treatment for Mac (which is why OpenGL is an equal performer).

Second, you should have followed the extremely easy directions for installation and configuration found [HERE]("https://help.ubuntu.com/community/WorldofWarcraft").

You should NOT have simply copied the files over from a Windows install, or, frankly, from any other installation. You need to install directly from the installation CDs. (I don't know why this makes a difference, but it really does matter a lot.)

If you don't have any other programs running under wine, you should delete your wine settings altogether and start from scratch, following the instructions linked above.
```
rm -rf ~/.wine
```

---

### Post by Zaha on 2007-06-08
I have a related question; my WoW runs great with wine, except that trying to change the graphics settings crashes the game (this seems to be a common problem). So, does somebody know how to set the graphics settings to a higher (or highest, while we're at it) quality using the config file?

---

### Post by Braytok on 2007-12-12
I came across a great add on that fixes the game crash while changing video settings.
Its called ApplyToForhead. I can't find the link at the moment but a google search should procure it for you.

---

