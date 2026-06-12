---
title: "bulk convert flac files?"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-08-29
How do I bulk convert a load of flac files to wav from flac? I have tried audio-convert script but despite it saying it's doing it, it doesn't actually create the wav file(s).

---

### Post by UbuWu on 2005-08-29
Soundconverter is a great easy to use program for this. [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

But it isn't in the Ubuntu hoary repositories, so you will have to install it yourself or wait for breezy, which will have it in the repositories.

---

### Post by gammyhand on 2005-08-29
[QUOTE=UbuWu]Soundconverter is a great easy to use program for this. [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

But it isn't in the Ubuntu hoary repositories, so you will have to install it yourself or wait for breezy, which will have it in the repositories.[/QUOTE]
 I will install it from the terminal. Just need to alien the package to deb and run the deb right?

That seemed to install ok but I don't know how to run the program?

---

### Post by UbuWu on 2005-08-29
[QUOTE=gammyhand]I will install it from the terminal. Just need to alien the package to deb and run the deb right?

That seemed to install ok but I don't know how to run the program?[/QUOTE]

Applications -> Run application -> soundconverter

---

### Post by gammyhand on 2005-08-29
[QUOTE=UbuWu]Applications -> Run application -> soundconverter[/QUOTE]
 hmm, that just says file not found. But synaptic has it listed as a converted deb package.

---

### Post by UbuWu on 2005-08-29
I think you will have to install it by extracting it and then running sudo make install in its directory.

---

### Post by gammyhand on 2005-08-30
Can you examplify please? :)

---

### Post by UbuWu on 2005-08-30
Mmm... don't do that, this will be the easiest way:

Download this file:
[http://archive.ubuntu.com/ubuntu/pool/universe/s/soundconverter/soundconverter_0.7.2-0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/s/soundconverter/soundconverter_0.7.2-0ubuntu2_all.deb)
(soundconverter from breezy)

Open a terminal (applications -> system tools -> terminal)

Go to the directory where the file has been saved (probably by 'cd Desktop')

Type:
sudo dpkg -i soundconverter_0.7.2-0ubuntu2_all.deb
type your password.

You can now find soundconverter under applications -> sound & video

---

### Post by gammyhand on 2005-08-30
[QUOTE=UbuWu]Mmm... don't do that, this will be the easiest way:

Download this file:
[http://archive.ubuntu.com/ubuntu/pool/universe/s/soundconverter/soundconverter_0.7.2-0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/s/soundconverter/soundconverter_0.7.2-0ubuntu2_all.deb)
(soundconverter from breezy)

Open a terminal (applications -> system tools -> terminal)

Go to the directory where the file has been saved (probably by 'cd Desktop')

Type:
sudo dpkg -i soundconverter_0.7.2-0ubuntu2_all.deb
type your password.

You can now find soundconverter under applications -> sound & video[/QUOTE]
 Hmm, that is what I originally did and soundconvertor is not under sound & video. Nor will it run from "run application".

---

### Post by UbuWu on 2005-08-30
Did you download the package from this link? I thought you used alien, that won't work.

---

