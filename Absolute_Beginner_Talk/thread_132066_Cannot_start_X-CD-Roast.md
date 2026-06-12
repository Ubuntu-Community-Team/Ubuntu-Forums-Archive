---
title: "Cannot start X-CD-Roast"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-02-17
I can't run CD Roast, it is saying "No root configuration found or not readable! The superuser must start and configure X-CD-Roast first, before other users can use it."

What do I need to type to launch the program as the superuser? I've tried sudo x-cd-roast but it doesn't work.

Thanks :)

---

### Post by cotcot on 2006-02-17
Is there a specific reason to choose X CD Roast ? If not K3B is well known as very good. It install under GNOME too.

---

### Post by Brunellus on 2006-02-17
[QUOTE=cotcot]Is there a specific reason to choose X CD Roast ? If not K3B is well known as very good. It install under GNOME too.[/QUOTE]
or, indeed GnomeBaker, which I use instead.

To the OP:  you must first open a terminal and run the program as root.  type 

sudo 

and then the program name.  That might solve your problem.  But I really recommend going for GnomeBaker or K3b.

---

### Post by Clark Nova on 2006-02-17
Thanks very much, they both look pretty good so I'll have to have a poke around in both.

[IMG]http://ubuntuforums.org/images/lite/icons/icon7.gif//[/IMG]

---

### Post by Brunellus on 2006-02-17
if you're running GNOME (Ubuntu's default desktop), get GnomeBaker.

If your'e running KDE (Kubuntu), get K3b

---

### Post by Michiba on 2006-04-17
I know this is an old post but, I know this one (and I don't know much)

In a terminal window type as follows

cd /usr/bin

xcdroast


You will get a  setup where you can change the root user only bit and you can work from there. I have used this program and it works Ok

Michiba

---

### Post by peterthewolf on 2006-05-31
It may be something I do wrong but I only usre cdroast as it is the only linux burner that I can rely on to burn a bootable CD all the others go through the motions and produce a non bootable CD

---

