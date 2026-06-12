---
title: "Remote works!?"
date: 2007-06-25
forum: Apple Intel Users
---

### Post by Torajima on 2007-06-25
Well I'm pretty stoked... I just discovered that, out of the box, the Apple Remote works with Movie Player! With the exception of the Menu button (which doesn't appear to do anything) all the keys do what they're supposed to... play/pause, volume up/down, and skip thru movies.

Hmm... it seems to work with RhythmBox too!

---

### Post by ronocdh on 2007-06-25
> **Torajima said:**
> Well I'm pretty stoked... I just discovered that, out of the box, the Apple Remote works with Movie Player! With the exception of the Menu button (which doesn't appear to do anything) all the keys do what they're supposed to... play/pause, volume up/down, and skip thru movies.

Hmm... it seems to work with RhythmBox too!
This made me laugh out loud. I never thought to try it! Thanks very much for this, how awesome.

:popcorn:

---

### Post by ivesjd on 2007-06-26
That was one of the first things I tried. Although I don't mine works as well. At least not with amarok.

---

### Post by benanzo on 2007-06-26
It has worked out of the box since like Feisty herd 1 - do you guys live under a rock? joking...seriously.

Anyway....

Yes, you can remap the keys to do whatever you want in the keyboard shortcuts.

I have installed and configured lirc's *irexec* utility so I can have the buttons do different things in different apps instead of just the global gnome settings.  For instance if I'm looking at my desktop I can press menu to launch rhythmbox then I press menu again to turn the forward/backward vol+/vol- buttons into directional keys so i can browse my library then play/pause to start a song, then menu again to turn the keys back to normal.  It works great in MythTV or Elisa as well.  Check out *irexec* in LIRC, it is wonderful.

---

### Post by ivesjd on 2007-06-26
That sounds very nice Benanzo.

---

### Post by kzm. on 2007-06-27
is there a good how to for irexec?
i get some errors:
irexec: could not connect to socket
irexec: Connection refused

---

### Post by vh1 on 2007-06-28
> **benanzo said:**
> It has worked out of the box since like Feisty herd 1 - do you guys live under a rock? joking...seriously.

Anyway....

Yes, you can remap the keys to do whatever you want in the keyboard shortcuts.

I have installed and configured lirc's *irexec* utility so I can have the buttons do different things in different apps instead of just the global gnome settings.  For instance if I'm looking at my desktop I can press menu to launch rhythmbox then I press menu again to turn the forward/backward vol+/vol- buttons into directional keys so i can browse my library then play/pause to start a song, then menu again to turn the keys back to normal.  It works great in MythTV or Elisa as well.  Check out *irexec* in LIRC, it is wonderful.

mind posting a about how you achieved this?
using the menu button to toggle between the two control methods is a nice idea

---

### Post by ronocdh on 2007-06-28
> **vh1 said:**
> mind posting a about how you achieved this?
using the menu button to toggle between the two control methods is a nice idea
Agreed. Let's have a how-to! We'll sticky it. ;)

---

### Post by benanzo on 2007-06-28
I'll write one up and post my lirc confs tomorrow or the next day.  Stay tuned.

---

### Post by kzm. on 2007-06-28
thanx, benanzo. looking forward.

---

### Post by Azathoth_ on 2007-06-28
Jejeje. I have just create a spanish howto about it.
I get it working with lirc but you don't need to configure it. It's simple: with inputlirc and your script of applets configuration:  [http://magarto.com/blog/archivo/2007/06/27/howto-usar-apple-remote-de-los-macbooks-en-ubuntu-entre-otros-para-multiples-aplicaciones-sin-necesidad-de-lirc/](http://magarto.com/blog/archivo/2007/06/27/howto-usar-apple-remote-de-los-macbooks-en-ubuntu-entre-otros-para-multiples-aplicaciones-sin-necesidad-de-lirc/)

The menu button does not work because its hexadecimal code is assigned in /usr/include/linux/input.h to KEY_BACK   and this key cannot be used in lirc, only in xmodmap:   xmodmap -pke > xmodmap.conf && nano xmodmap.conf

Assign the 164 or 158 (i cannot remind) to XF86AudioStop and after xmodmap xmodmap.conf

And you can use menu key as a keyboard key but not in lirc because it detects /dev/input/eventX and it is before xmodmap. But it is a temporal solution.

I am going to change the /etc/lircrc that i wrote in the howto to include: if mplayer is open do that, else if kaffeine is open... thath... i hope you follow me

:D

---

### Post by kzm. on 2007-06-28
"ich versteh nur spanisch"

thanx man! i dont really get what you are saying here, but i will definitely look at your spanish how to and just do the terminal stuff seeing where it gets me.

---

### Post by Azathoth_ on 2007-06-28
I do not have enought time now to make a howto in english here, but i am going to do soon

---

### Post by benanzo on 2007-06-28
my worst nightmare...

The PSU in my MacBook died overnight.  My machine wont even turn on -- it doesn't recognize the power plug nor the battery.  I have to send it in for warranty repair or replacement.  Does anyone know how Apple feels about not having OS X on the hard drive when they get it?  I am going to take out my regular Ubuntu drive and put in the original that came with the machine, but it has Ubuntu as well...

Will Apple freak out?

---

### Post by ivesjd on 2007-06-28
I'm not sure, a friend of mine just had the two inner pins on his break. So he bought a new PSU, but idk about sending it in.  Did you check the pins to see if they were stuck down?

---

### Post by vh1 on 2007-06-29
> **benanzo said:**
> my worst nightmare...

The PSU in my MacBook died overnight.  My machine wont even turn on -- it doesn't recognize the power plug nor the battery.  I have to send it in for warranty repair or replacement.  Does anyone know how Apple feels about not having OS X on the hard drive when they get it?  I am going to take out my regular Ubuntu drive and put in the original that came with the machine, but it has Ubuntu as well...

Will Apple freak out?

what do you mean exactly?
sometimes the battery in my macbook just freaks out. try turning the machine off, taking out the batter, plugging in the power and turning it on without the battery

---

### Post by luisbg on 2007-06-29
awesome! thanks

o mejor dicho... gracias!

---

### Post by benanzo on 2007-06-30
I tried taking out the battery and plugging it in but the light on the plug doesn't turn on.  I tried putting the battery in a friend's macbook and it still works.  I tried using my power plug in a friend's macbook with no problem.  I feel I have narrowed it down to a malfunction in the PSU or at least the magnetic power slot, but everything *looks* normal.

I am just going to send it in.  I can't use my friend's machine to install OS X on my disk because it reads the serial number out of the EFI...Apple will call me a thief or something.  I'll just send it in without a disk and claim "data sensitivity."

---

### Post by vh1 on 2007-07-03
okay, it may have taken a night of trial and error, but I finally have a reasonable .lircrc using the menu button as a toggle between "media" and "browsing"

I tried and tried to get a more OSX feel with holding down buttons (holding next turns into fast-forward) but I couldn't get rid of the initial next event

```
begin
	flags = startup_mode
	mode = media
end

begin media
	begin
		prog = irxevent
		button = PLAY
		config = Key KeyCode:162 CurrentWindow
	end
	begin
		prog = irexec
		button = VOLUME_UP
		config = volumemod up
		repeat = 3
	end
	begin
		prog = irexec
		button = VOLUME_DOWN
		config = volumemod down
		repeat = 3
	end
	begin
		prog = irxevent
		button = NEXT
		config = Key KeyCode:153 CurrentWindow
	end
	begin
		prog = irxevent
		button = PREVIOUS
		config = Key KeyCode:144 CurrentWindow
	end

	# failed attempt at holding/switching
	# sorry it's real late and my grammar has fallen apart
	# try uncommenting this and holding the next button
	#begin
	#	prog = irexec
	#	button = NEXT
	#	config = echo "next"
	#end
	#begin
	#	prog = irexec
	#	button = NEXT
	#	config = echo "forward"
	#	repeat = 10
	#	delay = 15
	#end

	begin
		flags = quit
		mode = browse
		button = MENU
		prog = irexec
		config = dcop khotkeys kmilod displayText "to browse"
	end
end media

begin browse
	begin
		prog = irxevent
		button = PLAY
		config = Key Return CurrentWindow
	end
        begin
                prog = irxevent
                button = VOLUME_UP
                config = Key Up CurrentWindow
        end
        begin
                prog = irxevent
                button = VOLUME_DOWN
                config = Key Down CurrentWindow
        end
        begin
                prog = irxevent
                button = NEXT
                config = Key Right CurrentWindow
        end
        begin
                prog = irxevent
                button = PREVIOUS
                config = Key Left CurrentWindow
        end

	begin
		flags = quit
		mode = media
		button = MENU
		prog = irexec
		config = dcop khotkeys kmilod displayText "to media"
	end
end browse
```

a few notes:
I'm a kubuntu user, so I use kmilo to alert what mode is set. there's probably someting better out there. I map keycode 162 to XF86AudioPlay instead of XF86AudioPause (programs didn't seem to detect that for some reason). your keycodes may differ. `xmodmap -pke | grep XF86Audio` to see which ones you'll be using

I couldn't get inputlirc to work and used irrecord to setup the buttons. volumemod is a little script I wrote for reasons I forget. probably something to do with pommed's strange controlling of audio

---

### Post by Azathoth_ on 2007-07-17
Hiii. Thankssss.
It is KEY_MENU
And holding does not work :(

---

### Post by Azathoth_ on 2007-07-17
Here is my /etc/lirc/lircrc script:

> 
##################################################
#### Change mode  ####
## If anyone can make this work (in example: pressing a button some time please notify us ##
##################################################

#begin
#	prog = irexec
#	button = KEY_PLAYPAUSE
#	mode = amarok
#	config = echo "Modo amarok"
#end
#
#begin
#	prog = irexec
#	button = KEY_NEXTSONG
#	mode = kaffeine
#	config = echo "Modo kaffeine"
#end
#begin
#	prog = irexec
#	button = KEY_PREVIOUSSONG
#	mode = kaffeine
#	config = echo "Modo kaffeine"
#end


#############
#### VLC ####
#############

begin
        prog = vlc
        button = KEY_PLAYPAUSE
        config = key-play-pause
	repeat = 0
end

begin
        prog = vlc
        button = KEY_MENU
        config = key-stop
	repeat = 0
end

begin
        prog = vlc
        button = KEY_PREVIOUSSONG
        config = key-jump-1min
	repeat = 1
end

begin
        prog = vlc
        button = KEY_NEXTSONG
        config = key-jump+short
	repeat = 1
end
begin
       prog = vlc
       button = KEY_VOLUMEUP
       config = key-vol-short
       repeat = 1
end

begin
       prog = vlc
       button = KEY_VOLUMEDOWN
       config = key-vol-down
       repeat = 1
end


#################
#### MPlayer ####
#################

#begin mplayer
begin
        prog = mplayer
        button = KEY_PLAYPAUSE
        config = pause
	repeat = 15
end

begin
        prog = mplayer
        button = KEY_MENU
        config = stop
	repeat = 15
end

begin
        prog = mplayer
        button = KEY_PREVIOUSSONG
        config = seek -10
        repeat = 10
end

begin
        prog = mplayer
        button = KEY_NEXTSONG
        config = seek +10
        repeat = 10
end
begin
       prog = mplayer
       button = KEY_VOLUMEUP
       config = volume 1
       repeat = 1
end

begin
       prog = mplayer
       button = KEY_VOLUMEDOWN
       config = volume -1
       repeat = 1
end
#end mplayer


##################
#### Kaffeine ####
##################

#begin kaffeine
begin
	prog = irexec
	button = 
	config = dcop kaffeine MainApplication-Interface
end

begin
	prog = irexec
	button = KEY_PLAYPAUSE
	config = if `dcop kaffeine KaffeineIface isPlaying`; then dcop kaffeine KaffeineIface pause; dcop kaffeine kaffeine_mainview hide; else dcop kaffeine KaffeineIface play; dcop kaffeine kaffeine_mainview hide; fi
end

begin
	prog = irexec
	button = KEY_MENU
        repeat = 1
	config = dcop kaffeine KaffeineIface stop
end

begin
	prog = irexec
	button = KEY_NEXTSONG
        repeat = 1
	config = dcop kaffeine KaffeineIface posPlus
end

begin
	prog = irexec
	button = KEY_PREVIOUSSONG
        repeat = 1
	config = dcop kaffeine KaffeineIface posMinus
end

begin
	prog = irexec
	button = KEY_VOLUMEUP
        repeat = 1
	config = dcop kaffeine KaffeineIface volUp
end

begin
	prog = irexec
	button = KEY_VOLUMEDOWN
        repeat = 1
	config = dcop kaffeine KaffeineIface volDown
end

#end kaffeine


################
#### Amarok ####
################

#begin amarok
begin
	prog = irexec
	button = KEY_PLAYPAUSE
	config = dcop amarok player playPause
end

begin
	prog = irexec
	button = KEY_MENU
	config = dcop amarok player stop
end

begin
	prog = irexec
	button = KEY_NEXTSONG
	config = dcop amarok player next
end

begin
	prog = irexec
	button = KEY_PREVIOUSSONG
	config = dcop amarok player prev
end

begin
	prog = irexec
	button = KEY_VOLUMEUP
        repeat = 1
	config = dcop amarok player volumeUp
end

begin
	prog = irexec
	button = KEY_VOLUMEDOWN
        repeat = 1
	config = dcop amarok player volumeDown
end
#end amarok


###############
#### Totem ####
###############

begin
	prog = irxevent
	button = KEY_PLAYPAUSE
	config = Key p Totem
	repeat = 0
end

begin
	prog = irexec
	button = KEY_MENU
	config = stop
	repeat = 0
end

begin
	prog = Totem
	button = KEY_NEXTSONG
	config = seek_forward
	repeat = 0
end

begin
	prog = Totem
	button = KEY_PREVIOUSSONG
	config = seek_backward
	repeat = 0
end

begin
	prog = irexec
	button = KEY_VOLUMEUP
        repeat = 10
	config = 
end

begin
	prog = irexec
	button = KEY_VOLUMEDOWN
        repeat = 10
	config = 
end



###################
#### Audacious ####
###################

begin
	prog = audacious
	button = KEY_PLAYPAUSE
	config = PAUSE
	repeat = 16
end

begin
	prog = audacious
	button = KEY_MENU
	config = STOP
	repeat = 0
end

begin
	prog = audacious
	button = KEY_NEXTSONG
	config = NEXT
	repeat = 16
end

begin
	prog = audacious
	button = KEY_PREVIOUSSONG
	config = PREV
	repeat = 16
end


##############
#### XMMS ####
##############

begin
	prog = xmms
	button = KEY_PLAYPAUSE
	config = pause
end

begin
	prog = xmms
	button = KEY_MENU
	config = stop
end

begin
	prog = xmms
	button = KEY_NEXTSONG
	config = next
	repeat = 16
end

begin
	prog = xmms
	button = KEY_PREVIOUSSONG
	config = prev
	repeat = 16
end

begin
	prog = xmms
	button = KEY_VOLUMEUP
	config = fwd 5
	repeat = 10
end

begin
	prog = xmms
	button = KEY_VOLUMEDOWN
	config = bwd 5
	repeat = 10
end


###############
##### XdTV ####
###############

begin
	prog = irexec
	button = KEY_PLAYPAUSE
	config = record
	repeat = 0
end

begin
	prog = irexec
	button = KEY_PREVIOUSSONG
	config = setstation prev
	repeat = 0
end

begin
	prog = irexec
	button = KEY_PNEXTSONG
	config = setstation next
	repeat = 0
end

################
#### TVtime ####
################

#begin tvtime

begin
    prog = irexec
    button = KEY_PLAYPAUSE
    config = tvtime-command ENTER
end

begin
    prog = irexec
    button = KEY_MENU
    config = tvtime-command TOGGLE_FULLSCREEN
end

begin
    prog = irexec
    button = KEY_NEXTSONG
    config = tvtime-command UP
    repeat = 1
end
begin
    prog = irexec
    button = KEY_PREVIOUSSONG
    config = tvtime-command DOWN
    repeat = 1
end
begin
    prog = irexec
    button = KEY_VOLUMEUP
    config = tvtime-command RIGHT
    repeat = 2
end
begin
    prog = irexec
    button = KEY_VOLUMEDOWN
    config = tvtime-command LEFT
    repeat = 2
end

#begin
#    prog = irexec
#    button = middle
#    config = tvtime-command CHANNEL_JUMP
#    repeat = 1
#end

#end tvtime


################################################################################
#### Turn up and down the volume (Working by default  on Feisty) ####
################################################################################

#begin
#prog = irexec
#button = KEY_VOLUMEUP
#config = amixer set PCM 9+ &      #amixer set PCM 3%+ &
#repeat = 2
#end
#begin
#prog = irexec
#button = KEY_VOLUMEDOWN
#config = amixer set PCM 9- &      #amixer set PCM 3%- &
#repeat = 2
#end

##############################################
#### Evince y OpenOffice (Presentations) ####
##############################################

begin
        prog = irxevent
        button = KEY_PLAYPAUSE
	config = Key F11 CurrentWindow
        config = Key F5 CurrentWindow
	repeat = 0
end

begin
        prog = irxevent
	button = KEY_MENU
	config = Key Escape CurrentWindow
	repeat = 0
end

begin
        prog = irxevent
        button = KEY_PREVIOUSSONG
        config = Key Prior CurrentWindow
	repeat = 1
end

begin
        prog = irxevent
        button = KEY_NEXTSONG
        config = Key Next CurrentWindow
	repeat = 1
end

begin
	prog = irxevent
	button = KEY_VOLUMEUP
	config = Key ctrl-plus CurrentWindow
	repeat = 0
end

begin
	prog = irxevent
	button = KEY_VOLUMEDOWN
	config = Key ctrl-minus CurrentWindow
	repeat = 0
end


---

### Post by vh1 on 2007-07-17
> **Azathoth_ said:**
> Here is my /etc/lirc/lircrc script:

if you look at the lirrc I posted it does mode-switching. you'll have to comment out the little bit of code to see my attempt and holding buttons

and as I said, I couldn't get anywhere with inputlirc so I just set it up manually with irrecord

---

