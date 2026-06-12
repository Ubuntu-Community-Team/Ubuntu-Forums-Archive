---
title: "My main problem with apt-get... Can anyone help?"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by quickk on 2006-12-06
Hi everyone,

   About 2 weeks ago, I installed Ubuntu 6.10 on my computer, and so far I have to say that I really like it (well, the 32bit version that is!).  By far, one of my major problems when I try to install something is finding the right package name to use with apt-get install.  

Here's an example that just happened to me: I'm trying to install HP printer drivers.  The installation script complains about a missing dependency: it seems that libjpeg isn't installed.  Ok, no problem, I try "sudo apt-get install libjpeg" but I get an error message "E: Couldn't find package libjpeg" .  This sort of thing happens all the time.  

Apt-get seems really nice, when you know the package name that you want to install.  If you don't, it seems that you are out of luck!  Am I missing anything?

Thanks for any help!

---

### Post by quickk on 2006-12-06
I forgot to mention that I was aware of synaptic package manager that can sometimes help by providing a search function.  Sometimes this works, sometimes it doesn't.  For my libjpeg problem, the only package that pops up if I search for libjpeg is libjpeg62, and is already installed.  Is this the same thing as libjpeg?  If so, why does the printer install script tell me I have a missing dependency?

---

### Post by ciscosurfer on 2006-12-06
Is there a reason you are trying to use a script to install your printer drivers?  Can you not install your printer through the Printer panel located under System > Administration > Printing ?

As for searching with apt-get, try using aptitude or synaptic (I know you mentioned this one, but it really is quite powerful when you use it correctly).  For aptitude, do the following:```
aptitude search ***any_letters_or_part_of_a_package_name_here***

LIKE THIS:

aptitude search gnom
aptitude search gnome-te
aptitude search gnome-terminal
```

---

### Post by kakalaky on 2006-12-06
What printer do you have?

---

### Post by quickk on 2006-12-06
Thanks for the replies.  The aptitude search command is exactly what I wanted.

My printer is the HP psc 2175 all-in-one (printer + scanner).  I can easily get the printer to work by using the printer panel, but absolutely cannot get scanning to work. When I open up Xsane, I can select my scanner/printer under available devices.  Then, I press the "OK" button, and Xsane seems to hang.  After a couple minutes I get this error message: "Failed to open device `hpaio:/usb/PSC_2170_Series?serial...': Error during device I/O. " 

I thought that perhaps if I downloaded the driver directly from HP, and followed their installation instructions, I'd get the scanner to work.  Well, I just got the script to work, the printer is reinstalled, but I still get the same error with Xsane.  

Any ideas?

---

### Post by ciscosurfer on 2006-12-06
Are you sure you're downloading a *linux* driver from the HP site?

---

### Post by quickk on 2006-12-06
Lol, yes I have downloaded a linux driver.  I got it from here:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

I wish the problem was so simple...

---

### Post by ciscosurfer on 2006-12-06
I checked the site and see that your Printer is supported (scanning, too) so that's good.

Have you made sure that you meet the minimum requirements for installation: [http://hplip.sourceforge.net/system_requirements.html](http://hplip.sourceforge.net/system_requirements.html)

And I assume as well that you've followed these instructions to a "T": [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Otherwise, (and I don't want to sound like I'm putting you off...b/c I'm not, I just want to make sure you avail yourself of all resources), perhaps try the **Usage and Support** & **Resources** links on the sidebar of the main page: [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

---

### Post by quickk on 2006-12-06
I got it to work!  It turns out that all I had to do was restart the computer, and then everything worked just like magic.  I have no idea why.  I thought that you didn't have to reboot linux to get programs installed.  Am I wrong?

Thanks for all your help!

---

### Post by angkor on 2006-12-06
> **quickk said:**
> I got it to work!  It turns out that all I had to do was restart the computer, and then everything worked just like magic.  I have no idea why.  I thought that you didn't have to reboot linux to get programs installed.  Am I wrong?

Thanks for all your help!

Congrats!

Usually you don't have to reboot, if you know what service to start and how to do that manually. If you don't, a reboot can help.

---

### Post by ciscosurfer on 2006-12-06
Glad it's all working now!

---

### Post by CatKiller on 2006-12-06
For reference, if you find yourself using a machine that uses apt, but doesn't have aptitude, you'll probably want to know that **apt-get** is the bit that gets the packages. **apt-cache** is the bit that tells you stuff about it. So you'd want ```
sudo apt-cache search *keyword*
sudo apt-cache show *packagename*
```

---

### Post by ciscosurfer on 2006-12-06
> **CatKiller said:**
> For reference, if you find yourself using a machine that uses apt, but doesn't have aptitude, you'll probably want to know that **apt-get** is the bit that gets the packages. **apt-cache** is the bit that tells you stuff about it. So you'd want ```
sudo apt-cache search *keyword*
sudo apt-cache show *packagename*
```You don't need to use** sudo** for *either* one of those commands

---

### Post by CatKiller on 2006-12-07
> **ciscosurfer said:**
> You don't need to use** sudo** for *either* one of those commands

I'll take your word for it. I'm just in the habit of using sudo for anything to do with the package management.

---

### Post by ciscosurfer on 2006-12-07
> **CatKiller said:**
> I'll take your word for it. I'm just in the habit of using sudo for anything to do with the package management.You only need to use **sudo** in these instances when you want to install or remove a package.  Searching for a package doesn't require it.  With Synaptic, for example, the reason you enter your password at the beginning is because Synaptic doesn't know what you are going to use it for (you may want to install, remove, etc., as well as search).

---

### Post by CatKiller on 2006-12-07
Yes, that makes total sense. It's just that it takes less than a second to type sudo, and so I do. Habit, as I said.

---

### Post by ciscosurfer on 2006-12-07
> **CatKiller said:**
> Yes, that makes total sense. It's just that it takes less than a second to type sudo, and so I do. Habit, as I said.I totally understand. :KS

---

### Post by PietreWitobi on 2006-12-07
tab completion cna be a pretty useful search tool...
Pretty Ghetto, I know, but I just log in as su and type

apt-get install 

then the first few letters of a package I'm looking for, and hit tab (a couple times if necessary)  If too much shows up on screen, then I can modify my search without having to retype the entire damn command.

---

### Post by quickk on 2006-12-08
Thanks for the great tips.  Sometimes I can get quite frustrated trying to do the simplest things in Linux.  In windows I knew how to do pretty much anything that I wanted so getting stumped on the simple things in linux makes me want to pull my hair out (like when I spend hours trying to get a scanner to work!).  

I really like that tab completion trick.  I didn't realize that you could do this!

---

### Post by ciscosurfer on 2006-12-08
> **quickk said:**
> [...]I really like that tab completion trick.  I didn't realize that you could do this!You can do it in DOS, too ;)

---

