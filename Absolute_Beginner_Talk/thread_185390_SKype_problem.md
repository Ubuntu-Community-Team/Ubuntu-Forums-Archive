---
title: "SKype problem"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by newhen on 2006-05-31
Hi, its me again the total noob at linux. I have a problem when useing skype:


**the Problem : okay well first of lets me tell you some info about my comp I have gatwayfpd1520 with ubuntu breezy on it ( i think mybe dapper) I have skype and I use a sound blaster live card. _okay so When I Try to call somebody on skype I get this error message"problem with sound device" my sound and mic work but whats up with this???? If anybody know that would make my day:KS _**




EVIL SKYPE:evil:

---

### Post by newhen on 2006-05-31
Bump

---

### Post by newhen on 2006-05-31
Bump

---

### Post by gbinal on 2006-06-02
I'm having the same problem and can't figure it out.  Did you have any luck?  

Thanks.

---

### Post by piggyaugu on 2006-06-03
[QUOTE=newhen]Hi, its me again the total noob at linux. I have a problem when useing skype:


**the Problem : okay well first of lets me tell you some info about my comp I have gatwayfpd1520 with ubuntu breezy on it ( i think mybe dapper) I have skype and I use a sound blaster live card. _okay so When I Try to call somebody on skype I get this error message"problem with sound device" my sound and mic work but whats up with this???? If anybody know that would make my day:KS _**




EVIL SKYPE:evil:[/QUOTE]


Try disable ESD in Preferences->Sound.

---

### Post by padre999 on 2006-06-04
I had the same problem. I discovered that amarok and skype don't like each other so much. On my system at least. 
When I start amarok first and then skype, I can't make calls (get the error described above). When I start skype first I can't listen to music with amarok. It just races through the playlist without playing anything.

So. Turn of all sound/multimedia apps and try again with skype...

Kubuntu Dapper, KDE 3.5.3, Amarok 1.4 Beta

---

### Post by wieman01 on 2006-06-07
Hello, 

It seems I had the same problem... my sound device would not work after the first call. There are currently two solutions to work around this problem:

a) Find Skype's sound directory and delete or rename hangup.wav file.
cd /usr/share/skype/sound
mv hangup.wav hangup.wav-disabled

b) skype_dsp_hijacker from version 0.5 implements workaround to catch situation that leads to lockup, and workaround it.

A detailed instruction can be found here: [http://juljas.net/linux/skype/](http://juljas.net/linux/skype/)

Removing the hang-up file did it for me.

---

### Post by dmizer on 2006-06-07
this is for breezy, but it still should be relevant:
[http://www.ubuntuforums.org/showthread.php?t=121756&highlight=howto+skype](http://www.ubuntuforums.org/showthread.php?t=121756&highlight=howto+skype)

it includes the above mentioned skyp hyjacker among many other good tips on making skype work correctly.

---

### Post by padre999 on 2006-06-11
[QUOTE=wieman01]Hello, 

It seems I had the same problem... my sound device would not work after the first call. There are currently two solutions to work around this problem:
[/QUOTE]
No. That is a different problem. At least from the one I have... The error message you describe I know too. But I also got the same message when I tried to make the first call.

As described above a problem with ubuntu not allowing several applications too use the soundcard at the same time...

---

