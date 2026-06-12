---
title: "Amaya error - won't open"
date: 2007-03-05
forum: Art &amp; Design
---

### Post by geovino on 2007-03-05
I just installed Amaya, but when I open it it opens for a moment then disappears.

I ran Amaya in the terminal and I get this:

davek@davek-desktop:~$ amaya
09:02:33 AM: Deleted stale lock file '/home/davek/.amaya-davek'.

(amaya:13288): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 9050 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
davek@davek-desktop:~$ 

What do I do to correct this?

---

### Post by bizzy on 2007-03-08
> **geovino said:**
> I just installed Amaya, but when I open it it opens for a moment then disappears.
I am seeing the same with Kubuntu 6.10. There is another reference to this problem in the Forum but no solution that I could find.

Oh - how I wish I could get HotMetaL Pro to run under Wine. IMHO still the best tool for generating industrial quantities of nested table infested pages. Installation fails when it tries to find Internet Explorer ...

---

### Post by happybrick on 2007-06-18
I had the same problem. Add / Remove Apps gives you version 9.53 of Amaya.

I downloaded version 9.55 from the Amaya website and it starts without a problem.

[http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)

---

### Post by geovino on 2007-06-19
I've downloaded it, how do I install it? I tried the instructions, but none of them worked. Is Amaya worth it? or is Quanta or Bluefish just as good?

---

### Post by happybrick on 2007-06-21
When I clicked on the link Firefox asked if I want to open the file with GDebi package installer. Click OK and it automatically installs. Forgot to mention you might prefer 9.54 as that's the most recent stable release.

As for if it's worth it, that I don't know. I'm new to Linux so don't have experience of any of these packages.

I'm looking for an editor which I can use to setup a website, and then allow others with no HTML or CSS knowledge to add their own articles.

If you have any experience of this I'd like to hear which package you prefer.

---

### Post by coolglobal on 2007-06-21
I have just experienced the same bug. Fixed by completely removing Amaya then downloading and installing the latest version, see below. 

UPDATE
I installed the latest build from the website, 9.54, and it now opens.
[http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)

---

### Post by geovino on 2007-06-21
> **happybrick said:**
> When I clicked on the link Firefox asked if I want to open the file with GDebi package installer. Click OK and it automatically installs. Forgot to mention you might prefer 9.54 as that's the most recent stable release.

As for if it's worth it, that I don't know. I'm new to Linux so don't have experience of any of these packages.

I'm looking for an editor which I can use to setup a website, and then allow others with no HTML or CSS knowledge to add their own articles.

If you have any experience of this I'd like to hear which package you prefer.

I've been getting used to Quanta, but the easiest is probably Nvu or the update called Kompozer.
[http://kompozer.net/](http://kompozer.net/)

Try it out.

---

### Post by jtpoole99 on 2008-09-07
I'm having the same issue.  I uninstalled and then installed the Amaya 9.55 version and then once everything was done, I tried to load it and got a different error after the program crashed.  I'm starting to feel that this program isn't worth it.

---

### Post by zakeytech on 2008-09-09
Anything you say.

---

