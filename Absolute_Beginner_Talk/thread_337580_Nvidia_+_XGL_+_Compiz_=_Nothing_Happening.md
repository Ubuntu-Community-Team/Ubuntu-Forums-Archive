---
title: "Nvidia + XGL + Compiz = Nothing Happening"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by XtremeSki2001 on 2007-01-13
I've followed [this guide on installing XL+compiz]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit") after I got my NVIDIA drivers working.

Everything looks OK ... I have Beryl Manager in my top toolbar, I click it and select Emerald Theme Manager and I get a new window with several themes.  I installed subversion and then clicked "Fetch Themes" and got quite a few more themes.

I double-clicked some of the themes, but nothing happens.  I read some troubleshooting guides, but everything looks fine on my system.

Any ideas as to why I can't apply a theme?

---

### Post by XtremeSki2001 on 2007-01-13
Just to add ....none of the effects of compiz/xgl are working either.

---

### Post by Blondie on 2007-01-13
If you click on the emerald icon on the toolbar and bring up the menu make sure you have it set to Beryl rather than Metacity on the option that lets you choose between them (can't remember what it's called precisely, just hover over them all until it comes up with the choice between the two).

---

### Post by Blondie on 2007-01-13
It's "Select Window Manager". See this [pic]("http://photos1.blogger.com/photoInclude/blogger2/2841/4384/1600/beryl-settings.0.png")

Make sure that when you have your mouse over that option that it's set to Beryl and not Metacity. If it's Metacity then change it to Beryl.

---

### Post by XtremeSki2001 on 2007-01-13
> **Blondie said:**
> It's "Select Window Manager". See this [pic]("http://photos1.blogger.com/photoInclude/blogger2/2841/4384/1600/beryl-settings.0.png")

Make sure that when you have your mouse over that option that it's set to Beryl and not Metacity. If it's Metacity then change it to Beryl.

Gotcha.  I clicked Beryl and the screen flickers a few times, but it remains in its present state.   Currently, compiz is selected.

---

### Post by XtremeSki2001 on 2007-01-13
OK, I'm a bit confused on some posts I've been reading today.

I've read in some posts that Compiz and Beryl don't work together, yet on the [guide I followed]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit"), Beryl/XGL/Compiz is installed.

I've also read that AIXLX won't work with NVIDIA cards, but in other places I read it will work.

All I'm trying to do is get kiba-dock installed and get the other visual effects created by Beryl.

So far I have:

Ubuntu 6.06
Compiz
kiba-dock (but it errors out because of some Segmentation Fault)
XGL

Any help at this point would be greatly appreciated.  I'm definitely doing something wrong.

---

### Post by matrooswolf on 2007-01-13
Hi, 
I think the wiki you are using is outdated.

You can find more information about Beryl here:
[http://www.beryl-project.org/](http://www.beryl-project.org/)

In their wiki [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu) you can find install instructions, but Beryl is no longer supported on Dapper it seems, and using XGL is discouraged ...

In case you're planning to uprgrade to Edgy anyway, I would do that first and then try the AIGLX install of Beryl.

Good Luck!

---

### Post by XtremeSki2001 on 2007-01-13
> **matrooswolf said:**
> Hi, 
I think the wiki you are using is outdated.

You can find more information about Beryl here:
[http://www.beryl-project.org/](http://www.beryl-project.org/)

In their wiki [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu) you can find install instructions, but Beryl is no longer supported on Dapper it seems, and using XGL is discouraged ...

In case you're planning to uprgrade to Edgy anyway, I would do that first and then try the AIGLX install of Beryl.

Good Luck!

Stupid question, but is it easier to just reformat and do an Edgy install ... or is this upgrade tasks not too hard.

---

### Post by matrooswolf on 2007-01-13
Hi, 
I haven't upgraded yet myself, due to all the problems people report.  And I have no time to sort out all the problems yet.
If you can do a clean install, I suppose you will have a smoother ride ...

(But if you're planning to do a clean install, you could try the upgrade anyway, you haven't got much to lose.)
to upgrade, see here:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by XtremeSki2001 on 2007-01-13
> **matrooswolf said:**
> Hi, 
I haven't upgraded yet myself, due to all the problems people report.  And I have no time to sort out all the problems yet.
If you can do a clean install, I suppose you will have a smoother ride ...

(But if you're planning to do a clean install, you could try the upgrade anyway, you haven't got much to lose.)
to upgrade, see here:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Thanks bud ... I don't have too much time sorting out the problems either :) 

Currently on XP downloading Edgy ...

Hoping to finally tackle Kiba-Dock, Beryl, and finally AIGLX for NVIDIA :D

---

### Post by matrooswolf on 2007-01-13
Good Luck!

---

### Post by XtremeSki2001 on 2007-01-14
Good News!

Reformatted to Edgy ... love it, much better then Dapper, IMHO.

I've installed the beta NVIDIA drivers and AIGLX + Berly and all is working .. fairly well.

^^^ [followed this guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") ... it was flawless ^^^

When I type:

```
emerald --replace
```

The emerald theme starts, but as soon as I close the terminal window, the theme disappears.  It's as if the command doesn't finish:

```
erich@erich-desktop:~$ emerald --replace


```

See what I mean ... it never goes back to the prompt.

Any ideas?

Next project ... installing kiba-dock!

---

### Post by matrooswolf on 2007-01-19
I think you only need 
```
beryl-manager
```
and then you get a beryl icon, and you can choose your window decorator (emerald) from the drop down menu ...
(anyway, that's how it works with me)

Good luck with Kiba dock, it's fun, but I didn't really found a use for it

---

