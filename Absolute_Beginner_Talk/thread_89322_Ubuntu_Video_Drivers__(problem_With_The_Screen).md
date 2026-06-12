---
title: "Ubuntu Video Drivers?  (problem With The Screen)"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by slade on 2005-11-12
i wasnt sure if i should put this here or in the hardware video and sound section, but since im new to linux ill put it here.

i just got a computer thats about 4 years old and decided to install linux on it instead of windows, although i know nothing about linux.  i deleted windows and installed ubuntu, and although i couldnt get the linksys connection working i can get online through an ethernet connection.  one problem im having though is the screen has vertical lines on it, one about every inch across the screen.  do i need a new video driver or something?  the screen was fine when i booted up the computer in windows, and it was fine during the installation process.  the computer is a dell optiplex GX150.  it doesnt have a video card, i guess its integrated.  can i get this fixed with software/drivers, or would i need to buy a video card?

oh, and how do i get to the terminal?  i have 5.10, i found a guide for 5.04 that says go to applications>system tools>terminal, but that isnt there on 5.10 aparently.

thanks in advance for your help.

---

### Post by frodon on 2005-11-12
The terminal is in Application > Tools (not sure of the english name because i have a french version but it's the first tab under application).

Some thread about this kind of problems : [http://www.ubuntuforums.org/showthread.php?t=77588&highlight=screen+lines](http://www.ubuntuforums.org/showthread.php?t=77588&highlight=screen+lines)
[http://www.ubuntuforums.org/showthread.php?t=88579&highlight=screen+lines](http://www.ubuntuforums.org/showthread.php?t=88579&highlight=screen+lines)

---

### Post by slade on 2005-11-12
[QUOTE=frodon]The terminal is in Application > Tools (not sure of the english name because i have a french version but it's the first tab under application).

Some thread about this kind of problems : [http://www.ubuntuforums.org/showthread.php?t=77588&highlight=screen+lines](http://www.ubuntuforums.org/showthread.php?t=77588&highlight=screen+lines)
[http://www.ubuntuforums.org/showthread.php?t=88579&highlight=screen+lines](http://www.ubuntuforums.org/showthread.php?t=88579&highlight=screen+lines)[/QUOTE]
thanks, its under Applications>Accessories.

the second thread isnt the problem, i know  the screen is fine because it works fine with windows and when it boots up.  it isnt the battery, because its a desktop, and it doesnt say anything about "checking battery state".  The lines are the opposite color of whatever is around them, on this site they appear blue, theyre green against my blue background.  They pretty much stay constant as far as size and location.  its not an nvidia card, its integrated.  where do you get the drivers that (im assuming) i need?  whats apt-get?

---

### Post by teaker1s on 2005-11-12
how about trying screen resolution and size first in system-preferences-screen resolution.
If you don't find a dell issue or suggestion

it could be xserver thats detected the graphics and screen wrong try other solutions first and if all else fails
terminal and type
"sudo dpkg-reconfigure xserver-xorg"
and use the wizard to set it up-be aware any errors and the gui won't boot but you can still boot in recovery mode and run the wizard again

---

### Post by slade on 2005-11-13
[QUOTE=teaker1s]how about trying screen resolution and size first in system-preferences-screen resolution.
If you don't find a dell issue or suggestion

it could be xserver thats detected the graphics and screen wrong try other solutions first and if all else fails
terminal and type
"sudo dpkg-reconfigure xserver-xorg"
and use the wizard to set it up-be aware any errors and the gui won't boot but you can still boot in recovery mode and run the wizard again[/QUOTE]
thanks, that worked.  although now the screen is a lot smaller than i wanted.  is there any way to fix the problem but keep a larger resolution?  would i need to get a video card?

also, i have a few more problems.  before i could not get online thorugh my wireless linksys system, but i could get online when i just attached an ethernet cable and set up the connection as DHCP.  today, the ethernet cable no longer works and i cant get online at all.  i tried reconfiguring the network settings but it didnt work.  does anyone know what the problem is, and why it suddenly doesnt work today?  i can get online fine through this computer.  i just have the ethernet cable plugged into the back of the router.    Also, how would i set up the wireless connection?  What is/what do i put down for the ESSID?

:edit:  oh, and when ubuntu starts up it pauses when it says "initializing network" or something like that, but after a minute or so it passes that line and continues with the startup.

One more thing.  When ubuntu starts Gaim starts twice as in (if i could get online) i have two buddy lists and if someone messages me two windows appear.  i think i did that by accident.  how do i fix that?

---

### Post by Donnut on 2005-11-13
lets see, I'll help how I can.  Close out both versions of Gaim and then open one.  Log out and hit "save session"  When you hit "save session" it will boot at your current window settings every time.

As far as network goes, I have found that unless the ethernet is disabled, wireless sometimes will not connect, and it pauses during bootup to search ethernet for an active connection.
Hope some of this helps!

---

### Post by slade on 2005-11-13
[QUOTE=Donnut]lets see, I'll help how I can.  Close out both versions of Gaim and then open one.  Log out and hit "save session"  When you hit "save session" it will boot at your current window settings every time.

As far as network goes, I have found that unless the ethernet is disabled, wireless sometimes will not connect, and it pauses during bootup to search ethernet for an active connection.
Hope some of this helps![/QUOTE]
Thanks, I think that was the problem with Gaim.  I didnt know what save session was.  it definately sounds useful though.  Although, i need to get the internet working before Gaim will really matter.

the wireless would not connect when i tried connecting before trying the ethernet cable.  i got online through the ethernet cable because i could not get the wireless to work, although now the ethernet is not working either.  I dont think i changed anything that would keep it from working.  And I still dont know what to put down for the ESSID, if i try the wireless connection.

---

### Post by slade on 2005-11-13
the ethernet cable is working now.  for some reason the domain name wasnt there although i didnt change it.  I still need to know what the network name/ESSID is to get the wireless connection working.

does anyone know if id need to get a video card for ubuntu to work with a higher resolution?  what video cards work best with ubuntu?

---

### Post by Donnut on 2005-11-13
Hard to know, ATI cards are a pain, but once I got it working right, it worked better than windows.  To run at a different resolution, type "sudo dpkg-reconfigure xserver-xorg" then answer the questions and choose all the resolutions you want to use.

---

### Post by slade on 2005-11-16
[QUOTE=teaker1s]it could be xserver thats detected the graphics and screen wrong try other solutions first and if all else fails
terminal and type
"sudo dpkg-reconfigure xserver-xorg"
and use the wizard to set it up-be aware any errors and the gui won't boot but you can still boot in recovery mode and run the wizard again[/QUOTE]
my other computer just died yesterday, so i put extra parts in this computer, including another stick of ram, a sound card and video card.  its a GeForce 3 Ti 200.  i could see the screen fine but it wouldnt boot up past the terminal.  i tried typing "sudo dpkg-reconfigure xserver-xorg" in the terminal and went through the setup, everything went fine, it autodetected the video card...  then it went through the rest of the setup about the keyboard and mouse, etc.  when it got to the page about color, after pressing "enter" it went back to the terminal and had the message "xserver-xorg postinst warning:  overwriting possibly customized configuration file; backup in /etc/X11/xorg.conf.200511161951".  at that point i didnt know what to do.  im pretty sure it didnt actually overwrite the file, since it wouldnt boot after that, and nothing changed if i pressed ctrl+alt+f7.  it did create the file xorg.conf.200511161951 though.  when i took out the video card at first the same thing happened, but after i restarted it booted normally.  what was i actually supposed to do at that point?  everything seemed to go fine during the configuration.

---

### Post by slade on 2005-11-20
[QUOTE=slade]my other computer just died yesterday, so i put extra parts in this computer, including another stick of ram, a sound card and video card.  its a GeForce 3 Ti 200.  i could see the screen fine but it wouldnt boot up past the terminal.  i tried typing "sudo dpkg-reconfigure xserver-xorg" in the terminal and went through the setup, everything went fine, it autodetected the video card...  then it went through the rest of the setup about the keyboard and mouse, etc.  when it got to the page about color, after pressing "enter" it went back to the terminal and had the message "xserver-xorg postinst warning:  overwriting possibly customized configuration file; backup in /etc/X11/xorg.conf.200511161951".  at that point i didnt know what to do.  im pretty sure it didnt actually overwrite the file, since it wouldnt boot after that, and nothing changed if i pressed ctrl+alt+f7.  it did create the file xorg.conf.200511161951 though.  when i took out the video card at first the same thing happened, but after i restarted it booted normally.  what was i actually supposed to do at that point?  everything seemed to go fine during the configuration.[/QUOTE]
any help?  i downloaded automatrix which will install video drivers for NVIDIA cards, but the problem is, the card needs to be in when you run the program so it can detect the card, but if the card is in i cant get past the CLI when i start the computer.

also the sound card isnt working, it still plays through the integrated sound.  does anyone know how to change that?  i changed it under system>preferences>sound, but that didnt do anything.

thanks everyone.

---

