---
title: "Youtube Freezing"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by tajmahall on 2007-12-22
I'm unable to get Youtube videos to play correctly. They start playing, then freeze after about 2 seconds. They continue to buffer, and if I click to some later point in the video or back to the beginning I get another 2 seconds out of it before it freezes again. When I look at videos through idesktop.tv, I get the same issue, except I can get 5 seconds out of them. 

Navigating to this:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507)

seems to confirm that I have Flash correctly installed (version 9,0,115,0). I've tried uninstalling and reinstalling both Flash and Firefox several times. I forget where but in another thread I found a link to an archive of older versions of Flash, so I also tried 9,0,48,0, to the same end.
 
I have no idea whether it's related but I'm also having general sound issues. In another thread (again, can't seem to find it now) I found a fix, which seemed to work. It involved looking up the driver for my sound card, deleting a lot of stuff, reinstalling said stuff, and rebooting. Sound worked on reboot, but now has failed again (as I sit tinkering with Flash). 

The Youtube problem isn't entirely consistent. Ironically enough, this is the one Youtube video I've found that seems to play correctly (someone explaining how to use Synaptic to upgrade to Firefox 3 ...):

[http://www.youtube.com/watch?v=pIpne4cc3Hk&feature=related](http://www.youtube.com/watch?v=pIpne4cc3Hk&feature=related)

Sadly, I did try using Firefox 3 and no luck. =(

Any suggestions?

---

### Post by JEMHillcrest on 2007-12-22
did you download the plugin flash
if so, then mabye ubuntu thinks you bandwith is very low, so it loads it slowly
if this is the case.......well, i have no idea what to do then

---

### Post by tajmahall on 2007-12-22
Yep, I've installed the flash plugin in several different ways. 

Is there any way I could tell if it's an Ubuntu problem?

---

### Post by detroit/zero on 2008-01-04
I've found that the freeze problem is consistent from Feisty to Gutsy, happens in regular Firefox, SwiftFox, and IceWeasel browsers - and happens whenever any page using Flash is loaded; YouTube, Google Vid, MetaCafe, etc, etc.

I've tried un- and re-installing *everything*, individually and all at once. No luck.

---

### Post by synss on 2008-01-04
I have the exact same problem, adding (unsurprisingly) Epiphany to the list of affected browsers. So, at least, you are not alone. I did not do anything fancy on my install either and it used to work some time ago on edgy, at least. That is to the best of my memories, I cannot say when it has stopped working either as my main computer is not running linux.

---

### Post by RSLxH on 2008-01-04
Why not install Gnash instead of Flash.

---

### Post by Nunu on 2008-01-04
> **RSLxH said:**
> Why not install Gnash instead of Flash.

Works like a charm for me :)

---

### Post by detroit/zero on 2008-01-05
> **RSLxH said:**
> Why not install Gnash instead of Flash.

Still freezing after a complete removal of all things Adobe and installing Gnash, although - admittedly - not nearly as bad; I can actually watch some or all of a video before it crashes. Closing a page with a flash object is what causes the crash most of the time, but sometimes just opening a page with a flash object does it too.

---

### Post by sleepingdragon on 2008-01-05
I found I had similar problems in FF2 and Epiphany. I switched over to Opera 9.5 (currently in beta), and that seems to work a lot better. The BBC iPlayer was a nightmare in FF. You can find the Linux beta version [[COLOR="#777777"]at this page here[/COLOR]]("http://www.opera.com/download/?ver=9.50b")

Note this is a *beta* version, so it might be a little quirky and could have unpredictable results on your system, but so far I have found it to be working well.

---

### Post by detroit/zero on 2008-01-05
I don't think this is so much a problem with FF or even Ubuntu as much as it is a problem with Adobe's software. 

Sure, I'm now using Gnash, but it's probably safe to say that places like YouTube, MetaCafe, Google Vid, and such all use official licensed versions of Adobe software for their .sfv serving setups.

The problem is too spread out for it to be localized to any one or two things on our ends of the connection. I've seen it first hand on two different freshly installed OSs (Feisty & Gutsy) across three different browsers (Firefox Original, SwiftFox, and IceWeasel), and a variety of plugins to access this content. Granted, all three browsers are technically the same basic thing, but I have a feeling that the problem lies in the fact that Adobe over-engineers everything into a convoluted, bloated mess. Just look at Adobe reader and the resources needed to run it as compared to something like ePDF or Foxit.

---

### Post by esva on 2008-01-05
I can't see the videos normally in firefox, but in opera 9.50 I can very smoothly.
I first insisted on the firefox thing but by now I'm used to opera, so what gives!

---

### Post by detroit/zero on 2008-01-06
I can't get any flash content to play in Opera. I checked the installed plugins and it uses all the same ones that are already there for Mozilla.

Maybe a connection? I'm about to uninstall and reinstall plugins one at a time to see if any of them affect Opera.

---

### Post by tajmahall on 2008-01-28
> **esva said:**
> I can't see the videos normally in firefox, but in opera 9.50 I can very smoothly.
I first insisted on the firefox thing but by now I'm used to opera, so what gives!

Opera doesn't seem to solve it for me either. =(

---

### Post by steve8track on 2008-03-26
I think it's an xorg.conf problem.  I commented out:

```
	Option 		"RenderAccel" 	"True"

```
from the device section, and I added to the screen section:

```
	Option         "AddARGBGLXVisuals" "true"
	Option         "DisableGLXRootClipping" "true"
```

I think it probably has more to do with the RenderAccel option.

I hope that works for some of you.

---

### Post by stchman on 2008-03-26
The flash 9 plugin for Linux has bugs.  Adobe knows about them and refuses to fix them.  They don't care.

---

### Post by dimeotane on 2008-03-27
It must be a problem with a new version of something, because I've been playing youtube videos for years with no problem, then suddenly last I went to youtube, nothing will play... but for a second or two.   Uninstalling flash now and will try the other, gnash.  

Nope still freezes a few seconds in.  

Is the problem with the new version of mozilla?  Or is it with my xorg.conf as a previous poster suggests.

---

### Post by steve8track on 2008-03-29
Hmm, I was wrong, it froze after changing my xorg.conf.  Sorry.

I did read somewhere else that Realtek audio doesn't get along with flash.  Does anyone else have a  Realtek soundcard?

I wonder if I should just install the older version of flash...  How do you get youtube to recognize gnash? Youtube doesn't seem to recognize it and says I need to install flash.  I already installed the gnash firefox plugin from the repositories.

---

### Post by tombott on 2008-04-01
I am now getting this on Gutsy 7.10.
I did a fresh install 2 weeks ago, and it worked for a while, but now all YouTube videos freeze on 2 seconds.
Google Video however works without any problems.

---

### Post by detroit/zero on 2008-04-01
> **steve8track said:**
> I did read somewhere else that Realtek audio doesn't get along with flash.  Does anyone else have a  Realtek soundcard?

I also have Realtek sound.

We could be on to something here..

---

### Post by tajmahall on 2008-04-03
I have an Intel ICH6 AC'97 series soundcard (which is also giving me issues). I feel like that may well be the problem given that at one point I had sound every time I rebooted, and would lose it after navigating to any video site.

---

### Post by steve8track on 2008-04-06
I also have my audio break now and then.  For example, amarok will give me an error where I can choose to disable sound or try again.

---

### Post by Crafty Kisses on 2008-04-06
Not sure, it could be a possible resource issue, post the following output:
```
top
```

---

### Post by tajmahall on 2008-04-18
I've basically confirmed that (for me) this is a sound card issue. I uninstalled everything to do with alsa and then movies began to play fine (with no sound). Still working on the sound ...

---

### Post by sojusnik on 2008-06-06
Same annyoing problem here. Using 64-bit Hardy.

Any idea how to fix?

Hardware specs: [http://www.box.net/shared/d0rfuonkck](http://www.box.net/shared/d0rfuonkck)

---

### Post by detroit/zero on 2008-06-06
I followed the instructions in this tutorial at [UbuntuUnleashed]("http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html") and I no longer have problems.

Make sure you check the comments section, too, and look for info relevant to you.

---

### Post by sojusnik on 2008-06-06
Superb! Thank you!

Installing "libflashsupport" via synaptic solved the problem.

Any idea how I can get this video to run properly on 64bit Hardy?

I always get:
> Connection failed: Try rtmp://[server-ip-address]/fastplay

Link to video: [http://www.secret.tv/player_popup.php?id=4946469&movieid=4946478](http://www.secret.tv/player_popup.php?id=4946469&movieid=4946478)

---

