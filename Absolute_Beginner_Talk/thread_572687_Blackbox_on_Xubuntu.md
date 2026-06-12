---
title: "Blackbox on Xubuntu"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2007-10-10
Hello firends

I am thinking in replacing Xfce with Blackbox in Xubuntu. I read that Blackbox was really fast. Do you know if it's faster than Xfce? I need it as a frontend for my server, so speed and low use of RAM are my goals.

Has someone tested this? How where the results?

Thanks!

Jordi

---

### Post by rscott5 on 2007-10-10
This link may help a little: [http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

The things that stuck out to me are that Blackbox has nearly zero library dependencies and "ultra low memory consumption." The other thing to note is that Xfce is a full environment while Blackbox is simply a window manager. Hope that helps :-)

---

### Post by por100pre1 on 2007-10-10
You can also try Fluxbox which is based on Blackbox. [Here]("http://ubuntu-utah.ubuntuforums.org/showpost.php?p=3245368&postcount=6") is the way I installed it.

---

### Post by jordi_rc on 2007-10-11
Thank you all for your answers. I will read all that and try.

:popcorn::popcorn::popcorn:

Jordi

---

### Post by RedSquirrel on 2007-10-11
> **jordi_rc said:**
> Hello firends

I am thinking in replacing Xfce with Blackbox in Xubuntu. I read that Blackbox was really fast. Do you know if it's faster than Xfce? I need it as a frontend for my server, so speed and low use of RAM are my goals.

Has someone tested this? How where the results?

Thanks!

Jordi

I would recommend Fluxbox as well. Blackbox is not being worked on anymore. 

```
sudo apt-get install fluxbox && sudo update-menus
```The first step installs the fluxbox package and the second step creates the default menu. :)

---

### Post by jordi_rc on 2007-10-11
Thank you RedSquirrel for your info. I will see it, it sounds better than Blackbox

To you: :popcorn::popcorn:

Just one question: is it as quick and uses as low resources as Blackbox?

Jordi

---

### Post by jordi_rc on 2007-10-11
I found another alternative that is GPL:

[http://icculus.org/openbox/index.php/Main_Page](http://icculus.org/openbox/index.php/Main_Page)

"Openbox makes desktop environments better. By running Openbox inside the GNOME or K desktop environments, you can combine their ease and functionality with the power of Openbox. Your desktop becomes cleaner and faster, and is in your control, when you use Openbox."

As I use Xubuntu, there is a page that explains how to use:
[http://icculus.org/openbox/index.php/Help:XFCE/Openbox](http://icculus.org/openbox/index.php/Help:XFCE/Openbox)

---

### Post by RedSquirrel on 2007-10-11
Fluxbox, Blackbox, and Openbox are all very light window managers. They're pretty close in terms of system resources consumption. I suppose Fluxbox might be a bit heavier, but not by much. Openbox is an active project and it is quite popular here on the forums. This thread has a fair bit of discussion:

[http://ubuntuforums.org/showthread.php?t=190476](http://ubuntuforums.org/showthread.php?t=190476)

---

### Post by por100pre1 on 2007-10-11
> **RedSquirrel said:**
> I would recommend Fluxbox as well. Blackbox is not being worked on anymore. 

```
sudo apt-get install fluxbox && sudo update-menus
```The first step installs the fluxbox package and the second step creates the default menu. :)

Thanks RedSquirrel for correcting the way I installed Fluxbox at that time. You were right, I made some unnecessary steps. I just have 5 months using Linux, I'm a n00b. :redface: ;-)

---

### Post by jordi_rc on 2007-10-11
And compared to Xfce? Are those systems much better?

Jordi

---

### Post by diatribe on 2007-10-11
they will all consume less resources than xfce, openbox is my preference of the three though

---

### Post by kellemes on 2007-10-11
> **diatribe said:**
> they will all consume less resources than xfce, openbox is my preference of the three though

Same here.. even Fluxbox seems a little slow sometimes. Although I like the slit a lot.

---

### Post by por100pre1 on 2007-10-11
> **jordi_rc said:**
> And compared to Xfce? Are those systems much better?

Jordi

Fluxbox is much lighter than XFCE, at least in my personal experience. However I have to make clear that XFCE has a file browser, text editor and many other programs Fluxbox doesn't have.

---

### Post by huckabuck on 2007-10-11
Will fluxbox work with thunar , or does it need rox filer ? i'm running fiesty xubuntu on a IBM T30 with a gig of ram ... i'd love to cut back on resources , but i dont know which would be better for flux ... thunar  or rox ... or if it doesn't matter  ... 

whats the best approach ?

---

### Post by shae on 2007-10-11
I am just going to toss this out there, but why do you not just use no DE and use ssh to run the server.  That would require even less resources than Openbox, etc.  If you are just new to linux and want a GUI, you might consider removing it once you are comfortable with the system.I believe there is even a GUI you can run on another computer that can control your other box through ssh but I cannot remember its name right now.

---

### Post by por100pre1 on 2007-10-11
> **huckabuck said:**
> Will fluxbox work with thunar , or does it need rox filer ? i'm running fiesty xubuntu on a IBM T30 with a gig of ram ... i'd love to cut back on resources , but i dont know which would be better for flux ... thunar  or rox ... or if it doesn't matter  ... 

whats the best approach ?

I guess you can use Thunar with Fluxbox, but that will require other xfce modules as well. I use rox-filer with fluxbox because rox-filer is lighter and it makes a good companion if you want go the lightest possible.

---

### Post by huckabuck on 2007-10-11
> **por100pre1 said:**
> I guess you can use Thunar with Fluxbox, but that will require other xfce modules as well. I use rox-filer with fluxbox because rox-filer is lighter and it makes a good companion if you want go the lightest possible.

OK , Does that mean i have to remove thunar , or xfce4 completely from the machine ? and can i remove them ... or will fluxbox automatically know to that Rox is there for it ? I've been reading several threads about fluxbox , and i like the comments about it . I like xfce4 , this machine is running great with it , but fluxbox looks very cool and intuitive .

---

### Post by John.Michael.Kane on 2007-10-11
> **huckabuck said:**
> OK , Does that mean i have to remove thunar , or xfce4 completely from the machine ? 

No you don't have to. after running the command posted to update the menu you log out, select sessions, and log into fluxbox via gdm.

> **huckabuck said:**
> and can i remove them ... or will fluxbox automatically know to that Rox is there for it ? I've been reading several threads about fluxbox , and i like the comments about it . I like xfce4 , this machine is running great with it , but fluxbox looks very cool and intuitive .
You can remove as much as you want,however doing it this way without knowing what you are doing or removing can lead to problems. 

Most users of lightweight WM build from a base install.

example: 
install command line system
Next install packages.
```
sudo apt-get install xorg fluxbox feh firefox  gksu synaptic thunar abiword xpdf scrot mplayer sylpheed-claws leafpad xarchive gtk-theme-switch system-config-printer
```
Then build from there

---

### Post by por100pre1 on 2007-10-11
> **huckabuck said:**
> OK , Does that mean i have to remove thunar , or xfce4 completely from the machine ? and can i remove them ... or will fluxbox automatically know to that Rox is there for it ? I've been reading several threads about fluxbox , and i like the comments about it . I like xfce4 , this machine is running great with it , but fluxbox looks very cool and intuitive .

No, if you have Thunar already in your system there's no problem in using it. :) My suggestion goes best for users who just want a very light environment. If you are already an XFCE user you can use Fluxbox with e. g. Thunar and Mousepad with good performance.

---

### Post by huckabuck on 2007-10-11
Thanks guys ... apologies to the OP for hijacking the thread for a minute  ...

---

### Post by RedSquirrel on 2007-10-12
> **por100pre1 said:**
> Thanks RedSquirrel for correcting the way I installed Fluxbox at that time. You were right, I made some unnecessary steps. I just have 5 months using Linux, I'm a n00b. :redface: ;-)

You're welcome. (I see you updated your instructions. :))

---

### Post by jordi_rc on 2007-10-12
> 
No you don't have to. after running the command posted to update the menu you log out, select sessions, and log into fluxbox via gdm.


This conversation is very interesting. Thanks for all the infos.
I actually like Xfce that comes with Xubuntu.

I see most of us want to free resources and have a graphical gui to deal with.
What I don't understand well is what needs to set free, I suppose it is CPU cycles, RAM memory and hard drive space, isn't it?

With a big hard disk, using 100 mb instead of 2 is not so big problem.

As I learn from you all, I see the graphical interface uses most of that CPU and RAM. If we have a minimalist GUI like Openbox, FLuxbox or Blackbox, we use few CPU cycles and RAM.
If we had not GUI at all, it would be nice but hard to deal with.

[B]In another post I asked about how to free resources. They said me this method:

1) Go to Applications/System/Services
2) Uncheck the 1st option regarding GDM.
3) We are sent to the console. We enter the password.

This way we abandon the graphical interface of our Xubuntu (or Ubuntu, I suppose) and they said me that all resources are now for the server to work (CPU, RAM).

To go back to the graphical interface, we type: "startx"

[/B](I noticed that at least in Xubuntu 6.04 I can't turn off the PC normally, but when I want to close I can open Terminal and use the commands "reboot" or "halt" and it goes OK).

**Is this method a good solution?** If it is, the choose of one GDM or another is not so important for a server. (We should still prefer one on the speed when working with it, anyway)

If it is, I will stay with Xfce or try a Fluxbox or Openbox, but exit the gdm when I have all running. But I won't uninstall the gdm so I can enter graphically when I want in the future.

Please opinions and advice.

Jordi.

---

### Post by jordi_rc on 2007-10-14
No one knows? :confused:

---

### Post by RedSquirrel on 2007-10-14
If you want to shutdown gdm, I would do it this way:

1. Logout of the desktop environment or window manager you are using. 
2. At the gdm login screen, press Ctrl-Alt-F2 to go to a console. 
3. Login there with your username and password. 
4. At the prompt ($), run the following command:

```
sudo /etc/init.d/gdm stop
```

When you want to use the GUI again, run the following command, which will start gdm and take you to the login screen:

```
sudo /etc/init.d/gdm start
```


You can also setup your system so that you don't need a display manager (e.g., gdm) at all. I'm not sure if I should go into that here since this is supposed to be Absolute Beginner Talk. I can provide the details though if you are interested. :)

gdm doesn't consume that much in terms of system resources, so if you are just going to use it to help you start the GUI occasionally, that sounds OK to me.

---

### Post by jordi_rc on 2007-10-14
Thank you RedSquirrel, I take note of your method, I will test it.

> gdm doesn't consume that much in terms of system resources, so if you are just going to use it to help you start the GUI occasionally, that sounds OK to me.


Having said that, I will test all blackbox derivates and keep the one I like most.
Thank you :)

Jordi

---

### Post by Hero of Time on 2007-10-18
These options sound nice, to use an even lighter WM. However, does Fluxbox or Openbox have system statistics to show? On Xfce what I run now, I added a few system stats on my top panel. I see if my wlan is connected and the link quality, processor usage, memory usage, processor speed, processor temperature, battery status and network utilization. Is that on others aswell?

---

### Post by urukrama on 2007-10-18
When you use Openbox or Fluxbox, you'll have to add applications to do so. You can use conky or gkrellm to do what you want to, or use the xfce4-panel in Openbox/Fluxbox (just add it to your autostart or startup file, and it will load whenever you start Openbox/Fluxbox).

---

