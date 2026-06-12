---
title: "[gtkmm 2.4] get a widget position"
date: 2013-01-23
forum: Art &amp; Design
---

### Post by alderic on 2013-01-23
Hello everyone, I am new here, so i dont know if i am posting on the good place. Feel free to point me the good section for my post, Thanks.

I am making a GUI, and I am new to the gtkmm devellopement.

I am looking for a way to catch a mouse click on a Gdk::_Pixbuf

Here are my configuration: 

my pixbuf is the only item inside my drawingAera. 
And my drawingAera is inside a Table, which own several DrawingAera, each of them containing just one picture (Gdk::_Pixbuf)

All the class that i use are derivated from the corresponding widget, except for the Gdk::_Pixbuf, which i really use.

into the Ctor of my derivated DrawingAera (MyDAera)
i have put the following line:
MyDAera:: MyDaera()
{ 
/*some stuff*/ 
 this->add_events(Gdk::BUTTON_PRESS_MASK);

   this->signal_button_press_event().connect(sigc::mem_fun(*this,
	   &MyDAera:: on_button_press_event) );
/*other stuff*/
 }

my problem is the following :
When i click on the pixbuf my signal occur which is working as intended, but it also occur when I click on the rest of the Table which own the drawing aera.
If I click on an other Table on my GUI nothing happen as intended.

[B]
Could you help me to find a way to get the position of my Gtk::_Pixbuf or the position of MyDaera inside the main window ? [/B]

I want to know the position of MyDAera,so i can check if the coordinate of my mouse when i click are realy on the Pixbuf, in order the execute the signal function or not.


i am also trying to catch the signal "ctrl + mouse click"
any idea about how to catch a signal inside a signal.
like catching ctrl press signal then mouse press signal ? ?

thanks for your help.

ps : i am using Gtkmm 2.4
edit : adding space and _ after :: to remove smiley

---

