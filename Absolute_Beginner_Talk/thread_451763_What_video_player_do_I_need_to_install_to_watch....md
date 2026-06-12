---
title: "What video player do I need to install to watch..."
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-05-22
I sometimes am interested in looking at the news videos on FoxNews. However, I see only a black screen when starting any of the videos. I hear the audio fine. Do you know what I need to install? I've been unsuccessful in figuring out what I need.

Thanks for any assistance you can give,
kh

Edit: This works beautifully. Just be sure and follow the instructions carefully. Follow the link in the first post. You will be installing Greasemonkey and a script.
[http://www.mepislovers.org/forums/showthread.php?t=5511](http://www.mepislovers.org/forums/showthread.php?t=5511)

---

### Post by Ek0nomik on 2007-05-22
Faux News.  :)

Try this, hopefully it will help:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by dr.silly on 2007-05-22
you don't need to install anything just a slight adjstment

hit alt+f2
type gstreamer-properties
in video tab change default output plugin to X Window System (No xv)

---

### Post by kittyhawk63 on 2007-05-22
> **dr.silly said:**
> you don't need to install anything just a slight adjstment
hit alt+f2
type gstreamer-properties
in video tab change default output plugin to X Window System (No xv)

Thanks, but that didn't work.
kh

---

### Post by wormser on 2007-05-22
I am having the same issue the Faux News.  

> **Ek0nomik said:**
> Faux News.  :)

Try this, hopefully it will help:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

It looks like I have everything installed on that link.

> **dr.silly said:**
> you don't need to install anything just a slight adjstment

hit alt+f2
type gstreamer-properties
in video tab change default output plugin to X Window System (No xv)

That solution did not work also.

Any other ideas?

---

### Post by Ek0nomik on 2007-05-22
If he can hear the audio but not the video than he probably needs a codec.

What I linked you to before is all I have installed, (besides Flash), and I can watch videos on Faux.

---

### Post by kittyhawk63 on 2007-05-22
> **Ek0nomik said:**
> If he can hear the audio but not the video than he probably needs a codec.

What I linked you to before is all I have installed, (besides Flash), and I can watch videos on Faux.

I do not have any of the gstreamers files that the link you suggested gave. They do not appear in Synaptic or Add/Remove. Do you know why?
kh
Edit; Eventually I did find a few in Synaptic. Half are missing. None are in Add/Remove.

---

### Post by wormser on 2007-05-22
> **Ek0nomik said:**
> If he can hear the audio but not the video than he probably needs a codec.

What I linked you to before is all I have installed, (besides Flash), and I can watch videos on Faux.

Maybe I am still missing something from gstreamer.  Here is a picture of what is installed.

[IMG]http://zune-downloadz.com/gstreamer_installed.png[/IMG]

---

### Post by kittyhawk63 on 2007-05-22
> **Ek0nomik said:**
> Faux News.  :)
Try this, hopefully it will help:
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

I am in Gnome, Would that make a difference in finding these gstreamer files?

---

### Post by kittyhawk63 on 2007-05-22
> **wormser said:**
> Maybe I am still missing something from gstreamer.  Here is a picture of what is installed.

[IMG]http://zune-downloadz.com/gstreamer_installed.png[/IMG]
Ok. I've checked most of these. I will check the rest. Thanks.

---

### Post by Ek0nomik on 2007-05-22
Do you have the restricted repository enabled?

---

### Post by kittyhawk63 on 2007-05-22
> **Ek0nomik said:**
> Do you have the restricted repository enabled?

Yes, I have all the repositories that come with Feisty enabled.

---

### Post by theicyj on 2007-05-22
Aren't the videos on Fox News flash based?  At least the one I am watching right now is (Hourly Update).  Try installing "libswfdec0.3" from the repos.

---

### Post by kittyhawk63 on 2007-05-22
> **theicyj said:**
> Aren't the videos on Fox News flash based?  At least the one I am watching right now is (Hourly Update).  Try installing "libswfdec0.3" from the repos.

Not sure if they are flash based or not. I will install libswfdec0.3 as you've suggested. Thanks.
kh

---

### Post by wormser on 2007-05-22
> **theicyj said:**
> Aren't the videos on Fox News flash based?  At least the one I am watching right now is (Hourly Update).  Try installing "libswfdec0.3" from the repos.

I installed libswfdec0.3 and it did not help.

Any other sugestions?

---

### Post by kittyhawk63 on 2007-05-22
All gstreamer files installed and all other files suggested have been installed. Still no video. Only a black screen.

---

### Post by theicyj on 2007-05-22
To confirm, the videos you are trying to watch are here: [http://www.foxnews.com/video/index.html]("http://www.foxnews.com/video/index.html")?  If so, I can watch those videos with no problems.  I know I installed the bulk of my codecs using [Automatix]("http://www.getautomatix.com/"), not sure if you have tried that or not.

---

### Post by Ek0nomik on 2007-05-22
You guys restarted Firefox right?

---

### Post by kittyhawk63 on 2007-05-22
> **Ek0nomik said:**
> You guys restarted Firefox right?

Yes, yes, and yes again. Each time I install a new file.
kh

---

### Post by kittyhawk63 on 2007-05-22
> **theicyj said:**
> To confirm, the videos you are trying to watch are here: [http://www.foxnews.com/video/index.html](http://www.foxnews.com/video/index.html)?  If so, I can watch those videos with no problems.  I know I installed the bulk of my codecs using [Automatix]("http://www.getautomatix.com/"), not sure if you have tried that or not.
Tried this link. Same problem.
kh

Edit, Installed everything there is to install for videos in Automatix2. Still no picture.

---

### Post by wormser on 2007-05-22
> **theicyj said:**
> To confirm, the videos you are trying to watch are here: [http://www.foxnews.com/video/index.html]("http://www.foxnews.com/video/index.html")?  If so, I can watch those videos with no problems.  I know I installed the bulk of my codecs using [Automatix]("http://www.getautomatix.com/"), not sure if you have tried that or not.

Yes, when you click on the link for a video another window opens to the Faux News media center.  I just get a black screen.  Everything else is viewable except the video.  I can hear the audio.

Just to make sure we have all the gstreamer packages installed can you go into synaptic, search for gstreamer and sort by installed.  Then post the image.

---

### Post by wormser on 2007-05-22
I fixed it!!!  It is a problem with Flash Player.  I was trying to remove flash, so I went into firefox and put about:plugins as the url.  Found the Flash plugin file name - libflashplayer.so.  Next I backed up the file libflashplayer.so.  Then I removed it and went to Faux News.  The video played.  I was expecting to get a prompt Flash plugin is needed.

The file was located here:

> /home/username/.mozilla/plugins/libflashplayer.so

Back it up, delete it and check Faux News.

Hopefully that does not cause any other problems.

---

### Post by wormser on 2007-05-22
That solution has issues.  Now I cannot see flash sites.  Can somebody who can view the videos on [Fox News]("http://www.foxnews.com/") go about:plugins in Firefox and post the details of Flash Player.

Thank you

---

### Post by macewan on 2007-06-02
Head over to this directory and grab what you need to write your own page. Should still be up through the weekend and everything is there.

[http://www.foxnews.com/video2/](http://www.foxnews.com/video2/)

---

### Post by jimrz on 2007-06-02
> **Ek0nomik said:**
> Faux News.  :)
really,...when did they start doing news?

---

### Post by Shinobi326 on 2007-06-08
The greasemonkey script recommendation in the link below install worked for me and it was a complete snap.

[http://userscripts.org/scripts/show/1371](http://userscripts.org/scripts/show/1371)

---

### Post by kittyhawk63 on 2007-06-08
> **Shinobi326 said:**
> The greasemonkey script recommendation in the link below install worked for me and it was a complete snap.

As the Brits would say, "Hear, hear!" 

GreaseMonkey did it for me as well.
kh

---

### Post by Shinobi326 on 2007-06-08
Also if that Greasemonkey script doesn't do the trick (sometimes Foxnews reverts back to the black screen for some reason after a few videos) then try out this script

[http://userstyles.org/style/show/808](http://userstyles.org/style/show/808)

---

### Post by kittyhawk63 on 2007-06-08
> **Shinobi326 said:**
> Also if that Greasemonkey script doesn't do the trick (sometimes Foxnews reverts back to the black screen for some reason after a few videos) then try out this script

[http://userstyles.org/style/show/808](http://userstyles.org/style/show/808)

That's true Shinobi. I have found that restarting the video will often get the video to display. Sometimes it takes several tries. Has worked so far.
kh

---

