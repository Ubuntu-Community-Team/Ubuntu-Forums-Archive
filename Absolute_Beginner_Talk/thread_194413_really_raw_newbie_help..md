---
title: "really raw newbie help."
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by FIST on 2006-06-11
ok so i took the plunge last night and installed ubuntu on my laptop. went really smooth and didn't give me any problems( or it did and i just don't know what to look for).

anyway i was able to connect to my internet connection no problem last night but this morning i cant get anything. not sure where to start looking to find out why.

secondly i just sort of noticed that when i minimize a window it just sort of goes away. i don't see how to bring it back up.

thanks.

---

### Post by mscman on 2006-06-11
[QUOTE=FIST]anyway i was able to connect to my internet connection no problem last night but this morning i cant get anything. not sure where to start looking to find out why.[/QUOTE]
What type of internet connection do you have?  Also, if it's broadband, are you connected straight to your DSL/Cable modem or do you use a router as well?

> secondly i just sort of noticed that when i minimize a window it just sort of goes away. i don't see how to bring it back up.
There should be a bar at the bottom of the screen showing what programs are running.  If the panel is there but there is no list of running programs, right click on the panel and choose "Add to Panel..."  Then you want to choose "Window List" and click "Add" then "Close".  Your programs should appear there when running and when minimized.

---

### Post by Fafnir on 2006-06-11
[QUOTE=FIST]ok so i took the plunge last night and installed ubuntu on my laptop. went really smooth and didn't give me any problems( or it did and i just don't know what to look for).

anyway i was able to connect to my internet connection no problem last night but this morning i cant get anything. not sure where to start looking to find out why.[/QUOTE]

First place to look is (from the top menu) System->Administration->Networking. If you're on a network connection, you want the interface 'eth0', and if you're using a modem, you want 'ppp0'. Select the right interface and click "Properties", then check that all the data seems to be correct. Also check the stuff under General, DNS and Hosts. If you can't find the problem (or don't understand what the information means), post everything in those places here, plus everything you know about your network/internet connection, and we'll try to fix it.

Also, if you have experience in diagnosing network problems, you can get to ping, traceroute etc. by going to System->Administration->Network Tools (again on the top menu). If you don't have experience, don't worry.

[QUOTE=FIST]secondly i just sort of noticed that when i minimize a window it just sort of goes away. i don't see how to bring it back up.[/QUOTE]

There *should* be a panel at the bottom of the screen where you can select minimised programs - like the Start Bar in Windows. It might be set to autohide, in which case if you move your mouse to the bottom of the screen and wait a few seconds it should pop up. If you want to disable autohide, right click on an unoccupied area (you may need to close a couple of programs to get one) and select Panel Properties. From there, just uncheck autohide and click OK.

If there isn't, it may have been deleted somehow - I'll walk you through how to reconstruct it. 

Right-click the menu bar at the top of the screen, and select Add Panel - a bar should appear on one of the edges of the screen. Drag it to the bottom edge, right click it and select Add to Panel. Select Show Desktop, and click OK. Right click on the button that has appeared, select Move, and move it to the far left of the panel. Then add a Window List, and move it just to the right of the Show Desktop button. Add a Wastebasket to the far right side, and a Workspace Switcher to the left of the Wastebasket. One new panel! 

Don't be afraid to experiment with the other things in the Add to Panel dialog either - if you add something you decide you don't want, you can remove it by right-clicking it and selecting Remove From Panel, and nothing you can do there will damage your system, so go for it! There's some neat stuff there :-)

---

### Post by FIST on 2006-06-11
i thank you for the help.

as far as my connection goes, its a dsl. all i had to do before was plug the cat5 in and it worked.  now for some reason i can't go to any webpage. its showing the connection as active and all but nothing is going through it.

i was going to post whats in the System->Administration->Networking but now that wont even open anymore. it still shows eth0 in the bottom right corner but i can't get to the properties. i must have done something wrong somewhere....

and again thanks so much for the help.

---

