---
title: "Extremely unstable webbrowsers."
date: 2005-07-20
forum: Apple PPC Users
---

### Post by phibxr on 2005-07-20
For some reason every webbrowser installed on my system is very unstable; which includes Firefox, Galeon, Epiphany and Konqueror.

Firefox and Konqueror randomly freezes, while Galeon and Epiphany randomly quits. Has anyone else experienced this under Hoary?

---

### Post by Lord Illidan on 2005-07-20
Mind giving us some more information on your system, your specs, etc? Is your pc a Power Pc?

---

### Post by phibxr on 2005-07-20
[QUOTE=Lord Illidan]Mind giving us some more information on your system, your specs, etc? Is your pc a Power Pc?[/QUOTE]

iMac PPC G4 700MHz, 256 MB RAM, 40GB HDD.

---

### Post by procdan on 2005-07-22
I have the exact same problem. It existed under Warty, as well. I installed Java 1.4.2 to combat it, but to no avail. When I boot into Mac OS X I'm always struck by the stability of the web browsers (though they are slow).

I'm running a Powermac G4 (digital audio 2001) 466Mhz with >1GB ram and plenty of disk space. I usually use GNOME 2.10 (Hoary). I have checked the ram (software checks under OS X) to no avail. Any thoughts/ help would be extremely appreciated.

-Dan

---

### Post by Tommy on 2005-07-22
[QUOTE=procdan]I have the exact same problem. It existed under Warty, as well. I installed Java 1.4.2 to combat it, but to no avail. When I boot into Mac OS X I'm always struck by the stability of the web browsers (though they are slow).
[/QUOTE]

That sounds strange -- I have been impressed with the stability of the Ubuntu installed browsers UNTIL this week's security update to Firefox, and it turns out you can have the update and stability IF you remove all the Firefox extensions.

I have not yet successfully installed Java on PowerPC, so I'm impressed that you got it going. However it also makes me wonder if you're also loading other plugins that may be causing your instability. When my browsers crash it's usually after clicking a link to some sort of media. In my opinion the two options for loading flash under Ubuntu / Debian are a choice between broken and awful. The option available in Ubuntu main (Gstreamer swfdec) at least has the advantage that it doesn't crash my system. Sadly, though, in most cases it simply does nothing....

Anyway, enough of a rant -- is there a particular web site that crashes one or more of your browsers? I can click them from here and report back. I use Firefox most of the time, Konqueror some of the time, and I just had to look to see that I have Mozilla installed but I almost never use it.

---

### Post by Gary Powers on 2005-07-22
[QUOTE=phibxr]For some reason every webbrowser installed on my system is very unstable; which includes Firefox, Galeon, Epiphany and Konqueror.

Firefox and Konqueror randomly freezes, while Galeon and Epiphany randomly quits. Has anyone else experienced this under Hoary?[/QUOTE]

I've been running Ubuntu on four different computers for eight months using Opera, Firefox, Epiphany and Konqueror, though I'm not a heavy user of the two latter browsers.  Not so much as a hiccup!  

Gary

---

### Post by phibxr on 2005-07-22
[QUOTE=Tommy]Anyway, enough of a rant -- is there a particular web site that crashes one or more of your browsers? I can click them from here and report back. I use Firefox most of the time, Konqueror some of the time, and I just had to look to see that I have Mozilla installed but I almost never use it.[/QUOTE]

[http://www.lunarstorm.se](http://www.lunarstorm.se)
[http://www.aftonbladet.se](http://www.aftonbladet.se)
[http://www.expressen.se](http://www.expressen.se)
[http://www.idg.se](http://www.idg.se)

No extensions. By the way, the crashes are not always reproducible. They seem quite random. Sometimes a text-only site crashes the browser.

---

### Post by Tommy on 2005-07-23
[QUOTE=phibxr][http://www.lunarstorm.se](http://www.lunarstorm.se)
[http://www.aftonbladet.se](http://www.aftonbladet.se)
[http://www.expressen.se](http://www.expressen.se)
[http://www.idg.se](http://www.idg.se)

No extensions. By the way, the crashes are not always reproducible. They seem quite random. Sometimes a text-only site crashes the browser.[/QUOTE]

Thank you for the examples -- those are all very "busy" sites with lots of active graphics, so I can see how an unstable setup would fail on those.Some of the pages at [http://www.weather.com/](http://www.weather.com/) and [http://et.tv.yahoo.com/](http://et.tv.yahoo.com/) probably break them, too. (On my computer, the et.tv.yahoo home page takes most of my slow cpu, but it doesn't crash anything.)

By the way, what browser plugins do you have -- look in this directory for instance:

/usr/lib/mozilla/plugins/

I believe Mozilla uses this directly, Firefox and other browsers will symlink to items in that directory. Other browsers will look in other directories too.

BTW I only have the vlc plugin in mine: libvlcplugin.so

---

### Post by procdan on 2005-07-24
[QUOTE=Tommy]Thank you for the examples -- those are all very "busy" sites with lots of active graphics, so I can see how an unstable setup would fail on those.Some of the pages at [http://www.weather.com/](http://www.weather.com/) and [http://et.tv.yahoo.com/](http://et.tv.yahoo.com/) probably break them, too. (On my computer, the et.tv.yahoo home page takes most of my slow cpu, but it doesn't crash anything.)

By the way, what browser plugins do you have -- look in this directory for instance:

/usr/lib/mozilla/plugins/

I believe Mozilla uses this directly, Firefox and other browsers will symlink to items in that directory. Other browsers will look in other directories too.

BTW I only have the vlc plugin in mine: libvlcplugin.so[/QUOTE]

For me, the crashing doesn't appear to consistently happen on particular sites, though they do tend to be 'busy' sites as you describe. I've had the most problems when switching tabs (mouse click) after clicking on a link. These problems don't seem to be dependent on the type of file requested, either (html, php, swf, pl, whatever); however, they consistently do very well on simpler text-only pages.

The difference in my experience with the linux-ppc web browsing experience and the Mac OS X one is that I can do whatever I want to the user interface in mozilla under OSX but if I rush too much in linux, I seems to cause it to bind up irreparably. I could just be misperceiving it, but I think that my problems are really there on the linux side. I *really* prefer using linux, so I don't want to have to focus on OSX, even if in MOL.

I irregularly but consistently have problems with spontaneous crashes in all of the following (gecko and non-gecko):
mozilla-browser
mozilla-firefox
epiphany
galeon
kazehakase
dillo (!)
amaya (rarely used though, as it's less of a web browser than an html-editor)

Should I try to compile one of these myself? To be honest, I'm a noob and scared of compilation (though I have successfully compiled and installed 3-4 versions of MOL modules.) I will try to pull the plugins out of one of the linked gecko browsers (prob firefox) and give it a try, though. I'll report back after that.

Thanks, in advance. -Dan

P.S. Installing Java wasn't nearly as hard as I thought it would be. The Ubuntu wiki was all I needed. I haven't noticed a great deal of benefit, yet, though. So, I can't recommend the hassle just yet. YMMV.

---

### Post by Tommy on 2005-07-25
[QUOTE=procdan]Should I try to compile one of these myself? To be honest, I'm a noob and scared of compilation (though I have successfully compiled and installed 3-4 versions of MOL modules.) I will try to pull the plugins out of one of the linked gecko browsers (prob firefox) and give it a try, though. I'll report back after that.
[/QUOTE]

As you have seen, as long as the source package is done properly, compiling is not a big deal even for a noob, but UNLESS you change some of the compilation options you should end up with EXACTLY the same code supplied by the binary packages you have already loaded. 

(I write that as if I could tell you what options you could change, which I can't. I'm an "experienced noob" myself. I know more than enough to get myself in trouble, but I have been using UNIX and linux since about 1992, and Macs since 1986. My first experience with UNIX required me to know how to compile the kernel on that system, but I sure didn't change any of the compile options then!)

It's of course possible your system or processor needs something to be compiled in, but I doubt it. You can easily check the plugin theory by renaming the plugin directory(ies) and seeing if the browsers' stability changes.... otherwise all I can say is my experience has been much better, though I've gotten very few of the multimedia features or even Java working so that's why I suspect the plugins in your case.

---

### Post by phibxr on 2005-07-26
[QUOTE=Tommy]Thank you for the examples -- those are all very "busy" sites with lots of active graphics, so I can see how an unstable setup would fail on those.Some of the pages at [http://www.weather.com/](http://www.weather.com/) and [http://et.tv.yahoo.com/](http://et.tv.yahoo.com/) probably break them, too. (On my computer, the et.tv.yahoo home page takes most of my slow cpu, but it doesn't crash anything.)

By the way, what browser plugins do you have -- look in this directory for instance:

/usr/lib/mozilla/plugins/

I believe Mozilla uses this directly, Firefox and other browsers will symlink to items in that directory. Other browsers will look in other directories too.

BTW I only have the vlc plugin in mine: libvlcplugin.so[/QUOTE]

Even though the sites are "busy", they all work just perfectly under all browsers I've tried under OSX, and even more so (if possible) under every browser I have access to in Gentoo at my P3 (Galeon, Epiphany, Firefox, Deer Park, Konqueror).

At the present time I'm running OSX, so I'm not able to check which plugins that resides in /usr/lib/mozilla/plugins; but as I haven't installed any plugins manually, there shouldn't be any more than the standard plugins, if there are any.

---

### Post by procdan on 2005-07-26
update...

I rm'd the plugin contents of the plugin folder in /usr/lib/mozilla-firefox (after backing them up), and firefox has become extremely usable. Stability has increased markedly. I miss quite a bit 'content' without the plugins, but I prefer the stability.

To continue the experiment, I'm going to move the plugins (libmozswfdec.so, libvlcplugin.so) back into the above folder to see if the random crashing reappears. I'll let you all know what happens.

I intend to do the same experiments with my other installed gecko browsers, too, but it will take a while.

Thanks for all your help Tommy. Thanks for starting the thread, phibxr.
Enjoy, -Dan

---

### Post by phibxr on 2005-07-27
[QUOTE=procdan]update...

I rm'd the plugin contents of the plugin folder in /usr/lib/mozilla-firefox (after backing them up), and firefox has become extremely usable. Stability has increased markedly. I miss quite a bit 'content' without the plugins, but I prefer the stability.

To continue the experiment, I'm going to move the plugins (libmozswfdec.so, libvlcplugin.so) back into the above folder to see if the random crashing reappears. I'll let you all know what happens.

I intend to do the same experiments with my other installed gecko browsers, too, but it will take a while.

Thanks for all your help Tommy. Thanks for starting the thread, phibxr.
Enjoy, -Dan[/QUOTE]

Actually, I had some plugins installed: libflash-mozplugin.so  libnullplugin.so  libtotem_mozilla.so  libtotem_mozilla.xpt

I moved these to a temporary directory, and for the last hour I haven't experienced any lock up-tendencies. I'd place my bet on libflash-mozplugin.so.

Edit: This seems to have fixed my problems. Epiphany seems stable to the point of absurdity now.

I went ape creating dozens of new tabs and hammering on every clickable object I could find (you'd almost wish that someone was taping the show), and I didn't even experience a slowdown.

---

### Post by RJARRRPCGP on 2005-07-27
[QUOTE=Tommy]Thank you for the examples -- those are all very "busy" sites with lots of active graphics, so I can see how an unstable setup would fail on those.Some of the pages at [http://www.weather.com/](http://www.weather.com/) and [http://et.tv.yahoo.com/](http://et.tv.yahoo.com/) probably break them, too. (On my computer, the et.tv.yahoo home page takes most of my slow cpu, but it doesn't crash anything.)
[/QUOTE]


If the Javascripts make the processor usage jump up and down with a jerky mouse pointer with Weather.com, it appears to be a Firefox 1.0.6 bug!!! Thus it looks like bug report time!!! :mad:

---

### Post by Tommy on 2005-07-27
[QUOTE=RJARRRPCGP]If the Javascripts make the processor usage jump up and down with a jerky mouse pointer with Weather.com, it appears to be a Firefox 1.0.6 bug!!! Thus it looks like bug report time!!! :mad:[/QUOTE]

I haven't seen that yet, but to be honest, there's a lot that doesn't work at Weather.com because they rely on flash and java for a lot of their pages. For checking the weather on this computer, most of the time I go to the NOAA maps at [http://weather.gov/](http://weather.gov/) which in recent years have become much better. (So much better I hear the commercial weather services have complained, even though they themselves mostly rely upon the publicly-produced data from the weather service.)

Anyway, performance is decent without flash and java, except for a few like the entertainment one I mentioned before. (I actually looked for it, figuring if anyone had a busy page it would be one for a celebrity TV show. In practice, if the web site is that slow or busy I just find an alternative that works better.)

In my experience you can sometimes get a little flash to work using the gstreamer plugin. (It's been awhile since I tried it in Debian, and so far I haven't tried it in Ubuntu.) Fewer flash pages work under gstreamer on ppc BUT at least gstreamer's swfdec (flash decoder) does not crash all the time. I believe to make it work in a browser requires a gstreamer browser plugin.

---

