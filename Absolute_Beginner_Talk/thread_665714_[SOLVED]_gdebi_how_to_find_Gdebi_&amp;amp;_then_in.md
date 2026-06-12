---
title: "[SOLVED] gdebi how to find Gdebi &amp;amp; then install programs with it"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by ctoaun on 2008-01-12
Can someone tell me how to add Gdebi to add applications menu? 
Can someone tell me how to get “open with Gdebi pkg installer” to be an option after one right clicks the desired DEB file?

Please provide information that does not leave out steps the experienced user would take for granted, thanks.

Note: sudo-apt is not an option for now

---

### Post by PeterJS on 2008-01-12
> **ctoaun said:**
> Can someone tell me how to add Gdebi to add applications menu? 
Can someone tell me how to get “open with Gdebi pkg installer” to be an option after one right clicks the desired DEB file?

Please provide information that does not leave out steps the experienced user would take for granted, thanks.

Note: sudo-apt is not an option for now

Do you mean that the account that you're using doesn't have admin rights? If that's what you're saying, then gdebi won't help you at all as it needs administrative rights to install.

To add it to the menu, go to System > Preferences > Main menu, and then add it where every you want. The command for gdebi is gdebi-gtk. To add it to the nautilus right click menu has something to do with nautilus scripts, I've heard of people adding stuff but I don't remember the details.

---

### Post by ugm6hr on 2008-01-12
You should be able to just double-click a .deb in Nautilus, and the default should be to open with GDebi.

If not, right-click and it should also have Open with GDebi Package installer as the top option.

If you have removed that option by accident... This might work

Right-click on any .deb file, and go to Properties.
In the "Open with" tab, click ADD
If GDebi isn't in the list, try *gdebi-gtk* in the Custom Commands box

None of this will work if your are not an administrator account though.

---

### Post by ctoaun on 2008-01-12
> **PeterJS said:**
> Do you mean that the account that you're using doesn't have admin rights? If that's what you're saying, then gdebi won't help you at all as it needs administrative rights to install.

To add it to the menu, go to System > Preferences > Main menu, and then add it where every you want. The command for gdebi is gdebi-gtk. To add it to the nautilus right click menu has something to do with nautilus scripts, I've heard of people adding stuff but I don't remember the details.

Thanks for the friendliness

This does not work for me. 
Gdebi is present because this morning I accidentally installed something with it, which was ok because I was going to install that driverloader anyway.

There is a menu that says browse. This menu allows one to pick the  application that one wants to add to the menu. However, there are ~50 files folders etc that include the name gdebi, and none of them look anything like an application launcher.

---

### Post by ctoaun on 2008-01-12
> **ugm6hr said:**
> You should be able to just double-click a .deb in Nautilus, and the default should be to open with GDebi.

If not, right-click and it should also have Open with GDebi Package installer as the top option.

If you have removed that option by accident... This might work

Right-click on any .deb file, and go to Properties.
In the "Open with" tab, click ADD
If GDebi isn't in the list, try *gdebi-gtk* in the Custom Commands box

None of this will work if your are not an administrator account though.

I am logged on as an administrtor

thanks, you responded to [my other post]("http://ubuntuforums.org/showthread.php?t=665726"), which is related to this one.

1) A file search returns many entries for Nautilus, none of which signify anything to me, except the music player

2)  I have no ideal how to access gdebi from nautilus. A file search returns many files none of which indicate the ability to launch a command prompt, much less  GUI.

3) Is this for deb or does it work for tar.gz?

4) Right clicking properties: Need to change file permissions. This, according to the output means that I need to be root not admin. I do not know how to become root while logged in as a sudo user.

---

### Post by PeterJS on 2008-01-12
> **ctoaun said:**
> Thanks for the friendliness

This does not work for me. 
Gdebi is present because this morning I accidentally installed something with it, which was ok because I was going to install that driverloader anyway.

There is a menu that says browse. This menu allows one to pick the application that one wants to add to the menu. However, there are ~50 files folders etc that include the name gdebi, and none of them look anything like an application launcher.

I'm not sure where you were looking, but here's screen shot's of what I was trying to describe. It's good to be aware of, most things are good about adding menu entires, but if you ever want to add, remove, or rearrange things, here's where to do it.

[img]http://oregonstate.edu/~sandinp/Ubuntu/menu1.png[/img]

[img]http://oregonstate.edu/~sandinp/Ubuntu/menu2.png[/img]

[img]http://oregonstate.edu/~sandinp/Ubuntu/menu3.png[/img]


> **ctoaun said:**
> I am logged on as an administrtor

thanks, you responded to [my other post]("http://ubuntuforums.org/showthread.php?t=665726"), which is related to this one.

1) A file search returns many entries for Nautilus, none of which signify anything to me, except the music player


Nautilus is the name of the file browser in Gnome all of the menu entries under the places menu open Nautilus in one way or an other.

> 
2)  I have no ideal how to access gdebi from nautilus. A file search returns many files none of which indicate the ability to launch a command prompt, much less  GUI.


Just browse to where you save the deb file you want to install and double click on it, and it will open in gdebi.

> 
3) Is this for deb or does it work for tar.gz?

g**deb**i only works with deb files. but if you double click on a tar.gz archive in nautilus it will open up in the file roller archive manager

> 
4) Right clicking properties: Need to change file permissions. This, according to the output means that I need to be root not admin. I do not know how to become root while logged in as a sudo user.

Admin accounts have access to root privileges but when specifically requested with sudo. So if you want to change permissions with nautilus, you can run it from the run dialog with:
```

gksudo nautilus

```

---

### Post by ctoaun on 2008-01-12
*gdebi only works with deb files. but if you double click on a tar.gz archive in nautilus it will open up in the file roller archive manager*

Problems 1) Although I have an archive manager, the term rollover eludes me.

[I]Admin accounts have access to root privileges but when specifically requested with sudo. So if you want to change permissions with nautilus, you can run it from the run dialog with:
Code:

gksudo nautilus
[/I]

Problem 2)
Since, I'm using a sudo account, the file's permission's would be changed to what?

Problem 3) This computer will not run a tar -zvxf command, period. while initially there were typing errors, a copy and paste returns the same results. After reating rows in text document, I placed the terminals, forum help and program instructions in a row. The result is there is nothing wrong with the syntax because everything lines up perfectly, except username, which of course varies from person to person.

Good news:

1) i now understand Gdebi and it works
2) I now know what nautilus is

thanks for getting me this far.

---

### Post by oldos2er on 2008-01-12
> **ctoaun said:**
>  This computer will not run a tar -zvxf command, period. 

 It'll work, you just need to be in the proper directory, and feed it the correct file name.

---

### Post by PeterJS on 2008-01-12
> **ctoaun said:**
> *gdebi only works with deb files. but if you double click on a tar.gz archive in nautilus it will open up in the file roller archive manager*

Problems 1) Although I have an archive manager, the term rollover eludes me.

File Roller is the name of the archive manager, just like nautilus is the name of the file manager.

> 
Problem 2)
Since, I'm using a sudo account, the file's permission's would be changed to what?


Nope, root can do what ever it wants, and one of those things is assign ownership and permission* on files any way that it wants.

*This only works on linux native file systems, things like ntfs can only be set at mount time, but that's because they aren't real permissions, but just some made up ones so that partition will operate like the rest of the system

> 
Problem 3) This computer will not run a tar -zvxf command, period. while initially there were typing errors, a copy and paste returns the same results. After reating rows in text document, I placed the terminals, forum help and program instructions in a row. The result is there is nothing wrong with the syntax because everything lines up perfectly, except username, which of course varies from person to person.


Unless your doing something fancy and know what you're doing assume that the terminal can only work on the current directory. To list the contents of your current directory run ls (to **l**i**s**t files), if you don't see the file that you're looking for that would be a good explanation of why it isn't working. To **c**hange **d**irectory use cd followed by the directory name, by default the terminal opens in you home directory, so to get to the desktop you would run
```

cd Desktop

```

---

### Post by ctoaun on 2008-01-13
Thank you all very much

I will come back and add this to my file. Hyperlinks and bookmarks for easy reference.

this really helped a lot.

thread is solved

---

