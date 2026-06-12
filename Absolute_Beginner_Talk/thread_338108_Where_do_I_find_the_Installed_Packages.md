---
title: "Where do I find the Installed Packages"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by ekka on 2007-01-14
Hi all

Where do I find the packages that I have recently installed? My synaptic package manager shows a large list of packages that are installed on the system but I don’t find them on the applications menu. Sure I can start them in a terminal, but is there a better way to do it. 
Can I update my menu list with all the applications that are installed on the system? How do I create a shortcut to a package (similar to an .exe) on the desktop or menu?

thanks

---

### Post by taurus on 2007-01-14
What apps did you install?  Sometimes, logging out and back in again will get those apps to show up on the menu.

---

### Post by ekka on 2007-01-14
Well I have been installing a lot these days like system and office utilities. Some of them do come up in the menu list but not all.

---

### Post by Sef on 2007-01-14
Try alt + F2.  That will give you Run Application.   Then type in the app name.  Hint: The names are case sensitive.

---

### Post by ekka on 2007-01-14
Do I need to do that every time I want to run the application? Is there any way of creating the shortcut in the menu list?

---

### Post by mojoman on 2007-01-14
> **ekka said:**
> Do I need to do that every time I want to run the application? Is there any way of creating the shortcut in the menu list?

How about the ala carte menu editor? Couldn't you use this to get your appz on the menu? (and that should already be on the menu...)

/Mojoman

---

### Post by ekka on 2007-01-14
Alacarte Menu Editor sure sounds promising. I will try it when I go back home. Any idea where I can find the executables for the installed packages (which are not there in the menu)? In Windows by default it is “\Program Files\Package\package.exe”
Thanks

---

### Post by oyvindaa on 2007-01-14
They usually go in /usr/bin 

Just do a 

```
whereis program_name
```

or a 

```
locate program_name
```

in the terminal. (Applications --> Accessories --> Terminal).

It's also normally enough to type the name of the program in the terminal to start it, i.e ```
firefox
```

---

### Post by wesley_of_course on 2007-01-14
in  a   terminal , (Applications --> Accessories --> Terminal),

      
      command ;

             update-menus


     Just a thought .

---

### Post by mojoman on 2007-01-14
> **ekka said:**
> Alacarte Menu Editor sure sounds promising. I will try it when I go back home. Any idea where I can find the executables for the installed packages (which are not there in the menu)? In Windows by default it is “\Program Files\Package\package.exe”
Thanks

The advice from oyvindaa and wesley_of_course are good tips, especially if you're trying to locate something that isn't installed from the standard repositories (say, from a .deb or a tarball). However, if you've installed something from the standard repositories chances are pretty good that you can add it to your gnome menu by using alacarte menu editor. Also, if you activate the debian menu (in the alacarte menu editor) you get the debian menu under applications and it shows, I think, just about anything you got installed.

/Mojoman

---

### Post by ekka on 2007-01-14
Thanks Mojoman

I will sure try those tips. All my installations are from standard repositories using automatix2 and Synaptic. I have already installed the debian menu but not all of them are in it either. I will try your tips and see what happens.

Thank you all for the help.

---

### Post by ENN0 on 2007-01-14
<sorry>

---

