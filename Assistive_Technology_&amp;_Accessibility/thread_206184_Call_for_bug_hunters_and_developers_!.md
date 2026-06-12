---
title: "Call for bug hunters and developers !"
date: 2006-06-29
forum: Assistive Technology &amp; Accessibility
---

### Post by linbetwin on 2006-06-29
I am a visually-impaired user who wants to switch to Linux, but so far I've spent more time on these forums than actually using Ubuntu (I'm writing from XP right now). I know that disabled users are a minority in the Linux world, and although there are quite a few applications for our needs, most of them are buggy or barely work.

So I'm asking you, the more knowledgeable users of this community, even if you don't need a screen magnifier, please try it for just a few minutes! Maybe you'll be able to identify (or even fix) some of the problems it has.

I'll give you the directions below, although there might be some inaccuracies due to the fact that I'm writing from memory:

1) Go to System > Preferences > Assistive Technologies
2) Check "Enable assitive technologies"
3) Log out and back in

At this point, you'll see a little magnifier window that is probably obscuring the program's menu box. But you can access the Magnifier Settings by pressing ALT+F2, then ALT+F3. Now click on the button under the Profiles window (I don't remember the exact name, but it's somewhere to the right). A new window will open with more settings. If you have a 1024x768 display, I recommend these settings:

Left: 0
Right: 1023
Top: 540
Bottom: 767

Now that (hopefully) you have it working in the lower third of your screen, please use it a little and tell me if you encounter any of the problems below:

- The magnified image is rendered very poorly, with black spots and patches all over and CPU usage goes up to 100%.

- Magnifier freezes whenever a password box (like the Synaptic one) locks the screen or when I try to open more than one app.

- When writing something in Firefox, the focus jumps to the upper-left corner of the screen, instead of following the cursor.

- Nautilus crashes sometimes after clicking through a few folders.

- BitTorrent doesn't start when the magnifier is working.

If you know anything about programming, please investigate these problems! Maybe you can help me find solutions. I did file bug reports in launchpad ([36008]("https://launchpad.net/distros/ubuntu/+source/gnome-mag/+bug/36008") and [36013]("https://launchpad.net/distros/ubuntu/+source/firefox/+bug/36013")) but there are no fixes yet.

I know that a new compiz-mag is in the works, but I don't know when that will be ready and if xgl-compiz will be usable from a stability point of view.

Thank you very much for your time and I'm looking forward to reading your replies.

---

### Post by Henrik on 2006-06-30
Hi libetwin,

Thanks for sticking with us :) We are actually doing ok WRT to developer resources ATM. We had a very good meeting in Paris where several important projects were discussed and started on. We have people working on a new on-screen keyboard, better magnifier, and a more usable and stable Live CD system (access-wise).

There are several areas where we could do with some focused testing though and with both technical and end-user documentation.

**Testing**

 * The AT-SPI coverage in standard applications will always need testing. How well does OpenOffice, Firefox, Natilus, etc. share its content with the access tools. It would be very worthwhile to test this in a systematic way and report problems upstream. Reporting upstream will help raise awareness of access issues as well. This can be done using the access apps, or with at-poke (install with synaptic). [https://wiki.ubuntu.com/Accessibility/Specs/Testing](https://wiki.ubuntu.com/Accessibility/Specs/Testing)
 * KDE4: I've been told by KDE devs that the latest KDE code now supports AT-SPI, though it's not actually ready to run on non-developer systems yet because it's still very unstable (all of KDE4 that is, not specifically the AT-SPI). When KDE4 becomes a bit more stable in a month or two it will be very valuable to get some early testing in on their AT-SPI implementation, again using tools like at-poke.
 * The new AT applications themselves need testing too. This includes Orca, Speech Dispatcher, SOK and compiz-mag (not yet available)
 * Live CD testing - We are improving the boot screen access and making other tweaks, which could do with testing. In this cycle we will be rolling out Kubuntu and Xubuntu accessible versions as well so those will need testing.

**Documentation**

Our access documentation is already out of date. Helping keep that current and useful would be a big help: [https://wiki.ubuntu.com/Accessibility/doc](https://wiki.ubuntu.com/Accessibility/doc) We are also working on a website section: [https://wiki.ubuntu.com/Website/access](https://wiki.ubuntu.com/Website/access)

**Development**

There are some areas where we could do with some dev help as well.

 * AT configuration system - This is a topic that wasn't picked up by the summer of code students (understandably, as it's quite boring). I'd like to see all the access configurations moved to a single location, giving us the opportunity to easily add more options as well. [https://wiki.ubuntu.com/Accessibility/Specs/CommonATConfig](https://wiki.ubuntu.com/Accessibility/Specs/CommonATConfig)
 * Compiz hooks - A key ingredient for the compiz-magnifier is the ability for an outside application to manipulate the behaviour of the magnifier compiz plugin. That really needs to be done by the compiz people, so some lobbying might be useful there.

---

