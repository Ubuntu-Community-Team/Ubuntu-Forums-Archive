---
title: "Toshiba Satellite A135-S4677"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by roscohoworiginal on 2008-03-15
Hello.

I just switched from Vista and I'm very happy with Ubuntu-- except that I can't hear any sound. When I click on sound control i get error messages that say :
> No volume control GStreamer plugins and/or devices found.
and
> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
I tried searching on google and in this forum, but any proposed solution was beyond my capability to understand. Any kind souls willing to help me out?

---

### Post by LeoSolaris on 2008-03-15
Alright, I have a funky sound card on my Dell Insperion 1520.

Go to your system menu then Administration. Look down it till ya get to Software Sources. On the page that pops up, chuck everything but source code. (you may add that later once you get to the level of compiling from source) Next, the tabs at the top of Software Sources has an 'Updates" tab. Go there. Select them all. Then close.

Go to system again and Admin. This time head to Update Manager. Check for updates. You should have a bunch. Download and install them. The backport updates have an upgrade so to speak for some flaky soundcards like mine.

If that does not work, you're headed back to Sys->Admin, then to Synaptic. (Synaptic is like the Add/Remove but it has a lot more technical stuff in it) At the top is a search button. Click it and search for 'gstreamer' Check all of the plugins for gstreamer0.10 stuff, atleast that is what is the latest in my Synaptic. Select all of the ones you think apply, but make sure you select the Alsa if it is not already checked. You may need some of the 'bad' set as well.

Thats about all the realy help I can give. I know where they are and how to get them, but without knowing what soundcard you have, I can only give you that rough advice.

Best thing to do if you want to test them out is do it one at a time. (You do not need the ones marked develpoers, or usually the ones that only contain documents.)

Happy hunting and hopefully someone else has more knowledge about the subject than I do. I can only tell you what worked on my laptop.

Leo

---

### Post by roscohoworiginal on 2008-03-15
Thanks for the help. It didn't work, but at least now I know how to use Synaptic and that's a good thing. Is there anybody out there who might have more advice on how to fix this?

---

