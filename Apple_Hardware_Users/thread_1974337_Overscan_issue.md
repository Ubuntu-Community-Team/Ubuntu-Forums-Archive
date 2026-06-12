---
title: "Overscan issue"
date: 2012-05-05
forum: Apple Hardware Users
---

### Post by poconnell2005 on 2012-05-05
It's been a while for me since I have attempted to use Ubuntu though when I last did, I loved it. Currently, I'm trying to run 12.04 on my 2007 Mac Mini but have run into an issue. My display is a Sanyo 720p LCD. It had all installed beautifully, except for the fact that my desktop is a bit oversized for the display. When I am in OSX I ran into the same issue but there all I needed to do was tick the overscan box in the display settings and all was well with the world. In Ubuntu, there is no such option. I'm a bit at a loss with this as I have absolutely no idea where to even begin to resolve this make or break issue (I am only able to see the right side of the icons on the left, I don't see the bar across the top at all and see nothing on the bottom of the screen either). I'd love some advice at this point. And since I'm extremely rusty, I am also hoping that that advice is extraordinarily dumbed down for a long time noob. 

Thanks in advance.

---

### Post by papibe on 2012-05-05
Hi poconnell2005.

Is the Sanyo an HDTV?
What is your graphic card?

Regards.

---

### Post by poconnell2005 on 2012-05-05
Thanks for taking the time. 

Yes, it's an HDTV, though with no settings on it that help with this issue. The only settings it contains are things like color, contrast, etc. I can also zoom in and out on the screen, but that does not help at all. 

The mini is a 1.83 GHz model with integrated graphics (Intel). It is connected to the mini via a dvi to hdmi adapter.

---

### Post by papibe on 2012-05-06
There's a good chance you can solve your overscan problem using 'xrandr'. Unfortunately, I don't have much experience with it.

Search the internet and the forums for tips on how to use it.

With luck someone else will pitch in.

Kind Regards.

---

### Post by poconnell2005 on 2012-05-07
So I gave xrandr a shot last night but to no avail. I was only able to adjust the resolution which just made the screen more blurry with only a slight increase in visibility of the desktop edges. And what could be seen was stretched.

Any other advice would be helpful. I love the os, but as is it is unusable.

Thanks again.

---

### Post by papibe on 2012-05-07
I found 3 ways people use to fix overscan using xrandr: [here]("http://forums.freebsd.org/archive/index.php/t-20987.html"), [here]("http://ubuntuforums.org/showthread.php?t=1849599&highlight=intel+overscan+xrandr&page=2"), and [here]("http://forums.overclockers.com.au/showthread.php?t=862388&page=10").

My bet would be in post#14 from the second link.
Regards.

---

### Post by poconnell2005 on 2012-05-08
I certainly do appreciate your help. Perhaps it's my lack of knowledge, but all I have been able to do is bring the right side of my screen WELL within the border of the monitor. Almost like it is a 4:3 display output onto a 16:9 monitor. Except the delightful part is that the left side of the screen is still stretched out past the viewable area. I'm sure at some point I'll figure it out, but in all honesty I am at a loss and feeling rather frustrated with the issue. I love the idea behind as well as (most of the) execution of Ubuntu, but not being able to get the screen to show within the border of my display without having to go and purchase another monitor is disheartening.

Thank you again though.

---

### Post by poconnell2005 on 2012-05-08
We have liftoff!

Not long after I last posted, I decided to go a-hunting for information on the specific TV I have. While I did not find my specific model, I did find some information about a hidden menu for Sanyo TVs. The instructions to access it remind me of the Contra cheat for some reason but they worked. Ridiculous that it is that difficult to adjust something that is so basic on other makes. 

Anyway, for others that may run into this issue and are unable to figure it out, I got the instructions from this site: [http://osxtechtips.com/?p=237](http://osxtechtips.com/?p=237)

Here are the instructions copy/pasted from that site (hope that is OK):

Turn off the TV.
Unplug all devices from the back of the TV.
Unplug the AC power to the TV.
Press the Power button several times with the AC power unplugged, then hold the power button in for about 30 seconds with the AC power still unplugged. (This often took me several attempts to get the menu to come up).
Hold down the Channel Down button on the side of the TV, while holding it down, plug in the AC power.  Once you hear the TV turn on, release the Channel down button immediately.  Within a few seconds you should see a two row menu come up on the screen.
Use the Up/Down and Left/Right arrow keys on the remote (D-pad) to cycle through the options.  This will be accomplished with the left-most number highlighted  in a green block.  You will want to use the Up/Down arrows to move to Item #25 (LetteerBoxOvSc).
Now use the Left/Right arrow to move the green box to the column labeled “Value”.  Change the number to 0 using the Up/Down arrows, then use the Left/Right arrow to move back to the  ”Index” column.
Now use the Up/Down arrows to go to item # 55 (LeftOvS), and again use the Left/Right arrow to move to the “Value” column and change the number to 0 using the Up/Down arrows.
Move back to the “Index” column and repeat step 8 for items 56 – 58 (RightOvS, TopOvS, and BottomOvS).
When all items are 0, press the “Menu” button on the remote to return to regular viewing mode.
Turn off the TV.  Re-connect a device that you know Overscans, and see if it looks proper now.
If it does, then reconnect all devices and enjoy.
If not, then you cn navigate back in and make the changes again.
Hope this helps anyone else having this issue.

Thank you again for your help.

---

### Post by papibe on 2012-05-08
Super! I'm glad you solved your problem.

Thanks for sharing your solution too. This way other Sanyo owners in the forums will have a better chance to solve their overscan problem as well.

:) Kind Regards

---

