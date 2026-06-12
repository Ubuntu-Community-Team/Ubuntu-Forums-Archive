---
title: "Ubuntu 11.04 and Compiz Enhanced Zoom"
date: 2011-05-18
forum: Assistive Technology &amp; Accessibility
---

### Post by RKCole on 2011-05-18
Hello, everyone.

I did a fresh install of Ubuntu 11.04 (64-bit) this afternoon. I just enabled the Enhanced Zoom plugin for compiz, and I find that it is quite jumpy compared to Ubuntu 10.10 (64-bit); it ran much more smoothly then. Is there any way that I can change this? I do not even know what could be causing this slight lag, but it is noticeable.

Also, I am using the Ubuntu classic (GNOME) desktop, as I could not zoom in on the top panel nor the launcher bar on the left in Unity, unfortunately.

Is anyone else experiencing a jumpy magnifier using eZoom, or is it just me?

Thanks for any help or input.

Take care.

---

### Post by jschmeau on 2011-05-20
Same here.  I am slightly visually impaired and I rely greatly on the wonderful enhanced zoom desktop plugin.  The new version in Natty is noticeably jumpy and somewhat headache inducing.
Any suggestions would be greatly appreciated...

---

### Post by RKCole on 2011-05-20
Hello, jschmeau.

I have not found out anything further here, and there has been no response (other than yours) on the Compiz Forums. On top of that, it seems that the Compiz Forums have been flooded with spam.

Hopefully we can figure something out. I miss the smoothness of the Enhanced Zoom plugi, and I don't really want to downgrade.

---

### Post by notlistening on 2011-05-22
Hi Guys,


I have filed two bugs similar to this subject:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/786774 ](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/786774 )
[https://bugs.launchpad.net/bugs/774531](https://bugs.launchpad.net/bugs/774531)


However it is on their wish list, please add yourself to affects me and we can grow the number of affected users.


Most applications support zoom with ALT+CTRL and scroll with the mouse button to zoom into things. 

This release has stopped me from using the Enhanced Zoom feature and I have to use a negative workaround. Which is a pain as I use it all the time. I am managing though.

Ubuntu 11.04 seems to have dropped some of its accessibility features by the way side. This is a regression in my opinion.

T

---

### Post by RKCole on 2011-05-23
Thanks, notlistening. I went to the links you provided and added myself to the affected users, as I experience the same things on my end.

This is kind of saddening, as I completely depend on the Enhanced Zoom plugin. Also, I really was looking forward to using Unity, but the plugin does not zoom in on the desktop, and not the top and bottom panels.

I don't really want to downgrade, but my quality of use is definitely diminished.

I guess it is just a waiting game now. I just wish I had programming experience and the ability to work on these bugs...or any bugs for that matter...

---

### Post by Raaaaay on 2011-05-24
Hi, I'm also affected by this and would like to add myself onto the affected people list in the links notlistening posted. How do I do that?

---

### Post by okmat on 2011-05-24
Hello, I managed to get a somewhat smoother zoom tweaking the Zoom Desktop plugin in CSSM (with enhanced zoom disabled). Check the attached screenshot to see if it's of any help

Bye

---

### Post by RKCole on 2011-05-25
Hello, Raaaaay.

In order to add yourself to the affected users, go to the links provided to notlistening, and at the top fo the page under the heading for the bug, you should see something like, "This bug affects [a given number] of users."  to the right of this, there should be something which says something to the effect of "affects you". You click on this link to add yourself, but you may have to create a launchpad account if you do not already have one.

Hope this helps.

---

### Post by RKCole on 2011-05-25
Hello, okmat.

I tried out the Zoom Desktop plugin. It does run quite smoothly, but it unfortunately does not scale the mouse pointer. With my limited vision, I was not able to use it successfully.

I will just have to wait until the Enhanced Zoom plugin is fixed, or whatever is causing the jumpiness.

---

### Post by okmat on 2011-05-27
RKcole, as it turns out, the choppy behavior is due to the "mouse polling" plugin, use CCSM to set the mouse polling plugin to a smaller time (<10) and manually define the "zoom in" and "zoom out" in enhanced zoom:

zoom in: super + button 4
zoom out: super + button 5

info taken from this post:
[http://ubuntuforums.org/showthread.php?p=10847583]("http://ubuntuforums.org/showthread.php?p=10847583")

---

### Post by RKCole on 2011-05-27
Thank you, okmat. That was the solution. Now it works great. Just have to wait until I can zoom in on Unity panels, so I can test out Unity. But I am so glad to have a smooth magnification experience again!

---

### Post by RKCole on 2011-05-27
For anyone else experiencing this problem (assuming you have Compiz Config Settings Manager (CCSM) installed on your system), just do the following:

1. Open up CCSM.

2. Go to the **Utility** section (which is an option found on the left-hand pane of the CCSM window).

3. Open the **Mouse position polling** plugin settings page.

4. Set the **Mouse Poll Interval** to a value **less than 10** (I set mine to '1', and it works flawlessly).


If your Enhanced Zoom Plugin is not already enabled, you will have to enable it and manually set the shortcut keys/mouse buttons for the **Zoom In** and **Zoom Out** settings.

**NOTE:** For my system, **Button4** worked for scrolling up/away from me (Zoom In), and **Button5** worked for scrolling down/toward me (Zoom Out).

Special thanks to okmat for pointing me to the solution. I am so glad to have a much better computing experience now.

Take care, everyone.

---

### Post by Raaaaay on 2011-06-24
Thanks RKCole!

---

### Post by RKCole on 2011-06-24
Anytime, Raaaaay; however, the major thanks goes to okmat for posting the solution. :) I just gave the steps to get there. I hope that all is working smoothly for you now.

Take care.

---

### Post by startgame412 on 2011-07-03
Thanks so much for this fix. I was wondering why Enhanced Desktop Zoom was not working smoothly. I'm a legally blind disabled male who needs magnification software to comfortably operate a computer. The Unity desktop is extremely unfriendly to people with visual disabilities. The Orca magnifier is quite buggy and the speech is hit and miss though can be useful. Happy that I came on here to see if this problem was posted which gladly I found that it was. BTW has anyone tried Vinux? Its a distro targeting people with low vision and blindness.

---

### Post by RKCole on 2011-07-03
Hello, startgame412.

I am glad that a solution was found for this problem as well. I, too, am a visually impaired user, and I completely rely on magnification software for any and all computer-related tasks.

I agree with you about how unfriendly Unity is. Unfortunately, the limitations and circumstances of all users are accounted for in the development of new technologies. this is very disheartening, but it is just the way it is. :( I was looking forward to trying out Unity, so I was quite disappointed when I found ti was not usable for me.

As far as Vinux goes, I have not really tried it, but I have heard a lot of good things about it.

In any case, I am glad that you are now more comfortably able to use your system.

Take care, and enjoy your day (morning or evening...depending on where you are).

---

### Post by vondummkopf on 2012-08-16
Unfortunately, the solution doesn't seem to work in Ubuntu 12.04. I can set keys or mouse buttons but nothing happens when I use them. The same thing is outlined here:

[http://ubuntuguide.net/how-to-zoom-desktop-scale-windows-down-in-ubuntu-12-04](http://ubuntuguide.net/how-to-zoom-desktop-scale-windows-down-in-ubuntu-12-04)

But whatever key combination I try, it does nothing.

Any ideas, anyone?

EDIT: Found another accepted solution which doesn't work here: [http://askubuntu.com/questions/36751/how-to-activate-superscroll-to-zoom](http://askubuntu.com/questions/36751/how-to-activate-superscroll-to-zoom)

---

