---
title: "How to make VLC Player default for streaming wmv files?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-19
When I try to watch streaming wmv files the default player to load is Totem and it does not work at all with wmv.  I noticed that VLC player works OK but I need to manually paste the link which is a pain.  How do I change the default player for this streaming file type? I already tried to change it under properties when highlighting wmv file, but it does not work for streaming files.

Thankx

---

### Post by starcraft.man on 2007-06-19
> **bagrol1 said:**
> When I try to watch streaming wmv files the default player to load is Totem and it does not work at all with wmv.  I noticed that VLC player works OK but I need to manually paste the link which is a pain.  How do I change the default player for this streaming file type? I already tried to change it under properties when highlighting wmv file, but it does not work for streaming files.

Thankx

I present, one of the greatest Firefox extensions. [Tada!]("https://addons.mozilla.org/en-US/firefox/addon/446")

It's easy to set up, any questions reply...

---

### Post by bagrol1 on 2007-06-19
Installed the Firefox extension and it defines vlc as default for everything, but it does NOT work.  Totem is again launched and not VLC for windows media.

---

### Post by starcraft.man on 2007-06-19
> **bagrol1 said:**
> Installed the Firefox extension and it defines vlc as default for everything, but it does NOT work.  Totem is again launched and not VLC for windows media.

Hmmm, very weird. Open Firefox > Tools > Media Player Connectivity > Configure.

Make sure the Windows Media (and the rest) entry reads "/usr/bin/vlc".

That should do it. I can't imagine something being wrong with the extension... If that fails still, a very weird case indeed. I dunno why...

---

### Post by bagrol1 on 2007-06-20
Well, there should be some way to disable Totem and make VLC open automatically for every media file.  I have a paid video subscription over the net and this is "to be or not to be" for me and Linux.  

I tried to remove Totem but got message that it would also remove gstreamer codecs so I guess this is no go.

Right now I can only watch these streaming wmv files by clicking copy url in Totem and manually pasting them to VLC.

Anyway, I have nothing against Totem.  If anybody knows how to make it work with wmv files this would solve the whole thing.

I feel there must be a way to force VLC or any player as default.  In Windows I think changing some registry setting would do it.  I have no clue how to make it in Ubuntu.

Please help.

---

### Post by trginter on 2007-06-20
I'm having this same problem.  I have the plugin configured to run VLC for streaming WMV files and when the movie loads and I click play it launches VLC player and doesn't play the movie.  It won't play the movie in the browser either, only in the launched program.

---

### Post by silkstone on 2007-06-20
Not sure if this helps, but....

I do have the MediaPlayerConnectivity plugin and it does let me play .wmv streams with VLC, but only with a bit of jiggling. I have to click on the arrow symbol that comes up in the browser window (the cursor must be within this window for the symbol to appear) and then it will open VLC in a separate window.

It then plays video but no sound. To get sound, I have to click on the 'play slower' button, and then on the 'play faster' button so it's back to 1.0x speed - then it works! That's a bit of a nuisance, but at least I can use it.

Without the MPC plugin, I believe that Firefox by default uses the last plugin installed to play media files. If that's the case, it may be worth uninstalling the VLC plugin and then reinstalling it so it is the most recent.

You can check which plugins are installed by typing ```
about:plugins
``` in Firefox.

---

### Post by Michaelt74 on 2007-06-20
This may help:

[http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

---

### Post by NilsE on 2007-06-20
It appears that whatever is the last player to install is the default player.  So, uninstall totem, uninstall VLC, reinstall totem, reinstall VLC and VLC should now be the default.

Worked for me but could just be the timing and luck but I have done it a few times like when I installed MPlayer and it took over.

---

