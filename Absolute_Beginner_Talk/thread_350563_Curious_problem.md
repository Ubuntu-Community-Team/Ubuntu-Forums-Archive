---
title: "Curious problem?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-01-31
Hi,

If I open an application such as Mozilla then open a second application, the Terminal for example, a curious problem arises.  When I move the mouse pointer to the newly opened application (the Terminal which has been opened above Mozilla) it disappears behind the first opened application.

Copying and pasting terminal commands becomes a real pain in the application when this problem continues to occur.  The only thing I have tried to do recently, that may have had some effect on my system, is install Beryl (with no success I might add!).  This has now been uninstalled.

Please advise.

---

### Post by saadakhtar on 2007-01-31
check your xorg.conf.
i installed beryl on my pc a while ago it is running fine but i do understand that it makes some changes to your xorg.conf.
please open terminal "konsole"
and type in:

sudo  nano /etc/X11/xorg.conf

or use your favorite text editor (just change nano to the other text editor etc. "vi")

Post your entire xorg.conf.

i am sure i can help you with this issue.

---

### Post by ComplexNumber on 2007-01-31
> **Norfolk 'n' Good said:**
> Hi,

If I open an application such as Mozilla then open a second application, the Terminal for example, a curious problem arises.  When I move the mouse pointer to the newly opened application (the Terminal which has been opened above Mozilla) it disappears behind the first opened application.

Copying and pasting terminal commands becomes a real pain in the application when this problem continues to occur.  The only thing I have tried to do recently, that may have had some effect on my system, is install Beryl (with no success I might add!).  This has now been uninstalled. 

Please advise.
are you using kde or gnome? i woud bet tat you're using kde, if i understand your problem correctly.
also, you don't say if you click on the application - that would bring that application into focus. 

on kde, i know you can configure the mouse so that the user merely has to move the mouse anywhere on an application (without having to click on the app) for the that application to get focus. go to the kde control centre and select 'peripherals', then "mouse". change it in there.

on gnome, go to main menu -> system -> preferences -> windows. see the screenshot - on your system, it should be ticked.  untick the top tickbox.

---

### Post by Norfolk 'n' Good on 2007-01-31
Thank you Saadakhtar for your suggestion.  This was in fact what I was worried about; erroneous changes to my config files after trying to install Beryl.  As it turned out the second posting from ComplexNumber fixed my problem.  I am in fact using a Gnome setup, but from the attached screenshot I easily rectified the problem.

Once again guys (and gals - if the case may be), Thank you.

---

