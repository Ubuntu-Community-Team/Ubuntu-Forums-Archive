---
title: "Update indicator in panel?"
date: 2011-04-11
forum: Any Other OS
---

### Post by haapsalu_sall on 2011-04-11
Mint has an update indicator on their panel which I find makes remembering updates easy. I've searched here and online, as well as the Synaptic Package Manager and saw a freepops-updater-gnome, but I'm not sure and can't find what this does.

Bottom line -- is there an update indicator I can install on the panel?

Thanks.

---

### Post by Enigmapond on 2011-04-11
You can just set the Update Manager to show you when there's updates. It won't show unless there are updates. This can be set in the Settings.

---

### Post by haapsalu_sall on 2011-04-11
Could you tell me please where to find settings?

---

### Post by Enigmapond on 2011-04-11
Sure.. System/Administration/Update Manager/Settings (lower left corner)/Updates.

---

### Post by mcduck on 2011-04-11
> **Enigmapond said:**
> Sure.. System/Administration/Update Manager/Settings (lower left corner)/Updates.

I'm pretty sure that doesn't change the Update Manager back to old behavior of showing a notification icon instead of popping up the whole update manager window when updates are available.

The only way I know to change this is by opening gconf-editor and disabling the *apps/update-notifier/auto_launch* .key.

---

### Post by Enigmapond on 2011-04-11
> **mcduck said:**
> I'm pretty sure that doesn't change the Update Manager back to old behavior of showing a notification icon instead of popping up the whole update manager window when updates are available.

The only way I know to change this is by opening gconf-editor and disabling the *apps/update-notifier/auto_launch* .key.

This is not true as I have mine set to show when updates are available. It is not there when there are none but when there is, the icon will appear and the Manager won't appear until the icon is clicked. So I was instructing based on how I have mine set up which works very well.

---

### Post by Perfect Storm on 2011-04-11
Moved to Other OS/Distro Talk

---

### Post by haapsalu_sall on 2011-04-11
Sorry for the novice questions. What do I do to get the updates to show? I've gone to System Sources and have it set for updates. Is there some place there that I need to click on? I had updates waiting for me today when I was doing something else that I didn't know about.

---

### Post by mcduck on 2011-04-12
> **Enigmapond said:**
> This is not true as I have mine set to show when updates are available. It is not there when there are none but when there is, the icon will appear and the Manager won't appear until the icon is clicked. So I was instructing based on how I have mine set up which works very well.

There are only three options, none of which should have anything to do with the method used for informing users about available updates.

Instead they allow you to switch between automatically installing security updates, downloading updates in background or notifying about them. "Only notify about available updates" is the default setting anyway, and without changing the gconf key should use the default method of notifying about them, which is popping up the Update Manager (max once per seven days by default, unless there are security updates) window instead of showing a notification icon.

I'm not sure if the method for notifying about them was already changed in 10.04 (which you are running based on your profile), but those options really have nothing to do with it. Perhaps 10.04 still sued the old notification mechanism (I can't remember any more), you have at some point changed the gconf key, or are running a system upgraded from older Ubuntu version.

---

### Post by mcduck on 2011-04-12
> **haapsalu_sall said:**
> Sorry for the novice questions. What do I do to get the updates to show? I've gone to System Sources and have it set for updates. Is there some place there that I need to click on? I had updates waiting for me today when I was doing something else that I didn't know about.

Did you try doing what I suggested and changing the gconf key?

Press Alt-F2, run *gconf-editor*, browse to *apps/update-notifier* and disable the *auto_launch* -key.

---

### Post by haapsalu_sall on 2011-04-12
Would you tell me how to do that please?

---

### Post by frankbooth on 2011-04-12
either follow mcduck's instructions or open a terminal and write:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

---

### Post by haapsalu_sall on 2011-04-12
Thanks. I've done something about this right, because I did have an update menu pop up on its own (I didn't have to go looking for it).

---

### Post by haapsalu_sall on 2011-04-12
One last question. While I have added solved to 3 other threads, now, for some reason, I can't find where I add that. Could someone pleeease tell me?? (Grrrr at myself).

---

### Post by Elfy on 2011-04-12
Normally it would be in the thread tools at the top.

It could possibly be down to the way thsi sub-forum is set up. 

I've asked.

---

### Post by Joeb454 on 2011-04-12
> **forestpiskie said:**
> Normally it would be in the thread tools at the top.

It could possibly be down to the way thsi sub-forum is set up. 

I've asked.

It should be there now

---

### Post by Elfy on 2011-04-12
Thank you [Joeb454]("http://ubuntuforums.org/member.php?u=324421")

---

