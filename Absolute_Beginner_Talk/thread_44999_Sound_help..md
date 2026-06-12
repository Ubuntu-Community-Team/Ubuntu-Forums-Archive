---
title: "Sound help."
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by Cerbz on 2005-06-28
I've got xmms installed, and i try to play mp3's, but i get nothing, i have switched the sound plug in to alsa in the xmms menu so it doesnt hang. I have figured out how to get the sound working at last (thanks to Kimm for the killall esd) but after i reboot it goes back to how it was, is there anyway i can keep the killall esd setting? Bear in mind i am utter newb. thanks :P

---

### Post by AntiDragon on 2005-06-28
I had sound problems too after my install but there was a real simple fix. What sound card do you have?

---

### Post by Cerbz on 2005-06-28
[QUOTE=AntiDragon]I had sound problems too after my install but there was a real simple fix. What sound card do you have?[/QUOTE]
 I hav an intel 82801DB-ICH4

---

### Post by AntiDragon on 2005-06-28
Sorry my bad - it's not the sound card. I believ you need an extra plugin for XMMS to play MP3s. Try using Synaptic and search for xmms-mp3 and install that.

---

### Post by Cerbz on 2005-06-28
[QUOTE=AntiDragon]Sorry my bad - it's not the sound card. I believ you need an extra plugin for XMMS to play MP3s. Try using Synaptic and search for xmms-mp3 and install that.[/QUOTE]
 No i can play them.. by typing killall esd into the terminal, but i have to do that everytime i log into my account. Sorry maybe i didnt type clearly enough :-/

---

### Post by AntiDragon on 2005-06-28
Ah, gotcha. A bit more reasearch....

ESD is a sound mixer - let's programs play sound indendently and then mixes them into a single sound source that is sends to your sound card. If you kill it, you can still play sound but only one program at a time can do so - i.e if you play MP3s you won't hear any system sounds and vice versa.

So what to do? Top of my head, I don't know, save having "killall esd" scripted so that it runs automatically at each start, but that's just a workaround.  I can't check right now but maybe there's a later version of ESD available? ([ESD page](http://www.tux.org/~ricdude/download.html) )

Honestly, I think someone else will have to help here (I'm still too new  :-? ) although you might want to take a look [here](http://www.ubuntuforums.org/showthread.php?t=44753) as this thread outlines an "harmonious" setup.

Note:  The thread above is a little heavy and could have some unforseen consequences from the look of it - be careful!

---

### Post by AntiDragon on 2005-06-28
Have you checked out [this](http://ubuntuguide.org/#configuresoundproperly) ?

---

### Post by Cerbz on 2005-06-28
[QUOTE=AntiDragon]Have you checked out [this](http://ubuntuguide.org/#configuresoundproperly) ?[/QUOTE]
 I have read that post, before the post you posted and it seems confusing and im kinda newby so i dont know if i should try it as i dont wanna mess everything up..and alright i will check the link you just gave me and report back if i have managed to fix it or not, thanks for your help!



EDIT: And thanks again for showing that link as i now have it fixed and my mp3 support loads up on startup, cheers dude you've been a great help  :grin:

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=Cerbz]No i can play them.. by typing killall esd into the terminal, but i have to do that everytime i log into my account. Sorry maybe i didnt type clearly enough :-/[/QUOTE]


Thats a bug. The biggest bug in Ubuntu right now. The real solution is to wait for it to be fixed in the next release.

---

### Post by Cerbz on 2005-06-28
[QUOTE=poofyhairguy]Thats a bug. The biggest bug in Ubuntu right now. The real solution is to wait for it to be fixed in the next release.[/QUOTE]
 Ah I see.. It only took a few seconds to fix. So im glad its done. These forums are uber helpfull ^_^

---

### Post by AntiDragon on 2005-06-28
Woohoo! I actually helped someone with Linux....Ha! \\:D/

---

### Post by andlinux21 on 2005-06-29
ok I have a question maybe you can help me i can get sound in gnome but how do i make it work in my other managers ie. xfce4, fluxbox, openbox, etc... it sucks to not have it just work period....

---

