---
title: "I need to be a root user?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-06-06
I am trying to burn my lightscribe DVD and downloaded the stuff I needed but now when I am about to print the image, it tells me I need to be a root user.  How do I get around this?

---

### Post by loathsome on 2007-06-06
Run the application with **gksu** (gksudo)

[COLOR="DarkSlateGray"]**$ man gksu**[/COLOR] for more information.

---

### Post by bean77 on 2007-06-07
Sorry, I have no idea what that means.

---

### Post by reckless2k2 on 2007-06-07
what program are you using to lightscribe?

---

### Post by Hendrixski on 2007-06-07
:-) that's Ok... what he meant was that if you run your application from the terminal you can specify to run it as a root user.

how do you get a terminal?  click applications-->accessories-->terminal

then in the terminal type gksudo application_name

when you want to learn more about a comand in the command line you type "man" to get the manual.  for example man gksu will tell you all about how to use gksu.

There's probably an easier way to do it than the command line... just, that's how it used to be done so that's how we're used to doing it... I know, very antiquated isn't it?

---

### Post by Hendrixski on 2007-06-07
Also.. don't get in the habit of running applications as root user.

Root user means that you have UNLIMITED privileges to the computer.  meaning you can accidentally delete everything, or accidentally change something that you shouldn't.  Imagine if you ran firefox as a root user, and some webpage installed a script that then spammed all of your email contacts.  That would be bad... so normally, try to avoid doing anything as root user.

---

### Post by bean77 on 2007-06-08
Great tips-thank you!  I am using Lacie for Lightscribe burning.

---

### Post by bean77 on 2007-09-29
So if my program is located here:

/home/lydia/Desktop/usr/4L

What do I type in the command line?

---

