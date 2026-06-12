---
title: "[SOLVED] Xubuntu: Play .wav on logout/shutdown instead of system beep"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Odd-rationale on 2007-12-06
Is there a way to make xubuntu play a .wav file on logout/shutdown instead of the ugly system beep? Thanks!

---

### Post by mali2297 on 2007-12-06
Run
```

gksudo gdmsetup

```
and look under *Accessibility*. (I'm not certain there is such an option though.)

---

### Post by Odd-rationale on 2007-12-06
I already went there to confiure the login sound. Now I want to do the logout sound. the gdmsetup does not have the option.

---

### Post by mali2297 on 2007-12-07
I haven't tried this myself so I don't know if it will work. Anyhow...

Install **sox**:
```

sudo apt-get install sox

```

Open the file **/etc/gdm/PostSession/Default**:
```

gksudo mousepad /etc/gdm/PostSession/Default

```

Add the following line into the file:
```

play /usr/share/sounds/shutdown.wav > /dev/null 2>&1 &

```
(Of course, you can change shutdown.wav to whatever .wav file you want.)

Save and quit.

Report back on how it went.

---

### Post by Odd-rationale on 2007-12-07
Works fantastically!

Thanks so much!

---

### Post by arcx.rw on 2008-05-02
You can also do the same without installing sox:
```
/usr/lib/gdmplay /usr/share/logout.wav > /dev/null 2>&1 &
``` :guitar:

---

### Post by mali2297 on 2008-05-02
> **arcx.rw said:**
> You can also do the same without installing sox:
```
/usr/lib/gdmplay /usr/share/logout.wav > /dev/null 2>&1 &
``` 

That seems to be a better alternative, thanks.

---

### Post by Specto on 2008-05-25
Doesn't work in xUbuntu Hardy 8.04 64-bit using play command...

However the modification of file
```
gksudo mousepad /etc/gdm/PostSession/Default
```
seems to work because when double clicked in thunar it plays the sound.

Anyway computers still beeps while login out so maybe this file isn't processed?

Here's the file's content:
```
#!/bin/sh

play /usr/share/sounds/System/logoff.wav > /dev/null 2>&1 &

PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}
exit 0
```

---

### Post by mali2297 on 2008-05-25
> **Specto said:**
> Doesn't work in xUbuntu Hardy 8.04 64-bit using play command...

Try giving the whole path to *play*:
```

/usr/bin/play /usr/share/sounds/System/logoff.wav > /dev/null 2>&1 &

```
Check it first by executing the line in a terminal.

---

### Post by Specto on 2008-05-25
> **mali2297 said:**
> Try giving the whole path to *play*:
```

/usr/bin/play /usr/share/sounds/System/logoff.wav > /dev/null 2>&1 &

```

Work's now :)   Funny

Thx :)

---

### Post by whizkid515 on 2008-06-21
Does this work with all sounds? It seems that all notifications for Xubuntu are beeps. Any way to get it to play the sounds like regular Ubuntu?

---

### Post by mali2297 on 2008-06-21
> **whizkid515 said:**
> Does this work with all sounds? It seems that all notifications for Xubuntu are beeps. Any way to get it to play the sounds like regular Ubuntu?

In general, the desktop environment Xfce4 does not support system sounds. I don't think the developers are planning to add this feature either. The login/logout sounds are handled by the GNOME Display Manager (GDM) and thus not really part of Xfce4.

---

