---
title: "Getting Root"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by gnama on 2006-11-08
Ok, heres the deal. This has been stressing me out all day, How do I add myself to root to add folders and such? I've tried Sys>Administration>Users and groups and added myself to the root group but still nothing. Thanks.
-Jake

---

### Post by MasterOfDisaster on 2006-11-08
Ubuntu uses your password supplied as root password by default.  Any 'Administrative Programs' need your password.

Logging in as root is not recommended, so use 'sudo' instead.

---

### Post by gnama on 2006-11-08
Thanks, but whats the command to make a folder?

---

### Post by aysiu on 2006-11-08
> **gnama said:**
> Thanks, but whats the command to make a folder?
You don't need commands. Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by gnama on 2006-11-08
Thank you for the quick replies and awesome support!

---

### Post by aysiu on 2006-11-08
In case you do still want to make a folder at the command line, this is the command you'd want: ```
sudo mkdir /path/to/name/of/folder
```

---

### Post by freshmaker on 2006-11-09
I want to create a file how can I do this using commands and terminal???

---

### Post by 3rdalbum on 2006-11-09
It depends...

If you want to create a file in Gedit, then you would press Alt-F2 and type:

```
gksudo gedit
```

Then just create your file and save it as usual.

If you want to copy a file, you could do:

```
sudo cp <source-file> <destination-file>
```

where <source-file> is the file you want to copy, and <destination-file> is the place you want to copy it to, or...

```
gksudo nautilus
```

which lets you browse the file system as root.

---

### Post by Bachstelze on 2006-11-09
I strongly recommend **not** to do *gksudo nautilus*. A simple drag-and-drop mistake and you break your whole system...

---

### Post by bulldog on 2006-11-09
> **HymnToLife said:**
> I strongly recommend **not** to do *gksudo nautilus*. A simple drag-and-drop mistake and you break your whole system...

Yeah,well live is a risk anyway.:D 

You can make other bad mistakes,bud with a little luck you can learn from it.

---

### Post by Ben Sprinkle on 2006-11-09
> **gnama said:**
> Thanks, but whats the command to make a folder?

```

sudo mkdir <<dir>>

```

> **HymnToLife said:**
> I strongly recommend **not** to do *gksudo nautilus*. A simple drag-and-drop mistake and you break your whole system...

So what I do it all the time. Just not be a dragaholic and you'll be fine.

---

### Post by aysiu on 2006-11-09
> **HymnToLife said:**
> I strongly recommend **not** to do *gksudo nautilus*. A simple drag-and-drop mistake and you break your whole system...
Quite to the contrary, you're less likely to make a mistake in the GUI than on the command line. Let's say, for example, that you wanted to delete /opt/firefox

If you do *gksudo nautilus*, you can navigate to /opt, right-click the firefox folder and delete it.

If you do it from the command-line: ```
sudo rm -r /opt/firefox
``` You hit return by accident a little too soon, and you're in trouble.

The command-line is too powerful.

---

### Post by punx45 on 2006-11-09
> **freshmaker said:**
> I want to create a file how can I do this using commands and terminal???

to make an empty file in the current directory, or to a specific path
```
touch filename
touch /path/filename 
```



otherwise it depends on what you plan to do with the file.  theres millions of ways to create files depending on your planned use.

---

### Post by ratanjska on 2006-11-09
Hi!

I need to change some files in /etc/ folder. I could not do it as user. Is there any “power-user” account capable to do changes without to use su account. Using su account makes me nervous. 

If yes, how to make a such account?

Thanks a lot 

Ratanjska (is a small river near my hometown)

---

### Post by bulldog on 2006-11-09
You have to use the sudo command,but make a copy of each file before altering.

Just an advice though.

---

### Post by ratanjska on 2006-11-09
Thank you!

I am going to do it that way.

All the best

Ratanjska (is a small river near my hometown)

---

### Post by steve.horsley on 2006-11-09
Once again, I have to agree with aysiu. This:
**sudo rm /opt/firefox**
is harmless, but this:
**sudo rm / opt/firefox**
is catastrophic.

I suggest changing the background of the root nautilus to red or whatever, to remind you this file manager is dangerous. But let's face it, Windows users use file managers with admin rights every day, and they don't all trash their systems.

---

### Post by aysiu on 2006-11-09
> **steve.horsley said:**
> Once again, I have to agree with aysiu. This:
**sudo rm /opt/firefox**
is harmless, but this:
**sudo rm / opt/firefox**
is catastrophic.

I suggest changing the background of the root nautilus to red or whatever, to remind you this file manager is dangerous. But let's face it, Windows users use file managers with admin rights every day, and they don't all trash their systems.
I believe that's the default (red background) in Edgy.

---

### Post by Ben Sprinkle on 2006-11-10
No, I don't believe so? I use it all the time in root, no red background.

---

### Post by aysiu on 2006-11-10
Sorry. You're right. In Nautilus, there is no red background. In Thunar, however, there is.

---

### Post by Ben Sprinkle on 2006-11-10
Would be nice to have it though, something for the developers to think about. :)

---

