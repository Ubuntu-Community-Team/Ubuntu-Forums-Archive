---
title: "Video card driver problems"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by darthlunchbox42 on 2008-02-15
I just installed Ubuntu 7.10 a little bit ago, and I'm am trying to install my video card's drivers.  Eventually, I found System -> Administration -> Restricted Drivers Manager

I open it up and I kind of get the feeling that Ubuntu doesn't like my video card.  It gives me the message:
> Proprietary drivers do not have public source code that Ubuntu developers are free to modify.  They represent a risk to you because they are only available on the types of computer chosen by the manufacturer, and security updates to them depend solely on the responsiveness of the manufacturer.  Ubuntu cannot fix or improve these drivers.
Below that it has the option to enable the 'NVIDIA accelerated graphics driver (latest cards)'.  I click the enable option and a warning comes up saying:
> The software source for the package

nvidia-glx-new

is not enabled.

I have [this](http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=268341) card.  I have the driver that installs it on Windows, but big load of good that will do me here, I suspect.

---

### Post by oedha on 2008-02-15
you have to give what it wanted.......nvidia-glx-new
first...make sure your software source is pointing to an ubuntu server
then reload
after that...you can go to add/remove 
search nvidia in all available applications
actually after to finish with the software source.....when you try to enable that card...it will automatically search for it online

---

### Post by skymera on 2008-02-15
try Envy

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

