---
title: "Unable to install flash from add/remove"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Sawta on 2007-10-07
Hello everyone,

I have been running ubuntu 7.04 (Feisty Fawn) on an Intel iMac 24&#8221; with the latest software updates, etc. etc. for two  days now.  It's really pretty, and I've run into very few problems that I haven't been able to fix so far, besides the one that I'm about to talk about.

My problem is that I tried to install macromedia flash.  I originally tried to follow the directions that were listed on adobe.com.   I tried installing all three versions that they had listed, since it made no mention of which version was for which OS (that I could see, at least).  After I failed at following their directions, I deleted them all from my computer and searched for a thread about it on these forums.  Sure enough it was listed in one of the sticky threads ([http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)).  However, when I went to add/remove programs, although I was easily able to get every other package listed in the tutorial, I was unable to check the box for that one (Flash).  No error message, or anything telling me whither I have the program installed or not, it just seems slightly grayed out, as if it doesn't want me to download it.

[http://img.photobucket.com/albums/v497/Sawta/Internet%20Stuff/screenshot1.png](http://img.photobucket.com/albums/v497/Sawta/Internet%20Stuff/screenshot1.png)
[http://img.photobucket.com/albums/v497/Sawta/Internet%20Stuff/screenshot2.png](http://img.photobucket.com/albums/v497/Sawta/Internet%20Stuff/screenshot2.png)

I'm thinking that maybe I had messed up the ability to download flash after I used the terminal the first time around.  I don't remember putting in anything too crazy when I was messing around trying to make it work, but I believe I typed in something into the terminal like, &#8220;sudo install_flash_player_9_linux&#8221; or &#8220;sudo ./flashplayer-installer&#8221;.  I just wanted to see what sudo would do, but when a bunch of odd characters came up, it read something like { -k| -s| -l (etc.)} I exited out of terminal out of fear of really messing something up.

Any ideas on what I might of done and how I could fix this?  Sorry if I'm a bit wordy in this post, I'm just trying to be as descriptive as possible.

Just as an update, I finally got around to installing 7.10.  With a fresh install and using the "install plug-in" firefox method, it seems to be working fine.  If you're having a similar problem and you haven't customized your OS too much by this point, I would just suggest re-installing the whole thing.  Lets you cover up any mistakes you made the first time around anyway. :)

---

### Post by Billy_McBong on 2007-10-07
[COLOR="Blue"]try using Synaptic to install it(system>administration<Synaptic)[/COLOR]

---

### Post by Sawta on 2007-10-07
I tried searching for programs using Synaptic, by searching for Macromedia.  I downloaded gstreamer0.8-swfdec and swf-player.  Restarted Firefox but no luck.  Was I supposed to look for something different?

---

### Post by aysiu on 2007-10-07
Isn't the package called *flashplugin-nonfree*?

You can also do a local install by just visiting a webpage that requires Flash and then following the *Install Missing Plugin* dialogue in Firefox.

More details here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Sawta on 2007-10-07
Hmm, well when I tried searching for that in synaptic, nothing came up, and when I tried to install it form Add/Remove, it came up to the same program that was "locked" or what have you.  I'll try giving the link you listed a look.

Thanks for the suggestion

Oh, and when I try to use the firefox route, this is what comes up.
[http://img.photobucket.com/albums/v497/Sawta/Internet%20Stuff/screenshot3.png](http://img.photobucket.com/albums/v497/Sawta/Internet%20Stuff/screenshot3.png)

---

### Post by aysiu on 2007-10-07
That's weird. You're definitely on an Intel Mac and not PowerPC?

---

### Post by Sawta on 2007-10-07
Hrm, from what I can tell, it is.

Here's a quick screen of my hardware specs.
[http://img.photobucket.com/albums/v497/Sawta/Internet%20Stuff/Picture3.png](http://img.photobucket.com/albums/v497/Sawta/Internet%20Stuff/Picture3.png)

I'm not sure if that's exactly what you were referring to or not, though.  I installed ubuntu 7.04 as a dual boot. Humm, I'm not quite sure if thats referred to as a virtual PC, or if that's when you use something like Parallels to have two OS'es running at the same time or not, but I  suppose that that's besides the point.

I also tried to follow the directions listed in the link you gave me.  All the installations made sense, and *seemed* to work, but when I tried to view a flash video, I kept seeing the same error message asking if I have Javascript active (Which I do) or if I have the latest flash player..which I've seemed to have done.

If I can't get it sorted out, it's not the end of the world, as I still have to get sound up and running as well, but it would be nice to not having to boot into OS X every time I want to view something. :P

---

### Post by Python425 on 2007-10-21
hey guys. I'm brand new to the Linux OS and just installed Gutsy(7.10) and have had almost no problems except for what the topic starter has had, with some slight differences. I have java and javascript enabled but I cannot view pictures on some websites(especially myspace) and cannot stream music from radio station sites. At the top of the firefox window it says "additional plugins required to display all media on this page" but when I click on the install plugins button and click either of the two options(adobe or Gnash) then next, it says that it cannot find the file but also says that the plugin was installed. Even when I restart my computer and restart firefox the images still do not appear. I also ran the adobe install in the terminal which again said that the program was already installed. Any ideas?

---

