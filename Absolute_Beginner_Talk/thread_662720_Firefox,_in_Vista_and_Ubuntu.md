---
title: "Firefox, in Vista and Ubuntu"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by KIDRoach on 2008-01-09
Hi, I'm pretty new to LInux, Ubuntu, and of course, this forum itself.:)

I'm currently dual booting Vista and Ubuntu.

I have a problem with my Firefox browser. When I was using Vista, the browser would automatically block all the advertisements, without me ever needing to configure anything. Now that I've changed to Ubuntu, and that the default browser is firefox, there are a couple of things that changed for me.

In Ubuntu, the advertisements aren't blocked by firefox. Somehow, the firefox missed it. When I go to this forum [I'm not trying to promote this forum or anything, but it's the only site that I can think of right now.], there are all kinds of ads in it. However, when I use firefox in vista, all the ads are gone.

Whenever I clicked on the address bar, or the search bar in firefox, it doesn't automatically block all the characters. Any ideas on how to configure this? It did this in Vista, same browser, so I thought there might be a setting to configure this.

I didn't know if this is a problem with Ubuntu, or the firefox itself. I'm so sorry if I posted in the wrong section :(

Thanks

---

### Post by Pevichaey5 on 2008-01-09
there is a plugin for firefox called adblock i use all of the adblock plugins for extra protection

---

### Post by PmDematagoda on 2008-01-09
In Ubuntu Firefox go to Edit>Preferences>Content and make sure that the check box for pop-ups is enabled, you may also get [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865") from the Firefox web site.

---

### Post by aeiah on 2008-01-09
the 'blocking of all characters' thing, as i understand it, is the select all thing that windows does with things like the address and search bars. in ubuntu you'll have to double or tripple click (i cant remember which).

as for advert blocking, perhaps you have an antivirus program in vista that does this for you? in firefox in ubuntu, i use the firefox addon 'adblock plus'. i also use flashblock to block flash which i fnid useful (it only plays flash if you click inside the play icon that replaces the normal flash animation/video. good for loading loads of youtube vids).

---

### Post by asmoore82 on 2008-01-09
The ads thing sounds like you need the AdBlock Plus Add-On.

as for the blocking text thing: even though Firefox is the same program across all
platforms, it does have slightly different default settings in hopes to be more familiar
to native users or blend in with their environment ...

**To change this particular behavior:**
type "about:config" into the address bar;
then, type "urlbar" in the "Filter" field;
and, change the key **browser.urlbar.clickSelectsAll** to **true**.

Firefox will have to be restarted for this change to take effect.

---

### Post by KIDRoach on 2008-01-09
^Thanks, that works very well.

As for the advertisement blocking, I did indeed have an Internet Security program [Kaspersky] that was installed in the computer, in Vista, and not in Ubuntu [I think it's incompatible and I heard you don't need an antivirus in Linux]

I'll try the adblock add-ons in Firefox though. Thanks so much !!! This really helps a lot !!

---

### Post by chadridesabike on 2008-01-09
One thing to remember about firefox is that no antivirus programs currently work with firefox.  so in vista, you might, unfourtunately, be better off with i.e.

---

