---
title: "?ask your administrator to remove..."
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by tpz78 on 2006-09-23
...the xpti.dat from the component directory of mozilla or netscape application.

 this was the last thing i was told to do upon completing the installation of the flash player that has been giving me so much trouble.

lets go to the start. go to clevelandbrowns.com. there is a "window" with pictures and news stories there on the main page. at least usually. when i go to that site,the window is not there, only text that says "alternate html content should be placed here. this content requires the macromedia flash player."

ok. i have identified the problem. i dont have flash. i have been trying for several days to get this plugin on my system. i can't, and its driving me mad.

i used automatix and downloaded the flash player, but i still cant view the content on clevelandbrowns.com. i tried the synaptic packaging thing, it didnt work. so i decided to use the terminal and do it manually. i downloaded the program. i extracted to the desktop. i went to the directory in the terminal and ran ./flashplayer-installer. it told me some fornts had to be added, cool, close any browsers, did that, and finally that the administrator had to remove the xpti.dat from the component directory of mozilla or netscape application.

in my terminal i typed "cd /". this gave me a huge list of things. one of which is "etc". i type "cd etc". then "ls". after another huge list of things, i see "mozilla-firefox". "ls" in the mo-fox directory reveals "mozilla-firefoxrc" "pref" and "profile". i hit "ls" in each one of these but could not find the xpti.dat. 

where can i find the xpti.dat for mozilla, and how do i remove it? i've searched the forums all night and can't find it. pleaqse help.:confused:

p.s. if you can't tell, i'm a complete newb to ubuntu,firefox, linux, whatever. i'm just tired of all the viruses and pop-ups of windows. i like the OS, but it's a little intimidating.

---

### Post by ronmarley1 on 2006-09-23
Welcome to Ubuntu!  Sorry, I can't help you with the Flash problem.  My guess is you probably need a newer version that's not out for Linux yet.  As far as finding files, in a terminal, you can type locate <filename>.  If you prefer a graphical search tool, you can right click on a panel (the bars at the top or bottom of the screen) and ten click "+ Add to Panel" and scroll through the list.  Under Utilities is "Search for Files..."  Click on it and it will add a launcher (Shorcut, in Window$-speak) to the Panel.  Click the icon to launch the Search applet.  
Go Browns!  I'm a season ticket holder in the Dawg Pound, Section 120, row 32, seat 7.  I'll be there tomorrow.  Stop by if you're ever at a game!

---

