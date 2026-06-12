---
title: "Flash 9's arrival...?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-10-17
Have there been any updates on when flash player 9 beta comes out?

---

### Post by james.gornall on 2006-10-17
Not that I've seen.

Ground to a halt since Adobe takeover.

Tonnes of content I can access at university that I'm wanting to go on at home but cant cause of req = flash9.

](*,)

---

### Post by spyker3292 on 2006-10-17
No flash 9 is coming out soon. I've read stuff

---

### Post by skymt on 2006-10-17
> **james.gornall said:**
> Not that I've seen.

Ground to a halt since Adobe takeover.

Tonnes of content I can access at university that I'm wanting to go on at home but cant cause of req = flash9.

](*,)

Adobe's actually sped up the process. Macromedia is the reason Flash was at a standstill for so long. Expect a beta by the end of the year.

EDIT: For updates, watch [Penguin.SWF](http://blogs.adobe.com/penguin.swf/), the blog of the head Flash/Linux developer.

---

### Post by Sef on 2006-10-17
> Expect a beta by the end of the year.


On the link that you provided, a beta is expected in about 2 weeks (i.e., the end of October.)

---

### Post by etomic13 on 2006-10-17
you can always use it under wine if you cant wait, its a little slow but for most stuff it works 
[http://www.howtoforge.com/ubuntu_flash_player9](http://www.howtoforge.com/ubuntu_flash_player9)

---

### Post by RKCole on 2006-10-17
I missed the Oct. 13 post on the blog.  It looks like things are beginning to fall into place.  I'm looking forward to having a newer version of Flash to use...

---

### Post by TrendyDark on 2006-10-17
I wrote about this on my blog a while back, I'm worried they may give up on us right before the next installment of Flash and just "develop for the newest". Meaning, we may never see a new version of Flash. Although, the developer blog makes me warm and fuzzy, I still hold my doubts. . . Did we ever see Flash 8? 8.5? like promised?

---

### Post by Sef on 2006-10-17
> 8.5? like promised?

Flash 9 is the renamed Flash 8.5, and it is almost in beta testing.

---

### Post by twisted_steel on 2006-10-18
It looks like the beta is out.

[http://blogs.adobe.com/penguin.swf/2006/10/beta_is_live.html](http://blogs.adobe.com/penguin.swf/2006/10/beta_is_live.html)

---

### Post by McQuaid on 2006-10-18
I just tried it and so far not so good.  The games at [http://www.games1.org](http://www.games1.org) aren't working.  As a matter of fact, games that did work with flash7 no longer work.

about:plugins verifies I have 9 installed.

---

### Post by Totzo on 2006-10-18
> **twisted_steel said:**
> It looks like the beta is out.

[http://blogs.adobe.com/penguin.swf/2006/10/beta_is_live.html](http://blogs.adobe.com/penguin.swf/2006/10/beta_is_live.html)

wow, anyone got it working?

---

### Post by skymt on 2006-10-18
> **Totzo said:**
> wow, anyone got it working?

Me. I just listened to a Youtube video while watching another video in Mplayer, just for the fun of it. It mixes perfectly!

---

### Post by Jason_25 on 2006-10-18
> **McQuaid said:**
> I just tried it and so far not so good.  The games at [http://www.games1.org](http://www.games1.org) aren't working.  As a matter of fact, games that did work with flash7 no longer work.

about:plugins verifies I have 9 installed.
I have no trouble with those with the new flash 9 and konqueror.  In fact, all flash I have tried works perfectly.

---

### Post by McQuaid on 2006-10-19
Can anyone else verify that they can/can't play games at [http://www.games1.org/](http://www.games1.org/)

I installed flash by removing the nonfree pkg and simply created a plugins dir in my home .mozilla dir and placed it there.  Youtube works, but not games1.org.  When I right click it says about flash 9 but nothing is there.

How did you install it in konqueror?  I'll try it in that browser to see if there's a difference.

---

### Post by jordanmthomas on 2006-10-19
The games at the site you're listing work for me.
I put my plugin in /usr/lib/firefox/plugins though.

---

### Post by McQuaid on 2006-10-19
Ok, they work for me now.  I figured out the issue but I'm hoping someone can propose a workaround.

I use 'click to flash' which I have in my homes' userContent.css.

By placing the below it will show just a grey box for all flash and you click it if you want to actually see the flash content.

/* Prevent flash animations from playing until you click on them. */
object[classid$=":D27CDB6E-AE6D-11cf-96B8-444553540000"],
object[codebase*="swflash.cab"],
object[type="application/x-shockwave-flash"],
embed[type="application/x-shockwave-flash"],
embed[src$=".swf"]
{ -moz-binding: url("http://www.floppymoose.com/clickToView.xml#ctv"); }


I have used this for ages and really like using this method to block flash, but for some reason, it doesn't work with flash 8/9 content.  Once I removed that flash 9 stuff started working, but there's no way I'm going back to seeing flash content everywhere.  I have no clue how the above works just grabbed it from a site, I'm hoping someone might know a way to adopt it for newer flash content.

Btw, flash has always seemed to be a bit of a resource hog, and I read the new flash uses a lot less cpu resources.  I never did much testing, but one thing I noticed is youtube videos that appear smooth in a window, become choppy with the large window option.  I've always assumed that this is a flash/cpu usage issue, but flash 9 still does this.  Maybe a little smoother, kind of hard to tell.  I've read it could also be a gtk issue.  So I wanted to test the latest flash in konqueror.  I haven't used konq in ages, where do konq plugins go so I can test this?

---

### Post by TooDamFast on 2006-10-19
just a few how-tos
[http://linux.edu.lv/index.php?name=News&file=article&sid=244](http://linux.edu.lv/index.php?name=News&file=article&sid=244)

[http://www.wikitut.org/index.php?title=How_to_Install_the_Flash_9_Plugin_on_Linux](http://www.wikitut.org/index.php?title=How_to_Install_the_Flash_9_Plugin_on_Linux)

yippie, now myspace videos work.

---

### Post by RKCole on 2006-10-20
Has anyone been able to get this working in Edgy beta yet?  I'm not sure if I have it set up incorrectly (I have the plugin in /usr/lib/firefox/plugins), but when I go to a page containing Flash movies or games, Firefox crashes/closes immediately.  This occurs on the Firefox 2.0rc3 which I recently updated to via update-manager.  Removing the plugin sets things back to normal, just that (obviously) no Flash content is displayed.

Has anyone else experienced this same issue?

Thanks and take care.

PS:  It's nice to see something finally coming along with Flash for Linux!

---

### Post by PriceChild on 2006-10-20
I'm fine in Edgy beta...

I removed flashplugin-nonfree then moved the new flash file to the global dir (not my home)

---

### Post by jordanmthomas on 2006-10-20
ditto.  Works fine for me and I didn't even remove the flash-plugin first, I just overwrote it.

...removing it is a good idea so it doesn't get overwritten though.
**goes to remove it

---

### Post by RKCole on 2006-10-20
Still no luck.

I uninstalled my gxine and totem Firefox plugins, thinking that they could have been causing a problem, but to no avail.  I'm not too worried about it, though.  When the final release of Edgy comes out I'm going to do a fresh install as I probably broke something in the beta while I was testing some things.

Hopefully it will work then.

Thanks and take care!

---

