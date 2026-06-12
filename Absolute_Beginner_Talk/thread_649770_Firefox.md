---
title: "Firefox"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-12-25
Hi.  I've been having issues with firefox that seem to be getting progressively worse.  It is now randomly closing once or twice an hour, for no apparent reason.  The only symptom I can detect is that it happens when I am actively doing something such as typing or clicking a link.  This can be anywhere from a google search or in the address bar, to a forum.

I am a complete newb, and would like to just uninstall and reinstall Firefox (hoppfully without losing my bookmarks etc) but I do not know how to uninstall and re-install in ubuntu.  Is there an add/remove programs function like in windows?

Now the Find function is no longer working - that makes using FF completely impractical for me.

Any help appreciated.

---

### Post by waste301 on 2007-12-25
bump

---

### Post by SOULRiDER on 2007-12-25
Open a terminal and type
```
sudo aptitude install firefox
```

Does this happen with other browsers too? Are you using flash when it crashes?

---

### Post by waste301 on 2007-12-25
No, I'm not using Flash.  It just closes very suddenly - that command looks like it is to reinstall over my current installation.  Is that ok?  I hesitate to use the synaptic package manager to uninstall anything, there are about 20 firefox related options in there.

Is FF 2 compatible with ubuntu, or should I try an older version (which I would need to locate an don't know how to install)

---

### Post by waste301 on 2007-12-25
I tried your command. It updated 0 and apparently did nothing.

---

### Post by Moop on 2007-12-25
You could reinstall over the old version but I doubt that is the problem. Try creating a new profile and see if firefox works better. 

To create a new profile (your old profile with bookmarks etc won't be deleted) in terminal

```
firefox -profilemanager
```

It would be a good idea to close firefox before creating your profile.

---

### Post by atomkarinca on 2007-12-25
Next time opening Firefox, try running it through the terminal. When it crashes it will most probably print some error on the terminal. Paste the error here and we can have a better idea of what is causing it to crash.

---

### Post by LaRoza on 2007-12-25
> **waste301 said:**
> 
Is FF 2 compatible with ubuntu, or should I try an older version (which I would need to locate an don't know how to install)

There is also the new version, 3.0 in beta. It can be installed next to 2.0.0.11, but it doesn't work with most extensions.

---

### Post by waste301 on 2007-12-25
> **atomkarinca said:**
> Next time opening Firefox, try running it through the terminal. When it crashes it will most probably print some error on the terminal. Paste the error here and we can have a better idea of what is causing it to crash.

> **Moop said:**
> You could reinstall over the old version but I doubt that is the problem. Try creating a new profile and see if firefox works better. 

To create a new profile (your old profile with bookmarks etc won't be deleted) in terminal

```
firefox -profilemanager
```

It would be a good idea to close firefox before creating your profile.


Ok - I will close out FF and try to create a new profile.  Hopefully that will work.  If it crashes again I will try to post a log - but you hae to tell me how to run FF from the terminal, and locate the log it creates.

---

### Post by waste301 on 2007-12-25
i ran your command

firefox -profilemanager

It opened a new firefox and my Find now appears to be working - no idea about the crashes.  MY bookmarks are still there.

Do I need to select this profile now somehow? Or is it automatically fixed now and I can use FF as usual?

---

### Post by waste301 on 2007-12-25
I lied - the Find function stopped working again.

---

### Post by erfahren on 2007-12-25
just open up a terminal (Apps > Accessories > Terminal) and just type in 
firefox

leave the terminal open (if you close it firefox will close as well) 
the out put will just show in that terminal window if/when firefox crashes

(the Firefox that's installed is the best version for Ubuntu, your best bet is to try to get it working)

.... another thought:

in a terminal, enter:
```

cd /usr/lib/firefox/plugins

```
and then (for a list of contents):
```

ls

```
and post it here

---

