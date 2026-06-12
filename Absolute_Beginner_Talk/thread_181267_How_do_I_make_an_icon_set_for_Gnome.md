---
title: "How do I make an icon set for Gnome?"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by Maelgwyn on 2006-05-23
Another probably very simple question from me!

I've been browsing through gnome-look.org and downloaded a few sets. What I'd like to do now is setup my own one and get it going from there!

Does anybody have a guide to how to do this?

Cheers!

---

### Post by ProjectGod on 2006-05-23
get: **gnome-iconedit**

at the terminal:

**sudo apt-get install gnome-iconedit**

supply your password when prompted to.

then after installation type this at the terminal

**sudo killall gnome-panel**

let the panel refresh itself... then under APPLICATIONS .. GRAPHICS .. Gnome icon editor!

simple little program i use personally!

---

### Post by ProjectGod on 2006-05-23
or perhaps if you want to make a whole set so that you can share it online. you could create a whole bunch of icons... then save them to a folder. compress it and upload it. 
;)

---

### Post by Clay85 on 2006-05-24
I have a small problem with Gnome-iconedit:
When I close one window, they all close. Is this supposed to happen?

Why do you personally not use Kicon Edit? Are they basically the same thing?

Edit: I had the word 'personally' in parenthesis, but I didn't realize you had use that word before. This sounded like I was being rude or condescending. So, I took them out in order to raise my charisma and score some cool points. (Did it work?)

---

### Post by Maelgwyn on 2006-05-24
Wow - talk about dependency hell! ](*,)

I tried to apt-get install that program, but came up with a pile of unmet dependencies.

So I tried through Synaptic... It said a whole pile of other files would be installed as well, but missed out about 6 that I can't install without needing to install something else, which requires yet another file to install first et cetera et cetera ad nauseum!!!!

Any work-arounds?

---

### Post by Clay85 on 2006-05-24
That's odd. It was a very simple install for me. :-/

---

### Post by ProjectGod on 2006-05-24
have you got added the repositories Maelgwyn??

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Clay85. i use gnome editor cause i have a gnome desktop! :mrgreen: 

i notice gnome editor closes all windows too :mad: . i think its inherent in the program. nothing much one can do unless one gets the source code to reprogram and recompile! :twisted:

---

### Post by catlett on 2006-05-24
```
sudo aptitude install gnome-iconedit
```
Aptitude is better than apt-get when it comes to dfependency issues. Might help your situation to run it like this.

---

### Post by Maelgwyn on 2006-05-25
I'm not sure if this is what I'm looking for... I've got a whole heap of .ico files that I'd dearly love to use as an icon set for Gnome, but don't know how to go about this.

Is there a how-to somebody can point me towards?

---

### Post by catlett on 2006-05-27
This is beyond me but it may be usefull to you. At least there is a mailing list to be part of. [http://www.freedesktop.org/wiki/Standards/icon-theme-spec](http://www.freedesktop.org/wiki/Standards/icon-theme-spec)
There is also yhis [http://www.freedesktop.org/wiki/Standards/icon-theme-spec](http://www.freedesktop.org/wiki/Standards/icon-theme-spec) which is the chapter on icons from the Gnome Human Interface Guidelines  [http://developer.gnome.org/projects/gup/hig/1.0/index.html](http://developer.gnome.org/projects/gup/hig/1.0/index.html)

---

### Post by Wangsta on 2006-10-04
you guys are all using gnome or kde.
but is there an icon editor for xubuntu that can make xfce icons?

or is there a way to convert gnome iconsets to xfce icon sets?

---

