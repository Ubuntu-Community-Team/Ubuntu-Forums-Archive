---
title: "Gedit highlighting mode when opening a document"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2007-06-03
Is there a way to set a specific gedit highlighting mode when you open a new document?

---

### Post by rich.bradshaw on 2007-06-04
either save it with an extension such as .sh, .c, .php etc or just choose highlighting from one of the menus. It's obvious somewhere. Don't use Gnome so can't check for you, but I know you can!

---

### Post by jehosephat on 2007-09-25
You're asking about automatically opening, right?  I needed a fix for octave/matlab files (*.m), which get recognized as objective C-code ... if I opened up a bunch of scripts at the same time I'd have to go through and change the highlighting one by one.  This [post]("http://ubuntuforums.org/showthread.php?t=368353") outlines how to change that for my issue ... maybe you could adapt it for yours.

---

### Post by Buffalo Soldier on 2007-09-25
> **boom2k1 said:**
> Is there a way to set a specific gedit highlighting mode when you open a new document?

View -> Highlighting Mode

---

### Post by geokker on 2008-01-28
I think boom2k1 want to register a file extension with a Gedit highlight mode. For instance, I have changed all my .php files to .gof. When I open them in Gedit, it has no idea what highlight mode to automatically select - I have to do it manually. I want it either to remember or allow me to 'add' the extension to a list against php highlight mode.

---

### Post by nick_h on 2008-01-28
> I want it either to remember or allow me to 'add' the extension to a list against php highlight mode.
Try adding the new extension to your */usr/share/mime/packages/freedesktop.org.xml* file.

---

### Post by geokker on 2008-01-28
Bang! Solved!

I added 

```
<glob pattern="*.gof"/>
``` 

to the

```
<mime-type type="application/x-php">
```

declaration in the

```
/usr/share/mime/packages/freedesktop.org.xml
```

file and it works as expected.

Cheers.

---

### Post by gwillem on 2008-02-08
I also had to run 

```
update-mime-database /usr/share/mime
```

and restart gedit. Then it worked!

---

