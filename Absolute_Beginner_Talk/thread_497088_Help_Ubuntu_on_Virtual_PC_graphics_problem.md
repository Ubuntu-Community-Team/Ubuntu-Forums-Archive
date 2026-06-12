---
title: "Help Ubuntu on Virtual PC graphics problem"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by marioguy on 2007-07-09
Hello, I don't know if talking about virtual pc is allowed but I have tried to start ubuntu in Virtual PC to try it and it always ends starting but the graphics severely glitched up(my cursor looks like a multicolored finger)  Which resolution should I select and what about safe graphics mode?  I am a super noob when it comes to Linux but my friend convinced me to try it on Virtual PC and I would like some help.

---

### Post by dmfield on 2007-07-10
Never used virtual PC myself, but a quick google brought up this:

[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004)

Which im not use if you used?

I've done this a few times using VMWare server (which is free) and it works fine in there..

Also this site [http://haacked.com/archive/2007/05/06/installing-ubuntu-on-virtual-pc-for-windows-lovers.aspx](http://haacked.com/archive/2007/05/06/installing-ubuntu-on-virtual-pc-for-windows-lovers.aspx)

**The Bit Depth Issue**

 Earlier I mentioned making sure to start Ubuntu in Safe Graphics Mode. The reason for this is that the default bit depth property for Ubuntu is 24, which Virtual PC does not support. If you fail to heed this advice, you&#8217;ll see something like this. Kind of looks like that [All Your Base Are Belong to Us]("http://en.wikipedia.org/wiki/All_your_base_are_belong_to_us") video.
 [IMG]http://haacked.com/images/haacked_com/WindowsLiveWriter/InstallingUbuntuonVirtualPCforWindowsLov_C436/image029.png[/IMG] 
 Fortunately, I found the fix [in this post]("http://weblogs.asp.net/pscott/archive/2005/10/13/427426.aspx") on Phil Scott&#8217;s blog (Phils rule!).I bolded the essential elements.
 [INDENT] Once I was in there, I found the configuration file for the graphics card in /etc/X11. Sso type in **cd /etc/X11**, although I certainly hope even the most harden of MScentric people can figure that out :). Once in there I opened up xorg.conf using pico (so type in **pico xorg.conf** - isn&#8217;t this fun?). Browse down to the screen section. Opps, looks like the **defaultDepth** property is 24, which VirtualPC doesn&#8217;t support. I changed this to 16 and hit CTRL-X to exit (saving when prompted of course). Typed in reboot and awaaaaaaay we go.
[/INDENT] When I ran through these steps, I found that I had to use the sudo command (runs the command as a super user) first. For example:
  sudo pico xorg.conf
 Your results may vary. *Speaking of sudo, *[*have you seen my t-shirt*]("http://www.flickr.com/photo_zoom.gne?id=480589091&size=l")* from *[*XKCD.com*]("http://xkcd.com/")*?*

---

