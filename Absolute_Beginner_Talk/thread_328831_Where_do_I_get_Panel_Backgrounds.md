---
title: "Where do I get Panel Backgrounds?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2006-12-31
The default Ubuntu panel background doesn't look so good. I think, a simple panel background will significantly change my desktop look and feel. 

Where do I get good panel backgrounds?

---

### Post by CriticalStealth on 2006-12-31
whats a panel background

---

### Post by _simon_ on 2006-12-31
make them yourself?

Here's 3.

3rd is hard to see as it's translucent :)

---

### Post by wersdaluv on 2006-12-31
Wow! I like the 3rd one.... but the first two ones are so much better as I easily see text with them! LOL

Thank you very much!

Where did you get that? Did you do it yourself?

---

### Post by wersdaluv on 2006-12-31
> **CriticalStealth said:**
> whats a panel background

The panel is the one you see below and above the desktop (assuming that you are using Ubuntu). Now, its look will be changed by the background, which is named "panel background."

---

### Post by 23meg on 2006-12-31
> whats a panel background
You can just drag and drop an image file on your panel to set it as the background.

---

### Post by califman831 on 2006-12-31
cool now i can mod it in gimp, does it  change when i switch themes?

---

### Post by Ambimom on 2006-12-31
A few days ago, someone here turned me on to: 

gnome-color-chooser  ([http://www.gnome-look.org/content/show.php?content=47349](http://www.gnome-look.org/content/show.php?content=47349))

		[http://www.gnome-look.org](http://www.gnome-look.org)
Requirements:
- libgtkmm >= 2.8.0
- libglademm >= 2.6.0
- libxml2 >= 2.6.0

It works like a charm!  Once installed, it is on the Systems Menu/Preferences.

If you've never installed anything before [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) will show you how!

---

### Post by CriticalStealth on 2006-12-31
AHH thats awesome, thanks alot, im using the translucent one now, it looks amazing! thanks alot man!

---

### Post by wersdaluv on 2006-12-31
> **Ambimom said:**
> A few days ago, someone here turned me on to: 

gnome-color-chooser  ([http://www.gnome-look.org/content/show.php?content=47349](http://www.gnome-look.org/content/show.php?content=47349))

		[http://www.gnome-look.org](http://www.gnome-look.org)
Requirements:
- libgtkmm >= 2.8.0
- libglademm >= 2.6.0
- libxml2 >= 2.6.0

It works like a charm!  Once installed, it is on the Systems Menu/Preferences.

If you've never installed anything before [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) will show you how!
 
Thank you... That looks helpful and I am to try it right nowww... :)

---

### Post by wersdaluv on 2006-12-31
> **_simon_ said:**
> make them yourself?

Here's 3.

3rd is hard to see as it's translucent :)

I tried the black panel background but I had a hard time reading the text on the upper panel (which includes the applications, places, and systems tab). Can I change the font color to white? If I can, how?

---

### Post by _simon_ on 2006-12-31
> **wersdaluv said:**
> I tried the black panel background but I had a hard time reading the text on the upper panel (which includes the applications, places, and systems tab). Can I change the font color to white? If I can, how?

Create a new empty file and paste this in:

```

style "panel"
{
#    fg[NORMAL]               = "#FFFFFF"
#   fg[PRELIGHT]            = "#000000"
#   fg[ACTIVE]               = "#FFFFFF"
#   fg[SELECTED]            = "#000000"
#   fg[INSENSITIVE]            = "#FFFFFF"

#   bg[NORMAL]               = "#FFFFFF"
#   bg[PRELIGHT]            = "#FFFFFF"
#    bg[ACTIVE]               = "#000000"
#   bg[SELECTED]            = "#FFFFFF"
#   bg[INSENSITIVE]            = "#FFFFFF"

#   base[NORMAL]            = "#FFFFFF"
#   base[PRELIGHT]            = "#FFFFFF"
#   base[ACTIVE]            = "#FFFFFF"
#   base[SELECTED]            = "#FFFFFF"
#   base[INSENSITIVE]         = "#FFFFFF"

  text[NORMAL]            = "#FFFFFF"
  text[PRELIGHT]            = "#FFFFFF"
  text[ACTIVE]               = "#FFFFFF"
  text[SELECTED]            = "#FFFFFF"
  text[INSENSITIVE]            = "#FFFFFF"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

Place the file in /home and call it .gtkrc-2.0

As you can see, there are a number of different things you can play with in that file, just uncomment what you want and have a play with the colours.

You'll need to restart for it to take affect (CTRl ALT BACKSPACE)

---

### Post by wersdaluv on 2006-12-31
> **_simon_ said:**
> Create a new empty file and paste this in:

```

style "panel"
{
#    fg[NORMAL]               = "#FFFFFF"
#   fg[PRELIGHT]            = "#000000"
#   fg[ACTIVE]               = "#FFFFFF"
#   fg[SELECTED]            = "#000000"
#   fg[INSENSITIVE]            = "#FFFFFF"

#   bg[NORMAL]               = "#FFFFFF"
#   bg[PRELIGHT]            = "#FFFFFF"
#    bg[ACTIVE]               = "#000000"
#   bg[SELECTED]            = "#FFFFFF"
#   bg[INSENSITIVE]            = "#FFFFFF"

#   base[NORMAL]            = "#FFFFFF"
#   base[PRELIGHT]            = "#FFFFFF"
#   base[ACTIVE]            = "#FFFFFF"
#   base[SELECTED]            = "#FFFFFF"
#   base[INSENSITIVE]         = "#FFFFFF"

  text[NORMAL]            = "#FFFFFF"
  text[PRELIGHT]            = "#FFFFFF"
  text[ACTIVE]               = "#FFFFFF"
  text[SELECTED]            = "#FFFFFF"
  text[INSENSITIVE]            = "#FFFFFF"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

Place the file in /home and call it .gtkrc-2.0

As you can see, there are a number of different things you can play with in that file, just uncomment what you want and have a play with the colours.

You'll need to restart for it to take affect (CTRl ALT BACKSPACE)

Wow.. I want to know more about that. What made text files edit font color? Where can I learn more about that?

---

### Post by califman831 on 2006-12-31
a short utility that handles that file shouldnt be that hard to come up with, anyone know of any?

---

### Post by wersdaluv on 2007-01-01
> **Ambimom said:**
> A few days ago, someone here turned me on to: 

gnome-color-chooser  ([http://www.gnome-look.org/content/show.php?content=47349](http://www.gnome-look.org/content/show.php?content=47349))

		[http://www.gnome-look.org](http://www.gnome-look.org)
Requirements:
- libgtkmm >= 2.8.0
- libglademm >= 2.6.0
- libxml2 >= 2.6.0

It works like a charm!  Once installed, it is on the Systems Menu/Preferences.

If you've never installed anything before [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) will show you how!

I have followed the monkeyblog instructions by running the configure file. As the terminal seemed to react well, I expected that the installation was succesful. When I looked at System-->Preferences, I didn't see the GNOME color chooser app. What could have went wrong? What do I do now?

---

### Post by Ambimom on 2007-01-01
LOL, I had the same reaction at first....It's there, but it doesn't appear in the Preferences menu until after you boot the next time.  You can open it now by going into the terminal and typing gnome-color-chooser.

Enjoy!

---

### Post by wersdaluv on 2007-01-01
I already restarted my laptop but the app is still missing.

I tried to install it again and as I was installing, this appeared in the terminal: 

"/bin/bash: /home/allan/Extracted: No such file or directory
configure: WARNING: `missing' script is too old or missing

checking for ANSI C header files... no
checking for sys/types.h... no
checking for sys/stat.h... no
checking for stdlib.h... no
checking for string.h... no
checking for memory.h... no
checking for strings.h... no
checking for inttypes.h... no
checking for stdint.h... no
checking for unistd.h... no

checking whether we are cross compiling... no

checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for ANSI C header files... (cached) no

checking whether C++ has buggy scoping in for-loops... no

checking whether user wants warnings... no"

I those negative things and I think those state what my problem is. What can I do?

---

### Post by Ambimom on 2007-01-01
I downloaded the gnome color chooser and then followed the instructions for installing tar.gz files on [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

As I recall, I made sure I had  the following installed:  You can install these with Synaptic.

- libgtkmm >= 2.8.0
- libglademm >= 2.6.0
- libxml2 >= 2.6.0

and the  Build-essential package, also available in Synaptic.

> Once these are installed, you open the terminal and navigate to the directory in which you've extracted the color chooser files.  The monkeyblog shows you how to do this as well.

When you're in the correct directory you execute a configure script: ./configure. The purpose of the configure script is usually to check for dependencies and then create the makefile. If the script fails for some reason and tells you to install certain packages, look up the names in Synaptic (Important! If you find packages in Synaptic named almost the same but with a -dev extension, remember to install those as well! They're development packages and are needed for compiling). Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways:

Normal install: If you want to install it the normal "primitive" way, type sudo make install. To remove the temporary files you run make clean. To uninstall the program you run sudo make uninstall. These two clean-up commands don't always work, though, the programmer needs to have enabled them. 

Package manager install: If you want to install it in a way that means it can be easily removed from inside the package manager, first install the package checkinstall. To install the package type sudo checkinstall. This will take slightly longer than a normal install and quite possibly you'll have to supply a description of the application yourself (and edit the other information slightly). If the need arises, this will be easy to take care of from inside the checkinstall program.


It worked for me.  I took it very slowly...step by step. 

I wish I could decipher your error messages but I am relatively new to linux. 

Good luck.

---

### Post by wersdaluv on 2007-01-01
> **Ambimom said:**
> I downloaded the gnome color chooser and then followed the instructions for installing tar.gz files on [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

As I recall, I made sure I had  the following installed:  You can install these with Synaptic.

- libgtkmm >= 2.8.0
- libglademm >= 2.6.0
- libxml2 >= 2.6.0

and the  Build-essential package, also available in Synaptic.


Ohh...

When I went back to the requirements, the packages I got from Synaptic are not updated. 

My libgtkmm is only ver. 2.4, my libglademm is only ver. 2.4, while my libxml2 is ver. 2.6.26. Could that be the problem?

---

