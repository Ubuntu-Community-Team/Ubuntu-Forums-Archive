---
title: "Sound control is different depending on remote or keyboard"
date: 2008-06-19
forum: Apple Hardware Users
---

### Post by Zaff on 2008-06-19
So I've reinstalled hardy and everything works from the remote to the isight and all is well.
Just one thing that I wonder and find weird, if I change the volume using the F5 or F4 keys the "jump" will be larger than if I use the remote keys.
Basically if I go from 0 to max with F5 it only take about 7 strokes whereas with the remote it takes about 17.
Now I'd much rather the keyboard keys to act as the remote as this is more precise. I just do't understand why it does this since it seems the key code for F5 and the up touch on the remote is the same.
Any clues ?

---

### Post by cyberdork33 on 2008-06-19
> **Zaff said:**
> So I've reinstalled hardy and everything works from the remote to the isight and all is well.
Just one thing that I wonder and find weird, if I change the volume using the F5 or F4 keys the "jump" will be larger than if I use the remote keys.
Basically if I go from 0 to max with F5 it only take about 7 strokes whereas with the remote it takes about 17.
Now I'd much rather the keyboard keys to act as the remote as this is more precise. I just do't understand why it does this since it seems the key code for F5 and the up touch on the remote is the same.
Any clues ?
are you sure they are both adjusting the same channel?

---

### Post by Zaff on 2008-06-20
> **cyberdork33 said:**
> are you sure they are both adjusting the same channel?
Yep, the PCM Channel to be exact. I made sure the remote or keyboard wasn't adjusting an other channel on top of PCM but it doesn't.
And again, the keycode is the same, whether it's the remote or the keyboard keys, for those volume keys. It's extremely weird...

---

### Post by cyberdork33 on 2008-06-20
well, I'd have a look into the remote configuration (wherever that is) and see if there is anything to note, but I think you've stumped me... Maybe the keyboard is sending a separate signal for both press and release or something, but I kind of doubt that is the case... Strange indeed.

EDIT: OK, I did some looking, and thought of something else. Your keyboard inputs are processed by Gnome, and gnome is likely sending the volume change signal. There might be a way to adjust this parameter, but I don't know where. I did find some information on rebinding keys in gnome that might be useful. and if it doesn't work, just deleting the config file from your home directory should revert to normal:
[http://ubuntuforums.org/showthread.php?t=79717](http://ubuntuforums.org/showthread.php?t=79717)

EDIT AGAIN: I found how in KDE! :-?
[http://ubuntuforums.org/showthread.php?t=428844](http://ubuntuforums.org/showthread.php?t=428844)

LAST EDIT:
There is not a lot of info on this, but a few people have asked about it. Last thing I can offer is to check in System->Preferences->Keyboard Shortcuts->Sound

---

### Post by Zaff on 2008-06-20
> **cyberdork33 said:**
> well, I'd have a look into the remote configuration (wherever that is) and see if there is anything to note, but I think you've stumped me...
Ah ah, I didn't think such a thing could be possible. :P

>  Maybe the keyboard is sending a separate signal for both press and release or something, but I kind of doubt that is the case... Strange indeed.

Nope, the volume changes on press only. release does nothing. In fact if I stay pressed the "jumps" are as big as if I type several times (if that makes any sense.

> 
EDIT: OK, I did some looking, and thought of something else. Your keyboard inputs are processed by Gnome, and gnome is likely sending the volume change signal. There might be a way to adjust this parameter, but I don't know where. I did find some information on rebinding keys in gnome that might be useful. and if it doesn't work, just deleting the config file from your home directory should revert to normal:
[http://ubuntuforums.org/showthread.php?t=79717](http://ubuntuforums.org/showthread.php?t=79717)

I don't know what normal is though, it's always been like this ...
one thing's changed though, I used to have a sound signal indicating the level of the volume (everytime I pressed F5 it would be louder and increasing with the sound level like in mac osx and softer with F4) and this didn't happen with the remote. It's not doing it anymore though, don't know why.
I'll look this link up when I have time.

> 
EDIT AGAIN: I found how in KDE! :-?
[http://ubuntuforums.org/showthread.php?t=428844](http://ubuntuforums.org/showthread.php?t=428844)


Good for Kubuntu users :P

> 
LAST EDIT:
There is not a lot of info on this, but a few people have asked about it. Last thing I can offer is to check in System->Preferences->Keyboard Shortcuts->Sound
Been there done that, I tried to set them with the remote keys, the keyboards keys and so forth, didn't change anything, the keycode is the same from one to the other.
Ah well, no biggie I use the remote most of the time anyway. I'd be interested in knowing where you've read about this though.

---

### Post by cyberdork33 on 2008-06-20
> **Zaff said:**
> I'd be interested in knowing where you've read about this though.
Most of the information I could find was from searching "keyboard volume increment" in the forums.

---

### Post by Zaff on 2008-07-03
Ok so here's a small update on the issue, I still don't know why, but here's what I've gathered :
The F5 and F4 buttons change the volume of both the Master Channel and the PCM Channel
The F3 button mutes the Master Channel and the Front Channel, however when pressed a second times, only the Master channel is unmuted, the Front channel remains muted.
The Infrared Remote volume control only changes the volume of the Master Channel.
So this makes less and less sense now. I don't understand why two keys with the same code would do something different.
I have keytouch installed and am looking into the possibility that the problem might be coming from there. I'll keep you updated.
Thanks

---

### Post by Zaff on 2008-07-17
okay so keytouch is not the problem.
So I've toyed with the System -> Preferences -> Sound dialog and here's what I get basically : 
If I select PCM as the device to control, the remote and the F5 / F4 keys only control PCM but, as was originally the proble, the F4 and F5 keys make the volume change more important than the remote (which is rather annoying).
If I select Master as the device (which would be the best really as I don't really want the PCM to move anyway) the remote controle the Master only but the F5 and F4 control both PCM and Master channel, which is equally annoying but it appears that in that case, the PCM volume will increase and decrease in lesser amounts, like when it was previously controlled by the remote.

Still with me here ? :P
So anyway, I don't know why it's doing this and I'm just gonna use the remote fromnow on, I just really would like it if I could have the same volume control between the two.
Ah well... Not really the biggest issue ever I guess.

---

### Post by Zaff on 2008-07-18
I have made some progress:
It turns out that if I go into System -> Preferences -> Keyboard Shortcuts and I disable the Volume up and the volume down actions, the remote doesn't work anymore (which is expected) BUT the F5 and F4 keys still modify the PCM channel (and only that one, regardless of what is set in the Sound dialog).
So I'm guessing there's a mapping somewhere for those keys that is not related to Gnome, but I haven't found it yet.
If anyone's got a clue, I'm all ears :)

---

