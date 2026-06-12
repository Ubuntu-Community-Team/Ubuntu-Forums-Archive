---
title: "Gtkmm!!! Help!!"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by nerddy on 2008-03-26
OK guys im a newbie is this linux thing.. i need some noob help too.. can u guys teach me how to run a program/application.. i wanna run gtkmm, but i dunno which is the exe file.. i tried using the terminal but to no avail.. so help me please!!!

---

### Post by glennric on 2008-03-26
gtkmm is not an application that you can run.  It is the C++ interface for GTK.  This means that programmers can use the libraries in gtkmm so that their C++ programs can use GTK.

---

### Post by northern lights on 2008-03-26
Do you have it installed in the first place? If not run ```
sudo apt-get install libgtkmm-2.4-dev
```

Anything else you'll find in the [Programming with gtkmm book]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/pdf/programming-with-gtkmm.pdf")

--> You can use it, not "start" it though - it's not an app.

---

### Post by nerddy on 2008-03-26
i download the gtkmm already. it came in a folder. when i open up, there are more subfolders inside. so how do i go about using this gtkmm thing.. im confused.. im told to create a GUI from it and was also told to draw a topology using gtkmm..

---

### Post by northern lights on 2008-03-26
You've probably downloaded some source, it would need to be installed by running ```
./configure
make
make install
```from the parent folder, but installing via apt-get is really much simpler - so I'd say discard the download.

As for creating the GUI - check the book. Is this for some sort of CS homework?
Anyway if you want some help with that one also: What sort of GUI are you asked to create and for what?

---

### Post by nerddy on 2008-03-26
oh no, i installed it using the synaptic manager.i wanna ask if there is any way the i can use gtkmm to do my project.. first thing here, i have no idea what gtkmm is about and i expected it to be like a programme just like in windows..how do i go about making use of gtkmm?

---

### Post by northern lights on 2008-03-26
gtkmm is a GUI toolkit for C++

It's really not a Windows/Linux issue, but simply a misunderstanding of what it is.

Can you either describe the exact nature of your project, or just post a link?

---

### Post by nerddy on 2008-03-26
im doing on manet( mobile ad hoc network) im told by my supervisor to initialize a topology table.. he wants us to use familiarize on vector and raster methods of drawing a network topolgy table.. and the problem now i faced is .. where do i start drawing all these vector and raster lines and dots??

---

### Post by northern lights on 2008-03-26
[Drawing Area Widget in gtkmm]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-drawingarea.html")

---

### Post by nerddy on 2008-03-27
hen do i have to download cairo? and if i download it , how do i launch it?

---

### Post by nerddy on 2008-03-31
How To Start A Thread???

---

### Post by nerddy on 2008-03-31
gcc simple.cc -o simple  'pkg-config gtkmm-2.4 --cflags --libs'
i found this from the internet, but when i wanna compile using this sentence, i cant.. can u tell me whats the meaning of this sentence and how should i use it?

---

