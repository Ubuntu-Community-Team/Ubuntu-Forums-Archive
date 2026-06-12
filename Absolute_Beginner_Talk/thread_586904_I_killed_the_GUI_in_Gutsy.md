---
title: "I killed the GUI in Gutsy?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by DarqueWing on 2007-10-22
While there are a few people with similar problems, it looks like I've gotten myself into a slightly different situation than what's described in other threads.

I upgraded to Gutsy Gibbon, and everything actually looked and worked beautifully for some time.  The first time I shut it down, upon restart, it had adopted a new screen resolution that was way off - looked like 800x600 or so, while my laptop is a native 1024x768.  I changed it using the Resolution Switcher, and it went back to normal.  I decided to try to duplicate the problem, to see if it would do this every time I restarted, and lo and behold, it's in the wrong resolution again.  Unfortunately, this time it wouldn't go back.

I tried to reinstall drivers, switch resolutions, every way of changing the settings I could think of, but nothing.  Gutsy said it was using 1024x768 in every case, but whatever resolution it was using, it sure wasn't 1024x768. Then, during the last restart, I hit a much more serious problem.

I get the Ubuntu screen with the orange bar, and it fills all the way.  Then it goes to a console, where I see everything booting up, and it looks normal.  The last screen reads:

Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/ee75b98a-7d74-454f-a474-15d0cbaa2b5b) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/ee75b98a-7d74-454f-a474-15d0cbaa2b5b
kinit: No resume image, doing normal boot...

And then I have a text login.  I can log in, and it looks like a fully functioning terminal, but that's all there is - text only.  In another thread, "startx" was suggested.  I'm not entirely sure how much is going by, but I only see the last 25 lines - even all-text mode gives me such a weird resolution that text looks huge.  But in those last 25 lines, I see: "(EE) I810(0): No Video BIOS modes for chosen depth." and "Fatal server error: Caught signal 11.  Server aborting" and "XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining."

So what's going on here?  Did something go haywire with the xorg.config file?  Any help would be much appreciated.  I admit, I haven't used the terminal as much as I said I would since coming to Ubuntu, and I don't know my way around the console commands as well as I should, so any help that comes in simple, step-by-step form would be great.

---

### Post by dynamethod on 2007-10-22
when it loads up and your in the command line interface(the text) try typing in:

sudo dpkg-reconfigure -phigh xserver-xorg


and then type in:

startx

---

### Post by evilregis on 2007-10-22
dynamethod beat me to it.

If that works and gets you your GUI back, try this: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

There's some good info there to see if your xorg.conf is using proper horizontal sync and vertical refresh rates.

---

### Post by fatalerr on 2007-10-22
if you can get to the command line, great.  If not, hit ctrl+alt+f3 and you should be able to log in there.  Once at the prompt, you can try having your xorg.conf auto generated with the command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

EDIT: looks like i missed the boat on that one too ;)

---

### Post by DarqueWing on 2007-10-22
Wow...  okay, you guys really are on the ball.  That worked to get graphics up and running again - out of curiosity, what did that do?  Fetch a premade xorg file and reinstalled?

That puts me back into my resolution problem, though - it's hard to tell by looking, but it's definitely not the proper resolution.  Evilregis, I'll check out that link to see if I can figure out what's going on there.

Thanks guys, you rock.

---

### Post by William S on 2007-10-22
I also got the same problem as thread starter and I will try what is suggested.

---

### Post by sailor2001 on 2007-10-22
had the same problem with 1024x768    did the sudo dpkg-reconfigure -phigh xserver-xorg and put in 1280x1024 and it all worked then

---

### Post by DarqueWing on 2007-10-22
The link that Evilregis provided helped me fix my resolution problem, too - now Gutsy is as happy as a tornado in a trailer park.  And now I can get back to doing my statistics homework.

Ah, crap.  Now I have to do my statistics homework.

---

