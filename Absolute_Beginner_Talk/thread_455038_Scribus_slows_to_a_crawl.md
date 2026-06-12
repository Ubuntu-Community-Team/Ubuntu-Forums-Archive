---
title: "Scribus slows to a crawl"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-26
I am fairly new to Ubuntu, very new to Scribus.  I've been looking for an alternative to Pagemaker/Indesign since loading 7.04 Feisty onto my machine.

For fun, I started a new doc in Scribus and just picked up a magazine and started typing - to see if I could duplicate the layout, fonts, styles, etc from the magazine.

I did not get through the first page of text (first page on my computer screeen) before my typing speed far exceeded my computer's ability to keep pace.

This evoked memories of my early computing/DTP days - working with Springboard Publisher on an Apple IIC or Express Publisher on my PC Clone Swan 210 - where lack of RAM and CPU speed would allow you to get so far ahead of the computer that, sometimes it might forget or lose some of what you typed.

It's not that bad with Scribus, but, it's pretty bad.  I'll look up at the screen and see that the computer is three or four lines of text behind.

I am running on a Shuttle XPC with a Pentium 4-3.0 GHz processor with 2 MB of RAM.  I can run Pagemaker 7.0 via Crossover with none of this sluggishness, so, I do not believe the problem to be my lack of hardware resources.  Obviously, the fault does not lie within the Scribus software, itself, or I would have seen similar comments concerning the software in abundance.

So, I must have some configuration error as regards this application.

Can someone help me?


Thanks.

Caruso

---

### Post by freakboysystem on 2007-05-26
firstly just go through all settings that you can find in scribus if that doesn't do jack try my second guess 
secondly probably try and uninstall and install scribus again, porbably when installing you should have paid better attention (no one really reads through the install programs) but do it anyway

---

### Post by carusoswi on 2007-05-26
> **freakboysystem said:**
> firstly just go through all settings that you can find in scribus if that doesn't do jack try my second guess 
secondly probably try and uninstall and install scribus again, porbably when installing you should have paid better attention (no one really reads through the install programs) but do it anyway

I should have paid more attention during install?  Install was totall automatic - no choices for me at all.  I have uninstalled/reinstalled several times.  No change in performance.

Must be something else.

Caruso

---

### Post by handylinux on 2007-05-30
Haven't tried it yet, but apparently Scribus has problems running in Ubuntu -- though it works fine in other distros. See [Scribus on Debian GNU/Linux and derivatives]("http://www.scribus.net/index.php?name=Sections&req=viewarticle&artid=4&page=1") and [Getting Scribus on Ubuntu/Kubuntu up and running]("http://wiki.scribus.net/index.php/Getting_Scribus_on_Ubuntu/Kubuntu_up_and_running").

Sure would be nice if the Scribus and Ubuntu teams could get together and fix whatever the problems are.

---

### Post by teknosexual on 2007-05-30
I am running Scribus just fine on Ubuntu/Gnome and my hardware is much less powerful than yours. I've never had more than two pages open on a project though. I don't know how many pages you had going, but if it was a lot perhaps that's what slowed you down? If it wasn't many pages, then I think you might be right about some sort of configuration error. 

If you search Google for "scribus runs slow" you'll see some bug report threads discussing Scribus's behavior with various kernals. The latest release on [scribus.net](http://www.scribus.net/) is 1.3.3.9, not sure if that's the one installed by the repos. There are also some [alternative releases](http://www.scribus.net/index.php?name=Sections&req=viewarticle&artid=4&page=1) you might have a look at. Perhaps one of those would be better suited to your hardware configuration?

You might want to post a bug report over at [bugs.scribus.net](http://bugs.scribus.net/my_view_page.php). I'm sure they could help you get things sorted out.

---

### Post by handylinux on 2007-05-30
> **teknosexual said:**
> The latest release on [scribus.net](http://www.scribus.net/) is 1.3.3.9, not sure if that's the one installed by the repos.

Actually, [v.1.3.4 has just been released]("http://www.scribus.net/index.php?name=News&file=article&sid=143"), though it hasn't been posted on the Downloads page yet (neither was 1.3.3.9; the Scribus site unfortunately is not well maintained). And no, apparently some repositories (especially the *buntus) don't have the latest version. See the Debian/Ubuntu page linked above for more information.

---

