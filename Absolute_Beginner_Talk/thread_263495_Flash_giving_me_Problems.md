---
title: "Flash giving me Problems"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-09-23
Ok so I have AIGLX working with Compiz and then I went and installed Flash 7. Now when ever I go to a website that has flash it closes the FireFox window when it loads up. When I switch to metacity then the site loads and I can see the flash and the window does not close. Is there anyway to fix the problem so I don't have to keep switching?

Thanks for the help

---

### Post by deadgobby on 2006-09-23
> **PPAAUULL said:**
> Ok so I have AIGLX working with Compiz and then I went and installed Flash 7. Now when ever I go to a website that has flash it closes the FireFox window when it loads up. When I switch to metacity then the site loads and I can see the flash and the window does not close. Is there anyway to fix the problem so I don't have to keep switching?

Thanks for the help I had the same problem and has tick me off to no end. Because suse kde has the same plugins that I have on Ubie. So thus you can do this. It is a flash blocker and most of the ads are in flash any ways. Who wants a be bother with a bunch of adds any ways. It will block the flash intill you click on the Flashplayer icon.
[https://addons.mozilla.org/firefox/433/](https://addons.mozilla.org/firefox/433/)
 There is other people with the same problem. I am starting to think is a bug in Ubie and FF.  It fix the crash problem, but some time the crash would kick Ubie all the way into the login screen. Ugg
Gobby:shock:

---

### Post by PPAAUULL on 2006-09-23
But I want and need flash to veiw things on Ubuntu.

---

### Post by deadgobby on 2006-09-26
Ok I found that the crashing of Flash Player is on the bug report. I used the fix and seems to run stable for now.
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911)
 Open up the terminal and

gksudo gedit /etc/firefox/firefoxrc

 Add the following line

export XLIB_SKIP_ARGB_VISUALS=1

save and close.
 this is what mine looks like.

# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
export XLIB_SKIP_ARGB_VISUALS=1
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).

Gobby

---

