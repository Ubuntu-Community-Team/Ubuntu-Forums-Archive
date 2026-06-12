---
title: "gnome-mag please read before installing"
date: 2006-07-20
forum: Assistive Technology &amp; Accessibility
---

### Post by jasongrieves on 2006-07-20
Hi,

ok so I am not the best at making debs.  Currently we have a libgnome-mag2 package which carries all of the libs of gnome-mag.  Since I don't know how to seperate the two, my .deb installs libs and executable.

This is the newest magnifier, which updates the screen differently.

This means you must issue

sudo dpkg -i --force-overwrite gnome-mag_0.13.0-0ubuntu1_i386.deb

Please note!  If upgrades are done to gnome-mag and libgnome-mag2 you better be sure that both packages are upgraded, becasue ubuntu's magnifier depends on libgnome-mag2.  Do NOT remove this file!!!!

[http://filebox.vt.edu/users/jgrieves/html/gnome-mag_0.13.0-0ubuntu1_i386.deb](http://filebox.vt.edu/users/jgrieves/html/gnome-mag_0.13.0-0ubuntu1_i386.deb)

I personally feel the new way of updating the screen is much better this way, as opposed to the other.  Comments?  There is a bug in gnome bugzilla where the devs are discussing if you want to add your input.

If you install PLEASE review my guide for full screen magnification and tell me what you think of the review

---

### Post by RKCole on 2006-07-20
I'll give this a try tomorrow.  I'm really anticipating it.

As for the guide you mentioned: where can I find it?  I've never really worked with Full-screen magnification...I've always used a horizontal split with the magnified version docked on the top of the screen.  I also use this configuration (although it was a little tough at first to set up with Gnopernicus) in Ubuntu.  I’m debating on beginning to use full-screen, though.

Thanks for the .deb package.

Take care.

---

### Post by yellowband on 2006-07-20
what is this exactly Jason?  Is it different than the default gnopernicus magnifier you get with Ubuntu 6.06?  

If so, i'll give it a shot as well.  I'm not too keen on putting my ATI drivers back on, since i'm getting better stability from the mesa one.  If it will increase the performance of the magnifier though, i'll consider it.

---

### Post by yellowband on 2006-07-20
hey jason, is there any way to tell what version of gnome-mag we are running?  I tried the deb file you made, but i got some install failure message. something about not having being able to overwrite.  I'm assuming that has to do with the command you posted as well. i tried that command before adn after i installed the deb package, and both times it gave me an error message saying that the file/directory did not exist.

```

darren@darren-laptop:~$ sudo dpkg -i --force-overwrite gnome-mag_0.13.0-0ubuntu1_i386.deb
dpkg: error processing gnome-mag_0.13.0-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gnome-mag_0.13.0-0ubuntu1_i386.deb
darren@darren-laptop:~$

```

---

### Post by jasongrieves on 2006-07-20
> As for the guide you mentioned: where can I find it
[https://wiki.ubuntu.com/Accessibility/Reviews/gnome-mag](https://wiki.ubuntu.com/Accessibility/Reviews/gnome-mag)
Definitely need input

> what is this exactly Jason? 
Sorry!  I keep forgetting not everyone reads all my silly threads :).  This is the newest gnome-mag package.  To me its kinda big to talk about because of the new way it handles updating the screen.  Devs are talking about it also.

> hey jason, is there any way to tell what version of gnome-mag we are running? 
I have not found a way to do this yet without using apt-get/synaptic.  The actual magnifier does not have a --version as far as I know.  could be in the docs?  Perhaps in /share or something...

> i tried that command before adn after i installed the deb package, and both times it gave me an error message saying that the file/directory did not exist.

That message typically means you are not in the directory of the deb.  If you downloaded the default directory is the Desktop so..
```

1) open up a term
2) cd Desktop
3) ls (to make sure the file is there
4) sudo dpkg -i --force-overwrite gnome-mag_0.13.0-0ubuntu1_i386.deb

```

---

### Post by yellowband on 2006-07-20
changing the directory fixed the problem. i'm an idiot.

This updated version does seem a bit smoother, but not to a point where i would feel comfortable relying on it.  For example, as i'm tying this, nothing is being updated in the zoomed windows. It seems to have some refreshing problems.  

I am going to try the fullscreen guide you have posted on e the weekend. i'll let you know how that goes for me.  Thanks for your effort on this.

---

### Post by jasongrieves on 2006-07-20
> **yellowband said:**
> changing the directory fixed the problem. i'm an idiot.

This updated version does seem a bit smoother, but not to a point where i would feel comfortable relying on it.  For example, as i'm tying this, nothing is being updated in the zoomed windows. It seems to have some refreshing problems.  

I am going to try the fullscreen guide you have posted on e the weekend. i'll let you know how that goes for me.  Thanks for your effort on this.

are you talking about in firefox?  Are you sure its the magnifier?  Does the focus go to the top-corner of the screen?  If so this is a firefox bug not a magnifier bug.  The fix for this will come in like 2.0 or 3.0....I thought about bringing in all the accessibility patches for FF and putting them into a stable executable.  I would not replace the firefox package, but you could run it standalone and still get the most accessibility out of it.  However it would likely take up more resources.

---

### Post by RKCole on 2006-07-20
Wow...very nice!

I can definitely see an improvement over the last version of the magnifier.  In Firefox (when not entering informatino into text fields) I can actually see smooth-scrolling in the magnifier as well as the unmagnified portion...which was not the case previously.

I'll test out the full-screen magnification when I have time.  But I must say that I am impressed with the improvements.

---

### Post by RKCole on 2006-07-20
Phew...that was scary (haha).

I followed the guide, but I think I made a type.  It is very difficult for me to go through the xorg.conf file and straighten everything out the way ti is set in the guide.  But the guide is very good and comprehensive.  I wish I would have known about ti when I first started using Ubuntu.

I apparently made a typo or something when making edits to the xorg.conf file as when I restarted the X Server I received a command-line GUI that stated that there were problems.  Luckily I had followed the guide to the word and made a backup xorg.conf file which fixed the problem completely and I'm back up and running.

If that would have been Windows ti would probably have been a reinstall situation...possibly.  I sure love Linux.

jason:  I was wondering (if it would not be of any trouble to you) if you could possibly edit my xorg.conf so that it is done the right way?  If it is too much trouble, please do not feel obligated.  I am working well with split-screen...I just wanted to see if full-screen would work, and how well ti would work on my PC.

I have an integrated Intel 82865G graphics controller with 128MB shared RAM.  My PC has an Intel Pentium 4 (2.8 GHz) processor with 256MB RAM.  Do you think it can work on this machine, or would I need to upgrade my RAM?

Thanks for all of the help/comments.  I'm definitely learning.

Take care.

---

### Post by jasongrieves on 2006-07-20
> **RKCole said:**
> Phew...that was scary (haha).

jason:  I was wondering (if it would not be of any trouble to you) if you could possibly edit my xorg.conf so that it is done the right way?  If it is too much trouble, please do not feel obligated.  I am working well with split-screen...I just wanted to see if full-screen would work, and how well ti would work on my PC.

I have an integrated Intel 82865G graphics controller with 128MB shared RAM.  My PC has an Intel Pentium 4 (2.8 GHz) processor with 256MB RAM.  Do you think it can work on this machine, or would I need to upgrade my RAM?

Take care.

Hi,

I am sorry about not having better instructions!  I am working hard at making the guide as easy to follow as possible.  Send me your xorg file at [email]jasongrieves@hotmail.com[/email], and I should be able to make the necessary changes.  Also do me a huge favor and maybe try to do it one more time, but this time don't actually implement it!  If I can find where you made the mistake, perhaps I can fix it in my guide to make it more clear.  Hopefully after I get all the kinks worked out I can try to shell script this, though  parsing will be a pain.

Mag will work, memory is a little low, so I am not sure How that will affect performance.  The processing power should help.  How well does it work in split screen?  I typically see about 3-10% speed decrease in full screen mode (much more to update)

---

### Post by RKCole on 2006-07-20
Oh, no.  It wasn't your guide at all.  I explained the situation in the e-mail I just sent to you.  Your guide was excellent.  Even before coming to Ubuntu (when we had to use Fedora Core 2 at the college I attend) I was looking for a guide like that but never could find one.  So please do not feel in any way that it was your instructions as they were very well put.

---

### Post by jasongrieves on 2006-07-21
> **RKCole said:**
> Oh, no.  It wasn't your guide at all.  I explained the situation in the e-mail I just sent to you.  Your guide was excellent.  Even before coming to Ubuntu (when we had to use Fedora Core 2 at the college I attend) I was looking for a guide like that but never could find one.  So please do not feel in any way that it was your instructions as they were very well put.

Thanks RKCole!  You foind a big bug in the documentation.  I forgot not to assume everyone would have "Default Screen" as their identifier.  Here is the updated piece

      Find the section “ServerLayout'
         1. Modify the screen line to read 'Screen "YOUR_REAL_MONITOR_NAME" 0 0', Where YOUR_REAL_MONITOR NAME=Identifier found in the original "Monitor" Section. Ususally this is "Default Screen"
         2. Create another screen line which reads 'Screen "ScreenD" RightOf "YOUR_REAL_MONITOR_NAME" '
         3. NOTE: the code below was for My Monitor's Identifier which read "Default Screen"

Screen “Default Screen” 0 0 
Screen  "ScreenD" RightOf "Default Screen" 


Thanks for catching this!  Hope it works now.

---

