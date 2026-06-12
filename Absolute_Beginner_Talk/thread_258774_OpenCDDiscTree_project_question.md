---
title: "OpenCD/DiscTree project question"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by ano1 on 2006-09-16
Hello,

Sorry for the [cross-post]("http://www.ubuntuforums.org/showthread.php?t=257403"), but I think this might be the more appropriate category for my question. I want to create a windows based CD like the Ubuntu LiveCD. I noticed that the cd is powered by DiscTree <[disctree.sourceforge.net/]("http://disctree.sourceforge.net/") ??>, so I decided to do more research into that. However when I go to that projects page, I see they have not released any files. Can someone please point me in the right direction? I would love to have a CD based browser that can read files off of the CD like Ubuntu does. I would like to learn how it was made and do a similar project.

Also if I have chosen the wrong forum category for this post can someone please point me in the correct direction, or could a moderator please move this to the correct section for me. Thanks in advance.

thanks,
JAS

---

### Post by dbd on 2006-09-16
Not quite sure what you are asking, but I think it is to make a live Cd like the ubuntu one, but with Windows. As far as I know it is not possible to make a Windows live CD. Windows is closed source software, so you are not allowed to change it to make it run off a CD, only Microsoft would be able to make it run off a CD.

Just had a look at your other post, and I'm really not sure what you are asking. The Ubuntu Live CD can read PDFs, not sure about the Open CD.

Do you want to make a live CD with different applications than on the Ubuntu Live CD or Open CD? That would be possible, but I'm not sure how to help you, but if you make it clear that is what you want to do then I'm sure someone could point you in the right direction.

There may already be a CD with all of what you want already? Have you tried [Knoppix]("http://www.knoppix.org")?

---

### Post by ano1 on 2006-09-16
Hello,

Thank you for your information and for your post.

Sorry if there is a lack of clearity. My question is not about the Ubuntu portion of the LiveCD, I am wondering how the Windows portion of the Ubuntu CD was created. 

When one loads the Ubuntu LiveCD in windows a program pops up which I think is a version of the OpenCD project and the kmeleon browser. This is where my question stems from. I want to be able to to build a windows program, like the one  from the LiveCD/OpenCD that loads html documents of my choosing. 

In reguards to the PDF question I was wondering if there was a way to include a no-install PDF plugin and reader on the CD, so that someone without acrobat could view a PDF on the CD without having to install Acrobat on their system.

If the liveCD/OpenCD are just a derivative of Kmeleon, can anyone tell me how it was tweaked. For example how one gets it to run off of CD?

I hope the clears up the confusion from my post. Please let me know if more explaination is necessary.

thanks in advance,
JAS

---

### Post by dbd on 2006-09-18
Ah, I understand now. But I'm afraid I can't help, maybe the Open Cd forums will be able to help:

[http://www.theopencd.org/forum](http://www.theopencd.org/forum)

---

### Post by hantms on 2006-10-26
I think I can help you with this, I wanted to do the exact same thing you are thinking of;

We have a Windows application that requires installing the MSDE database on the server only.  So we needed a basic front-end switchboard screen that gives users the option of installing MSDE first, followed by the application. 

I really liked the Disctree thingy that pops up when you pop an Ubuntu disc into a Windows PC. 

Indeed I could not find any builds, help, documentation or anything else on their Sourceforge page; it seems dead project from there... 

However I think the OpenCD and Ubuntu people are developing this one further.  Fortunately it's all standard HTML and image files, so it's very easy to just copy the lot, change the text/graphics on the HTML files with your favorite HTML editor, GIMP up some icons and Fancy Stuff, and hey presto, a professional looking splash screen / switchboard!!

I actually used the Breezy version, not Dapper, which was a bit too fancy for my needs. 

Most of the HTML files are in the Disctree\en folder. Just edit the html files as necessary.   The actual programs are launched by linking a *.lch file from the HTML page.  This is a text file that basically just specifies the executable file, just open one up in Notepad and edit.

Note that it displays an initial Splash screen for x seconds before the actual 'browser' comes up.  There's a start.ini file that specifies for how many milliseconds this should be displayed.  Keep in mind that the browser takes a lot longer to load from CD than from harddisk, so don't set this too low. 10,000 (10 seconds) is actually pretty reasonable. The splash image is start.bmp; just replace with Fancy Artwork of your own. 

So: I love Disctree!!!  :)  I think more people could benefit from it.  It's the perfect addition to making a professional Windows installer with an $-free tool like InnoSetup.

[[IMG]http://www.customsoftwaregroup.com/images/stories//agrosys_install_screen.jpg[/IMG]]("http://www.customsoftwaregroup.com")

---

### Post by hantms on 2006-10-26
One thing I was not able to do though: I'd like to 'launch' a folder, i.e. a link like 'Browse this CD'.. If I specify a folder as the thing to launch though, it doesn't work.  Someone with thoughts, visions, meditations on that one?

---

