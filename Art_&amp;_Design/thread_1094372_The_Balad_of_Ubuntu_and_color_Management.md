---
title: "The Balad of Ubuntu and color Management"
date: 2009-03-12
forum: Art &amp; Design
---

### Post by Gerhardus on 2009-03-12
Ok, so for the past few months I have been continuing my conversion to Linux. I do photography and my big goal was to make sure I could have a real workflow in linux. Color calibration is painful and frustrating and can be the end of all sanity (as many of you know). So this is what I have found. I use Argyllcms, as it is the the only thing I've found to be able to support creation of monitor profiles (and so much more) at the current release state. Using the command line turned out not to be that difficult, after finding a tutorial, one I believe was posted in my previous thread. 

[http://jcornuz.wordpress.com/2007/11/18/use-colorvision-spyder-to-produce-an-icc-monitor-profile-under-argyllcms-linux/](http://jcornuz.wordpress.com/2007/11/18/use-colorvision-spyder-to-produce-an-icc-monitor-profile-under-argyllcms-linux/)

Now as I said in my last thread oh so many months ago, I would prefer to have a gui because it is much easier to get converts and to use myself. I'm not afraid of command line, but in some instances it's easier to click a check box than it is to try and remember or figure out what string of variables one needs to list after a command. I recently found a solution that works very well for setting up a monitor profile with argyll.

[http://hoech.net/dispcalGUI/#screenshots](http://hoech.net/dispcalGUI/#screenshots)

I find the installation to be a cake walk as it has an auto installer and you only need to download the binary files for argyll and point the gui in the right direction on first use.

Now the issues I have been having with my color management in general:
I made my profile and pointed all my software to it. I have a friend of mine who has recently gotten into photography and I sent him links to some of my work once I started posting from my new workflow. The response I got from him was that they were all muddy. So I checked everything it's all set up as I thought it should be, and thus I checked the links on another computer and to my surprise they were muddy. So for days I bounced around trying to get things set up so that the images I was putting out seemed reasonable, which meant disabling color management in some programs, and switching over to srgb instead of adobergb or photorgb which are my preferred workflows (though I know for the web you should use srgb, I prefer printing my work) Now I realize that the whole point of profiling an color management in general was that screens unmanaged won't show you work right, but in reality most people have unmanaged screens, so when it's that far off...it doesn't do you much good. If a potential client thinks your work looks terrible, you can't tell him "oh well you need to color manage your system. Now that being said, when I was running windows I was color managed and there was never that drastic of a difference between images on my monitor and those of an unmanaged screen (I mean, I could see differences, but they were slight and didn't effect the overall vision of the image, just would be a pain to get a perfect print of) So I was wondering if anyone else has this problem and what the causes and solutions could be.

---

### Post by lt_gustavsen on 2009-04-02
It sounds like your friend are viewing your images in a non color managed viewer. What about a link to one of the affected images?

What are your editing workflow?

---

