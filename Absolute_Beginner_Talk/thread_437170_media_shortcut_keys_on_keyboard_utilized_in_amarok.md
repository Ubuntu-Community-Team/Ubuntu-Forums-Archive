---
title: "media shortcut keys on keyboard utilized in amarok"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-05-08
[on ubuntu 7.04]

firstly, i have to make it clear that my media keys on my keyboard work normally in rhythmbox, with no setting up.

However, I want to use them in amarok, and so go to global shortcuts, and add the usual as secondary keys.

they come up as wierd things:

play/pause: XF86AudioPause
stop: XF86AudioStop

(etc).

I then press ok, and i try the media keys, but it does not do anything.

Any ideas?



Thanks in advance ;)

---

### Post by moredhel on 2007-05-08
bump?

---

### Post by moredhel on 2007-05-08
anyone?

---

### Post by orb9220 on 2007-05-08
> they come up as wierd things:

play/pause: XF86AudioPause
stop: XF86AudioStop


Those are the keys for multimedia. They use to work 

Are you using beryl?
Beryl takes over the keyboard shortcuts.

Haven't found a solution yet.

---

### Post by moredhel on 2007-05-08
beryl... mmm... stable :P

No, i'm not after too many crashes xD

especially after finding some simply beautiful gnome themes on deviantart ;)

---

### Post by moredhel on 2007-05-08
anyone?

is this a bug in amarok, like no media keys work at all?

---

### Post by moredhel on 2007-05-08
last call?

---

### Post by BrowneR on 2007-06-22
This was a known issue due to changes in gnome 2.18. This should get you up and running in amarok:

I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

---

### Post by crav on 2007-06-22
> **moredhel said:**
> beryl... mmm... stable :P

No, i'm not after too many crashes xD

especially after finding some simply beautiful gnome themes on deviantart ;)


links please?

---

### Post by TrinitronX on 2007-06-26
> **BrowneR said:**
> This was a known issue due to changes in gnome 2.18. This should get you up and running in amarok:

I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.


Thanks!!!  I've been trying to figure out why the keys weren't working ever since updating to feisty :P
The script kinda makes me want to learn python.  Now to figure out how to get gnome to launch amarok when I press my start media player key.

---

### Post by BrowneR on 2007-06-27
I've done a bit of digging on that and apparently Rhythmbox is hard coded as the default for Gnome.
I did however dig up this as an alternative work arround:

[http://ubuntuforums.org/showpost.php?p=1004109&postcount=7](http://ubuntuforums.org/showpost.php?p=1004109&postcount=7)

maybe for you the hex value you are after will instead be the string "XF86AudioMedia"?
to check that you could locate it in gconf:

/apps/gnome_settings_daemon/keybindings/music.

---

### Post by chocomoojuice on 2007-07-10
> This was a known issue due to changes in gnome 2.18. This should get you up and running in amarok:

I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php...?content=60910](http://kde-apps.org/content/show.php...?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

You sir, are a life saver.  I don't know what I'd do without my multimedia keys.  Again, thank you!

---

### Post by Exergy on 2007-07-11
Indeed thanks very much script works wonderfully.

As for getting Amarok to load with the media key on your keyboard, first go to keyboard shortcuts and assign "Launch Media Player" to the key. As youve mentioned its hardcoded to Rhythmbox annoyingly, so a fix I found in another thread which works brilliantly is creating a symlink:

```
sudo ln -s /usr/bin/amarok /usr/local/bin/rhythmbox
```

So thanks to these to things, all is good with my keyboard and amarok, good stuff!

---

### Post by Chymera on 2007-07-21
why didnt i look here before expecting any help from the guys on the amarok forum :confused: 
Ah well, gj with the plugin, and yes, it is partly beryl's fault because everything worked fine before i installed beryl.

---

### Post by calethix on 2007-08-23
wow, these forums are great :)

I was just sitting here thinking how much I missed being able to use my media buttons in Amarok under ubuntu.  A quick search and I had my answer.

For what it's worth, here's how I configured beryl to make the media player button launch amarok
1. system -> preferences -> keyboard shortcuts and disabled the 'launch music player' action as mentioned in the other thread
2. beryl settings manager -> general options -> commands tab -> entered 'amarok' for 'command 0'
3. shortcuts tab -> under commands, entered 'XF86AudioMedia' for 'Run command 0'

---

### Post by Maverickprowls on 2007-09-14
Thanks very much for the script, it works perfectly.  

And (an aside) what the hell was all that griping on the kde-apps website?

---

### Post by BrowneR on 2007-09-15
> **Maverickprowls said:**
> Thanks very much for the script, it works perfectly.  

And (an aside) what the hell was all that griping on the kde-apps website?

glad you found it useful.

beats me, i guess some people are just rather sensitive regarding their choice of desktop environment. free choice introduces the possibility for a lot of bitching :p hehe

---

### Post by bluenova on 2007-10-19
Script worked like a charm, thanks!

---

### Post by MatthewPlanchard on 2007-10-20
> **BrowneR said:**
> This was a known issue due to changes in gnome 2.18. This should get you up and running in amarok:

I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

Just wanted to say thanks for this script. It worked like a charm.

---

### Post by doorknob60 on 2007-11-14
Woot! Thanks! I was wondering why they weren't working.

---

### Post by bigbrovar on 2007-12-15
thanks mate .. because of u i have got one less thing to worry about

---

### Post by tom957 on 2007-12-22
awesome. thanks a bunch!

---

### Post by prince_niceguy on 2007-12-29
> **BrowneR said:**
> This was a known issue due to changes in gnome 2.18. This should get you up and running in amarok:

I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

thank you so much... i was missing the keyboard short cuts of amarok in gnome... now it is solved thanks to you....

---

### Post by codesplice on 2008-01-08
> **BrowneR said:**
> This was a known issue due to changes in gnome 2.18. This should get you up and running in amarok:

I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

Thank you. works beautifullly :)

---

### Post by JediK809 on 2008-02-14
> **BrowneR said:**
> This was a known issue due to changes in gnome 2.18. This should get you up and running in amarok:

I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

I was searching and searching for a way to get my Logitech G15's multimedia keys working, after going through all the trouble of installing the G15 libraries (which you can find here, if you're interested: [http://sourceforge.net/projects/g15tools](http://sourceforge.net/projects/g15tools), and instructions for how to install them here: [http://ubuntuforums.org/showpost.php?p=2461304](http://ubuntuforums.org/showpost.php?p=2461304)), setting up the .Xmodmap file (lots of possibilities for this one, search around), and configuring my shortcuts in Ubuntu and Amarok.

Yet, even though I could successfully map my shortcuts in Amarok, I would get no response from my multimedia keys.  Thanks to your script, everything works great.  I'm mainly posting this here so that others trying to get their G15s working will be able to find this post in a search, but I also wanted to say, thanks a lot!

---

### Post by vishnu_sresht on 2008-07-17
Thanks a lot dude, that was one cool script. I've been trying to get the multimedia keys on my iBall to work for a long time. They work perfectly in Vista but didn't do anything for Amarok ... I couldn't have Vista be better at something than Ubuntu, could I ? 

However my mute key still doesn't do what I want it to do. It mutes the system volume but I can still hear Amarok ... is there anything I can do to fix that ? My play/pause and stop buttons work like a charm though.

---

### Post by BrowneR on 2008-07-17
> **vishnu_sresht said:**
> Thanks a lot dude, that was one cool script. I've been trying to get the multimedia keys on my iBall to work for a long time. They work perfectly in Vista but didn't do anything for Amarok ... I couldn't have Vista be better at something than Ubuntu, could I ? 

However my mute key still doesn't do what I want it to do. It mutes the system volume but I can still hear Amarok ... is there anything I can do to fix that ? My play/pause and stop buttons work like a charm though.

Hi there... I've looked into your suggestion and I can find no way to mute Amarok when the systems mute key is pressed.

I'm still struggling to work out why this is necessary though? If the system volume is muted and you have the correct sound card selected under "system-->preferences-->sound-->default mixer tracks" then you should hear no sound from Amarok (or any other program) from that soundcard... First of all I would make sure you have the correct soundcard and the correct tracks selected (usually master track or PCM track) then get back to me.

---

