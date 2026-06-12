---
title: "[SOLVED] Can I launch Firefox and Thunderbird to specific workspaces during boot?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by arvevans on 2007-12-22
Is there a relatively easy way to configure for automatic launching of specific applications, Firefox, Thunderbird or Evolution, etc. at boot time and have them open in a specific workspace?

Thanks
Arv
_._

---

### Post by Nano Geek on 2007-12-22
I don't know of a way to do that.
Sorry.

---

### Post by kool_kat_os on 2007-12-22
me niether

---

### Post by blueridgedog on 2007-12-22
System -> Preferences -> Sessions

---

### Post by High Camp on 2007-12-22
To get them to appear on a specific workspace use Devilspie and ensure it's running before the program is opened.

More info about Devilspie here: [http://ubuntuforums.org/showthread.php?t=98071](http://ubuntuforums.org/showthread.php?t=98071)

Hope that helps,

EDIT: Personally I have a simple shell script that launches Devilspie, Firestarter, Conky, and a couple others and I have that mapped to a hotkey (I'm on XFCE). That way the system can do it's thing on boot up and then I can press one button to start the "extras".

---

### Post by Nano Geek on 2007-12-22
> **blueridgedog said:**
> System -> Preferences -> SessionsWell, I'm not sure if this is what you're talking about, but the OP could get everything set up just like he wants it, go to **Session Options**, and click on **Remember currently running applications**. 

That might do it.

---

### Post by blueridgedog on 2007-12-22
I was more or less giving the OP a chance to explore and see if the tools worked for them or not.  I was implying that they either use the Startup Programs -> Add tool or the Session Options -> Remember etc after getting things tweaked.

Did it work?

---

### Post by arvevans on 2007-12-23
Did it work...well yes, and no.

System.Preferences.Sessions allowed me to make Firefox and Thunderbird autostart as part of reboot.  Problem is though that they both come up in the left-most workspace instead of separated into two workspaces.  I can live with this because all that is required is to drag one of them to another workspace.

Using "Remember Current Sessions" does not work...may be broken?

The other tools "DevilSpi, etc." seem overly complex for something that should be quite simple.  When time allows I may go into the code for System.Preferences.Sessions to see if I can add something there make it do what I want (it needs a box for "workspace" selection and the code to make that happen).  For now, just starting the two most frequently used applications is adequate.

Thanks for the pointers and all the help.  It is appreciated.

Arv
_._

---

### Post by blueridgedog on 2007-12-23
Thanks for the followup.  If you figure it out, post a note.

---

### Post by bowsercake on 2007-12-23
install DevilsPie and go into your home folder and then into the hidden folder .devilspie

from there make a new file called Firefox.ds

My file looks like:

```

(if
        (is (application_name) "Firefox")
        (begin
                (wintype "normal")
		(geometry "880x690+0+0")
        )
)

```

you might want yours to be like:

```

(if
        (is (application_name) "Firefox")
        (begin
                (wintype "normal")
                (set_workspace 2)
        )
)

```

this will open your firefox into the second workspace whenever you open it though, which may not be exactly what you want.

---

### Post by arvevans on 2007-12-24
Thanks.  That is exactly what I want.  I had hoped to do it without additional software.  Seems like this capability should/could be included in System.Preferences.Sessions as an option when adding applications to call at boot time, but I guess the programmers have not got that far yet.

Thanks,
Arv
_._

---

### Post by arvevans on 2007-12-24
Thanks.

---

