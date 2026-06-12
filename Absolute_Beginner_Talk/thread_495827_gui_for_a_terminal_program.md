---
title: "gui for a terminal program"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by stepan2 on 2007-07-08
Hi guys. I am really impressed with the power of the linux terminal . I am thinking of remastering kubuntu and want to create my own applications for it . I want to know if there are programs that will help me make a gui program . An example of what i want would be that if a user clicks a button , i will type an action that the computer will perform . Like typing firefox should start firefox or typing apt-get install firefox should install it . I am basically looking for something like visual basic for the gui modelling

---

### Post by Nekiruhs on 2007-07-08
> **stepan2 said:**
> Hi guys. I am really impressed with the power of the linux terminal . I am thinking of remastering kubuntu and want to create my own applications for it . I want to know if there are programs that will help me make a gui program . An example of what i want would be that if a user clicks a button , i will type an action that the computer will perform . Like typing firefox should start firefox or typing apt-get install firefox should install it . I am basically looking for something like visual basic for the gui modelling
Try learning Python. Its a very versatile powerful and useful language. Its an interpreted language. like BASH scripting, but it can be compiled. Also with the PyGTK and PyQT modules that come preinstalled you can program GUIs  for Gnome and KDE respectively.

---

### Post by stepan2 on 2007-07-08
thank you for the help. I searched pyQT in add/remove programs but could not find a program. Could you tell me the exact name of the program so i can get it? Also , could you direct me to where i can learn python?

---

### Post by nitro_n2o on 2007-07-08
open the terminal and type this: 
```
sudo apt-get install python-qt4-dev 
```
Have fun

---

### Post by Nekiruhs on 2007-07-08
PyQT is just the library that enables you to program in QT with Python.  it is not a GUI Builder. You still have to type out the commands in a .py file. For example in PyGTK:
```

import gtk

#Global variable 'count' stores the number of button clicks
count = 0

def button_pressed_cb(button):
    global count
    count += 1
    print "Hello again - the button was pressed: ", count, " time(s)."

window = gtk.Window()
window.set_title("Hello World!")

button = gtk.Button("Press me")
button.connect("clicked", button_pressed_cb)

window.add(button)
window.connect("delete-event", gtk.main_quit)
window.show_all()

gtk.main()

```
Creates a window with a button that says Press me and displays a count of how many times the buttons been pressed in the terminal. As far as I know there is no Python equivalent of VB.

---

### Post by stepan2 on 2007-07-08
Ok i understand. Then is there any other language that has a program that can be a vb quivelant? I wil lstill try using python but how wil lyou tell where you want the button to go or what icons to add where

---

### Post by Nekiruhs on 2007-07-08
As far as I know, not really. You align the buttons by using pixels relative from the edge of the window. I think.

---

### Post by forrestcupp on 2007-07-08
If you don't mind using GTK, try the [Glade User Interface Builder](http://glade.gnome.org/).

Check out that link to read up on it.  If you want it, you can install it from the repos
```
sudo aptitude install glade
```
I don't know a lot about it, but it can generate code for C++, Perl, and Python.

---

### Post by bioShark on 2007-07-09
> **forrestcupp said:**
> If you don't mind using GTK, try the [Glade User Interface Builder](http://glade.gnome.org/).

Check out that link to read up on it.  If you want it, you can install it from the repos
```
sudo aptitude install glade
```
I don't know a lot about it, but it can generate code for C++, Perl, and Python.

Thanks a lot for this command. I am new to Linux and I was searching for glade instalation...and there it is. Thanks again!

P.S. I should really learn these commands. :)

---

