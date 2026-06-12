---
title: "Trouble Player"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by mishranurag on 2005-12-13
I am trying to make real player 10 work and I searched lots of forums and it appears like there is no perfect, standard and genuine solution for making real player work properly. 
my real player plugin doesn't work, and if I  use real player to play any music, it behaves so slowly that it frsutrates. 
Is there any standard solution?? 

Anurag

---

### Post by mishranurag on 2005-12-15
My browser is showing following info about plugins. How can I make firefox use RealPlayer for realplayer streams??
Anurag
RealPlayer 9
 File name:  mplayerplug-in-rm.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 3.05

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    audio/x-pn-realaudio RealAudio ram,rm Yes   audio/x-realaudio RealAudio ra Yes   audio/x-pn-realaudio-plugin RealAudio rpm Yes   application/smil SMIL smil Yes

---

### Post by kaamos on 2005-12-15
This worked perfectly for me [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer)

---

### Post by mishranurag on 2005-12-16
Thanks!
But that don't seem to work for me. Do I need to remove the installed version,I have?? If yeas, how can I do that?
Anurag

[quote=kaamos]This worked perfectly for me [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer")[/quote]

---

### Post by Mustard on 2005-12-16
Try installing mozplugger through synaptic and see if that helps with getting realplayer and other stuff to play within firefox.

Btw, 'doesn't seem to work' is a bit vague.  It would be better to describe what actions you took to attempt to use it and what the results where and any error messages that might have occured.

---

### Post by mishranurag on 2005-12-17
Hi!

I have following issues with RealPlayer10
1. When I try to navigate Realplayer to files in other media (windows drive), it never identifiess those drives. Although Rhythmbox and Totem play those files without trouble.
2. When I play certain file with Realplayer, it behaves real sluggish. It becomes difficult to move volume tab and do other stuff.
3. I cannot play streaming music. You can try [www.raaga.com](www.raaga.com), the player keeps on saying loading and does nothing.
4. I installed mozplugger, where can I locate it to run it?

Thanx
Anurag


[quote=Mustard]Try installing mozplugger through synaptic and see if that helps with getting realplayer and other stuff to play within firefox.

Btw, 'doesn't seem to work' is a bit vague.  It would be better to describe what actions you took to attempt to use it and what the results where and any error messages that might have occured.[/quote]

---

### Post by sunny_nwho on 2005-12-27
there is not need to explicitly run mozplugger anurag but it should work automatically...by the way did u delete the plugin.dat from ur firefox folder after u install mozplugger...and to remove realplayer did u try using synaptic...ory try sudo apt-get remove realplayer

Santhosh (sunny)

---

### Post by mishranurag on 2006-01-10
Hey Santosh,

 I haven't tried your suggestions yet, as I was not well till now and will try very soon. This real player issue will make me stop using Ubuntu. I have started hating real player. Why don we have a simple solution.:mad: Everybody in the world has problem with it   .
Could you please explain your instructions systematically once again?
Thanks and Happy new Year.

Anurag

[quote=sunny_nwho]there is not need to explicitly run mozplugger anurag but it should work automatically...by the way did u delete the plugin.dat from ur firefox folder after u install mozplugger...and to remove realplayer did u try using synaptic...ory try sudo apt-get remove realplayer

Santhosh (sunny)[/quote]

---

### Post by sunny_nwho on 2006-01-14
Hi anurag....if u have installed mozplugger then there is no need to start it it will start automatically but before starting it u must remove plugins.dat file from ~/.firefox or ~/.mozilla-firefox/plugins depending on ur installation.....and  for removing realplayer u can type the command sudo apt-get --purge remove realplay(er) it shud do the job...yes even i have not found a way to get songs playing from raaga but i can from music india online not in the straight way but a loop if u r instersted i can tell u....sorry 4 the late reply...happy new year to u too yaar...Sunny

---

### Post by gshresth on 2007-07-06
> **sunny_nwho said:**
> Hi anurag....if u have installed mozplugger then there is no need to start it it will start automatically but before starting it u must remove plugins.dat file from ~/.firefox or ~/.mozilla-firefox/plugins depending on ur installation.....and  for removing realplayer u can type the command sudo apt-get --purge remove realplay(er) it shud do the job...yes even i have not found a way to get songs playing from raaga but i can from music india online not in the straight way but a loop if u r instersted i can tell u....sorry 4 the late reply...happy new year to u too yaar...Sunny

Hey Sunny, COULD you put up a guide on how you got Music India to work under Ubuntu...?  I've tried pretty much everything without success!

Gaurav

---

### Post by twiceasworn on 2007-07-06
Boy talk about thread resurrection...

---

