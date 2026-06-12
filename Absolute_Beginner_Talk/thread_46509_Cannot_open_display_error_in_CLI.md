---
title: "Cannot open display error in CLI"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-05
My Ubuntu desktop has finally kicked into a satisfying order, but as of yet, I am still unable to enter the desktop as the root/superuser.

When I run the command  "gksudo nautilus" from the CLI, I get the error, "
cannot open display." I had to edit the fstab to mount my windows disks, but running "gedit" also throw out the error "cannot open display." I tried random programs from the CLI, but I almost always get the "cannot open display" error.

Using ALT-F7, I can always change back to the desktop, but not being the superuser, I cannot edit the files. Via the desktop, I can open "gedit." I worked around the problem by changing ownership, but that is no fun. 

Another problem I experience is my monitor seems to be too small. I have only one option which is right, and that is  800x600. Some programs seems to go right over the screen, and I cannot resize it to see all the buttons. Is the two problems maybe related? The man files run of the right hand side of my screen, but I can scroll there with the cursors.

---

### Post by Knome_fan on 2005-07-05
Are you trying to run these programs from a console (Alt+F[1-6])? If that's the case it won't work unless you export the DISPLAY variable first, iirc. Don't ask me how to do it, I can't remember, but google should help out here.

But the easiest solution would be to simply fire up gnome-terminal and start the applicaten with sudo $application from there.
Or simply use Run as different user, which should be under System in your Gnome menu and start the application from there.

Hope this helps.  :grin:

---

### Post by GrootBrak on 2005-07-05
> Are you trying to run these programs from a console (Alt+F[1-6])? 

Yes, I did that. The rest of Export  display variable is completely lost on me. What do you mean by that?

I'm a bit lost with the following line "fire up gnome-terminal and start the applicaten with sudo $application from there." Do you mean open the terminal window in the desktop? I've done that, but did not get anywhere. Originally I understand that was the CLI with Gnome! Then I learned about ALT F(1-6).

I will try and run as different user from the the desktop. Never tried that though. ;-)

---

### Post by Knome_fan on 2005-07-05
Hi, sorry for not being to clear.

The problem if you are trying to start a graphical app from ALT+[F1-6] is that your computer simply doesn't know where to start this app. For example there could be several graphical desktops running on your machine. So in order for this to work you'd have to tell Linux which desktop to use and you can do that by exporting (that is setting) a variable that tells it what to use. I hope this made more sense now, but it isn't really important anyway.

The easiest and best way to start a graphical app is from an already running graphical environment, as the problem I just describe simply doesn't exist then.

So, yes, I mean that you have to open a terminal window in the desktop. Now if you want for example to start gedit as root, simply type sudo gedit. It now should ask you for your users password and then launch gedit. (Rember, Ubuntu uses sudo, so you can get root rights with your users password. There is no seperate root password.)

Hope this made more sense now.  :grin:

---

### Post by GrootBrak on 2005-07-05
Thank you. Makes sense now about the Xporting and why my desktop won't run from Nautilus. I have  not yet founf any info regarding it in the manuals I have. Maybe you have link as to where to hunt?

Tonight I will try out the terminal window. What you describe sounds familiar. I have edited the Lilo-config that whay before. At the time I thought it did not work because I was unable ti "run lilo again" as I got in the help files. Only later did I realise that  the lilo I was running was in a completely different directory to to one that was neaded! That's the reason I gave up the terminal window in favour of the CLI!!! 

Will keep you in the loop. There is still hope!

---

### Post by GrootBrak on 2005-07-05
Heck no. This is too much trouble. Here is the thing. I want to click and drag and copy and paste and whatever file operations I need to do without having to type in every single command. I am going to post a new thread, so please check back on it.

---

