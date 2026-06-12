---
title: "No Repositories Tab in Emerald"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by kolisikepu on 2008-03-25
Hi Community,

I thought I'd play around with Ubuntu Hardy and I've noticed that when installing Emerald, I don't have the Repositories tab to fetch themes.

Any idea's??

Here's a screen shot and the other is what it should look like.

---

### Post by Bölvaður on 2008-03-25
what version of emerald do you have?

---

### Post by kpkeerthi on 2008-03-25
> **Bölvaður said:**
> what version of emerald do you have?

I think it is in one of the screenshots attached :)

---

### Post by LowSky on 2008-03-25
I found this 
> **mahiyar said:**
> How to make emerald themes run in Gutsy.
 

 **Basic Requirement--** Should be able to run advance desktop settings in the &#8220;extra&#8221; mode. i.e you should be able to run compiz-fusion. I have Nvidia drivers enabled on my computer and have checked the How-To for the same. I'am not aware of how this behaves with any other driver.[LIST=1]
[*]**Install emerald**: Go to     >System>Administration>Synaptic package Manager and search     for emerald. This package is in the &#8220;Universe&#8221; repositories.      Install the emaerald package (emerald and emerald engine will be     installed). Check for the green ruby icon in your     >System>Preferrences menu.
[*]**Install Emerald themes:** For     the emerald windows decorator there are no themes in the Gutsy     repositories. We have to make use of Fiesty themes, the deb files     can be installed from this link     _[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fe%2Femerald-themes%2Femerald-themes_0.2.1-0ubuntu1_all.deb&md5sum=40b7e970de248d7b04e3aced4f4908fb&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fe%2Femerald-themes%2Femerald-themes_0.2.1-0ubuntu1_all.deb&md5sum=40b7e970de248d7b04e3aced4f4908fb&arch=all&type=main) _[COLOR=#000000]after     downloading you can install this package by using Gebi package     installer. [/COLOR]
[*][COLOR=#000000]**Enable     the Decorator Plug-in: **[/COLOR][COLOR=#000000]System>Preferences>(advance     desktop [/COLOR]effect  settings) , in that window     go to the effects section and see that the windows decorator is     selected.
[*]**Start Emerald:** In the     terminal run this comand >> emerald --replace. Hopefully at     this stage if you are using the advance desktop settings you will     see your emerald frame. You might want to run it at the start, when     you boot your computer. As usual go to     >>Systems>Preferrences>Session, press the add Button and     fill in the lines, Name : Emerald, Command: emerald --replace,     Comment: Emerald window frame. (There is a double dash before     replace.)[/LIST]Thats it, your emerald should be up and running.

---

### Post by Bölvaður on 2008-03-25
> **kpkeerthi said:**
> I think it is in one of the screenshots attached :)

Actually the first screenshot is from him, the second one was added afterwards as an example of how it should look.

So that means that we aren't reading what he's writing and therefore the only thing he has got back is pretty random "help".


kolisikepu, I think you do not have to have any worries of missing this option if you are able to customize the look with some of the popular frame engines like trueglass and oxygen.

---

### Post by kolisikepu on 2008-03-25
Version 0.7.2 and the first screen dump is mine where the repositories tab is not present and no themes are in the window.  The 2nd screendump is what it should look like with the repositories tab and status bar when fetching themes for Emerald.

I just want to know if it has something to do with Hardy or it's just a problem with Emerald.  I still don't have Repositories tab.

---

### Post by kolisikepu on 2008-03-25
> **LowSky said:**
> I found this

The link in that quote you posted is also dead.  Anywhere else I can download the Emerald themes packages without fetching from the Repositories?

---

### Post by krelverehan on 2008-04-28
I am having the same problem too. I found this:

[https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/205364](https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/205364)

I reckon that you have to download the source again, and recompile with the uncommented line.

---

### Post by vjkeito on 2008-04-29
bump. needs fixing in an update?!

---

