---
title: "Streaming Video and general lag"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by VulgarDischord on 2008-03-27
Can anyone give me any tips as to how I can adjust my settings or whatever I need to do to get youtube and other streaming video to come through cleanly?

When I ran XP I could watch movies and vids and the like almost flawlessly, but now that i've got Ubuntu, everything is choppy and slow. Everything is choppy and slow.

It takes a fairly good amount of time for standard stuff to load for me now.

anything on here that I'm missing that just needs to be adjusted to make things run smoother?

---

### Post by ubuntu-freak on 2008-03-27
Do you mean they are slow to buffer, or choppy during playback? What graphics device do you have? Are desktop effects enabled? If so, try disabling them. Also, take a look at Part 2 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) and the troubleshooting section also.
 
nAtHaN

---

### Post by forrestcupp on 2008-03-27
Are you using Flash or Gnash?  If Flash, how did you install it.

Try going to System->Administration->Software Sources and click the 'Updates' tab.  Check the buttons next to 'Pre-released updates' and 'Unsupported updates'.  Then in a terminal, type:
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

Then restart your Firefox and see if it works better.

I don't have much lag trouble with YouTube other than the videos that are just like that whether you use Linux or Windows.

Also, make sure you have the best drivers installed for your video card.

---

### Post by VulgarDischord on 2008-03-30
Unfortunately nothing changed after I tried your commands.

---

### Post by ubuntu-freak on 2008-03-30
> **VulgarDischord said:**
> Unfortunately nothing changed after I tried your commands.

 
Make sure you don't have gnash and gnash-common installed, that may be it. Failing that, try installing flash manually, first do this;
 
**sudo apt-get purge flashplugin-nonfree**
 
Then install it manually by downloading the tar from adobe.com, and follow the instructions from part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan
 
P.S. Are you running Gutsy or Hardy?

---

