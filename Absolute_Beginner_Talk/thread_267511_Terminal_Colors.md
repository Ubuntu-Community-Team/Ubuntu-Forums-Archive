---
title: "Terminal Colors"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by DarkOdysseus on 2006-09-28
how do you change the colors of the Ubuntu terminal?
can you include an example?

---

### Post by bodhi.zazen on 2006-09-28
What colors? text, background ? window dressings ?

---

### Post by DarkOdysseus on 2006-09-28
background and text

---

### Post by bodhi.zazen on 2006-09-28
Right click on the terminal and select preferences.

Edit profile.

---

### Post by FyreBrand on 2006-09-30
I've recently done a reinstall of Dapper.  I noticed that previously the shell text was colored for directories and different file types (like executables).  Now all the text is black.

I looked in the terminals default profile which is the only profile.  I am using the colors from the system theme (that box is checked) and under palette the built-in scheme is "Linux console".

Is there a config file that I should edit?  I am still learning the terminal and shell commands. I want to make sure I do this the right way and I'm not breaking something by messing with stuff I shouldn't.

edit: ok after a little bit of research I realized that I don't have a local .bashrc file.  When I did my latest reinstall I moved my /home directory structure to a seperate partition.  I actually only moved my data files to the same username and then reinstalled Dapper.

I don't know where I made my error, but somehow I didn't get a local bashrc file when I reinstalled.  So my question would be how do I generate an appropriate local bashrc file?

---

### Post by jpmorelli on 2006-10-02
I have the same problem you have, and with your post now I know what is wrong so I copy the .bashrc file from root's directory and chown it for my user.
That's it ! It is working now ! :D

---

### Post by syxbit on 2007-12-31
i'd like to know a way to have black background and white text, but done by editing your .bashrc.
i know you can edit the terminal profile to do it, but since i backup my .bashrc and restore it anyway, it would be quicker
any ideas?

---

