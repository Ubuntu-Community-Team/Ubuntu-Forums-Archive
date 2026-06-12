---
title: "help with Gdesklets"
date: 2006-10-09
forum: Art &amp; Design
---

### Post by MyNameUhBorat on 2006-10-09
hey everyone I just recently(last night) switched from Windows to Ubuntu,and I absolutley love it. But I'm having a problem with gdesklets. One of the widgets I tried out is a toolbar for the desktop, but whenever I move my mouse the thing goes with it. I've tried uninstalling and reinstalling gDesklets but had no luck. I just want to get rid of the darn thing.[IMG]http://img235.imageshack.us/img235/5546/screenshotiw5.png[/IMG]

---

### Post by MyNameUhBorat on 2006-10-09
It's that stupid thing under the GIMP tips menu. I just want to kill it. lol

Thanks in advance,
Jeremy

I'm obsessed with linux

---

### Post by TigPT on 2006-10-10
hapened the same to me.. try press rigth key and close all programs until left nothing on the bar..

then you can rigth key on bar and press "remove deskelt"

it worked with me

hope helped, Good Luck 8) 


TigPT

---

### Post by MyNameUhBorat on 2006-10-11
Didn't work. This thing is frustrating me.

---

### Post by IsKall on 2006-10-12
I like your GTK2.X, what gtk theme is it?

---

### Post by MyNameUhBorat on 2006-10-24
Does anyone have any idea of how to get rid of this stupid toolbar. I've tried uninstalling and re-installing but the thing just keeps coming up. And my mouse won't leave the spot that it's on.

---

### Post by Zok on 2006-10-25
Try creating a new profile.  That worked for me.  But now I want to know how I can delete the default, or any subsequent profiles.

---

### Post by skinny on 2006-10-26
> **Zok said:**
> But now I want to know how I can delete the default, or any subsequent profiles.

As long as the profile is empty (no gdesklets) it is removed when you close the gdesklet shell. not tried this with the default yet, but it removes the other profiles i've created.

hope this helps

---

### Post by Maxtorm on 2006-10-28
> **MyNameUhBorat said:**
> Does anyone have any idea of how to get rid of this stupid toolbar. I've tried uninstalling and re-installing but the thing just keeps coming up. And my mouse won't leave the spot that it's on.

I just ran into an equally annoying problem (installed a display desklet that errored out -- when I logged back in, desklets were *all* gone; when I went into the gDesklets Shell, it opened to a blank window and the application hung).  The solution may fix your problem as well:

Beware: This will remove the gDesklet configuration for the current user.

Open a terminal session and type
```
rm -rf .gdesklets
```

When I restarted, I had to build by gDesklets from scratch, but at least it solved the problem.

---

