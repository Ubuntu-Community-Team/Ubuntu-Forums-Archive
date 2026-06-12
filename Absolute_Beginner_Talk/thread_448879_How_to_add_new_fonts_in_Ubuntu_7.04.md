---
title: "How to add new fonts in Ubuntu 7.04?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-19
I need to add some Hindi language Fonts. I have the fonts, but I do not know how to load them and cannot find out anything about it through Ubuntu's "help" application.

---

### Post by diatribe on 2007-05-19
all you have to do is create a .fonts directory in your home diretcory and copy them there; from terminal:

cd ~/
mkdir .fonts
cp location_of_font ~/.fonts

that should do it

---

### Post by swarup on 2007-05-19
> **diatribe said:**
> all you have to do is create a .fonts directory in your home diretcory and copy them there; from terminal:

cd ~/
mkdir .fonts
cp location_of_font ~/.fonts

that should do it

I am a brand new Ubuntu user, so this next question may sound silly: I can copy and paste what you gave here, into terminal. That much I understand. But once I've done that, then how do I get to the place where I need to paste or load the new font? When you say my "home directory", I do not know what that means. There is a folder which Ubuntu gave my name to. Is that the folder you refer to? Or something else?

---

### Post by Oki on 2007-05-19
> **swarup said:**
> I am a brand new Ubuntu user, so this next question may sound silly: I can copy and paste what you gave here, into terminal. That much I understand. But once I've done that, then how do I get to the place where I need to paste or load the new font? When you say my "home directory", I do not know what that means. There is a folder which Ubuntu gave my name to. Is that the folder you refer to? Or something else?

On the panel there is "Application", "Places" amd "System"; click on "Places" and then home; witch will open nautilus in your home folder. The font folder is a hidden folder(all folders with an . in front are hidden). To see them press Ctrl + H(or go to "View" then "show hidden folders"). Then you can find and open the font folder and paste the new fonts.

---

### Post by swarup on 2007-05-19
> **Oki said:**
> On the panel there is "Application", "Places" amd "System"; click on "Places" and then home; witch will open nautilus in your home folder. The font folder is a hidden folder(all folders with an . in front are hidden). To see them press Ctrl + H(or go to "View" then "show hidden folders"). Then you can find and open the font folder and paste the new fonts.

Thank you!!!!!!

That was wonderful. What you wrote is very helpful and clear, and I am confident it should work. I will try it now.

---

### Post by swarup on 2007-05-19
> **swarup said:**
> Thank you!!!!!!

That was wonderful. What you wrote is very helpful and clear, and I am confident it should work. I will try it now.

Hey, I followed all the instructions above-- but when I went into the OO wordprocessor, the fonts I added were not listed in the fonts tab. What should I do to get these fonts properly loaded?

---

### Post by diatribe on 2007-05-19
log out and log back in, then they should be there

---

