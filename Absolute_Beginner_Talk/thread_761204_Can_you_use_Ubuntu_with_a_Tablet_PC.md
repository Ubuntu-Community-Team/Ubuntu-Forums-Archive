---
title: "Can you use Ubuntu with a Tablet PC?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-04-21
Will Ubuntu let you write on the screen as in Windows Tablet Edition?

Is the functionality the same? Are there any differences?

Thanks

---

### Post by nicedude on 2008-04-21
You should list your make & model # of PC so that someone who might know can help you. Also if you can determine what company makes the touchscreen I would try googling that along with something like "ubuntu support" or "linux support" searching along those line you should find someone talking about trying to set up linux on your model machine. It doesn't matter really what linux they are using just that they got it to work with linux. But in general I have to say that it is very likely that there is a way to configure and use your tablet including the touchscreen in Ubuntu but no one can say without knowing what PC you are referring to exactly.

Hope you find out you can for sure & then decide to switch it :-)

---

### Post by T-Virus on 2008-04-21
Yes like Nice Dude said - it depends on a model.

Why don't you give a try with Ubuntu Live CD? It sure might not work 'out of the box' but you can always give a try. :)

---

### Post by stalkingwolf on 2008-04-21
Dont know if it will help, but you might also look at eeebuntu.

---

### Post by Odd-rationale on 2008-04-23
Yes. I am, in fact, using Ubuntu on a tablet right now.

It works very well. Rotation and everything.

For a handwriting recognition program, try CellWriter
[http://www.getdeb.net/app/cellwriter](http://www.getdeb.net/app/cellwriter)

Let me know if you need any help setting up your tablet. Basically, you just need to install wacom-tools, make some changes to your xorg.conf file, add a script to rotate the display, and install CellWriter.

However, if you have an ATI graphics card, you might have some problems, as ATI does not support rotation to my knowledge. nVidia would be fine...

---

### Post by sackbj on 2008-04-23
> **Odd-rationale said:**
> Yes. I am, in fact, using Ubuntu on a tablet right now.

It works very well. Rotation and everything.

For a handwriting recognition program, try CellWriter
[http://www.getdeb.net/app/cellwriter](http://www.getdeb.net/app/cellwriter)

Let me know if you need any help setting up your tablet. Basically, you just need to install wacom-tools, make some changes to your xorg.conf file, add a script to rotate the display, and install CellWriter.

However, if you have an ATI graphics card, you might have some problems, as ATI does not support rotation to my knowledge. nVidia would be fine...
I installed 7.10 on a Lenovo X60 tablet and was having some issues with my Wacom drivers.  I am always scared to edit my xorg.conf file, as I tend to break things that way.  I finally got it working, but I wouldn't say it was easy (at least not from a newbie point of view).  That hard drive died and I am back in Windows now.

I am currently using Ubuntu in a VM environment, and I will try getting it working again.

---

