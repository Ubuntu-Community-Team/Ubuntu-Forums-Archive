---
title: "Longtime XFCE User New to KDE/Netrunner"
date: 2013-10-25
forum: Any Other OS
---

### Post by vtpoet2 on 2013-10-25
I just installed the latest Netrunner. 

It's the version of Kubuntu that appealed to me the most.  I have some questions:  

**1.)** It looks as though it's not possible to shade the window using the mouse scrollbar? 
**2.)** The KDE weather widgets seem very limited. On XFCE, the new/latest weather plugin app gives one a nice 5 day forecast at the click of a button. I can't find anything like that sophistication on KDE. The weather apps on KDE don't seem to tell me anything more than my living room window? Any suggestions? 
**3.)** The Dictionary Widget on KDE also seems extremely limited. On XFCE, the dictionary applet had the capability to search a number of online dictionaries (including thesauri). This applet is incredibly useful, being a writer; but KDE's Dictionary Widget is extremely basic, providing something that might be useful to a second grader it seems. Any suggestions? This one is at the dealbreaker level. 

 Thanks. :-)

---

### Post by vtpoet2 on 2013-10-25
Solved **2&3** :

#-oInstalled xfce4-panel, then the dictionary and weather applet plugin. Forgot that XFCE is modular.

---

### Post by Toz on 2013-10-25
*Moved to **Other OS/Distro Support***

---

### Post by buzzingrobot on 2013-10-26
Artha is a long-standing dictionary/thesarus tool that can be added as a startup application and will popup to a keystroke, optionally displaying a definition of the currently highlighted word.

---

### Post by neu5eeCh on 2013-10-27
Thanks Buzzing, I thought of that; and tried Artha. I compared Artha and XFCE's Dictionary App. side by side. Artha isn't nearly as good -- especially it's thesaurus. The XFCE app lays it all out, plainly, in text -- all of it on one scrollable page. That's a nice feature. I don't need Artha dividing and subdividing information into tabs and clickable links. I *do* think, lately, that the urge to categorize and sub-categorize certain types of information has gotten out of control.  

As to Netrunner. I'm hooked. I've dabbled in KDE every year for years (including way back in 1999 when it was just a bunch of half-functioning windows), and never liked it. With this release (credit Kubuntu in part) the whole *finally* exceeds the sum of its parts. The DE is finally feeling cohesive. I can even shade the window using the mouse scroll button! Finally!  I'm also liking  KWIN. I've installed it as my window manager in both my Xubuntu installs.  

Now I'm off exploring some of KDE's many configurations.

---

### Post by buzzingrobot on 2013-10-27
And thank's for that.  I'll look at XFCE's dictionary.  My use of Artha has been to define the occasional obscure word. The rest of what it does I don't need.

Agree about KDE.  It's come about as a result of adherence to a design concept and the monthly bugfix releases.

---

### Post by orb9220 on 2013-10-27
> **vtpoet2 said:**
> I just installed the latest Netrunner. 

**2.)** The KDE weather widgets seem very limited. On XFCE, the new/latest weather plugin app gives one a nice 5 day forecast at the click of a button. I can't find anything like that sophistication on KDE. The weather apps on KDE don't seem to tell me anything more than my living room window? Any suggestions? 

 Thanks. :-)

I installed yaWP plasmoid allows you have a popup with 1,3 or 5 day forecast with radar map! :-)
You can add the plasmoid widget on desktop or add to the panel which is my choice.

[[IMG]http://i587.photobucket.com/albums/ss317/orb9220/5_zps16d40a36.jpeg[/IMG]](http://s587.photobucket.com/user/orb9220/media/5_zps16d40a36.jpeg.html)

Right click unlock widgets>Right click Add Widgets>Select Get New Widgets>Download New Widgets.
Popup then search weather to see all or yaWP and click on install. Then can add it to the panel.

---

### Post by neu5eeCh on 2013-10-29
Hey, thanks Buzzing.  I saw that. That widget definitely has the eye-candy-wow factor going for it. It's still not as *informative* as the xfce4-weather-plugin. I can extend the latter to 9 days (I keep it at 7). The temperatures given for each day are night/morning/noon/evening. The only thing the latter doesn't offer is the radar. That's cool. Almost sells it. :-)

---

### Post by neu5eeCh on 2013-10-29
Oh, and *here's* a discovery. 

I had been using Xubuntu on my VAIO laptop (3000 series Radeon) for the last few cycles (ever since Unity) and always had to install the FGLRX drivers to prevent video tearing. Other than that, I had no reason to install the Catalyst drivers. 

I always figured it was the fault of the OpenGL drivers.

Turns out, the problem was the window manager -- XFWM4. KWIN, in KDE, has no problem playing videos without tearing and _with_ OpenGL installed (which is to say: _without_ Catalyst).

---

### Post by lykwydchykyn on 2013-10-29
If you look in the online repository for plasma-widgets, there's a panel dictionary plugin that I wrote *years and years* ago that (as far as I know) still works, and allows you to configure multiple backends and sources.

EDIT: here it is:

[http://kde-look.org/content/show.php/panel-dictionary?content=110707](http://kde-look.org/content/show.php/panel-dictionary?content=110707)

---

