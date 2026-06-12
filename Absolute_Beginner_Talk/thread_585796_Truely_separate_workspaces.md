---
title: "Truely separate workspaces?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by sullitf on 2007-10-21
I just installed Ubuntu 7.10 last week and completely wiped XP from my harddrive, and I have absolutely no regrets.  One of my favorite features of this OS (and Linux in general) is the separate workspaces.  I love being able to separate program windows and keep everything more organized, though I did have one question about it.  Does anyone know of a way to make the desktops truely separate?  By that I mean storing files on one desktop without it showing up on all the others as well.  On the same note, I think it would be even better if I could do the same thing with Widgets (I am using gDesklets).  I am currently using 4 different "desks," and want to take advantage of this by having separate uses for each (i.e. a school desk, work desk, work-in-progress desk, ect.).

I don't know if this is already possible and I just haven't found out how, or if it would be extremely difficult to do.  I am new to Linux so I don't know how it all works, but this is my guess.  It seems that the workspaces are set up to all load from /home/tony/desktop (in my case).  Would it be possible to create subfolders in there such as /home/tony/desktop/school or /home/tony/desktop/work and then change what each individual desk loads from to corrolate?  Again, this is just my guess as to how it could be coded and could be totally wrong, but if this seems possible or if there are any other ways that may work I would love to hear them, cause that could be a very good feature to help organize desktops even further.

---

### Post by Dr Small on 2007-10-21
I don't think so, but who knows. Maybe someone smarter than me knows how to do it, if it is possible.

If it isn't, I would write it in as a blueprint on Launchpad.net


Dr Small

---

### Post by adamorjames on 2007-10-21
So basically having each desktop be like a separate folder, doesn't seem too hard but who knows :lolflag:.
EDIT: You know what would also be cool? Changing which folder you want your desktop to use. Like DE preferences.

---

### Post by Beggar on 2007-10-21
While you can't arbitrarily change the desktop location, using the gconf key /apps/nautilus/preferences/desktop_is_home_dir you can set the desktop to be the home directory for the user. But thats not really useful here.

In regards to the OP, theoretically you could set up a different user account and have each one configured differently. For example beggar-school, beggar-surfing, beggar-private. The switching would be provided by our shiny new fast user switching option in 7.10. I think this would be the use case most ubuntu devs would come up with for your scenario.

---

### Post by sullitf on 2007-10-22
I guess the user profiles could work.  I have no idea how the desks are set up, so I was just hoping it would be possible.  Does anyone know if each desk is loaded separately or are they all loaded as one and just mirrors of the first?  If they are separately done it should be possible, because if I could get to the command that tells each individual desk what file to load from I could change it from there, though I am no programmer and know even less about how the desktops are set up so I could be trying to figure out something that is currently impossible.  Anyone know specifically how the multiple desks work?

The reason I'm hoping it could be done without profile switching is because 
1) I'm running a Dell Inspiron 1150 with 256 ram and it is barely enough to run Ubuntu (though still much faster than Windows was)
2) I don't know if the different profiles would cause problems with moving windows from one desk to another.


I know (2) seems like a contradiction to what I am hoping to achieve, but I am more so looking for the ability to have files saved to one desk rather than all desks, but I still like the versatility of being able to move windows freely from one desk to the other.

---

### Post by cfaulkner on 2007-10-22
I had my Gentoo setup with each desktop had it's own space, meaning i couldn't cross windows from one to the other.  Display was 0.0 and 0.1 respectively

---

### Post by sageb1 on 2007-10-22
as i understand it the workspaces are part of a virtual workspace.

think of  your current workspace * the number of workspaces.

it is more graphical than physical i.e. four 800x600 workspaces have a virtual workspace dimension of 3200 x 2400.

it is similar to the concept of the Tardis where the inside of the Doctor's "ship" is many times larger than a typical UK BT phonebooths.

you can put apps in other workspaces but any folders created in workspace x also shows up in the first workspace.

**i am open to another interpretation of workspaces.

---

### Post by barkej on 2007-10-22
Sounds like a cool feature. I've yet to see it done though.

---

### Post by sullitf on 2007-10-22
I guess this is just a concept I will have to hope to see in the future, cause it sounds like it would require a complete overhaul of the current "desk" system.  Too bad, I was hoping it could be a simple tweak

---

### Post by cfaulkner on 2007-10-22
you mean something like this?

[http://www.youtube.com/watch?v=Y_JDZBZhvmA](http://www.youtube.com/watch?v=Y_JDZBZhvmA)

---

### Post by adamorjames on 2007-10-22
> **cfaulkner said:**
> you mean something like this?

[http://www.youtube.com/watch?v=Y_JDZBZhvmA](http://www.youtube.com/watch?v=Y_JDZBZhvmA)

Awesome. So it would seem if there was a way to somehow emulate having ,more than monitor then it would be done. Seems not too hard for a dev to do. Make it where when you cllck a button it sends false info which makes you have more than one desktop. Meh, who knows.. :lol:

---

### Post by cb474 on 2007-10-30
Yeah, I've often wished I could have more than one desktop too. Mainly it would be nice simply if in different workspaces there could be different files and folders on the desktop. In a sense it would be like treating all the workspaces together like one big extended desktop, but viewed in separate parts. Something like this exists in Fluxbox, I think, and Enlightenment. But I'm generally not into those systems.

---

### Post by Kat of Zion on 2007-12-20
First off, I hope that this isnt construed as bringing up a "dead thread" but I have been wonderin about this feature since I started finding a need for using multiple desktops.  For example, if I send one browser window to "Desktop 3", the task bar at the bottom will still show that browser window in any of the other desktops as well.  

I understand why there might not be a way to have program/browser window COMPLETELY sent to one particular desktop/workspace.  You might forget that you have it open because you forgot that you were using multiple workspaces that day.  Still, the graphics within the workspace applet do help you remember so I could see myself still finding this a nice option to have.  

Any ideas?

-multibrowser gal Kat

---

### Post by Samhain13 on 2007-12-20
You can right-click on the Window List, choose preferences and select "Show windows in all workspaces" under Window List Content. :)

Err... that is if I understood you correctly.

---

### Post by Kat of Zion on 2007-12-20
Actually I do not get that option there at all.  Im still using Feisty Fawn but the only options it gives me is to set the amount of desktop/workspaces and if I want the mousewheel to make the workspace switch automatically when the mouse is atop it in the applet.  Thats it. :(

---

### Post by Samhain13 on 2007-12-20
I should have seen from your details that you're using Kubuntu. It works a bit different, sorry. I thought you were also using Gnome.

---

### Post by cormic on 2007-12-24
>  if I send one browser window to "Desktop 3", the task bar at the bottom will still show that browser window in any of the other desktops as well 

I have just installed Kubuntu and would love to know how to do this.  It was simple in Gnome.

---

### Post by cormic on 2007-12-24
> **cormic said:**
> I have just installed Kubuntu and would love to know how to do this.  It was simple in Gnome.

I have just found it....

Click on the little up arrow on your taskbar and click "configure taskbar". Then untick "Show windows from all desktops" 

I am very happy now :)

---

### Post by Kat of Zion on 2007-12-24
It was that easy. Hah!  Where iis a dunce cap when you need it?

---

