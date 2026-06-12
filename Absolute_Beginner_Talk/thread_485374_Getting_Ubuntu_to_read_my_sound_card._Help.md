---
title: "Getting Ubuntu to read my sound card. Help?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Dysan on 2007-06-26
I've been following the thread [here](https://help.ubuntu.com/community/HdaIntelSoundHowto) which tells me how to get Ubuntu to read my integrated sound card. Well, I didn't realize it said "integrated" until just now, so I guess I'll stop what I'm doing here and ask something different (lol):

How do I get my Creative Sound Blaster Audigy SE to work on Ubuntu?

---

### Post by abn91c on 2007-06-26
in a terminal type alsamixer to check if linux finds it. If there it may be just a matter of playing with the settings there

---

### Post by inuyokai on 2007-06-28
What type of sound card do you have?

I have a Sound Blaster Audigy and I had a similar problem; not where Kubuntu wouldn't detect it, just where it wouldn't work.

Things you may try before you take any install actions are:

1, K Menu (or the Gnome Menu) -> Systems And Settings -> Sound System -> Be sure "enable the sound system" is checked -> click the hardware tab -> set the "audio device" to Auto Detect" -> See if your sound card is listed under the "select the MIDI device" option.
2. K/Gnome Menu -> Multimedia -> Kmix or GnomeALSA Mixer -> See if you can choose your sound card from the dropdown menu on the upper right / on the "switches" tab try unchecking the tab that says something about Analog/Digit (for instance mine says Audigy/Analog/Digit).

You might try the following in the Terminal as well:

```
asoundconf list
```

if you see your sound card in the list then try:

```
asoundconf set-default-card yourcardname
```

If neither of those work, I saw somewhere around the forums that you need to download libasound2.deb. I think you can get it from [http://www.alsa-project.org](http://www.alsa-project.org)

---

### Post by Anarchy965 on 2007-06-28
What do you mean by the "Gnome menu"? I think this could help with my problem too.

---

### Post by timmahhny on 2007-06-29
inuyokai
> You might try the following in the Terminal as well:

Code:
asoundconf list
if you see your sound card in the list then try:

Code:
asoundconf set-default-card yourcardname
 
 I had the same problem with my Audigy which worked fine, until a while ago.
Ran the code you posted and it solved the problem.
Thanks a bunch
Timmahhny

---

### Post by inuyokai on 2007-07-02
Gnome menu... Umm... I was in Gnome today, I think its like  whatever the menu option is on the left. I cant stand Gnome so I'm not entirely sure.

I am, however, almost positive that your problem is the same as everyone elses who has an Audigy.

Here is how I've gotten it to work a few times now.

Open Terminal

```
asoundconf list
```

This lists the cards installed on your computer - most likely your card is called Audigy (I have an SB Audigy and thats what mine is called).

Next

```
asoundconf set-default-card Audigy
```

If your card is not called Audigy then replace "Audigy" with the name of your card found in asoundconf list.

Then

```
alsamixer
``` or ```
sudo alsamixer
``` if for some reason you need to run as root

The card name should show up at the top so if it doesnt say your card name next to "Card:" you haven't done something right.

Now, scroll all the way over (using the right arrow key) to Audigy M - where it says "Item:" it should say "Audigy Analog/Digital Output Jack" - and press 'm' to turn it off. 

For some reason the Analog/Digital Output Jack causes the sound not to work. Go into whatever sound mixer your using and make sure your settings are in line with what you just did. If your sound did not turn on right after closing alsamixer then restart X Window by pressing ctrl-alt-backspace.

Hope that helps man. It sucks without sound.  And like I told a guy in another post, I think sound is random in (K)ubuntu.

On another note, if you're having problems in Gnome; switch to KDE. Its a lot easier and more customizable, in my opinion.

---

### Post by inuyokai on 2007-07-02
> **timmahhny said:**
> inuyokai

 
 I had the same problem with my Audigy which worked fine, until a while ago.
Ran the code you posted and it solved the problem.
Thanks a bunch
Timmahhny

Glad it worked for you! I hated being without sound.

---

