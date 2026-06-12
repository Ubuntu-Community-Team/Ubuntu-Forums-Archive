---
title: "The use of Wine for a Newbie"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by martialartist81 on 2007-08-17
So, I got ahold of wine through Ubuntu last night, and I have to admit, while I'm quite new to Linux, I am completely and totally lost.

I've spent the last couple of hours scouring the net (Wine's webpage, and these forums included) for an introduction/idiot's guide to using Wine, and I for the life of me, cannot find anything that doesn't jump right into the mix without telling me what I'm doing, why and how to get there.  

Anyone have any links or advice for just starting out?  Remember, I'm quite new to all of this.  So any kind of true and simple beginner's guide would be seriously appreciated.

Thanks all!

---

### Post by orion21 on 2007-08-17
sorry I dont think this is beginners question, I would rather use a distribution with wine or forget wine completely. never been a good administrator


------------
cool website swiftvideos.com

---

### Post by grandioseus on 2007-08-17
I'm new to Linux too and don't have any experience with Wine, but the following link looks like it might be what you are looking for:

[http://spidertools.com/wine_setup.php](http://spidertools.com/wine_setup.php)

I am going to try out these directions to see how accurate they are when I get home tonight.

---

### Post by brennydoogles on 2007-08-17
> **grandioseus said:**
> I'm new to Linux too and don't have any experience with Wine, but the following link looks like it might be what you are looking for:

[http://spidertools.com/wine_setup.php](http://spidertools.com/wine_setup.php)

I am going to try out these directions to see how accurate they are when I get home tonight.

Those instructions are written for redhat users.... not us.

---

### Post by Outrunner on 2007-08-17
Well, it's quite simple actually... to start an .exe file go to the Terminal and type
```

wine /path/to/filename.exe
```

for instance if you want to install a game cd (change directory) to where your CDis mounted( usually /media/cdrom0):

```
cd /media/cdrom0
```

then execute the .exe file

```
wine setup.exe
```

Of course, you would have to use the exact filename because in GNU/Linux Setup.exe is not the same setup.exe . To see the exact file name in the terminal type 'ls' (list)

```
ls
```

If you still don't understand or have a specific need in mind, don't hesitate to ask! good luck

---

### Post by Arthur Archnix on 2007-08-17
It's easier if you have a specific program in mind. There are plenty of good instructions on getting certain programs to work. I'm afraid that, to the best of my knowledge, the only way to learn wine is to setup the programs. I'm aware of no general introduction to wine, like you might find a general introduction to the terminal in Linux.

Truthfully though, since you've gone and switched to Linux, why not give the Linux alternatives a shot for a while before settling back to your old favorites? For instance, once you get DVD Shrink up and running in wine, you may miss out on the chance to experience the joy of K9Copy. :) It's different, but great in its own way too.

---

### Post by gobbles414 on 2007-08-17
Hi all,

Here is a VERY quick summery of how to use Wine at its most basic level in Ubuntu 7.04. Assuming that you are installing Wine from the beginning:

01. Enable backports in system --> administration --> software sources. The purpose of this is to get the latest version of Wine possible.

02. Go to system --> administration --> synaptic package manager and type *wine* into the search field. You should get a result with a box that you can click in. Once you have clicked, select apply.

03. Restart you computer if you wish (optional).

04. Before trying to install a program in Wine launch the Wine Configuration program. You can do this by going system --> preferences --> Wine Configuration. The only option you should mess with now is in the graphics tab. Select emulate a virtual desktop. The purpose of this is to make it easier to quit Wine should it freeze.

05. Consult Wine's [appdb]("http://appdb.winehq.org") before attempting to install a program. For practice, let's try to install the Windows version of [Google Picasa]("http://picasa.google.com") (a great jpeg organizer/editor). BTW, there is a Linux version of Picasa available. But it is much older than the current Windows version.

06. After downloading the installer, you can activate it by going applications --> accessories --> wine file. You should get a window with your Ubuntu directories on it. Navigate to your desktop by clicking to /home/username/Desktop. Double-left-click on the installer and follow the instructions.

07. The easiest way to launch Picasa is to go back to applications --> accessories --> wine file, click on the C: drive button on the top, and navigate to the directory where you installed Picasa. As I recall the program's default location is program files --> picasa2 --> picasa2.exe. Double-left-click.

08. To uninstall a Windows program use the Wine Software Uninstaller, which is located in the System Tools menu.

09. Alternatively, all of these tasks can be accomplished in the terminal.

---

### Post by martialartist81 on 2007-08-17
I'm into Linux for many different reasons, but the only reason I wanted Wine was because I'm a heavy PC gamer.  I'm still dual-booting my WinXP and Ubuntu, but I want to try and convert more and more over to the Linux side and start relying less of Windows for my daily stuff (e-mail, internet, games, burning CDs/DVDs, etc).

So Wine is essential to me since almost none of the games that I play are ported over to Linux (i.e. Lord of the Rings Online, Half-Life 2, etc).  Wine is needed in order to play these in the Linux OS.

But thanks for the hints guys.  I'm gonna check out the terminal commands posted two above, and see what I can get going.  I appreciate the help!

Cheers!

---

### Post by gobbles414 on 2007-08-17
martialartist81,

Wine is almost guaranteed NOT to work with newer Windows games. Check [this]("https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems") out for other alternatives!

---

### Post by Mad_Max_1412 on 2007-09-06
Hi Gobbles414,

I had installed WINE prior to finding this thread, but when I went to do step 4, I didn't have the Wine Configuration option available, so I went back to step 2, and because Ubuntu thinks I already have it installed, I took the option to re-install it.  Now the synaptic package manager is showing I have the following version installed:
0.9.44~winehq0~ubuntu~7.04-1

I still don't have the Wine Configuration option availableunder System --> Preferences.

Under the "Applications" pulldown menu, there is no mention of Wine in any of the sub-menus (Accessories, Graphics, Games, Internet, Office, Sound and Video or Office Tools).

If I go to "Add/Remove" and select "Installed Applications" then I can see that Wine is installed.  

What am I doing wrong to not have the configuration manager available?

Thanks

---

### Post by toidi on 2007-09-06
first off I managed to get lotro to work in linux.  I did have to download a seperate launcher for the game from [http://www.lotrolinux.com/](http://www.lotrolinux.com/)

Also the launcher will not allow you to patch to the latest version (you will need to update it using a windows machine).

This thread explains an awful lot on getting lotro working.
[http://ubuntuforums.org/showthread.php?t=386480](http://ubuntuforums.org/showthread.php?t=386480)

Lotro is not a good beginners example to try though as it does require a fair bit of work to get it running.

To get into the wine config simply launch a terminal and type:
```
winecfg
```

This will open the wine configuration utility, where you can mess around with different compatibility/audio settings etc.

Hope this helps.

---

### Post by TeaSwigger on 2007-09-06
Hello, 

Suggest you don't get too fussed - because you'll find your way all right. I'm pretty new to linux and have a group of windows programs running just fine in WINE. You sort of learn by osmosis but the show will go on :)

Don't worry about that missing Wine Configuration thingy either. It is probably installed and you haven't messed up. You can add it into your menu yourself when you get around to fussing with the menu but until there here's what you can do. Open a terminal. Enter this:

```
winecfg
```

It'll come up. Then you can close it, 'cause basically all you're doing by firing it up the first time is having it set itself up for your user. As to this suggestion in the (excellent) post above:

> The only option you should mess with now is in the graphics tab. Select emulate a virtual desktop. The purpose of this is to make it easier to quit Wine should it freeze.

I suggest you can just close that window and get to other things. You needn't bother until you've decided later on by experimenting if you like it set that way or not; entering "wineserver -k" in a terminal does a good job of stopping WINE if it should freeze up or what have you.

A very good suggestion though, trying linux-native apps instead where possible. There are so many free linux apps that work great and so few things you need windows apps for.

Feel free to ask, ask and ask if you have questions :) You'll get it.

EDIT lol beaten to it ;)

---

### Post by Paulmd on 2007-09-06
> **martialartist81 said:**
> I'm into Linux for many different reasons, but the only reason I wanted Wine was because I'm a heavy PC gamer.  I'm still dual-booting my WinXP and Ubuntu, but I want to try and convert more and more over to the Linux side and start relying less of Windows for my daily stuff (e-mail, internet, games, burning CDs/DVDs, etc).

So Wine is essential to me since almost none of the games that I play are ported over to Linux (i.e. Lord of the Rings Online, Half-Life 2, etc).  Wine is needed in order to play these in the Linux OS.

But thanks for the hints guys.  I'm gonna check out the terminal commands posted two above, and see what I can get going.  I appreciate the help!

Cheers!

My advice: keep the dual boot. Running Windows games in Windows way more reliable than running Windows games in Linux. 

Most other things that are available for Windows, are available in linux. Just not that many popular games.

Suggesting the following programs for the other things:

email- thunderbird
internet- firefox (or opera)
CD burning- k3b

Photo manipulation -GIMP (as good as Photoshop, but uses less ram, I've used it to colorize some  Cassini Spaceprobe's raw Images of the Saturnian system, a process that involves taking 3 greyscale images, taken with different filters of light, setting each layer to red, green or blue, screening the images, and possibly re-aligning and resizing the layers. Anyway It works well enough to handle all that. It doesn't seem to have any problem with multiple 1024x1024 images, even on this celery 566mhz machine) 

Ms Office- OpenOffice (great wordprocessor, mediocre spreadsheet. Nothing better right now, that I know about.)

Winamp-XMMS. (Simple, it works)

Videos -VLC (not because it's great, but because it's the least worst i've tried so far :( )

---

### Post by Mad_Max_1412 on 2007-09-06
Guys,

In the terminal window, when I type winecfg, I get the following:  Could someone just let me know if there's anything here I should be concerned with, as it mentions things missing and to expect problems.


wine: creating configuration directory '/home/max/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
wine: '/home/max/.wine' created successfully.
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet


Edit:  The smiling face above is because the text has a colon followed by a lowercase p as in "pack".  I don't know how to disable Smilies.

---

### Post by ahale1987 on 2007-09-06
> **martialartist81 said:**
> I'm into Linux for many different reasons, but the only reason I wanted Wine was because I'm a heavy PC gamer.  I'm still dual-booting my WinXP and Ubuntu, but I want to try and convert more and more over to the Linux side and start relying less of Windows for my daily stuff (e-mail, internet, games, burning CDs/DVDs, etc).

So Wine is essential to me since almost none of the games that I play are ported over to Linux (i.e. Lord of the Rings Online, Half-Life 2, etc).  Wine is needed in order to play these in the Linux OS.

But thanks for the hints guys.  I'm gonna check out the terminal commands posted two above, and see what I can get going.  I appreciate the help!

Cheers!

I know exactly what you mean. I used to be a heavy(ier) gamer before LInux, but ever since I made the switch, my 7900GS isn't getting much of a workout. Wine is a very mysterious tool until you figure it out. winehq.com has no beginner tutorial, but here's what you do. 

1. After installing it via Applications > Add/Remove programs, go into the terminal and type without quotes "winecfg". 

2. A small, windows-looking box will pop up. This is how you set up wine. If you want it to act like windows 98, ME, NT, 2000, XP, etc. Some basic system parameters really. 

3. Once you have wine configured, (from a CD for example) put in the CD of the software you're trying to install. It'll come up as cdrom0, and look for the Setup.exe file, or similar. Right-click on the setup file and select "Open with other Application). Once in this menu, at the bottom, select "Use a custom command". In this box, type "wine". 

It should open right up. As for some games working, I know Steam games will work, but you have to do a bit of tinkering. When I tried installng Steam and HL2, the dialog boxes had no text. You have to install the Tahoma font, but I've yet to do this. I just know of it. This is why Google is our friend. I assume not old, but "not new" games like HL2, Halo, Swat4, NFSU2, or Starwars Battlefront 2 will work, but FEAR and STALKER, or BF2142 won't. Hell, BF2 won't, but it's almost fully functional in Cedega. Cedega is much better for games. Being a heavy gamer, Cedega might be something to seriously consider.

---

### Post by Mad_Max_1412 on 2007-09-07
Guys,

Once I've installed a program, is there supposed to be some menu item for me to start the application?

When I installed the program, it offered to create a desktop shortcut, which has appeared and with which I can open the application, but there's been no change to my start menus .

Regards

---

### Post by TeaSwigger on 2007-09-07
> **Mad_Max_1412 said:**
> Guys,

Once I've installed a program, is there supposed to be some menu item for me to start the application?

When I installed the program, it offered to create a desktop shortcut, which has appeared and with which I can open the application, but there's been no change to my start menus .

Regards

That's normal. It usually makes the desktop shortcut for ya, but you'd usually have to make a menu entry. If you right click the desktop entry and open it in a text reader like gedit or something, you may quickly glean from it what to put in the menu entry until you figure how that stuff works.

---

### Post by philinux on 2007-09-07
The later version from winehq 9.44 does not put menu items into your system. The package that comes with ubuntu 9.33 does do this. Personally the 9.33 version is more stable.

---

### Post by TeaSwigger on 2007-09-07
Oh a suggestion for folks unfamiliar yet with WINE: the windows "versions" you can select to have WINE emulate (in winecfg) do not necessarily correspond to how well they'll work with a given program regardless of the version the program was built for. So if there's any probs, you've nothing to lose or mess up by trying to run the program by selecting another windows "version." It's said the Windows98 option is often the best bet, but sometimes one will work better than another. Consider it more as a rough rule of thumb and an extra option you can try for troubleshooting.

> **philinux said:**
> The later version from winehq 9.44 does not put menu items into your system. The package that comes with ubuntu 9.33 does do this. Personally the 9.33 version is more stable.

You're right. There's tradeoffs though, with about every version it seems. A video utility that wouldn't run on 9.33 is now running ok in 9.44, but there's a graphics prog that liked 9.33 better...

I'd like to thank MicroSoft for putting everyone through all this trouble.

---

### Post by Paulmd on 2007-09-07
> **TeaSwigger said:**
> Oh a suggestion for folks unfamiliar yet with WINE: the windows "versions" you can select to have WINE emulate (in winecfg) do not necessarily correspond to how well they'll work with a given program regardless of the version the program was built for. So if there's any probs, you've nothing to lose or mess up by trying to run the program by selecting another windows "version." It's said the Windows98 option is often the best bet, but sometimes one will work better than another. Consider it more as a rough rule of thumb and an extra option you can try for troubleshooting.



You're right. There's tradeoffs though, with about every version it seems. A video utility that wouldn't run on 9.33 is now running ok in 9.44, but there's a graphics prog that liked 9.33 better...

I'd like to thank MicroSoft for putting everyone through all this trouble.

How is this Microsoft's problem???? They didn't write Wine.  You can blame them for other stuff, but somehow I don't see them as responsible for the failure of certain Windows programs, that they also didn't write, to run under an operating system that they were never intended for.

---

### Post by TeaSwigger on 2007-09-08
Oh another good tip for Wine newbies, from asmoore82 at these forums:

> immediately after the 'winecfg' step you should run ...
Code:

~ $ wine iexplore [http://www.google.com](http://www.google.com)

and Wine will automatically download the Gecko rendering engine.
This is needed for most games to run properly (like Counter-Strike).

> **Paulmd said:**
> How is this Microsoft's problem???? They didn't write Wine.  You can blame them for other stuff, but somehow I don't see them as responsible for the failure of certain Windows programs, that they also didn't write, to run under an operating system that they were never intended for.

But then who would need to write, develop or use WINE were it not for Microsoft's 'policies'?

---

### Post by gobbles414 on 2007-09-18
Mad_Max_1412,

If you are installing Wine using Synaptic, then I should be able to help you.

* Regarding your terminal output: Make sure that 3D acceleration has been installed in Ubuntu. Go SYSTEM --> ADMINISTRATION --> RESTRICTED DRIVERS MANAGER. If you see any option pertaining to your graphics card, try to select it. If it will not install go SYSTEM --> PREFERENCES --> DESKTOP EFFECTS to attempt to force a download. if Desktop Effects opens without prompting you to download 3D drivers, then there may not be any available for your computer.

1. Navigate to your home folder. Activate hidden files/folders by going VIEW --> SHOW HIDDEN FILES.
2. Delete the file called .wine (WARNING this will delete any Windows programs that you have installed)
3. In the terminal, type *sudo apt-get --purge remove wine*
4. Restart your computer.
5. Install Wine using Synaptic.
6. Restart your computer.
7. If the wine stuff is still not showing in your menus, go SYSTEM --> PREFERENCES --> MAIN MENU and look for unchecked wine options in the menus.

8. Some Windows applications will install shortcuts onto your desktop. For others, you will need to use the wine file browser.

Keep us informed about your progress.

---

### Post by Mad_Max_1412 on 2007-09-23
Hi Gobbles414,

I'm in a bit of a pickle now.

Firstly, let me say that at some point a WINE menu folder appeared and it has the links to the 2 programs I've installed.

One of them was the VideoReDo Plus program which wasn't working too well until a recent update to Wine and now it works pretty well except the video is mostly blue tones.

Anyway, I saw your response and thought perhaps the 3D acceleration fix my resolve this and so I went to the restricted drivers option and selected the only thing there which was the nvidia drivers.  I'm only a newbie so I am relying pretty much on the expertise of others, and I've had problems before with driver issues but thought it was because I was trying things on my own.

Anyway, now I can get into Ubuntu GUI.  As I have experienced earlier, I now get the following:
"Failed to start the X Server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem."

When I select Yes, part of the message I see says about a mis-match "The nVidia kernel module has version 1.0-9755 but this x module has the version 1.0-9631".

I've experienced something similar as shown at [http://ubuntuforums.org/showthread.php?t=484862&page=3](http://ubuntuforums.org/showthread.php?t=484862&page=3) and if you follow it onto page 4 there are some instructions that I was to try.

I've tried these but they haven't resolved the problem.  Here's what I've done.

sudo -s
<password> - now I'm at the root prompt
rmmod nvidia
modprobe vesafb         (modprobe nv or modprobe vesa only give me errors)
/etc/init.d/gdm start     (I get a message saying "Starting GNOME Display Manager [OK]"
Ctrl+Alt+F7                  (I get a message saying "The X Server is now disabled. Restart GDM when it's configured properly")

Then it doesn't matter if I hit the restart button or power off totally, I just get the same problem on bootup.

Could you please provide some assistance please??

---

### Post by gobbles414 on 2007-09-24
Mad_Max_1412,

Are you sure that it is my suggestion that has caused your display problems? I first posted to this thread in August 2007. The "Page 4" link that you mention contains posts from you dated June/July 2007. Anyway, If you have been experiencing a display problem since July 2007 it is doubtful that you will solve it anytime soon. Thus, my recommendation is that you:

* backup any important data and reformat your Ubuntu partition
* install Ubuntu (maybe you want to try a Gusty alpha for improved video support)
* go to the software sources control panel and enable backports and ALL recommended updates (some recommended updates may not install unless there is a check in the recommended updates box)
* install all updates
* activate the restricted driver for your graphics and reboot
* if the reboot fails to give you a login window, then obviously it is best to reinstall again but avoid 3D acceleration.

Let us know what happens.

---

### Post by Mad_Max_1412 on 2007-09-25
Hi,

Sorry Gobbles414 if my post was a little confusing.  That link I mentioned did show I had the same/similar problem that I have now where it won't boot to the GUI, but as you can see from the end of that thread, I did get my GUI back.

My current problem of it not booting into the GUI happened when I followed your suggestion to me where you wrote:

> Regarding your terminal output: Make sure that 3D acceleration has been installed in Ubuntu. Go SYSTEM --> ADMINISTRATION --> RESTRICTED DRIVERS MANAGER. If you see any option pertaining to your graphics card, try to select it.

In my response I had a small typo where I wrote:

> Anyway, now I can get into Ubuntu GUI. As I have experienced earlier, I now get the following:
"Failed to start the X Server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem."

What the first sentence was supposed to say is now I can't get into the GUI.

What happened when I went to restricted drivers manager was that there was a nvidia option so I selected it.  I confirmed my choice and it downloaded the drivers (I gather).  It then said that a re-boot was required which I did but all I get now is the message about it not starting the X Server.

I went back to that other thread where I had a similar problem (thank goodness I had another computer to log onto the forums with) and tried to repeat what solved it back then and those steps were:

> sudo -s
<password> - now I'm at the root prompt
rmmod nvidia
modprobe vesafb (modprobe nv or modprobe vesa only give me errors)
/etc/init.d/gdm start (I get a message saying "Starting GNOME Display Manager [OK]"
Ctrl+Alt+F7 (I get a message saying "The X Server is now disabled. Restart GDM when it's configured properly")

Unfortunately nothing has worked.

Sorry for any confusion.

Regards

---

### Post by gobbles414 on 2007-09-25
Mad_Max_1412,

It should be possible to deactivate restricted drivers before the computer has finished the startup sequence. I'm not sure of the procedure -- I couldn't find anything with a quick search of the forums. Once you've logged in, there should be a way to uninstall your restricted graphics driver. Then restart as normal and your problem should be solved (although you may not have 3D acceleration for you Ubuntu/WINE apps). I've read that Gusty is supposed to have better support for graphics than Feisty. Also Gusty is supposed to have a "safe mode" that one can use to fix problems exactly like yours. I guess that I've just been extremely lucky with Ubuntu -- 5 or 6 computers and no restricted driver issues. None of my laptops will suspend correctly. But that is a minor inconvenience. Post your progress when you have had some time to experiment with my comments above.

---

### Post by Mad_Max_1412 on 2007-10-05
I resolved the issue by entering

sudo dpkg -reconfigure -phigh xserver-xorg

and then accepting nv as the answer to the first question, and not selecting any resolutions in the next question.

It then took me to the prompt where I entered

init 3

and this took me into the gui but only at a maximum resolution of 1024x768.

So I've edited the xorg.conf file to add 1680 x 1050 to each of the lines but will need to wait until my updates finish loading so I can re-boot and have this new resolution available.

In the meantime, since I've got a nVidia 6600GT card, how can I be sure I'm using the best driver to get the best out of my graphic card? I seen talk about enabling 3D acceleration etc and since I will be working with video and be trying out some heavy graphic based games, I want to make sure I have the best driver.

Under Administration --> Restricted Drivers it now shows nVidia accelerated drivers as "Not in Use" but enabling them is what caused the problems in the first place.

Under "Applications --> System Tools" there's Nvidia settings but when I select that now it says it can't launch it because there's no such file or directory.

Thanks

---

