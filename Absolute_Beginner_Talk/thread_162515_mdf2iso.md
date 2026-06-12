---
title: "mdf2iso"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Riz on 2006-04-19
Hey peeps,

Jst a quick question, am trying to install mdf2iso on me linux ubuntu os but im having some probs, ive managed to get some instructions for doing so only its not working, i think i need a step -by- step instalation guide inclu the exact comands to type in.

If anyone can help id be very very greatful, thankyou in advance

---

### Post by htinn on 2006-04-19
First, you'll probably want to get the deb file:

[http://prdownload.berlios.de/mdf2iso/mdf2iso_0.3.0-2_i386.deb](http://prdownload.berlios.de/mdf2iso/mdf2iso_0.3.0-2_i386.deb)

Then open a terminal and install it:

sudo dpkg -i mdf2iso_0.3.0-2_i386.deb

then:

mdf2iso source.mdf destination.iso

---

### Post by henryk69 on 2006-04-19
Hi Ritz,
Why dont you use Synaptic - thats a great tool for instaling software.
You can find it in the System->Administration menu. There click on the search button and you should find your desired program.
If you cannot find it, you probably should activate additional "Universe" and "Multiverse" repositories. 

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

After that you'll have full access to a huge amout of programs.

---

### Post by Riz on 2006-04-19
I do use synaptic with all additional repositories but theres nothing to burn mdf files in there. Your help is greatly appreciated though since im absolutely determined to get away from Windows

---

### Post by henryk69 on 2006-04-19
Yes your right, I checked it - mdf2iso is not there- sorry. 

So you should follow the steps Htinn posted above. Download the file, open a terminal (Aplications->Accessories->Terminal) and type the comand Htinn wrote. 

(Remember if you downloaded the file somewhere else than your home directory you have to type in also the correct path)
Hope this helps you,
cheers

---

