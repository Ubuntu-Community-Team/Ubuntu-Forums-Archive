---
title: "Mute Sound - Keyboard Button"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by yanewby on 2006-08-16
I have a "Mute Sound" button on my keyboard.  When I press this button it only mutes the "Master" channel according to "Volume Control" panel widget.  Any sounds playing on the PCM channel continue to play.

I would like to press the "Mute Sound" button and have ALL sound turned off.    How do I achieve this?

---

### Post by Cone on 2006-08-16
I'm not sure if this is what fixed my problem, but after doing it my problem went away, so it couldn't hurt to try.

In a terminal type "alsamixer", and right-arrow-key over to PCM and turn it up past 0 (mine was at zero, being why I was messing around with alsamixer, so quiet X_X) if it's at 0.  Then test muting the master channel and see if that affects everything.

Worked for me, hope it works for you.

Also, after doing this, the command "sudo alsactl store 0" will save the sound config so it loads on each boot.

Hope this helps you,
~Cone

---

### Post by yanewby on 2006-08-17
This did not solve my problem.  Still when I press the mute button on my keyboard it mutes the master channel and not the pcm channel (or preferably both).

---

### Post by LadyDoor on 2006-08-18
Here's what works for me! I warn you, these instructions are terminal-intensive. However, you don't actually need to know anything about it to begin with :D ! All you need to do is copy and paste--and don't worry, I'll explain what each command does. Now, start up a terminal. This can likely be found in one of your menus.

Pretty much any time I ask you to input something from here on out, I'm assuming that you're in a terminal and in your home directory. You'll know you're there because you'll see a line that looks something like this:

```
user@computername:~$
```

The tilde right before the end tells you you're in your home directory.

Oh, and **don't** copy the dollar signs in the following commands--they're to show you that this is somehting you enter and not the output from a program.

==========================================================================
STEP 0.5:  Installation of useful and necessary programs
==========================================================================

First, type or (better) copy/paste the following to install three programs:

```
$ sudo aptitude install xev xmodmap xbindkeys
```

I used aptitude in that command because it keeps track of any dependencies that get installed--so if something is installed just because xev required it (for example), and you decide to uninstall xev, that something will be uninstalled at the same time if nothing else needs it.

==========================================================================
STEP ONE:  Xev--find out the keycodes
==========================================================================

First, you need to find out what keycodes your volume keys are producing. The keycode is an identifier that X uses whenever a key is pressed. To discover the keycodes, we will use **xev**. If you want more info about the program (not necessary for this guide), type the following to bring up its manual.

```
$ man xev
```

When you're ready to find out what the keycodes are, enter:

```
$ xev
```

Move your mouse over the xev window that will pop up--but keep your eyes on the terminal! You'll see a LOT of nonsense speeding by. This is xev telling you what's happening "under the hood" anytime you do anything in X. Now, when you're ready, press the volume down key. Somewhere in all the messy output that will appear should be something that says something along the lines of 

```
keycode x
```

where x is the number you should write down. Repeat the same for the volume up key and the mute key, as well as anything you just happen to be curious about (for example, my laptop has a play/pause key)

Now that you have the keycodes for those keys (you do remember which is which, right? I'd make a note of that, too), it's time for step two!

==========================================================================
STEP 2:  The Xmodmap--naming the keys
==========================================================================

This step should be easy (yay!). No reading of bizarro-output, I promise. You will be using the *very* useful tool **xmodmap**, which can be used to give a keycode a keyname or to change what a key does (such as switching caps lock and control). For more info, enter the following.

```
$ man xmodmap
```

Now fire up your favorite text editor...in this example I'll use nano, becase it's easy to use and has nice little reminders of what keys to press in the toolbar (just remember, in the toolbar at the bottom, **^** = **Control** (so **^X**= **Control+x**)). You may prefer gedit, emacs, vi/m, etc. Your choice.

To do this, enter the following line. Note that I use .Xmodmap with a capital X. That's what happens to work on my computer. If it doesn't work, you might try changing that to a lowercase X. Also, note that the -w is important--whenever you're editing a config file, it's useful to have, because it prevents the program from breaking a line of code, which can mess things up badly.

```
$ nano -w .Xmodmap
```

Now copy and paste these lines in (**replacing** 174, 176, and 160 with whatever keycodes xev gave *you*). Note that any line starting with an exclamation point is considered a comment by the program and will be ignored.

```

!=========================================================================
! My .Xmodmap File
!=========================================================================

! These lines will name my volume keys.
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute

```

Press control-o, and hit enter to save the file, then press control-x to quit nano. If you want to make sure it worked, do

```
$ less .Xmodmap
```

You should see everything you just copied in.

Now, to load your xmodmap and name the keys, do the following.

```
$ xmodmap .Xmodmap
```

On to step three!

==========================================================================
STEP 3:  Xbindkeys--making them do what you want!
==========================================================================

We're in the home stretch! Just bear with me a little longer and we'll be finished.

Now, for this step, we're going to use **xbindkeys**. This nifty program lets you take any key on your keyboard and assign a **completely arbitrary** command to it. So if I wanted the letter A to shut down my computer anytime I pressed it, I could do that with xbindkeys. Personally, I don't use it for anything that stupid :-) . For example, I've got a screenshot button that (*gasp*) takes screenshots now. For more info, as always,

```
$ man xbindkeys
```

Let's start by giving you the xbindkeys default config file. Enter the following:

```
$ xbindkeys --defaults > .xbindkeysrc
```

The **--defaults** makes xbindkeys print out what its default configuration file would look like. The **>** takes what would normally scroll along your screen as the output of the command and puts it into a file, which you name afterwards. NOTE:  When adding something to an already-existing file this way, be **sure** to use >>, which adds instead of overwriting.

Now, once again you're going to fire up nano (or whatever).

```
$ nano -w .xbindkeysrc
```

You'll see a lot of stuff. The lines with "#" in front are comments and are ignored. Look through the file--it's not that long. Anything that you don't understand the explanation of or just don't want is safe to delete, and might actually do something annoying. I would advise you to leave the comments at the top, though, as they have very useful information in them!

After you get done with that, copy and paste the following at the end of the file.

```

#======================================================================================
# Add the volume keys
#======================================================================================

# These first set up just the volume keys to control the PCM channel
"amixer set PCM 1-"
  XF86AudioLowerVolume
"amixer set PCM 1+"
  XF86AudioRaiseVolume
"amixer set PCM toggle"
  XF86AudioMute

# These next three will make control+volume control the Master channel
"amixer set Master 1-"
  control + XF86AudioLowerVolume
"amixer set Master 1+"
  control + XF86AudioRaiseVolume
"amixer set Master toggle"
  control + XF86AudioMute

# And alt+volumekeys controls the headphone volume
"amixer set Headphone 1-"
  Mod1 + XF86AudioLowerVolume
"amixer set Headphone 1+"
  Mod1 + XF86AudioRaiseVolume
"amixer set Headphone toggle"
  Mod1 + XF86AudioMute

# Shift+mute toggles automatic muting of the master channel when
#  headphones are plugged in
"amixer set 'Headphone Jack Sense' toggle"
  shift + XF86AudioMute

```

Again, save with control-o and exit with control-x.

Now, to load that file, enter this command:

```
$ xbindkeys
```

Check it out! Does it work? (No, really, I'm curious--I've never tried it in any of the actual desktop environments like GNOME/KDE/XFCE--I tend to use ratpoison, or if I need more graphics, Fluxbox). If it does work, I believe there should be a way to automatically load both xmodmap and xbindkeys when you log in--if you're using GNOME, I *think* there may be a "session settings" dialog somewhere, but I could just be making that up. Look around in the GNOME menus a little bit and maybe search for "start program login" or something along those lines on the forum, or check the GNOME help.

You're almost done. You've made it this far, now just enter this (DO copy and paste the SECOND dollar sign--it's important):

```
$ echo "Finished! $(whoami) totally rocks"
```

Aaaaand...you're done. I hope this helps!

Good luck,
Door

---

### Post by sirlancelot on 2006-09-04
Whenever I type```
amixer set PCM toggle
```I get this error:```
amixer: Unknown capture setup 'toggle'..
```Am I running an old/new version of amixer?

---

### Post by LadyDoor on 2006-09-04
SirLancelot, is your PCM device a recording device for some reason? You might install and run the command alsamixer (escape exits) to determine your exact device names. I hope that helps/works!

--Door

---

### Post by sirlancelot on 2006-09-09
Thanks LadyDoor, but I'm trying to mute (toggle) a playback channel. the "Master" channel to be specific. I read the manpage for 'amixer' and apparently toggle is used for the recording channels only.

Is there a way to toggle a playback (output) channel volume?

---

### Post by LadyDoor on 2006-09-10
> Thanks LadyDoor, but I'm trying to mute (toggle) a playback channel. the "Master" channel to be specific. I read the manpage for 'amixer' and apparently toggle is used for the recording channels only.

Is there a way to toggle a playback (output) channel volume?

Hmmm, this is a quandary. I don't use capture on my computer, and toggle works to toggle the mute setting for any given playback channel (such as Master & PCM) in my amixer. Here's the relevant line from the manpage (emphasis added for effect):

```
The  parameters  cap,  nocap, mute, unmute, toggle are used to change capture (recording) *and muting* for the group specified.
```

This wording is somewhat ambiguous, perhaps because which devices are considered to be recording devices and which will be playback devices differ, but I'm not sure. I don't know whether this will work, but you might try

```

$ amixer set ChannelName nocap
$ amixer set ChannelName toggle

```

on the commandline to see whether perhaps your channel is set up to capture...if not, in theory, "toggle" should toggle mute. Also, did you remember the quotes in your .xbindkeysrc?

I hope that does something for you,
Door

---

### Post by TMU on 2006-09-15
LadyDoor I think I'm in love with you! It works, YESSSSS!!
Awesome how-to!
Thanks a lot, I'll recommend it at least to 20.000 german ubuntu-users (although I'm from Austria ;-))

---

### Post by mtron on 2006-09-15
thanks for this! 

but i have some special buttons that produce no output in xev. is there a way to assign keycodes to them, (or do they have already a keycode?) it's a MS Wireless Optical Desktop for bluetooth

chees mtron

---

### Post by H.E. Pennypacker on 2006-09-16
LadyDoor, I've followed the directions from someone else that are almost identical to yours, with the obvious exception being .Xmodmap.

[http://www.tannerstokes.com/2006/08/02/getting-those-multimedia-keys-to-work-in-kubuntu/](http://www.tannerstokes.com/2006/08/02/getting-those-multimedia-keys-to-work-in-kubuntu/)

I used that guide, and I tried to follow yours too, but I am still having a problem with the raise volume key being "capped" somewhere.  It can't raise the volume all the way to the top of the volume bar.  In other words, as I explained in that guide's comment section, I can only raise the volume to a certain point.  Lowering the volume is perfect, and so is mute.

---

### Post by LadyDoor on 2006-09-16
> but i have some special buttons that produce no output in xev. is there a way to assign keycodes to them, (or do they have already a keycode?) it's a MS Wireless Optical Desktop for bluetooth

Yeah...I don't know that that's possible. I also have a key which wouldn't co-operate with Xev and which I just gave up on mapping. You might consider instead mapping a key combination to do the same thing you want that button to (such as, say, control+F5 to open firefox instead of Fn+www (not actually something I use, just a generic example)). Let me know if you get it to work, I guess, and good luck!

> I am still having a problem with the raise volume key being "capped" somewhere. It can't raise the volume all the way to the top . . . I can only raise the volume to a certain point. Lowering the volume is perfect, and so is mute.

That is very strange. Are you using amixer to raise/lower your volume or something else? One thing you might try is to open a terminal and see whether it's possible to use the command you're using to raise the volume all the way to the top. So for me, that would be:

```
$ amixer set PCM 1+
```

over and over again. Note:  you wouldn't have to use the number "1" if that's too slow for you (though I think it raises it more than 1% each time you hit it). Also, pressing control-p will take you to the previous command entered, so you don't have to retype it each time. I hope that helps, and good luck!

--Door

---

### Post by H.E. Pennypacker on 2006-09-16
LadyDoor, yes, I am using Alsa Mixer, and yes, "amixer set Master 1+" does work.  Note that I don't use PCM, only Master.  I've merged the two so that Master and PCM work as one.

Still, raising the volume is still capped.  Check out this screenshot:

[[IMG]http://img158.imageshack.us/img158/7936/screenshot10ph6.th.png[/IMG]](http://img158.imageshack.us/img158/7936/screenshot10ph6.png)

Notice how volume dialog appears whenever I either raise/lower/mute the volume.  You'll see that there are multiple "blocks" there of that bar.  When lowering the volume, I could go all the way down beginning at the end, but the same can't be done with raising the volume.  It moves a little, but can't go up significantly, and definitely can't reach the end.

---

### Post by LadyDoor on 2006-09-18
Aha, the problem here is that GNOME has autodetected your volume keys and thinks it ought to control them. I don't know how to turn that off other than just not using a desktop environment (i.e., using just a window manager instead). You might post a question regarding how to disable GNOME's volume-key support, or even better if you like desktop environments, ask how to reconfigure it so that it works right. That's about all I know...good luck.

--Door

---

### Post by H.E. Pennypacker on 2006-09-21
LadyDoor, yes, Gnome does control the keys...isn't that the whole objective?

I *can* turn off Gnome's (System > Preferences > Keyboard Shortus > Disable shorts cuts for the volume keys) control over this, but wouldn't that defeat the purpose?  With Gnome controlling the keys, my lower volume key and mute keys work perfectly fine.  So, the question is, why not the raise volume key?  It doesn't make sense.

For the purposes of experimenting with your train of thought, I'll turn off  Gnome's control over the keys, and start all over with this or Tanner's guide.

---

### Post by LadyDoor on 2006-09-22
If you'll recall, the point of this guide was to provide a *cross-platform* way of binding your volume keys. The idea is that anyone, including people like myself who are not fond of any of the desktop environments offered as standard by *buntu (GNOME, KDE, XFCE4) can still have the same benefit of volume keys as users who are fond of them have. It *should* work in GNOME/KDE/XFCE4, but it also works in simpler window managers. So no, the idea is not to have GNOME controlling the volume keys--it's to not have to have GNOME to use the volume keys. However, that does not preclude its working in those environmtents. *shrug* [/diatribe]

As to your problem, I'm afraid that I really don't know what would cause it to not go all the way up. It's actually kind of bizarre and may have something to do with its misdetecting the capabilities of your hardware, but that's just a guess. Good luck!

--Door

---

### Post by ]Nbx*cmD[ on 2006-12-15
Ladydoor you use ratpoison!!!! Me too!!
I've been looking for a long time for ubuntu rat users, i'd want to create a little community (eg mail list) to communicate each other
or maybe just a thread about rat and exchange our scripts, configs, tweaks... I've found one or two more people over there using ubuntu and rat! :)

---

