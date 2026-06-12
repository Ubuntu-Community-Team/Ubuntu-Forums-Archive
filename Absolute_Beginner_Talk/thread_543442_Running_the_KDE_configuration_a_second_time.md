---
title: "Running the KDE configuration a second time"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Aishiko on 2007-09-05
OK I was trying out KDE but didn't like the set up I tried first and wanted to try a different theme (you know Gnome, KDE, Win, and OSX) but I can't seem to find the wizard.  Can anyone help me find it?

---

### Post by wieman01 on 2007-09-05
The quickest way is still through the Control Center... type this in a terminal:
> kcontrol
That let's you configure KDE as you please.

---

### Post by Aishiko on 2007-09-05
> **wieman01 said:**
> The quickest way is still through the Control Center... type this in a terminal:

That let's you configure KDE as you please.
ohh OK I'll give it a try.  Thank you.

Ideally, I'd like to learn how to modify the look and feel of both KDE and Gnome.

---

### Post by wieman01 on 2007-09-05
Aeh... Gnome, KDE, etc. aren't exactly themes, but Desktop environments. I misunderstood your question. The point is that you have to install all DE's first and customize them separately. You choose the corresponding DE before you log on to your system via GDM or KDM, you know.

Anyway, hope this helps. If you have any other questions, simply post here. :-)

---

### Post by Aishiko on 2007-09-05
Ohh I know they are Desktop environments, but KDE had a thing to let you chosse to have it feel like one of 4 OSes and when it said I could run the wizard again to change the feel if I didn't like the first choice and I didn't or rather I wanted to try a second one.  I may just have to do an uninstall of KDE-Core and then reinstall it.  ButI'd like to avoid wasting bandwidth like that.

---

### Post by wieman01 on 2007-09-06
> **Aishiko said:**
> Ohh I know they are Desktop environments, but KDE had a thing to let you chosse to have it feel like one of 4 OSes and when it said I could run the wizard again to change the feel if I didn't like the first choice and I didn't or rather I wanted to try a second one.  I may just have to do an uninstall of KDE-Core and then reinstall it.  ButI'd like to avoid wasting bandwidth like that.
Reinstalling KDE won't do any good because the settings remain in your home folder ("~/.kde"). That said what exactly do you want to change in KDE? Perhaps we can give you a hand. KDE is confusing in the beginning but I got to like it very much in the end. I only use KDE these days.

---

### Post by Aishiko on 2007-09-06
Ohhh it comes with choses of OSes it will work like and after finding KDE setting works like Knoppix, I figured I'd try the Windows setting soooo I think I'll go and delete the .kde and I think that might force it to run the wizard again. if it doesn't work well, I'll think of something.

I basicly just wanted to see what the different default envirnoments looked and worked like.

---

### Post by wieman01 on 2007-09-06
> **Aishiko said:**
> Ohhh it comes with choses of OSes it will work like and after finding KDE setting works like Knoppix, I figured I'd try the Windows setting soooo I think I'll go and delete the .kde and I think that might force it to run the wizard again. if it doesn't work well, I'll think of something.

I basicly just wanted to see what the different default envirnoments looked and worked like.
Don't delete the folder (.kde) if you still plan to run KDE. Only delete it when you want to reinstall anyway. :-) Otherwise you might run into trouble...

Post here if you have more questions relating to customization. I have gone through a long process of customizing my system as well. I know how painful it can be.

---

### Post by Aishiko on 2007-09-06
Too late, learned the hard way.

and I could not restore the files, at least all I lost were the configuration settings for Kaffiene.  Now if I can get konquere to load up with a collapsable filesystem, like in explorer (what can I say it's easy to move files about if you only have to deal with 1 window instead of 2+.

When I figure out what I want to modified I'll take you up on that offer, but until then I need to see what I want/need changed.

---

### Post by funpop on 2007-09-06
i think you wanted to run kpersonalizer again
just hit alt +f2 and type "kpersonalizer"

if this doesnt work you need to install it first: sudo aptitude install kpersonalizer

thats the wizard where you can choose the behaviour of kde among some other things.

note: all this settings can also made in "kcontrol" or "systemsettings"

---

