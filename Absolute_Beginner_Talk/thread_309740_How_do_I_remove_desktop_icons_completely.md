---
title: "How do I remove desktop icons completely?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-11-30
I like a clean desktop. Right now it's got Computer, hda1, trash, and whatever I have in my CD drive. What's the best way to get rid of these?

---

### Post by lizardking on 2006-11-30
start gonf-editor
got to 

apps>nautilus>preferences and click out show VOlues, show computer, show home etc..

---

### Post by Amablue on 2006-11-30
There's no options in that folder. It's empty aside from "Show Special Flags"

---

### Post by Kieranties on 2006-11-30
Have you expanded the folder?

You must be missing a trick, as that is the only place to change it!  Unless you change it via a script.  While you are there, it may be worth having a look round at what else you can change for other programs

---

### Post by Bachstelze on 2006-11-30
```
rm -rf ~/Desktop/*
```

---

### Post by CatKiller on 2006-11-30
It's actually /apps/nautilus/desktop/, at least on Dapper.

---

### Post by Mahmoud on 2006-11-30
> **lizardking said:**
> start gonf-editor
got to 

apps>nautilus>preferences and click out show VOlues, show computer, show home etc..
```
gconf-editor
```It's in Apps > Nautilus > Desktop as CatKiller pointed out even on Edgy.
> **CatKiller said:**
> It's actually /apps/nautilus/desktop/, at least on Dapper.

> **HymnToLife said:**
> ```
rm -rf ~/Desktop/*
```
This will delete the Desktop folder and its contents but he wants to remove the links to the trash, mounted volumes ..etc

---

### Post by Amablue on 2006-11-30
Still not seeing anything...

---

### Post by hotbrainz on 2006-11-30
If i remember right it is "app" that you should open and not nautilus..

---

### Post by CatKiller on 2006-11-30
> **Amablue said:**
> Still not seeing anything...

That's weird. Mine looks like this.

I don't know why you haven't got those options.

---

### Post by Amablue on 2006-11-30
Anyone have any idea where all my options went? Did I install or uninstall something I shouldn't have?

---

### Post by freddy metz on 2006-12-03
i dont want to hijack this topic, but does anyone know if you can remove specific mounted devices?

---

### Post by mcduck on 2006-12-03
> **freddy metz said:**
> i dont want to hijack this topic, but does anyone know if you can remove specific mounted devices?
change fstab to mount them into /mnt, or anywhere else other than /media ;)

---

### Post by freddy metz on 2006-12-03
how exactly do i do that :???:

---

### Post by mostwanted on 2006-12-03
Past this into a terminal. It sets up new values in Gconf:

```
gconftool-2 --type boolean --set /apps/nautilus/desktop/volumes_visible false
```

Optionally, to remove computer, trash and home icon:

```
gconftool-2 --type boolean --set /apps/nautilus/desktop/computer_icon_visible false
gconftool-2 --type boolean --set /apps/nautilus/desktop/trash_icon_visible false
gconftool-2 --type boolean --set /apps/nautilus/desktop/home_icon_visible false
```

---

### Post by mcduck on 2006-12-03
> **freddy metz said:**
> how exactly do i do that :???:

see this thread: [http://www.ubuntuforums.org/showthread.php?t=196818&highlight=edit+fstab+hide]("http://www.ubuntuforums.org/showthread.php?t=196818&highlight=edit+fstab+hide")

---

### Post by kinson on 2006-12-03
Ooh, just wanted to say thanks. This helped me get rid of the hard disk icons on my desktop :)

Cheers,
Kinson

---

### Post by ashmew2 on 2007-02-15
> **lizardking said:**
> start gonf-editor
got to 

apps>nautilus>preferences and click out show VOlues, show computer, show home etc..

Man atleast type the commands right!! LOL!! i banged my head 10 times trying to install "gonf-editor" and starting it!!!! And then i read posts of others..LOL

---

### Post by Finsen on 2007-03-07
I have just come up with another solution.  In Configuration Editor, go to the directory everyone has been talking about, 

*apps>nautilus>Desktop*

As you have mentioned before, it is empty.  Then right-click the space, pick "New Key".

Fill in the following
Name: computer_icon_visible
Type: boolean
Value: True

Then you should see the line created in the space with a box beside it.  Check that box to show "Computer" on Desktop; uncheck to hide.

You can also replace the "Name" with a new value to remove other icons.  
For example, fill in:
Name: documents_icon_visible
then repeat the above procedures should give you an options to remove any icon named Documents on the Desktop.

Also, when filling out the name, uppercase didn't work for me; only lowercase works.

---

### Post by Bingulim on 2007-03-14
Hi.
Here it's my first contribution for the comunity. :) 

I too wanted a clean desktop.
Here is what I did:

```

gconf-editor

```
**apps>nautilus>preferences**
At this point, in the right portion of the window you will find an option called: *"show_desktop"*.
Just uncheck it and you get a clean one!

That's it.

---

### Post by Hexydes on 2007-04-28
Thanks Bingulim! Good call! :)

---

### Post by AdotB on 2007-04-28
I found a little tool in the LinuxMint repository called MintDesktop that lets you easily choose what you want to show on your desktop.
Here it is: http://www.linuxmint.com/repository/bianca/mintdesktop_1.3_i386.deb

---

