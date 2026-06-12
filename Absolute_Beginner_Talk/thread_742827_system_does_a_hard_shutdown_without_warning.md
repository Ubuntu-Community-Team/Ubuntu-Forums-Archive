---
title: "system does a hard shutdown without warning"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by satanic-yobbo on 2008-04-02
i have been using gutsy for a while now and have had little or no problems at all untill i started to get a complete shutdown without any prior warning at all it seems like i have just pressed and held the power button for a few seconds and shut it down like that but i havent gone anywhere neear the power button to turn it off and it does so without any signs of over heating or system load and also it doesnt matter what programs i have running this just happens when it feels like it 

does anyone have an idea on why,, or how to fix this problem?? please ... ps i am still reasonably new to linux so please be newbie friendly with me :) ..

---

### Post by viciouslime on 2008-04-02
Is this machine also running windows? Does it happen with windows too? This sounds very much like a hardware problem rather than a problem caused by any operating system. Do you have a high-end graphics card and if so, have you installed the proprietary nvidia/ati driver?

---

### Post by frezasaga on 2008-04-02
nvidia is oki with ubuntu but ati its too hard to deal with it..........

---

### Post by stefangr1 on 2008-04-02
See also this thread with the exact same (unsolved) question:

[http://ubuntuforums.org/showthread.php?t=742000](http://ubuntuforums.org/showthread.php?t=742000)

---

### Post by satanic-yobbo on 2008-04-02
no this does not happen at all under windows it can run for a week without any problems and i do not have a high end graphics card just the standard card that came with the pc which is ati i think ....it seems like my pc is using a lot of memory but which is unusual such as 72.7mb for pidgin and 62.9 for the trash applet 96.4 mb for nautilus 160.8 for firefox which is unbelieveable and 63.7 for the deskbar applet would this be in any way related at all ??

---

### Post by viciouslime on 2008-04-02
Linux makes use of all available memory all of the time wherever possible, to give the best possible experience. You'll notice that if you start some other application that is memory intensive, those programs will just give up the memory they're using, so it is unlike that this is related.

It could be that ubuntu is being slightly less power efficient in the way it operates your computer, this could be requiring more power than the computer's power supply can handle, causing it to shut off. However, the difference, if there is one, between power drawn in ubuntu and power drawn in windows, especially if you don't have a high end graphics card, should be negligible.

It could well be that in windows you're right on the limit though...

Could you provide the specs of your machine and the rated power output for your power supply(should be written on it)? Just so this can be completely ruled out.

---

### Post by satanic-yobbo on 2008-04-03
pent.4   512mb ram 2.8 ghz but this shows in system monitor as being 2x 2.8 which it may be i am not sure how to check this out and i got this pc from a friend so dont have original documentation to look at and power supply is output 200w +3.3v=14 a +5v= 21a +12v= 10a +sb= 2a -12 =0.5a is this the info you need on the power supply ?

---

### Post by The Titan on 2008-04-03
i agree that this sounds like a hardware problem, and i don't know why it would say 2x 2.8, did you maybe install the 64bit edition on accident or something.  I'm  not sure if this would even work or cause this problem, just a theory. BTW. Nice sig :lol:

---

### Post by satanic-yobbo on 2008-04-03
no i am reasonably sue  it is the correct edition installed  and i can see in system monitor.>system and under hardware it says  

memory 500.6 ( 512 card)
processor 0: intel pent.4 cpu 2.80 ghz
processor 1: intel pent.4 cpu 2.80 ghz 
which i think is saying that there is a master and a slave there ?? is this correct that it is what its saying ?

---

### Post by viciouslime on 2008-04-03
Sounds like a dual core P4, I'm fairly sure they exist. I think they were called Pentium 4 D or something...

Basically that means you essentially have two processors on one chip, however, I should imagine this processor could draw 100W of power alone, then there are all the other components to your system.

Furthermore, a power supply rated at 200W, won't necessarily cut out at 200W, as you can see from the specs you listed, you can only draw 10A from the 12V rail, so if you had something, or several somethings combined, drawing more than 120W from the 12V rail, the PSU would cut out.

Really, in a system like this, you could do with at least a 300W PSU, if you are going to replace it, look for something that has as high a current rating as possible on the 12V rail, this is generally a good indication of quality of the PSU too.

As to why it works in windows, it probably only just works in windows, you're no doubt pushing the PSU to its maximum which will probably result in an early death for it. If you'd like any more help/advice on this, please get in touch, I'm no expert on this and there might be someone else on here who can give a better explanation, or indeed recommendation, but personally I think a new PSU rated somewhat higher than 200W is the way to go.

---

### Post by satanic-yobbo on 2008-04-03
ok yeah i understand why it would cut out yeah i think i will try a replacement power supply and see what happens if this works i will be very happy as i never wish to use windows at all again so i am willing to try anything to keep ubuntu on this pc and this sounds like a realistic reason for a shut down like this. i am educated in electricals and power just not so much on computers but its all the same when it comes to power so i will try a new bigger power supply and see what that does for me .. until then i will keep this thread open or "unsolved" to re-access it later if i need to post more on the specific problem..

 thankyou for the advice and the help i appreciate it a lot

---

### Post by LukeCarrier on 2008-04-03
Really does sound like somebody needs to buy a bigger power supply. A 300 watt should suffice, but I'd buy a 400 watt or above just to be on the safe side. Heck, my PC runs off a 700 watt :D

---

### Post by viciouslime on 2008-04-03
Lol 700W would certainly do the trick, little bit like overkill though... Since you haven't got a high end graphics card you shouldn't need to spend too much on it 3/400W should be fine, maybe you can borrow a friends to try it first?

Let me know how it works out for you :)

---

