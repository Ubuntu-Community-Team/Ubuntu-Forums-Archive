---
title: "Turning an old iMac 350 Mhz into a JukeBox"
date: 2011-06-24
forum: Apple Hardware Users
---

### Post by LtPitt on 2011-06-24
Hello everybody!

I have this lovely iMac sitting in my cellar and I want to revive it.
It's objectively beautiful and it has enough horsepower to become my jukebox.
Its integrated audio is crystal clear and it has no fans: perfect.

I have just one serious problem: I'd like to use it without mouse and keyboard...
So what I'd need is a cool app to handle mp3s (with album art and the more cool stuff I can get) AND to be controlled from an Android phone.

There's a lot of applications (songbird, xbmc, banshee, rythmbox, others) that have remote controller app on android market but I think they will not run on ppc in their latest versions...


Any compiling from source succesfull experience / hints on my little project?

---

### Post by Untitled_No4 on 2011-06-25
I think the problem might be finding pre-compiled packages for PPC. Have you tried MintPPC ([http://mintppc.org/](http://mintppc.org/)), perhaps you can get those packages there precompiled?

Also, you might want to have a look if they have MythTV. It's a media centre package for Linux which also has a remote on the android market.

---

### Post by LtPitt on 2011-06-25
Wow! :D

I didn't know of such a port! Thanks a lot!

MintPPC (hopefully fluxbox) is just a GREAT idea for those oldies: the perfect mix of style, speed and functionality.
I'll test it and come back with news.
I think that for sure they've prepared at least a single mainstream mp3 player and that's exactly what I need.

I'm the happiest :)

---

### Post by LtPitt on 2011-06-27
Et voilà! :D

It is BEAUTIFUL! :D

I just decided to use Amarok instead of Rhythmbox because I've had problems compiling a newer version of it (minimum 1.7.0 to let Android remote control work).

I've been able to let it autostart amarok now all I'd need is to let the little beast autologin so I can throw keyboard and mouse away :)

Any ideas? :)

---

### Post by linuxopjemac on 2011-06-27
Did you install MintPPC ?

---

### Post by LtPitt on 2011-06-28
hey!
Of course I did: it went great!
Super-easy and amazing performance.
I loved the user-care part about knowing all the pain behind a long wait and the brainy way to arrange packets to let me have a beer :D
At first I was a little scared seeing LXDE because Fluxbox would've been lighter but I was really surprised to see how well this acient iMac would do (with such a little ram!).
App list is perfect: really perfect.

(for all the friends reading: you could have problems at your first reboot with graphic settings and X will not start... In that case: [http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf](http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf) ps I loved the "wget friendly" textfile version)

You're behind the project, right?

AWESOME piece of work!

I am gonna donate to keep it alive as soon as I recharge my debit card :)

Of course you have a dinner waiting for you in Rome, Italy, whenever you want.

Now I just need to set up a samba server to upload new songs easily and tweak Amarok to automatically refresh song list and download album covers.

And...
Open itself full screen :D

And...
turn off imac screen not to waste energy while it keeps playing tunes.

Thank you all for making this fun possible :)

---

### Post by linuxopjemac on 2011-06-28
You are welcome. And yes, I am the man behind MintPPC.

---

