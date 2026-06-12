---
title: "xpti.dat in components dir of mozilla browser... whu?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by t0p on 2007-12-11
I just installed the adobe flash player into my firefox browser.  I installed it from the adobe site.  After doing the installation, the installer program told me: 

> NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

I don't know where to look to find this components directory.  Can anyone tell me where it is/how to do this thing?

---

### Post by yabbadabbadont on 2007-12-11
It will be located in your local profile directory for firefox.  Mine is here:

```
/home/daffy/.mozilla/firefox/dxxwcqge.default/xpti.dat
```

The ".mozilla" directory is hidden by default.  Also, "dxxwcqge.default" is the name of my profile directory, yours will be named something different.

---

### Post by t0p on 2007-12-11
Thanks yabbadabbadont!!  :)

---

### Post by iansane on 2008-01-02
> **yabbadabbadont said:**
> It will be located in your local profile directory for firefox.  Mine is here:

```
/home/daffy/.mozilla/firefox/dxxwcqge.default/xpti.dat
```

The ".mozilla" directory is hidden by default.  Also, "dxxwcqge.default" is the name of my profile directory, yours will be named something different.

Just did the same thing but have a question if anyone reads this and knows

Where did the xpti.dat file come from and why ask administrator to remove it? I just right click deleted it after making a backup copy as a standard user.

Are they assuming the administrator knows where it is? LOL I am the administrator.

---

### Post by Charles2008 on 2008-01-07
I went in to view my xpti.dat file in my profiles file and there was no xpti.dat there.  So, I'm fine then right?

Thanks,

Charles

---

### Post by yabbadabbadont on 2008-01-08
> **Charles2008 said:**
> I went in to view my xpti.dat file in my profiles file and there was no xpti.dat there.  So, I'm fine then right?

Thanks,

Charles

You should be.

---

### Post by CorryJm on 2008-01-31
I am attempting to do this right now.

I find the xpti.dat file just fine and delete it, but then the terminal still gives me the

 Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


when I try to continue with installation.

also: is this xpti.dat file recreated each time I open Mozilla? Because it seems to be re-appearing.

---

### Post by RomeReactor on 2008-01-31
Hi.
> **CorryJm said:**
> I am attempting to do this right now.

I find the xpti.dat file just fine and delete it, but then the terminal still gives me the

 Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


when I try to continue with installation.
I think this is a remnant of the way Firefox used to handle the component registration; the XPTI.DAT file used to be only available in the application directory--which in our case is '/usr/lib/firefox/components'--and that's why it asks for an Administrator to remove the file; while the file *is still* there, now the component registration depends on the XPTI.DAT file in the user's profile directory (~/.mozilla/firefox/*.default). More on that [here]("http://www.mozilla.org/projects/firefox/extensions/restart.html").

> also: is this xpti.dat file recreated each time I open Mozilla? Because it seems to be re-appearing.
Yes, it does get regenerated.

---

### Post by gallup on 2008-02-10
I find the file but can't delete it. Upon right click there is no delete available to me. I double click to open then select all and can delete...however I then get message to save change to file, which I do, and then upon trying to close file with changes from within I get the same message to save, cancel or exit without saving. File seems to remain intact no matter what I chose. What am I doing wrong in trying to delete this file as instructed?
thanks,

---

### Post by frandy on 2008-05-13
Hi

Same problem here.

I deleted the xpti.dat file and tried installing again - same message in terminal asking me to delete it... but it isn't there.


Any suggestions?

Thanks

---

### Post by 0olong on 2008-07-18
I got rid of one xpti.dat using
```
/usr/lib/firefox/components$ sudo rm xpti.dat
```
and the other by finding it under /home/oolong/.mozilla/firefox/ and just deleting it using File Browser... and it's STILL saying

> NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


What the hey?

Flash was working on my machine until a week or two back - around the time I installed 8.4, but I'm not sure it happened immediately upon upgrading. It's even been appearing in Update Manager asking to be upgraded, but there's no sign of it if I go to about: plugins in Firefox.

I miss Flash!

---

