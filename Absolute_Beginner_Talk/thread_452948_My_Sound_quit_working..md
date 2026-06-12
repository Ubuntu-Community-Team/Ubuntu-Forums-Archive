---
title: "My Sound quit working."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-05-23
My sound has worked fine previously up until just 3 minutes ago.
My computer mini-rebooted (meaning it logged off and took me back to the login screen) for no reason, I logged back in, and i quickly noticed the x over my volume control.

I clicked on it, and here is the message I receive:
> No Volume Control Gstreamer Plugins and/or devices found.

I go to an ogg vorbis on my computer, and I get this error:
> Totem could not play 'file:///home/drsmall/My Music/where should i go.ogg'.
This is an audio-only file, and there is no audio output available.

Does anyone have any ideas of what I could do to get my sound back?
It was just previously working 10 minutes ago, and then it has quit!
I have no idea what to do, and I would really like to have my sound back.

Dr Small

---

### Post by IainT on 2007-05-23
First and simplest thought is to reboot the computer. I've got a strange little sound issue going on, not the same thing, that sorts itself out after a reboot. Can't hurt to try.

---

### Post by Dr Small on 2007-05-23
Ok. Rebooted, same thing, but I know the sound DOES work.
When at the login screen, I've got some little sound, and it played that.
So, my sound DOES work, but when it loggs in, it doesn't want to play anything.

Could it be a permissions problem? Because I have just recently been messing around with different folder permissions (although I really don't see it revelant since I was just changing permissions on folders in /opt/ and stuff).

But, since that was the last thing that I did, right before it mini-booted, I have it to question.

Dr Small

---

### Post by Dr Small on 2007-05-23
Hello, Since I have not received any answer for the last 30 minutes, I'll write in an update.
I opened totem as root (gksudo totem), opened a song, and it played. So it must be a permissions problem.

Any help regarding this subject would be appreciated!

Dr Small

---

### Post by icechen1 on 2007-05-23
> **Dr Small said:**
> Ok. Rebooted, same thing, but I know the sound DOES work.
When at the login screen, I've got some little sound, and it played that.
So, my sound DOES work, but when it loggs in, it doesn't want to play anything.

Could it be a permissions problem? Because I have just recently been messing around with different folder permissions (although I really don't see it revelant since I was just changing permissions on folders in /opt/ and stuff).

But, since that was the last thing that I did, right before it mini-booted, I have it to question.

Dr Small

Post the output of
```
 /etc/init.d/alsasound status

```
and are you in audio group?
do
 ```
cat /etc/group | grep audio
```
and is your username in it?

---

### Post by Dr Small on 2007-05-23
> drsmall@drsmall:~$ /etc/init.d/alsasound status
bash: /etc/init.d/alsasound: No such file or directory


And honestly, I have no idea if I am in an audio group.
Any ideas how to check that out, or put myself in it, if I am not?

Dr Small

---

### Post by icechen1 on 2007-05-23
> **Dr Small said:**
> And honestly, I have no idea if I am in an audio group.
Any ideas how to check that out, or put myself in it, if I am not?

Dr Small

in a terminal tape:
[HTML]cat /etc/group | grep audio[/HTML]
it will say something like audio  : x: 29:icechen1
 if not you are not in audio group

---

### Post by icechen1 on 2007-05-23
maybe you accidentally uninstalled ALSA? you get:
[HTML]drsmall@drsmall:~$ /etc/init.d/alsasound status
bash: /etc/init.d/alsasound: No such file or directory[/HTML]
but you should get 
```
icechen1@icechen1-laptop:~$  /etc/init.d/alsasound status
ALSA sound driver loaded.

```

---

### Post by Dr Small on 2007-05-23
I found out how to go and add myself to the audio group, from under the system menu, I rebooted, my volume control is back, it played the sound at the splash screen (when booting gnome), but it won't play any other audio files such as ogg vorbis, mp3 or whatnot. I have no sound....

Dr Small

---

### Post by Cattie on 2007-05-23
If you get the uninstalled-alsa message in your terminal, how do you fix it?  I should have Alsa on, but it'[s showing as uninstalled.

---

