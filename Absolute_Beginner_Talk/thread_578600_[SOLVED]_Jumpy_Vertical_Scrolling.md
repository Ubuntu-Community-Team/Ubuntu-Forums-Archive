---
title: "[SOLVED] Jumpy Vertical Scrolling"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by jamiehendrich on 2007-10-17
 NOVICE QUESTION NO. 1:    I have Edgy installed with a Firefox browser.  Is there a very simple way to correct my "jumpy/wavy" vertical scrolling other than to go into sudo gedit/device and changing the "vesa" to "nvidia"?  I don't have the drivers installed, do not know how to do it, and my "too busy" teacher would absolutely ring my neck if I tried to do it on my own, and he'd tell me, if I mucked up the settings, "tough!"  Why is it doing this?  Maybe it is just a simple setting I need to make.  

Jamie

---

### Post by jordanmthomas on 2007-10-17
You can try turning off smooth scrolling in firefox: Edit --> preferences --> Advanced and uncheck smooth scrolling.

Using the vesa driver you will likely still have a hard time though.

---

### Post by jamiehendrich on 2007-10-17
Jordan, "use smooth scrolling" was  already unchecked.  I checked "use autoscrolling" just to see if that would help to no avail.    It obviously is a "Nvidia" problem which this greenie/novice knows absolutely nothing about.  So thank you so much anyway.

Jamie

PS  You would not know why I cannot see  a full page on my screen, would you?  Explanation:  When I go into "Ubuntu Forums," I see the title "Ubuntu Forums and then "reply to thread," and then only about an inch of the box in which to type a reply is showing and I have to scroll down to get the full box and my text is very small.

---

### Post by jordanmthomas on 2007-10-17
I'm not sure what you mean with your PS.  Perhaps you could take a screenshot (just hit the printscrn button on your keyboard) and upload it here?

Scrolling will always be slow if you're not using drivers that provide any acceleration.  If you don't want to install the nvidia drivers, you may have luck with the 'nv' driver.  Vesa is just too slow.

---

### Post by jamiehendrich on 2007-10-18
Thank you so much,  Jordan.  Never mind about the PS.  I will check on the driver and see what happens.

Jamie

---

### Post by jamiehendrich on 2007-10-18
PS  By the way, Jordan, I just noticed that my vertical scrolling on the machine I am on now was set up the exact same  way, with an Edgy CD ,  as the machine I have at my office that is having vertical scrolling problems.  I just noticed it.  So if I did not install any special drivers, wouldn't that mean I have an incorrect setting of some sort?

I will tell you that the machine at my home is a faster machine than the one at the office.  Does the CPU speed have anything to do with scrolling?

Jamie

---

### Post by jamiehendrich on 2007-10-18
My above message was worded incorrectly.  My apologies.  

The computer I am working on now has no problem with vertical scrolling.  I just noticed it.   It is the one at the office that has the wavy, slow vertical scrolling.  They both have Edgy  and no special drivers were put on either.  

However, the one at the office is a slower computer; the one at home is a faster computer.  Is there any correlation there with the CPU speeds causing the problem?

Jamie

---

### Post by jamiehendrich on 2007-10-18
One last thing.    When I dry to download Noia Xtreme on the "trouble" computer, not my home computer,   my orange horizontal download bar at the bottom that shows that something is downloading goes only halfway and stops.    So it just starts and stops, and I cannot download Noia.  There's a little white "wheel"  that shows something is downloading and that just keeps going round and round, the orange bar goes halfway and stops.  It will do that indefinitely until I  touch my mouse, and then the little white download "wheel"  stops.  Are you sure I haven't messed up a setting?  It almost sounds like it's all related somehow.

Jamie

---

### Post by bobpur on 2007-10-18
> **jamiehendrich said:**
> NOVICE QUESTION NO. 1:    I have Edgy installed with a Firefox browser.  Is there a very simple way to correct my "jumpy/wavy" vertical scrolling other than to go into sudo gedit/device and changing the "vesa" to "nvidia"?  I don't have the drivers installed, do not know how to do it, and my "too busy" teacher would absolutely ring my neck if I tried to do it on my own, and he'd tell me, if I mucked up the settings, "tough!"  Why is it doing this?  Maybe it is just a simple setting I need to make.  

Jamie

Go ahead and try to fix it!! Check the forums and Google for info. As for your "Too busy" teacher...
The beauty of linux is: 1)  " That if you break it you get to keep all of the peices." and 2) "How are you going to learn  it if you don't "break it." :) :)
Disregard advice if computer is teachers or "significant others."
Seriously, It seems to be a graphics driver issue(or lack of). See new version of Ubuntu, out today, which includes graphics drivers. Now, go back to first paragraph.

                                                             Good Luck!!

---

### Post by LowSky on 2007-10-18
i have broken linux video drivers so many times im getting used to typing 

sudo dpkg-reconfigure xserver-xorg

its amazing what this command does in safe mode

---

### Post by jamiehendrich on 2007-10-18
Sorry, Bopur, but I cannot load the newest version of Ubuntu with graphics drivers.    My "too busy" teacher told me I had to stay with Edgy.  So thanks anyway.

Jamie

PS  May I make a suggestion?  Would you mind working on your sentence structure from here on out.      A portion of your message was completely incoherent regarding "teachers" and  "significant others" -- whatever that means -- and disregarding the advice.

---

### Post by jamiehendrich on 2007-10-18
I'll try typing in that command and see what happens.

Thank you.

---

### Post by jamiehendrich on 2007-10-18
I hope my response did not sound curt, Bopur.  I'm sorry if it did.  I just did not know what you meant.  Anyway, I do not want to break my machine and learn "the hard way."  I just wish someone could tell a greenie which buttons to push, then it would be set, then I could just leave it alone and do my work on my very specialized software.  My teacher always says, "If you break it, you get to keep the pieces."  No thank you to that.    Thank you for your comments, though.

Jamie

PS    If I used the same CD to remove Windows and upload Ubuntu Edgy Eft on both of these computers, I just cannot understand why one would work and not the other.   One is a fast Dell computer; the other a slower HP.  If it's a graphics driver issue, would I not be having the same on both computers?  

Unfortunately I think I am going to have to continue with wavy scrolling on this computer.

Jamie

---

### Post by jordanmthomas on 2007-10-18
> If it's a graphics driver issue, would I not be having the same on both computers? 
Certainly not.  For one, the two machines probably have different graphics cards.  The reason the "good" drivers were not preinstalled is that nvidia doesn't play along with the idea of "free" very well.  They do not open the source of their driver and many people simply won't use it because of this, and this is why it's not installed by default.  Assuming they have the same graphics card, the faster machine would possibly be able to handle the scrolling using just its CPU and no graphics acceleration.  The slower machine probably just can't keep up (scrolling a web page is serious business).  Even with graphics acceleration my CPU jumps to 100% when scrolling in firefox.  I will say there is less of an issue in Opera which seems to do everything faster than firefox.

As for your magic button you're looking for:  it simply doesn't exist.  Since you're stuck with edgy, you're going to have to edit your /etc/X11/xorg.conf.  You seem to be a little afraid you'll mess up your system.  Don't worry about it.  The worst you'll do is make it so that X (your graphical display) doesn't come up.  In that case you'll just need to change nvidia back to vesa and restart; nothing too tough.  If this happens, just look for instructions on the forums on how to do it, or better yet, learn beforehand how to fix it.  Check out lowsky's comment.  (Again, it's not very difficult....just intimidating perhaps, I promise)

So, if you decide it's worth editing a file or two to be able to enjoy browsing the web, look [here.]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-683579986265cf8ec1604def825232dd8f32eb35")  If there's anything that you don't understand, post back here and someone will be glad to help you out.  I suppose you could call my link the "button you need to push".

Good luck.

---

### Post by jamiehendrich on 2007-10-18
"Seem a little afraid?"  How about "petrified?"   If I don't mess it up, it'll be the first time.  :)   All of these issues are wearisome when one knows nothing about computers.

Anyway, I clicked "here" and the instructions are really long but seemed fairly clear.   Maybe I will try it  in the next couple of days.    Silly me.  I thought the drivers were in the operating system.   Greenie!

Final question before I try this:  I have done the procedure before with the synaptic package.  So that part I get.   I also have something called "Automatix."    And I launched it and the word "drivers" was there.  So I clicked on "Drivers" and there was "nvidia."  So I tried to install it this afternoon.   It got almost to the end and this was the error message:

"There was an apt-based error.  Nvidia did not install."  

So is that just another way of doing it and I have another glitch?  "Apt-based error?"

Thank you, Jordan.  I really appreciate your help.

Jamie

---

### Post by jordanmthomas on 2007-10-18
I'm not sure why Automatix failed.  It could be for any number of reasons.  Odds are, it was a problem with Automatix.  Any help with Automatix can be found [here]("http://www.getautomatix.com/forum/").  Because Automatix isn't open source, it's difficult to know exactly what went wrong.  The people there are more knowledgable on the subject.

---

### Post by jamiehendrich on 2007-10-18
thank you.  I'll try it the other way.

---

### Post by jamiehendrich on 2007-10-24
  Woo-hooooooooooooooooooooooooooo!  It worked!

Thank you jordanmthomas for the "click here" link on how to very simply install an nvidia driver in Ubuntu so that my vertical scrolling is not jumpy or wobbly.   This is magnificent!!!!!  My goodness, if I knew it would be so simple I would have done it five days ago.  You were right.  It is just a few simple steps and voila, perfect scrolling.  I absolutely, positively cannot thank you enough.

Thank you, bopur, for your input.  You were correct as well.  

And, last but not least, thank you LowSky for  "sudo dpkg-reconfigure xserver-xorg"just in case I messed up which thankfully I did not have to use it because everything  went through  perfectly the first time.

Jamie

PS  I absolutely love this web forum.  it is soooooooo helpful.:KS

---

