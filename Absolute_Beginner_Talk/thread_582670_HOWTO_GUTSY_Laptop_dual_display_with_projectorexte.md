---
title: "HOWTO GUTSY: Laptop dual display with projector/external screen"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by tboxmy on 2007-10-20
Just installed Ubuntu 7.10 Gutsy and was in for some surprises. The VGA output for the laptop worked without much fuss. I had to find this out after manually changing the xorg.conf a thousand times. Today I learnt that you dont need to touch the xorg.conf at all, duh!

What I wanted to do was to be able to plug-in the external Projecter/LCD screen at any time my system is running. A problem I found was that when I played a video with TOTEM or VLC, The video only appeared on the external screen.

My hardware specs:
Lenovo R60 
Display: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller

I found that Gutsy detected and is using an Intel experimental driver for the 945.

1. Start Gutsy and stay at the login screen. Press Ctrl+Alt+Backspace
2. Plug in the external display
3. Log-in and you can see two screens.
4. Play a movie and it appears on the external screen.
It is working!

Next problem, You have watched the movie on the external screen now you want to remove the external screen and resume work as normal. This includes watching movies on the laptop.
1. Logout and remove the external screen cable.
2. At the login screen press Ctrl+Alt+Backspace
3. Login
4. Play a movie and it appears on the laptop screen.

All done!

---

### Post by Crafty Kisses on 2007-10-20
> **tboxmy said:**
> Just installed Ubuntu 7.10 Gutsy and was in for some surprises. The VGA output for the laptop worked without much fuss. I had to find this out after manually changing the xorg.conf a thousand times. Today I learnt that you dont need to touch the xorg.conf at all, duh!

What I wanted to do was to be able to plug-in the external Projecter/LCD screen at any time my system is running. A problem I found was that when I played a video with TOTEM or VLC, The video only appeared on the external screen.

My hardware specs:
Lenovo R60 
Display: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller

I found that Gutsy detected and is using an Intel experimental driver for the 945.

1. Start Gutsy and stay at the login screen. Press Ctrl+Alt+Backspace
2. Plug in the external display
3. Log-in and you can see two screens.
4. Play a movie and it appears on the external screen.
It is working!

Next problem, You have watched the movie on the external screen now you want to remove the external screen and resume work as normal. This includes watching movies on the laptop.
1. Logout and remove the external screen cable.
2. At the login screen press Ctrl+Alt+Backspace
3. Login
4. Play a movie and it appears on the laptop screen.

All done!
Nice one.

---

