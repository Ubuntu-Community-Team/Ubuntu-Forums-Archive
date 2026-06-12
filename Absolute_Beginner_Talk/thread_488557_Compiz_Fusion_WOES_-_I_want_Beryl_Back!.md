---
title: "Compiz Fusion WOES - I want Beryl Back!"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-06-30
I messed up a good thing. I had a perfectly functioning desktop, and I went for the bleeding edge because of a couple of little features. I love Beryl. The physics feel good to me. Compiz doesn't feel right, no matter how much I play with the settings. I can't disable snapping windows, and it's doing nasty stuff with my widgets. Can someone please tell me how to uninstall and go back to beryl? I did sudo apt-get remove compiz, and reinstalled beryl, but it didn't work. Compiz was gone, but beryl was seriously broken. Is it true that Compiz Fusion will come with 7.10? If so, I guess I'll have to get used to it, but I don't want to.
Thanks

---

### Post by overdrank on 2007-06-30
> **coldstatue said:**
> I messed up a good thing. I had a perfectly functioning desktop, and I went for the bleeding edge because of a couple of little features. I love Beryl. The physics feel good to me. Compiz doesn't feel right, no matter how much I play with the settings. I can't disable snapping windows, and it's doing nasty stuff with my widgets. Can someone please tell me how to uninstall and go back to beryl? I did sudo apt-get remove compiz, and reinstalled beryl, but it didn't work. Compiz was gone, but beryl was seriously broken. Is it true that Compiz Fusion will come with 7.10? If so, I guess I'll have to get used to it, but I don't want to.
Thanks

Hi I had to do this command to get remove compiz fusion
[PHP]sudo apt-get remove compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
[/PHP]

I did not have to reinstall beryl just select it as the window manager. Post back if you need more help. Like what type card and glxinfo.

---

### Post by xpod on 2007-06-30
> Is it true that Compiz Fusion will come with 7.10? If so, I guess I'll have to get used to it, but I don't want to.

[http://ubuntuforums.org/showthread.php?t=487397](http://ubuntuforums.org/showthread.php?t=487397)

If you really really want to;)

---

### Post by coldstatue on 2007-06-30
@overdrank - i already did that. No window decorations with Beryl, and still getting transparent menus. (bizarre)

@xpod - well, after trying to get rid of it 4 times, seeing that beryl wasn't coming back, I worked out some of the little bugs by accident. I guess it will take some getting used to, but it looks like I might as well. It's not bad at all when it's working right. 

the grouping is pretty awesome.

Take care, and thanks,.

---

### Post by coldstatue on 2007-06-30
can anyone tell me where the option is to keep windows from flying into the ring switcher in a circular path? I am seeing that sort of thing in several places, and can't figure our how to turn it off. It also does it during scale, In beryl, scale just brought the windows onto the screen smoothly. Here, they keep bouncing back and forth for a sec after they get to their positions.

---

### Post by tyreck on 2007-07-30
I too am regretting installing CF, now even after removing it, and removing and reinstalling Beryl . Beryl is using the CF plugins

ring switcher is activated with beryl (alt+tab) but doesn't look like it used to, and more annoying, my emerald theme doesn't look right, it took all of the color out and i just have a slightly glasified boarder with the button scheme in place.

I just noticed it's using the CF window picker settings as well

anyone have any ideas of how i can get my system back to the way i want it (i'll settle for back to defaults and just redo beryl and emerald.)

---

