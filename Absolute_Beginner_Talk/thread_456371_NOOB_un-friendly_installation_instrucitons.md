---
title: "NOOB un-friendly installation instrucitons"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Killtown on 2007-05-27
Myself and my friends who I've gotten to switched over to Ubuntu are finding a lot of installation instructions are not NOOB friendly.

For instance, we are trying to set up our webcams and [the instructions]("https://help.ubuntu.com/community/EasyCam") say:

> Add the following line to your /etc/apt/sources.list

Great, so we would add the following line to our "/etc/apt/sources.list" if we knew where it is and how to add lines to it.

So:

1) you see how these kinds of instructions are not NOOB friendly?

2) really, how do we add lines to the  /etc/apt/sources.list ?


This post should be taken mostly as a constructive criticism and partially about frustrated NOOB's.

---

### Post by yabbadabbadont on 2007-05-27
> **Killtown said:**
> Great, so we would add the following line to our "/etc/apt/sources.list" if we knew where it is

Hmmm, so if it had been windows and said, "edit c:\etc\apt\sources.list and add the following..." you would have done what?  Perhaps opened the file with a text editor...  as for not know where it is, it gave you the full path to the file.  The only thing those instructions probably should have included was something like, "edit /etc/apt/sources.list and add...  You will need to use gksudo to run your editor (gedit is a nice one) in order to have permission to save your changes."

As for the quality of the documentation, as with most things in life, you get what you pay for...  ;)  :D

---

### Post by Killtown on 2007-05-27
> **yabbadabbadont said:**
> 1) Hmmm, so if it had been windows and said, "edit c:\etc\apt\sources.list and add the following..." you would have done what?

2) As for the quality of the documentation, as with most things in life, you get what you pay for...  ;)  :D
1) Gone to a Windows forum and b*tched and complain:  "how do I do that?"

2) Ain't that the truth.


So again, how do I do this:

> Add the following line to your /etc/apt/sources.list

      deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main


---

### Post by ahaurw01 on 2007-05-27
Yeah, just type
```
sudo gedit /etc/apt/sources.list 
```
in a terminal, go to the end of the file and paste whatever they tell you to paste.
Alternatively, if you must use a GUI, go to System->Administration->Software Sources, click on the Third Party tab, then click on Add and paste whatever they tell you into the box that pops up. 
If i've learned anything about linux, its that you sometimes have to roll up your sleeves and get dirty. Because of the extreme customizable nature of it all, it sometimes requires a little more tinkering than you might be used to in windows or OSX. 
happy installing :)

---

### Post by Lucifiel on 2007-05-27
> **Killtown said:**
> 1) Gone to a Windows forum and b*tched and complain:  "how do I do that?"

2) Ain't that the truth.


So again, how do I do this:

Press Alt + F2.

Paste this command into the pop-up box. Note: gksudo allows you to edit as root but only use it when you're unable to open or save a file or folder(permission errors). 
> 
gksudo gedit /etc/apt/sources.list

:) Well, have fun! :)

Ubuntu is different from Windows, so you will have to use different ways than the ones you were used to in Windows. :) Ubuntu = another operating system. Ubuntu does not = to Windows.

---

### Post by benmoreassynt on 2007-05-27
> 

1) really, how do we add lines to the  /etc/apt/sources.list ?

2) you see how these kinds of instructions are not NOOB friendly?


This post should be taken mostly as a constructive criticism and partially about frustrated NOOB's.

I know what you mean, but it is just like learning to use Windows for the 1st time.

Explanation. Adding that line means you can download a lot more software.

You do not need to actually edit the sources list by hand. Instead you can open the Synaptic Package Manager (if using Ubuntu and not Kubuntu). Click Settings and then Repositories and then Third Party Software. Click Add and then paste "deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main" into the box.

A lot of people will tell you the 'command line' way of doing stuff, because once you get familiar with it, it is often quicker.

For example.

/etc/apt/sources.list is a text file which contains all the places you can download software from. The line includes the "path" to the file, so it actually tells you where it is on your hard drive. 

In Windows you may be familiar with this sort of thing: "C:\Program Files\Microsoft Office\setup.exe". In Linux the same idea is put this way:

/some_directory/some_other_directory/sources.list, where sources.list is a text file.

If the 'path' begins with a '/', it is telling you where the file is in relation to the 'root' of your hard drive. Which is equivalent to C:\ on Windows.

So to edit a file you would usually use the Nautilus file manager to navigate to it, and then open it by double clicking.

BUT, because sources.list is an important system file, you will not be able to open it using your default Ubuntu account! Instead the easiest thing to do is to give up on the GUI way of doing things for a minute and do this:

Open a terminal window.

Type:

```
sudo gedit /etc/apt/sources.list
```

Enter your usual password when prompted

What you are saying there is 'Using 'gedit' (the text editor) open the file called sources.list which is in the /etc/apt/ directory. Gedit will open with the file. You can change it, save, and then close the window and the terminal window.

There is a way to do this in a 'gui/Windows' manner, but it will take longer. For that reason, people who are experienced with Linux will often tell you the 'command line' way of doing things. You can do the same in Windows, but it is much more rare that people do any more, even though the Windows terminal can be equally quick.

---

### Post by Killtown on 2007-05-27
Ok thanks everybody for the actual NOOB friendly instructions!  ;)


The easycam2 program installed, but now can't find my webcam.  Any links that can help me with this?

(and yes, my webcam is plugged in.)

---

### Post by shen-an-doah on 2007-05-27
> **benmoreassynt said:**
> A lot of people will tell you the 'command line' way of doing stuff, because once you get familiar with it, it is often quicker.

There is a way to do this in a 'gui/Windows' manner, but it will take longer. For that reason, people who are experienced with Linux will often tell you the 'command line' way of doing things. You can do the same in Windows, but it is much more rare that people do any more, even though the Windows terminal can be equally quick.

Another reason is that people might be running different Desktop environments. Doing it via the GUI is different in GNOME, KDE and XFCE, but sources.list will always be in /etc/apt, no matter what environment you use.

---

### Post by rillip on 2007-05-27
As for getting the webcam detected, I'm not really sure as I haven't tried it.  Hardware manufacturers tell you what OS they support - typicall some version of Windows.  Maybe it works in other versions, maybe it doesn't.

In this case, maybe Linux will detect it, maybe it won't.  It's really the hardware manufacturer's job to provide the drivers.  You might try and Google "[your camera] linux" and see if it comes up with any suggeestions.  I did that with my digital camera and found a step by step guide on how to install what I needed for it to work.  They may or may not be new user friendly, you might have to research it. ;)

---

### Post by benmoreassynt on 2007-05-27
Do a search for the specific bit of hardware on this forum. If no luck, try the Ubuntu wiki. If no luck, try Google and the manufacturer. Most hardware is pretty well covered, but you do get teething troubles.

---

### Post by Sonix3D on 2007-05-27
Don't make the switch until you're 100% sure you're ready.

---

