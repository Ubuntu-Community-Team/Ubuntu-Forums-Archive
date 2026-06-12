---
title: "Open Office toolbars have no icons only text"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by groovomata on 2007-04-23
Hello All,
I install feisty and the Open Office toolbars are all wonky with only text and no icons. I tried to change them in Tools > Customize > Toolbars; but they won't change to an icon view. I wonder if perhaps the icons somehow didn't get installed?
Thanks,
Erik.

---

### Post by mikeyphi on 2007-04-23
Try - under Tools-Options-Open Office-view.....check the show icons in menus box....hope that helps!

---

### Post by groovomata on 2007-04-23
Unfortunately this didn't help... :(
Thanks,
Erik.

---

### Post by groovomata on 2007-04-23
If I cannot get my toolbar icons back in Open Office, perhaps if I deleted it and re-installed it? What would be the best way to do that? Simply remove the programme from 'Add/Remove Applications' and then re-install it? I checked the spreadsheet and presentation applications and none of them display icons. 
Thanks,
Erik.

---

### Post by annda on 2007-04-23
you may need to install/reinstall openoffice.org-gtk and maybe openoffice.org-gnome too.

search synaptic for openoffice. i hope it helps. if not, completely remove oo2 in synaptic and install again.

---

### Post by groovomata on 2007-04-23
I searched 'Open Office' in the Synaptic Package Manager and selected reinstall for everything to do with Open Office. It didn't complain and it's doing it now. I'll post back with the result.
Thanks,
Erik.

---

### Post by groovomata on 2007-04-23
Well I reinstalled everything to do with Open Office in the Synaptic Package Manager. Unfortunately when I launched Open Office Writer, it still has no toolbar icons. However when I went to Tools > Customize > Toolbars tab > there's a selection under the Modify pull down menu to 'Change Icon...'. When I select that Open Office crashes. I suspect that somehow the icon files that are supposed to be included are not included which is why Open Office Writer crashed. 
My question is: does anyone know which package the Open Office icons might be found in?
Thanks, 
Erik.

---

### Post by annda on 2007-04-23
there are a few packages: openoffice.org-style-*

---

### Post by groovomata on 2007-04-23
Okay, I found a posting in the Open Office forum. Apparently it's a problem with feisty that the icons were not included. Read about two thirds down the page to find the icons in Synaptic:
[http://www.oooforum.org/forum/viewtopic.phtml?t=55712&highlight=toolbar+icons](http://www.oooforum.org/forum/viewtopic.phtml?t=55712&highlight=toolbar+icons)

I worked perfectly for me.
Erik.

---

### Post by VictorR on 2007-05-30
I had the same problem with Feisty Fawn. After reading this thread I scanned everything what appeared in Synaptic for "Open Office" and found missing packages at the very bottom of the list. My selected style in OO was Tango which had not been installed. The icons appeared immediately as I installed some styles.

---

### Post by vitalik on 2007-05-30
Ok same problem here. Don't know why was the icons removed from the default installation, bu if you install some styles icons come back. Thanx for the help guys.

---

### Post by pcl on 2007-07-13
Same problem last night, 

I would say same problem output, I know where the source of the problem is tough your source might be a different one...

Open OO.org open the tool-option dialog box (see your previous posts) and from there make sure you have in the view left section "Icons size and style" set to automatic and in the drop down list beside choose "Default" or "Human" the latter works fine with me.

Then you should have your icons back straight away.

Since your post is quite old you might have found a way around... I know that you don't get your icons back by re-installing Oo so it might be interesting to know how you dealt with it.

---

### Post by Drone4four on 2007-08-07
SOLUTION

> I am using Ubuntu 7.04 and I had the same problem with OpenOffice.org 2.2

But I just found out why most of the icons were missing from the tool bar. It is not loaded by default. I am not sure how you do this in Kubuntu Feisty, but do this:

1. Goto Synaptic Package Manager and then "Reload" everything, this will update all the packages.
2. Then Search for "OpenOffice.org" then scroll down to AND check for installation for following packages: "openoffice.org-style-crystal" "openoffice.org-style-default," "openoffice.org-style-human," "openoffice.org-style-industrial," and so forth.
3. Install 

That's a quote from a user, doulos115 on the official OOo forums, here: [http://www.oooforum.org/forum/viewtopic.phtml?t=55712&highlight=toolbar+icons](http://www.oooforum.org/forum/viewtopic.phtml?t=55712&highlight=toolbar+icons)

---

### Post by Afkpuz on 2007-08-24
This will install all the availible icon sets for openoffice.

```


sudo apt-get install openoffice.org-style-andromeda openoffice.org-style-crystal openoffice.org-style-default openoffice.org-style-hicontrast openoffice.org-style-human openoffice.org-style-industrial openoffice.org-style-tango


```


Then make sure to pick whichever set suites your fancy at

Tools->Options->View

---

### Post by dryliketoast on 2007-09-20
OK here is how i fixed mine - much easier than installing/uninstalling.  i hope it works for you too.

goto Tools > Options > OpenOffice > View
and set the interface scale to be around 95% or lower.

this solved it for me. 

I think the real problem here is the font size of the buttons in the menu's - i set mine quite small (in the gnome font options) and noticed all application toolbars lose a few pixels in height. 

therefore i think its possible that the icons are already installed, its just the space available to display them is not enough. hence why scaling everything down worked for me!

---

### Post by octopuskevin on 2007-09-28
just a heads up on this for some people,

my icons also disappeared for some reason until I realized that it seems to be a problem with the GTK theme that I was using. Switching to another [add-on] theme solved this problem.

---

### Post by disraeli on 2007-10-03
That worked for me! I was lacking the Tango icon set, so I ran Synaptic and installed openoffice.org-style-tango. Anyway I think you should rename this topic and put [SOLVED]

---

### Post by jARLAXL on 2007-10-23
faced the same problem when installed gutsy.
but after the update it got fixed.
thanks goes to afkpuz

---

### Post by chudder on 2007-10-27
> **groovomata said:**
> Okay, I found a posting in the Open Office forum. Apparently it's a problem with feisty that the icons were not included. Read about two thirds down the page to find the icons in Synaptic:
[http://www.oooforum.org/forum/viewtopic.phtml?t=55712&highlight=toolbar+icons](http://www.oooforum.org/forum/viewtopic.phtml?t=55712&highlight=toolbar+icons)

I worked perfectly for me.
Erik.

This worked for me too!  I just installed Gutsy and that's when I had problems.  Thanx!

---

### Post by frumple on 2007-12-27
Installing the ooo style packages solved my problem too ;)
Thanks for the tip!

Happy new year to everybody.

---

### Post by evil_cat on 2008-05-11
Thanks for your advice but this one is easier

In OO open Tools>Options>View and select 'Automatic' + 'Human' in "Icon Size and Style". Then click OK.

---

