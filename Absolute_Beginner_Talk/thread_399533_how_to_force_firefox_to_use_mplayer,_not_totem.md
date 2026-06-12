---
title: "how to force firefox to use mplayer, not totem?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by jexdawg13 on 2007-04-02
i just want to watch movies in firefox.

totem sucks and i hate it. it won't work in firefox (or swiftfox in my case... but it won't work in firefox either).

what i've done:

removed totem-mozilla via synaptic, as well as rm'd it in terminal, as well as rm'd and purged it in terminal. i've prayed to some norse gods in the offchance that that might help too. i've done everything in my power to kill totem. die totem, die.

i've installed mozilla-mplayer and mplayer via synaptic, via terminal, reconfigured them via terminal, and prayed to zues. i haven't been struck down by lightning yet, so i assume zues is working on it.

i've also removed all the applicable xine, libxine, and gstreamer packages. 


WHY DOES FIREFOX CONTINUE TO HATE ME?

about:-plugins (i had to include the dash so it didn't look like about:plugins) says: 
```
Totem Web Browser Plugin 2.16.2

    File name: libtotem-basic-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

```

i've also manually gone into /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins and /usr/lib/mozilla-firefox/plugins and deleted all totem related stuff in there. all thats left is mplayer files....

what else do i need to do? why won't firefox just cooperate? i just need to force it to use mplayer instead of crap-*** totem.

also, why does ubuntu use totem over mplayer anyways? totem sucks. mplayer doesn't. dig? (and that was only half-complaining, i am genuinely interested in why ubuntu chooses totem over other, imo better apps).

please help. i just want to watch some freaking por--err videos in swiftfox. make it stop hating me. :(

also, here is a guitar playing smiley... because i want it here: :guitar:

---

### Post by srt4play on 2007-04-02
Looks like you've taken all of the steps I take to get rid of totem, plus some extra.  I never have to go in and manually delete stuff.   Search for totem in synaptic, uninstall everything with totem in the name, install mozilla-mplayer.  That always works for me.  Here's a suggestion, look in the '.mozilla/plugins'  directory in your home to see if that totem plugin is hiding in there.

Also, you probably already know but you have to restart firefox to reread the plugins directories.  Also something you probably already know, if you don't see that totem plugin in the directory I mentioned above,  do 'sudo updatedb' and then 'locate libtotem-basic-plugin.so'  to see where it is.

---

### Post by kirtap on 2007-04-02
I had the same problem as you, totem wasn't working in firefox. I searched synaptic for totem and removed only totem-mozilla. Then I installed mozilla-mplayer. 

Now mplayer works in-browser. I wonder if by doing all the manual removals if you've removed something you needed? Try checking synaptic again and make sure you've got all the totem stuff uninstalled and all the mplayer installed. Good luck.

---

### Post by kerry_s on 2007-04-02
You can grab the media connectivity extension and set it up to open exactly what you want to use. I only use vlc. [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by jexdawg13 on 2007-04-02
> **srt4play said:**
> Looks like you've taken all of the steps I take to get rid of totem, plus some extra.  I never have to go in and manually delete stuff.   Search for totem in synaptic, uninstall everything with totem in the name, install mozilla-mplayer.  That always works for me.  Here's a suggestion, look in the '.mozilla/plugins'  directory in your home to see if that totem plugin is hiding in there.

Also, you probably already know but you have to restart firefox to reread the plugins directories.  Also something you probably already know, if you don't see that totem plugin in the directory I mentioned above,  do 'sudo updatedb' and then 'locate libtotem-basic-plugin.so'  to see where it is.


i did the "do 'sudo updatedb' and then 'locate libtotem-basic-plugin.so' to see where it is." part and deleted it. works beautifully now!

wooooo thanks for your help everyone

---

### Post by mikesmith36 on 2007-04-02
> **kerry_s said:**
> You can grab the media connectivity extension and set it up to open exactly what you want to use. I only use vlc. [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Thanks very much for this - virtually the only little niggle I had with Ubuntu now resolved, goodbye windows!:lolflag:

---

