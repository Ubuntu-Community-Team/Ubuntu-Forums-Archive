---
title: "Lircrc working on Macbook!"
date: 2007-07-17
forum: Apple Intel Users
---

### Post by Azathoth_ on 2007-07-17
[SIZE="3"]**If anyone can make a better script using Menu + another key + another key to enable modes or detecting the application that is in the Current Window  and enabling a different function if we keep on pushing a key some time, please report it.**[/SIZE]

This lircrc supports: _VLC, Mplayer, Kaffeine, Amarok, Totem, Audacious, XMMS, TVtime, XdTV, Evince and Presentations of OpenOffice._

First install inputlircrc and lirc:

```
sudo aptitude install inputlirc lirc lirc-x
```

Now, make it works on boot. Add this to the top of /etc/rc.local

```
sudo /etc/init.d/inputlirc start
```

Now you have to add these two commands to the session init: System/Preferencies/Session

```
irexec -d
irxevent
```

Now, copy the next text to the /etc/lirc/lircrc doing

```
sudo nano /etc/lirc/lircrc
```

_Note_: If you are not superuser, you can write it in /home/your_user/.lircrc instead of /etc/lirc/lircrc

And add this script i have created by myself

```
##################################################
#### Change mode ####
## If anyone can make this work (in example: pressing a button some time please notify us ##
##################################################

#begin
# prog = irexec
# button = KEY_PLAYPAUSE
# mode = amarok
# config = echo "Modo amarok"
#end
#
#begin
# prog = irexec
# button = KEY_NEXTSONG
# mode = kaffeine
# config = echo "Modo kaffeine"
#end
#begin
# prog = irexec
# button = KEY_PREVIOUSSONG
# mode = kaffeine
# config = echo "Modo kaffeine"
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
button = KEY_NEXTSONG
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
# prog = irexec
# button = middle
# config = tvtime-command CHANNEL_JUMP
# repeat = 1
#end

#end tvtime


################################################## ##############################
#### Turn up and down the volume (Working by default on Feisty) ####
################################################## ##############################

#begin
#prog = irexec
#button = KEY_VOLUMEUP
#config = amixer set PCM 9+ & #amixer set PCM 3%+ &
#repeat = 2
#end
#begin
#prog = irexec
#button = KEY_VOLUMEDOWN
#config = amixer set PCM 9- & #amixer set PCM 3%- &
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
```

Now save (Ctrl + o) and close nano (Ctrl + x)

Reboot and you can use your apple remote now.

If you are spanish, please visit my web: [http://magarto.com](http://magarto.com)

:D :D :D

Note: I'm going to modify this script soon to add the work of [vh1]("http://ubuntuforums.org/member.php?u=36514") made [here]("http://ubuntuforums.org/showpost.php?p=2954579&postcount=19").

---

### Post by joselin on 2007-07-17
Hi,

I own an iMac with remote.

With a fresh install remote works, only have limited functions, but works. I meant, works play, stop, rewind and forward keybs. And doesn't work menu keyb. And this, only works on several programs (totem, rythmbox) and does not work on others (listen).

I can't locate lircrc file, so do you know where the configuration files for this are?

Regards

---

### Post by Azathoth_ on 2007-07-17
It can be on /home/your_user/.lircrc or in /etc/lirc/lircrc

---

### Post by Azathoth_ on 2007-07-17
> **joselin said:**
> Hi,

I own an iMac with remote.

With a fresh install remote works, only have limited functions, but works. I meant, works play, stop, rewind and forward keybs. And doesn't work menu keyb. And this, only works on several programs (totem, rythmbox) and does not work on others (listen).

I can't locate lircrc file, so do you know where the configuration files for this are?

Regards

I think its better disabling this functions and enabling lirc. By this way you can use lirc to any program: using **irexec** if this program supports lirc or **irxevent** if this program does not support lirc.

Joselin if you need any help, please sent it throught Privated Message in spanish (i can see you are spanish). I am busied now :(

---

### Post by benanzo on 2007-07-17
Great work...(you stole my thunder)...I was going to post this when I got my MacBook back from Apple repair.  I can't remember how my lircrc looked but it seems similar.  When I get it back (next week?) I will post my config.

---

### Post by Azathoth_ on 2007-07-17
> **benanzo said:**
> Great work...(you stole my thunder)...I was going to post this when I got my MacBook back from Apple repair.  I can't remember how my lircrc looked but it seems similar.  When I get it back (next week?) I will post my config.

Great then. Could you get the things i am going to try working??? Please tell me to try them or not

---

### Post by benanzo on 2007-07-17
Yes, I did get it to work.  I didn't do mode switching by holding down any buttons though.  I just used the Menu button for mode-switching.  For instance, if I had rhythmbox open I would press Menu to make the left/right vol+/vol- buttons into directional keys so I can browse the library and Play/pause was Tab so I could switch panes.  If I pressed Menu again it would change them back to normal.

Also, I didn't use inputlirc for anything.  I just used irxevent and irexec.  I had trouble switching the focused window, sometimes LIRC would get too confused and stop working.  I'll post what I had when I get my machine back.

---

### Post by Azathoth_ on 2007-07-17
> **benanzo said:**
> Yes, I did get it to work.  I didn't do mode switching by holding down any buttons though.  I just used the Menu button for mode-switching.  For instance, if I had rhythmbox open I would press Menu to make the left/right vol+/vol- buttons into directional keys so I can browse the library and Play/pause was Tab so I could switch panes.  If I pressed Menu again it would change them back to normal.

Also, I didn't use inputlirc for anything.  I just used irxevent and irexec.  I had trouble switching the focused window, sometimes LIRC would get too confused and stop working.  I'll post what I had when I get my machine back.

Great, but by this way, if you have supported a lot of applications it might be always a script to see what is the main application and then you can select the different modes adding mode = x1 and mode = x2 to the button to enable the modes.

Anyway i can wait gor it :P

---

### Post by boumcke on 2007-07-24
Nice job. I don't use half of these programs but hey, that's not the point.

Anyway, do you have any idea on how I could get the remote to control gThumb? It would be kind of sweet to browse through my pictures with the remote...

---

### Post by Azathoth_ on 2007-07-24
> **benanzo said:**
> Yes, I did get it to work.  I didn't do mode switching by holding down any buttons though.  I just used the Menu button for mode-switching.  For instance, if I had rhythmbox open I would press Menu to make the left/right vol+/vol- buttons into directional keys so I can browse the library and Play/pause was Tab so I could switch panes.  If I pressed Menu again it would change them back to normal.

Also, I didn't use inputlirc for anything.  I just used irxevent and irexec.  I had trouble switching the focused window, sometimes LIRC would get too confused and stop working.  I'll post what I had when I get my machine back.

Do you have it???

---

### Post by benanzo on 2007-07-24
I will post my lircrc when I get my machine back from apple repair...the psu died about two weeks ago.

---

### Post by mccrackin on 2007-08-05
Hi,

I followed the instructions on page one and my MacBook remote does NOT work.  The volume controls worked right out of the box, but there is no difference after following the steps on page one of this discussion.  I'm no linux expert, but I'm pretty certain I did everything as I should.  All I really want to do is use the remote for OO/powerpoint presentations.

Thanks in advance!
DM

---

### Post by Azathoth_ on 2007-08-06
> **mccrackin said:**
> Hi,

I followed the instructions on page one and my MacBook remote does NOT work.  The volume controls worked right out of the box, but there is no difference after following the steps on page one of this discussion.  I'm no linux expert, but I'm pretty certain I did everything as I should.  All I really want to do is use the remote for OO/powerpoint presentations.

Thanks in advance!
DM

Open a terminal and try this:
killall irxevent
killall irexec

Now in this terminal launch.
irxevent

Does this terminal wait? Or this terminal open this command and close it?

Now press + button of the apple remote. What happens?

---

### Post by bsantos on 2008-01-23
Hi,

I only use the remote for totem and got mode changing to work so I can seek with the default mode and change track on the other mode.

I use menu for mode change and also switch fullscreen on the second mode with the PLAY button.

My .lircrc
```
begin
  flags = startup_mode
  mode = totem1
end

begin totem1
  begin
    prog = Totem
    button = PLAY
    config = play_pause
  end

  begin
    prog = irexec
    button = MENU
     config = gnome-osd-client -f "<message id='irexec' osd_fake_translucent_bg='on' osd_vposition='center' animations='on' hide_timeout='1000' osd_halignment='center'>Changed to mode 2</message>"

  end

  begin
    prog = Totem
    button = MENU
    mode = totem2
    flags = mode quit
  end 
   
  begin
    prog = Totem
    button = NEXT
    config = seek_forward
    repeat = 3
  end

  begin
    prog = Totem
    button = PREV
    config = seek_backward
    repeat = 3
  end

  begin
    prog = Totem
    button = PLUS
    config = volume_up
    repeat = 3
  end

  begin
    prog = Totem
    button = MINUS
    config = volume_down
    repeat = 3
  end
end totem1

begin totem2
  begin
    prog = Totem
    button = PLAY
    config = fullscreen
  end

  begin
    prog = Totem
    button = NEXT
    config = next
  end

  begin
    prog = Totem
    button = PREV
    config = previous
  end
end totem2

begin
   button = MENU
   mode = totem1
   flags = mode quit
   prog = irexec
   config = gnome-osd-client -f "<message id='irexec' osd_fake_translucent_bg='on' osd_vposition='center' animations='on' hide_timeout='1000' osd_halignment='center'>Changed to mode 1</message>"

end

```

My lircd.conf
```
begin remote

  name  lircd.conf
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   24
  pre_data       0x800100
  gap          132990
  toggle_bit_mask 0x800100A4

      begin codes
          NEXT                     0xA3
          PREV                     0xA5
          PLUS                     0x73
          MINUS                    0x72
          PLAY                     0xA4
          MENU                     0x8B
      end codes

end remote
```

My hardware.conf
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event1"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

```

I still haven't tried more than 2 modes.

To have the notifications you'd have to install gnome-osd and add irexec to the gnome session startup daemons.

Let me know if something doesn't makes sense. :)

---

### Post by stueng on 2008-05-21
> **Azathoth_ said:**
> Open a terminal and try this:
killall irxevent
killall irexec

Now in this terminal launch.
irxevent

Does this terminal wait? Or this terminal open this command and close it?

Now press + button of the apple remote. What happens?

I am having the same issue... I followed another post to get the remote to work with "out of the box" functionality i.e I could change volume and could control rythmbox but I couldnt use it for VLC or anything. For some reason even that basic functionality has stopped working so now I have followed your steps to try get it working. I followed your instructions but still nothing... when I try the above steps irxevent the terminal just waits, pressing buttons on the remote does nothing

Stu

---

### Post by freeedom on 2008-06-07
I am having the same big issue here. on a macbook pro core duo running ubuntu 8.04

So far I tried every possible how-to I found, from the macbook pro documentation at the ubuntu wiki, from this thread and other older ones which weren't that helpful at all.
I tried several times to only read any input with the ifw program, which by default should show something.
a ps in terminal showed, that lircd and inputlirc are running while watching /dev/input/event1 to 9.

and now I am out of any ideas what to try next. ah something funny: in the apple remote lircd.conf file which was shipped with lirc, there are actually two definitions if I understood right. but even substituting all my configurations with the ones a few posts before didn't work. and the batteries surely work, tested in leopard with itunes.

so many people got it easily working ...

thanks in advance for any suggestions.
cheers,

freedom

PS: and be aware, that the lircrc file attached in the macbook pro/ubuntu documentation was formatted with DOS line endings, which confuses irxevent because it expects the UNIX style.

---

### Post by cyberdork33 on 2008-06-08
please use the new apple forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

