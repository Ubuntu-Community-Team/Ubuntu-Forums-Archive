---
title: "[SOLVED] XMMS probs"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Shadyjames on 2007-12-28
For a few sessions i was using XMMS to play my music without any troubles, but now it skips every song (not all at once, it goes to each song and then doesn't play it individually). The only thing thats changed imbetween now and then is i got my dual monitor setup working (finally =D)

Thanks in advance for the help, once this is fixed i'll be ready to use ubuntu for something other than character growth  ](*,)
And i can't wait :D

Update for those just joining us, both xmms and audacious will only play if they use a playlist that was created that session. IE i reboot and it breaks again. Still unsolved :P

---

### Post by Perfect Storm on 2007-12-28
Xmms is obsolite and havn't been maintained for years. Try something like audacious instead.

[http://audacious-media-player.org/index.php?title=Main_Page](http://audacious-media-player.org/index.php?title=Main_Page)

It can be found in the repo, but if you want the latest, I wrote this compiling guide: [http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html](http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html)

---

### Post by Seti on 2007-12-28
not really, I still like to use Xmms all the time.

---

### Post by disturbedite on 2007-12-28
i was gonna mention audacious too.

and bah!  xmms is a dead dinosaur.  audacious is king!  its much more modern and has better features.

---

### Post by DirtDawg on 2007-12-28
I use an updated version of XMMS called Beep. In the repos under beep-media-player.

---

### Post by Seti on 2007-12-28
Yeah I've toyed around with Audacious, and still have my reasons for preferring Xmms. 
besides;

[http://www.xmms.org/](http://www.xmms.org/)

:guitar:

---

### Post by Perfect Storm on 2007-12-28
Can you elaborate why?

---

### Post by Seti on 2007-12-28
partly force of habit, and Audacious seems kind of choppy as far as it integrates into my desktop, particularly if I resize the playlist. I'm not denying its a nice program otherwise. 
Also with xmms I use xmms-crossfade, which I like.

Show me where Audacious outperforms Xmms. I'm not doubting you, but tell me.

---

### Post by Perfect Storm on 2007-12-28
The interface is better on Audacious - also gtk2 supported. Still get attention, fixes and features by its devs.

speed wise it's the same for xmms and audacious on my computer.

---

### Post by Seti on 2007-12-28
true enough. I'll have to find the crossfade plugin for it; I like 'gapless'.

---

### Post by Perfect Storm on 2007-12-28
If there's something that you're missing on audacious there direct contact to the devs here:
forum: [http://boards.nenolod.net/](http://boards.nenolod.net/)
IRC: irc://irc.atheme-project.org/audacious
Mailing list: [http://mail.atheme-project.org/mailman/listinfo/audacious](http://mail.atheme-project.org/mailman/listinfo/audacious)

---

### Post by Seti on 2007-12-28
well I copied crossfade.so after reading Audacious supports the xmms-crossfade plugin.

```
sudo cp /usr/lib/xmms/Output/libcrossfade.so .
```

restarted Audacious but still can't find the crossfade plugin in the Preferences. Perhaps there is a specific Audacious crossfade plugin I can just apt-get. But I'm too tired and its WAY past my bedtime.
AND I've taken this thread WAY off-topic!!!:(

ciao 4 now

---

### Post by disturbedite on 2007-12-28
> **DirtDawg said:**
> I use an updated version of XMMS called Beep. In the repos under beep-media-player.
i thought beep media player was dead too?

---

### Post by DirtDawg on 2007-12-28
> **disturbedite said:**
> i thought beep media player was dead too?

Who knows, maybe it is.

---

### Post by Shadyjames on 2007-12-29
I've converted to audacious now simply on the grounds that xmms isn't working, but i do see seti's argument, because it takes more time for it to read my playlist after opening than xmms did, and it takes a little while to respond when i push a button. Hopefully i'll discover why everybody likes it so much and not NEED to fix this problem, but right now i'm curious. Nobody knows why xmms is doing this?
Un-edit-reedit-edit: I just needed to sudo xmms -_- its going to take a while to get used to the file system on ubuntu, glad i managed to spark an interesting debate though :)

---

### Post by alx010 on 2007-12-29
> **Artificial Intelligence said:**
> Xmms is obsolite and havn't been maintained for years. Try something like audacious instead.

[http://audacious-media-player.org/index.php?title=Main_Page](http://audacious-media-player.org/index.php?title=Main_Page)

It can be found in the repo, but if you want the latest, I wrote this compiling guide: [http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html](http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html)

Thanks for that 2nd link. I haven't been using Audacious because the default skins were terrible :p Now I have my favorite old Winamp skin installed, making it much easier to navigate \\:D/

---

### Post by disturbedite on 2007-12-29
> **Shadyjames said:**
> I've converted to audacious now simply on the grounds that xmms isn't working, but i do see seti's argument, because it takes more time for it to read my playlist after opening than xmms did, and it takes a little while to respond when i push a button.
i don't experience either of those things, so i think it might be a problem on your end...

---

### Post by Perfect Storm on 2007-12-29
> **alx010 said:**
> Thanks for that 2nd link. I haven't been using Audacious because the default skins were terrible :p Now I have my favorite old Winamp skin installed, making it much easier to navigate \\:D/

There's a new version of Audacious released yesterday. I have updated the guide. Just remember to uninstall the previous version first.

---

### Post by Shadyjames on 2007-12-29
Coincidence alert, it just so happened that the time i sudo'd it was the time i happened to re-create my playlist. Unless i create a new playlist every session it doesn't work, it won't use old ones. Maybe i should update the OP with this

OHMYGODIMSOSTUPID!!

um....

i didn't realise you had to mount your drives every time you started a session

never mind :(

---

### Post by war59312 on 2007-12-30
Well, anyone got the winamp presets working in Audacious? I try and import them but they still dont show up... Any thoughts?

Thanks!

---

### Post by Seti on 2007-12-31
Alright, I've got Audacious working pretty much like I want it to now, including having installed the correct crossfade plugin.
Where do I put more skins tho; I don't have a ~/.Audacious/ dir for settings?

---

### Post by disturbedite on 2007-12-31
> **Artificial Intelligence said:**
> There's a new version of Audacious released yesterday. I have updated the guide. Just remember to uninstall the previous version first.
i filed a bug for audacious & audacious-plugins to update them to the newest versions.

---

### Post by Perfect Storm on 2007-12-31
> **Seti said:**
> Alright, I've got Audacious working pretty much like I want it to now, including having installed the correct crossfade plugin.
Where do I put more skins tho; I don't have a ~/.Audacious/ dir for settings?

Skins go for /usr/local/share/audacious/Skins
I have a section in my guide that explain.

---

### Post by jackmccaskill on 2007-12-31
> **Artificial Intelligence said:**
> Xmms is obsolite and havn't been maintained for years. Try something like audacious instead.

[http://audacious-media-player.org/index.php?title=Main_Page](http://audacious-media-player.org/index.php?title=Main_Page)

It can be found in the repo, but if you want the latest, I wrote this compiling guide: [http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html](http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html)



Greeting AI,

    I am not sure if this is a legitimate way to contact you directly.  I am a new user but can not seem to get a really helpful reply to my questions either through "Absolute beginners Tals" or the "multimedia" forum.  thread name in both forums is "Without a Song".  With your experience perhapsw I can end my frustration.

     I have two major problems.  Having used Microsoft for many years, all my music files are in the WMA format and i can not find out if they can be played in linux at all or how to convert them to a format that linux will accept.

      I am also having an extremely frustrating time getting my printer to work.  I have gone through the set up procedure VERY carefully and even got to the "Print Test File"  the next screen up indicates the test document was sent to the printer , however no test page is not actually printed.

     Can you help with either or both?  It will be much appreciated and will probably save both my lap top and the window I am about ready to throw it through!

     If it makes any difference i am running ubuntu 6.10 updated with all updates through today.  the printer I am trying to connect to is a Dell all in one printer model 922

    Happy New Year.

---

### Post by Perfect Storm on 2007-12-31
So far as I know and read WMA can be played in linux. I havn't tried as I don't use the format but audacious have WMA plugin and I guess other media/music players can do it as well.

nautilus-script-audio-convert (in the repo) can convert format back and forth including WMA


Check and see if your printer is supported - you might getting a newer version of Ubuntu if it's not supported in the old version of Ubuntu you have.
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by disturbedite on 2008-01-01
> **war59312 said:**
> Well, anyone got the winamp presets working in Audacious? I try and import them but they still dont show up... Any thoughts?

Thanks!
thats one thing i never could get to work.  i tried the "official" instructions for "installing" them & i even tried other methods but they would never work.

---

### Post by war59312 on 2008-01-04
Yeah I've given up fo now then, sounds pefectly fine without them anyhow, thanks...

---

### Post by clickelliott on 2008-02-11
If you can't play WMA files with XMMS,
Here's how to play WMA files with XMMS:

DISABLE WMA plug-in

ENABLE mplayer plug-in.

Ba da bing, ba da boom.:guitar:

---

