---
title: "Would like to use Azureus as by default Bit Torrent Client"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Blood Red Sandman on 2006-10-18
How do I got about installing and configuring[Azureus](http://azureus.sourceforge.net/) as my default Bit Torrent Client under Ubuntu?

Currently I am Bit Torrenting with Ubuntu's default Bit Torrent cleint, however I would rather abuse my ISP's Bandwidth with Azureus instead. :twisted:

---

### Post by randomi on 2006-10-18
Easiest way is to use apt

```
sudo aptitude install azureus
```

That will install and configure Azureus for you.

---

### Post by x64Jimbo on 2006-10-18
1. Install it from the repos
2. Set GNOME's app affinity for .torrent files to Azureus (System > Preferences > Preferred Applications)
3. Enjoy!
4. You might also want to turn on mandatory traffic encryption to make sure your ISP can't throttle your traffic based on its type.

---

### Post by Blood Red Sandman on 2006-10-19
Dumb question because I am still new to ubuntu.....
What's an apt?

What's an Repo?

---

### Post by sebbex on 2006-10-19
> Easiest way is to use apt

```
sudo aptitude install azureus
```

That will install and configure Azureus for you.

in other words he is saying to open the terminal/konsole and enter that code.

---

### Post by maaronB on 2006-10-19
> **Blood Red Sandman said:**
> Dumb question because I am still new to ubuntu.....
What's an apt?

What's an Repo?

If you are that new it might be easier to do everything graphically(though you should eventually learn the command line).  


*1. Install it from the repos*
To do this with graphics.

Open up Applications.  
Click on Add/Remove.
Click Advanced.
This opens up the Synaptic package manager.
*A repository is the location for a collection of programs that you can easily download and install.  Apt is a commandline tool used to access the repository and download/install the program.  Synaptic is a graphical program that does the same.*
Go to Settings, click on Repositories.
Check all boxes. 
Then go back to main synaptic menu and simply type Azureus into the search box.  
Check Azureus.
Click Apply.
Then Azureus will be installed on your computer.

Then to make Azureus the default you can do it two ways.
like x64Jimbo said.
2. Set GNOME's app affinity for .torrent files to Azureus (System > Preferences > Preferred Applications)
or if you have a torrent.
Right click on the torrent, click on Open With.  click on Azureus.

That your done.

---

### Post by gentlemanmasher on 2006-10-28
> **x64Jimbo said:**
> 1. Install it from the repos
2. Set GNOME's app affinity for .torrent files to Azureus (System > Preferences > Preferred Applications)
3. Enjoy!
4. You might also want to turn on mandatory traffic encryption to make sure your ISP can't throttle your traffic based on its type.


While reading through the forms to fix my Azureus problem I came across this thread which fixed my problem.  It did raise another question which I didn't seem to find posted anywhere.  
How do you turn on mandatory traffic encryption?](*,)

---

### Post by x64Jimbo on 2006-10-28
It's in your Azureus options. Check your preferences.

---

