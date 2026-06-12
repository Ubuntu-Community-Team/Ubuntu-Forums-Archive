---
title: "nero for linux"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by verby on 2006-11-01
anyone using this program? how is it? as good as for win?

---

### Post by yabbadabbadont on 2006-11-01
I've used it under both Gentoo and Ubuntu.  It works fine for me, but it doesn't have all the features of the Windows version.  If you already have a license key from Windows, then I would say go ahead and give it a try.  If you don't have a key, I would suggest you try the various free programs that work very well for most people.  (K3b, Gnomebaker, Gtoaster, Xcdroast, ...)

---

### Post by verby on 2006-11-01
yeah... looks like that nerolinux is not even close to nero for win. i guess for linux k3b is the way to go.

---

### Post by dvarsam on 2006-11-14
> **verby said:**
> yeah... looks like that nerolinux is not even close to nero for win. i guess for linux k3b is the way to go.

Interesting Talk!

Since I am NOT able to play VCDs with any Open Source S-ware out there, I would like to ask:

Is the program "NeroLinux" capable of handling VCDs?

Thanks.

P.S.> Nobody was able to solve my problem (in this issue).
As a conclusion, it might be better to pay for an application that can handle VCDs, compared to not being able to play them at all...

---

### Post by yabbadabbadont on 2006-11-15
> **dvarsam said:**
> Interesting Talk!

Since I am NOT able to play VCDs with any Open Source S-ware out there, I would like to ask:

Is the program "NeroLinux" capable of handling VCDs?

Thanks.

P.S.> Nobody was able to solve my problem (in this issue).
As a conclusion, it might be better to pay for an application that can handle VCDs, compared to not being able to play them at all...

Are you saying that you are looking for a linux app that can play vcds? Or are you asking for one that can create them?

If you just want to play them, xine-ui can do it.  To create them, you might search the forums for the "tovid" thread.  It can be used fairly easily to master both dvds and vcds.  The vcd creation might be a little buggy though, since it isn't used as much.  The authors are very good about fixing things in a timely manner and the svn version is easy to install.  (to get any fixes you ask for)

---

### Post by ericesque on 2006-11-15
I don't know why you'd want to use nero when there are equally good free solutions installable from the repos.  But then I never liked nero much to begin with.  Probably something to do with the fact that at one point I remember being absolutley unable to find the button to begin burning a disc in expert mode... stupid stinking nero.

---

### Post by yabbadabbadont on 2006-11-15
I use Nero for two reasons:

1) I already had a license from the windows version.
B :)) All the free tools seem to use cdrecord to do the actual work and recent versions of it always fail while performing the power calibration.  Nero has always worked for me.

Strangely enough, growisofs always works when I use it to burn dvds though.  It just seems to be cdrecord that doesn't want to work.  I haven't tried cdrdao to see if it will work.

---

### Post by Atomic Dog on 2006-11-15
I tried to use Nero, but ended up using gnomebaker -less problems and it's a snap to use.

---

### Post by David Corrales on 2006-11-15
I have a Nero license but I'm using gnomebaker/brasero now. Also, I LOVE the right-click-on-an-iso-file and burn to disc.

---

### Post by Malta paul on 2006-11-15
I agree Gnomebaker is also my choice, never had any problems with it.

---

### Post by Turin Turambar on 2006-11-16
NeroLinux has a verify option + handles the multisession (not working in Gnomebaker & Edgy). That's more than enough for me.
It uses its own engine and not a buggy cdrecord.

You only need to "fix" the horrible GTK 1.2 theme... but I managed to do that and now it looks almost like default Ubuntu theme.

---

### Post by Perfect Storm on 2006-11-16
Can you post the solution to that, Turin Turambar?

---

### Post by yabbadabbadont on 2006-11-16
For me, I simply installed a decent GTK1 theme and configured it to be used in my .gtkrc-1.2-gnome2 file.

(The theme is Ana by the way.)

---

### Post by Turin Turambar on 2006-11-16
> **Artificial Intelligence said:**
> Can you post the solution to that, Turin Turambar?

Firstly, go to Synaptic and install gtk-engines-industrial.

THEN, go to this address:
[http://www.gnome-look.org/content/show.php?content=47104&PHPSESSID=8e045442d9ec88063ab2f53a0924a320](http://www.gnome-look.org/content/show.php?content=47104&PHPSESSID=8e045442d9ec88063ab2f53a0924a320)

...and install it as described. It's a Ubuntu dapper GTK1 theme.

After that, type

```
echo "include \"$HOME/.gtkrc.mine\"" > ~/.gtkrc-1.2-gnome2 
```

Do a ```
 gedit .gtkrc.mine 
``` delete everything (if any) and add this: 

```
 include "/usr/share/themes/Industrial/gtk/gtkrc" 
```

That's all. Now NeroLINUX and all other GTK1 programs will look good! :)

---

### Post by Perfect Storm on 2006-11-17
Thanks :)

---

