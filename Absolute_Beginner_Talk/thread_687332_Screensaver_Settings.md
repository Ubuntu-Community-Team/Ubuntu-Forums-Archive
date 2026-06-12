---
title: "Screensaver Settings"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Liet_Kynes on 2008-02-04
Why is there no individual settings to configure on each screensaver?

I know i've seen such configurations eg. for glmatrix screensaver berfore.


PS. I'm using ubuntu feisty

---

### Post by emarkd on 2008-02-04
That's an interesting question.  According to the Gnome project, which is the desktop you're using in Ubuntu, any screensaver that needs configuration is inherently broken, so they don't support configuring individual screensavers.  There have been a few people to work on replacements for the Gnome screensaver dialog and I think it'll eventually get done, but it's not there yet.

You can read the bug report at Gnome's site:  [http://bugzilla.gnome.org/show_bug.cgi?id=316654](http://bugzilla.gnome.org/show_bug.cgi?id=316654)

With some screensavers, you can work around this by going to the command line.  If you read the man page for the screensaver you want to configure, you'll probably find that you can set each option from the command line when the screensaver is executed.  After you figure out how you want the command to read, you can edit the .desktop file for the screensaver in /usr/share/applications/screensavers.

Also, some people used to replace gnome-screensaver with xscreensaver and make that work, but the last time I tried it, which was years ago, I never got it integrated properly.  If you're interested in that approach do some searching around.

---

### Post by texasjim on 2008-04-15
> **Liet_Kynes said:**
> Why is there no individual settings to configure on each screensaver?

I know i've seen such configurations eg. for glmatrix screensaver berfore.


PS. I'm using ubuntu feisty

I finally figured this out, for me it was a case of FindTFM then RTFM. There is a man page for each screensaver when xsreensaver is installed.  After reading in man carousel, I found that you run xscreensaver-demo prog in a terminal.  This gives a window to select and configure each screensaver. Got carousel pointed at the right file & speed set.

  Enjoy
  Jim

---

