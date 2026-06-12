---
title: "Problem related to screen resolution"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by juggleclown on 2008-02-13
Hello everybody. I'm completely new to Linux. I know my way around a Windows system, and even a good deal about the command line. I haven't taken the time to read the READ FIRST (for shame!), but bear with me.

Basically, I'm not a terribly bright person, and I've been trying out Linux. I started tinkering with DSL a few months back after asking myself "Why haven't I tried Linux?", and didn't get anywhere with it (to say I was a stranger in a strange land would be an understatement)

Recently, my laptop went pretty sad. Sound wouldn't work, it couldn't list the hardware, internet wouldn't work, and I couldn't install or run any security tools. Eventually it got worse and Windows stopped booting. My Windows disks were pretty scratched when I found them, and so I couldn't recover or reinstall the OS, and I'm not in the mood to redownload it for now, I'd rather learn Linux until I really need it.

I pulled out my DSL disk and gave it a whirl. It was still too much for me. It had internet, sound, and Firefox, so I enjoyed a usable laptop once again. I couldn't figure out how to get Flash on it, so I gave up trying to watch YouTube and came to the understanding that I'd have to learn the system a bit more before I should bother.

Anyways, I was directed to Kubuntu, and although I've been spending several days struggling, I've mostly been enjoying this alternative. Eventually, I was able to click about until I found the KNetworkManager in the lower-right and got the ol' wireless working, and from there I eventually got Flash through Konsole and "sudo apt-get install flash".

Given, at the moment I've no idea what "sudo" means and why this command downloads and installs flash, but I intend to learn myself into a competent Linux user capable of using other distros.

Today, I discovered Adept Installer, and I've gotten myself a few programs. I've been using Firefox in place of Konqueror, and I've got some of my favorites from Windows, such as NetHack (I can't figure out how to get text-mode graphics, only tiles), The Ur-Quan Masters, and a few video game system emulators such as ZSNES and VisualBoyAdvance (and was quite happy to see these things work instantly without me having to figure out how to set up my gamepad or flash drive), and I've been listening to the Super Smash Bros Brawl soundtrack on my now sound-capable laptop. :)

Anyway, I can't ask every question I have here, and I'll be sure to read more here without asking first, but I've got a considerable problem, and I'd prefer to be able to solve it prior to beginning my quest to learn Linux.

The thing is, I've got this weird problem. When I installed Kubuntu, the default resolution was 1600x1200, which is the max setting available, and is way too high for me, as well as this laptop. I want to set it down to 800x600. Problem is, every resolution lower than this causes the screen to split in half and double in a weird way that makes it impossible to use. My computer really has trouble with such high resolutions, and it's hard for me as well, and I really want to fix this now.

In ZSNES for example, if I set it to 1600x1200 full screen, it looks perfect but runs so slow I can barely close it. If I set it to 320x240 or 640x480, it runs at a good speed, but it's too small to see and if I stretch it to full screen, it gets that same glitch as before, and this happens with all programs such as The Ur-Quan Masters, which works perfectly in a 640x480 window.

On YouTube, I can watch reasonably well, but if I click full-screen, the video plays at a horribly slow speed. My laptop isn't exactly new, but can I expect it to play games at lower resolution with little or no drop in speed? My computer was certainly capable of these tasks with Windows XP, so I'll assume it probably can.

Basically, my biggest problem is the glitch related to lowering the resolution. I have a cell-phone camera and a photobucket account, if submitting pictures of the problem would help. Kubuntu is hard for me to use at such a high resolution, so please help me fix this thing.

My eventual goal is to be able to play Starcraft on this laptop again, which I understand requires a program called Wine which emulates Windows functions. It's safe to assume it will work online with WIndows and Mac OS users, correct? Of course, I can't play Starcraft with this glitch, and I can't really delve to deep into learning this system while it's like this.

When I was younger, I wanted to learn to program, and that is why I'm rather decent with a Windows computer. I appreciate the complexities of Linux, and I think if I can learn it maybe I can become a better computer user, and possibly understand a programming language one day. That's why I've chosen to stick with this. If I can get this laptop to perform it's basic needs, it'll be much easier for me to learn what I want, and if I can get it "on it's feet", so to speak, I'll give myself at least 6 months to a year before I decide I want to use Windows on this computer again. I've used Windows since I was a kid, even dabbled in a little Mac. It's time for Linux to get it's fair share. ;)

---

### Post by NightwishFan on 2008-02-13
sudo is a command to temporarily run something as root user (think administrator)

---

### Post by juggleclown on 2008-02-13
^ I deduced that much. I just meant I had no idea what "Sudo" meant yet. It's an arbitrary term as far as I know at the moment.

---

### Post by TheDilettante on 2008-02-13
I'm going to bed, but I'll help get the ball rolling.  Go to your terminal (Applications -> Accessories -> Terminal) and type:

*cat /etc/X11/xorg.conf*

and copy the output here.  This will give the next reader a better understanding of what your sytem looks like, and where the problem might be.

Also useful - what exactly is your laptop?  Was 800x600 its native resolution under windows?

Good luck.

---

### Post by juggleclown on 2008-02-13
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Rage Mobility M3 AGP 2x"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-80
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Rage Mobility M3 AGP 2x"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1600x1200"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection








My laptop actually was at 1024x768 IIRC, but about two months ago I decided to set it to 800x600. I'm accustomed to that resolution, it's just a lot easier for me, but 1024x768 was how it was always previously set. Any more details about the screen, I'm afraid I don't know.

I completely forgot to mention this in the last post, but if it helps this laptop is an IBM Thinkpad. My uncle worked for a computer business and apparently got a few of these things for free and kept them to collect dust in the garage. I was quick to take one of them. :)

I should note that I'm running a distro of Kubuntu, not Ubuntu, and that there doesn't seem to be an "Applications > Accessories > Terminal". I can access the Terminal with "K Menu > System > Konsole", however.

---

### Post by oedha on 2008-02-13
have you try :==> sudo dpkg-reconfigure -phigh xserver-xorg
from terminal ?

---

### Post by barbedsaber on 2008-02-13
sudo =  **s**uper **u**ser **do**

---

### Post by juggleclown on 2008-02-13
[I]have you try :==> sudo dpkg-reconfigure -phigh xserver-xorg
from terminal ?[/I]

I just tried that, reluctantly. I don't know what it was supposed to do, but it made my screen flicker off for a moment, and other than that I don't see any difference, and the problem is still there.

---

### Post by rkd on 2008-02-13
The dpkg-reconfigure command should have made the graphics software rescan your hardware, determine its capabilities, and rewrite the xorg.conf file.  It would be interesting to look at that file again and see whether, under section "Screen", the modes line shows anything more than 1600x1200. No need to post the file here again unless you see other things that are different and want to ask about them.

If xorg.conf now does show more modes, then you might be able to change resolution now. I don't know Kubuntu, so I can't tell you exactly where to find the interface to change the resolution. In Ubuntu, it is System -> Preferences -> Screen Resolution to set the default, and System -> Administration -> Screen and Graphics to change the current resolution. I trust you can find something similar in your Kubuntu.

If xorg.conf still doesn't have any more modes, maybe you need a better graphics driver. On Ubuntu, System -> Administration -> Restricted Drivers Manager takes you to a window that permits enabling a restricted driver for your graphics, if one is available. I don't know whether one is available for your graphics, but if you can find the restricted drivers manager on Kubuntu, you can check.

If you do switch to the restricted driver for your graphics, you might have to run the dpkg-reconfigure again after making the switch before the new resolutions are available.

---

### Post by erginemr on 2008-02-13
You should first check out what **rkd** suggests above and find and use "Restricted Drivers Manager" in Kubuntu (sorry, I am also an Ubuntu - Gnome user). Your xorg.conf file says you are using open-source "ati" driver, while there is a binary driver "fglrx" in Synaptic (Adept for KDE) for ATI cards, that will supposedly perform better. The restricted drivers manager above should find and install the correct driver for your card.

If that does not work, then you can do the following. You will do all the below commands from the terminal (Konsole). You can use copy and paste to avoid syntax mistakes:

1. First of all, take a backup of your current xorg.conf file with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

2. Edit xorg.conf manually with
```
gksudo gedit /etc/X11/xorg.conf
```
and change the line:
```
Modes "1600x1200"
```
to
```
Modes "1024x768"
```
Save and exit. And restart the X server with Ctrl+Alt+BackSpace.

2. Alternatively, run "dpkg-reconfigure" again but without the "-phigh" parameter now.
```
sudo dpkg-reconfigure xserver-xorg
```
which will then ask you a couple of questions. Keep the copy of your current xorg.conf file open, by opening a new terminal and entering the below command into it:
```
gedit /etc/X11/xorg.conf.mybackup
```
so that you may give more educated answers to those questions. Don't worry, the script will also guide you.

3. When you reach the stage for selecting the resolutions, select the ones you desire. Apply the new setting, cross your fingers and restart your X (graphical) server as said above.

The following ATI binary driver howto is also a good starting point:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by juggleclown on 2008-02-14
Well, I've determined that the IBM Thinkpad A22p model has 1600x1200 as the native resolution, and a number of the computer's specs are listed here:

[http://www.thinkwiki.org/wiki/Category:A22p](http://www.thinkwiki.org/wiki/Category:A22p)

Given, mine varies a small amount, the CD Drive is not DVD and can't burn CD's, it's actually from another laptop. I've tried looking up info on ATI Rage Mobility drivers for this thing, but it's all pretty much getting nowhere for me.

I can say this with certainty though. I tried Kubuntu on my brother's Thinkpad A22p, and the same problem arises. It's obvious that anybody who has an IBM Thinkpad A22p will be unable to use a lower resolution than 1600x1200, nor will they be able to run any applications in fullscreen. My computer is also mostly identical to any other IBM Thinkpad A22p, and I believe the Thinkpad is a rather popular laptop. I'm not so technically savvy, if anybody here could seek out somebody with the same laptop model as me, perhaps this problem could be solved for any future users, as well as myself.

Perhaps my problem isn't too common or important to solve. As it is though, there's a problem likely related to the graphic drivers, and I don't really know how to fix this. :(

I've ended up reinstalling Kubuntu about three times now. To describe it again, the screen seems to split or wrap around in lower resolutions. It becomes like four or five strips, with a strip in the middle showing what should be on the left, and two parts of the screen showing where the cursor is, kind of like that.

I've uploaded pictures from my phone to photobucket here:

[http://i18.photobucket.com/albums/b112/JuggleClown/Thinkpad/sspx0348.jpg](http://i18.photobucket.com/albums/b112/JuggleClown/Thinkpad/sspx0348.jpg)
[http://i18.photobucket.com/albums/b112/JuggleClown/Thinkpad/sspx0349.jpg](http://i18.photobucket.com/albums/b112/JuggleClown/Thinkpad/sspx0349.jpg)

The first picture is from GFCE Ultra, an NES Emulator running Castlevania in fullscreen. The second picture is the menu screen from The Ur-Quan Masters. You can see in the mid-right of both a blue bar that seems to be part of the desktop, and that parts of the display are doubled or not visible at all (note the absence of the life-meter in Castlevania).

This is what my screen looks like at resolutions lower than 1600x1200. I can't run games fullscreen at 1600x1200, as the laptop can't handle that. When in full-screen at lower resolutions, or when simply set to lower-resolutions, the screen will always do this on IBM Thinkpad A22p.

Has anybody ever seen anything quite like this?

---

### Post by rkd on 2008-02-14
I see that at the link you gave, the "ATI Rage Mobility M3" page says that the ati driver doesn't support this device. Your initial xorg.conf file that you posted here in post #5 shows it using the ati driver. Did you ever look at the xorg.conf file after doing the dpkg-reconfigure? Did it change at all? If you aren't sure you know what to look for, put the new xorg.conf into another post.

The correct driver for that graphics controller is r128. I saw that both at the link you gave and another site I found. If your xorg.conf doesn't have that, we should try it.

You never mentioned whether you tried editing xorg.conf to change the modes line as erginemr suggested in post #10 (I hope I counted the posts accurately). Did you try that? If so, did you see any difference in the screen at all?

---

### Post by juggleclown on 2008-02-15
I have tried the previous suggestions in the topic, as well as my own ideas. Several times I have compromised the system's stability as root by trying various things, most of which I can't remember, and unfortunately I'm on a new install with no data from those changes. If you wish, I could try them again.

I'm glad to see you suggested that r128 though. I spend hours google searching it up. I came to the conclusion that I just couldn't find what I need, and that this "r128" was either something that didn't apply to Linux, was too complicated for me to install, or had become too difficult to find. I wanted to try to install r128, but to no avail. I don't know what to download, where to get it, and how to get it set up.

I'm sure I probably don't have this r128 already, and that ATI's website had absolutely nothing that could help me, or I simply couldn't navigate it, whichever one. If you think that installing this driver could fix my problem, please help me figure out how to go about doing that. :)

---

### Post by rkd on 2008-02-15
When you come up with a lead like that and can't figure it out after making a decent effort at research, post here with the idea and pointers to where you found it and where you've researched it. We can often clear up the puzzle very quickly.  It is good that you try to solve things on your own, but we are here to make it a bit easier, so don't spend hours and hours before asking some questions.

The r128 driver is included with X, the graphics system in Linux, so you don't have to download it from anywhere.

I'm not an expert on X, so it might take us a couple of tries before we get things right, but if you follow the instructions I write and ask before you try something that I haven't suggested that you aren't sure of, we can avoid trashing your system. 

At worst, you'll have to switch to a virtual console or boot into recovery mode and enter a couple of text commands to put back the X configuration from the last good copy (which we will carefully save before fiddling with it).  If you aren't sure about what a virtual console or booting into recovery mode means, we can talk about that and you can try it first, before you need it, to get familiar with it. It really is easy, as long as someone has told you what commands to run, so don't be very wary of it.  It is just like having ONLY a Konsole window to work with. I describe how to get to a virtual console near the end of this post, but if you want more explanation, just ask.

Also, I'm only familiar with Ubuntu, so far, so there is some potential for me to give Ubuntu-specific instructions that won't work in Kubuntu, but for this task, I think there won't be a very big chance of that happening.

I'm very unclear about how one is supposed to change from one available screen resolution to another in either Ubuntu or Kubuntu. There is something called Screens and Graphics, but it function seems to be to set up the description of the available resolutions in the xorg.conf file (and I found one warning on a non-Ubuntu web page that Screens and Graphics doesn't work very well and should be avoided). There is a command line program named xrandr that apparently comes from the X group that may be the current best way to switch resolutions, but it isn't clear to me that it really is the right tool. We may have to experiment. How have you been making the resolution change when you tried using 800x600?

Keep in mind that I make typos and outright mistakes, so if anything looks wrong or even odd, ask about it. Better to check than waste time with incorrect instructions.

When you are ready to try the change, open a Konsole window and enter these commands
```
cd  /etc/X11
sudo cp  xorg.conf  xorg.conf.orig
kdesu kate  xorg.conf
```The first command switches to the directory where the xorg.conf file is, so the other commands can be shorter. The second command copies the current version of xorg.conf to xorg.conf.orig so we will have a copy of the current version in case one of our changes makes xorg.conf unusable. We can then copy back from xorg.conf.orig to restore X to a working state. Only make this copy once -- we don't want to alter xorg.conf.orig once we've got it. You don't have to use kate in the third command. Use whatever editor you prefer using from the command line, and remember to use kdesu or sudo, depending the which is appropriate for the editor you choose. 

Once you have the file open for editing, page down until you find the lines ```
Section "Device"
Identifier "ATI Technologies Inc Rage Mobility M3 AGP 2x"
Driver "ati"
BusID "PCI:1:0:0"
EndSection


```Change the Driver line to replace "ati" with "r128". Then save the file and exit the editor.

Now we have to stop and restart X, the graphics system. This will stop all applications you opened from the desktop and all Konsole windows and programs running from them, so if you have any unsaved work, save it now. When X restarts, you will have to login again and you'll have a fresh environment.

Restarting X is very simple -- just type Ctrl-Alt-Backspace.

Assuming the edit didn't mess things up, in a few seconds you should see the graphical login prompt you normally see when starting up your computer. Login and see how the display looks. We didn't change the resolutions available, so I think there won't be any change in that yet, but make sure things still seem healthy.

If things seem okay, next step is to try to get access to other resolutions. First try this in a Konsole window```
sudo dpkg-reconfigure -phigh xserver-xorg
```I don't know whether this will find all the available resolutions, but it is easy to try. When the dpkg-reconfigure is done, restart X again using Ctrl-Alt-Backspace. When it comes up and you have logged in, go to the place where you control screen resolution and see what is available. If there are other options besides 1600x1200, try one of them and see whether the display looks right. If there aren't other resolutions available, try the next step.

From Konsole, open /etc/X11/xorg.conf for editing again, as we did above, but skip the cp command. We already have a copy of the original configuration and we don't want to alter it during the experiments. Look at the Device section where we changed "ati" to "r128" in the first step above. See whether it still says "r128". If it does not, change it to "r128" again. A little below the Device section, there is a Screen section. In the Screen section, currently you have a Modes line that says just "1600x1200". I'm assuming that if the dpkg-reconfigure command did not make more resolutions available, this Modes line will still have just "1600x1200" on it. If that is not the case, stop and let's investigate why we didn't see the other modes. If the line still has just the one mode, change the Modes line to```
Modes "1600x1200" "800x600"
```Save the file and exit the editor. Restart X again. After you login, go check what resolutions are available. If 800x600 is listed, select it and see what the screen looks like.

If this works and you want more resolution choices than 1600x1200 and 800x600, we can edit the Modes line appropriately. I think you have to list only certain resolutions that the hardware knows how to handle and we need to check some of the sites about using the A22p with Linux to get the allowed resolutions. Actually, if this works, I think we probably should copy large sections of the xorg.conf file that Richard Neill has posted on his web site about using the A22p.

If at any point in the process, the display becomes unusable, we can put the X configuration back to the original that we saved. We do this in a virtual console or by booting into recovery mode. To switch to a virtual console, type Ctrl-Alt-F2. That should switch to a text mode screen display with a login prompt. Type your userid and push Enter. Then when it prompts for the password, type it and push Enter.  Just as in Konsole, your password will not echo, but it is being accepted.

When you have logged in, enter the following commands```
cd  /etc/X11
sudo cp  xorg.conf  xorg.conf.borked
sudo cp  xorg.conf.orig  xorg.conf
sudo reboot
```The first command switches to the directory containing the files of interest. The second command saves the current (bad) version of xorg.conf so we can look at it later. The third command copies the original version of xorg.conf back, putting things back to their state before we started fiddling. The fourth command restarts the computer.

A quick note about xrandr. It probably is installed already. If not, you can get it from the Ubuntu repositories -- package is named xrandr. At the command line, if you just enter xrandr, it shows you a number of things about your display configuration, including all available resolutions. to change resolution, you enter a command something like```
sudo xrandr -s 800x600
```where the characters after -s are one of the resolutions xrandr without arguments displays. That works on my system to change the resolution.

So look over this, ask about anything you aren't sure you understand and know how to do, and when you feel ready, give it a try.

---

### Post by juggleclown on 2008-02-15
OMG! I could hug you! :D

Well, after I finally found a working solution, I did various tests to see what fixed it. As it turns out, the ATI driver works just as good as the r128. I ended up having to restore that backup, thank you very much for saving me from reinstalling Kubuntu for the millionth time.

I tried just about everything you said, but eventually I got the idea to try something of my own, and it actually worked like a charm. Of course, I'd never have been able to do so without all of your help.

All that had to be changed, it seems, was two little digits in the xorg.conf. I changed the DefaultDepth under "screen"  from 24 to 16. Now my laptop can correctly run any of the resolutions, and my laptop screen is now much easier to read, as well as capable of running programs in full screen, which is also pretty darn important! ^_^

Well, now everybody knows how to fix resolution problems for the IBM Thinkpad A22p running Kubuntu. My laptop is now so totally usable, and I am enjoying Kubuntu as an alternative to Windows XP. I'm going to go on to learn more about Kubuntu and Linux, as well as try to learn to use as many other Distro's as I can. My first priority in terms of that is DSL, unlike Kubuntu I don't know how to do so much as save to the hard disk in that, so now my journey into Linux begins here, I suppose.

Kudos to you. Seriously, this is awesome. I can use this computer for a number of things I've been unable to do now, hopefully I'll be learning to use Wine and find myself playing Starcraft with my neighbors again. ^_^

I'm sorry if I bugged you with a lot of questions while still at such a beginner level. Like I said, I couldn't read the screen on this computer very well, so I didn't have a lot of time to go elsewhere to read up information. This was a problem I wanted to solve before anything else, but you did a good job explaining things to me. Thanks a lot. \\:D/

---

### Post by rkd on 2008-02-15
You're welcome. I'm glad you got it working, finally. I do remember seeing something in one of the web pages I looked at about needing depth to be 16 for graphics acceleration to work. I kept that in the back of my mind for something more to try if we didn't get things working at the end of the steps I had written. I didn't want to go on farther in the first round of attempts. Good for you in pressing on!

A couple of questions: How are you changing resolution? Are you using xrandr, or some other way? Before I wrote about xrander, how were you changing resolution?

There is a possibility that we could get things working even better if we copied large parts of Richard Neill's xorg.conf from his web page about setting up the A22p. I think we could do that experiment without endangering your setup by making a copy of your current xorg.conf to restore from, just as we did in the experiment you just completed. Do you want to try that? If so, I'd want you to post your current xorg.conf and I'll compare it with Richard Neill's and decide what to change. 

If you post your xorg.conf, attach it to your post rather than pasting it into your post (use the "Manage Attachments" button down below "Additional Options" which is considerably below the text box in which you compose the post). I think there is no need to make this thread extra long with an additional copy of that big file.

---

### Post by juggleclown on 2008-02-16
A xorg.conf file dedicated to the A22p? You're *quite* good at finding things, aren't you? Yeah, changing depth always seems to be a good thing, I can't tell you how many programs have run better for me by cutting the depth in half. *cough*half-life*cough* ;)

Anyways, I've gotten Starcraft working now, quite quickly I must say. I learned how to make ISOs using K3b (which came pre-installed on Kubuntu), as well as mounting them through terminal. Of course, I installed Wine and that was easy enough to figure out. Starcraft is a little on the laggy side, it runs pretty smooth but it could be faster, and the scrolling and cursor skip a good bit. However, everything is working and it's quite playable, it could even update and play against other computers on the network. I doubt I could run any 3D programs (this laptop was never too great with 3D in the first place), I've yet to reinstall TuxKart to try that.

Seeing as how it's quite easy to recover the xorg.conf file (will Kubuntu always boot into terminal if there's a problem with the graphics?), I'm quite willing. I've established a number of roms and programs, but I'm not too worried about losing them anyway.

I've enclosed a copy of my currently used xorg.conf file. I had to rename the extention, as the uploader refuses anything that isn't a specific filetype, so I changed it to txt so it would accept it.

To change graphics setting in Kubuntu (in which I'm not sure about how to change them in terminal), I can easily click the K Menu in the lower-left corner and click "System Settings" and from there I just select "Monitor and Display" and adjust the screen size to the resolution of my choice (640x480-1600x1200). I should note that in the hardware tab, the default setting is "Custom1" for the monitor. If I change it to anything else (including 1600x1200 LCD or Autodetect), the screen will glitch again and the default setting will no longer be accessible, requiring me to restore the backup. It's not a real problem, but I thought it should be noted anyway.

---

