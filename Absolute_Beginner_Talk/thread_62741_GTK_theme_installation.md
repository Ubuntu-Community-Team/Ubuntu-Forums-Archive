---
title: "GTK theme installation"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by pinguimtux on 2005-09-05
Hi all! I'm a new Linux user, and I've been installing some distro for a while, but I finally found one that I really like, that beeing Ubuntu:)

I'm trying to customize the looks of gnome and I found a gtk+ theme that I like, but when I try to install it it gives me an error, it says "Error while installing" (I'm using other language, so the error message may be a bit different). 

The theme is here: [http://www.gnome-look.org/content/show.php?content=24229&forummode=2&forumpage=2&forumexplevel=all](http://www.gnome-look.org/content/show.php?content=24229&forummode=2&forumpage=2&forumexplevel=all)

After downloading it I renamed the file extension to .tar.gz and installed it with the themes manager...


Thanks in advance!

---

### Post by Kapre on 2005-09-05
[QUOTE=pinguimtux]Hi all! I'm a new Linux user, and I've been installing some distro for a while, but I finally found one that I really like, that beeing Ubuntu:)

I'm trying to customize the looks of gnome and I found a gtk+ theme that I like, but when I try to install it it gives me an error, it says "Error while installing" (I'm using other language, so the error message may be a bit different). 

The theme is here: [http://www.gnome-look.org/content/show.php?content=24229&forummode=2&forumpage=2&forumexplevel=all](http://www.gnome-look.org/content/show.php?content=24229&forummode=2&forumpage=2&forumexplevel=all)

After downloading it I renamed the file extension to .tar.gz and installed it with the themes manager...


Thanks in advance![/QUOTE]

Why did you rename the file? When you downloaded it, it should already be in the tar format (that is how I get all my themes from Gnome-Look). Just open the Themes program and selecr install new theme. Browse for the downloaded theme and viola, theme is now on your list and can be selected.

K

---

### Post by pinguimtux on 2005-09-05
[QUOTE=Kapre]Why did you rename the file? When you downloaded it, it should already be in the tar format (that is how I get all my themes from Gnome-Look). Just open the Themes program and selecr install new theme. Browse for the downloaded theme and viola, theme is now on your list and can be selected.

K[/QUOTE]

I renamed it because it's in .zip, and themes installer won't install that extension.

---

### Post by TristanMike on 2005-09-05
Ok, these are confusing as hell, and why there is no very simple instructions on how to do this is kinda rediculous. So after a tonne of looking and installing and uninstalling of several themes that it appeared I couldn't get to work I was fed up and scowered high and low, and the answer was there in front of my face all of the time, however, not as clear and straightforward as I has expected.

So anyway, I installed this particular package and here's how you do it and *where* to look(which is the most important).

1. go to "Places-->Home Folder"  and under "View" check "Show hidden files"

2. look for a ".themes" folder, notice the "." this indicates the hidden folder.

3. unpack the .zip or what ever file, even a tar is ok, into this folder. (For an icon theme, look for the ".icon" folder and do the same)

4. Now the step that was catching me off guard. You might ask yourself, "Self, why can't I pick a theme?" Well, the answer is simple, it's not a "Theme" you just installed. "WHAT? What the heck is it then? Why do they lie so?" To question 1, they are the "Details" of a theme, but not a fully fledged theme, and to question 2, I don't know why they lie so....lol. Ok, so you open "System-->Preference-->Themes" and click on "Theme Details" and if you had simply unpacked that pack into the ".themes" folder, you will find your stuff under "Controls" and "Window Boarders" then save the theme as your own personal and boom there ya go.

Hope this helps. :)

---

### Post by poofyhairguy on 2005-09-05
[QUOTE=TristanMike]Ok, these are confusing as hell, and why there is no very simple instructions on how to do this is kinda rediculous. So after a tonne of looking and installing and uninstalling of several themes that it appeared I couldn't get to work I was fed up and scowered high and low, and the answer was there in front of my face all of the time, however, not as clear and straightforward as I has expected.

So anyway, I installed this particular package and here's how you do it and *where* to look(which is the most important).

1. go to "Places-->Home Folder"  and under "View" check "Show hidden files"

2. look for a ".themes" folder, notice the "." this indicates the hidden folder.

3. unpack the .zip or what ever file, even a tar is ok, into this folder. (For an icon theme, look for the ".icon" folder and do the same)

4. Now the step that was catching me off guard. You might ask yourself, "Self, why can't I pick a theme?" Well, the answer is simple, it's not a "Theme" you just installed. "WHAT? What the heck is it then? Why do they lie so?" To question 1, they are the "Details" of a theme, but not a fully fledged theme, and to question 2, I don't know why they lie so....lol. Ok, so you open "System-->Preference-->Themes" and click on "Theme Details" and if you had simply unpacked that pack into the ".themes" folder, you will find your stuff under "Controls" and "Window Boarders" then save the theme as your own personal and boom there ya go.

Hope this helps. :)[/QUOTE]


OR:

Go to System, Preferences, Theme.

Open up nautilus and find the folder with the theme in it. Drag the theme from nautilus to the Theme windows. Should install itself.

---

### Post by TristanMike on 2005-09-05
[QUOTE=poofyhairguy]OR:

Go to System, Preferences, Theme.

Open up nautilus and find the folder with the theme in it. Drag the theme from nautilus to the Theme windows. Should install itself.[/QUOTE]Even as a .zip extenstion? It won't seem to install it that way....for me that is....

---

### Post by Lux Perpetua on 2005-09-06
I think that was the whole point. I personally have never tried to install a .zip theme, so I can't verify whether that's true or not. 

The reason renaming a .zip to .tar.gz doesn't work is that ".zip" and ".tar.gz" are completely different file formats. Making the theme installer think it is in the .tar.gz format when it was actually packaged in the .zip format will only confuse it, because it will treat it the wrong way. As an analogy, renaming a .jpeg image to .txt will not let you view the picture in a text editor!

---

### Post by j800r on 2008-06-03
help! i'm trying to install a gtk theme. went into system-appearence-theme, and dragged the theme package there. it said it had installed ok but the theme didnt appear in the window. what am i doing wrong? [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

