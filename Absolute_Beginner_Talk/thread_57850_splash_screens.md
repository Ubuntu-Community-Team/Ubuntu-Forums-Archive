---
title: "splash screens"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-08-18
how do i make my own?

---

### Post by chiefofthejojos on 2005-08-26
well, that depends on which programming language you're using.
which is it?

[Python?](http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A//mail.python.org/pipermail/tutor/2004-February/028426.html&ei=YdYPQ-X8E7PyYLOXmbcJ)
[Java?](http://www.javaworld.com/javaworld/javatips/jw-javatip104.html)
C++?
Perl/Tk?

---

### Post by cayamara on 2005-08-27
[QUOTE=jasonpeinko]how do i make my own?[/QUOTE]
As far as I know, splash screens in GNOME (I hope that's what you mean) are just images (png). GNOME then automatically puts the startup icons at the bottom of the image. So most splash screens have a dark bar at the bottom.

You can easily make your own splash screen and tell GNOME to use it instead of the default one (I hope you know how to do this).

---

### Post by jasonpeinko on 2005-08-27
[QUOTE=chiefofthejojos]well, that depends on which programming language you're using.
which is it?

[Python?](http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A//mail.python.org/pipermail/tutor/2004-February/028426.html&ei=YdYPQ-X8E7PyYLOXmbcJ)
[Java?](http://www.javaworld.com/javaworld/javatips/jw-javatip104.html)
C++?
Perl/Tk?[/QUOTE]
 C++

---

### Post by chiefofthejojos on 2005-08-27
Cayamara, I didn't know you could change the splash screen for gnome.  That's pretty cool.  Where is the png file you need to modify?

jasonpeinko, it's been awhile since I did a splash screen in C++, and that was on windows using Visual Studio.  I assume you are on ubuntu.  I'm not sure how to do splash screens in C++ in linux.
After a little searching, I think what I would use is the wxWidgets toolkit.  It's a crossplatform C++ GUI toolkit.  They have a wxSplashScreen class that can be used as follows:

```
  
<wx/splash.h>
...
wxBitmap bitmap;
  if (bitmap.LoadFile("splash16.png", wxBITMAP_TYPE_PNG))
  {
      wxSplashScreen* splash = new wxSplashScreen(bitmap,
          wxSPLASH_CENTRE_ON_SCREEN|wxSPLASH_TIMEOUT,
          6000, NULL, -1, wxDefaultPosition, wxDefaultSize,
          wxSIMPLE_BORDER|wxSTAY_ON_TOP);
  }
  wxYield();
...

```

mind you, I haven't tried this, it just seems like a good option.

---

### Post by cayamara on 2005-08-28
[QUOTE=chiefofthejojos]Cayamara, I didn't know you could change the splash screen for gnome.  That's pretty cool.  Where is the png file you need to modify?[/QUOTE]
In gconf, the key "/apps/gnome-session/options/splash_image" points to the splash image. You can either edit the image or download a splash (from [art.gnome.org](http://art.gnome.org) for example) and change the value in /apps/gnome-session/options/splash_image.

---

