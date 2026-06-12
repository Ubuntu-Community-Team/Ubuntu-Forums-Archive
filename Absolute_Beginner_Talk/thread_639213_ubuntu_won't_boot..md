---
title: "ubuntu won't boot."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by slothmonster on 2007-12-12
Alright i've been searching around i see a few people are getting the same error i am but they are getting it for completely different reasons so i figured i'd make a thread.

earlier today i tried to install a splash theme from gnome-look.org. theme in question is called [fingerprint]("http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468")

it had a set of instructions [here]("https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765") which i'm pretty sure i followed exactly, anyway i restarted my computer to take a gander at my new splash or whatever and low and behold i am now getting this:

**Error 18: Selected cylinder exceeds maximum supported by BIOS**

and my ubuntu won't boot up, it allowed me to edit some lines of code which i remember adding to in the instructions for the splash but when i removed the piece of code i added it still won't boot.

is there any way i can fix this or at least reinstall ubuntu while keeping all my files as i have a few projects with a couple of hours of work into them and a fair bit of my movies and music and would be pretty upset if i lost them.

---

### Post by Tristicus on 2007-12-12
Hmmm....you weren't updating were you? If you were, CTRL+ALT+F4 then you can run 

sudo get update 

or similar (I forgot it). If not, there should be a way to remove the code or you could do 

sudo apt-get uninstall splash

or whatever you did to get it running.
Just trying to help however unhelpful I may be.

---

### Post by slothmonster on 2007-12-12
> **Tristicus said:**
> Hmmm....you weren't updating were you? If you were, CTRL+ALT+F4 then you can run 

sudo get update 

or similar (I forgot it). If not, there should be a way to remove the code or you could do 

sudo apt-get uninstall splash

or whatever you did to get it running.
Just trying to help however unhelpful I may be.

hmmm i'm currently running off a live cd, would those work if i entered them into the terminal?

---

