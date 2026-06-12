---
title: "Flash in Opera"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-10-08
So, Flash works no problem in Firefox, but I prefer Opera.

How do I get Flash to work in Opera?

---

### Post by Cheese Roller on 2007-10-08
bump

---

### Post by Incense on 2007-10-08
Have you checked here?

[http://www.opera.com/linux/docs/plugins/install/]("http://www.opera.com/linux/docs/plugins/install/")

> Flash Player (Adobe)

Command line instructions to locate the Flash plug-in if it is installed:

    * locate libflashplayer.so, or
    * find / -name libflashplayer.so 2> /dev/null

If Flash plug-in is not installed, or you wish to upgrade, proceed as follows:

   1. Download the plug-in from Adobe's Web site.
   2. Follow the instructions on the download page. The installer will offer to install the plug-in, and for Opera you should choose /usr/lib/opera as the installation path.
   3. Restart Opera.
   4. Verify that the plug-in is working by going to Adobe's test page.

For additional information on Flash Player for Linux, see Adobe's blog.

MIME types:
    application/futuresplash:spl:FutureSplash Player
    application/x-shockwave-flash:swf:Shockwave Flash

---

### Post by RomeReactor on 2007-10-08
Hi. Try this: close Opera, open a terminal (Applications->Accessories->Terminal) and paste the following:
```
cp /usr/lib/mozilla/plugins/libflashplayer.so ~/.opera/plugins
```
Now open Opera again and go to YouTube to see if it's working.

---

### Post by Cheese Roller on 2007-10-09
It said no such file or directory.

---

### Post by RomeReactor on 2007-10-09
> **Cheese Roller said:**
> It said no such file or directory.

It's probably installed in ~/.mozilla/firefox. Run:
```
locate libflashplayer.so
```
and please post the output here.

---

### Post by Paulmd on 2007-10-09
> **Cheese Roller said:**
> It said no such file or directory.

In Opera:

tools->prefrences->advanced->content

Make sure the "enable plugins" box is checked

Then click on the "plugin options" button, then click  "change path", add the directory where flash is installed. Click OK. then click on the "find new" button.

---

### Post by Cheese Roller on 2007-10-09
/home/matthew/.mozilla/plugins/libflashplayer.so

---

### Post by Cheese Roller on 2007-10-09
> **Paulmd said:**
> In Opera:

tools->prefrences->advanced->content

Make sure the "enable plugins" box is checked

Then click on the "plugin options" button, then click  "change path", add the directory where flash is installed. Click OK. then click on the "find new" button.

Then it asks what MIME types will be shown with a plug-in.

What do I do here?

---

### Post by Paulmd on 2007-10-09
> **Cheese Roller said:**
> Then it asks what MIME types will be shown with a plug-in.

What do I do here?

Do you have the exact message?

I think the mime types for flash are

application/x-shockwave-flash

with an extension of swf

I think. I wasn't asked for that when I got flash on Opera.

---

### Post by RomeReactor on 2007-10-09
> **Cheese Roller said:**
> /home/matthew/.mozilla/plugins/libflashplayer.so

OK, so the correct command was:
```
sudo cp ~/.mozilla/plugins/libflashplayer.so ~/usr/lib/opera/plugins
```

Then open Opera, go to "Tools-->Preferences-->Advanced-->Content-->Plug-in options" and make sure the plugin path only reads **/usr/lib/opera/plugins**; now restart Opera and go to YouTube; Flash should be working now.

---

### Post by milesbh on 2008-03-30
sorry to hijack this thread, but i've done everything said in this topic, and all flash objects just appear as a grey box and when I hover my mouse over it, it says "Title: Click to activate and use this control" and nothing happens when i click on it.

---

