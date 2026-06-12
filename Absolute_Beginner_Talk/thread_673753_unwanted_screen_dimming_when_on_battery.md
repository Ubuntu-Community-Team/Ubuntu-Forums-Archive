---
title: "unwanted screen dimming when on battery"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by kaston on 2008-01-21
i am running gutsy on a toshiba satellite A100 VA9.  what i want is my screen to remain at full brightness when unplugged, but to dim when idle to save power.  when i set power management to not dim at all on battery (dim by 0%) and check dim when idle, the screen dims when i unplug and doesn't return to full brightness even if i move the mouse.  i can only get the screen to stay at full brightness when unplugged if i uncheck dim when idle .  is there a way to get both full brightness when unplugged AND the dim when idle feature working?

also, both when my screen dims when unplugged and when i plug it back in to return to full brightness (even though it is set to not dim at all on battery), the brightness icon appears.  i have not been able to get these brightness icons to appear in any other way because none of my function keys work.  might this have something to do with my problem?

---

### Post by JoshuaRL on 2008-01-21
Maybe, maybe not.  I would suggest backing up your /etc/X11/xorg.conf and trying:

```

sudo dpkg-reconfigure xserver-xorg

```

Go with whatever the default is for the keyboard and graphics card.

That is unless you know your card needs something special.

---

### Post by kbless7 on 2008-01-21
Why don't you just set it to turn the screen off after five minutes or something like that when its on battery power.

---

### Post by dysolve on 2008-01-21
my laptops screen dimming is handled by bios have a look in your bios for settings

---

### Post by kaston on 2008-01-21
> **JoshuaRL said:**
> Maybe, maybe not.  I would suggest backing up your /etc/X11/xorg.conf and trying:

```

sudo dpkg-reconfigure xserver-xorg

```

Go with whatever the default is for the keyboard and graphics card.

That is unless you know your card needs something special.

would you be able to explain to me basically what that code does.  and i'm not sure i understand what you mean by "Go with whatever the default is for the keyboard and graphics card".  sorry for my noobness but i'm trying to learn about linux in the process of fixing my problems instead of just blindly following suggestions.  thanks.

---

### Post by kaston on 2008-01-21
> **kbless7 said:**
> Why don't you just set it to turn the screen off after five minutes or something like that when its on battery power.that's a good idea, but unfortunately i have another problem which is that anytime my screen turns off for standby, suspend, or whatever, it never comes back on.  which is why i figured that dimming would be the next best thing.  but dimming doesn't work either!  i'm grateful that linux does away with antivirus and spyware software but i've got to say that most things worked better with win xp.

---

### Post by emarkd on 2008-01-22
Before you run the dpkg-reconfigure command MAKE SURE you've got a backup of your xorg.conf file.  You can make one by running

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

That just makes a copy and names it xorg.conf.backup

The dpgk-reconfigure command will step you through the process of reconfiguring your xserver.  It may or may not help and could make things worse if you don't answer the questions properly.  That's why the backup is so important.

---

### Post by jesusfreak107 on 2008-01-22
It is probably the BIOS that tells your computer to dim the monitor. also, it could simply be the fact that there is less power going to the monitor now that it is unplugged. You could always just raise the brightness. most laptops, you can do that with a couple keys, you would need to look at your keyboard.

---

### Post by firefeather on 2008-01-22
I'd also agree that it's your computer---not linux---that's changing your brightness. I don't have a laptop compatible with this but there's an applet that you can put on your panel (right-click on the panel at the top or bottom of the screen, click Add to Panel) that can change or deal with brightness of your screen. It's called "Brightness Applet".

EDIT: I wouldn't recommend worrying about reconfiguring xorg---I doubt it would help any IMHO but if it works, then great.

---

### Post by Rhubarb on 2008-01-22
Issuing "sudo dpkg-reconfigure xserver-xorg" will not fix up this problem at all.

Try System --> Preferences --> Power Management
In the "On Battery Power" tab, Uncheck the box named "Dim display when idle".

---

### Post by Rocket2DMn on 2008-01-22
Try this: Go to Applications->System Tools->Configuration Editor then select
Apps->Gnome-Power-Manager->Backlight
and set "brightness_battery" to 100.  Otherwise unchecking "enable" might work.

You can also specify "idle_dim_time" and "idle_brightness" here.

---

### Post by kaston on 2008-01-22
> **Rocket2DMn said:**
> Try this: Go to Applications->System Tools->Configuration Editor then select
Apps->Gnome-Power-Manager->Backlight
and set "brightness_battery" to 100.  Otherwise unchecking "enable" might work.

You can also specify "idle_dim_time" and "idle_brightness" here.i don't have configuration editor in my applications->system tools menu.  i only have virtualbox which i installed

---

### Post by emarkd on 2008-01-22
Try System > Preferences > GConf

or from the command line

```
gconf-editor
```

---

### Post by cujo on 2008-01-29
It may be too late, but I had this problem as well and I think I may have just solved it.  Then again, maybe I'm just not very observant.  Ok, here is what I did.

Assuming you have the power manager applet in your panel, right click on it and open the preferences.  Otherwise, go to System->Preferences->Power Management.

Now, for me, I would get random dimming when on battery even though I thought I had it set not to dim at all.  Well, I think the layout of that gnome power management preferences window screwed me up. 

The first tab, "On AC Power" has a slider at the bottom that says "Set display brightness to" with values from 0 to 100%.  The "On Battery Power" tab looks nearly identical except  the bottom slider is labeled "DIM display brightness by".  Well, I had them both set to 100%.  Not what I was after.  I just misread it.  Make sure you're setting them by what they actually say.  It tricked me.  I now have the battery one set to 0% so it is never dimmed automagically.

On one hand I hope this helps because it is the easiest fix of all.  On the other hand, I hope you aren't as silly as I.

---

