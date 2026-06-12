---
title: "GRUB Configuration Question..."
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-10-01
A few questions...

1)  I'm reading up on GRUB and finding that there is something called GRUB 2 and GRUB CVS.  What are the differences between them?

2)  How can I tell which version I'm using?  

3)  I've visited the website for an application called GrubConf which provides a graphical interface for modifying the .conf file.  Does anyone have experience with this?  What is your opinion on the app?

4)  Is it possible to add a GUI to Grub?

and finally...

5)  How do I install a newer version of Grub?

---

### Post by orb9220 on 2006-10-02
> I'm reading up on GRUB and finding that there is something called GRUB 2

It will be awhile for grub2.

> How can I tell which version I'm using?

There are very few upgade path's to grub I believe so I wouldn't worry about version. I have never seen an upgrade to grub.

> I've visited the website for an application called GrubConf which provides a graphical interface for modifying the .conf file

Actually it is not a conf file it is a file called  menu.lst in /boot/grub/ directory.

And this is the gui that is talked about here. [http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)

That is all I have for now. Hope it helps a bit.

---

### Post by Chickencha on 2006-10-02
1) They're not two different versions, exactly.  GRUB 2 is under development.  If somebody refers to "GRUB CVS," they probably mean a version of GRUB 2 compiled from CVS.  (If you don't know what CVS is, it's just a way of getting the most recent source of something, among other things.)

2) Go to the console and type

```

grub --version

```

If you're using the version that came with Ubuntu, then you're probably using GRUB .97, which is GRUB Legacy (rather than GRUB 2).

3) I've used it a little bit and haven't had any problems with it.  I do suggest that you make regular backups of your configuration if you find yourself changing it often.

4) GRUB 2 is supposed to use a GUI.  Additionally, there are a few guides floating around on the howto forum.

5) You could compile a newer version yourself, but I don't know that I'd suggest it.  GRUB .97 is the latest and last version of GRUB Legacy and GRUB 2 is still under development, although it is supposed to be usable.  What's the problem with your current version?

---

