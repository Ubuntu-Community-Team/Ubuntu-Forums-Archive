---
title: "distribution upgrade?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by qpwoeiruty on 2007-03-10
I just installed xchat 2.8.0 manually yesterday since Ubuntu was still stuck back at 2.6. Today, the "Software Updates" box came up and lo and behold there is a 2.6 -> 2.8 upgrade and i get a dialog box that says "Not all updates can be installed" and to run a distribution upgrade.

What do I do now?
I have a feeling that I'm getting this because I forgot to remove the xchat ubuntu package before i manually installed the newest version of xchat. Should I remove xchat and install it from apt-get again or must i now remove the manually installed version or what?

Should I back up my settings too?

THanks for looking

---

### Post by bruenig on 2007-03-10
A distribution upgrade would be
```
sudo apt-get dist-upgrade
```

Depending on your setup with the manually installed xchat, it might be necessary to remove it. I assume that if you had two of them installed before, the repo one and the manual one, that it should still work.

I am also curious as to what feature you were just falling over yourself to get.

---

### Post by qpwoeiruty on 2007-03-10
I'm running edgy so I shouldn't need to do a distribution upgrade, right? Or is it not like a Dapper -> Edgy upgrade? Basically I'd like to know if it's safe or avoidable to do it. I dont really need the one that ubuntu had installed by default.

As for the features, I just liked built-in support for the system tray. The older version didn't work the way I'd have liked it too. Also, URLs were opened in some text browser in the terminal and I wasn't sure how to change it to Firefox.

It seemed simpler to run tar..., ./configure, make, make-install than to wait for who knows how long before the repo one was updated or try to work around the problems I did have with xchat

---

### Post by bruenig on 2007-03-10
For the terminal thing, I bet you installed opera and then uninstalled it, they are evil like that. And installing the new xchat didn't fix it either.

You could have just done
```
sudo update-alternatives --set x-www-browser /usr/bin/firefox
```

The system tray already existed in package xchat-systray.

But anyways, dist-upgrade won't be a problem. It won't try to upgrade you to feisty. I am kind of curious as to why it wants you to do that. You can always just N, it won't force you to do anything.

---

### Post by Linuturk on 2007-03-11
I'm getting this same message.

When I go into Synaptic Package Manager, it tells me it can upgrade the packages, but it wants to remove the systray plugin.

Any word or info you need?

EDIT

I just updated via Synaptic and everything seems fine. I'd apply the update.

---

### Post by Ocxic on 2007-03-11
it's because the package is backported, I'm assuming same thing happend to me, I just let it do the dist-upgradwe and it installed fine.

---

### Post by loclarkey on 2007-03-12
I had this exact same issue.  in Synaptic, i did Reload, Mark all Updates, and Apply, and nothing broke and now I'm up to date.

---

### Post by hanzomon4 on 2007-03-13
I got this message too, it upgraded me to edgy which is what I've been running.. I'm perplexed....

Beryl-extras or unsupported plugins was the app that could not be upgraded without this pseudo dist-upgrade

---

