---
title: "Multiple Instances of Firefox with Dual Monitor"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by jezebel on 2008-02-09
Hi.

I finally got my dual monitor set up to work under Gutsy (I installed Envy, then a little trial and error in the Nvidia settings (have a cheap Geforce FX5200)).

I'm running the monitors as separate X screens. I cannot drag a window from Screen 0 (default) to Screen 1 (secondary); however, if I have Firefox running on Screen 0, I cannot open it on Screen 1. When I try, I get the error message: 

"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

In Firefox, if I go to File - New Window, it just opens on whatever monitor I'm running in originally, which I no help to me. Ideally, I want to be able to watch streaming videos while surfing other stuff...

I'm an *absolute* beginner here. I look forward to any and all help, and would be especially delighted if said help were delivered in extremely simple and very detailed form:) Seriously - you can't make it too simple for me!

---

### Post by vinnybad on 2008-02-09
Hey,

when you say you have two separate xscreens...do you mean that you manually did something that launched 2 screens?  I'm pretty sure Ubuntu will let you detect another monitor and "extend your desktop" to the other monitor, kinda like windows.

Or is that what you've done?

---

### Post by jezebel on 2008-02-09
By separate screens, I mean that, in my Nvidia settings, I chose the "Separate X Screen" option, which means that each of my two monitors has it's own complete desktop (with the menu and logout options, etc). I had first tried extending the screen, but couldn't get the resolutions to stick, since I'm using one monitor that's 1440x900, and another that's 1024x768. 

Also had a few other issues, and It took about three hours for me to get both monitors running correctly, so I'm loathe to alter that:lolflag:

Any ideas for getting two instances of Firefox to run?

J.

---

### Post by nynoah on 2008-02-09
you could just download swiftweasel.....and run one of each in each screen

I really like swift better than firefox anyways.

---

### Post by jezebel on 2008-02-09
Thanks, Nynoah!

I was wondering about installing a second browser, but am so attached to Firefox. I'd never heard of Swiftweasel, and I just installed it and love it.  It works great, and kept all my bookmarks from Firefox. 

I'm now streaming The Family Guy on one monitor while typing my thanks into this forum on another.

J.

---

### Post by nynoah on 2008-02-09
swiftweasel and firefox are cousins basically.  Also if you want to try any other browsers, try Opera.  That is a good one too.  But the version for 64 bit is in the Beta version.  teh 32 bit version is easily to get though.

---

### Post by kmoguinn on 2008-04-01
Here is the fix and how it works. (Btw, I did not come up with this solution, I read it myself somewhere else on the boards and it worked for me.)

run firefox -ProfileManager

create a second profile, then on your second monitor, when starting firefox, start it with

firefox -p whateveryourprofilenameis

The -p will allow you to select a different profile for firefox to run with.

Make sure you update your shortcuts on the second monitor to reflect you want it to start with a differnet profile, otherwise it will give you the same old error.

The reason x is complaining about it already running is because an instance is already running with your default profile (settings and stuff.)
You can have two instances of firefox running with no problems, but you can't have two instances running using the same settings, it's a contention issue.

The favorites and preferences won't be sync'd between them (since they a different profiles) but it will allow you to run multiple instances of firefox.

---

