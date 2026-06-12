---
title: "How to add a new font"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-07-09
I am trying to add a new font for use in OpenOffice, and I found the instructions in the Help file. But I cannot understand the very first step, listed below. What does it mean to "Go to the {install_path}/program directory"? Where do I find this, and how do I get there? Once I can reach that place, I should be able to follow the rest of the directions myself. Thanks!

To integrate additional fonts in the OpenOffice.org software, proceed as follows:
1.Go to the {install_path}/program directory.
2.Enter: ./spadmin
3.Click Fonts.
4.The dialog lists all fonts added for the OpenOffice.org software. You can select and remove fonts using the Remove button or add new fonts with the Add button.
5.Click Add. The Add Fonts dialog appears.

---

### Post by ajax75 on 2007-07-09
Hi

An easy way I have found to add fonts is to simply
(A) Create a folder called "*.fonts*" (dont forget the dot in front of fonts) in your Home Folder
(B) Copy the font to that folder 
(C) Close your home folder

That should do it! When you reopen your home folder the .fonts folder will be gone!

---

### Post by swarup on 2007-07-09
> **ajax75 said:**
> Hi

An easy way I have found to add fonts is to simply
(A) Create a folder called "*.fonts*" (dont forget the dot in front of fonts) in your Home Folder
(B) Copy the font to that folder 
(C) Close your home folder

That should do it! When you reopen your home folder the .fonts folder will be gone!

I tried to do what you suggested. But it is strange, when I try to create a folder by the name .fonts in my home folder, I get an error stating:

"The name ".fonts" is already used in this folder. Please use a different name."

But there is no folder or file by this name in this folder. So I do not know why I am getting this error message. 

Perhaps someone could tell me why this is happening. Also, if someone could answer my question in my first letter in this thread, then I'll know two ways to create new fonts. Thanks!

---

### Post by forrestcupp on 2007-07-09
> **swarup said:**
> I tried to do what you suggested. But it is strange, when I try to create a folder by the name .fonts in my home folder, I get an error stating:

"The name ".fonts" is already used in this folder. Please use a different name."

But there is no folder or file by this name in this folder. So I do not know why I am getting this error message. 

Perhaps someone could tell me why this is happening. Also, if someone could answer my question in my first letter in this thread, then I'll know two ways to create new fonts. Thanks!

Well, if there is already a .fonts folder, you won't need to create a new one.  The reason you can't see it is because it is a hidden folder.  Any folder with a dot in the front of the name like .fonts is hidden.  What you need to do in Nautilus is to enable the showing of hidden files.  That is in the options menu, I think (I'm using KDE now).  When you enable the viewing of hidden files, you will see the .fonts folder in your /home directory.  Just put your font file in that folder and it should work.

---

### Post by swarup on 2007-07-09
> **forrestcupp said:**
> Well, if there is already a .fonts folder, you won't need to create a new one.  The reason you can't see it is because it is a hidden folder.  Any folder with a dot in the front of the name like .fonts is hidden.  What you need to do in Nautilus is to enable the showing of hidden files.  That is in the options menu, I think (I'm using KDE now).  When you enable the viewing of hidden files, you will see the .fonts folder in your /home directory.  Just put your font file in that folder and it should work.

Thank you, that did the trick perfectly. Now the font is installed.

One last question--going back to my initial question, if I were to have followed the instructions in OO help, how would I have executed this first instruction: "Go to the {install_path}/program directory."

Can you tell me what this terminology represents: {install_path}/program directory

Where is this pathway, how do I reach there?

Thanks!

---

### Post by mc4man on 2007-07-09
places/ computer/usr/lib/openoffice/program and then scroll down

---

### Post by taisao on 2007-07-09
> **swarup said:**
> ...
 "Go to the {install_path}/program directory."

Can you tell me what this terminology represents: {install_path}/program directory

Where is this pathway, how do I reach there?



I can't anwser that question. But if you install new fonts. Then openoffice will recognize it automatic as like others applications.

You need to do this first:

after copying the fonts in the .fonts folder, open up the terminal and run this command **sudo fc-cache -f** , you need to provide the superuser password (the one that you create when installing ubuntu)

after that, application should recognize new installed fonts

source: [http://ubuntuforums.org/showthread.php?t=493456]("http://ubuntuforums.org/showthread.php?t=493456")

---

### Post by forrestcupp on 2007-07-09
1. ```
cd /usr/lib/openoffice/program
```

2. ```
./spadmin
```

If #2 doesn't work try putting a sudo in front of it.

Those are pretty dumb instructions.  Why didn't they explain how to find the path?

Just my opinion here, but I wouldn't install fonts this way.  If you do, you'll probably only be able to use them with OpenOffice.  If you install them the way we showed you earlier, you can use the fonts with anything.

---

### Post by John Jason Jordan on 2007-07-11
> **forrestcupp said:**
> Just my opinion here, but I wouldn't install fonts this way.  If you do, you'll probably only be able to use them with OpenOffice.  If you install them the way we showed you earlier, you can use the fonts with anything.
I have installed fonts on my Ubuntu computer many times, but every time I end up going through all kinds of baloney to get them recognized by applications. OOo is the worst. 

I just moved three fonts to ~/.fonts and then launched OOo. They did not appear. I closed OOo. Then I used the command sudo fc-cache -f, After it finished I relaunched OOo. They're still not in the font list. Then I rebooted the computer, but they still do not appear in OOo. I tried Scribus, but it does not see the fonts either. 

I don't want to install them just for OOo. I don't mind installing them just for myself (in ~/.fonts) because I am the only user of this computer and I am always logged in as myself anyway.

How can I get these fonts working?

---

