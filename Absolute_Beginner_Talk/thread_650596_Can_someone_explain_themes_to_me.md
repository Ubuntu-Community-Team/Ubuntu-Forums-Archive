---
title: "Can someone explain themes to me?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by sd_smoker on 2007-12-26
I recently set up my desktop with Ubuntu Gutsy. I've got it more or less where I want it functionally so I figured I'd start on the eye candy. I was quickly overwhelmed by all the options and I realized I need some sort of primer on customizing. Is there anything like that out there? Most of the stuff I find assumes a certainly level of understanding that I apparently lack. Here are but a few of my questions if anyone wants to take a stab at them:

- My onboard video card will not allow me to use Compiz (i.e. tells me it's unable to use any desktop effects when I attempt to enable them from the Appearance menu). What limits does that place on me?
- What is the relationship between GTK, Compiz, Metacity, gnome-art, various types of themes (see the menu at gnome-look.org, for example)? I know that's a pretty broad question, but it would help if I had a high-level view of how all these things interact...
- I installed gnome-art. How come when I select a theme the active window title bar retains the color from the previous theme I was using?

---

### Post by overdrank on 2007-12-26
> **sd_smoker said:**
> I recently set up my desktop with Ubuntu Gutsy. I've got it more or less where I want it functionally so I figured I'd start on the eye candy. I was quickly overwhelmed by all the options and I realized I need some sort of primer on customizing. Is there anything like that out there? Most of the stuff I find assumes a certainly level of understanding that I apparently lack. Here are but a few of my questions if anyone wants to take a stab at them:

- What's the difference between all the options at gnome-look.org? GTK2.x? Metacity? GDM Themes? 
- I installed gnome-art. How come when I select a theme the active window title bar retains the color from the previous theme I was using?
- My onboard video card will not allow me to use Compiz (i.e. tells me it's unable to use any desktop effects when I attempt to enable them from the Appearance menu). What limits does that place on me?

HI and this thread has some good info
[http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093)
And what is the onboard graphics on your system?

---

### Post by sd_smoker on 2007-12-26
Sorry, I was in the middle of rewriting my questions when you answered, so they're a bit different now.

To answer the question, it's a S3 ProSavage DDR. Don't know any more details since I'm at work at the moment...

---

### Post by spiderbatdad on 2007-12-26
you may be able to use compiz depending on your graphics card, you may just need to add a composite driver from synaptic if you post the output of ```
sudo lshw -C Video
```  someone could probably adivise you there. Gnome-look.org is a good site for eye-candy too. Themes are placed, as tar packages into Appearance-->Theme via the install button, or simply dropping into the window. Usplash themes, which are really cool, are untarred into /usr/share/gdm/themes

---

### Post by Ub1476 on 2007-12-26
When you're home at your Ubuntu comp, post the output of:

```
lspci | grep VGA

compiz --replace
```

For the gnome-look menu, just click on them and you'll pretty much see what they represent. However, you should use GTK2 instead of GTK1 (it's about Gnome (desktop envirement) version).

I suggest you check out "latest" and "highest rated", cause those are quite sure to work with Gnome 2.20 (which ships with Ubuntu 7.10).

---

### Post by sd_smoker on 2007-12-26
> **spiderbatdad]you may be able to use compiz depending on your graphics card, you may just need to add a composite driver from synaptic if you post the output of

```
sudo lshw -C Video
```[/QUOTE]

Will do as soon as I'm at home...

[QUOTE=Ub1476 said:**
> When you're home at your Ubuntu comp, post the output of:

```
lspci | grep VGA

compiz --replace
```


I'll do that as soon as I get home as well. Just to clarify, do I run these as two separate commands?

[QUOTE=Ub1476]
For the gnome-look menu, just click on them and you'll pretty much see what they represent. However, you should use GTK2 instead of GTK1 (it's about Gnome (desktop envirement) version).

I suggest you check out "latest" and "highest rated", cause those are quite sure to work with Gnome 2.20 (which ships with Ubuntu 7.10).[/QUOTE]

Thanks. So are Metacity themes a subset of GTK2.x themes or do GTK2.x themes not change app window appearances? It would appear that they do, so what's the purpose of Metacity themes?

---

### Post by sd_smoker on 2007-12-26
For what it's worth, I found this thread ([http://ubuntuforums.org/showthread.php?t=621884](http://ubuntuforums.org/showthread.php?t=621884)) that indicates that my graphics chip cannot handle Compiz. I can still run those commands when I get home, but I can't imagine they'll indicate anything different.

---

