---
title: "Sound on Ibook G4"
date: 2005-02-09
forum: Apple PPC Users
---

### Post by Pineault on 2005-02-09
Upgraded to Hoary, can't figure out how to get sound working right, ie like it worked on  warty,

 sound keys don't work, volume control app doesn't start, crashes on start, gnome volume control applet is always on mute by default, and Xmms sounds like coming out of tin can and crashes, can't seem to sync the appropriate sound driver in Xmms, ie also, Oss, esound with the choice of driver in gnome applet, anyone has an ibook G4 where all this is organized adequately, pelase give me a hand

It all worked on warty...

---

### Post by toojays on 2005-02-10
I have Hoary installed on my iBook G4 and sound is fine. I didn't have Warty though, and I don't have much experience with Ubuntu (although I have a lot with GNU/Linux).

The sound driver I have loaded in my /etc/modules is snd-powermac.
```
toojays@fuzz:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Feb  7 2005 for kernel 2.6.10-3-powerpc.
toojays@fuzz:~$ cat /proc/asound/cards
0 [Snapper        ]: PMac Snapper - PowerMac Snapper
                     PowerMac Snapper (Dev 38) Sub-frame 0

```
Any other info I could give you?

---

### Post by Pineault on 2005-02-12
[QUOTE=toojays]I have Hoary installed on my iBook G4 and sound is fine. I didn't have Warty though, and I don't have much experience with Ubuntu (although I have a lot with GNU/Linux).

The sound driver I have loaded in my /etc/modules is snd-powermac.
```
toojays@fuzz:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Feb  7 2005 for kernel 2.6.10-3-powerpc.
toojays@fuzz:~$ cat /proc/asound/cards
0 [Snapper        ]: PMac Snapper - PowerMac Snapper
                     PowerMac Snapper (Dev 38) Sub-frame 0

```
Any other info I could give you?[/QUOTE]

Thanks for the reply
Exact same config as me, which driver have you chosen for xmms, and which one with the volume applet, I've got both on alsa, I've disabled system sound events, and my buttons set up with warty are still configured but don't work...

---

### Post by toojays on 2005-02-13
In the Gnome volume applet it is set to OSS. I don't use Xine, but Rhythmbox works fine. I believe some of the other apps go through esd.

---

### Post by Pineault on 2005-02-15
[QUOTE=toojays]In the Gnome volume applet it is set to OSS. I don't use Xine, but Rhythmbox works fine. I believe some of the other apps go through esd.[/QUOTE]

Well did that, put xmms on esound and reset the volume biitons, sound still below what it was on warty, but acceptable (barely).

thanks

---

